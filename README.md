# Deteksi Penipuan Transaksi Bank (Bank Transaction Fraud Detection)

## Deskripsi Proyek

Repositori ini berisi proyek Machine Learning end-to-end yang berfokus pada deteksi transaksi perbankan yang mencurigakan (fraud). Proyek ini terdiri dari dua fase utama: pembelajaran tanpa pengawasan (Unsupervised Learning) untuk segmentasi pelanggan menggunakan algoritma Clustering, dan pembelajaran terawasi (Supervised Learning) untuk pemodelan klasifikasi deteksi penipuan.

Tujuan utama dari proyek ini adalah memanfaatkan data transaksi yang belum berlabel untuk mengelompokkan pelanggan berdasarkan perilaku mereka, mengidentifikasi segmen berisiko tinggi, dan membangun model prediktif untuk mengklasifikasikan transaksi di masa mendatang.

## Teknologi yang Digunakan

- Python 3.x
- Pandas (Manipulasi Data)
- Scikit-Learn (Pemodelan Machine Learning)
- Matplotlib & Seaborn (Visualisasi Data)
- Yellowbrick (Evaluasi Model Clustering)
- Jupyter Notebook (Eksplorasi Data dan Eksekusi Kode)

## Struktur Repositori

- **[Clustering]\_Submission_Akhir_BMLP_Haerul_Yuda_Aditiya.ipynb**: Jupyter Notebook yang memuat seluruh alur kerja proses clustering.
- **[Klasifikasi]\_Submission_Akhir_BMLP_Haerul_Yuda_Aditiya.ipynb**: Jupyter Notebook yang memuat seluruh alur kerja pemodelan klasifikasi.

* **data_clustering.csv**: Dataset hasil pemrosesan akhir dari fase clustering, yang telah dilengkapi dengan kolom label baru bernama 'Target'.
* **data_clustering_inverse.csv**: Versi dataset clustering yang telah dikembalikan ke skala aslinya (inverse transform) untuk keperluan interpretasi profil pelanggan secara bisnis.
* **model_clustering.h5 & PCA_model_clustering.h5**: Model KMeans dan PCA yang telah dilatih dan disimpan.
* **decision_tree_model.h5 & explore_RandomForest_classification.h5**: Model klasifikasi prediktif (Decision Tree dan Random Forest) yang telah dilatih dan disimpan.

## Metodologi

### 1. Fase Clustering (Segmentasi Pelanggan)

- **Exploratory Data Analysis (EDA)**: Memahami distribusi data, menangani anomali, serta melihat korelasi antar fitur transaksi.
- **Pra-pemrosesan Data (Preprocessing)**: Penanganan nilai yang hilang (missing values), penghapusan data duplikat, eliminasi kolom spesifik yang tidak relevan (seperti ID, IP, dan Tanggal), categorical label encoding untuk merubah nilai teks menjadi angka, serta penanganan outlier menggunakan metode IQR.
- **Penskalaan Fitur (Scaling)**: Standarisasi jarak fitur numerik menggunakan StandardScaler.
- **Rekayasa Fitur (Feature Engineering)**: Melakukan binning pada kelompok usia nasabah ('CustomerAge').
- **Pemodelan**: Implementasi algoritma K-Means Clustering. Jumlah cluster yang paling optimal ditentukan secara matematis menggunakan metode Elbow (Distortion) dan divalidasi dengan skor kohesi Silhouette Index. Principal Component Analysis (PCA) digunakan untuk mengurangi dimensi fitur sehingga sebaran cluster dapat divisualisasikan menggunakan diagram scatter 2D.
- **Interpretasi**: Menganalisis karakteristik setiap cluster menggunakan statistik deskriptif mean/max/min. Berdasarkan analisis kebiasaan belanja dan frekuensi login, setiap segmen kemudian diberikan label final ('Target') mengacu pada tingkat risiko mereka.

### 2. Fase Klasifikasi (Prediksi Fraud)

- **Persiapan Data Terlabel**: Memuat dataset hasil prediksi dari fase clustering (kolom 'Target') dan membagi dataset menjadi set pelatihan (train) dan pengujian (test).
- **Pemodelan Baseline**: Membangun algoritma klasifikasi pertama menggunakan Decision Tree Classifier.
- **Eksplorasi Metode Pembelajaran Ensembel**: Menggunakan model yang lebih kompleks yakni Random Forest Classifier, lengkap dengan penyetelan hyperparameter (GridSearchCV) untuk mendapatkan prediksi yang paling akurat tanpa overfitting.
- **Evaluasi Kinerja**: Menguji kinerja prediksi model-model di atas menggunakan Confusion Matrix serta metrik pengukuran seperti Akurasi, Presisi, Recall, dan F1-Score.

## Cara Penggunaan

1. Klon (clone) repositori ini ke komputer lokal Anda.
2. Pastikan Anda telah menginstal seluruh pustaka yang dibutuhkan dengan menjalankan perintah `pip install pandas numpy scikit-learn matplotlib seaborn yellowbrick jupyter joblib`.
3. Buka file ekstensi `.ipynb` melalui Jupyter Notebook, VS Code, atau Google Colab untuk mendalami analisis serta mengeksekusi kode per tahap.
