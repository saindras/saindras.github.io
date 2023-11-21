---
layout: post
title: Ancova satu jalur menggunakan SPSS
categories: [Statistik, Ancova]
tags: [statistik, ancova]
date: 2023-11-17 10:35 +0700
---

## Pendahuluan

Pada tulisan sebelumnya terkait [Analysis of Covariance (Ancova)](https://saindras.github.io/posts/ancova/){:target="\_blank"}, telah dijelaskan bahwa Ancova merupakan salah satu metode statistik gabungan dari Anova dan Regresi untuk membandingkan rata-rata antara dua atau lebih kelompok dengan mempertimbangkan pengaruh variabel bebas yang disebut sebagai covariate. Salah satu tool statistik yang dapat digunakan untuk melakukan perhitungan Ancova adalah [_Statistical Package for the Social Sciences_ (SPSS)][id1] versi 25.

[id1]: ## "SPSS merupakan perangkat lunak statistik yang digunakan untuk analisis data. Dikembangkan oleh IBM, SPSS menyediakan fitur manajemen data, analisis statistik deskriptif, uji hipotesis, analisis regresi, analisis faktor, visualisasi data, dan pembuatan laporan. Digunakan di berbagai bidang, SPSS membantu dalam pengambilan keputusan berdasarkan analisis statistik."

## Contoh deskripsi penelitian

[id2]: ## "Virtual Learning Environments (VLEs) adalah platform pembelajaran online yang memfasilitasi akses terstruktur ke materi pembelajaran dan interaksi antar peserta didik. Dengan fitur-fitur interaktif, evaluasi online, dan kemampuan kolaborasi, VLEs menjadi kunci dalam mendukung pembelajaran jarak jauh. Contohnya termasuk Moodle, Blackboard, dan Canvas."

Seorang peneliti ingin mengetahui pengaruh dari suatu [_Virtual Learning Environments_ (VLEs)][id2] terhadap prestasi belajar peserta didik pada mata kuliah Jaringan Komputer. Pengaruh tersebut dikontrol oleh suatu co-variabel (covariate) pretest. Oleh karena itu, peneliti merancang suatu penelitian eksperimen semu _(quasi-experiment)_ dengan melibatkan kelas kontrol dan kelas eksperimen. Kelas kontrol adalah kelas yang menggunakan Virtual Learning Environments existing, contohnya menggunakan Moodle dengan suplemen video pembelajaran dan simulator Cisco-PT. Sedangkan, kelas eksperimen menggunakan Moodle dan media pembelajaran inovatif seperti _Virtual Lab Network Simulation_ (Vilanets).

Sampai di sini, kita mengetahui ada 3 kelas dalam penelitian tersebut. Kelas ke-1 dinamakan VLE1 (VLEs dengan suplemen video), kelas ke-2 dinamakan VLE2 (VLEs dengan suplemen Cisco-PT), dan kelas ke-3 dinamakan VLE3 (VLEs dengan suplemen Vilanets). Kelas-kelas tersebut nantinya akan menjadi kelompok/dimensi di dalam variabel bebas Ancova. Jika menggunakan 3 kelas (atau lebih), maka akan ada kemungkinan perhitungan akan dilanjutkan ke _post-hoc test_ ketika terdapat pengaruh antara VLEs dan prestasi belajar.

Karena ini adalah penelitian kuantitatif di mana tujuannya adalah menguji teori, teori baru yang diajukan harus dikontruksi. Misalnya, peneliti ingin menguji teori VLEs. Oleh karena itu, disarankan ada teori baru turunan dari VLEs. Peneliti mengajukan teori bernama _Advanced VLEs_. Apabila dikaitkan dengan 3 kelas sebelumnya, dikontruksi teori sebagai berikut. VLE1 mewakili teori `Beginner VLEs`, VLE2 mewakili teori `Intermediate VLEs`, dan VLE3 mewakili teori `Advanced VLEs`.

## Contoh tujuan penelitian

Tujuan penelitian tersebut adalah sebagai berikut.

1. Peneliti ingin menemukan pengaruh antara VLEs dan prestasi belajar yang dikontrol oleh pretest.
2. Peneliti ingin menemukan perbedaan antara 3 kelompok VLEs (beginner, intermediate, dan advanced VLEs) terhadap prestasi belajar yang dikontrol oleh pretest.

## Variabel-variabel dan tipe data

Variabel-variabel penelitiannya adalah sebagai berikut.

1. Variabel bebas _(independent variable)_: VLEs dengan tiga kelompok (beginner, intermediate, dan advanced VLEs), selanjutnya dinamakan VLE1, VLE2, dan VLE3. Tipe datanya adalah kategorikal di mana 1 mewakili VLE1, 2 mewakili VLE2, dan 3 mewakili VLE3.
2. Variabel terikat _(dependent variable)_: prestasi belajar (posttest). Tipe datanya adalah numerikal berkisar antara 0 - 100.
3. Co-variabel _(covariate)_: pretest. Tipe datanya adalah numerikal berkisar antara 0 - 100.

## Diagram konstelasi dan hipotesis penelitian

Diagram konstelasi menunjukkan hubungan antar variabel, seperti pada Gambar 1. Hubungan tersebut memandu peneliti untuk menentukan hipotesis-hipotesis penelitian dalam rangka tercapainya tujuan-tujuan penelitan.

![Diagram konstelasi light](1Flwpoxk-rumUw5Au4j49njcV2e8sqx5E){: .light .w-75 }
![Diagram konstelasi dark](1Fluuseg7U94KWkKTHBzwY7ZlfUpgGBT4){: .dark .w-75 }
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
2. Data view: masukkan (copy/paste) data ke sel yang bersesuaian.

Download dataset:

[![Static Badge](https://img.shields.io/badge/DOI-10.6084%2Fm9.figshare.24580801-blue)](https://doi.org/10.6084/m9.figshare.24580801){:target="\_blank"}

> Ubah terlebih dahulu data pada kolom VLEs mengikuti `values` pada variable view. Contoh: VLE1 ubah ke nilai `1`, VLE2 ubah ke nilai `2`, dan VLE3 ubah ke nilai `3`.
> {: .prompt-tip }

> Dataset tersebut telah dipublikasi dan dilindungi hak cipta. Silakan digunakan sebagaimana mestinya dengan tetap melakukan sitasi apabila digunakan.
> {: .prompt-warning }

<details>
  <summary>Klik di sini untuk melihat contoh tampilan inisiasi data pada SPSS.</summary>
  
  <img src="1FLLMP0kCMeB20bDE5dp3sRs46uncPO6-">

</details>

## Uji asumsi

Adapun [uji asumsi][id3] sebelum melakukan perhitungan Ancova adalah uji asumsi _ouliers_, _linearity_, _homogeneity of regression slopes_, _normality of residuals_, dan _homogeneity of variances_.

[id3]: ## "Uji asumsi dilakukan untuk memastikan bahwa data penelitian memenuhi prasyarat yang diperlukan oleh analisis Ancova. Memeriksa asumsi-asumsi ini penting karena kesalahan dalam asumsi dapat mempengaruhi keandalan dan validitas hasil analisis Ancova. Jika data tidak memenuhi asumsi-asumsi tersebut, maka mungkin perlu mencari alternatif atau menerapkan transformasi data untuk memenuhi asumsi tersebut sebelum menggunakan Ancova."

### _Outliers_

[id4]: ## "Uji asumsi *outliers* adalah pemeriksaan terhadap data terkait ada atua tidaknya observasi yang secara signifikan berbeda dari pola umum dalam data Anda. Outlier dapat mempengaruhi hasil analisis dan memeriksa asumsi tentang distribusi normalitas dan homogenitas varians."

Uji asumsi yang pertama adalah [_outliers_][id4]. Uji asumsi _outliers_ berfungsi untuk mengidentifikasi adanya nilai-nilai ekstrim dalam dataset. _Outliers_ dapat memengaruhi kehandalan hasil analisis Ancova, terutama terkait dengan dua asumsi utama: normalitas dan homogenitas varians. Jika ada outlier, distribusi data dapat menjadi tidak normal, sehingga memengaruhi interpretasi statistik, termasuk uji Ancova. _Outliers_ juga dapat menyebabkan ketidakhomogenan varians antar kelompok, yang dapat menghasilkan kesalahan dalam penentuan signifikansi hasil. Dengan mendeteksi _outliers_, peneliti dapat mempertimbangkan tindakan korektif, seperti transformasi data atau penggunaan metode analisis yang lebih tahan terhadap ketidaknormalan atau ketidakhomogenan varians. Oleh karena itu, uji asumsi _outliers_ merupakan langkah penting dalam memastikan validitas dan kehandalan hasil dari Ancova serta mendukung interpretasi yang akurat dari dampak variabel kovariat pada variabel terikat. Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

#### Prosedur input

1. Masuk ke menu SPSS `Analyze > General Linear Model > Univariate`. Pada jendela `Univariate`, sesuaikan isiannya sebagai berikut.
   1. Dependent Variable: `posttest`.
   2. Fixed Factor(s): `VLEs`.
   3. Covariate(s): `pretest`.
2. Klik tombol `Save`, akan muncul jendela `Univariate: Save`. Sesuaikan isiannya sebagai berikut.
   1. Residuals: `Studentized` (dicentang)
3. Klik tombol `Continue`, kemudian klik tombol `OK`. Hasilnya akan muncul pada jendela `output` dan `dataset`. Abaikan dulu jendela `output` dan fokus pada jendela `dataset`.
4. Pada jendela `dataset`, muncul kolom baru bernama `SRE_1`. Kemudian pilih menu `Transform > Compute Variable`. Pada jendela `Compute Variable`, sesuaikan isiannya sebagai berikut.
   1. Target Variable: `ABS_SRE_1`
   2. Numeric Expression: `ABS(SRE_1)`
5. Klik tombol `OK` dan kembali ke jendela `dataset`. Muncul kolom baru bernama `ABS_SRE_1`.
6. Pilih menu `Graphs > Chart Builder`. Apabila muncul jendela dialog, klik `OK`.
7. Pada jendela `Chart Builder`, tab `Gallery > Choose from:`, pilih `Boxplot`. Klik 2x pada gambar `1-D Boxplot`, maka akan muncul pada kotak `Chart preview uses example data`.
8. Masih di jendela `Chart Builder`, pada kotak `Variables`, lakukan drag and drop variabel `ABS_SRE_1` ke `X-Axis?` yang terletak di kotak `Chart preview uses example data`, kemudian Klik tombol `OK`.
9. Hasil akan muncul pada jendela `output` berupa gambar boxplot.

#### Tampilan output

<details>
  <summary>Klik di sini untuk melihat output.</summary>
  
  <img src="1G9ptFRtRJdqLnpjCv08YuDLCAaV7XCDG">

</details>

#### Interpretasi hasil

Pada boxplot, terlihat hanya ada 1 data yang muncul dengan nilai _Absolute Studentized Residual_ (ABS_SRE) = 2. Data ini bukanlah outlier, karena data yang mengandung outlier adalah ketika nilai ABS_SRE lebih besar dari 3 (SRE > 3)[^footnote]. Simpulannya, data tidak mengandung outlier sehingga asumsi ini terpenuhi.

### _Linearity_

[id5]: ## "Uji asumsi linearitas pada Ancova adalah langkah evaluasi untuk memastikan bahwa hubungan antara variabel kovariat dan variabel terikat bersifat linier."

Uji asumsi yang ke-2 adalah [_linearity_][id5]. Uji asumsi _linearity_ bertujuan untuk memeriksa apakah hubungan antara variabel kovariat dan variabel terikat bersifat linier. Asumsi ini penting karena Ancova mengasumsikan bahwa efek variabel kovariat terhadap variabel terikat adalah konstan melintasi semua tingkat variabel kovariat. Jika asumsi ini tidak terpenuhi, hasil Ancova mungkin tidak valid, dan interpretasi dampak variabel kovariat dapat menjadi meragukan. Uji linearitas melibatkan penilaian pola sebaran titik antara variabel kovariat dan variabel terikat, baik melalui metode grafis maupun uji statistik. Jika ditemukan pola non-linear, peneliti dapat mempertimbangkan transformasi data atau penggunaan metode analisis alternatif yang lebih sesuai. Memeriksa asumsi linearitas menjadi langkah kritis dalam memastikan keakuratan hasil Ancova serta mendukung kesimpulan yang valid terkait pengaruh variabel kovariat pada variabel terikat. Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

#### Prosedur input

1. Masuk ke menu SPSS `Analyze > Regression > Linear`. Pada jendela `Linear Regression`, sesuaikan isiannya sebagai berikut.
   1. Dependent: `postest`.
   2. Independent(s): `pretest`.
2. Klik tombol `OK`. Akan muncul hasilnya pada jendela `output`. Fokus pada tabel `Model Summary` dan `Coefficients`.
3. Untuk menghasilkan grafik linearitas antar variabel, masuk ke menu `Graphs > Legacy Dialogs > Scatter/Dot`.
4. Pilih `Simple Scatter`, kemudian klik tombol `Define`. Pada jendela `Simple Scatterplot`, sesuaikan isiannya sebagai berikut.
   1. Y Axis: `postest`.
   2. X Axis: `pretest`.
5. Klik tombol `OK`, akan muncul hasil berupa _scatter plot_ pada jendela `output`.
6. Untuk memunculkan garis linear di gambar _scatter plot_, pada jendela `output`, klik 2 kali di gambar _scatter plot_ untuk memunculkan jendela `Chart Editor` kemudian klik tombol `Add Fit Line at Total` yang terletak pada menu bar di atas gambar, akan muncul jendela `Properties`.
7. Pada jendela `Properties`, tab `Fit Line`, kotak `Fit Method`, pilih `Linear`. Kemudian klik tombol `Close`, dan tutup jendela `Chart Editor`. Akan muncul gambar _scatter plot_ berisikan garis linear dan nilai _R<sup>2</sup>_-nya.

#### Tampilan output

<details>
  <summary>Klik di sini untuk melihat output tabel.</summary>
  
  <img src="1Gh_Ghq0_CVMMm0X6632ltOsoL7tk9qC7">

</details>

<details>
  <summary>Klik di sini untuk melihat output <i>scatter plot</i>.</summary>
  
  <img src="1Gm3p-WcfLYXZNL16eIGyzyNsUdWSb70v">

</details>

#### Interpretasi hasil

Pada tabel `Model Summary`, terlihat bahwa nilai _R<sup>2</sup>_ = 0,612 yang artinya model linier dinilai cukup baik untuk memperkirakan pengaruh dengan persentasenya sebesar 61,2%. Pada tabel `Coefficients`, terlihat bahwa nilai koefisien sebesar 0,722 dengan _Sig._ sebesar 0,00. Jika nilai koefisien tidak nol dan _Sig._ kurang dari 0,05, maka terdapat hubungan linier antara kovariat dan variabel terikat[^fn-nth-2]. Oleh karena itu, uji asumsi _linearity_ terpenuhi.

Hal ini diperjelas dengan gambar _scatter plot_, di mana terlihat data tersebar acak. Data pada _scatter plot_ yang telihat acak (tidak membentuk pola tertentu) menandakan hubungan antara kovariat dan variabel terikat adalah linear[^fn-nth-3].

### _Homogeneity of regression slopes_

[id6]: ## "Uji asumsi *homogeneity of regression slopes* pada Ancova digunakan untuk memeriksa apakah hubungan antara variabel kovariat dan variabel terikat memiliki kemiringan yang seragam di antara kelompok perlakuan."

Uji asumsi yang ke-3 adalah [_homogeneity of regression slopes_][id6]. Uji asumsi ini bertujuan untuk untuk memastikan bahwa pengaruh variabel kovariat terhadap variabel terikat memiliki kemiringan yang seragam di antara kelompok perlakuan yang berbeda. Jika hubungan tersebut tidak seragam, ini dapat menunjukkan bahwa efek kovariat bervariasi di antara kelompok perlakuan, yang dapat mengancam validitas analisis Ancova. Oleh karena itu, uji ini membantu memastikan bahwa asumsi homogenitas regresi terpenuhi sebelum melanjutkan analisis Ancova. Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

#### Prosedur input

1. Masuk ke menu SPSS `Analyze > General Linear Model > Univariate`. Pada jendela `Univariate`, sesuaikan isiannya sebagai berikut.
   1. Dependent Variable: `posttest`.
   2. Fixed Factor(s): `VLEs`.
   3. Covariate(s): `pretest`.
2. Klik tombol `Model`, akan muncul jendela `Univariate: Model`, sesuaikan isiannya sebagai berikut.
   1. Specify Model: `build terms`.
   2. Factors & Covariates: `VLEs`, `pretest`.
   3. Model: `VLEs`, `pretest`, `pretest*VLEs`.
3. Klik tombol `Continue`.
4. Klik tombol `Save`, akan muncul jendela `Univariate: Save`. Sesuaikan isiannya sebagai berikut.
   1. Residuals: `Studentized` (hilangkan centang). Jika secara default tidak dicentang, maka abaikan langkah ini.
5. Klik tombol `OK`, akan muncul hasil berupa tabel `Tests of Between-Subjects Effects` pada jendela `output`.
6. Untuk menghasilkan grafik linearitas antar variabel, masuk ke menu `Graphs > Legacy Dialogs > Scatter/Dot`.
7. Pilih `Simple Scatter`, kemudian klik tombol `Define`. Pada jendela `Simple Scatterplot`, sesuaikan isiannya sebagai berikut.
   1. Y Axis: `postest`.
   2. X Axis: `pretest`.
   3. Set Markers by: `VLEs`.
8. Klik tombol `OK`, akan muncul hasil berupa _scatter plot_ pada jendela `output`.
9. Untuk memunculkan garis linear pada masing-masing kelompok variabel bebas di gambar _scatter plot_, pada jendela `output`, klik 2 kali di gambar _scatter plot_ untuk memunculkan jendela `Chart Editor` kemudian klik tombol `Add Fit Line at Subgroups` yang terletak pada menu bar di atas gambar, akan muncul jendela `Properties`.
10. Pada jendela `Properties`, tab `Fit Line`, kotak `Fit Method`, pilih `Linear`. Kemudian klik tombol `Close`, dan tutup jendela `Chart Editor`. Akan muncul gambar _scatter plot_ berisikan garis linear dan nilai _R<sup>2</sup>_ untuk masing-masing kelompok pada variabel bebas.

<details>
  <summary>Klik di sini untuk melihat detail langkah nomor 2.</summary>
  
  <img src="1HtEcVKyJOoc1l-e0r0lSCutEXpi8eEEi">

</details>

#### Tampilan output

<details>
  <summary>Klik di sini untuk melihat output tabel.</summary>
  
  <img src="1I01XHlL5c4SECdvbSm5z_kM_So2_OL5k">

</details>

<details>
  <summary>Klik di sini untuk melihat output <i>scatter plot</i>.</summary>
  
  <img src="1I3pk56-p7HXbfyyeZb7cYMamh8Rj8mk8">

</details>

#### Interpretasi hasil

Pada tabel `Tests of Between-Subjects Effects`, terlihat nilai _F_ = 0,028 dan nilai _Sig._ = 0,973 pada baris `VLEs*pretest`. Jika nilai _Sig._ lebih besar dari 0,05, maka tidak ada perbedaan kemiringan secara signifikan di antara kelompok perlakuan[^fn-nth-3]. Hal ini diperjelas dengan gambar _scatter plot_, di mana terlihat garis linear antar variabel cenderung paralel yang menunjukkan tidak ada perbedaan kemiringan antar kelompok dalam variabel bebas[^fn-nth-3]. Simpulannya, kemiringan garis ketiga kelompok sangat mirip, menunjukkan bahwa hubungan antara posttest dan pretest sangat mirip pada ketiga kelompok. Oleh karena itu, asumsi ini terpenuhi.

Jika asumsi homogenitas lereng regresi terpenuhi, maka F-statistik yang dihasilkan dapat diasumsikan memiliki distribusi F yang sesuai[^fn-nth-3]. Sebaliknya, jika asumsinya tidak terpenuhi, maka artinya statistik F yang dihasilkan dievaluasi berdasarkan distribusi yang berbeda dari distribusi sebenarnya. Akibatnya, tingkat kesalahan tes Tipe I meningkat dan kemampuan untuk mendeteksi efek tidak maksimal. Hal ini terutama berlaku ketika ukuran kelompok tidak sama dan ketika kemiringan regresi standar berbeda lebih dari 0,4.

> Jika asumsi _homogeneity of regression slopes_ tidak terpenuhi, maka dapat memodelkan variasi ini secara eksplisit menggunakan model linier bertingkat _(multilevel linear models)_[^fn-nth-3]
> {: .prompt-info }

> Example line for prompt.
> {: .prompt-info }

### Normality of residuals

[id7]: ## "Uji normality of residuals pada Ancova adalah pemeriksaan terkait sejauh mana residu dari model regresi memiliki distribusi normal. Hal ini penting karena analisis inferensial bergantung pada asumsi distribusi normal pada residu untuk hasil yang valid."

Uji asumsi yang ke-4 adalah [normality of residuals][id7]. Uji asumsi ini bertujuan untuk memeriksa sejauh mana residu dari model regresi memiliki distribusi normal. Residu yang memiliki distribusi normal menunjukkan bahwa asumsi normalitas terpenuhi, sehingga hasil analisis Ancova dapat diandalkan. Normality of residuals menjadi penting karena analisis inferensial, seperti uji hipotesis dan interval kepercayaan, membutuhkan asumsi distribusi normal pada residu. Jika distribusi residu tidak normal, hal ini dapat memengaruhi validitas hasil dan interpretasi analisis Ancova. Oleh karena itu, uji normality of residuals membantu memastikan bahwa asumsi distribusi normal pada residu terpenuhi untuk hasil analisis yang lebih akurat.

Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

### Homogeneity of variances

[id8]: ## "Uji homogeneity of variances pada Ancova adalah pemeriksaan terkait apakah variabilitas residu dari model regresi seragam di semua tingkat variabel bebas kategorikal."

Uji asumsi yang ke-5 adalah [homogeneity of variances][id8]. Uji asumsi ini bertujuan untuk memastikan bahwa variabilitas dari residu regresi seragam di seluruh kelompok perlakuan. Homogenitas varian merupakan asumsi kritis yang perlu dipenuhi agar hasil analisis ANCOVA dapat diandalkan. Jika terdapat perbedaan yang signifikan dalam variabilitas antar kelompok perlakuan, hal ini dapat mempengaruhi validitas interpretasi hasil dan kesimpulan yang diambil dari analisis tersebut. Oleh karena itu, uji ini bertujuan untuk memverifikasi apakah homogenitas varian dapat diasumsikan, sehingga memastikan keabsahan hasil analisis ANCOVA.

Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

> Bagaimana jika salah satu atau beberapa uji asumsi tidak terpenuhi? Kita akan bahas pada tulisan selanjutnya.
> {: .prompt-tip }

## Ancova satu jalur

Setelah semua uji asumsi terpenuhi, selanjutnya adalah melakukan perhitungan Ancova. Langkah-langkah Ancova pada SPSS adalah sebagai berikut.

## Interpretasi hasil

_(dalam proses)_

## Referensi

[^footnote]: Pardoe, I. (2021). _Applied regression modeling_ (3rd ed). Wiley.
[^fn-nth-2]: Klopper, J. (2022). _Analysis of covariance using Python_. YouTube. <https://www.youtube.com/watch?v=FhZB1oGVrYc>{:target="\_blank"}.
[^fn-nth-3]: Field, A. (2017). _Discovering Statistics Using IBM SPSS Statistics_ (5th ed.). SAGE Publications.
