# predictive-analytics
submission dicoding terapan
# Domain Proyek
Oada project kali ini ialah proyek di bidang ekonomi dan bisnis. Dalam dunia bisnis, para pebisnis berusaha mencari cara untuk meningkatkan keuntungan bisnis. Hal yang sama berlaku untuk bisnis penjualan rumah. Dalam prakteknya dalam persaingan pasti ada tantangan dan hambatan, namun para pelaku bisnis harus mampu memutar otak agar tantangan dan hambatan tersebut tidak menjadi hambatan dalam berbisnis. 

Salah satu tantangan yang dihadapi operasi penjualan adalah kondisi lingkungan. Kondisi lingkungan di sini seperti maraknya kejahatan, kekerasan, penjarahan, dll. Namun, apakah kondisi lingkungan tersebut memberikan peluang bagi para pelaku bisnis untuk menjalankan usahanya, atau justru sebaliknya? Dalam memprediksi permasalahan tersebut saya menggunakan 3 algoritma, yakni Linear Regression, KNN, dan Random Forest.
# Bussiness understanding
Perusahaan yang menjual rumah akan menjual rumah di tempat yang kondisi lingkungannya baik, dimana ada kasus kriminal pasti perusahaan akan bertanya-tanya apakah rumah yang nantinya dijual akan laris manis dipasaran? Dengan sedikitnya jumlah kriminal maka diharapkan akan semakin meningkat harga jual rumahnya.
# Problem Statements
Berdasarkan situasi di atas, perusahaan akan mengembangkan sistem prediksi harga rumah untuk mengatasi masalah berikut:

• Di antara ciri-ciri atau syarat-syarat pidana, ciri-ciri manakah yang paling berpengaruh terhadap harga jual rumah?

• Jika rumah tersebut memiliki ciri atau kondisi kriminal tertentu, berapa harga jualnya?
# Goals
Untuk menjawab pertanyaan diatas, maka hal yang akan dilakukan ialah membuat pemodelan prediktif dengan tujuan atau sasaran berikut:

• Mengetahui fitur mana yang paling relevan dengan harga jual rumah. 

• Membuat model pembelajaran mesin yang dapat memprediksi harga jual rumah seakurat mungkin berdasarkan fitur yang ada.
# Solution Statements
• Regresi linier. Metode regresi linier dipilih sebagai metode peramalan dalam penelitian ini berdasarkan keunggulannya dalam mengestimasi parameter model sederhana dan data berbasis time-series. Selain itu, metode ini dapat dianalisis dengan beberapa variabel bebas (X) yang membuat hasil prediksi lebih akurat. Sisi negatifnya adalah prediksi dari regresi linier adalah perkiraan, sehingga masih ada kemungkinan ketidaksesuaian dengan data sebenarnya. Cara kerja regresi linier adalah dengan memanggil fungsi LinearRegression() yang  telah diimpor dari library scikit-learn.

•	K-Nearest Neighbor. Pemilihan metode K-Nearest Neighbor sebagai metode prediksi pada penelitian ini didasari oleh kelebihannya yang mudah dipahami dan diimplementasikan, tangguh terhadap data training sample yang noisy, dan memiliki konsistensi yang kuat. Kekurangannya yakni perlu menentukan parameter k (jumlah tetangga terdekat), sensitif terhadap data outlier. Cara kerja K-Nearest Neighbor yakni dengan memanggil fungsi KNeighborsRegressor() yang telah diimport dari library scikit-learn.

•	Random Forest. Pemilihan metode Random Forest sebagai metode prediksi pada penelitian ini didasari oleh kelebihannya yaitu dapat mengatasi noise dan missing value serta dapat mengatasi data dalam jumlah yang besar. Dan kekurangan pada algoritma Random Forest yaitu interpretasi yang sulit dan membutuhkan tuning model yang tepat untuk data. Cara kerja Random Forest yakni dengan memanggil fungsi RandomForestRegressor() yang telah diimport dari library scikit-learn.
# Data Understanding
Data yang digunakan yakni diunduh dari situs Kaggle yang berisi indeks harga nsa atau non seasonal index yang merupakan fitur yang akan diprediksi, fitur yang lain merupakan kondisi kriminal di sekitar rumah tersebut yang akan menjadi pertimbangan dalam prediksi ini. Deskripsi variabel pada dataset adalah sebagai berikut:

