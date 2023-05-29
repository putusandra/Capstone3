##**1.1 Context**

Perusahaan TeleHub ingin meningkatkan revenue dengan menjaga anggaran tetap efisien. Biaya mengakuisisi pelanggan baru umumnya lebih besar daripada mempertahankan pelanggan yang sudah ada. Menurut beberapa sumber, Acquisition Cost 5x lebih besar daripada Retention Cost. Oleh sebab itu selain promosi, diperlukan juga upaya menganalisis pola-pola terjadinya customer churn.

Hasil dari analisa ini diharapkan mampu memberi wawasan bagi:

Tim manajemen, tentang kelompok pelanggan yang berpotensi churn serta faktor-faktor yang mempengaruhi keputusan churn.
Tim layanan pelanggan, agar mengambil tindakan proaktif untuk meningkatkan kepuasan pelanggan.
Tim pengembangan produk, tentang fitur produk atau layanan baik yang unggul maupun yang berkontribusi terhadap churn.
Tim pemasaran, agar dapat merancang kampanye pemasaran yang lebih efektif sesuai perilaku pelanggan. Sehingga perusahaan dapat meretensi pelanggan dan mempertahankan revenue secara berkelanjutan.
Target

0 : customer tidak churn
1 : customer churn atau berpindah ke provider lain

##**1.2 Problem Statement**
Problem Statement for Analytic

* Bagaimana pola customer yang paling banyak churn?
* Apa yang membuat customer bertahan menggunakan TeleHub?
* Apa produk unggulan yang dimiliki TeleHub?
* Layanan apa yang paling tidak diminati oleh customer TeleHub?

Problem Statement for Machine Learning

Manakah fitur yang berdampak pada customer churn?
Model apa yang paling tepat untuk mendeteksi pelanggan yang akan churn?
Bagaimana memprediksi pelanggan yang churn dengan baik, sehingga dapat meminimalisir prediksi berupa false negatif?
Matriks apa yang akan digunakan untuk pengukuran kualitas machine learning?
1.3 Goal
TeleHub ingin mengetahui faktor-faktor yang mempengaruhi seorang customer untuk churn/tidak, sehingga dapat mengurangi customer potential loss. Kemudian TeleHub juga ingin memprediksi kemungkinan seorang customer akan berpindah menggunakan produk layanan perusahaan telekomunikasi lain. Sehingga strategi dapat difokuskan kepada customer yang akan churn, seperti dengan memberikan promo paket layanan atau menambah layanan tertentu agar customer tidak beralih menggunakan produk layanan sejenis dari perusahaan kompetitor.

1.4 Plan
Langkah yang akan dilakukan untuk mencapai goal tersebut:

Melakukan Exploratory Data Analysis
Melakukan Data Pre-Processing
Melakukan Pemodelan Machine Learning
Menentukan Model Terbaik
2. Data Understanding
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
