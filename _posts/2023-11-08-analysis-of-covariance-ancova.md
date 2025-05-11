---
layout: post
title: Analysis of Covariance (Ancova)
date: 2023-11-08 15:13 +0700
categories:
  - Statistik
  - Ancova
tags:
  - statistik
  - ancova
---

[![DOI badge - Zenodo](https://zenodo.org/badge/DOI/10.5281/zenodo.10219354.svg)](https://doi.org/10.5281/zenodo.10219354){:target="\_blank"}

## Sekilas tentang Ancova

Ancova adalah singkatan dari _"Analysis of Covariance"_ yang merupakan metode statistik yang menggabungkan elemen-elemen dari dua teknik statistik yang berbeda: Analisis Varians (Anova) dan Analisis Regresi. Tujuan utama Ancova adalah untuk membandingkan rata-rata antara dua atau lebih kelompok dengan mempertimbangkan pengaruh variabel bebas yang disebut sebagai covariate. Ini digunakan untuk memeriksa apakah ada perbedaan signifikan antara kelompok-kelompok tersebut setelah mengontrol atau memperhitungkan perbedaan dalam nilai rata-rata covariate. Covariate adalah variabel yang mempengaruhi variabel terikat, dan dengan mengontrol covariate ini, Ancova membantu mengurangi variabilitas yang dapat menyebabkan kesalahan dalam penentuan perbedaan antara kelompok-kelompok tersebut.

Dalam konteks Ancova, ada beberapa istilah yang perlu dipahami:

1. Variabel Terikat: variabel yang ingin dibandingkan antara kelompok-kelompok. Misalnya, dalam penelitian pendidikan, variabel terikat mungkin adalah hasil tes peserta didik.
2. Variabel Bebas: variabel yang digunakan untuk membagi kelompok-kelompok. Misalnya, dalam penelitian pendidikan, variabel bebas mungkin adalah metode pengajaran, dengan beberapa kelompok diajar dengan metode A dan yang lainnya dengan metode B.
3. Covariate: Ini adalah variabel yang dapat mempengaruhi variabel terikat dan perlu dikontrol. Ini adalah bagian penting dari Ancova dan membantu mengurangi kesalahan dalam penentuan perbedaan antara kelompok-kelompok. Misalnya, dalam penelitian pendidikan, covariate mungkin adalah tingkat intelegensi peserta didik.

Ancova digunakan ketika ingin membandingkan rata-rata antara kelompok-kelompok yang berbeda, sambil mempertimbangkan pengaruh dari covariate. Ancova dapat membantu memahami apakah perbedaan antara kelompok-kelompok tetap signifikan setelah mengontrol faktor-faktor tertentu yang dapat memengaruhi hasil.

## Contoh kasus Ancova satu jalur

Diketahui variabel bebas VLEs terdiri dari 3 kelompok yakni VLE1, VLE2, dan VLE3. VLE1 treatment menggunakan video, VLE2 treatment menggunakan Cisco-PT, dan VLE3 treatment menggunakan Vilanets. Covariate adalah hasil pretest peserta didik. Variabel terikat adalah hasil posttest peserta didik. Data untuk variabel bebas bertipe kategorikal dan data untuk variabel terikat dan covariate adalah tipe numerikal.

Dalam hal ini, peneliti ingin menemukan pengaruh dari Virtual Learning Environments (VLEs) terhadap prestasi belajar peserta didik (PB). Apabila ada pengaruh, peneliti juga ingin menemukan apakah covariate merupakan sebuah variabel penting dalam menentukan pengaruh. Selain itu, peneliti juga dapat menemukan perbedaan antara ketiga jenis variabel bebas (VLE1, VLE2, dan VLE3) menggunakan perhitungan EMM dan Bonferroni post-hoc test.

Adapun uji asumsi yang terlebih dahulu dilakukan sebelum ke proses Ancova adalah uji asumsi _outliers_, _linearity_, _homogeneity of regression slopes_, _normality of residuals_, dan _homogeneity of variances_.

## Hasil perhitungan menggunakan Python, R, dan SPSS

1. [Hasil perhitungan menggunakan Python](https://nbviewer.org/github/saindras/statistik/blob/4db47c97616b2579d986841fb2c869da0366606d/ancova-satu-jalur/ancova-satu-jalur-menggunakan-python.ipynb){:target="\_blank"}
2. [Hasil perhitungan menggunakan R](https://rpubs.com/gsaindras/Ancova-satu-jalur-menggunakan-r){:target="\_blank"}
3. [Hasil perhitungan menggunakan SPSS](https://saindras.github.io/posts/ancova-satu-jalur-menggunakan-spss/){:target="\_blank"}

## Referensi

1. [Analysis of covariance using Python](https://www.youtube.com/watch?v=FhZB1oGVrYc){:target="\_blank"}
2. [Ancova in R](https://www.datanovia.com/en/lessons/Ancova-in-r/){:target="\_blank"}
3. [Ancova using R and Python](https://www.reneshbedre.com/blog/Ancova.html){:target="\_blank"}

## Sitasi dokumen ini

Santyadiputra, G. S., Purnomo, & Juniantari, M. (2023, November 29). Analysis of Covariance (Ancova). GitHub. https://doi.org/10.5281/zenodo.10219354

> Untuk sitasi lebih lanjut, silakan klik badge di bawah.
> {: .prompt-info }

[![DOI badge - Zenodo](https://zenodo.org/badge/DOI/10.5281/zenodo.10219354.svg)](https://doi.org/10.5281/zenodo.10219354){:target="\_blank"}
