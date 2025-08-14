# Analisis Prediksi Kebakaran Hutan

## Tujuan Proyek

Tujuan utama dari proyek ini adalah untuk memprediksi **luas area yang terbakar** pada kebakaran hutan berdasarkan berbagai faktor meteorologi seperti suhu, kelembapan, kecepatan angin, dan indeks kebakaran. Proyek ini menggunakan model pembelajaran mesin untuk memperkirakan luas area yang terbakar, yang merupakan variabel target dalam dataset. Ini dapat digunakan untuk membantu mitigasi kebakaran hutan dengan memprediksi kemungkinan kerusakan berdasarkan kondisi lingkungan.

### Algoritma yang Digunakan:

1. **Support Vector Regression (SVR)**:

   * **SVR** digunakan untuk memprediksi nilai kontinu (dalam hal ini, luas area yang terbakar oleh kebakaran hutan). SVR dipilih karena dapat menangani hubungan non-linear antara fitur dan target.
   * SVR bekerja dengan mencari hyperplane yang memisahkan data secara optimal di ruang fitur. SVR sangat efektif dalam menangani ruang fitur dengan dimensi tinggi, yang membuatnya ideal untuk masalah regresi semacam ini.

2. **Random Forest Regressor**:

   * **Random Forest Regressor** adalah metode pembelajaran ensemble yang membangun banyak pohon keputusan dan menggabungkan prediksi dari pohon-pohon tersebut. Kekuatan Random Forest terletak pada kemampuannya untuk menangani dataset yang kompleks dan besar, serta lebih tahan terhadap overfitting dibandingkan pohon keputusan tunggal.
   * Algoritma Random Forest sangat ideal untuk memprediksi luas area yang terbakar karena dapat menangkap interaksi kompleks antara fitur-fitur serta lebih tahan terhadap overfitting.

3. **Tuning Hyperparameter untuk Random Forest**:

   * **GridSearchCV** digunakan untuk menyetel hyperparameter model Random Forest agar dapat mengoptimalkan parameter seperti jumlah pohon (`n_estimators`), kedalaman maksimum (`max_depth`), dan lainnya. Tuning hyperparameter ini akan meningkatkan kinerja model dengan menemukan konfigurasi terbaik.

## Metodologi

### 1. **Eksplorasi Data (EDA)**:

* Dataset dimuat dan struktur dasar dataset diperiksa menggunakan `df.info()` dan `df.describe()`.
* Histogram dari variabel target **`area`** divisualisasikan untuk memahami distribusinya.

### 2. **Pra-pemrosesan Data**:

* **Transformasi Logaritma** diterapkan pada variabel target **`area`** untuk mengurangi skewness dan menormalkan distribusi.
* **Fitur Kategorikal (Bulan dan Hari)** dikonversi menjadi nilai numerik. **`month`** dipetakan dari nama bulan (misalnya, Jan, Feb) ke angka (1-12), dan **`day`** dipetakan dari nama hari (misalnya, Sen, Sel) ke angka (0-6).
* **Penskalaan Fitur** dilakukan pada fitur numerik seperti **`FFMC`**, **`DMC`**, **`DC`**, **`ISI`**, **`temp`**, **`RH`**, **`wind`**, dan **`rain`** menggunakan **StandardScaler** agar semua fitur berada dalam skala yang sama, yang penting untuk model seperti **SVR**.

### 3. **Pelatihan Model**:

* **Support Vector Regression (SVR)** dan **Random Forest Regressor** dilatih menggunakan data yang telah diproses.
* **GridSearchCV** digunakan untuk tuning hyperparameter model Random Forest, memungkinkan kita untuk menemukan parameter terbaik seperti **`n_estimators`**, **`max_depth`**, **`min_samples_split`**, dll.

### 4. **Evaluasi Model**:

* Kedua model (**SVR** dan **Random Forest**) dievaluasi menggunakan dua metrik utama:

  * **Mean Absolute Error (MAE)**: Mengukur rata-rata perbedaan absolut antara nilai prediksi dan nilai aktual.
  * **Root Mean Squared Error (RMSE)**: Mengukur akar kuadrat dari rata-rata kuadrat perbedaan antara nilai prediksi dan nilai aktual, memberikan lebih banyak bobot pada kesalahan yang lebih besar.

