---
layout: post
title: Ancova satu jalur menggunakan SPSS
categories: [Statistik, Ancova]
tags: [statistik, ancova]
date: 2023-11-17 10:35 +0700
---
## Pendahuluan

Pada tulisan sebelumnya terkait [Analysis of Covariance (Ancova)](https://saindras.github.io/posts/ancova/), telah dijelaskan bahwa Ancova merupakan salah satu metode statistik gabungan dari Anova dan Regresi untuk membandingkan rata-rata antara dua atau lebih kelompok dengan mempertimbangkan pengaruh variabel bebas yang disebut sebagai covariate. Salah satu tool statistik yang dapat digunakan untuk melakukan perhitungan Ancova adalah [*Statistical Package for the Social Sciences* (SPSS)][id1] versi 25.

[id1]: # "SPSS merupakan perangkat lunak statistik yang digunakan untuk analisis data. Dikembangkan oleh IBM, SPSS menyediakan fitur manajemen data, analisis statistik deskriptif, uji hipotesis, analisis regresi, analisis faktor, visualisasi data, dan pembuatan laporan. Digunakan di berbagai bidang, SPSS membantu dalam pengambilan keputusan berdasarkan analisis statistik."

## Contoh deskripsi penelitian

[id2]: # "Virtual Learning Environments (VLEs) adalah platform pembelajaran online yang memfasilitasi akses terstruktur ke materi pembelajaran dan interaksi antar peserta didik. Dengan fitur-fitur interaktif, evaluasi online, dan kemampuan kolaborasi, VLEs menjadi kunci dalam mendukung pembelajaran jarak jauh. Contohnya termasuk Moodle, Blackboard, dan Canvas."

Seorang peneliti ingin mengetahui pengaruh dari suatu [*Virtual Learning Environments* (VLEs)][id2] terhadap prestasi belajar peserta didik pada mata kuliah Jaringan Komputer. Pengaruh tersebut dikontrol oleh suatu co-variabel (covariate) pretest. Oleh karena itu, peneliti merancang suatu penelitian eksperimen semu *(quasi-experiment)* dengan melibatkan kelas kontrol dan kelas eksperimen. Kelas kontrol adalah kelas yang menggunakan Virtual Learning Environments existing, contohnya menggunakan Moodle dengan suplemen video pembelajaran dan simulator Cisco-PT. Sedangkan, kelas eksperimen menggunakan Moodle dan media pembelajaran inovatif seperti *Virtual Lab Network Simulation* (Vilanets).

Sampai di sini, kita mengetahui ada 3 kelas dalam penelitian tersebut. Kelas ke-1 dinamakan VLE1 (VLEs dengan suplemen video), kelas ke-2 dinamakan VLE2 (VLEs dengan suplemen Cisco-PT), dan kelas ke-3 dinamakan VLE3 (VLEs dengan suplemen Vilanets). Kelas-kelas tersebut nantinya akan menjadi kelompok/dimensi di dalam variabel bebas Ancova. Jika menggunakan 3 kelas (atau lebih), maka akan ada kemungkinan perhitungan akan dilanjutkan ke *post-hoc test* ketika terdapat pengaruh antara VLEs dan prestasi belajar.

Karena ini adalah penelitian kuantitatif di mana tujuannya adalah menguji teori, teori baru yang diajukan harus dikontruksi. Misalnya, peneliti ingin menguji teori VLEs. Oleh karena itu, disarankan ada teori baru turunan dari VLEs. Peneliti mengajukan  teori bernama *Advanced VLEs*. Apabila dikaitkan dengan 3 kelas sebelumnya, dikontruksi teori sebagai berikut. VLE1 mewakili teori `Beginner VLEs`, VLE2 mewakili teori `Intermediate VLEs`, dan VLE3 mewakili teori `Advanced VLEs`.

## Contoh tujuan penelitian

Tujuan penelitian tersebut adalah sebagai berikut.
1. Peneliti ingin menemukan pengaruh antara VLEs dan prestasi belajar yang dikontrol oleh pretest.
2. Peneliti ingin menemukan perbedaan antara 3 kelompok VLEs (beginner, intermediate, dan advanced VLEs) terhadap prestasi belajar yang dikontrol oleh pretest.

## Variabel-variabel dan tipe data

Variabel-variabel penelitiannya adalah sebagai berikut.
1. Variabel bebas *(independent variable)*: VLEs dengan tiga kelompok (beginner, intermediate, dan advanced VLEs), selanjutnya dinamakan VLE1, VLE2, dan VLE3. Tipe datanya adalah kategorikal di mana 1 mewakili VLE1, 2 mewakili VLE2, dan 3 mewakili VLE3.
2. Variabel terikat *(dependent variable)*: prestasi belajar (posttest). Tipe datanya adalah numerikal berkisar antara 0 - 100.
3. Co-variabel *(covariate)*: pretest. Tipe datanya adalah numerikal berkisar antara 0 - 100.

## Diagram konstelasi dan hipotesis penelitian

Diagram konstelasi menunjukkan hubungan antar variabel, seperti pada Gambar 1. Hubungan tersebut memandu peneliti untuk menentukan hipotesis-hipotesis penelitian dalam rangka tercapainya tujuan-tujuan penelitan. 

![Diagram konstelasi light](/fc7143ec-8da3-4ee2-8314-68655f475cfa/){: .light .w-75 }
![Diagram konstelasi dark](/5b54d9a1-6423-46a5-87c4-c259359c373b/){: .dark .w-75 }
_Gambar 1. Diagram konstelasi antar variabel_

Adapun hipotesis-hipotesis penelitian adalah sebagai berikut.
1. H1: Terdapat pengaruh yang signifikan VLEs terhadap prestasi belajar dikontrol oleh pretest.
2. H2: Terdapat perbedaan signifikan antara VLE1, VLE2, dan VLE3 terhadap prestasi belajar dikontrol oleh pretest.

## Inisiasi data

Buka SPSS, kemudian akan muncul 2 jendela: `dataset` dan `output`. Buka jendela dataset, kemudian konfigurasi sebagai berikut.

1. Variable view:
    1. Name: `VLEs`; Decimals: `0`; Values: `{1, VLE1; 2, VLE2; 3, VLE3}`; Measure: `Nominal`.
    2. Name: `pretest`; Measure: `Scale`.
    3. Name: `posttest`; Measure: `Scale`.
2. Data view: masukkan data ke sel yang bersesuaian.

Download dataset: 

[![Static Badge](https://img.shields.io/badge/DOI-10.6084%2Fm9.figshare.24580801-blue)](https://doi.org/10.6084/m9.figshare.24580801)

> Ubah terlebih dahulu data pada kolom VLEs mengikuti `values` pada variable view. Contoh: VLE1 ubah ke nilai `1`, VLE2 ubah ke nilai `2`, dan VLE3 ubah ke nilai `3`.
{: .prompt-tip }

> Dataset tersebut telah dipublikasi dan dilindungi hak cipta. Silakan digunakan sebagaimana mestinya dengan tetap melakukan sitasi apabila digunakan.
{: .prompt-warning }

<details>
  <summary>Klik di sini untuk melihat tampilan pada SPSS</summary>
  
    ![Diagram konstelasi light](/fc7143ec-8da3-4ee2-8314-68655f475cfa/){: .light .w-75 }

</details>

## Uji asumsi

Adapun [uji asumsi][id3] sebelum melakukan perhitungan Ancova adalah uji asumsi ouliers, linearity, homogeneity of regression slopes, normality of residuals, dan homogeneity of variances.

[id3]: # "Uji asumsi dilakukan untuk memastikan bahwa data penelitian memenuhi prasyarat yang diperlukan oleh analisis Ancova. Memeriksa asumsi-asumsi ini penting karena kesalahan dalam asumsi dapat mempengaruhi keandalan dan validitas hasil analisis Ancova. Jika data tidak memenuhi asumsi-asumsi tersebut, maka mungkin perlu mencari alternatif atau menerapkan transformasi data untuk memenuhi asumsi tersebut sebelum menggunakan Ancova."

### Outliers

[id4]: # "Uji asumsi outliers adalah pemeriksaan terhadap data terkait ada atua tidaknya observasi yang secara signifikan berbeda dari pola umum dalam data Anda. Outlier dapat mempengaruhi hasil analisis dan memeriksa asumsi tentang distribusi normalitas dan homogenitas varians."

Uji asumsi yang pertama adalah [outliers][id4]. Uji asumsi outliers berfungsi untuk mengidentifikasi adanya nilai-nilai ekstrim dalam dataset. Outliers dapat memengaruhi kehandalan hasil analisis Ancova, terutama terkait dengan dua asumsi utama: normalitas dan homogenitas varians. Jika ada outlier, distribusi data dapat menjadi tidak normal, sehingga memengaruhi interpretasi statistik, termasuk uji Ancova. Outliers juga dapat menyebabkan ketidakhomogenan varians antar kelompok, yang dapat menghasilkan kesalahan dalam penentuan signifikansi hasil. Dengan mendeteksi outliers, peneliti dapat mempertimbangkan tindakan korektif, seperti transformasi data atau penggunaan metode analisis yang lebih tahan terhadap ketidaknormalan atau ketidakhomogenan varians. Oleh karena itu, uji asumsi outliers merupakan langkah penting dalam memastikan validitas dan kehandalan hasil dari Ancova serta mendukung interpretasi yang akurat dari dampak variabel kovariat pada variabel terikat. 

Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

### Linearity

[id5]: # "Uji asumsi linearitas pada Ancova adalah langkah evaluasi untuk memastikan bahwa hubungan antara variabel kovariat dan variabel terikat bersifat linier."

Uji asumsi yang ke-2 adalah [linearity][id5]. Uji asumsi linearity bertujuan untuk memeriksa apakah hubungan antara variabel kovariat dan variabel terikat bersifat linier. Asumsi ini penting karena Ancova mengasumsikan bahwa efek variabel kovariat terhadap variabel terikat adalah konstan melintasi semua tingkat variabel kovariat. Jika asumsi ini tidak terpenuhi, hasil Ancova mungkin tidak valid, dan interpretasi dampak variabel kovariat dapat menjadi meragukan. Uji linearitas melibatkan penilaian pola sebaran titik antara variabel kovariat dan variabel terikat, baik melalui metode grafis maupun uji statistik. Jika ditemukan pola non-linear, peneliti dapat mempertimbangkan transformasi data atau penggunaan metode analisis alternatif yang lebih sesuai. Memeriksa asumsi linearitas menjadi langkah kritis dalam memastikan keakuratan hasil Ancova serta mendukung kesimpulan yang valid terkait pengaruh variabel kovariat pada variabel terikat.

Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

### Homogeneity of regression slopes

[id6]: # "Uji asumsi homogeneity of regression slopes pada Ancova digunakan untuk memeriksa apakah hubungan antara variabel kovariat dan variabel terikat memiliki kemiringan yang seragam di antara kelompok perlakuan."

Uji asumsi yang ke-3 adalah [homogeneity of regression slopes][id6]. Uji asumsi ini bertujuan untuk untuk memastikan bahwa pengaruh variabel kovariat terhadap variabel terikat memiliki kemiringan yang seragam di antara kelompok perlakuan yang berbeda. Jika hubungan tersebut tidak seragam, ini dapat menunjukkan bahwa efek kovariat bervariasi di antara kelompok perlakuan, yang dapat mengancam validitas analisis Ancova. Oleh karena itu, uji ini membantu memastikan bahwa asumsi homogenitas regresi terpenuhi sebelum melanjutkan analisis Ancova.

Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

### Normality of residuals

[id7]: # "Uji normality of residuals pada Ancova adalah pemeriksaan terkait sejauh mana residu dari model regresi memiliki distribusi normal. Hal ini penting karena analisis inferensial bergantung pada asumsi distribusi normal pada residu untuk hasil yang valid."

Uji asumsi yang ke-4 adalah [normality of residuals][id7]. Uji asumsi ini bertujuan untuk memeriksa sejauh mana residu dari model regresi memiliki distribusi normal. Residu yang memiliki distribusi normal menunjukkan bahwa asumsi normalitas terpenuhi, sehingga hasil analisis Ancova dapat diandalkan. Normality of residuals menjadi penting karena analisis inferensial, seperti uji hipotesis dan interval kepercayaan, membutuhkan asumsi distribusi normal pada residu. Jika distribusi residu tidak normal, hal ini dapat memengaruhi validitas hasil dan interpretasi analisis Ancova. Oleh karena itu, uji normality of residuals membantu memastikan bahwa asumsi distribusi normal pada residu terpenuhi untuk hasil analisis yang lebih akurat.

Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

### Homogeneity of variances

[id8]: # "Uji homogeneity of variances pada Ancova adalah pemeriksaan terkait apakah variabilitas residu dari model regresi seragam di semua tingkat variabel bebas kategorikal."

Uji asumsi yang ke-5 adalah [homogeneity of variances][id8]. Uji asumsi ini bertujuan untuk memastikan bahwa variabilitas dari residu regresi seragam di seluruh kelompok perlakuan. Homogenitas varian merupakan asumsi kritis yang perlu dipenuhi agar hasil analisis ANCOVA dapat diandalkan. Jika terdapat perbedaan yang signifikan dalam variabilitas antar kelompok perlakuan, hal ini dapat mempengaruhi validitas interpretasi hasil dan kesimpulan yang diambil dari analisis tersebut. Oleh karena itu, uji ini bertujuan untuk memverifikasi apakah homogenitas varian dapat diasumsikan, sehingga memastikan keabsahan hasil analisis ANCOVA.

Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

> Bagaimana jika salah satu atau beberapa uji asumsi tidak terpenuhi? Kita akan bahas pada tulisan selanjutnya.
{: .prompt-tip }

## Ancova satu jalur

Setelah semua uji asumsi terpenuhi, selanjutnya adalah melakukan perhitungan Ancova. Langkah-langkah Ancova pada SPSS adalah sebagai berikut.

## Interpretasi hasil

XX