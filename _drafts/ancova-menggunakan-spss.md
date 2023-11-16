---
layout: post
title: Ancova satu jalur menggunakan SPSS
categories: [Statistik, Ancova]
tags: [statistik, ancova]
author: <author_id>
---
## Pendahuluan

Pada tulisan sebelumnya terkait [Analysis of Covariance (Ancova)](https://saindras.github.io/posts/ancova/), telah dijelaskan bahwa Ancova merupakan salah satu metode statistik gabungan dari Anova dan Regresi untuk membandingkan rata-rata antara dua atau lebih kelompok dengan mempertimbangkan pengaruh variabel bebas yang disebut sebagai covariate. Salah satu tool statistik yang dapat digunakan untuk melakukan perhitungan Ancova adalah Statistical Package for the Social Sciences (SPSS) versi 25.

> SPSS merupakan perangkat lunak statistik yang digunakan untuk analisis data. Dikembangkan oleh IBM, SPSS menyediakan fitur manajemen data, analisis statistik deskriptif, uji hipotesis, analisis regresi, analisis faktor, visualisasi data, dan pembuatan laporan. Digunakan di berbagai bidang, SPSS membantu dalam pengambilan keputusan berdasarkan analisis statistik.
{: .prompt-info }

## Contoh deskripsi penelitian

Seorang peneliti ingin mengetahui pengaruh dari suatu Virtual Learning Environments (VLE) terhadap prestasi belajar peserta didik pada mata kuliah Jaringan Komputer. Pengaruh tersebut dikontrol oleh suatu co-variabel (covariate) pretest. Oleh karena itu, peneliti merancang suatu penelitian eksperimen semu *(quasi-experiment)* dengan melibatkan kelas kontrol dan kelas eksperimen. Kelas kontrol adalah kelas yang menggunakan Virtual Learning Environments existing, contohnya menggunakan Moodle dengan suplemen video pembelajaran dan simulator Cisco-PT. Sedangkan, kelas eksperimen menggunakan Moodle dan media pembelajaran inovatif seperti Virtual Lab Network Simulation (Vilanets).

Sampai di sini, kita mengetahui ada 3 kelas dalam penelitian. Kelas ke-1 dinamakan VLE1 (VLE dengan suplemen video), kelas ke-2 dinamakan VLE2 (VLEs dengan suplemen Cisco-PT), dan kelas ke-3 dinamakan VLE3 (VLEs dengan suplemen Vilanets). Kelas-kelas tersebut nantinya akan menjadi kelompok/dimensi di dalam variabel bebas Ancova. Jika menggunakan 3 kelas (atau lebih), maka akan ada kemungkinan perhitungan akan dilanjutkan ke post-hoc test ketika terdapat pengaruh antara VLEs dan prestasi belajar.

Karena ini adalah penelitian kuantitatif di mana tujuannya adalah menguji teori, teori baru yang diajukan harus dikontruksi. Misalnya, peneliti ingin menguji teori VLEs. Oleh karena itu, disarankan ada teori baru turunan dari VLEs. Peneliti mengajukan  teori bernama `Advanced VLEs`. Apabila dikaitkan dengan 3 kelas sebelumnya, dikontruksi teori sebagai berikut. VLE1 mewakili teori `Beginner VLEs`, VLE2 mewakili teori `Intermediate VLEs`, dan VLE3 mewakili teori `Advanced VLEs`.

## Contoh tujuan penelitian

Tujuan penelitian tersebut adalah sebagai berikut.
1. Peneliti ingin menemukan pengaruh antara VLEs dan prestasi belajar yang dikontrol oleh pretest.
2. Peneliti ingin menemukan perbedaan antara 3 kelas VLEs.

## Variabel-variabel dan tipe data

Variabel bebas (dependent variable): VLEs dengan tiga kelompok

## Diagram konstelasi

## Hipotesis

## Inisiasi data

## Uji asumsi

### Outliers

### Linearity

### Homogeneity of regression slopes

### Normality of residuals

### Homogeneity of variances

## Ancova satu jalur

## Interpretasi hasil