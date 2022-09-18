# Laporan Proyek Machine Learning - Abimanyu Sri Setyo

## Domain Proyek
Organisasi Kesehatan Dunia (WHO) memperkirakan 12 juta kematian terjadi di seluruh dunia, setiap tahun karena penyakit jantung. Setengah dari kematian di Amerika Serikat dan negara maju lainnya disebabkan oleh penyakit kardiovaskular. Prognosis awal penyakit kardiovaskular dapat membantu dalam membuat keputusan tentang perubahan gaya hidup pada pasien berisiko tinggi dan pada gilirannya mengurangi komplikasi. Penelitian ini bertujuan untuk menunjukkan dengan tepat faktor/faktor risiko penyakit jantung yang paling relevan, serta memprediksi risiko secara keseluruhan menggunakan regresi logistik.

Pada proyek ini, dataset berasal dari situs web [Kaggle](https://www.kaggle.com/datasets/dileep070/heart-disease-prediction-using-logistic-regression), dan berasal dari studi kardiovaskular yang sedang berlangsung pada penduduk kota Framingham, Massachusetts. Tujuannya adalah untuk memprediksi apakah pasien memiliki risiko 10 tahun penyakit jantung koroner (PJK). Dataset menyediakan informasi pasien. Ini mencakup lebih dari 4.000 catatan dan 15 atribut.

Daftar Pustaka:
- Kemenkes, (2017). *Penyakit Jantung Penyebab Kematian Tertinggi, Kemenkes Ingatkan CERDIK*. Tersedia di:
<https://www.kemkes.go.id/article/view/17073100005/penyakit-jantung-penyebab-kematian-tertinggi-kemenkes-ingatkan-cerdik-.html> [Diakses 17 September 2022]
- Gobel, F. A., Mahkota, R, (2006). *Faktor-faktor yang Mempengaruhi Kematian Pasien Penyakit Jantung Koroner di Pusat Jantung Nasional Harapan Kita Tahun 2004*. Tersedia di:
<https://journal.fkm.ui.ac.id/kesmas/article/view/303/303> [Diakses 17 September 2022]
- Suryadi, T., (2017). *Kematian Mendadak Kardiovaskuler*. Tersedia di:
<http://www.jurnal.unsyiah.ac.id/JKS/article/view/8990> [Diakses 17 September 2022]


## Business Understanding
### Problem Statement:
- Bagaimana cara prediksi apakah seseorang beresiko menderita penyakit jantung atau tidak dalam beberapa tahun kedepan dari statistik kesehatannya?

### Goals:
- Memprediksi apakah seseorang memiliki resiko menderita penyakit jantung atau tidak dalam beberapa tahun kedepan dari statistik kesehatannya.

### Solution Statements:
- Menggunakan metode Logistic Regression, dimana metode ini merupakan metode yang efektif untuk melakukan klasifikasi yang outputnya hanya 0 dan 1 atau True/False.
- Menggunakan metode Random Forest, dimana metode ini simpel untuk diimplementasikan, namun powerful. Maka dari itu, Random Forest digunakan sebagai pembanding dari Logistic Regression.
- Sebagai pembanding, menggunakan dua metrik antara lain **Nilai Akurasi** dan **Mean Squared Error**.



## Data Understanding
### Overview Dataset:
Dataset yang digunakan adalah **Heart Diseases** yang bersumber dari [Kaggle](https://www.kaggle.com/datasets/dileep070/heart-disease-prediction-using-logistic-regression). Dikutip dari [algorit.ma](https://algorit.ma/blog/exploratory-data-analysis-2022/), Analisis Data Eksplorasi mencakup proses kritis uji investigasi pendahuluan pada data untuk mengidentifikasi pola, menemukan anomali, menguji hipotesis , dan periksa asumsi melalui statistik ringkasan dan representasi grafis (visual).
- Dataset ini terdiri dari 4238 baris data, dan memiliki 16 kolom data.

![1](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/1.png)

![2](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/2.png)

- Dataset memiliki beberapa nilai kosong atau NaN yang perlu dilakukan penanganan.

![3](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/3.png)

Dataset Titanic bersumber dari https://www.kaggle.com/c/titanic/data.
### Fitur pada dataset:
Dataset ini, ada 10 variabel dengan 9 fitur dan 1 label sebagai berikut.	
- Demografi singkat:
	- Sex: male or female
	- Age: Age of the patient
- Perilaku responden:
	- Current Smoker: Perokok atau bukan.
	- Cigs Per Day: Konsumsi batang rokok perhari
	- BP Meds: Apakah mengambil *Blood Pressure Medication* atau tidak.
	- Prevalent Stroke: Pernah stroke atau tidak.
	- Prevalent Hyp: Pernah hipertensi atau tidak.
	- Diabetes: Pernah diabetes atau tidak.
- Statistika:
	- Tot Chol: total level kolesterol
	- Sys BP: tekanan darah *systolic*
	- Dia BP: tekanan darah *diastolic*
	- BMI: *Body Mass Index* atau indeks massa tubuh
	- Heart Rate: *heart rate* atau detak jantung
	- Glucose: glucose level (Continuous)
- Variabel prediksi:
	- 10 year risk of coronary heart disease CHD (binary: “1” : Iya”, “0” : “Tidak”)

### Korelasi pada dataset:
Untuk menjelaskan korelasi fitur – fitur pada dataset, diperlukan visualisasi data yang terdiri sebagai berikut. Namun, ada baiknya untuk melihat NaN values yang dimiliki oleh dataset dan dilakukan penanganan. Menurut [DQLab.id](https://www.dqlab.id/kursus-belajar-data-mengenal-apa-itu-missing-value), nilai NaN akan membuat data tidak dapat digunakan, dan sayang untuk dibuang begitu saja. Informasi penting di banyak baris hanya karena 1-2 nilai yang hilang, jadi salah satu langkah yang tepat adalah mengisi nilai yang hilang. Pengisian data menggunakan median akan membantu “menetralisir” data yang hilang, karena pengisian median tidak akan menggeser atau menambah varians data.

![3](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/3.png)

#### Univariate Analysis
-   Barplot Pertama

	![5](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/5.png)

	Pada barplot pertama yang ada pada notebook, dapat disimpulkan bahwa lebih sedikit responden yang berjenis kelamin *male*.

-   Barplot Kedua

	![6](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/6.png)

	Pada barplot kedua yang ada pada notebook, dapat disimpulkan bahwa responden yang bukan perokok sedikit lebih tinggi dibandingkan responden yang merupakan perokok.

-   Barplot Ketiga

	![7](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/7.png)

	Pada barplot ketiga, dapat disimpulkan bahwa responden yang tidak memiliki riwayat stroke lebih tinggi dibandingkan responden yang memiliki riwayat stroke.

-   Barplot Keempat

	![8](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/8.png)

	Pada barplot keempat, dapat disimpulkan bahwa responden yang tidak memiliki riwayat hipertensi lebih tinggi dibandingkan responden yang memiliki riwayat hipertensi.

-   Barplot Kelima

	![9](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/9.png)

	Pada barplot kelima, dapat disimpulkan bahwa responden yang tidak memiliki riwayat diabetes lebih tinggi dibandingkan responden yang memiliki riwayat diabetes.

-   Barplot Keenam

	![10](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/10.png)

	Pada barplot kelima, dapat disimpulkan bahwa responden yang tidak memiliki resiko penyakit jantung dalam kurun 10 tahun kedepan lebih tinggi dibandingkan responden yang memiliki resiko penyakit jantung dalam kurun 10 tahun kedepan.

-   Barplot Keenam

	![11](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/11.png)

	Pada barplot keenam, dapat diketahui fitur numerical responden yang memiliki resiko penyakit jantung.

#### Multivariate Analysis

![12](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/12.png)

Dari heatmap pada notebook, dapat terlihat bahwa semua fitur berkorelasi.

## Data Preparation

Dalam data preparation, dilakukan beberapa hal berikut sebelum memasukkan data ke model latih:

-	Drop column yang kurang relevan<br>
	Drop column yang kurang relevan. Hal ini akan membantu efektivitas dalam fitting model yang dilakukan.
-	Mengisi missing value dengan median<br>
	Pengisian data dengan menggunakan median akan membantu "menetralkan" data yang hilang, karena pengisian median tidak akan menggeser atau menambah varians dari data.
-	Train-Test-Split<br>
	Membagi dataset menjadi data latih dan data validasi  dilakukan supaya kita dapat melakukan validasi dengan benar tanpa bias dari model.
-	Standarisasi<br>
	Scaling ini dilaksanakan untuk membantu model machine learning yang akan dipakai lebih mudah diolah.

## Modeling

Model – model yang saya pakai dalam projek ini adalah:
-	**Logistic Regression**<br>
    Logistic Regression adalah sebuah algoritma klasifikasi di mana algoritma ini mencari hubungan antar fitur diskrit/kontinu dengan probabilitias hasi loutput diskrit tertentu.
-	**Random Forest**<br>
	Random Forest merupakan algoritma yang menggabungkan keluaran dari beberapa pohon keputusan untuk mencapai satu hasil dengan dibentuk dari banyak pohon (tree) yang diperoleh melalui proses bagging atau bootstrap aggregating.

Berikut adalah hasil akurasi model:

![13](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/13.png)

## Evaluasi
Penggunaan Regresi Logistik dalam data terbukti lebih baik berdasarkan metrik akurasi yang diberikan. Namun terdapat anomali berupa MSE dari Regresi Logistik yang lebih tinggi dari Random Forest. Dari hasil pemodelan ini, Regresi Logistik dipilih sebagai model yang akan digunakan dalam prediksi PJK.

Sebelum ke metrik evaluasi, terlebih dahulu kita harus mengerti tentang confusion matrix.
 
Di dalam confusion matrix, terdapat 4 kesimpulan yang dapat kita ambil:
-	True Positive (TP): Jumlah prediksi positif yang benar terhadap jumlah positif yang sebenarnya.
-	False Positive (FP): Jumlah prediksi positif yang salah.
-	True Negative (TN): Jumlah prediksi negatif yang benar terhadap jumlah negatif yang sebenarnya.
-	False Negative (FN): Jumlah prediksi negatif yang salah.

Dalam projek ini, metrik evaluasi yang idgunakan adalah sebagai berikut.
-	**Accuracy**<br>
	Akurasi adalah metrik yang paling umum dalam pemodelan klasifikasi. Ini adalah persentase jumlah data yang diprediksi dengan benar terhadap jumlah total data.
-	**MSE** 
	<br>Mean Squared Error (MSE) adalah Rata-rata Kesalahan kuadrat diantara nilai aktual dan nilai prediksi. Metode Mean Squared Error secara umum digunakan untuk mengecek estimasi berapa nilai kesalahan pada predoksi.

Berikut adalah hasil akurasi model:

![13](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/13.png)

Berikut adalah hasil MSE model:

![14](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/14.png)

![15](https://raw.githubusercontent.com/bzizmza/First-Project---Predictive-Analytics/main/img/15.png)