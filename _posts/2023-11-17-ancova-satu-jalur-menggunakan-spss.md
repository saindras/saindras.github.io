---
layout: post
title: Ancova satu jalur menggunakan SPSS
categories:
- Statistik
- Ancova
tags:
- statistik
- ancova
date: 2023-11-17 10:35 +0700
---

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.10217507.svg)](https://doi.org/10.5281/zenodo.10217507){:target="blank"}

## Pendahuluan

Pada tulisan sebelumnya terkait [Analysis of Covariance (Ancova)](https://saindras.github.io/posts/ancova/){:target="_blank"}, telah dijelaskan bahwa Ancova merupakan salah satu metode statistik gabungan dari Anova dan Regresi untuk membandingkan rata-rata antara dua atau lebih kelompok dengan mempertimbangkan pengaruh variabel bebas yang disebut sebagai covariate. Salah satu tool statistik yang dapat digunakan untuk melakukan perhitungan Ancova adalah [Statistical Package for the Social Sciences (SPSS)][id1] versi 25.

[id1]: ## "SPSS merupakan perangkat lunak statistik yang digunakan untuk analisis data. Dikembangkan oleh IBM, SPSS menyediakan fitur manajemen data, analisis statistik deskriptif, uji hipotesis, analisis regresi, analisis faktor, visualisasi data, dan pembuatan laporan. Digunakan di berbagai bidang, SPSS membantu dalam pengambilan keputusan berdasarkan analisis statistik."

## Contoh deskripsi penelitian

[id2]: ## "Virtual Learning Environments (VLEs) adalah platform pembelajaran online yang memfasilitasi akses terstruktur ke materi pembelajaran dan interaksi antar peserta didik. Dengan fitur-fitur interaktif, evaluasi online, dan kemampuan kolaborasi, VLEs menjadi kunci dalam mendukung pembelajaran jarak jauh. Contohnya termasuk Moodle, Blackboard, dan Canvas."

Seorang peneliti ingin mengetahui pengaruh dari suatu [Virtual Learning Environments (VLEs)][id2] terhadap prestasi belajar peserta didik pada mata kuliah Jaringan Komputer. Pengaruh tersebut dikontrol oleh suatu co-variabel *(covariate)* pretest. Oleh karena itu, peneliti merancang suatu penelitian eksperimen semu (*quasi-experiment*) dengan melibatkan kelas kontrol dan kelas eksperimen. Kelas kontrol adalah kelas yang menggunakan Virtual Learning Environments existing, contohnya menggunakan Moodle dengan suplemen video pembelajaran dan simulator Cisco-PT. Sedangkan, kelas eksperimen menggunakan Moodle dan media pembelajaran inovatif seperti Virtual Lab Network Simulation (Vilanets).

Sampai di sini, kita mengetahui ada 3 kelas dalam penelitian tersebut. Kelas ke-1 dinamakan VLE1 (VLEs dengan suplemen video), kelas ke-2 dinamakan VLE2 (VLEs dengan suplemen Cisco-PT), dan kelas ke-3 dinamakan VLE3 (VLEs dengan suplemen Vilanets). Kelas-kelas tersebut nantinya akan menjadi kelompok/dimensi di dalam variabel bebas Ancova. Jika menggunakan 3 kelas (atau lebih), maka akan ada kemungkinan perhitungan akan dilanjutkan ke post-hoc test ketika terdapat pengaruh antara VLEs dan prestasi belajar.

Karena ini adalah penelitian kuantitatif di mana tujuannya adalah menguji teori, teori baru yang diajukan harus dikontruksi. Misalnya, peneliti ingin menguji teori VLEs. Oleh karena itu, disarankan ada teori baru turunan dari VLEs. Peneliti mengajukan teori bernama Advanced VLEs. Apabila dikaitkan dengan 3 kelas sebelumnya, dikontruksi teori sebagai berikut. VLE1 mewakili teori `Beginner VLEs`, VLE2 mewakili teori `Intermediate VLEs`, dan VLE3 mewakili teori `Advanced VLEs`.

## Contoh tujuan penelitian

Tujuan penelitian tersebut adalah sebagai berikut.

1. Peneliti ingin menemukan pengaruh antara VLEs dan prestasi belajar yang dikontrol oleh pretest.
2. Peneliti ingin menemukan perbedaan antara 3 kelompok VLEs (beginner, intermediate, dan advanced VLEs) terhadap prestasi belajar yang dikontrol oleh pretest.

## Variabel-variabel dan tipe data

Variabel-variabel penelitiannya adalah sebagai berikut.

1. Variabel bebas (independent variable): VLEs dengan tiga kelompok (beginner, intermediate, dan advanced VLEs), selanjutnya dinamakan VLE1, VLE2, dan VLE3. Tipe datanya adalah kategorikal di mana 1 mewakili VLE1, 2 mewakili VLE2, dan 3 mewakili VLE3.
2. Variabel terikat (dependent variable): prestasi belajar (posttest). Tipe datanya adalah numerikal berkisar antara 0 - 100.
3. Co-variabel (covariate): pretest. Tipe datanya adalah numerikal berkisar antara 0 - 100.

## Diagram konstelasi dan hipotesis penelitian

Diagram konstelasi menunjukkan hubungan antar variabel, seperti pada Gambar 1. Hubungan tersebut memandu peneliti untuk menentukan hipotesis-hipotesis penelitian dalam rangka tercapainya tujuan-tujuan penelitan.

![Diagram konstelasi light](1Flwpoxk-rumUw5Au4j49njcV2e8sqx5E){: .light .w-75 }
![Diagram konstelasi dark](1Fluuseg7U94KWkKTHBzwY7ZlfUpgGBT4){: .dark .w-75 }
Gambar 1. Diagram konstelasi antar variabel

Adapun hipotesis-hipotesis penelitian adalah sebagai berikut.

1. H1: Terdapat pengaruh yang signifikan VLEs terhadap prestasi belajar dikontrol oleh pretest.
2. H2: Terdapat perbedaan signifikan antara VLE1, VLE2, dan VLE3 terhadap prestasi belajar dikontrol oleh pretest.
    1. H2.1: Terdapat perbedaan signifikan antara VLE1 dan VLE2 terhadap prestasi belajar dikontrol oleh pretest.
    2. H2.2: Terdapat perbedaan signifikan antara VLE1 dan VLE3 terhadap prestasi belajar dikontrol oleh pretest.
    3. H2.3: Terdapat perbedaan signifikan antara VLE2 dan VLE3 terhadap prestasi belajar dikontrol oleh pretest.

## Inisiasi data

Buka SPSS, kemudian akan muncul 2 jendela: `dataset` dan `output`. Buka jendela dataset, kemudian konfigurasi sebagai berikut.

1. Variable view:
   1. Name: `VLEs`; Decimals: `0`; Values: `{1, VLE1; 2, VLE2; 3, VLE3}`; Measure: `Nominal`.
   2. Name: `pretest`; Measure: `Scale`.
   3. Name: `posttest`; Measure: `Scale`.
2. Data view: masukkan (copy/paste) data ke sel yang bersesuaian.

Download dataset:

[![Static Badge](https://img.shields.io/badge/DOI-10.6084%2Fm9.figshare.24580801-blue)](https://doi.org/10.6084/m9.figshare.24580801){:target="_blank"}

> Ubah terlebih dahulu data pada kolom VLEs mengikuti `values` pada variable view. Contoh: VLE1 ubah ke nilai `1`, VLE2 ubah ke nilai `2`, dan VLE3 ubah ke nilai `3`.
{: .prompt-tip }

> Dataset tersebut telah dipublikasi dan dilindungi hak cipta. Silakan digunakan sebagaimana mestinya dengan tetap melakukan sitasi apabila digunakan.
{: .prompt-warning }

<details>
  <summary>Klik di sini untuk melihat contoh tampilan inisiasi data pada SPSS.</summary>
  
  <img src="1FLLMP0kCMeB20bDE5dp3sRs46uncPO6-">

</details>

## Uji asumsi

[id9]: ## "Pada contoh penelitian, tipe data yang digunakan pada variabel bebas adalah kategorikal degan tiga kategori/kelompok/dimensi/faktor. Sedangkan tipe data variabel terikat dan co-variabel adalah numerikal dengan skala 0 sampai dengan 100."

[id10]: ## "Responden dalam tiap kelompok pada variabel bebas harus berbeda. Misalnya, kelompok VLE1 adalah peserta didik kelas XI-A, kelompok VLE2 adalah peserta didik kelas XI-B, dan kelompok VLE3 adalah peserta didik kelas XI-C."

[id11]: ## "Proses penilaian pre-test dan post-test harus berbeda dari segi waktu. Pre-test sebagai co-variabel dilakukan pada awal pertemuan. Sedangkan post-test sebagai variabel terikat dilakukan di akhir pertemuan. Hal ini akan memberikan independensi antara co-variabel dan variabel terikat."

[id12]: ## "Desain penelitian quasi-experimental pretest-posttest control group adalah suatu pendekatan penelitian yang mencoba untuk mengevaluasi efek dari suatu perlakuan atau intervensi tanpa adanya randomisasi penuh seperti pada desain eksperimen murni. Dalam desain ini, peneliti mengumpulkan data sebelum dan sesudah perlakuan dari kelompok perlakuan (yang menerima intervensi atau perlakuan) dan kelompok kontrol (yang tidak menerima intervensi)."

[id3]: ## "Uji asumsi dilakukan untuk memastikan bahwa data penelitian memenuhi prasyarat yang diperlukan oleh analisis Ancova. Memeriksa asumsi-asumsi ini penting karena kesalahan dalam asumsi dapat mempengaruhi keandalan dan validitas hasil analisis Ancova. Jika data tidak memenuhi asumsi-asumsi tersebut, maka mungkin perlu mencari alternatif atau menerapkan transformasi data untuk memenuhi asumsi tersebut sebelum menggunakan Ancova."

Terdapat dua jenis [uji asumsi][id3] sebelum melakukan perhitungan Ancova yakni asumsi dasar dan tambahan. Uji asumsi dasar meliputi [tipe data dari masing-masing variabel][id9], [observasi yang independen antar kelompok dalam variabel bebas][id10], dan [independensi antara co-variabel dan variabel terikat][id11]. Seluruh uji asumsi dasar akan terpenuhi apabila menggunakan desain penelitian [quasi-experimental pretest-posttest control group][id12]. Sedangkan uji asumsi tambahan dalam Ancova ada 5 yakni, uji asumsi *outliers*, *linearity*, *homogeneity of regression slopes*, *normality of residuals*, dan *homogeneity of variances*. Uji asumsi dasar dan uji asumsi tambahan wajib dipenuhi sebelum melakukan analisis Ancova guna mengurangi bias hasil penelitian. Berikut prosedur uji asumsi menggunakan SPSS terutama pada kelima uji asumsi tambahan.

### *Outliers*

[id4]: ## "Uji asumsi outliers adalah pemeriksaan terhadap data terkait ada atua tidaknya observasi yang secara signifikan berbeda dari pola umum dalam data Anda. Outlier dapat mempengaruhi hasil analisis dan memeriksa asumsi tentang distribusi normalitas dan homogenitas varians."

Uji asumsi yang pertama adalah [*outliers*][id4]. Uji asumsi *outliers* berfungsi untuk mengidentifikasi adanya nilai-nilai ekstrim dalam dataset. *Outliers* dapat memengaruhi kehandalan hasil analisis Ancova, terutama terkait dengan dua asumsi utama: normalitas dan homogenitas varians. Jika ada outlier, distribusi data dapat menjadi tidak normal, sehingga memengaruhi interpretasi statistik, termasuk uji Ancova. *Outliers* juga dapat menyebabkan ketidakhomogenan varians antar kelompok, yang dapat menghasilkan kesalahan dalam penentuan signifikansi hasil. Dengan mendeteksi *outliers*, peneliti dapat mempertimbangkan tindakan korektif, seperti transformasi data atau penggunaan metode analisis yang lebih tahan terhadap ketidaknormalan atau ketidakhomogenan varians. Oleh karena itu, uji asumsi *outliers* merupakan langkah penting dalam memastikan validitas dan kehandalan hasil dari Ancova serta mendukung interpretasi yang akurat dari dampak variabel kovariat pada variabel terikat. Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

#### Prosedur input

1. Masuk ke menu SPSS `Analyze > General Linear Model > Univariate`. Pada jendela `Univariate`, sesuaikan isiannya sebagai berikut.
   1. Dependent Variable: `posttest`.
   2. Fixed Factor(s): `VLEs`.
   3. Covariate(s): `pretest`.
2. Klik tombol `Save`, akan muncul jendela `Univariate: Save`. Sesuaikan isiannya sebagai berikut.
   1. Residuals: `Studentized` (dicentang).
3. Klik tombol `Continue`, kemudian klik tombol `OK`. Hasilnya akan muncul pada jendela `output` dan `dataset`. Abaikan dulu jendela `output` dan fokus pada jendela `dataset`.
4. Pada jendela `dataset`, muncul kolom baru bernama `SRE_1`. Kemudian pilih menu `Transform > Compute Variable`. Pada jendela `Compute Variable`, sesuaikan isiannya sebagai berikut.
   1. Target Variable: `ABS_SRE_1`.
   2. Numeric Expression: `ABS(SRE_1)`.
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

Pada boxplot, terlihat hanya ada 1 data yang muncul dengan nilai Absolute Studentized Residual (ABS_SRE) = 2. Data ini bukanlah outlier, karena data yang mengandung outlier adalah ketika nilai ABS_SRE lebih besar dari 3 (SRE > 3)[^footnote]. Simpulannya, data tidak mengandung outlier sehingga asumsi ini terpenuhi.

> Bagaimana jika terdapat *outlier*? Kita akan bahas pada tulisan selanjutnya.
{: .prompt-tip }

### *Linearity*

[id5]: ## "Uji asumsi linearitas pada Ancova adalah langkah evaluasi untuk memastikan bahwa hubungan antara variabel kovariat dan variabel terikat bersifat linier."

Uji asumsi yang ke-2 adalah [*linearity*][id5]. Uji asumsi linearity bertujuan untuk memeriksa apakah hubungan antara variabel kovariat dan variabel terikat bersifat linier. Asumsi ini penting karena Ancova mengasumsikan bahwa efek variabel kovariat terhadap variabel terikat adalah konstan melintasi semua tingkat variabel kovariat. Jika asumsi ini tidak terpenuhi, hasil Ancova mungkin tidak valid, dan interpretasi dampak variabel kovariat dapat menjadi meragukan. Uji linearitas melibatkan penilaian pola sebaran titik antara variabel kovariat dan variabel terikat, baik melalui metode grafis maupun uji statistik. Jika ditemukan pola non-linear, peneliti dapat mempertimbangkan transformasi data atau penggunaan metode analisis alternatif yang lebih sesuai. Memeriksa asumsi linearitas menjadi langkah kritis dalam memastikan keakuratan hasil Ancova serta mendukung kesimpulan yang valid terkait pengaruh variabel kovariat pada variabel terikat. Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

#### Prosedur input

1. Masuk ke menu SPSS `Analyze > Regression > Linear`. Pada jendela `Linear Regression`, sesuaikan isiannya sebagai berikut.
   1. Dependent: `postest`.
   2. Independent(s): `pretest`.
2. Cek pada bagian model regresi dengan menekan tombol `Model`. Pastikan `Specify Model` adalah `Full factorial`. Klik tombol `Continue`.
3. Klik tombol `OK`. Akan muncul hasilnya pada jendela `output`. Fokus pada tabel `Model Summary` dan `Coefficients`.
4. Untuk menghasilkan grafik linearitas antar variabel, masuk ke menu `Graphs > Legacy Dialogs > Scatter/Dot`.
5. Pilih `Simple Scatter`, kemudian klik tombol `Define`. Pada jendela `Simple Scatterplot`, sesuaikan isiannya sebagai berikut.
   1. Y Axis: `postest`.
   2. X Axis: `pretest`.
6. Klik tombol `OK`, akan muncul hasil berupa *scatter plot* pada jendela `output`.
7. Untuk memunculkan garis linear di gambar *scatter plot*, pada jendela `output`, klik 2 kali di gambar *scatter plot* untuk memunculkan jendela `Chart Editor` kemudian klik tombol `Add Fit Line at Total` yang terletak pada menu bar di atas gambar, akan muncul jendela `Properties`.
8. Pada jendela `Properties`, tab `Fit Line`, kotak `Fit Method`, pilih `Linear`. Kemudian klik tombol `Close`, dan tutup jendela `Chart Editor`. Akan muncul gambar *scatter plot* berisikan garis linear dan nilai *R<sup>2</sup>*-nya.

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

Pada tabel `Model Summary`, terlihat bahwa nilai *R<sup>2</sup>* = 0,612 yang artinya model linier dinilai cukup baik untuk memperkirakan pengaruh dengan persentasenya sebesar 61,2%. Pada tabel `Coefficients`, terlihat bahwa nilai koefisien sebesar 0,722 dengan *Sig.* sebesar 0,00. Jika nilai koefisien tidak nol dan *Sig.* kurang dari 0,05, maka terdapat hubungan linier antara kovariat dan variabel terikat[^fn-nth-2]. Oleh karena itu, uji asumsi linearity terpenuhi.

Hal ini diperjelas dengan gambar *scatter plot*, di mana terlihat data tersebar acak. Data pada *scatter plot* yang telihat acak (tidak membentuk pola tertentu) menandakan hubungan antara kovariat dan variabel terikat adalah linear[^fn-nth-3].

> Bagaimana jika data tidak linier atau uji asumsi *linearity* tidak terpenuhi? Kita akan bahas pada tulisan selanjutnya.
{: .prompt-tip }

### *Homogeneity of regression slopes*

[id6]: ## "Uji asumsi homogeneity of regression slopes pada Ancova digunakan untuk memeriksa apakah hubungan antara variabel kovariat dan variabel terikat memiliki kemiringan yang seragam di antara kelompok perlakuan."

Uji asumsi yang ke-3 adalah [*Homogeneity of regression slopes*][id6]. Uji asumsi ini bertujuan untuk untuk memastikan bahwa pengaruh variabel kovariat terhadap variabel terikat memiliki kemiringan yang seragam di antara kelompok perlakuan yang berbeda. Jika hubungan tersebut tidak seragam, ini dapat menunjukkan bahwa efek kovariat bervariasi di antara kelompok perlakuan, yang dapat mengancam validitas analisis Ancova. Oleh karena itu, uji ini membantu memastikan bahwa asumsi homogenitas regresi terpenuhi sebelum melanjutkan analisis Ancova. Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

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
8. Klik tombol `OK`, akan muncul hasil berupa *scatter plot* pada jendela `output`.
9. Untuk memunculkan garis linear pada masing-masing kelompok variabel bebas di gambar *scatter plot*, pada jendela `output`, klik 2 kali di gambar *scatter plot* untuk memunculkan jendela `Chart Editor` kemudian klik tombol `Add Fit Line at Subgroups` yang terletak pada menu bar di atas gambar, akan muncul jendela `Properties`.
10. Pada jendela `Properties`, tab `Fit Line`, kotak `Fit Method`, pilih `Linear`. Kemudian klik tombol `Close`, dan tutup jendela `Chart Editor`. Akan muncul gambar *scatter plot* berisikan garis linear dan nilai R<sup>2</sup> untuk masing-masing kelompok pada variabel bebas.

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

Pada tabel `Tests of Between-Subjects Effects`, terlihat nilai F = 0,028 dan nilai *Sig.* = 0,973 pada baris `VLEs*pretest`. Jika nilai *Sig.* lebih besar dari 0,05, maka tidak ada perbedaan kemiringan secara signifikan di antara kelompok perlakuan[^fn-nth-3]. Hal ini diperjelas dengan gambar *scatter plot*, di mana terlihat garis linear antar variabel cenderung paralel yang menunjukkan tidak ada perbedaan kemiringan antar kelompok dalam variabel bebas[^fn-nth-3]. Simpulannya, kemiringan garis ketiga kelompok sangat mirip, menunjukkan bahwa hubungan antara posttest dan pretest sangat mirip pada ketiga kelompok. Oleh karena itu, asumsi ini terpenuhi.

Jika asumsi homogenitas lereng regresi terpenuhi, maka F-statistik yang dihasilkan dapat diasumsikan memiliki distribusi F yang sesuai[^fn-nth-3]. Sebaliknya, jika asumsinya tidak terpenuhi, maka artinya statistik F yang dihasilkan dievaluasi berdasarkan distribusi yang berbeda dari distribusi sebenarnya. Akibatnya, tingkat kesalahan tes Tipe I meningkat dan kemampuan untuk mendeteksi efek tidak maksimal. Hal ini terutama berlaku ketika ukuran kelompok tidak sama dan ketika kemiringan regresi standar berbeda lebih dari 0,4.

> Jika asumsi *Homogeneity of regression slopes* tidak terpenuhi, maka dapat memodelkan variasi ini secara eksplisit menggunakan model linier bertingkat *(multilevel linear models)*[^fn-nth-3]. Kita akan bahas pada tulisan selanjutnya.
{: .prompt-info }

### Normality of residuals

[id7]: ## "Uji normality of residuals pada Ancova adalah pemeriksaan terkait sejauh mana residu dari model regresi memiliki distribusi normal. Hal ini penting karena analisis inferensial bergantung pada asumsi distribusi normal pada residu untuk hasil yang valid."

Uji asumsi yang ke-4 adalah [*normality of residuals*][id7]. Uji asumsi ini bertujuan untuk memeriksa sejauh mana residu dari model regresi memiliki distribusi normal. Residu yang memiliki distribusi normal menunjukkan bahwa asumsi normalitas terpenuhi, sehingga hasil analisis Ancova dapat diandalkan. Normality of residuals menjadi penting karena analisis inferensial, seperti uji hipotesis dan interval kepercayaan, membutuhkan asumsi distribusi normal pada residu. Jika distribusi residu tidak normal, hal ini dapat memengaruhi validitas hasil dan interpretasi analisis Ancova. Oleh karena itu, uji normality of residuals membantu memastikan bahwa asumsi distribusi normal pada residu terpenuhi untuk hasil analisis yang lebih akurat. Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

#### Prosedur input

1. Masuk ke menu SPSS `Analyze > General Linear Model > Univariate`. Pada jendela `Univariate`, sesuaikan isiannya sebagai berikut.
   1. Dependent Variable: `posttest`.
   2. Fixed Factor(s): `VLEs`.
   3. Covariate(s): `pretest`.
2. Cek kembali pada bagian `Model`. Pastikan `Specify Model` adalah `Full factorial`.
3. Klik tombol `Save`, akan muncul jendela `Univariate: Save`. Sesuaikan isiannya sebagai berikut.
   1. Residuals: `Unstandardized` (dicentang). Pastikan jenis residu lainnya pada box `Residuals` tidak tercentang.
4. Klik tombol `Continue`, kemudian klik tombol `OK`. Hasilnya akan muncul pada jendela `output` dan `dataset`. Abaikan dulu jendela `output` dan fokus pada jendela `dataset`.
5. Pada jendela `dataset`, muncul kolom baru bernama `RES_1`. Masuk ke menu `Analyze > Descriptive Statistics > Explore`.
6. Pada jendela `Explore`, sesuaikan isiannya sebagai berikut.
      1. Dependent list: `Residual for posttest [RES_1]`.
7. Klik tombol `Plots`, akan muncul jendela `Explore: Plots`, sesuaikan isiannya sebagai berikut.
      1. Descriptive: `Steam-and-leaf` (hilangkan centang).
      2. Descriptive: `Histogram` (centang).
      3. Centang pada bagian `Normality plots with tests`.
8. Klik tombol `Continue`, kemudian klik tombol `OK`. Hasil akan muncul pada jendela `output` berupa gambar hostogram dan tabel `Tests of Normality`.
9. Pada jendela `output`, klik 2x pada gambar histogram, akan muncul jendela `Chart Editor`.
10. Pada jendela `Chart Editor` klik menu `Show Distribution Curve`, akan muncul jendela `Properties`. Pastikan pilihan pada kotak `Curves` adalah `Normal`. Setelah itu tekan tombol `Close` dan tutup jendela `Chart Editor`. Kita akan melihat gambar histogram pada jendela `output` dilengkapi dengan garis kurva normal.

#### Tampilan output

<details>
  <summary>Klik di sini untuk melihat output tabel.</summary>
  
  <img src="1IaZkRGjL8b1ykZbMDajgHmpXtwaLS2XH">

</details>

<details>
  <summary>Klik di sini untuk melihat output histogram dengan garis kurva normal.</summary>
  
  <img src="1IcQFrtHX13mbEATFzvcLqFuPzzOMZzU9">

</details>

#### Interpretasi hasil

Pada tabel `Tests of Normality`, terlihat nilai *Kolmogorov-Smirnov Statistic* = 0,077 dengan nilai *Sig.* = 0.200. Terlihat juga nilai *Shapiro-Wilk Statistic* = 0,990 dengan nilai *Sig.* = 0.901. Nilai *Sig.* lebih besar dari 0,05. Hal ini menandakan data *unstandardized* residual berdistribusi normal. Oleh karena itu, uji asumsi *normality of residuals* terpenuhi.

Terdapat banyak asumsi normalitas yang keliru *(miskonsepsi)*. Asumsi normalitas yang benar adalah mengacu pada sisa model (residu) yang terdistribusi secara normal, atau distribusi sampling dari parameter, bukan mengacu pada data itu sendiri[^fn-nth-3]. Dalam kasus ini, kita menganalisis asumsi normalitas mengacu pada nilai absolute studentized residual dari model regresi, bukan mengacu pada nilai pretest atau posttest mahasiswanya langsung.

> Bagaimana jika data tidak normal atau uji asumsi *normality of residuals* tidak terpenuhi? Kita akan bahas pada tulisan selanjutnya.
{: .prompt-tip }

### *Homogeneity of variances*

[id8]: ## "Uji homogeneity of variances pada Ancova adalah pemeriksaan terkait apakah variabilitas residu dari model regresi seragam di semua tingkat variabel bebas kategorikal."

Uji asumsi yang ke-5 adalah [*homogeneity of variances*][id8]. Uji asumsi ini bertujuan untuk memastikan bahwa variabilitas dari residu regresi seragam di seluruh kelompok perlakuan. Homogenitas varian merupakan asumsi kritis yang perlu dipenuhi agar hasil analisis ANCOVA dapat diandalkan. Jika terdapat perbedaan yang signifikan dalam variabilitas antar kelompok perlakuan, hal ini dapat mempengaruhi validitas interpretasi hasil dan kesimpulan yang diambil dari analisis tersebut. Oleh karena itu, uji ini bertujuan untuk memverifikasi apakah homogenitas varian dapat diasumsikan, sehingga memastikan keabsahan hasil analisis ANCOVA. Untuk melakukan uji asumsi ini pada SPSS, langkah-langkahnya adalah sebagai berikut.

#### Prosedur input

1. Masuk ke menu SPSS `Analyze > Compare Means > One-Way ANOVA`, akan muncul jendela `One-Way ANOVA` kemudian sesuaikan isiannya sebagai berikut.
      1. Dependen List: `Residual for posttest [RES_1]`.
      2. Factor: `VLEs`.
2. Klik tombol `Options`, kemudian sesuaikan isiannya sebagai berikut.
      1. Statistics: `Homogeneity of variance test` (dicentang).
3. Klik tombol `Continue`, lalu klik tombol `OK`, akan muncul tabel `Test of Homogeneity of Variances` pada jendela output.

#### Tampilan output

<details>
  <summary>Klik di sini untuk melihat output tabel.</summary>
  
  <img src="1If_PWBl16HnoT-g16fel76Mr_tvmZVTN">

</details>

#### Interpretasi hasil

Hipotesis *Levene's Test* adalah sebagai berikut.

1. Hipotesis Nol (H<sub>0</sub>): tidak terdapat perbedaan yang signifikan dalam varians antar kelompok data, atau varians dari setiap kelompok data adalah sama (homogen).
2. Hipotesis Alternatif (H<sub>a</sub>): terdapat perbedaan yang signifikan dalam varians antar kelompok data (tidak homogen/heterogen).

Jika nilai signifikansi *Levene's Test* lebih besar dari 0,05, maka Hipotesis Alternatif ditolak, dan Hipotesis Nol diterima. Dengan kata lain, kita tidak memiliki cukup bukti statistik untuk menolak Hipotesis Nol dan asumsi  *homogeneity of variances* terpenuhi[^fn-nth-3].

Pada tabel `Test of Homogeneity of Variances`, terlihat nilai *Sig.* = 0,066. Nilai ini lebih besar dari 0,05 yang artinya variabilitas atau dispersi dari kelompok-kelompok yang dibandingkan adalah sama atau tidak terdapat perbedaan signifikan dalam variabilitas antar kelompok. Oleh karena itu, asumsi *homogeneity of variances* terpenuhi.

> Bagaimana jika uji asumsi *homogeneity of variances* tidak terpenuhi? Kita akan bahas pada tulisan selanjutnya.
{: .prompt-tip }

## Ancova satu jalur

Setelah semua uji asumsi terpenuhi, selanjutnya adalah melakukan perhitungan Ancova. Langkah-langkah Ancova pada SPSS adalah sebagai berikut.

### Prosedur input

1. Masuk ke menu SPSS `Analyze > General Linear Model > Univariate`. Pada jendela `Univariate`, sesuaikan isiannya sebagai berikut.
   1. Dependent Variable: `posttest`.
   2. Fixed Factor(s): `VLEs`.
   3. Covariate(s): `pretest`.
2. Cek kembali pada bagian `Model`. Pastikan `Specify Model` adalah `Full factorial`.
3. Cek kembali pada bagian `Save`. Pastikan tidak ada yang tercentang pada kotak `Residuals`.
4. Klik tombol `Plots`, akan muncul jendela `Univariate: Profile Plots`, sesuaikan isiannya sebagai berikut.
   1. Factors: `VLEs`.
   2. Plots: `VLEs`.
5. Klik tombol `Continue`.
6. Pada jendela `Univariate`, klik tombol `EM Means`, akan muncul jendela `Univariate: Estimated Marginal Means`, sesuaikan isiannya sebagai berikut.
   1. Display Means for: `VLEs`.
   2. Centang pada pilihan `Compare main effects`.
   3. Confidence interval adjustment: `Bonferroni`.
7. Klik tombol `Continue`.
8. Pada jendela `Univariate`, klik tombol `OK`. Hasil akan muncul pada jendela `output` berupa tabel `Tests of Between-Subjects Effects`, `Estimates`, dan `Pairwise Comparisons`, serta hasil berupa gambar plot terkait *Estimated Marginal Means of posttest*.

<details>
  <summary>Klik di sini untuk melihat detail langkah nomor 4.</summary>
  
  <img src="1J6HkacWhMs9f-XXoFh_qxZKrjFQOffTS">

</details>

### Tampilan output

<details>
  <summary>Klik di sini untuk melihat output tabel Tests of Between-Subjects Effects.</summary>
  
  <img src="1IppZ1vUv3kfHEKL3UkF5cegibNWduccu">

</details>

<details>
  <summary>Klik di sini untuk melihat output tabel Estimates.</summary>
  
  <img src="1IqQDZLrn9sd3JOLXCfKwbLs7faQDkRxb">

</details>

<details>
  <summary>Klik di sini untuk melihat output tabel Pairwise Comparisons.</summary>
  
  <img src="1It_0VA7gaoOjTd5phPYX-NX7zYtbUSBi">

</details>

<details>

  <summary>Klik di sini untuk melihat output plot Estimated Marginal Means of posttest.</summary>
  
  <img src="1ItzzCuLYvyo1PyobZAsUmOUul2qcH2gm">

</details>

### Interpretasi hasil

Pada tabel `Tests of Between-Subjects Effects`, terlihat nilai signifikansi dari variabel `pretest` kurang dari 0,05 (*F* = 62,75; *Sig.* = 0,000) dan nilai dari variabel `VLEs` kurang dari 0,05 (*F* = 4,026; *Sig.* = 0,023). Nilai-nilai tersebut menjawab hipotesis penelitian yang pertama yakni terdapat pengaruh yang signifikan VLEs terhadap prestasi belajar dikontrol oleh pretest.

Pada tabel `Estimates`, terlihat rata-rata nilai posttest setelah dikontrol oleh nilai pretest dari kelompok VLE3 lebih tinggi dari VLE2 dan VLE1, serta VLE1 lebih tinggi dari VLE2. (VLE3 > VLE1 > VLE2). Hasil ini juga dapat dilihat dalam bentuk gambar diagram plot `Estimated Marginal Means of posttest`.

Pada tabel `Pairwise Comparisons`, terlihat bahwa perbedaan antara VLE3 dan VLE2 adalah signifikan (*Sig.* = 0,042; *Sig.* < 0,05). Perbedaan antara VLE3 dan VLE1 tidak signifikan (*Sig.* = 1,000; *Sig.* > 0,05). Perbedaan antara VLE2 dan VLE1 tidak signifikan (*Sig.* = 0,113; *Sig.* > 0,05). Hasil-hasil ini sekaligus menjawab hipotesis penelitian yang kedua yakni,
* Tidak terdapat perbedaan signifikan antara VLE1 dan VLE2 terhadap prestasi belajar dikontrol oleh pretest.
* Tidak terdapat perbedaan signifikan antara VLE1 dan VLE3 terhadap prestasi belajar dikontrol oleh pretest.
* Terdapat perbedaan signifikan antara VLE2 dan VLE3 terhadap prestasi belajar dikontrol oleh pretest.

## Sitasi dokumen ini

Santyadiputra, G. S., Purnomo, & Juniantari, M. (2023, November 29). Ancova satu jalur menggunakan SPSS. GitHub. https://doi.org/10.5281/zenodo.10217507

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.10217507.svg)](https://doi.org/10.5281/zenodo.10217507){:target="blank"}

## Referensi

[^footnote]: Pardoe, I. (2021). *Applied regression modeling* (3rd ed). Wiley.
[^fn-nth-2]: Klopper, J. (2022). *Analysis of covariance using Python*. YouTube. <https://www.youtube.com/watch?v=FhZB1oGVrYc>{:target="blank"}.
[^fn-nth-3]: Field, A. (2017). *Discovering Statistics Using IBM SPSS Statistics* (5th ed.). SAGE Publications.

## TES