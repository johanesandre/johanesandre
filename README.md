# Laporan Proyek Machine Learning – Johanes Andre

## Domain Proyek
Proyek Domain di berada di Industri pertanian. 
Hasil panen merupakan hal yang dinanti oleh para petani. Hasil panen yang baik mampu menentukan keuntungan yang didapat petani ke penadah / penerima hasil panen tersebut.

Pada proyek ini, hasil panen yang akan dianalisa berupa buah anggur.
Proyek ini menggunakan dataset berisi informasi kualitas anggur yang ditentukan oleh beberapa nilai/parameter. Data tersebut didapatkan melalui physicochemical tests dan yang diambil menggunakan sensoris.

Melalui model Machine Learning yang dibangun ini, diharapkan membantu sektor pertanian untuk memberikan prediksi kualitas anggur yang baik dari panen.
Kualitas yang baik tentu akan membuat kehidupan para petani makin sejahtera.

Sumber Refrensi:\
[Dataset](https://archive.ics.uci.edu/ml/datasets/wine+quality) 
[Papper](https://www.sciencedirect.com/science/article/abs/pii/S0167923609001377?via%3Dihub)


## Business Understanding
Memprediksi kualitas anggur yang baik berdasarkan variable yang dihasilkan oleh sensor. Dengan beraneka variable yang dimiliki maka hasil panen ke depan bisa memperhatikan suatu variable tersebut sebagai indikator utama/kontrol agar menghasilkan hasil panen anggur yg baik sebanyak-banyaknya.

### Problem Statements
Variable apa yang paling mempengaruhi kualitas anggur?\
Berapa tingkat akurasi yang dihasilkan dengan model machine learning yg dirancang?

### Goals
Hasil prediksi kualitas anggur yang baik dengan akurat

### Solution statements
Pada proyek ini, saya membangun dengan model ML SVM. Support Vector Machine adalah algoritma machine learning yang dapat digunakan untuk menyelesaikan permasalahan klasifikasi, regresi, dan pendeteksian outlier. Tujuannya jelas untuk menemukan hyperlane terbaik untuk memisahkan titik data input dengan jelas.
Libray yang digunakan menggunakan SVC.

Karena kita butuh prediksi kualitas anggur baik/tidak, maka kita perlu definisikan dulu yang nilai apakah anggur baik atau tidak. Dalam studi kasus ini, definisi nilai parameter yang dimaksud adalah:\
Quality >5 = Good. Selain itu Bad Quality (0-5).

## Data Understanding
[Dataset dari UCI Machine LEarning](https://archive.ics.uci.edu/ml/datasets/wine+quality)\
Keseluruhan Total Data yang tersedia adalah 1599 yang tiap data mempunyai 12 parameter yang akan dijelaskan sebagai berikut:\

Input Variable:
* fixed acidity (Keasaman tetap) 
* volatile acidity (Keasaman yang 
* citric acid (Asam Sitrat)
* residual sugar (Kandungan gula)
* chlorides (Klorida)
* free sulfur dioxide (Free SO2)
* total sulfur dioxide(Total SO2)
* density (Kekentalan) 
* pH
* sulphates (Sulfat) 
* alcohol (Alkohol)

Output variable (Based on sensory data):
* Quality (Kualitas. Bernilai 0-10)\
Dataset ini merupakan data bersih di mana tidak ada missing value di parameter apapun.\
Output yang kita harapkan adalah algoritma memberikan penilaian dengan berbagai variable yang dimiliki oleh input baru, anggur tersebut memiliki kualitas seperti apa. Quality adalah target variable

## Data Preparation
Pada data yang sudah disediakan ini, data sudah clean tanpa ada yang perlu diseragamkan lagi oleh teknik PCA ataupun Dimension Reduction.
Data preparation yang kita lakukan ini hanya membagi datatest sebanyak 1:4 yatu 80% data train, 20% data test. 
Selain itu, standarisasi data yang kita pakai menggunakan StandarScaler, yaitu  mengurangkan mean (nilai rata-rata) kemudian membaginya dengan standar deviasiuntuk menggeser distribusi.


## Modeling
Model yang dirancang untuk menyelesaikan masalah ini dengan algoritma SVM. Model ini dipilih karena output yang diharapkan dari hasil prediksi adalah TRUE atau FALSE (dari variable2 yang dimiliki oleh anggur yang didapatkan dari sensor).
Dengan SVM, maka akan ada klasifikasi hyperlane yang memisahkan antara kategori anggur Good / Bad

Hasil akhir dari Model yang dirancang akan mengeluarkan judge kualitas anggur (TRUE/FALSE)

## Evaluation
Hasil dari model yang dibuat dan formula rumus yang digunakan
* **Accuracy: 77.1875**\
Accuracy = TP+TN/TP+FP+FN+TN

* **Precision: 81.17647058823529**\
Precision = TP/TP+FP

* **Recall: 77.09497206703911**\
Recall = TP/TP+FN

Keterangan:
- TP = True Positif, Hasil yang diprediksi benar sesuai label TRUE
- TN = True Negatif, Hasil yang diprediksi benar dengan label FALSE
- FP = False Positif, Hasil yang dinilai benar padahal salah
- FN = False Negatif, Hasil yang dinilai salah padahal benar

**---Ini adalah bagian akhir laporan---**



