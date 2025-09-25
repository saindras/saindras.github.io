---
layout: post
title: "Simulasi Menggunakan Wokwi Online"
date: 2025-06-06 10:00:00 +0800
categories: [IoT]
tags: [esp8266, dht11, ds18b20, arduino, iot, monitoring, simulasi, wokwi]
description: "Panduan langkah demi langkah membangun sistem IoT real-time untuk memantau suhu dan kelembaban akuarium Anda, khusus pada bagian ini adalah untuk melakukan simulasi di Wokwi mode online."
---

## Pendahuluan

Wokwi adalah simulator IoT online yang mendukung berbagai mikrokontroler seperti ESP32 dan ESP8266, serta berbagai sensor. Ada dua cara menggunakan Wokwi: versi online (langsung menggunakan web Wokwi) dan versi offline (menggunakan ekstensi untuk Visual Studio Code (VS Code)).

**Kelebihan:**
*   Mendukung **ESP8266**, **DHT11**, **OLED 0.96”**, **DS18B20**, dsb.
*   Bisa **simulasikan WiFi**, delay, bahkan display.
*   Coding langsung dengan **Arduino IDE style (C++)**.
*   Tidak perlu instal software, **langsung online**.
*   Bisa save project & bagikan.

**Fitur unggulan:**
*   Real-time grafik suhu (jika pakai DS18B20).
*   Library lengkap dan cepat.
*   Bisa tambahkan **komentar visual** dalam wiring.

> Untuk simulasi WiFi (HTTP/MQTT), masih terbatas (bisa pakai placeholder).
{: .prompt-warning }

## Kebutuhan Simulasi

