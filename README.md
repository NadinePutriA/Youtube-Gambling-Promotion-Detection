# Youtube-Gambling-Promotion-Detection
Deteksi promosi judi online pada komentar YouTube berbahasa Indonesia menggunakan Support Vector Machine (SVM) dan Multilayer Perceptron (MLP), dengan perbandingan tiga skenario preprocessing dan normalisasi character obfuscation.


**Deteksi Promosi Judi Online pada Komentar YouTube Berbahasa Indonesia**

**Deskripsi Proyek**

Proyek ini membahas penerapan machine learning untuk mendeteksi komentar promosi judi online pada YouTube berbahasa Indonesia. Penelitian menggunakan algoritma Support Vector Machine (SVM) dan Multilayer Perceptron (MLP) serta membandingkan tiga skenario preprocessing teks untuk mengetahui pengaruh normalisasi character obfuscation terhadap performa klasifikasi.

Character obfuscation merupakan teknik penyamaran teks menggunakan karakter Unicode, simbol dekoratif, atau angka sebagai pengganti huruf sehingga kata tertentu menjadi lebih sulit dikenali oleh sistem deteksi otomatis.

**Tujuan**

1. Mendeteksi komentar YouTube yang mengandung promosi judi online.
2. Membandingkan performa algoritma SVM dan MLP.
3. Menganalisis pengaruh tiga skenario preprocessing terhadap hasil klasifikasi.
4. Mengevaluasi efektivitas normalisasi character obfuscation dalam meningkatkan deteksi komentar promosi judi online.

**Dataset**

Dataset yang digunakan adalah Judi Online dari Kaggle.
- Sumber: https://www.kaggle.com/datasets/yaemico/judionline
- Jumlah data awal: 10.230 komentar.
- Jumlah data setelah cleaning: 9.001 komentar.
- Bahasa: Indonesia.
- Label 0: Komentar normal.
- Label 1: Komentar promosi judi online.
Atribut utama yang digunakan meliputi komentar, label, dan komentar_clean. Kolom tanggal juga digunakan untuk analisis tren waktu.

**Metodologi**


**1. Data Cleaning dan Exploratory Data Analysis**

Tahap awal mencakup pemeriksaan missing value, penghapusan data duplikat, validasi label, analisis distribusi kelas, panjang komentar, frekuensi kata, word cloud, bigram, dan pola character obfuscation.

**2. Text Preprocessing**

Penelitian membandingkan tiga skenario preprocessing:
- Standard Preprocessing: pembersihan teks dasar, lowercase, penghapusan URL dan simbol, tokenisasi, stopword removal, serta stemming.
- Advanced Preprocessing: preprocessing standar dengan tambahan Unicode normalization, penggabungan karakter yang terpisah, normalisasi leetspeak, dan penggantian simbol tertentu.
- Dataset Clean Preprocessing: menggunakan kolom komentar_clean yang tersedia pada dataset, kemudian melakukan pembersihan lanjutan.

**3. Feature Extraction**

Teks diubah menjadi representasi numerik menggunakan TF-IDF dengan kombinasi unigram dan bigram. Jumlah fitur dibatasi hingga 10.000 fitur.

**4. Pembagian Data**

Dataset dibagi menjadi 80% data training dan 20% data testing menggunakan stratified split agar proporsi kelas tetap terjaga.

**5. Pemodelan**

Dua algoritma yang digunakan:
- Support Vector Machine (SVM).
- Multilayer Perceptron (MLP).
Kedua algoritma dievaluasi pada ketiga skenario preprocessing untuk mengetahui kombinasi yang memberikan hasil terbaik.

**6. Evaluasi Model**

Evaluasi dilakukan menggunakan accuracy, precision, recall, F1-score, confusion matrix, cross-validation, runtime comparison, dan error analysis. Recall menjadi salah satu perhatian utama karena penelitian berfokus pada deteksi komentar promosi judi online.

**Konteks Akademik**

Proyek akhir mata kuliah Pembelajaran Mesin
Program Studi Sains Data
Universitas Negeri Surabaya

**Catatan**

Proyek ini dibuat untuk keperluan akademik dan penelitian klasifikasi teks. Hasil model merupakan prediksi otomatis dan tidak menjamin seluruh komentar dapat diklasifikasikan dengan benar. Penggunaannya untuk moderasi konten nyata tetap memerlukan evaluasi lebih lanjut.
