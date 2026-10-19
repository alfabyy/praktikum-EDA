# Cleaning Log

> **Template M2 — Exploratory Data Analysis (KMTI21133).**
> Hapus seluruh teks dalam blok kutip seperti ini sebelum mengumpulkan.
> Berkas ini diletakkan di **akar repositori** dengan nama persis `cleaning_log.md`.

**Tim:**
**Dataset:**
**Baris mentah:** → **baris bersih:**
**Terakhir diperbarui:**

---

## Cara mengisi

> Setiap baris menjawab tiga hal: **apa yang diubah, berapa banyak, dan mengapa**.
> Kolom *Alasan* adalah yang dinilai (Rubrik M2, bobot 30). Tulis MENGAPA, bukan mengulang nama langkah.
>
> | Ditulis begini | Dinilai |
> |---|---|
> | "Kolom umur diisi dengan median" | Deskripsi tindakan. Nilai rendah. |
> | "Kolom umur diisi dengan median karena kekosongannya hanya 3% dan tersebar merata di semua kelompok; membuang baris ditolak karena menghapus 48 transaksi yang kolom lainnya lengkap" | Justifikasi. Nilai penuh. |
>
> Catat **saat** Anda mengerjakan langkahnya, bukan di akhir. Log yang ditulis belakangan selalu kehilangan alasan yang sebenarnya.

---

## Urutan langkah

> Urutan ini bukan selera. Langkah yang dikerjakan terlalu awal membuat langkah berikutnya salah.
> Hapus baris yang tidak Anda perlukan, tetapi jangan mengubah urutannya tanpa alasan.

| # | Langkah | Kolom | Baris terdampak | Keputusan | Alasan |
|---|---|---|---|---|---|
| 1 | Perbaiki tipe data | | | | |
| 2 | Buang spasi pada kolom teks | | | | |
| 3 | Placeholder menjadi kosong | | | | |
| 4 | Seragamkan kategori | | | | |
| 5 | Tangani duplikat | | | | |
| 6 | Tangani nilai mustahil | | | | |
| 7 | Tangani nilai kosong | | | | |
| 8 | Buat kolom turunan | | | | |
| 9 | | | | | |
| 10 | | | | | |

---

## Peta keputusan manual

> Penyeragaman yang **tidak bisa diputuskan mesin**: sinonim, salah ketik, penggabungan kategori.
> Kolom terakhir adalah yang paling penting — dari mana Anda tahu penggabungan itu benar?

| Nilai asal | Diubah menjadi | Dasar keputusan |
|---|---|---|
| | | |
| | | |
| | | |

---

## Yang sengaja TIDAK diubah

> Sama pentingnya dengan yang diubah. Masalah yang Anda temukan tetapi putuskan untuk dibiarkan,
> beserta alasannya dan akibatnya bagi analisis.

| Masalah | Mengapa dibiarkan | Akibat bagi analisis |
|---|---|---|
| | | |
| | | |

---

## Pertanyaan yang belum terjawab

> Hal yang perlu dikonfirmasi ke pemilik data atau dosen. Tuliskan meskipun belum ada jawabannya;
> daftar ini menjadi bagian "Keterbatasan" pada laporan M2.

- [ ]
- [ ]
- [ ]

---

## Dampak keseluruhan

| Ukuran | Sebelum | Sesudah | Catatan |
|---|---|---|---|
| Jumlah baris | | | |
| Jumlah kolom | | | |
| Total sel kosong | | | |
| Baris duplikat | | | |
| Kategori pada kolom kunci | | | |

> **Nilai kosong Anda kemungkinan bertambah**, karena placeholder yang tadinya menyamar sebagai angka
> kini jujur mengaku kosong. Laporkan apa adanya dan jelaskan sebabnya di kolom Catatan.

---

## Reproduktibilitas

- [ ] Notebook berjalan dari awal sampai akhir setelah *Restart and run all*
- [ ] Pembersihan dibungkus dalam satu fungsi, bukan tersebar di banyak sel
- [ ] `data/raw/` tidak berubah dan tidak ikut diunggah
- [ ] Hasil tersimpan di `data/processed/`
- [ ] `python cek_m2.py` berjalan tanpa status GAGAL