1.  **Platform Wokwi**:
    * **Online**: Akses langsung di [wokwi.com](https://wokwi.com).
    * **Offline (VS Code)**: Instal ekstensi `Wokwi Simulator` di VS Code.
2.  **Kode Program (Firmware)**: Kita akan menggunakan kode yang ditulis dalam gaya Arduino (C++).
3.  **Pengetahuan Dasar**: Konsep dasar elektronika (VCC, GND, data pin), dan sedikit tentang pemrograman Arduino.

## Langkah-langkah Wokwi Online

Kita akan menggunakan **KODE PROGRAM CONTOH** sebagai contoh dasar simulasi.
1.  Silakan registrasi akun di [wokwi.com](https://wokwi.com), dengan menekan tombol `SIGN UP`.
2.  Buat proyek baru dengan menekan tombol `NEW PROJECT`.
3.  Pilih template `ESP32 (Arduino)`. Meskipun perangkat fisik kita nanti ESP8266, ESP32 di Wokwi menawarkan simulasi yang lebih kaya, dan kode Arduino-nya sebagian besar kompatibel.
4.  Tambahkan library pada **Library Manager** seperti: `DHT sensor library`, `LiquidCrystal I2C`, `OneWire`, dan `DallasTemperature`.
5.  Gunakan kode `sketch.ino`, `libraries.txt`, dan `diagram.json` yang saya sediakan.
6.  Jalankan simulasi.

<section class="details">
<details>
  <summary>Klik di sini untuk melihat tampilan proyek di Wokwi.</summary>

  <img alt="output" src="1UEzmSxNl4p7NczCNtM-hjv-f_vS4P83X"/>

</details>
</section>

## Langkah-langkah Wokwi Offline
1. Buat folder proyek baru di komputer Anda (misal: `my-aquarium-iot`).
2. Di dalamnya, buat tiga file penting: `main.cpp`, `wokwi.toml`, dan `diagram.json`.
3. Konfigurasi `wokwi.toml`. File ini mendefinisikan jenis board yang akan disimulasikan.

> Untuk lebih jelasnya mengenai penggunaan Wokwi offline via VS Code, akan dijelaskan secara detail pada postingan berbeda.
{: .prompt-info }


## Kode Program `sketch.ino`

Berikut adalah kode dasar yang membaca sensor dan menampilkannya ke LCD:

```cpp
#include <Arduino.h>

#include <WiFi.h>
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
#include <DHT.h>
#include <OneWire.h>
#include <DallasTemperature.h>
#include <HTTPClient.h>

// --- DHT22 ---
#define DHTPIN 15
#define DHTTYPE DHT22
DHT dht(DHTPIN, DHTTYPE);

// --- DS18B20 ---
#define ONE_WIRE_BUS 4
OneWire oneWire(ONE_WIRE_BUS);
DallasTemperature ds18b20(&oneWire);

// --- LCD I2C ---
LiquidCrystal_I2C lcd(0x27, 16, 2);

// --- WiFi & NTP ---
const char* ssid = "Wokwi-GUEST";
const char* password = "";
#define NTP_SERVER     "pool.ntp.org"
#define UTC_OFFSET     8 * 3600  // WITA (GMT+8)
#define UTC_OFFSET_DST 0

void setup() {
  Serial.begin(115200);
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("Connecting WiFi");

  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(250);
    lcd.print(".");
  }

  lcd.clear();
  lcd.print("WiFi Connected");
  Serial.println("WiFi Connected");

  configTime(UTC_OFFSET, UTC_OFFSET_DST, NTP_SERVER);
  dht.begin();
  ds18b20.begin();
  delay(2000);
  lcd.clear();
}

void loop() {
  struct tm timeinfo;
  if (!getLocalTime(&timeinfo)) {
    lcd.setCursor(0, 0);
    lcd.print("Waktu Error     ");
    lcd.setCursor(0, 1);
    lcd.print("Cek NTP Server  ");
    delay(2000);
    return;
  }

  // Baca DHT22
  float suhuLuar = dht.readTemperature();
  float kelembaban = dht.readHumidity();

  // Baca DS18B20
  ds18b20.requestTemperatures();
  float suhuDalam = ds18b20.getTempCByIndex(0);

  // Validasi
  if (isnan(suhuLuar) || isnan(kelembaban) || suhuDalam == DEVICE_DISCONNECTED_C) {
    Serial.println("Sensor gagal baca");
    lcd.setCursor(0, 0);
    lcd.print("Sensor Error     ");
    lcd.setCursor(0, 1);
    lcd.print("Retrying...");
    delay(2000);
    return;
  }

  // Format waktu
  char waktuStr[20];
  strftime(waktuStr, sizeof(waktuStr), "%Y-%m-%d %H:%M:%S", &timeinfo);
  String waktuEncoded = String(waktuStr);
  waktuEncoded.replace(" ", "%20");

  // Serial log
  Serial.printf("%s | S.luar: %.1f°C | Hum: %.1f%% | S.dalam: %.1f°C\n",
                waktuStr, suhuLuar, kelembaban, suhuDalam);

  // LCD
  lcd.setCursor(0, 0);
  lcd.printf("L:%.1fC A:%.1fC", suhuLuar, suhuDalam);
  lcd.setCursor(0, 1);
  lcd.print(&timeinfo, "%H:%M:%S");
  delay(5000);
  lcd.setCursor(0, 1);
  lcd.print(&timeinfo, "%d/%m/%Y");
  delay(5000);

}
```

## Kode Program `libraries.txt`

Berikut adalah kode yang digunakan untuk mendeklarasikan pustaka (library) eksternal Arduino yang ingin digunakan dalam proyek:

```yaml
# Wokwi Library List
# See https://docs.wokwi.com/guides/libraries

DHT sensor library
LiquidCrystal I2C
OneWire
DallasTemperature
```

## Kode Program `diagram.json`

Berikut adalah kode yang digunakan untuk mendeskripsikan rangkaian elektronika atau wiring yang dibuat dalam simulasi:

```json
{
  "version": 1,
  "author": "Santyadiputra, G. S.",
  "editor": "wokwi",
  "parts": [
    { "type": "wokwi-breadboard-half", "id": "bb1", "top": 25.8, "left": 204.4, "attrs": {} },
    { "type": "board-esp32-devkit-c-v4", "id": "esp", "top": 211.2, "left": 724.84, "attrs": {} },
    { "type": "wokwi-dht22", "id": "dht1", "top": -9.3, "left": 733.8, "attrs": {} },
    {
      "type": "wokwi-lcd1602",
      "id": "lcd1",
      "top": 467.2,
      "left": 600.8,
      "attrs": { "pins": "i2c" }
    },
    {
      "type": "wokwi-resistor",
      "id": "r1",
      "top": 91.2,
      "left": 796.25,
      "rotate": 90,
      "attrs": { "value": "10000" }
    },
    { "type": "board-ds18b20", "id": "temp1", "top": -68.33, "left": 109.68, "attrs": {} },
    {
      "type": "wokwi-resistor",
      "id": "r2",
      "top": 33.6,
      "left": 37.85,
      "rotate": 90,
      "attrs": { "value": "10000" }
    }
  ],
  "connections": [
    [ "esp:TX", "$serialMonitor:RX", "", [] ],
    [ "esp:RX", "$serialMonitor:TX", "", [] ],
    [ "esp:3V3", "bb1:bp.25", "red", [ "h-28.65", "v115.2", "h-153.6", "v-133.5" ] ],
    [ "esp:GND.1", "bb1:bn.25", "black", [ "h0" ] ],
    [ "dht1:VCC", "bb1:tp.25", "red", [ "h-28.8", "v-67.5" ] ],
    [ "dht1:GND", "bb1:tn.25", "black", [ "v28.8", "h-67.2", "v-86.3" ] ],
    [ "lcd1:GND", "bb1:bn.1", "black", [ "h-412.8", "v-278.4", "v0", "h46.4" ] ],
    [ "lcd1:VCC", "bb1:bp.1", "red", [ "v0.1", "h-422.4", "v-239.1" ] ],
    [ "dht1:SDA", "bb1:30t.a", "green", [ "h0.1", "v19.2", "h-67.2", "v-48" ] ],
    [ "r1:1", "bb1:tp.24", "red", [ "v-105.6", "h-232" ] ],
    [ "r1:2", "bb1:30t.b", "green", [ "v27.6", "h-144", "v-67.2" ] ],
    [ "esp:15", "bb1:30t.c", "green", [ "h9.6", "v-211.2", "h-163.2", "v-67.2" ] ],
    [ "esp:21", "bb1:29b.j", "gold", [ "h19.2", "v-96", "h-345.6" ] ],
    [ "esp:22", "bb1:28b.j", "blue", [ "h28.8", "v-57.6", "h-364.8" ] ],
    [ "lcd1:SDA", "bb1:29b.i", "gold", [ "h-19.2", "v-345.4" ] ],
    [ "lcd1:SCL", "bb1:28b.i", "blue", [ "h-134.4", "v-354.9" ] ],
    [ "temp1:GND", "bb1:tn.1", "black", [ "v0" ] ],
    [ "temp1:VCC", "bb1:tp.1", "red", [ "v0" ] ],
    [ "temp1:DQ", "bb1:1t.a", "violet", [ "v0" ] ],
    [ "r2:1", "bb1:tp.2", "red", [ "h0" ] ],
    [ "r2:2", "bb1:1t.b", "violet", [ "v18", "h163.2" ] ],
    [ "esp:4", "bb1:1t.c", "violet", [ "h19.2", "v86.4", "h-681.6", "v-345.6" ] ]
  ],
  "dependencies": {}
}
```

## Referensi

- [Dokumentasi Wokwi](https://docs.wokwi.com/)
