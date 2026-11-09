# Kerasss — Proyek Kelompok EDA: Harga dan Spesifikasi Laptop

**Mata kuliah:** Exploratory Data Analysis (KMTI21133) · STT Terpadu Nurul Fikri · TA 2026/2027
**Tim:** Kerasss — Eka Nurviantoro, Muhamad Rafly Zidan, Muhamad Yusuf Fathurrohman, Mulki Fahrudien

## Tujuan
Mengeksplorasi data harga dan spesifikasi laptop untuk memahami faktor-faktor yang berkaitan dengan harga,
perbedaan antarmerek, serta pola penilaian pembeli, lalu memberi rekomendasi yang dapat ditindaklanjuti bagi
calon pembeli dan penjual.

## Pertanyaan analisis
1. Spesifikasi apa (RAM, SSD, HDD, kartu grafis, prosesor) yang berkaitan dengan harga laptop, dan apa implikasinya bagi calon pembeli dalam memilih spesifikasi sesuai anggaran?
2. Bagaimana sebaran harga dan spesifikasi antarmerek (ASUS, Dell, Lenovo, HP, Acer, MSI, Apple, Avita), dan merek mana yang harganya lebih tinggi pada spesifikasi yang sebanding?
3. Bagaimana pola rating dan jumlah ulasan menurut merek dan rentang harga, dan apa implikasinya bagi penjual dalam menentukan harga?
4. Apakah kelas laptop (Casual, ThinNlight, Gaming) dan fitur tambahan (touchscreen, MS Office, garansi) berkaitan dengan perbedaan harga?

## Dataset
| | |
|---|---|
| Nama berkas | `laptopPrice.csv` (ada di `data/raw/`) |
| Ukuran | 823 baris x 19 kolom (mentah) → 802 baris setelah duplikat dihapus |
| Variabel | 3 numerik (harga, jumlah rating, jumlah ulasan) dan 16 kategorikal/teks |
| Sumber | Kaggle, dataset "Laptop Price" (`laptopPrice.csv`); lisensi mengikuti halaman dataset di Kaggle |
| Data pribadi | Tidak ada; data berupa spesifikasi produk, tidak memuat individu |

Kamus data lengkap: [`data_dictionary.md`](data_dictionary.md). Catatan pembersihan: [`cleaning_log.md`](cleaning_log.md).

## Cara menjalankan
```bash
# 1. Salin repositori
git clone https://github.com/Viaaannn/Kerasss-TIM-EDA.git
cd Kerasss-TIM-EDA

# 2. Buat environment dan pasang pustaka
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt

# 3. Jalankan notebook BERURUTAN dari folder notebooks/
jupyter notebook
```
Data asli sudah tersedia di `data/raw/laptopPrice.csv`. Semua path di notebook relatif terhadap folder `notebooks/`.

| Urutan | Notebook / berkas | Isi | Milestone |
|---|---|---|---|
| 1 | `notebooks/01_quality.ipynb` | diagnosis kualitas data | M2 |
| 2 | `notebooks/02_cleaning.ipynb` | pembersihan dan validasi → `data/processed/laptop_bersih.csv` | M2 |
| 3 | `notebooks/03_univariate.ipynb` | distribusi, sebaran, outlier | M3 |
| 4 | `notebooks/04_multivariate.ipynb` | hubungan antarvariabel | M3 |
| 5 | `knime/*.knwf` | workflow KNIME (buka di KNIME Analytics Platform) | M4 |
| 6 | `notebooks/05_advanced.ipynb` | regresi, clustering, PCA | M5 |

## Struktur repositori
```
├── README.md
├── requirements.txt
├── data_dictionary.md
├── cleaning_log.md
├── AI_usage_log.md
├── data/raw/            data asli, TIDAK PERNAH diubah
├── data/processed/      hasil pembersihan
├── notebooks/           01_quality ... 05_advanced
├── knime/               workflow .knwf
├── reports/             laporan, slide, figures/
└── latihan_individu/    arsip praktikum P02-P05 per anggota (dataset koperasi, bukan data proyek)
```

## Pembagian peran
Peran bergilir setiap milestone.

| Milestone | Koordinator | Data engineer | Analis | Penulis / visual |
|-----------|-------------|---------------|--------|------------------|
| M1 | Eka | Rafly | Yusuf | Mulki |
| M2 | Rafly | Yusuf | Mulki | Eka |
| M3 | Yusuf | Mulki | Eka | Rafly |
| M4 | Mulki | Eka | Rafly | Yusuf |
| M5 | Eka | Rafly | Yusuf | Mulki |

## Status milestone
| Milestone | Tag Git | Status |
|---|---|---|
| M1 | `m1` | Belum diberi tag |
| M2 | `m2` | Notebook 01 dan 02 sudah ada; belum diberi tag |
| M3 | `m3` | Belum dikerjakan |
| M4 | `m4` | Belum dikerjakan |
| M5 | `m5` | Belum dikerjakan |
