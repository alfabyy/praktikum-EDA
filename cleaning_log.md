# Cleaning Log

**Tim:** KELOMPOK EDA SIANG
**Dataset:** saham-daily-2024.csv
**Baris mentah:** 220,952 → **baris bersih:** 220,952
**Terakhir diperbarui:** 19 Oktober 2026

---

## Urutan langkah

| # | Langkah | Kolom | Baris terdampak | Keputusan | Alasan |
|---|---|---|---|---|---|
| 1 | Hapus kolom indeks ekspor | Unnamed: 0 | 220,952 | Dihapus dari salinan kerja | Menghindari variabel indeks bawaan ekspor yang tidak relevan dan berpotensi disalahartikan dalam analisis. |
| 2 | Perbaiki tipe data | Tanggal Perdagangan Terakhir | 220,952 | Dikonversi ke tipe datetime | Memudahkan pengurutan, pengelompokan waktu, dan validasi rentang deret waktu (time series). |
| 3 | Tangani nilai mustahil | First Trade | 8 | Dipertahankan sementara | Koreksi tanpa definisi kolom berisiko mengubah kode khusus; ditandai untuk verifikasi manual terhadap sumber asli. |
| 4 | Pertahankan placeholder nol | Open Price, Volume, Frekuensi | 204,197 (Open Price), 24,895 (Vol/Freq) | Dipertahankan tanpa imputasi | Nol bermakna sebagai indikasi tidak adanya transaksi, bukan data hilang; mengubahnya menjadi NaN akan menghilangkan informasi aktivitas perdagangan. |

---

## Peta keputusan manual

> Penyeragaman yang **tidak bisa diputuskan mesin**: sinonim, salah ketik, penggabungan kategori.

| Nilai asal | Diubah menjadi | Dasar keputusan |
|---|---|---|
| Format tanggal string lokal ("29 Jan 2024") | Format standar datetime (`2024-01-29`) | Berdasarkan pemetaan bulan bahasa Indonesia ke parser standar agar fungsi pengurutan waktu berjalan akurat. |
| Kolom indeks bawaan (`Unnamed: 0`) | Dihapus | Berdasarkan struktur file CSV yang menyertakan nomor indeks mentah dari sistem asal. |

---

## Yang sengaja TIDAK diubah

| Masalah | Mengapa dibiarkan | Akibat bagi analisis |
|---|---|---|
| Nilai 0 yang dominan pada *Open Price* dan *First Trade* (92.4% baris) | Belum ada dokumentasi resmi atau kamus data (*data dictionary*) yang mengonfirmasi apakah angka 0 adalah placeholder libur atau tidak ada transaksi. | Analisis yang melibatkan harga pembukaan harus memperhitungkan keberadaan nilai 0 agar tidak mendistorsi rata-rata harga pasar secara keseluruhan. |
| Selisih jumlah unik antara *Kode Saham* (948) dan *Nama Perusahaan* (959) | Penggabungan otomatis berisiko menyatukan emiten atau jenis efek yang berbeda tanpa kepastian metadata. | Analisis tingkat perusahaan perlu dibatasi atau menunggu verifikasi identitas lanjutan pada tahap M3. |

---

## Pertanyaan yang belum terjawab

- [ ] Apakah nilai 0 pada *Open Price* dan *First Trade* secara mutlak merepresentasikan ketiadaan perdagangan pada hari tersebut?
- [ ] Apakah perbedaan jumlah antara *Kode Saham* dan *Nama Perusahaan* disebabkan oleh emiten yang memiliki multi-efek atau ketidakkonsistenan penamaan?
- [ ] Bagaimana penjelasan spesifik terkait 8 baris data pada *First Trade* yang bernilai negatif?

---

## Dampak keseluruhan

| Ukuran | Sebelum | Sesudah | Catatan |
|---|---|---|---|
| Jumlah baris | 220,952 | 220,952 | Tidak ada baris yang dihapus untuk menjaga keutuhan data volume perdagangan. |
| Jumlah kolom | 29 | 29 | Kolom `Unnamed: 0` dibuang pada salinan kerja, namun bertambah kolom turunan tanggal `Tanggal_dt`. |
| Total sel kosong | 0 | 0 | Tidak ada *missing value* (NaN) eksplisit; nilai kosong direpresentasikan secara logis melalui penanganan nol/placeholder. |
| Baris duplikat | 0 | 0 | Tidak ditemukan duplikat identik pada dataset. |
| Kategori pada kolom kunci | 948 | 948 | Jumlah kode saham unik tetap dipertahankan untuk investigasi lebih lanjut. |

---

## Reproduktibilitas

- [ ] Notebook berjalan dari awal sampai akhir setelah *Restart and run all*
- [ ] Pembersihan dibungkus dalam satu fungsi, bukan tersebar di banyak sel
- [ ] `data/raw/` tidak berubah dan tidak ikut diunggah
- [ ] Hasil tersimpan di `data/processed/`
- [ ] `python cek_m2.py` berjalan tanpa status GAGAL
