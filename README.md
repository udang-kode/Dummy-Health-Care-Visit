# Dummy Health Care Visit Dataset

Kumpulan data tiruan (*dummy dataset*) kunjungan pasien fasilitas pelayanan kesehatan (Puskesmas / Klinik Pratama). Dataset ini disusun untuk keperluan simulasi analisis data kesehatan, pengujian sistem informasi rekam medis, pembuatan dashboard Business Intelligence, serta eksperimen machine learning/data science.

---

## 📌 Ringkasan Data

* **Nama Berkas:** `dummy health care visit.csv`
* **Jumlah Baris:** 17.760 catatan kunjungan
* **Jumlah Kolom:** 24 fitur
* **Rentang Waktu:** 2 Januari 2025 – 31 Desember 2025
* **Sifat Data:** Sintetis / Tiruan (aman dari isu privasi dan regulasi kerahasiaan data medis/HIPAA)

---

## 📋 Struktur & Kamus Data

| Nama Kolom | Tipe Data | Deskripsi | Contoh Nilai |
| :--- | :--- | :--- | :--- |
| `No. Registrasi` | Teks | Identitas unik nomor pendaftaran kunjungan | `REG-20250102-0001` |
| `No. Antrian` | Teks | Nomor urut antrean harian per poli | `U-001`, `K-001` |
| `Nama` | Teks | Nama lengkap pasien (nama dummy) | `Eka Rahayu` |
| `Jenis Kelamin` | Kategori | Jenis kelamin pasien (`Laki-laki` / `Perempuan`) | `Perempuan` |
| `Nama Kepala Keluarga` | Teks | Nama kepala keluarga pasien | `Budi Rahayu` |
| `Tanggal Lahir` | Tanggal | Tanggal lahir pasien (`YYYY-MM-DD`) | `1981-12-18` |
| `Umur` | Numerik | Usia pasien saat berobat (tahun) | `43` |
| `Kelurahan` | Teks | Wilayah domisili pasien | `Cilodong`, `Kedaung` |
| `Tanggal Kunjungan` | Tanggal | Tanggal saat pelayanan diterima (`YYYY-MM-DD`) | `2025-01-02` |
| `Jenis Bayar` | Kategori | Metode pembayaran / penjaminan | `BPJS`, `Umum`, `Asuransi Lain` |
| `Poli` | Kategori | Poliklinik tujuan pelayanan | `Umum`, `KIA`, `Lansia`, `Gizi`, `Gigi` |
| `ICDX` | Teks | Kode dan deskripsi diagnosis standar ICD-10 | `R50.9 - Demam`, `K29.7 - Gastritis` |
| `Jenis Kasus` | Kategori | Status kunjungan penyakit | `Baru`, `Lama` |
| `Klasifikasi Penyebab`| Kategori | Golongan jenis penyakit | `Menular`, `Tidak Menular`, `Lainnya` |
| `TB/BB` | Teks | Tinggi badan (cm) dan Berat badan (kg) | `154/52.8` |
| `Tensi` | Teks | Tekanan darah sistol/diastol (mmHg) | `101/83` |
| `Respirasi` | Numerik | Frekuensi pernapasan (kali per menit) | `22` |
| `Lingkar Perut` | Teks/Num | Ukuran lingkar perut (cm) | `67` |
| `Gula Darah` | Teks/Num | Pemeriksaan kadar glukosa sewaktu (mg/dL) | `147`, `-` (jika tidak diuji) |
| `Suhu` | Numerik | Suhu tubuh pasien (°C) | `38.1` |
| `Subjek` | Teks | Keluhan atau anamnesis dari pasien (S-SOAP) | `Demam 2 hari` |
| `Objek` | Teks | Temuan klinis pemeriksaan fisik (O-SOAP) | `Suhu meningkat` |
| `Intruksi` | Teks | Edukasi/rencana tindak lanjut tenaga medis | `Kompres, istirahat` |
| `Resep` | Teks | Daftar terapi farmasi/obat yang diresepkan | `Paracetamol 500mg` |

---

## 💡 Potensi Analisis & Proyek

1. **Analisis Pola Penyakit Terbanyak (Top Diseases):**
   * Distribusi diagnosis penyakit berdasarkan ICD-10 per kelompok umur dan jenis kelamin.
   * Analisis tren penyakit menular vs tidak menular bulanan.

2. **Kapasitas & Beban Kerja Layanan:**
   * Analisis volume kunjungan harian/mingguan di setiap poli untuk optimalisasi alokasi staf nakes.
   * Perbandingan proporsi penjamin pembayaran (BPJS vs Tunai/Umum).

3. **Pola Spasial / Sebaran Domisili:**
   * Agregasi jumlah kunjungan per kelurahan untuk memetakan cakupan layanan fasilitas kesehatan.

4. **Korelasi Tanda Vital:**
   * Hubungan indeks antropometri (TB/BB, Lingkar Perut) terhadap diagnosa hipertensi (`Tensi`) atau hiperglikemia (`Gula Darah`).

---

## 🛠️ Contoh Memuat Data (Python)

```python
import pandas as pd

# Membaca langsung dari repository GitHub
url = "[https://raw.githubusercontent.com/udang-kode/Dummy-Health-Care-Visit/main/dummy%20health%20care%20visit.csv](https://raw.githubusercontent.com/udang-kode/Dummy-Health-Care-Visit/main/dummy%20health%20care%20visit.csv)"
df = pd.read_csv(url)

# Cek 5 baris pertama
print(df.head())