•	Year = Tahun

•	index_nsa = Harga rumah (non seasonal index)

•	City, State = Kota, Negara Bagian

•	Rapes = Perkosaan

•	Assaults = Penyerangan

•	Robberies = Perampokan

•	Population = Populasi

•	Violent Crimes = Kekerasan

•	Homicides = Pembunuhan

Year index_nsa City, State Population Violent Crimes Homicides Rapes Assaults Robberies

0 1975.0 41.080 Atlanta, GA 490584.0 8033.0 185.0 443.0 3518.0 3887.0

1 1975.0 30.750 Chicago, IL 3150000.0 37160.0 818.0 1657.0 12514.0 22171.0

2 1975.0 36.350 Cleveland, OH 659931.0 10403.0 288.0 491.0 2524.0 7100.0

3 1975.0 20.910 Oakland, CA 337748.0 5900.0 111.0 316.0 2288.0 3185.0

4 1975.0 20.385 Seattle, WA 503500.0 3971.0 52.0 324.0 1492.0 2103.0

Dari gambar diatas dijelaskan bahwa didalam data terdapat 1 data kategori bertipe object dan 8 data numerik float64. Visualisasi data kategori sebagai berikut.
<class ‘pandas.core.frame.DataFrame’>
Int64Index: 1708 entries, 0 to 3476
Data columns (total 9 columns):

Column Non-Null Count Dtype

0 Year 1708 non-null float64

1 index_nsa 1708 non-null float64

2 City, State 1708 non-null object

3 Population 1708 non-null float64

4 Violent Crimes 1708 non-null float64

5 Homicides 1708 non-null float64

6 Rapes 1708 non-null float64

7 Assaults 1708 non-null float64

8 Robberies 1708 non-null float64

dtypes: float64(8), object(1)

memory usage: 133.4+ KB

