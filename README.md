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
| 2 | **Muhammad Fikrie El-Muqoffa** | **0110223222** | Penyusun Peta 3 (Placeholder) |
| 3 | **M. Zacky Alvansyah** | **0110233195** | Penyusun Peta 4 (Placeholder) |
| 4 | **Jamaluddin Almandili Hasibuan** | **0110223248** | Penyusun Peta 5 (Placeholder) |

---

## Matriks Pembagian 5 Tema Peta Tematik Kelompok

Proyek ini menghasilkan 5 tema peta tematik (*choropleth maps*) yang diklasifikasikan menggunakan metode kuantitatif bertingkat (*Graduated Symbology*) di QGIS:

| Tema Peta | Penanggung Jawab | Parameter / Indikator Utama | Satuan | Sumber & Atribut Kolom |
|:---|:---|:---|:---:|:---|
| **Peta 1** | **Muhammad Afif Naufal**<br>`(NIM: 0110223240)` | **Distribusi Produksi Kelapa Sawit** | Ton/Tahun | Kolom `prod_sawit` |
| **Peta 2** | **Muhammad Afif Naufal**<br>`(NIM: 0110223240)` | **Produktivitas Perkebunan Kelapa Sawit** | Ton/km² | Kolom `prodktv_sawit` (`prod_sawit` / `luas_wilayah`) |
| **Peta 3** | Muhammad Fikrie El-Muqoffa<br>`(NIM: 0110223222)` | *[Placeholder: Indikator Peta 3]* | *[Satuan]* | *[Kolom Atribut]* |
| **Peta 4** | M. Zacky Alvansyah<br>`(NIM: 0110233195)` | *[Placeholder: Indikator Peta 4]* | *[Satuan]* | *[Kolom Atribut]* |
| **Peta 5** | Jamaluddin Almandili Hasibuan<br>`(NIM: 0110223248)` | *[Placeholder: Indikator Peta 5]* | *[Satuan]* | *[Kolom Atribut]* |

---

## Metodologi Pengolahan Spasial di QGIS

1. **Sumber Data Geometri Spasial:**
   - 14 berkas GeoJSON batas wilayah administratif tingkat II (Kabupaten/Kota) dengan kode wilayah BPS/Kemendagri `1601` s.d. `1674` yang bersumber dari repositori publik `yusufsyaifudin/wilayah-indonesia`.
   - Sistem Referensi Koordinat: **WGS 84 (EPSG:4326)**.

2. **Sumber Data Atribut Non-Spasial:**
   - Data tabular sekunder yang dirilis oleh **Badan Pusat Statistik (BPS) Provinsi Sumatera Selatan (Publikasi Provinsi Sumatera Selatan Dalam Angka 2024)**.
   - Variabel yang dihimpun meliputi indikator sektor perkebunan, demografi, fasilitas umum, dan pembangunan daerah.

3. **Tahapan Analisis Geospasial:**
   - **Merge Vector Layers:** Menggabungkan 14 berkas batas wilayah terpisah menjadi satu layer spasial terpadu (`sumsel_merged.geojson` dan `sumsel_merged.shp`).
   - **Attribute Table Integration:** Menginjeksikan seluruh atribut data statistik sektoral ke dalam tabel basis data spasial.
   - **Field Calculator Computation:** Mengkalkulasi indikator rasio turunan secara otomatis (misalnya Produktivitas Sawit = Produksi Sawit / Luas Wilayah).
   - **Graduated Symbology & Cartographic Layout:** Menerapkan skema pewarnaan bertingkat (*Color Ramp*) dengan metode klasifikasi kuantitatif (Natural Breaks/Quantile) serta menyusun tata letak kartografi standar (Judul, Orientasi Utara, Skala Grafis & Numerik, Legenda, Inset Peta, Grid Koordinat, dan Sumber Data).

---

## Struktur Direktori Berkas (`uts-sig/`)

```text
uts-sig/
│
├── README.md                          # Dokumentasi utama proyek UTS kelompok
├── project_uts_sumsel.qgz             # Berkas proyek kerja utama QGIS
│
├── data/                              # Dataset spasial hasil integrasi & penggabungan
│   ├── sumsel_merged.geojson          # FeatureCollection GeoJSON (14 wilayah + atribut)
│   ├── sumsel_merged.shp              # ESRI Shapefile polygon
│   ├── sumsel_merged.shx              # Indeks geometri Shapefile
│   ├── sumsel_merged.dbf              # Tabel atribut dBASE
│   ├── sumsel_merged.prj              # Proyeksi WGS 84 (EPSG:4326)
│   └── sumsel_merged.cpg              # Codepage UTF-8
│
└── hasil-peta-tematik/                # Hasil ekspor gambar layout kartografi (.png)
    ├── 01_peta_produksi_sawit.png     # Ekspor Peta 1 (Muhammad Afif Naufal)
    ├── 02_peta_produktivitas_sawit.png # Ekspor Peta 2 (Muhammad Afif Naufal)
    ├── 03_peta_tematik_3.png          # [Placeholder: Peta 3 Anggota 2]
    ├── 04_peta_tematik_4.png          # [Placeholder: Peta 4 Anggota 3]
    └── 05_peta_tematik_5.png          # [Placeholder: Peta 5 Anggota 4]
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
