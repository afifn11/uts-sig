# Proyek UTS SIG - Peta Tematik Komposisi Wilayah Provinsi Riau (12 Kabupaten/Kota)

Proyek Ujian Tengah Semester (UTS) mata kuliah **Sistem Informasi Geografis (SIG)** yang mengkaji perancangan, manipulasi geospasial, dan visualisasi tematik multi-kriteria berbasis **Quantum GIS (QGIS)** pada 12 wilayah administratif (Kabupaten/Kota) di **Provinsi Riau**.

---

## Identitas Akademik

- **Nama Mahasiswa:** Muhammad Afif Naufal
- **NIM:** 0110223240
- **Mata Kuliah:** Sistem Informasi Geografis (SIG)
- **Dosen Pengampu:** Dr. Sirojul Munir, S.Si., M.Kom.
- **Program Studi:** Teknik Informatika
- **Institusi:** Sekolah Tinggi Teknologi Terpadu Nurul Fikri (STT Terpadu Nurul Fikri)
- **Tahun Akademik:** 2026

---

## Matriks 5 Tema Peta Tematik

Proyek ini menghasilkan 5 tema peta tematik (*choropleth maps*) yang diklasifikasikan menggunakan metode kuantitatif bertingkat (*Graduated Symbology*) di QGIS:

| Tema Peta | Parameter / Indikator Utama | Satuan | Atribut Kolom QGIS |
|:---|:---|:---:|:---|
| **Peta 1** | **Distribusi Produksi Kelapa Sawit** | Ton/Tahun | `prod_sawit` |
| **Peta 2** | **Produktivitas Perkebunan Kelapa Sawit** | Ton/km² | `prodktv_sa` (`prod_sawit` / `luas_wilay`) |
| **Peta 3** | **Produksi Perkebunan Karet** | Ton/Tahun | `prod_karet` |
| **Peta 4** | **Produksi Perkebunan Kelapa Dalam** | Ton/Tahun | `prod_kelap` |
| **Peta 5** | **Timbulan Sampah Harian** | Ton/Hari | `timbulan_s` |

---

## Metodologi Pengolahan Spasial di QGIS

1. **Sumber Data Geometri Spasial:**
   - 12 berkas GeoJSON batas wilayah administratif tingkat II (Kabupaten/Kota) Provinsi Riau dengan kode wilayah BPS/Kemendagri `1401` s.d. `1472` yang bersumber dari repositori publik `yusufsyaifudin/wilayah-indonesia`.
   - Sistem Referensi Koordinat: **WGS 84 (EPSG:4326)**.

2. **Sumber Data Atribut Non-Spasial:**
   - Data tabular sekunder yang dirilis oleh **Badan Pusat Statistik (BPS) Provinsi Riau (Publikasi Provinsi Riau Dalam Angka 2024)** dan **Sistem Informasi Pengelolaan Sampah Nasional (SIPSN KLHK)**.
   - Variabel yang dihimpun meliputi indikator sektor perkebunan (sawit, karet, kelapa dalam) dan pengelolaan lingkungan hidup (timbulan sampah).

3. **Tahapan Analisis Geospasial:**
   - **Merge Vector Layers:** Menggabungkan 12 berkas batas wilayah terpisah menjadi satu layer spasial terpadu (`riau_merged.geojson` dan `riau_merged.shp`).
   - **Attribute Table Integration:** Menginjeksikan seluruh atribut data statistik sektoral ke dalam tabel basis data spasial.
   - **Field Calculator Computation:** Mengkalkulasi indikator rasio turunan secara otomatis (Produktivitas Sawit = Produksi Sawit / Luas Wilayah).
   - **Graduated Symbology & Cartographic Layout:** Menerapkan skema pewarnaan bertingkat (*Color Ramp*) dengan metode klasifikasi kuantitatif (Natural Breaks) serta menyusun tata letak kartografi standar (Judul, Orientasi Utara, Skala Grafis & Numerik, Legenda, Inset Peta, Grid Koordinat, dan Sumber Data).

---

## Struktur Direktori Berkas (`uts-sig/`)

```text
uts-sig/
│
├── README.md                          # Dokumentasi utama proyek UTS
├── project_uts_riau.qgz               # Berkas proyek kerja utama QGIS
│
├── data/                              # Dataset spasial hasil integrasi & penggabungan
│   ├── riau_merged.cpg                # Codepage UTF-8
│   ├── riau_merged.dbf                # Tabel atribut dBASE
│   ├── riau_merged.geojson            # FeatureCollection GeoJSON (12 wilayah + atribut)
│   ├── riau_merged.prj                # Proyeksi WGS 84 (EPSG:4326)
│   ├── riau_merged.shp                # ESRI Shapefile polygon
│   └── riau_merged.shx                # Indeks geometri Shapefile
│
└── hasil-peta-tematik/                # Hasil ekspor gambar layout kartografi (.png)
    ├── 01_peta_produksi_sawit.png     # Ekspor Peta 1 (Produksi Sawit)
    ├── 02_peta_produktivitas_sawit.png # Ekspor Peta 2 (Produktivitas Sawit)
    ├── 03_peta_produksi_karet.png     # Ekspor Peta 3 (Produksi Karet)
    ├── 04_peta_produksi_kelapa.png    # Ekspor Peta 4 (Produksi Kelapa Dalam)
    └── 05_peta_timbulan_sampah.png    # Ekspor Peta 5 (Timbulan Sampah Harian)
```

---

## Lampiran Video Presentasi

Sebagai bagian dari pemenuhan evaluasi akademik UTS, rekaman pemaparan metodologi, pengolahan data di QGIS, dan interpretasi pola keruangan spasial dapat diakses melalui tautan berikut:

- **Tautan Video Presentasi:** [Tonton Video Presentasi Proyek UTS](https://drive.google.com/file/d/1rq7ZVQ_TjAAEXYNrHqZeDgEY-GyHt3Zl/view?usp=drive_link)
- **Durasi Maksimal:** 5 Menit
- **Materi Presentasi:**
  1. Pengantar Proyek & Metodologi Pengolahan Data.
  2. Alur Penggabungan Spasial (*Merge Vector Layers*) & Kalkulasi Atribut di QGIS.
  3. Pembacaan dan Analisis Komparatif Pola Keruangan 5 Peta Tematik Provinsi Riau.