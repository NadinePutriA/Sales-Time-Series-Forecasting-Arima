# Sales-Time-Series-Forecasting-Arima
Analisis pola revenue penjualan retail dan forecasting menggunakan metode ARIMA pada data time series mingguan, dilengkapi preprocessing, EDA, uji stasioneritas, serta evaluasi model menggunakan MAE, RMSE, dan MAPE.


# Analisis Pola dan Prediksi Penjualan Menggunakan ARIMA

## Deskripsi Proyek

Repository ini berisi implementasi analisis data dan forecasting revenue penjualan berbasis *time series* menggunakan metode **Autoregressive Integrated Moving Average (ARIMA)**. Proyek ini dikembangkan sebagai bagian dari tugas mata kuliah Penambangan Data pada Program Studi Sains Data, Universitas Negeri Surabaya.

Penelitian menggunakan **Global Retail Sales Dataset** yang diperoleh dari Kaggle. Data transaksi penjualan diolah menjadi data revenue mingguan untuk memahami pola perubahan pendapatan dan membangun model prediksi berdasarkan data historis.

Proses analisis meliputi preprocessing data, Exploratory Data Analysis (EDA), uji stasioneritas menggunakan Augmented Dickey-Fuller (ADF), identifikasi parameter menggunakan grafik ACF dan PACF, pemodelan ARIMA, forecasting, serta evaluasi model.

## Tujuan Proyek

- Menganalisis pola dan karakteristik perubahan revenue penjualan dari waktu ke waktu.
- Menerapkan metode ARIMA untuk memprediksi revenue penjualan mingguan.
- Mengevaluasi performa model menggunakan metrik MAE, RMSE, dan MAPE.
- Menginterpretasikan hasil forecasting sebagai informasi pendukung perencanaan dan pengambilan keputusan bisnis.

## Dataset

Dataset yang digunakan adalah [Global Retail Sales Dataset](https://www.kaggle.com/datasets/hamza0027/global-retail-sales-dataset) dari Kaggle.

Dataset terdiri dari 5.000 transaksi penjualan retail dengan periode Januari 2023 hingga Juni 2025. Penelitian berfokus pada dua variabel utama:

- `order_date`: tanggal transaksi yang digunakan sebagai indeks waktu.
- `revenue`: pendapatan dari transaksi penjualan.

Data revenue diagregasi menjadi **130 periode mingguan** sebelum digunakan dalam proses analisis dan pemodelan.

## Metodologi

### 1. Data Preprocessing
- Menyeragamkan nama kolom.
- Mengonversi tanggal transaksi ke format datetime.
- Mengurutkan data berdasarkan waktu.
- Memeriksa missing value dan data duplikat.
- Mengagregasi revenue ke periode mingguan.
- Mendeteksi outlier menggunakan metode Interquartile Range (IQR).

### 2. Exploratory Data Analysis (EDA)

EDA dilakukan untuk memahami karakteristik revenue mingguan melalui statistik deskriptif dan visualisasi, meliputi:
- Grafik revenue mingguan.
- Histogram distribusi revenue.
- Boxplot untuk mendeteksi outlier.
- Grafik tren revenue menggunakan rolling mean.

### 3. Train-Test Split

Data time series dibagi berdasarkan urutan waktu dengan proporsi 80:20, menghasilkan 104 data training dan 26 data testing. Pembagian ini mempertahankan urutan kronologis data.

### 4. Uji Stasioneritas

Pengujian dilakukan menggunakan Augmented Dickey-Fuller (ADF Test). Hasil pengujian pada data training menghasilkan p-value sebesar 0,002309, sehingga data dinyatakan stasioner pada tingkat signifikansi 5%.

### 5. Identifikasi dan Pemodelan ARIMA

Parameter ARIMA diidentifikasi menggunakan grafik Autocorrelation Function (ACF) dan Partial Autocorrelation Function (PACF). Beberapa kandidat model kemudian dibandingkan berdasarkan nilai Akaike Information Criterion (AIC).

Model yang dipilih adalah **ARIMA(1,0,1)** dengan nilai AIC sebesar 2512,303.

### 6. Forecasting dan Evaluasi

Model digunakan untuk memprediksi revenue pada data testing dan memperkirakan revenue untuk 12 minggu mendatang. Evaluasi dilakukan menggunakan:
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Mean Absolute Percentage Error (MAPE)
- Ljung-Box Test untuk mengevaluasi autokorelasi residual

## Hasil dan Evaluasi

Model ARIMA(1,0,1) menghasilkan evaluasi sebagai berikut:

| Metrik | Hasil |
|---|---:|
| AIC | 2512,303 |
| MAE | 38.649,69 |
| RMSE | 50.108,36 |
| MAPE | 24,89% |
| Ljung-Box p-value | 0,730 |

Hasil forecasting menunjukkan bahwa revenue untuk 12 minggu mendatang diperkirakan berada pada kisaran **192.000–193.500 per minggu**, dengan kecenderungan menurun secara perlahan.

Model mampu menggambarkan kecenderungan umum revenue, tetapi belum sepenuhnya mengikuti fluktuasi ekstrem pada data aktual. Oleh karena itu, hasil prediksi perlu dipahami sesuai karakteristik data dan tingkat kesalahan model.


## Konteks Akademik

Program Studi Sains Data  
Fakultas Matematika dan Ilmu Pengetahuan Alam  
Universitas Negeri Surabaya

Proyek ini disusun untuk memenuhi tugas mata kuliah Penambangan Data.