Untuk visualisasi distribusi data pada kolom dengan numeric features dan antar numeric features sebagai berikut.
![image](https://user-images.githubusercontent.com/59913378/201857596-58354dc1-43d4-4043-94d3-acac79167a49.png)

Untuk visualisasi heatmap (korelasi numeric features) adalah sebagai berikut.
![image](https://user-images.githubusercontent.com/59913378/201858094-17cbf1ef-ca93-4fcb-bd66-4fc9c5b97a0b.png)

Dalam tahap ini saya melakukan Data loading dan proses EDA yang saya representasikan menggunakan visualisasi, diantaranya : Exploratory Data Analysis - Menangani Missing Value dan Outliers, visualisasinya menggunakan boxplot dari library seaborn Exploratory Data Analysis - Univariate Analysis, visualisasinya menggunakan plot dan histogram dari library matplotlib Exploratory Data Analysis - Multivariate Analysis, visualisasinya menggunakan catplot dari library seaborn

# Data Preperation
Beberapa teknik yang digunakan pada tahapan Data Preparation ialah:

• Train-Test-split, teknik ini berguna untuk membagi data menjadi data uji dan data latih. Teknik ini menggunakan fungsi train_test_split dari library scikit-learn.

• Standarisasi, teknik ini membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma. Di sini mengurangkan mean (nilai rata-rata) pada seluruh fitur numerik kemudian membaginya dengan standar deviasi untuk menggeser distribusi menggunakan fungsi StandardScaler() dari library scikit-learn. Setelah mengecek informasi menggunakan fungsi .describe(), kita mengetahui bahwa mean pada fitur numerik berubah menjadi 0 dan standar deviasi-nya menjadi 1.

# Modelling
Pada tahap ini mengembangkan model machine learning dengan tiga algoritma, yakni Linear Regression, K-Nearest Neighbor, Random Forest. Langkah selanjutnya yakni mengevaluasi performa masing-masing algoritma dan menentukan algoritma mana yang memberikan hasil prediksi terbaik. Langkah pertama dalam proses modeling yakni menyiapkan sebuah DataFrame baru untuk menampung berapa nilai mae-nya yang berfungsi pada proses analisis model. 

- Linear Regression : Langkah pertama kita import terlebih dahulu fungsi LinearRegression() pada library scikit-learn. Setelah itu kita definisikan fungsi LinearRegression() ke dalam variabel baru bernama lin_reg. Kemudian kita uji model tersebut data uji kita yakni x_train dan y_train menggunakan fungsi .fit().
Setelah kita uji model terebut, kita cek akurasinya menggunakan metrik mae dan masukan nilai mae nya ke DataFrame yang telah kita buat sebelumnya.
- Nearest Neighbor : Langkah pertama kita import terlebih dahulu fungsi KNeighborsRegressor() pada library scikit-learn. Setelah itu kita definisikan fungsi KNeighborsRegressor() ke dalam variabel baru bernama knn. Kita masukkan juga parameter n_neighbors nya yakni berjumlah 10, yang berarti kita mendefinisikan nilai tetangga-nya 10. Kemudian kita uji model tersebut pada data uji kita yakni x_train dan y_train menggunakan fungsi .fit().
Setelah kita uji model terebut, kita cek akurasinya menggunakan metrik mae dan masukan nilai mae nya ke DataFrame yang telah kita buat sebelumnya.
- Random Forest : Langkah pertama kita import terlebih dahulu fungsi RandomForestRegressor() pada library scikit-learn. Setelah itu kita definisikan fungsi RandomForestRegressor() ke dalam variabel baru bernama RF. Pada fungsi tersebut kita tambahkan parameter n_estimators-nya 50, max_depth-nya 16, random_state-nya 55, n_jobs-nya -1. Kemudian kita uji model tersebut data uji kita yakni x_train dan y_train menggunakan fungsi .fit().
Setelah kita uji model terebut, kita cek akurasinya menggunakan metrik mae dan masukan nilai mae nya ke DataFrame yang telah kita buat sebelumnya.

![image](https://user-images.githubusercontent.com/59913378/201859187-692a61e2-a724-4517-b0e3-7d45d0b91871.png)

Tahap diatas untuk mengembangkan model machine learning dengan Linear Regression, K-Nearest Neighbor, Random Forest. Langkah selanjutnya yakni mengevaluasi performa masing-masing algoritma dan menentukan algoritma mana yang memberikan hasil prediksi terbaik. 


# Evaluation
![image](https://user-images.githubusercontent.com/59913378/201860044-f6a8cfa4-6981-4590-9a3e-6c6c539e8fa9.png)

Kode program diatas adalah teknik yang bertujuan untuk menghitung selisih rata-rata nilai sebenarnya dengan nilai prediksi biasa disebut dengan Mean Squared Error (MSE). Ouput yang akan dikeluarkan ialah: 

train test

LinearRegression 0.892576 0.96617

KNN 0.380629 0.52106

RandomForest 0.0456 0.33477

![image](https://user-images.githubusercontent.com/59913378/201860427-4b180498-80a9-49ea-bddb-6c10f5693844.png)
![image](https://user-images.githubusercontent.com/59913378/201860843-ccb42815-233c-4bdd-986a-80156d63b155.png)

Dari hasil diatas dapat disimpulkan kalau Random Forest mempunyai eror paling sedikit.

Terakhir, Mengukur kinerja model menggunakan fungsi .score() dalam skala 100.

Accuracy score dari model Linear Regression =  0.760807233952006

Accuracy score dari model KNN               =  0.8710022235399519

Accuracy score dari model Random Forest     =  0.9171194254885765

![image](https://user-images.githubusercontent.com/59913378/201861200-8fa28441-9cd7-40d2-9f0b-b211fb42ac8c.png)

dari hasil diatas dapat dilihat akurasi pada model Random Forest yang paling tinggi, mencapai 90%

# Kesimpulan
Setelah melakukan analisis di atas, dapat kita jawab Problem Statements dan Goal yang saya buat di atas, yakni :

1. Fitur-fitur kriminalitas di atas mempunyai korelasi yang kecil terhadap harga, sehingga tidak terlalu memengaruhi harga jual rumah.
2. Model machine learning yang akurat sesuai dengan metrik evaluasi dari MSE dan accuracy yakni menggunakan model Random Forest.
