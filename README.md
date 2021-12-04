# Laporan Proyek Machine Learning – Johanes Andre

## Project Overview
Proyek Domain di berada di Industri Entertainment khususnya di bidang seni/hiburan.
Komik merupakan hiburan yang banyak digemari oleh anak muda di jaman sekarang. Selain cerita yang menarik, kemudahan akses melalui telepon genggam juga merupakan faktor tingginya minat di bidang ini. Webtoon adalah platform yang diluncurkan oleh LINE dan dapat diakses dengan gratis.

Pada proyek ini, sistem rekomendasi yang dirancang menggunakan konsep Similarity Measure, yang berarti memberikan saran pengguna mungkin menyukai suatu judul komik berdasarkan yang dibacanya. Proyek ini menggunakan dataset berisi detail informasi komik dalam satu judul. Data ini didapatkan dari scrapping yang dilakukan oleh seorang user di Kaggle. Jumlah dataset yang didapat sekitar 568 data.

Melalui model Machine Learning yang dibangun ini, diharapkan pengguna semakin menyukai aplikasi Webtoon dikarenakan rekomendasi yang diberikan tepat sesuai dengan yang mereka sukai. Dengan begitu pengguna lebih mudah dalam mencari hiburan sesuai dengan yang mereka suka.

Sumber Refrensi:\
[Dataset](https://www.kaggle.com/swarnimrai/webtoon-comics-dataset)
[Papper](https://www.researchgate.net/publication/283148540_MBTI-based_Collaborative_Recommendation_System_A_Case_Study_of_Webtoon_Contents)


## Business Understanding
Dengan sistem rekomendasi yang tepat sesuai dengan prefensi pengguna/pembaca di aplikasi webtoon, maka tingkat kepuasan seseorang terhadap aplikasi webtoon akan semakin tinggi. Line Corporate juga berpotensi menghasilkan keuntungan dengan fitur 'baca lebih awal'. Ketika seseorang sudah menikmati kisah di webtoon, maka pengguna rela juga membayar episode yang seharusnya tayang minggu depan agar bisa dibaca lebih awal.

### Problem Statements
* Apa rekomendasi judul yang cocok untuk para pembaca webtoon?
* Bagaimana metode menetapkan rekomendasi judul untuk pembaca webtoon?

### Goals
* Pembaca mendapat 3 judul rekomendasi berdasarkan judul yang pernah dibaca.
* Model machine learning untuk menentukan rekomendasi judul berdasarkan historis bacaannya melalui pendekatna cosine similarity.

### Solution statements
Pada proyek ini, saya membangun dengan model rekomendasi menggunakan cosine similarity. Definisi Cosine Similarity menurut [Referensi Jurnal](https://journal.unnes.ac.id/nju/index.php/jte/article/download/10955/6659) berikut adalah mengukur kemiripan antara dua dokumen atau teks. Pada Cosine Similarity dokumen atau teks dianggap sebagai vector. Tujuannya untuk mengukur kosinus sudut antara dua vektor dan menentukan apakah dua vektor menunjuk ke arah yang kira-kira sama. Lihat [Referensi berikut](https://www.sciencedirect.com/topics/computer-science/cosine-similarity)

## Data Understanding
[Dataset dari Kaggle](https://www.kaggle.com/swarnimrai/webtoon-comics-dataset)\
Keseluruhan Total Data yang tersedia adalah 568 judul komik yang tiap data mempunyai 10 parameter yang akan dijelaskan sebagai berikut:

Input Variable:
* id - Id unik untuk judul tiap komik
* Name - Judul Komik
* Writer- Nama Penulis Komik
* Likes- Jumlah like yang dimiliki
* genre - Genres Komik
* rating - Penilian rata-rata suatu pembaca terhadap komik tersebit
* Subscribers- Jumlah subscribers komik tersebut
* Summary- Ringkasan isi cerita komik
* Update - Informasi terbit setiap minggu di hari apa
* Reading Link- link untuk membaca komik tersebut


## Data Preparation
Data preparation yang kita lakukan adalah dengan menghilangkan tanda baca atau yang dikenal dengan nama punctuation. Tujuannya untuk mendapatkan pendekatan judul yang lebih baik. Target yang kami proses adalah kolom summary.\
Kemudian masuk tahap persiapan data, yaitu mengubah tipe data text menjadi vector dengan fungsi CountVectorizer. Menurut Refrensi [berikut](https://ichi.pro/id/countvectorizer-dengan-python-42072304686163) CountVectorizer digunakan untuk mengonversi kumpulan dokumen teks menjadi vektor jumlah istilah / token. Ini juga memungkinkan pra-pemrosesan data teks sebelum menghasilkan representasi vektor. Fungsionalitas ini menjadikannya modul representasi fitur yang sangat fleksibel untuk teks. Setelah text menjadi tipe data vector, lakukan maka data bisa diproses ke tahap pemodelan machine learning.


## Modeling
Model yang dirancang untuk menyelesaikan project ini dengan konsep content based filtering. Mengadopsi definisi dari refrensi [MTI BINUS](https://mti.binus.ac.id/2020/11/17/sistem-rekomendasi-content-based/), Content-based filtering adalah memberikan rekomendasi berdasarkan kemiripan atribut dari item atau barang yang disukai. Pada sistem rekomendasi lagu kemiripan berdasarkan atribut yang dimiliki oleh lagu seperti genre, beat, dll. Pada proyek ini, model similarity/kemiripan yang dipakai menggunapan cosine similiratiy.  Definisi dari [Jurnal Teknik Elektro](https://journal.unnes.ac.id/nju/index.php/jte/article/view/10955) cosine similarity merupakan metode untuk menghitung kesamaan antara dua buah objek yang dinyatakan dalam dua buah vector dengan menggunakan keywords (kata kunci) dari sebuah dokumen sebagai ukuran.Ia menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus, semakin besar nilai cosine similarity.

Model ini dipilih karena biasa digunakan untuk mengukur kesamaan dokumen dalam analisis teks, salah satunya adalah sistem rekomendasi seperti [berikut](https://towardsdatascience.com/using-cosine-similarity-to-build-a-movie-recommendation-system-ae7f20842599#:~:text=Cosine%20similarity%20is%20a%20metric,the%20items%20are%20100%25%20similar.).


## Evaluation
Hasil berikut merupakan contoh 10 rekomendasi judul webtoon yang didapat dengan menggunakan metode Cosine Similarity. Dari top 10 rekomendasi yang didapat, kita dapat mengevaluasi hasil dengan metode precision. Menurut sumber [Towards Data Science](https://towardsdatascience.com/recommendation-systems-models-and-evaluation-84944a84fb8e), rumus untuk mencari precision adalah hasil rekomendasi yang relevan dibagi dengan total data yang direkomendasikan.

Ada 2 testcase judul yang diuji, yaitu: About Death & Delusion. About Death memiliki Genre Drama sedangkan Delusion Genre Thriler.

## TestCase 1
Hasil top 10 rekomendasi dari judul 'About Death':\
Karena anda menyukai webtoon  About Death mungkin kamu juga menyukai ini:\
1.Death's Game	--Drama\
2. ShootAround	--Drama\
3. The Horizon	--Drama\
4. Gourmet Hound	--Drama\
5. Annarasumanara	--Drama\
6. Ghost Theater	--Drama\
7. Dark Mortal	--Drama\
8. Your Letter	--Drama\
9. Days of Hana	--Drama\
10.The Golden Spoon	--Drama

Berdasarkan Genre, maka rekomendasi yg cocok untuk About game adalah **100% mirip**. Sekarang mari kita coba testcase ke 2

## TestCase 2
Hasil top 10 rekomendasi dari judul 'Delusion':\
Karena anda menyukai webtoon Delusion mungkin kamu juga menyukai ini:
1. Dear X	--Thriller
2. Ctrl+Z	--Thriller
3. Rotten	--Thriller
4. Nightmare Factory --Thriller
5. FLOWAR	--Sci-fi
6. Grasp	--Thriller
7. Shriek	--Thriller
8. Chiller	--Thriller
9. Epilogue	--Thriller
10. Bite Me	--Thriller

Berdasarkan Genre, maka 9 dari 10 rekomendasi judul, yang mirip dengan genre Thrille adalah 9. Berarti precissionnya adalah:
* **Precision: 90.00**\
Precision = TP/TP+FP

Kesimpulan : Model Machine Learning yang dibangun untuk sistem rekomendasi Judul webtoon untuk pembaca bisa diterima.

**---Ini adalah bagian akhir laporan---**



