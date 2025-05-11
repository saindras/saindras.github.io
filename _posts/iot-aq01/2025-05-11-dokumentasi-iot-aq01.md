---
layout: post
title: "Dokumentasi Proyek IoT AQ01"
date: 2025-05-11
categories: [IoT]
---

Selamat datang di dokumentasi proyek **IoT Monitoring Suhu dan Kelembaban Akuarium (AQ01)**.

---

## 1️⃣ Subsistem IoT

### Komponen
- **ESP8266 / ESP32**
- **Sensor DHT11 dan DS18B20**
- **LCD 16x2 I2C**

### Fungsi
Membaca suhu air dan kelembaban udara, menampilkan waktu, dan mengirimkan data ke server lokal atau ThingSpeak.

### Daftar Versi:
| ID Versi | Deskripsi |
|----------|-----------|
| `CODE-AQ01-001` | Baca DHT22 dan tampilkan ke LCD |
| `CODE-AQ01-002` | Kirim data ke ThingSpeak |
| `CODE-AQ01-003` | Dashboard Web Server Lokal ESP |
| `CODE-AQ01-004` | Versi fisik dengan WiFi sekolah |

---

## 2️⃣ Subsistem Lokal

### Komponen
- PHP + MySQL
- File utama: `index.php`, `upload.php`, `dashboard_thinkspeak.html`

### Fitur
- Tampilan grafik suhu dan kelembaban
- Ekspor data ke Excel/CSV/PDF
- Sinkronisasi manual ke ThingSpeak
- Input data dari ESP melalui `upload.php`

### Manajemen Versi CODE-AQ01-DSHBRD001

| File | Fungsi |
|------|--------|
| `index.php` | Menampilkan data realtime dari database lokal, grafik, dan kirim ke ThingSpeak |
| `upload.php` | Endpoint data dari IoT |
| `dashboard_thinkspeak.html` | Menampilkan grafik dari ThingSpeak |

---

## 3️⃣ Desain PCB

### Tools
- EasyEDA
- CNC Engraver 3018
- HSS drill bit 1.98–3.56 mm

### Komponen
- NodeMCU ESP8266 V3
- DHT11 dan DS18B20
- LCD I2C + header pin

### File pendukung
- `diagram.json`
- `pcb-layout.jpg`
- `bom.csv`

---

## 4️⃣ Server Raspberry Pi

### Setup
- OS: Raspberry Pi OS Lite 64-bit
- Docker + Portainer
- MQTT untuk komunikasi lokal
- Cronjob untuk sinkronisasi ke internet

### File Konfigurasi
- `docker-compose.yml`
- `mqtt-setup.sh`
- `cron-sync.sh`

---

> Proyek ini merupakan bagian dari pengembangan riset pendidikan vokasi oleh Gede Saindra, dan didokumentasikan menggunakan GitHub Pages + Jekyll Chirpy.
