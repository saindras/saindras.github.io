---
layout: post
title: "Dokumentasi Proyek IoT AQ01"
date: 2025-05-11 14:00 +0800
categories: [IoT]
tags: [iot, aq01, dokumentasi]
---

Dokumentasi lengkap proyek **IoT Monitoring Suhu dan Kelembaban Akuarium (AQ01)**:

## 1️⃣ Subsistem IoT

ESP8266/ESP32 membaca suhu & kelembaban melalui DHT11 dan DS18B20, menampilkan data di LCD I2C, serta mengirimkannya ke server lokal atau ThingSpeak.

**Versi Kode:**

- `CODE-AQ01-001`: LCD + pembacaan DHT22
- `CODE-AQ01-002`: Kirim ke ThingSpeak
- `CODE-AQ01-003`: Web dashboard ESP
- `CODE-AQ01-004`: Versi fisik dengan WiFi sekolah

## 2️⃣ Subsistem Lokal

Dashboard berbasis PHP dan MySQL, menampilkan grafik dan ekspor data, menerima input dari perangkat IoT.

**File penting:**

- `index.php`
- `upload.php`
- `dashboard_thinkspeak.html`

## 3️⃣ Desain PCB

Menggunakan EasyEDA dan mesin CNC 3018, desain menyatukan ESP, sensor, dan LCD I2C untuk kestabilan sistem IoT.

## 4️⃣ Server Raspberry Pi

Raspberry Pi OS Lite + Docker + MQTT untuk menerima data secara lokal dan sinkronisasi berkala ke cloud.

---

> Halaman ini dibangun dengan Jekyll + Chirpy, dan merupakan bagian dari dokumentasi riset pendidikan vokasi oleh Gede Saindra.
