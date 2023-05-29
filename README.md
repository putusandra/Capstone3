# Telco Customer Churn

## Context

Perusahaan TeleHub ingin meningkatkan revenue dengan menjaga anggaran tetap efisien. Biaya mengakuisisi pelanggan baru umumnya lebih besar daripada mempertahankan pelanggan yang sudah ada. Menurut beberapa sumber, Acquisition Cost 5x lebih besar daripada Retention Cost. Oleh sebab itu selain promosi, diperlukan juga upaya menganalisis pola-pola terjadinya customer churn.

Hasil dari analisa ini diharapkan mampu memberi wawasan bagi:

* Tim manajemen, tentang kelompok pelanggan yang berpotensi churn serta faktor-faktor yang mempengaruhi keputusan churn.
* Tim layanan pelanggan, agar mengambil tindakan proaktif untuk meningkatkan kepuasan pelanggan.
* Tim pengembangan produk, tentang fitur produk atau layanan baik yang unggul maupun yang berkontribusi terhadap churn.
* Tim pemasaran, agar dapat merancang kampanye pemasaran yang lebih efektif sesuai perilaku pelanggan. Sehingga perusahaan dapat meretensi pelanggan dan mempertahankan revenue secara berkelanjutan.

**Target**

0 : customer tidak churn
1 : customer churn atau berpindah ke provider lain

## Problem Statement

Problem Statement for Analytic
* Bagaimana pola customer yang paling banyak churn?
* Apa yang membuat customer bertahan menggunakan TeleHub?
* Apa produk unggulan yang dimiliki TeleHub?
* Layanan apa yang paling tidak diminati oleh customer TeleHub?

Problem Statement for Machine Learning
* Manakah fitur yang berdampak pada customer churn?
* Model apa yang paling tepat untuk mendeteksi pelanggan yang akan churn?
* Bagaimana memprediksi pelanggan yang churn dengan baik, sehingga dapat meminimalisir prediksi berupa false negatif?
* Matriks apa yang akan digunakan untuk pengukuran kualitas machine learning?

Langkah yang akan dilakukan :

1. Melakukan Exploratory Data Analysis
2. Melakukan Data Pre-Processing
3. Melakukan Pemodelan Machine Learning
4. Menentukan Model Terbaik

## Data Understanding

Dataset mengandung 11 kolom yang berisi informasi sebagai berikut:

Dependents: Apakah pelanggan memiliki tanggungan (anak, istri, dsb) atau tidak.
Tenure: Lama waktu (jumlah bulan) berlangganan dengan perusahaan
OnlineSecurity: Apakah pelanggan memiliki sistem keamanan online atau tidak.
OnlineBackup: Apakah pelanggan memiliki backup online atau tidak.
InternetService: Apakah klien berlangganan layanan Internet.
DeviceProtection: Apakah klien memiliki perlindungan perangkat atau tidak.
TechSupport: Apakah klien memiliki dukungan teknis atau tidak.
Contract: Tipe kontrak sesuai dengan durasi berlangganan.
PaperlessBilling: Apakah tagihan dikeluarkan secara paperless.
MonthlyCharges: Biaya bulanan yang dihabiskan untuk berlangganan (dalam satuan mata uang dollar).
Churn: Apakah klien berhenti berlangganan atau tidak dalam sebulan terakhir.

| No | __Nama Fitur__ | __Penjelasan__ | __Data Type__ |
| - | - | - | - | 
| 1 | Dependents | Apakah pelanggan memiliki tanggungan atau tidak (Yes, No) | categorical | 
| 2 | Tenure | Jumlah bulan berlangganan pada perusahaan | numeric, int |
| 3 | OnlineSecurity | Apakah pelanggan memiliki layanan online security atau tidak (Yes, No, No internet service) | categorical | 
| 4 | OnlineBackup |  Apakah pelanggan memiliki layanan online back up atau tidak (Yes, No, No internet service) | categorical | 
| 5 | InternetService | Internet service provider yang digunakan pelanggan (DSL, Fiber optic, No) | categorical |
| 6 | DeviceProtection | Apakah pelanggan memiliki layanan device protection atau tidak (Yes, No, No internet service) | categorical |
| 7 | TechSupport | Apakah pelanggan memiliki layanan tech support atau tidak (Yes, No, No internet service) | categorical | 
| 8 | Contract | Durasi kontrak pembayaran dari pelanggan (Month-to-month, One year, Two year) | categorical |
| 9 | PaperlessBilling | Apakah pelanggan menggunakan paperless billing atau tidak (Yes, No) | categorical |
| 10 | MonthlyCharges | Jumlah tagihan bulanan dari pelanggan |  numeric , int |
| 11 | Churn | Apakah pelanggan churn/beralih atau tidak (Yes or No) | categorical |


