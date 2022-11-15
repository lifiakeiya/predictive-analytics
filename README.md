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