* Model Random Forest disesuaikan menggunakan **GridSearchCV** untuk menemukan kombinasi hyperparameter terbaik, dan kinerjanya dievaluasi lagi pada data uji.

### 5. **Perbandingan Model**:

* Nilai aktual dan prediksi untuk kedua model dibandingkan menggunakan **scatter plot** untuk memvisualisasikan seberapa baik model-model tersebut bekerja pada data yang belum pernah dilihat sebelumnya.

### 6. **Menyimpan dan Mengunduh Data yang Telah Diproses**:

* Dataset yang telah diproses disimpan sebagai **CSV** dan disediakan untuk diunduh menggunakan **Google Colab**.

## Hasil yang Diharapkan

1. **Akurasi Prediksi**: Diharapkan model (**SVR** dan **Random Forest**) dapat memprediksi luas area yang terbakar dengan akurasi tinggi, dengan nilai MAE dan RMSE yang rendah, terutama setelah tuning hyperparameter.
2. **Pemahaman Faktor Meteorologi**: Proyek ini bertujuan untuk memberikan wawasan tentang bagaimana faktor meteorologi mempengaruhi kebakaran hutan dan seberapa besar kerusakan yang ditimbulkan.
3. **Aplikasi Dunia Nyata**: Model yang dikembangkan dapat digunakan oleh pihak berwenang untuk memprediksi kerusakan kebakaran hutan dan mengalokasikan sumber daya dengan lebih efektif.

## Menjalankan Proyek

### 1. **Clone Repositori**:

Anda dapat meng-clone atau mengunduh repositori ini dengan menjalankan perintah berikut:

```bash
git clone https://github.com/username/forest-fire-analysis.git
```

### 2. **Install Dependencies**:

Untuk menginstal pustaka yang diperlukan untuk menjalankan proyek, gunakan perintah berikut:

```bash
pip install -r requirements.txt
```

### 3. **Jalankan Skrip**:

Anda bisa menjalankan skrip Python yang memproses data, melatih model, dan mengevaluasi hasilnya dengan perintah berikut:

```bash
python forestfires_analysis.py
```

### 4. **Unduh Dataset yang Telah Diproses**:

Setelah model dijalankan, dataset yang telah diproses akan disimpan sebagai file CSV dan bisa diunduh melalui **Google Colab**.

### 5. **Lihat Hasil**:

Output akan mencakup metrik evaluasi (MAE dan RMSE) untuk kedua model, dan visualisasi akan menunjukkan perbandingan antara nilai aktual dan prediksi.

## Lisensi

Proyek ini dilisensikan di bawah **MIT License** - lihat file [LICENSE](LICENSE) untuk detail lebih lanjut.

---

### **Penjelasan README**:

1. **Tujuan Proyek**:

   * README ini menjelaskan tujuan proyek untuk memprediksi **luas area yang terbakar** pada kebakaran hutan menggunakan model pembelajaran mesin (SVR dan Random Forest Regressor).
   * Menjelaskan pemilihan algoritma yang sesuai berdasarkan kemampuan mereka untuk menangani masalah kompleksitas dan skala yang besar.

2. **Algoritma yang Digunakan**:

   * **SVR** dipilih karena kemampuannya untuk menangani hubungan non-linear antara fitur dan variabel target.
   * **Random Forest Regressor** digunakan karena dapat menangkap interaksi fitur yang lebih kompleks dan lebih tahan terhadap overfitting.
   * **GridSearchCV** digunakan untuk tuning hyperparameter **Random Forest** agar model bekerja dengan lebih baik.

3. **Metodologi**:

   * Penjelasan yang mendalam tentang setiap langkah, mulai dari eksplorasi data, pra-pemrosesan, pelatihan model, evaluasi model, hingga visualisasi dan penyimpanan data yang telah diproses.

4. **Menjalankan Proyek**:

   * Instruksi tentang cara meng-clone repositori, menginstal pustaka yang diperlukan, dan menjalankan proyek di lingkungan lokal atau **Google Colab**.

README ini memberikan penjelasan komprehensif dan jelas tentang proyek, tujuan, algoritma, serta cara menjalankannya. Jika Anda memerlukan penyesuaian lebih lanjut atau memiliki pertanyaan lainnya, beri tahu saya!
