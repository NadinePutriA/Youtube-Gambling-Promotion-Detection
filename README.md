# Youtube-Gambling-Promotion-Detection
Deteksi promosi judi online pada komentar YouTube berbahasa Indonesia menggunakan Support Vector Machine (SVM) dan Multilayer Perceptron (MLP), dengan perbandingan tiga skenario preprocessing dan normalisasi character obfuscation.

## Deskripsi Proyek

Proyek ini mengimplementasikan machine learning untuk mendeteksi komentar promosi judi online pada platform YouTube menggunakan pendekatan Natural Language Processing (NLP). Penelitian berfokus pada perbandingan algoritma Support Vector Machine (SVM) dan Multilayer Perceptron (MLP), serta pengaruh normalisasi *character obfuscation* terhadap performa klasifikasi teks berbahasa Indonesia.

Character obfuscation merupakan teknik penyamaran teks menggunakan karakter Unicode, simbol dekoratif, angka, atau variasi penulisan tertentu untuk menghindari deteksi otomatis. Untuk mengatasi permasalahan tersebut, proyek ini menerapkan beberapa skenario preprocessing dan membandingkan hasil klasifikasinya.

Proyek ini dikembangkan sebagai tugas akhir mata kuliah Pembelajaran Mesin pada Program Studi S1 Sains Data, Universitas Negeri Surabaya.

## Tujuan Proyek

- Mengembangkan model untuk mengklasifikasikan komentar YouTube menjadi komentar normal dan komentar promosi judi online.
- Menganalisis pengaruh normalisasi character obfuscation terhadap performa klasifikasi.
- Membandingkan performa algoritma SVM dan MLP pada beberapa skenario preprocessing.
- Menentukan kombinasi preprocessing dan model terbaik berdasarkan hasil evaluasi.
- Menganalisis kesalahan prediksi dan efisiensi komputasi model.

## Dataset

Dataset yang digunakan adalah **Judi Online**, yang diperoleh dari Kaggle.

Sumber dataset: https://www.kaggle.com/datasets/yaemico/judionline

Dataset awal terdiri dari 10.230 komentar YouTube berbahasa Indonesia. Setelah proses pembersihan data, sebanyak 9.001 komentar digunakan dalam penelitian.

Label klasifikasi terdiri dari:
- `0`: Komentar normal.
- `1`: Komentar promosi judi online.

Atribut utama yang digunakan adalah:
- `komentar`: teks komentar asli.
- `label`: kategori target klasifikasi.
- `komentar_clean`: teks komentar yang telah dibersihkan.
- `tanggal`: tanggal komentar untuk analisis tren temporal.

## Metodologi

### 1. Data Cleaning dan Seleksi Data

Tahap awal meliputi pemeriksaan missing value, penghapusan komentar duplikat, pemeriksaan konsistensi label, dan pemilihan atribut yang relevan untuk penelitian.

### 2. Exploratory Data Analysis (EDA)

EDA dilakukan untuk memahami karakteristik dataset melalui:
- Distribusi label komentar.
- Analisis panjang komentar.
- Frekuensi kata dan pasangan kata (*bigram*).
- Word cloud untuk setiap kategori.
- Identifikasi pola character obfuscation.
- Analisis variasi penulisan kata pada komentar promosi judi online.

### 3. Text Preprocessing

Penelitian membandingkan tiga skenario preprocessing:

**Standard Preprocessing**
- Mengubah teks menjadi huruf kecil.
- Menghapus URL, mention, tanda baca, dan karakter yang tidak diperlukan.
- Melakukan tokenisasi.
- Menghapus stopword.
- Melakukan stemming menggunakan Sastrawi.

**Advanced Preprocessing**
Menggunakan tahapan standard preprocessing dengan tambahan normalisasi untuk menangani character obfuscation, meliputi Unicode normalization, penggabungan karakter yang dipisahkan spasi, penggantian simbol, normalisasi angka dan huruf, serta normalisasi leetspeak secara selektif.

**Dataset Clean Preprocessing**
Menggunakan kolom `komentar_clean` yang tersedia dalam dataset, kemudian melakukan pemrosesan lanjutan seperti lowercase, penghapusan spasi berlebih, tokenisasi, stopword removal, dan stemming.

### 4. Feature Extraction

Teks hasil preprocessing diubah menjadi representasi numerik menggunakan **TF-IDF (Term Frequency-Inverse Document Frequency)** dengan fitur unigram dan bigram. Jumlah fitur dibatasi hingga 10.000 fitur teratas.

### 5. Data Splitting

Dataset dibagi menjadi:
- 80% data training.
- 20% data testing.

Pembagian dilakukan menggunakan stratified split untuk mempertahankan proporsi kelas pada data training dan testing.

### 6. Model Training

Dua algoritma klasifikasi yang digunakan adalah:

- **Support Vector Machine (SVM):** digunakan untuk mengklasifikasikan komentar berdasarkan representasi TF-IDF.
- **Multilayer Perceptron (MLP):** digunakan sebagai model pembanding yang mampu mempelajari pola nonlinier pada data teks.

Kedua model diuji menggunakan ketiga skenario preprocessing untuk membandingkan performanya.

### 7. Evaluasi dan Perbandingan Model

Evaluasi dilakukan menggunakan:
- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- 5-fold cross-validation
- Runtime comparison
- Error analysis

Recall menjadi salah satu metrik penting karena komentar promosi judi online yang tidak terdeteksi berpotensi tetap tersebar pada platform.

## Hasil Penelitian

Berdasarkan hasil penelitian, kombinasi **SVM dengan Advanced Preprocessing** menghasilkan performa terbaik.

| Metrik | Hasil |
|---|---:|
| Accuracy | 97,83% |
| F1-score | 96,69% |
| Mean F1-score 5-fold cross-validation | 95,85% |
| Runtime tercepat yang dilaporkan | Sekitar 0,02 detik |

Hasil analisis juga menemukan:
- Sebanyak 1.875 komentar teridentifikasi menggunakan Unicode obfuscation.
- Sebanyak 1.665 komentar teridentifikasi menggunakan substitusi angka.
- Kata seperti `alexis17`, `gacor`, `wd`, dan `maxwin` termasuk keyword yang dominan pada analisis komentar promosi judi online.

Advanced Preprocessing membantu menormalkan variasi penulisan sehingga kata yang disamarkan dapat lebih mudah dikenali dalam proses klasifikasi.

Hasil tersebut menunjukkan bahwa kualitas preprocessing, khususnya normalisasi character obfuscation, berperan penting dalam mendukung deteksi komentar promosi judi online.

## Konteks Akademik

Program Studi S1 Sains Data  
Fakultas Matematika dan Ilmu Pengetahuan Alam  
Universitas Negeri Surabaya
Mata Kuliah: Pembelajaran Mesin  
