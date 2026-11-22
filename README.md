# LAPORAN-SO-V1

Laporan Stock Opname (SO) harian resto - file utama: **TGRGEL.xlsx**

## FITUR BARU: Analisa Stock Anomali (v2)

Ditambahkan langsung di dalam TGRGEL.xlsx, terhitung otomatis dari pivot `CEK DEVIASI HARIAN` + `STOK AKHIR SEHARUSNYA` (tidak ada input manual).

### Sheet baru

| Sheet | Fungsi |
|---|---|
| `ANALISA ANOMALI` | Analisa per barang: statistik deviasi 31 hari, deteksi 11 jenis anomali, SKOR 0-100, PRIORITAS, dan REKOMENDASI tindakan. Threshold bisa diubah di sel kuning `B3:H3`. |
| `ANOMALI HARIAN` | Peta tanggal kejadian anomali per barang - kode `Z` (spike/outlier), `M` (hasil SO minus), `L` (loss besar), `P` (surplus besar). |
| `ANOMALI TOP 20` | Ranking otomatis 20 barang paling kritis bulan berjalan. |
| `PANDUAN ANOMALI` | Dokumentasi lengkap: cara pakai, definisi flag, parameter, catatan penting. |
| `ANOMALI DATA` | Sheet teknis perhitungan (jangan diedit). |

### Cara pakai singkat

1. Isi input seperti biasa, lalu **Data > Refresh All (2x)**.
2. Buka `ANALISA ANOMALI` > filter `PRIORITAS` = KRITIS/TINGGI, atau lihat `ANOMALI TOP 20`.
3. Telusuri tanggal kejadian di `ANOMALI HARIAN`, lalu investigasi sesuai REKOMENDASI.

### Jenis anomali yang dideteksi

`LN` loss tak terjelaskan, `LK` loss kronis, `Z` spike/outlier statistik (z-score), `M` hasil SO minus, `ZZ` zigzag/cut-off, `P` surplus, `PX` surplus ekstrem, `KV` salah konversi (deviasi identik harian), `NU` tidak terpakai, `DM` streak tak terpakai, `TM` tidak di-SO.

Detail aturan & bobot lihat sheet `PANDUAN ANOMALI`.

> Catatan teknis: fitur ini murni formula Excel (tanpa macro), tahan terhadap refresh pivot, dan aman dibuka di Excel 2016+ / Excel 365 / LibreOffice.
