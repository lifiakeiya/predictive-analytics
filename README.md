# predictive-analytics
submission dicoding terapan
# Domain Proyek
Untuk proyek ini, saya telah memilih proyek di bidang ekonomi dan bisnis. Dalam dunia bisnis, para pebisnis berusaha mencari cara untuk meningkatkan keuntungan bisnis. Hal yang sama berlaku untuk bisnis penjualan rumah. Dalam prakteknya dalam persaingan pasti ada tantangan dan hambatan, namun para pelaku bisnis harus mampu memutar otak agar tantangan dan hambatan tersebut tidak menjadi hambatan dalam berbisnis. 

Salah satu tantangan yang dihadapi operasi penjualan adalah kondisi lingkungan. Kondisi lingkungan di sini seperti maraknya kejahatan, kekerasan, penjarahan, dll. Namun, apakah kondisi lingkungan tersebut memberikan peluang bagi para pelaku bisnis untuk menjalankan usahanya, atau justru sebaliknya? Dalam memprediksi permasalahan tersebut saya menggunakan 3 algoritma, yakni Linear Regression, KNN, dan Random Forest.
# Bussiness understanding
Perusahaan yang menjual rumah akan menjual rumah di tempat yang kondisi lingkungannya baik, dimana ada kasus kriminal pasti perusahaan akan bertanya-tanya apakah rumah yang kita jual akan laris manis dipasaran? Dengan sedikitnya jumlah kriminal maka diharapkan akan semakin meningkat harga jual rumahnya.
# Problem Statements
Berdasarkan situasi di atas, perusahaan akan mengembangkan sistem prediksi harga rumah untuk mengatasi masalah berikut:

• Di antara ciri-ciri atau syarat-syarat pidana, ciri-ciri manakah yang paling berpengaruh terhadap harga jual rumah?

• Jika rumah tersebut memiliki ciri atau kondisi kriminal tertentu, berapa harga jualnya?
# Goals
Untuk menjawab pertanyaan ini, kami akan melakukan pemodelan prediktif dengan tujuan atau sasaran berikut:

• Cari tahu fitur mana yang paling relevan dengan harga jual rumah. 

• Membuat model pembelajaran mesin yang dapat memprediksi harga jual rumah seakurat mungkin berdasarkan fitur yang ada.
# Solution Statements
• Regresi linier. Metode regresi linier dipilih sebagai metode peramalan dalam penelitian ini berdasarkan keunggulannya dalam mengestimasi parameter model sederhana dan data berbasis time-series. Selain itu, metode ini dapat dianalisis dengan beberapa variabel bebas (X) yang membuat hasil prediksi lebih akurat. Sisi negatifnya adalah prediksi dari regresi linier adalah perkiraan, sehingga masih ada kemungkinan ketidaksesuaian dengan data sebenarnya. Cara kerja regresi linier adalah dengan memanggil fungsi LinearRegression() yang kita impor dari library scikit-learn.

•	K-Nearest Neighbor. Pemilihan metode K-Nearest Neighbor sebagai metode prediksi pada penelitian ini didasari oleh kelebihannya yang mudah dipahami dan diimplementasikan, tangguh terhadap data training sample yang noisy, dan memiliki konsistensi yang kuat. Kekurangannya yakni perlu menentukan parameter k (jumlah tetangga terdekat), sensitif terhadap data outlier. Cara kerja K-Nearest Neighbor yakni dengan memanggil fungsi KNeighborsRegressor() yang kita import dari library scikit-learn.

•	Random Forest. Pemilihan metode Random Forest sebagai metode prediksi pada penelitian ini didasari oleh kelebihannya yaitu dapat mengatasi noise dan missing value serta dapat mengatasi data dalam jumlah yang besar. Dan kekurangan pada algoritma Random Forest yaitu interpretasi yang sulit dan membutuhkan tuning model yang tepat untuk data. Cara kerja Random Forest yakni dengan memanggil fungsi RandomForestRegressor() yang kita import dari library scikit-learn.
# Data Understanding
Data yang saya gunakan yakni diunduh dari situs Kaggle yang berisi indeks harga nsa atau non seasonal index yang merupakan fitur yang akan diprediksi, fitur yang lain merupakan kondisi kriminal di sekitar rumah tersebut yang akan menjadi pertimbangan dalam prediksi ini. Deskripsi variabel pada dataset adalah sebagai berikut:

