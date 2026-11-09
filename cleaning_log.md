# Cleaning Log

Dataset: `laptopPrice.csv` · Baris mentah: 823 → baris bersih: 802
Data asli di `data/raw/` tidak diubah; hasil di `data/processed/laptop_bersih.csv`. Kode: `notebooks/02_cleaning.ipynb`.

| # | Langkah | Baris terdampak | Alasan |
|---|---|---|---|
| 1 | Hapus duplikat persis | 21 | Seluruh 19 kolom identik; satu salinan disimpan. Dilakukan pertama agar hitungan langkah lain tidak terdistorsi |
| 2 | Konversi `ram_gb`, `ssd`, `hdd`, `graphic_card_gb` dari teks `"8 GB"` ke angka | 802 | Teks bersatuan tidak dapat dihitung; satuan GB dipindah ke nama kolom |
| 3 | Konversi `warranty` ke `garansi_tahun` | 802 | `No warranty` = 0 tahun; pemetaan eksplisit agar nilai tak dikenal memicu galat, bukan lolos diam-diam |
| 4 | Konversi `rating` ke angka 1–5 | 802 | `"4 stars"` tidak dapat dihitung rata-ratanya |
| 5 | `Yes`/`No` menjadi boolean; nama kolom diseragamkan | 802 | Memudahkan agregasi dan konsisten dengan kolom lain |
| 6 | Seragamkan penulisan `brand` (acer, DELL, APPLE) | 223 | Hanya beda huruf besar/kecil; ASUS, HP, MSI dibiarkan karena singkatan |
| 7 | Rating pada baris tanpa penilai menjadi kosong | 243 | Seluruh baris dengan `Number of Ratings` = 0 berisi `3 stars` (nilai bawaan, bukan penilaian nyata); rata-rata rating naik dari 3,56 ke 3,82 setelah dikoreksi |
| 8 | `processor_gnrtn` = `Not Available` menjadi kosong + kolom `generasi_tersedia` | 224 | Kosong terstruktur (hampir seluruhnya Ryzen, Celeron, Pentium), bukan acak; ditandai, tidak diisi |
| 9 | Tandai OS 32-bit dengan RAM >= 8 GB (`flag_32bit_ram_besar`) | 63 | OS 32-bit tidak dapat memakai RAM sebesar itu, tetapi belum diketahui kolom mana yang keliru; ditandai, tidak ditimpa |
| 10 | Tandai outlier harga (`harga_outlier_iqr`) | 49 | Didominasi laptop berspesifikasi tinggi (RAM 16 GB pada 38 dari 49 baris, Core i7/i9, Apple M1), jadi wajar; dibuang akan menghapus segmen premium |

## Diperiksa dan sengaja tidak diubah
- `ssd`, `hdd`, `graphic_card_gb` bernilai `0 GB`: artinya komponen itu tidak ada, bukan data hilang, sehingga tidak dijadikan kosong.
- Tidak ada nilai kosong (NaN) pada data mentah; semua kekosongan di data bersih berasal dari langkah 7 dan 8.
- `Number of Reviews` tidak pernah melebihi `Number of Ratings`, dan semua harga > 0.

## Catatan keterbatasan
- Data tidak memuat nama model, sehingga dua baris berbeda yang kebetulan identik di semua kolom tidak dapat dibedakan dari duplikat sungguhan (langkah 1).
- Mata uang pada kolom harga tidak dinyatakan di berkas.
