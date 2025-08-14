# Forest Fire Analysis

Proyek ini bertujuan untuk menganalisis dataset kebakaran hutan di Portugal dan membangun model untuk memprediksi luas area yang terbakar (variabel target). Dataset yang digunakan mengandung berbagai fitur meteorologi seperti suhu, kelembapan, kecepatan angin, serta indeks kebakaran yang dapat digunakan untuk memprediksi luas area yang terbakar.

## Deskripsi Dataset

Dataset **Forest Fires** berasal dari [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/162/forest+fires) dan memiliki 517 entri dengan 13 atribut. Atribut-atribut tersebut meliputi:

- **FFMC (Fine Fuel Moisture Code)**: Kode kelembapan bahan bakar halus.
- **DMC (Duff Moisture Code)**: Kode kelembapan bahan bakar kasar.
- **DC (Drought Code)**: Kode kekeringan.
- **ISI (Initial Spread Index)**: Indeks penyebaran awal.
- **temp (Temperature)**: Suhu udara.
- **RH (Relative Humidity)**: Kelembapan relatif.
- **wind (Wind speed)**: Kecepatan angin.
- **rain (Rainfall)**: Curah hujan.
- **month (Month)**: Bulan kebakaran terjadi.
- **day (Day)**: Hari kebakaran terjadi.
- **area (Area burned in ha)**: Luas area yang terbakar (variabel target yang ingin diprediksi).

## Tujuan Proyek

Tujuan utama proyek ini adalah untuk membangun model prediksi untuk luas area yang terbakar berdasarkan data meteorologi dan indeks kebakaran. Beberapa algoritma yang digunakan dalam proyek ini adalah:

- **Support Vector Regression (SVR)**: Digunakan untuk menangani data yang memiliki hubungan non-linear antara fitur dan target.
- **Random Forest Regressor**: Digunakan untuk menangani data yang lebih besar dan lebih kompleks, serta mengurangi risiko overfitting.

## Algoritma yang Digunakan

1. **Support Vector Regression (SVR)**:
   - **SVR** adalah algoritma regresi yang berbasis pada konsep **Support Vector Machines (SVM)**. Algoritma ini digunakan ketika data memiliki hubungan non-linear yang sulit untuk dimodelkan menggunakan teknik regresi linear. SVR cocok digunakan karena kemampuan untuk menangani kompleksitas hubungan antar fitur dan target variabel.

2. **Random Forest Regressor**:
   - **Random Forest** adalah model ensemble yang membangun beberapa pohon keputusan dan menggabungkan hasil dari semua pohon tersebut untuk membuat prediksi. Model ini digunakan untuk menangani masalah dengan banyak fitur dan dapat mengatasi hubungan non-linear dengan baik. Selain itu, Random Forest membantu mengurangi masalah **overfitting** yang biasa terjadi pada model pohon keputusan tunggal.

## Metodologi

1. **Eksplorasi Data Awal**: Dataset dieksplorasi untuk memahami distribusi data dan statistik deskriptif. Visualisasi distribusi luas area kebakaran juga dilakukan untuk mengetahui skewness dan distribusi data.
   
2. **Pra-pemrosesan Data**:
   - **Log Transformation**: Dilakukan pada variabel target **area** yang sangat skewed untuk membuat distribusi data lebih normal.
   - **Konversi Variabel Kategorikal ke Numerik**: Variabel **month** dan **day** yang berupa kategori dikonversi menjadi numerik untuk memudahkan pemodelan.
   - **Standardisasi Fitur Numerik**: Fitur numerik seperti **FFMC**, **DMC**, **DC**, **ISI**, **temp**, **RH**, **wind**, dan **rain** distandarisasi menggunakan **StandardScaler**.

3. **Pembangunan Model**:
   - **SVR** dan **Random Forest Regressor** dilatih dengan data latih, dan hasil prediksi dievaluasi menggunakan **Mean Absolute Error (MAE)** dan **Root Mean Squared Error (RMSE)**.

4. **Hyperparameter Tuning**:
   - **GridSearchCV** digunakan untuk mencari kombinasi hyperparameter terbaik untuk **Random Forest Regressor**, seperti **n_estimators**, **max_depth**, **min_samples_split**, **min_samples_leaf**, dan **bootstrap**.

5. **Evaluasi Model**:
   - Setelah melatih model, hasilnya dievaluasi menggunakan **MAE** dan **RMSE** untuk mengetahui akurasi model dalam memprediksi luas area kebakaran.

6. **Visualisasi**:
   - Visualisasi perbandingan antara nilai aktual dan prediksi untuk kedua model (SVR dan Random Forest Regressor) menggunakan **scatter plot**.

## Hasil yang Diharapkan

- **Akurasi Prediksi**: Diharapkan model **SVR** dan **Random Forest Regressor** dapat memprediksi luas area yang terbakar dengan akurasi yang tinggi.
- **Pemahaman tentang Faktor-faktor Meteorologi**: Proyek ini juga bertujuan untuk memberikan wawasan lebih dalam tentang bagaimana faktor-faktor meteorologi mempengaruhi kebakaran hutan.
- **Aplikasi Dunia Nyata**: Model yang dikembangkan dapat digunakan oleh pihak berwenang untuk merencanakan pencegahan kebakaran dan mengalokasikan sumber daya secara lebih efektif.

## Tantangan yang Dihadapi

- **Data yang Tidak Seimbang**: Dataset cenderung memiliki lebih banyak kebakaran kecil dengan area yang terbakar lebih sedikit. Ini dapat memengaruhi hasil model. Penyeimbangan data atau teknik khusus bisa digunakan untuk mengatasi masalah ini.
- **Overfitting**: Pada model yang lebih sederhana, seperti **SVR** dan **Random Forest** yang tidak di-tune, mungkin ada risiko overfitting. Namun, penggunaan **GridSearchCV** untuk tuning hyperparameter dapat mengurangi risiko tersebut.

## Kesimpulan

Dengan menggunakan **Support Vector Regression** dan **Random Forest Regressor**, proyek ini bertujuan untuk memprediksi luas area kebakaran hutan secara akurat. Kedua model memiliki keunggulan dalam menangani hubungan non-linear antar fitur dan target variabel, serta dalam mengatasi data yang lebih kompleks. Tuning hyperparameter pada **Random Forest** akan lebih meningkatkan performa model.

## Instalasi dan Penggunaan

1. **Install dependencies**:
   - Pastikan semua pustaka yang dibutuhkan terpasang menggunakan **`requirements.txt`**:
     ```bash
     pip install -r requirements.txt
     ```

2. **Jalankan Kode**:
   - Jalankan skrip Python di atas untuk memuat dataset, melakukan pra-pemrosesan data, melatih model, dan mengevaluasi hasil.

3. **Menyimpan ke GitHub**:
   - Gunakan **Git** untuk menyimpan kode, output, dan dataset di GitHub.
   - Repositori GitHub dapat diakses di: **[https://github.com/username/forest-fires-analysis](https://github.com/username/forest-fires-analysis)**.

## Referensi

- Dataset **Forest Fires**: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/162/forest+fires)

---

### **Langkah berikutnya:**
- Anda dapat mengontribusikan ke repositori atau memperbarui dengan model yang lebih canggih atau teknik pemrosesan data lanjutan untuk meningkatkan akurasi lebih lanjut.
