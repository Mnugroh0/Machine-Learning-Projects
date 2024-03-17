# Laporan Proyek Machine Learning - Muhammad Adi Nugroho

## Domain Proyek

Churn, atau tingkat perpindahan pelanggan adalah hal yang sangat penting bagi perusahaan telekomunikasi karena dapat mempengaruhi pendapatan dan reputasi perusahaan tersebut.


## Business Understanding

### Problem Statements

1. Tingkat churn pelanggan yang tinggi dapat menjadi indikasi dari kekurangan dalam layanan atau promosi yang tidak memadai. Dengan demikian, perusahaan telekomunikasi perlu memahami faktor-faktor apa yang mendorong pelanggan untuk berhenti berlangganan.

2. Mengidentifikasi pola dan tren yang terkait dengan churn pelanggan dapat membantu perusahaan untuk mengantisipasi dan mencegah kehilangan pelanggan di masa depan. Namun, keberhasilan dalam hal ini bergantung pada kemampuan untuk mengelola dan menganalisis data pelanggan dengan efektif.

### Goals

1. Mengidentifikasi faktor-faktor utama yang berkontribusi terhadap churn pelanggan. Dengan memahami faktor-faktor ini, perusahaan dapat mengambil tindakan yang tepat untuk meningkatkan retensi pelanggan dan mengurangi tingkat churn.

2. Mengembangkan model prediktif yang dapat memprediksi churn pelanggan dengan akurasi yang tinggi. Dengan demikian, perusahaan dapat mengambil tindakan preventif dengan cepat untuk mempertahankan pelanggan yang mungkin berisiko berhenti berlangganan.

### Solution statements
1. Melakukan exploratory data analysis termasuk univariate analysis dan multivariate analysis untuk mengetahui faktor-faktor yang mempengaruhi churn seseorang. 
2. Membuat beberapa machine learning model untuk membandingkan mana model yang lebih baik dalam memprediksi.

## Data Understanding
Dataset yang digunakan pada proyek kali ini dapat diakses di [Customer Churn Dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn?resource=download).

Berikut informasi pada dataset:
- Dataset memiliki format csv.
- Dataset terdiri dari 7043 sample dengan 21 features.
- Dataset memiliki 3 features numerik, dan sisanya kategorik.
- Ada missing value di dataset

### Variabel-variabel pada Customer Churn Dataset:
- Customer ID
- Gender : Whether the customer is a male or a female
- Senior Citizen : Whether the customer is a senior citizen or not (1, 0)
- Partner : Whether the customer has a partner or not (Yes, No)
- Dependents : Whether the customer has dependents or not (Yes, No)
- Tenure : Number of months the customer has stayed with the company
- PhoneService : Whether the customer has a phone service or not (Yes, No)
- MultipleLines : Whether the customer has multiple lines or not (Yes, No, No phone service)
- InternetService : Customer’s internet service provider (DSL, Fiber optic, No)
- OnlineSecurity : Whether the customer has online security or not (Yes, No, No internet service)
- OnlineBackup : Whether the customer has online backup or not (Yes, No, No internet service)
- DeviceProtection : Whether the customer has device protection or not (Yes, No, No internet service)
- TechSupport : Whether the customer has tech support or not (Yes, No, No internet service)
- StreamingTV : Whether the customer has streaming TV or not (Yes, No, No internet service)
- StreamingMovies : Whether the customer has streaming movies or not (Yes, No, No internet service)
- Contract : The contract term of the customer (Month-to-month, One year, Two year)
- PaperlessBilling : Whether the customer has paperless billing or not (Yes, No)
- PaymentMethod : The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic))
- MonthlyCharges : The amount charged to the customer monthly
- TotalCharges : The total amount charged to the customer
- Churn : Whether the customer churned or not (Yes or No)

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation

Proses data preparation yang dilakukan pada proyek ini terbagi menjadi beberapa tahap:
- Memastikan tidak ada duplicate, missing values agar machine learning dapat dilatih.
- Menambah feature untuk meningkatkan performa machine learning model. Penambahan feature ini dari feature-feature yang sudah ada.
- Split the data. Data di bagi menjadi train dan test sebelum di encoding, untuk menghindari data leakage.
- Membuat Pipeline untuk memproses data. Pipeline ini terdiri dari pemrosesan untuk kategorikal berupa one hot encoding, dan standarisasi berupa Standard Scaler untuk data numerik, serta Label Encoder untuk kolom target.

## Modeling

Pemodelan untuk prediksi Churn menggunakan beberapa model machine learning. Diantaranya sebagai berikut:
- RandomForest
- K-Nearest Neighbor
- Logistic Regression
- AdaBoostClassifier

Logistic Regression menjadi model paling baik dalam memprediksi dalam proyek ini. Dikarenakan metriknya lebih tinggi dibandingkan model lainnya. Model ini juga sederhana dan juga cepat.

## Evaluation

Dalam meninjau performa machine learning model untuk permasalahan klasifikasi, digunakan presisi dan f1-score sebagai metrik dalam menentukkan model yang lebih baik. 
- Presisi menunjukkan seberapa banyak kasus yang diprediksi positif oleh model yang sebenarnya positif.
- F1-Score merupakan rata-rata harmonik dari presisi dan recall.
$$Precision = TP/(TP+FP)$$
$$f1-score = 2 \times ((precision \times recall)/(precision + recall))$$

TP = True Positif
FP = False Positif

Di bawah ini merupakan rangkuman hasil model dalam mendeteksi customer yang Churn (yang terlabel : Yes)
+ Hasil Evaluasi
  | Model | Precision | Recall | F1-Score | Accuracy |
  |------|-----------|--------|----------|----------|
  | Random Forest | 0.62 | 0.48	| 0.54 | 0.78 |
  | KNN | 0.57 | 0.55 | 0.56 | 0.77 |
  | Logistic Regression | 0.67 | 0.57 | 0.61 | 0.81 |
  | AdaBoost | 0.65 |	0.53	| 0.58 | 0.80 |