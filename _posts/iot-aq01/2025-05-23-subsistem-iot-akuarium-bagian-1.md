---
layout: post
title: "Menentukan Perangkat Keras IoT"
date: 2025-05-23 13:00:00 +0800
categories: [IoT]
tags: [esp8266, dht11, ds18b20, arduino, iot, monitoring]
description: "Panduan langkah demi langkah membangun sistem IoT real-time untuk memantau suhu dan kelembaban akuarium Anda, khusus pada bagian ini adalah untuk menentukan perangkat keras yang akan digunakan."
---

# Pendahuluan

Pernahkah Anda ingin memantau suhu dan kelembaban akuarium secara real-time? Dalam postingan ini, saya akan berbagi perjalanan saya membuat sistem IoT yang memantau parameter-parameter tersebut dan menampilkannya pada dashboard web. Proyek ini kita namakan "AQ1" yaitu pemantauan suhu dan kelembaban pada akuarium.

Halaman ini adalah bagian dari proyek AQ1 khusus pada subsistem IoT. Subsistem ini memiliki fungsi utama yaitu mengambil data suhu dalam akuarium, suhu luar akuarium, kelembaban luar akuarium, dan waktu pengambilan. Perangkat akan mengirimkan semua data ke server melalui media transmisi wireless.

<section class="details">
<details>
  <summary>Klik di sini untuk melihat ilustrasi sistem.</summary>

  <img alt="output" src="1SB0dHQb4kS_Qw5DdKjBNhzNCbvP1dHVx"/>

</details>
</section>

Proyek ini akan dibagi menjadi beberapa topik yaitu:

1. Menentukan perangkat keras
2. Melakukan simulasi di Wokwi

# Gambaran Proyek

Sistem ini mengumpulkan:

- Suhu air (menggunakan sensor DS18B20)
- Suhu dan kelembaban ruangan (menggunakan sensor DHT11)
- Timestamp untuk setiap pembacaan

Data dikumpulkan setiap 30 detik dan dikirim ke database cloud, sehingga dapat diakses dari mana saja melalui antarmuka web.

# Arsitektur Sistem

Proyek ini mengikuti arsitektur IoT standar dengan komponen-komponen berikut:

1. **Lapisan Perangkat Keras**: Sensor terhubung ke mikrokontroler
2. **Lapisan Konektivitas**: Koneksi WiFi ke internet
3. **Lapisan Cloud**: Database dan web hosting
4. **Lapisan Aplikasi**: Dashboard web untuk visualisasi

# Komponen Perangkat Keras

Untuk proyek ini, saya menggunakan:

- **ESP8266** (NodeMCU v3 Amica Type C) sebagai pengontrol utama dengan WiFi bawaan [Link](https://id.shp.ee/oTK9G8f)
- **DHT11** sensor untuk mengukur suhu dan kelembaban ruangan [Link](https://id.shp.ee/21CAyPk)
- **DS18B20 waterproof** sensor untuk mengukur suhu air [Link](https://id.shp.ee/YXFuQdJ)
- **Resistor 4.7k Ohm** 2 resistor pull-up untuk sensor-sensor [Link](https://id.shp.ee/GaZSBAG)
- **LCD 1602** sebagai monitor output dengan ukuran 16x2, termasuk module i2C yang sudah tersolder [Link](https://id.shp.ee/1ncfa3o)
- Breadboard 400 point untuk prototyping [Link](https://id.shp.ee/cK2DsDY)
- Kabel jumper untuk prototyping, rekomendasi menggunakan kabel male to female [Link](https://id.shp.ee/izo9t2m)

## Mengapa Resistor 4.7k Ohm?

Sensor DS18B20 berkomunikasi menggunakan protokol yang disebut "1-Wire" yang memungkinkannya mengirim data melalui satu jalur data. Protokol ini memerlukan resistor "pull-up" untuk memastikan transmisi sinyal yang tepat.

Bayangkan resistor seperti pegas yang menjaga jalur data dalam keadaan "tinggi" ketika tidak ada yang secara aktif menariknya ke posisi rendah. Tanpa resistor ini, sinyal akan berfluktuasi secara tidak terduga, menyebabkan kesalahan komunikasi.

Nilai 4.7k Ohm secara khusus direkomendasikan oleh produsen karena:

- Resistansi yang terlalu rendah (misalnya, 1k Ohm) akan menarik terlalu banyak arus
- Resistansi yang terlalu tinggi (misalnya, 10k Ohm) akan membuat sinyal terlalu lemah

Resistor ini ditempatkan di antara pin data dan jalur daya (VCC), menciptakan saluran komunikasi yang andal antara sensor dan mikrokontroler.

# Diagram Pengkabelan

Berikut cara menghubungkan semuanya:

## Koneksi ESP8266:

- Hubungkan ke sumber tegangan 5v menggunakan kabel USB (gunakan adaptor 5v): Kabel USB ke adaptor 5v
- Hubungkan sumber tegangan 5v (Vin 5v) ke LCD: kabel MERAH
- Hubungkan sumber tegangan 3.3v (3v3) ke DHT11 melalui resistor 4.7k Ohm: kabel MERAH
- Hubungkan sumber tegangan 3.3v (3v3) ke DS18B20 melalui resistor 4.7k Ohm: kabel MERAH
- Hubungkan ground (GND) ke LCD, DHT11, dan DS18B20: kabel HITAM
- Hubungkan pin data DHT11 ke D5 (GPIO14) melalui resistor 4.7k Ohm: kabel MAGENTA
- Hubungkan pin data DS18B20 ke D6 (GPIO12) melalui resistor 4.7k Ohm: kabel HIJAU
- Hubungkan pin data LCD SDA ke D2 (GPIO4): kabel KUNING
- Hubungkan pin data LCD SCL ke D1 (GPIO5): kabel BIRU

## Koneksi DHT11:

- Pin 1 (VCC) ke ESP8266 3.3V melalui resistor 4.7k Ohm: kabel MERAH
- Pin 2 (DATA) ke ESP8266 D5 (GPIO14) melalui resistor 4.7k Ohm: kabel MAGENTA
- Pin 3 (GND) ke ESP8266 GND: kabel HITAM

## Koneksi DS18B20:

- Pin 1 (VCC) ke ESP8266 3.3V melalui resistor 4.7k Ohm: kabel MERAH
- Pin 2 (DATA) ke ESP8266 D6 (GPIO12) melalui resistor 4.7k Ohm: kabel HIJAU
- Pin 3 (GND) ke ESP8266 GND: kabel HITAM

## Koneksi LCD:

- Pin 1 (VCC) ke ESP8266 5V (Vin 5v): kabel MERAH
- Pin 2 (SDA) ke ESP8266 D2 (GPIO4): kabel KUNING
- Pin 3 (SCL) ke ESP8266 D1 (GPIO5): kabel BIRU
- Pin 4 (GND) ke ESP8266 GND: kabel HITAM

<section class="details">
<details>
  <summary>Klik di sini untuk melihat diagram skematik.</summary>

  <img alt="output" src="1S7QCrEv74cECJDLS4Mq-PbtsAzVKlQK9"/>

</details>
</section>

Setelah semua rancangan terpenuhi, langkah selanjutnya adalah mensimulasikan di Wokwi.

## Referensi

- [Dokumentasi NodeMCU ESP8266](https://www.make-it.ca/nodemcu-details-specifications/)
