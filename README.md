# Proyek UTS SIG - Peta Tematik Komposisi Wilayah Provinsi Sumatera Selatan (14 Kabupaten/Kota)

Proyek Ujian Tengah Semester (UTS) mata kuliah **Sistem Informasi Geografis (SIG)** yang mengkaji perancangan, manipulasi geospasial, dan visualisasi tematik multi-kriteria berbasis **Quantum GIS (QGIS)** pada 14 wilayah administratif (Kabupaten/Kota) di **Provinsi Sumatera Selatan**.

---

## Identitas Akademik

- **Mata Kuliah:** Sistem Informasi Geografis (SIG)
- **Dosen Pengampu:** Dr. Sirojul Munir, S.Si., M.Kom.
- **Program Studi:** Teknik Informatika / Sistem Informasi
- **Institusi:** Sekolah Tinggi Teknologi Terpadu Nurul Fikri (STT Terpadu Nurul Fikri)
- **Tahun Akademik:** 2026

### Susunan Anggota Kelompok
| No | Nama Mahasiswa | NIM | Peran / Penanggung Jawab |
|:--:|:---|:---:|:---|
| 1 | **Muhammad Afif Naufal** | **0110223240** | Penyusun Peta Tematik Distribusi Produksi Kelapa Sawit & Peta Tematik Produktivitas Perkebunan Kelapa Sawit |
| 2 | **Muhammad Fikrie El-Muqoffa** | **0110223222** | Penyusun Peta 3 (isi sesuai peta yg dibuat) |
| 3 | **M. Zacky Alvansyah** | **0110233195** | Penyusun Peta 4 (isi sesuai peta yg dibuat) |
| 4 | **Jamaluddin Almandili Hasibuan** | **0110223248** | Penyusun Peta 5 (isi sesuai peta yg dibuat) |

---

## Matriks Pembagian 5 Tema Peta Tematik Kelompok

Proyek ini menghasilkan 5 tema peta tematik (*choropleth maps*) yang diklasifikasikan menggunakan metode kuantitatif bertingkat (*Graduated Symbology*) di QGIS:

| Tema Peta | Penanggung Jawab | Parameter / Indikator Utama | Satuan | Sumber & Atribut Kolom |
|:---|:---|:---|:---:|:---|
| **Peta 1** | **Muhammad Afif Naufal**<br>`(NIM: 0110223240)` | **Kepadatan Penduduk** | Jiwa/km² | Kolom `kepadatan` (`populasi` / `luas_wilayah`) |
| **Peta 2** | **Muhammad Afif Naufal**<br>`(NIM: 0110223240)` | **Distribusi Produksi & Produktivitas Perkebunan Kelapa Sawit** | Ton/Tahun & Ton/km² | Kolom `prod_sawit` & `prodktv_sawit` |
| **Peta 3** | Anggota 2 | **Distribusi Fasilitas Pelayanan Kesehatan (Faskes)** | Unit | Kolom `faskes_total` (RSU, Puskesmas, Klinik) |
| **Peta 4** | Anggota 3 | **Persebaran Sarana Pendidikan Menengah (SMA/SMK)** | Unit | Kolom `jml_sekolah` |
| **Peta 5** | Anggota 4 | **Indeks Pembangunan Manusia (IPM) & Kesejahteraan** | Indeks (0-100) | Kolom `nilai_ipm` |

---

## Metodologi Pengolahan Spasial di QGIS

1. **Sumber Data Geometri Spasial:**
   - 14 berkas GeoJSON batas wilayah administratif tingkat II (Kabupaten/Kota) dengan kode wilayah BPS/Kemendagri `1601` s.d. `1674` yang bersumber dari repositori publik `yusufsyaifudin/wilayah-indonesia`.
   - Sistem Referensi Koordinat: **WGS 84 (EPSG:4326)**.

2. **Sumber Data Atribut Non-Spasial:**
   - Data tabular sekunder yang dirilis oleh **Badan Pusat Statistik (BPS) Provinsi Sumatera Selatan (Publikasi Provinsi Sumatera Selatan Dalam Angka 2024)**.
   - Variabel yang dihimpun: Luas Daratan Wilayah (km²), Jumlah Penduduk (Jiwa), Produksi Sawit (Ton), Produksi Karet (Ton), Total Faskes (Unit), Jumlah Sekolah SMA/SMK (Unit), dan Angka IPM (Metode Baru).

3. **Tahapan Analisis Geospasial:**
   - **Merge Vector Layers:** Menggabungkan 14 berkas batas wilayah terpisah menjadi satu layer spasial terpadu (`sumsel_merged.geojson` dan `sumsel_merged.shp`).
   - **Attribute Table Integration:** Menginjeksikan seluruh atribut data statistik sektoral ke dalam tabel basis data spasial.
   - **Field Calculator Computation:** Mengkalkulasi indikator rasio turunan secara otomatis:
     $$\text{Kepadatan Penduduk} = \frac{\text{Populasi}}{\text{Luas Wilayah (km}^2\text{)}}$$
     $$\text{Produktivitas Sawit} = \frac{\text{Produksi Sawit (Ton)}}{\text{Luas Wilayah (km}^2\text{)}}$$
   - **Graduated Symbology & Cartographic Layout:** Menerapkan skema pewarnaan bertingkat (*Color Ramp*) dengan metode klasifikasi interval (Natural Breaks/Equal Interval) serta menyusun tata letak kartografi standar (Judul, Orientasi Utara, Skala Grafis & Numerik, Legenda, Inset Peta, Grid Koordinat, dan Sumber Data).

