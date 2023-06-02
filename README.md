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

* Jumlah baris dataset : 4930 baris
* Jumlah kolom dataset : 11 kolom
* Tidak terdapat missing value dan outliers

## Ringkasan Exploratory Data Analysis

* Dependents memiliki korelasi dan berkontribusi besar dalam kecenderungan pelanggan untuk churn.
* Ada sebagian pelanggan yang tidak memiliki internet service. Sementara sebagian besar feature yang tersedia berhubungan dengan internet service.
* Internet Service: Pelanggan yang menggunakan DSL membayar biaya bulanan yang lebih murah dibanding pengguna fiber optic. Pengguna fiber optic terlihat cenderung lebih banyak untuk churn.
* Online Security, Online Backup, Device Protection, Tech Support: Keempat layanan tersebut hanya bisa diakses jika pengguna memiliki layanan internet. Pengguna keempat layanan tersebut secara sekaligus cenderung untuk tidak churn. Terutama pengguna Tech Support dan Online Security.
* Kita memerlukan informasi tambahan seputar jasa dan produk lain yang ditawarkan oleh perusahaan (bila ada), sehingga dapat memberi insight lebih banyak dalam analisa.
* Contract: Pelanggan yang membayar secara bulanan lebih banyak yang churn daripada yang memilih kontrak pembayaran dalam setahun atau dua tahun.
* Paperless Billing: Pelanggan yang menggunakan paperless billing lebih banyak yang churn daripada yang tidak. Pengguna jenis pembayaran digital umumnya lebih mudah dijangkau oleh penawaran provider lain sehingga mudah terpengaruh oleh harga, kualitas layanan, atau kecepatan respons dari penyedia layanan. 
* Kita memerlukan informasi seputar metode pembayaran apa saja yang digunakan selain paperless billing untuk bisa menganalisa lebih lanjut.
* Tenure: Churn paling banyak terjadi di bulan-bulan awal berlangganan.
* Monthly Charges: Churn paling banyak terjadi di biaya bulanan yang tinggi. Rata-rata biaya bulanan untuk pelanggan yang churn lebih rendah daripada yang tidak (karena pada dataset tercatat hanya membayar beberapa bulan masa berlangganan sebelum churn). 
* Kita memerlukan informasi tambahan mengenai total seluruh biaya yang telah dikeluarkan pelanggan dalam jangka waktu tertentu. Total biaya ini tidak hanya mencakup biaya bulanan, tapi juga kemungkinan ada biaya lain seperti service, installasi, dan sebagainya.

## Modeling

| Target |	Persentase	| 
| - | - | 
| Churn	| 26.69% |	
| Tidak	| 73.31%	| 

Ada 2 cara untuk mengatasi data target yang imbalance:

  1. Setting parameter class_weight='balanced' untuk model yang memilikinya dan masing-masing "random_state" parameter.
  1. Menggunakan metode SMOTE oversampling dan setting "random_state" parameter untuk model yang tidak memiliki "class_weight" parameter.

### Base, Tune and Hyperparameter Tuning Model

RepeatedStratifiedKFold dan GridSearchCV digunakan untuk mencari nilai paramater yang terbaik. Scoring yang digunakan adalah 'recall'.

| Model |  Sebelum  | Setelah |
|:-:|:-:|:-:|
| Logistic Regression | 0.799 | 0.799 |
| Decision Tree Classifier | 0.559 | 0.753 |
| Random Forest Classifier | 0.598 | 0.713 |
| XGBoost Classifier | 0.703 | 0.643 |
| K Nearest Classifier | 0.713 | 0.632 |

Berdasarkan hasil confusion matrix dan waktu perhitungan, performa terbaik tampak pada model Decision Tree Classifier. Setelah dilakukan hyperparameter tuning pada model, 'recall' score bertambah drastis, yaitu dari 0.48 menjadi 0.85

### Decision Tree Classifier Confusion Matrix

#### Sebelum Hyperparameter Tuning
![dtc](https://user-images.githubusercontent.com/88280579/139032798-7452b98e-1834-4eec-90f7-79e0d1167f08.png)

#### Setelah Hyperparameter Tuning
![dtc_tuned](https://user-images.githubusercontent.com/88280579/139032956-27751966-992b-4578-a7c5-5319ef086668.png)


### Kesimpulan

Model machine learning yang dikembangkan dapat membantu perusahaan untuk menurunkan biaya dan waktu dalam memprediksi pelanggan mana yang akan berhenti. Sebagaimana disebutkan pada bagian problem stetment, fokus kita adalah false negative rate. Dimana kita ketahui sebelumnya bahwa, biaya yang dikeuarkan untuk memperoleh pelanggan 5 kali lebih besar dari biaya mempertahankan pelanggan yang sudah ada.

Dapat kita simpulkan, dari 100 pelanggan yang diprediksi, machine learning hanya menghasilkan kesalahan berjumlah 9 pelanggan atau 8,55%. Artinya 9 pelanggan tersebut tidak akan mendapat perlakuan khusus dari perusahaan dan akan berhenti berlangganan. Terdapat peningkatan dari model sebelumnya sebelum dituning, yakni dari 100 pelanggan yang diteliti, kesalahan prediksi mencapai 19 orang atau 18,64%.

Namun, yang perlu diingat juga bahwa terdapat konsekuensi lain. Yakni dari 100 pelanggan yang diprediksi akan berhenti berlangganan, ternyata 58,36% nya, atau 59 orang akan mendapatkan perlakuan khusus, tapi ternyata mereka tidak ada kecenderungan untuk churn dan akan tetap berlangganan. Jika dibandingkan model sebelumnya juga terdapat peningkatan dari 50.69% atau hanya 51 orang.

### Rekomendasi dan Insight

* Terdapat churn lebih besar pada pelanggan yang memiliki tanggungan. Strategi yang dapat dilakukan yakni memberikan promo bagi target market keluarga. 
* Layanan internet dengan fiber optic harganya cenderung lebih mahal dari DSL, sehingga kualitasnya mesti dipastikan secara baik agar mampu meretensi pelanggan yang memang mengutamakan kualitas.
* Tech support dan online security sebagai fitur unggulan dapat dijadikan sebagai sarana promosi kepada pelanggan yang berpotensi untuk churn.
* Masa 12 bulan pertama mulai berlangganan adalah periode krusial untuk follow up tingkat kepuasan pelanggan.
* Sediakan produk dan jasa yang lebih variatif agar bisa menjadi one stop solution bagi pelanggan, sehingga meningkatkan daya tawar.
* Biaya bulanan yang tinggi sebaiknya disertai dengan bonus layanan tertentu untuk meretensi pelanggan.
* Perhatikan kenyamanan teknis dan antar-muka pengguna pada aplikasi yang digunakan perusahaan untuk promosi dan pembayaran.
* Menyebar kuesioner evaluasi kepada pelanggan untuk menarik feedback dan komplain, kemudian menyusun ke dalam dataset agar dapat dianalisa. Sehingga ke depannya dapat dilakukan perbaikan yang tepat sasaran.
