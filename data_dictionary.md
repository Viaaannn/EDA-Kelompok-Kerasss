# Kamus Data

**Dataset:** `laptopPrice.csv` — 823 baris x 19 kolom (mentah) · **Sumber:** Kaggle, dataset "Laptop Price"
Tidak ada kolom data pribadi. Mata uang pada kolom `Price` tidak dinyatakan di berkas; nilai berkisar 16.990–441.990.

## Kolom pada data mentah (`data/raw/laptopPrice.csv`)
| Kolom | Tipe | Satuan | Deskripsi | Sumber |
|---|---|---|---|---|
| `brand` | kategori | — | Merek laptop: ASUS, DELL, Lenovo, HP, acer, MSI, APPLE, Avita (huruf besar/kecil tidak seragam) | Kaggle |
| `processor_brand` | kategori | — | Pembuat prosesor: Intel, AMD, M1 (chip Apple) | Kaggle |
| `processor_name` | kategori | — | Seri prosesor, mis. Core i5, Ryzen 5, Celeron Dual, M1 (11 nilai) | Kaggle |
| `processor_gnrtn` | kategori | generasi ke-n | Generasi prosesor (4th–12th); `Not Available` untuk 225 baris | Kaggle |
| `ram_gb` | teks | GB | Kapasitas RAM, tertulis `"8 GB"` (4, 8, 16, 32) | Kaggle |
| `ram_type` | kategori | — | Jenis RAM: DDR3, DDR4, DDR5, LPDDR3, LPDDR4, LPDDR4X | Kaggle |
| `ssd` | teks | GB | Kapasitas SSD, `"0 GB"` berarti tidak ada SSD | Kaggle |
| `hdd` | teks | GB | Kapasitas HDD, `"0 GB"` berarti tidak ada HDD | Kaggle |
| `os` | kategori | — | Sistem operasi: Windows, Mac, DOS | Kaggle |
| `os_bit` | kategori | bit | Arsitektur OS: 32-bit atau 64-bit | Kaggle |
| `graphic_card_gb` | teks | GB | Memori kartu grafis, `"0 GB"` berarti tanpa kartu grafis terpisah | Kaggle |
| `weight` | kategori | — | Kelas/tipe laptop: Casual, ThinNlight, Gaming (**bukan** bobot dalam kg) | Kaggle |
| `warranty` | kategori | tahun | Garansi: No warranty, 1 year, 2 years, 3 years | Kaggle |
| `Touchscreen` | kategori | — | Layar sentuh: Yes / No | Kaggle |
| `msoffice` | kategori | — | MS Office terpasang: Yes / No | Kaggle |
| `Price` | integer | mata uang tidak dinyatakan | Harga laptop | Kaggle |
| `rating` | teks | bintang | Rating rata-rata, `"1 star"` sampai `"5 stars"` | Kaggle |
| `Number of Ratings` | integer | jumlah | Banyaknya penilai | Kaggle |
| `Number of Reviews` | integer | jumlah | Banyaknya ulasan tertulis | Kaggle |

## Kolom pada data bersih (`data/processed/laptop_bersih.csv`, 802 baris x 22 kolom)
Nama dan tipe berubah di `02_cleaning.ipynb` (lihat `cleaning_log.md`).

| Kolom | Tipe | Satuan | Asal / deskripsi |
|---|---|---|---|
| `ram_gb`, `ssd_gb`, `hdd_gb`, `gpu_gb` | integer | GB | dari `ram_gb`, `ssd`, `hdd`, `graphic_card_gb` |
| `garansi_tahun` | integer | tahun | dari `warranty`; `No warranty` = 0 |
| `rating_bintang` | float | bintang 1–5 | dari `rating`; **kosong** bila belum ada penilai |
| `touchscreen`, `msoffice` | boolean | — | dari `Touchscreen`, `msoffice` |
| `harga` | integer | sama dengan `Price` | dari `Price` |
| `jumlah_rating`, `jumlah_ulasan` | integer | jumlah | dari `Number of Ratings`, `Number of Reviews` |
| `generasi_tersedia` | boolean | — | penanda: `False` bila generasi prosesor semula `Not Available` |
| `flag_32bit_ram_besar` | boolean | — | penanda: OS 32-bit dengan RAM >= 8 GB (janggal) |
| `harga_outlier_iqr` | boolean | — | penanda: harga di atas batas IQR (Q3 + 1,5 x IQR) |
| `brand`, `processor_brand`, `processor_name`, `processor_gnrtn`, `ram_type`, `os`, `os_bit`, `weight` | kategori | — | tidak berubah, kecuali `brand` diseragamkan hurufnya dan `processor_gnrtn` yang `Not Available` menjadi kosong |
