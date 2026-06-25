# Prediksi Nilai Ujian (Exam Score) - Pendekatan Regresi

## Anggota Kelompok
1. Verdina Tista Pudyawardhana (K1D024002)
2. Nabila Alsa Haryanto        (K1D024006)
3. Frisca Putri Aulia          (K1D024008)
4. Wuri Dwi Ariyanti           (K1D024025)
5. Dionisius Antoni Pratama    (K1D024031)

## Deskripsi Proyek
Proyek ini bertujuan untuk memprediksi nilai ujian mahasiswa berdasarkan berbagai faktor seperti durasi belajar, tingkat kehadiran, durasi tidur, penggunaan internet, jumlah tugas yang diselesaikan, dan nilai sebelumnya. Model machine learning yang digunakan meliputi Linear Regression, Decision Tree Regressor, dan Random Forest Regressor.

## Dataset
Dataset yang digunakan adalah Student Performance Prediction Dataset yang terdiri dari 1.999 observasi dan 8 variabel:
- `study_hours`: Jumlah jam belajar per minggu
- `attendance`: Persentase kehadiran (%)
- `sleep_hours`: Jumlah jam tidur rata-rata per hari
- `internet_usage`: Penggunaan internet dalam jam
- `assignments_completed`: Jumlah tugas yang diselesaikan
- `previous_score`: Nilai ujian sebelumnya
- `placement_status`: Status penempatan (Placed / Not Placed)
- **`exam_score`**: Nilai ujian akhir siswa (Target Variable)

## Cara Penggunaan (Google Colab)
Untuk menjalankan kode dari awal hingga akhir, ikuti langkah-langkah berikut:

1. Pastikan Anda telah mengunduh berkas `Student.ipynb` dan dataset `student_dataset.xlsx` dari repository ini.
2. Buka **[Google Colab](https://colab.research.google.com/)** di browser Anda.
3. Klik menu **File > Upload notebook**, lalu unggah berkas `Student.ipynb`.
4. Setelah notebook terbuka, klik ikon **Folder** (Files) di panel sebelah kiri.
5. Klik ikon **Upload to session storage** (ikon kertas dengan panah ke atas), lalu unggah berkas dataset. *(Alternatif: unggah dataset ke Google Drive pribadi dan mount drive ke Colab).*
6. Pastikan nama file dataset yang terunggah ejaannya persis dengan yang ada di dalam kode notebook.
7. Jalankan sel satu per satu dengan menekan `Shift + Enter`, atau langsung jalankan semua sel melalui menu **Runtime > Run all**.
8. Hasil analisis, grafik, dan ringkasan performa model akan muncul secara otomatis di bawah setiap sel setelah dieksekusi.

> **Catatan:** Pastikan koneksi internet stabil. Jika muncul error terkait library, jalankan sel berisi perintah `!pip install` untuk menginstall semua dependensi yang dibutuhkan.

## Alur Kerja (Metodologi)
1. **Eksplorasi Data (EDA)**: Analisis statistik deskriptif, distribusi data (Visualisasi Histogram/Boxplot), dan pengecekan korelasi antar variabel (Heatmap).
2. **Prapemrosesan Data**: 
   - Pengecekan *missing value*.
   - Penanganan anomali/*outlier* menggunakan metode IQR *clipping*.
   - Transformasi fitur menggunakan *Label Encoding* pada variabel kategorikal (`placement_status`).
   - Pembagian dataset menjadi data latih (80%) dan data uji (20%).
3. **Pemodelan Regresi**:
   - Baseline Model (Mean)
   - Linear Regression
   - Decision Tree Regression
   - Random Forest Regression
4. **Hyperparameter Tuning**: Menggunakan `GridSearchCV` untuk mencari parameter terbaik pada model *Random Forest*.

## Hasil Evaluasi
Model terbaik yang direkomendasikan adalah **Random Forest Regression (Tuned)** dengan capaian performa terbaik pada pengujian (*Testing Set*):
- **Mean Squared Error (MSE)**: 66.8521
- **Root Mean Squared Error (RMSE)**: 8.1763
- **R-squared (R²)**: 0.9021

Analisis *Feature Importances* menyimpulkan bahwa prediktor paling signifikan dalam penentuan nilai adalah **`previous_score`**, disusul oleh tingkat kehadiran (**`attendance`**), dan durasi **`study_hours`**.