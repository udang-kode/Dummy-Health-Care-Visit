# Dummy Health Care Visit Dataset

Kumpulan data sintetis (*dummy dataset*) kunjungan pasien pada fasilitas pelayanan kesehatan tingkat pertama (Puskesmas / Klinik). Berkas ini disusun khusus untuk kebutuhan eksplorasi data (*Exploratory Data Analysis*), pembuatan visualisasi dashboard Business Intelligence (BI), pengujian pipeline ETL, serta studi kasus machine learning di bidang analitik kesehatan.

---

## 📌 Ringkasan Data

* **Nama Berkas:** `dummy health care visit.csv`
* **Jumlah Catatan:** 17.760 baris kunjungan
* **Jumlah Fitur:** 24 kolom
* **Rentang Waktu Observasi:** 2 Januari 2025 – 31 Desember 2025
* **Sifat Data:** Data Fiktif / Tiruan (Bebas dari risiko kerahasiaan identitas pasien / HIPAA Compliant)

---

## 📋 Kamus Data (Data Dictionary)

Berikut adalah rincian kolom beserta tipe data dan penjelasannya:

| Nama Kolom | Tipe Data | Deskripsi | Contoh Nilai |
| :--- | :--- | :--- | :--- |
| `No. Registrasi` | String | Nomor unik registrasi pendaftaran kunjungan | `REG-20250102-0001` |
| `No. Antrian` | String | Nomor urut antrean harian sesuai poliklinik tujuan | `U-001`, `K-001` |
| `Nama` | String | Nama pasien (fiktif) | `Eka Rahayu` |
| `Jenis Kelamin` | Kategori | Jenis kelamin pasien (`Laki-laki` / `Perempuan`) | `Perempuan` |
| `Nama Kepala Keluarga` | String | Nama kepala keluarga pasien | `Budi Rahayu` |
| `Tanggal Lahir` | Date | Tanggal lahir pasien format `YYYY-MM-DD` | `1981-12-18` |
| `Umur` | Numerik | Usia pasien saat berobat (tahun) | `43` |
| `Kelurahan` | String | Kelurahan domisili pasien | `Cilodong`, `Kedaung` |
| `Tanggal Kunjungan` | Date | Tanggal pelayanan/pemeriksaan (`YYYY-MM-DD`) | `2025-01-02` |
| `Jenis Bayar` | Kategori | Skema pembiayaan (`BPJS`, `Umum`, `Asuransi Lain`) | `BPJS` |
| `Poli` | Kategori | Unit layanan poliklinik tujuan | `Umum`, `KIA`, `Lansia`, `Gigi`, `Gizi` |
| `ICDX` | String | Kode standar diagnosis penyakit ICD-10 beserta nama penyakit | `R50.9 - Demam`, `K29.7 - Gastritis` |
| `Jenis Kasus` | Kategori | Riwayat kunjungan diagnosis (`Baru` / `Lama`) | `Baru` |
| `Klasifikasi Penyebab`| Kategori | Golongan jenis penyakit (`Menular`, `Tidak Menular`, `Lainnya`) | `Menular` |
| `TB/BB` | String | Tinggi Badan (cm) dan Berat Badan (kg) | `154/52.8` |
| `Tensi` | String | Tekanan darah sistolik/diastolik (mmHg) | `101/83` |
| `Respirasi` | Numerik | Frekuensi napas (kali per menit) | `22` |
| `Lingkar Perut` | String/Num | Ukuran lingkar perut (cm) | `67` |
| `Gula Darah` | String/Num | Hasil tes gula darah sewaktu (mg/dL) atau `-` jika tidak diperiksa | `147` |
| `Suhu` | Numerik | Suhu badan pasien (°C) | `38.1` |
| `Subjek` | String | Keluhan utama atau anamnesis awal pasien (S - SOAP) | `Demam 2 hari` |
| `Objek` | String | Hasil temuan pemeriksaan fisik dokter (O - SOAP) | `Suhu meningkat` |
| `Intruksi` | String | Rencana edukasi atau instruksi perawatan medis | `Kompres, istirahat` |
| `Resep` | String | Terapi obat yang diresepkan | `Paracetamol 500mg` |

---

## 🎯 Ide & Topik Analisis

1. **Analisis Tren Pola Penyakit (Epidemiologi):**
   * Top 10 diagnosis ICD-10 yang paling sering dialami per kuartal.
   * Perbandingan rasio penyakit Menular vs Tidak Menular berdasarkan sebaran usia dan jenis kelamin.

2. **Kapasitas Layanan & Beban Kerja (Operations BI):**
   * Distribusi kunjungan harian/mingguan ke masing-masing poli untuk mengidentifikasi *peak hours/days*.
   * Proporsi kunjungan penjamin BPJS vs Pasien Umum.

3. **Geografi & Demografi Pasien:**
   * Wilayah kelurahan dengan frekuensi kunjungan tertinggi untuk pemetaan jangkauan faskes.

4. **Korelasi Tanda Vital:**
   * Pemodelan korelasi antara rasio antropometri (BMI/lingkar perut) dengan risiko hipertensi atau kadar gula darah tinggi.

---

## 💻 Cara Menggunakan Data

### Python (Pandas)
```python
import pandas as pd

# Load dataset via direct Raw URL GitHub
url = "https://raw.githubusercontent.com/udang-kode/Dummy-Health-Care-Visit/main/dummy%20health%20care%20visit.csv"
df = pd.read_csv(url)

print(f"Dimensi data: {df.shape}")
print(df.head())
```

### R
```r
library(readr)

url <- "https://raw.githubusercontent.com/udang-kode/Dummy-Health-Care-Visit/main/dummy%20health%20care%20visit.csv"
data <- read_csv(url)
head(data)
```

---

## ⚖️ Lisensi & Ketentuan
Dataset ini bersifat terbuka untuk tujuan edukasi, portofolio analisis data, maupun prototipe aplikasi. Semua identitas nama dan nomor identifikasi di dalamnya murni hasil simulasi fiktif.