•	Year = Tahun

•	index_nsa = Harga rumah (non seasonal index)

•	City, State = Kota, Negara Bagian

•	Rapes = Perkosaan

•	Assaults = Penyerangan

•	Robberies = Perampokan

•	Population = Populasi

•	Violent Crimes = Kekerasan

•	Homicides = Pembunuhan

![image](https://user-images.githubusercontent.com/59913378/201852488-7e5caf3e-d0af-4d23-bba4-1b6116dd06f2.png)
![image](https://user-images.githubusercontent.com/59913378/201852807-5546a8a8-faaa-4be6-8d13-0efb50ae979f.png)

Dari gambar diatas dijelaskan bahwa didalam data terdapat 1 data kategori bertipe object dan 8 data numerik float64. Visualisasi data kategori sebagai berikut.
![image](https://user-images.githubusercontent.com/59913378/201857655-dc517859-2461-4a25-b573-8cf727dc69bc.png)

Untuk visualisasi distribusi data pada kolom dengan numeric features dan antar numeric features sebagai berikut.
![image](https://user-images.githubusercontent.com/59913378/201857596-58354dc1-43d4-4043-94d3-acac79167a49.png)

Untuk visualisasi heatmap (korelasi numeric features) adalah sebagai berikut.
![image](https://user-images.githubusercontent.com/59913378/201858094-17cbf1ef-ca93-4fcb-bd66-4fc9c5b97a0b.png)

# Data Preperation
• Train-Test-split, teknik ini berguna untuk membagi data menjadi data uji dan data latih. Teknik ini menggunakan fungsi train_test_split dari library scikit-learn.

• Standarisasi, teknik ini membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma. Di sini kita mengurangkan mean (nilai rata-rata) pada seluruh fitur numerik kemudian membaginya dengan standar deviasi untuk menggeser distribusi menggunakan fungsi StandardScaler() dari library scikit-learn. Setelah kita mengecek informasi menggunakan fungsi .describe(), kita mengetahui bahwa mean pada fitur numerik berubah menjadi 0 dan standar deviasi-nya menjadi 1.

# Modelling
![image](https://user-images.githubusercontent.com/59913378/201859187-692a61e2-a724-4517-b0e3-7d45d0b91871.png)

Tahap diatas untuk mengembangkan model machine learning dengan Linear Regression, K-Nearest Neighbor, Random Forest. Langkah selanjutnya yakni mengevaluasi performa masing-masing algoritma dan menentukan algoritma mana yang memberikan hasil prediksi terbaik. 
# Evaluation
![image](https://user-images.githubusercontent.com/59913378/201860044-f6a8cfa4-6981-4590-9a3e-6c6c539e8fa9.png)

Kode program diatas adalah teknik yang bertujuan untuk menghitung selisih rata-rata nilai sebenarnya dengan nilai prediksi biasa disebut dengan Mean Squared Error (MSE). Ouput yang akan dikeluarkan ialah: 

![image](https://user-images.githubusercontent.com/59913378/201860427-4b180498-80a9-49ea-bddb-6c10f5693844.png)
![image](https://user-images.githubusercontent.com/59913378/201860843-ccb42815-233c-4bdd-986a-80156d63b155.png)

Dari hasil diatas dapat disimpulkan kalau Random Forest mempunyai eror paling sedikit.

Terakhir, Mengukur kinerja model menggunakan fungsi .score() dalam skala 100.

![image](https://user-images.githubusercontent.com/59913378/201861200-8fa28441-9cd7-40d2-9f0b-b211fb42ac8c.png)

dari hasil diatas dapat dilihat akurasi pada model Random Forest yang paling tinggi, mencapai 90%

