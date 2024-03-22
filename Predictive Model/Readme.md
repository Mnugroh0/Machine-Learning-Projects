# Laporan Proyek Machine Learning 
***
## Project Overview

Proyek ini berfokus pada analisis dan rekomendasi restoran menggunakan dataset dari TripAdvisor. Dataset ini berisi data restoran dari lima negara bagian utama di Amerika Serikat. Tujuan dari proyek ini adalah untuk memahami pola dan tren dalam ulasan restoran, dan pada akhirnya, memberikan rekomendasi restoran yang sesuai dengan preferensi pengguna.

Dataset ini mencakup berbagai atribut seperti nama restoran, alamat, lokasi, jenis makanan, ulasan, jumlah ulasan, komentar, nomor kontak, URL TripAdvisor, menu, dan kisaran harga. Dengan memanfaatkan informasi ini, kita dapat mengembangkan sistem rekomendasi yang dapat membantu pengguna menemukan restoran yang paling sesuai dengan preferensi mereka, jangkauan yang luas pada dataset ini dapat membantu pengguna untuk menemukan lebih banyak restaurant yang sesuai dengan kesukaan mereka.

Berdasarkan hal itu, kita dapat membuat sistem rekomendasi yang berdasarkan content-based filtering. Metode ini akan memberikan pengguna rekomendasi restaurant berdasarkan kesukaan restaurant mereka.

## Business Understanding
***
### Problem Statements
Berdasarkan penjelasan pada project overview, berikut merupakan  permasalahan yang perlu diselesaikan di proyek ini:
- Sistem rekomendasi apa yang baik, efisien dan dapat diterapkan pada kasus ini?
- Bagaimana cara membuat sistem rekomendasi restaurant yang akan merekomendasikan restaurant berdasarkan tipe cuisine, city, country dan rating?

### Goals
Tujuan dibuatnya proyek ini adalah sebagai berikut:
- Membuat sistem rekomendasi restaurant dengan tipe cuisine, city, country, dan rating sebagai fitur.
- Memberikan rekomendasi restaurant yang mungkin disukai pengguna.

### Solution 
Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini diantaranya:
- Membuat sebuah model sistem rekomendasi dengan melihat kemiripan fitur antar restaurant
- Mengevaluasi hasil rekomendasi yang diberikan
  
## Data Understanding
***
Dataset yang digunakan dapat diakses pada link ini [kaggle](https://www.kaggle.com/datasets/siddharthmandgi/tripadvisor-restaurant-recommendation-data-usa/data) 

Berikut informasi pada dataset:
- Dataset memiliki format csv.
- Dataset terdiri dari 3062 sample dengan 10 features.
- Dataset semuanya object.
- Ada missing value di dataset.

Variabel yang ada pada dataset:
- Name of the Restaurant : Restaurant Name
- Street Address : Restaurant Address
- Location : Detail Location, City, Country and PostCode
- Type of Cuisine Served : Cuisine
- Contact Number : Restaurant Contact Number
- TripAdvisor Restuarant URL : Restaurant URL 
- Menu URL : Restaurant Menu URL 
***
## Data Preparation

Proses data preparation yang dilakukan pada proyek ini terbagi menjadi beberapa tahap:
- Memastikan tidak ada duplicate, missing values agar dapat berjalan.
- Melakukan preprocessing data dengan mengambil city, country dari kolom location. Lalu, merubah rating dan no of reviews menjadi kolom numerik dengan mengekstrak numerik yang ada pada kolom tersebut.
- Menambah fitur untuk meningkatkan performa model. Penambahan fitur ini dari fitur yang sudah ada.
- Melakukan standarisasi kolom numerik menggunakan MinMaxScaler

## Modeling
***
### TF-IDF Vektorisasi
Pada tahap ini, akan membangun sistem rekomendasi berdasarkan Type Cuisine, City, Country, Weighted Ratings yang dimiliki restaurants. Teknik ini digunakan pada sistem rekomendasi untuk menemukan representasi fitur penting dari setiap fitur-fitur masing-masing restaurant. 

### Cosine Similarity
Pada tahap sebelumnya, telah berhasil mengidentifikasi korelasi antara nama restaurant dengan tipe cuisine nya. Sekarang, akan dihitung derajat kesamaan (`similarity degree`) antar nama restaurant dengan menggunakan teknik `cosine similarity`.

Cosine Similarity didasarkan dengan menghitung kesamaan antara dua vektor dengan cara menghitung cosine antara dua sudut antara dua vektor.

$$\text{cosine similarity} = \frac{A \cdot B}{||A||_2 \times ||B||_2}$$
Dimana:
- $A \cdot B$ merupakan dot produk A and B.
- $||A||_2$ merupakan Euclidean length dari vektor A.
- $||B||_2$ merupakan Euclidean length dari vektor B.

## Evaluasi
***
Pada tahap ini akan digunakan Precision untuk mengevaluasi hasil dari rekomendasi. Precision dapat didefinisikan sebagai berikut:  

$\text{Precision} = \frac{r}{i}$

- r= total rekomendasi yang relevan
- i= jumlah rekomendasi yang diberikan

Dengan menggunakan nama restoran _Betty Lou's Seafood and Grill_ dengan tabel sebagai berikut

| Location                        | Type                                      | Reviews | No of Reviews | City           | Country | Weighted Reviews |
|---------------------------------|-------------------------------------------|---------|---------------|----------------|---------|------------------|
| San Francisco, CA 94133-3908    | Seafood, Vegetarian Friendly, Vegan Options | 4.5     | 243.0         | San Francisco  | CA      | 0.049306         |

diperoleh hasil seperti berikut.
	
| Name               | Location                  | Type                                      | Reviews | No of Reviews | City           | Country | Weighted Reviews |
|--------------------|---------------------------|-------------------------------------------|---------|---------------|----------------|---------|------------------|
| Ristorante Franchino | San Francisco, CA 94133-3907 | Italian, Vegetarian Friendly, Vegan Options | 4.5     | 429.0         | San Francisco  | CA      | 0.087750         |
| Seven Hills        | San Francisco, CA 94109-3114 | Seafood, Italian, Vegetarian Friendly     | 4.5     | 923.0         | San Francisco  | CA      | 0.189854         |
| Quince             | San Francisco, CA 94133-4610 | French, Vegetarian Friendly, Vegan Options | 4.5     | 545.0         | San Francisco  | CA      | 0.111726         |
| Pacific Cafe       | San Francisco, CA 94121-1623 | American, Seafood, Gluten Free Options    | 4.5     | 241.0         | San Francisco  | CA      | 0.048893         |
| Pacific Catch      | San Francisco, CA 94123-2701 | Hawaiian, Seafood, Vegetarian Friendly    | 4.5     | 987.0         | San Francisco  | CA      | 0.203082         |


Dengan begitu kita bisa ukur tingkat kepresisiannya. Dari hasil 5 rekomendasi yang diberikan semuanya relevan oleh input. Oleh karena itu bisa diperoleh tingkat presisi 100%
## Referensi
[cosine similarity](https://towardsdatascience.com/cosine-similarity-how-does-it-measure-the-similarity-maths-behind-and-usage-in-python-50ad30aad7db)