---

## Ringkasan Data Atribut Geospasial (14 Kabupaten/Kota)

| Kode | Nama Wilayah | Luas (km²) | Populasi (Jiwa) | Kepadatan (Jiwa/km²) | Prod. Sawit (Ton) | Prodktv. Sawit (Ton/km²) | Prod. Karet (Ton) | Faskes (Unit) | Sekolah (Unit) | Nilai IPM |
|:---:|:---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **1601** | Kab. Ogan Komering Ulu | 4.797,00 | 379.000 | 79,01 | 18.500,0 | 3,86 | 62.400,0 | 45 | 32 | 70,21 |
| **1602** | Kab. Ogan Komering Ilir | 18.359,04 | 779.000 | 42,43 | 485.000,0 | 26,42 | 145.200,0 | 62 | 54 | 68,15 |
| **1603** | Kab. Muara Enim | 7.383,90 | 640.000 | 86,68 | 165.400,0 | 22,40 | 118.000,0 | 58 | 48 | 70,12 |
| **1604** | Kab. Lahat | 5.311,74 | 438.000 | 82,46 | 22.100,0 | 4,16 | 85.300,0 | 41 | 38 | 69,80 |
| **1605** | Kab. Musi Rawas | 6.350,10 | 412.000 | 64,88 | 210.000,0 | 33,07 | 92.100,0 | 39 | 35 | 68,90 |
| **1606** | Kab. Musi Banyuasin | 14.265,96 | 632.000 | 44,30 | 620.000,0 | 43,46 | 178.500,0 | 65 | 52 | 70,05 |
| **1607** | Kab. Banyuasin | 11.832,99 | 853.000 | 72,09 | 390.000,0 | 32,96 | 105.400,0 | 70 | 61 | 68,75 |
| **1608** | Kab. OKU Selatan | 5.493,94 | 420.000 | 76,45 | 8.200,0 | 1,49 | 34.600,0 | 32 | 28 | 67,10 |
| **1609** | Kab. OKU Timur | 3.370,00 | 682.000 | 202,37 | 450.000,0 | 133,53 | 48.200,0 | 50 | 45 | 70,85 |
| **1610** | Kab. Ogan Ilir | 2.666,07 | 436.000 | 163,54 | 38.400,0 | 14,40 | 54.100,0 | 35 | 30 | 68,40 |
| **1671** | Kota Palembang | 400,61 | 1.772.000 | 4.423,25 | 0,0 | 0,00 | 500,0 | 140 | 120 | 79,20 |
| **1672** | Kab. Empat Lawang | 2.256,44 | 336.000 | 148,91 | 3.100,0 | 1,37 | 41.000,0 | 25 | 22 | 66,80 |
| **1673** | Kota Pagar Alam | 633,66 | 150.000 | 236,72 | 0,0 | 0,00 | 8.100,0 | 20 | 18 | 69,50 |
| **1674** | Kota Lubuk Linggau | 401,50 | 241.000 | 600,25 | 1.200,0 | 2,99 | 12.300,0 | 30 | 25 | 72,90 |

---

## Struktur Direktori Berkas (`uts-sig/`)

```text
uts-sig/
│
├── README.md                          # Dokumentasi utama proyek UTS
│
├── data/                              # Dataset spasial hasil integrasi & penggabungan
│   ├── sumsel_merged.geojson          # FeatureCollection GeoJSON (14 wilayah + atribut lengkap)
│   ├── sumsel_merged.shp              # ESRI Shapefile polygon
│   ├── sumsel_merged.shx              # Indeks geometri Shapefile
│   ├── sumsel_merged.dbf              # Tabel atribut dBASE
│   ├── sumsel_merged.prj              # Proyeksi WGS 84 (EPSG:4326)
│   └── sumsel_merged.cpg              # Codepage UTF-8
│
└── maps/                              # Hasil visualisasi & file project QGIS
    ├── layouts/                       # Template cetak layout kartografi (.qpt)
    ├── Peta_1_Kepadatan_Penduduk.png  # Ekspor layout Peta 1 (resolusi tinggi 300 DPI)
    ├── Peta_2_Produksi_Sawit.png      # Ekspor layout Peta 2 (resolusi tinggi 300 DPI)
    ├── Peta_3_Fasilitas_Kesehatan.png # Ekspor layout Peta 3 (resolusi tinggi 300 DPI)
    ├── Peta_4_Sarana_Pendidikan.png   # Ekspor layout Peta 4 (resolusi tinggi 300 DPI)
    ├── Peta_5_Indeks_IPM.png          # Ekspor layout Peta 5 (resolusi tinggi 300 DPI)
    └── proyek_uts_sumsel.qgz          # Berkas project kerja QGIS
```

---

## Lampiran Video Presentasi

Sebagai bagian dari pemenuhan evaluasi akademik UTS, rekaman pemaparan metodologi, pengolahan data di QGIS, dan interpretasi pola keruangan spasial dapat diakses melalui tautan berikut:

- **Tautan Video Presentasi:** [Tonton Video Presentasi Proyek UTS (YouTube / Google Drive)](https://youtu.be/placeholder-uts-sig-sumsel)
- **Durasi Maksimal:** 5 Menit
- **Materi Presentasi:**
  1. Pengantar Proyek & Pembagian Tema Peta Kelompok.
  2. Alur Penggabungan Spasial (*Merge Vector Layers*) & Kalkulasi Atribut di QGIS.
  3. Pembacaan dan Analisis Komparatif Pola Keruangan 5 Peta Tematik Sumatera Selatan.
