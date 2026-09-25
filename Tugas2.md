# Hallo 

# Jawaban Tugas: Sistem Transaksi & Validasi Toko Buku Modern

## A. Analisis Komponen

**Variabel yang digunakan:**

| Nama Variabel | Tipe Data | Keterangan |
|---|---|---|
| `is_member` | Boolean | Status keanggotaan pelanggan |
| `jumlah_buku` | Integer | Jumlah buku yang dibeli |
| `total_awal` | Real | Total belanja sebelum diskon |
| `persen_diskon` | Real | Persentase diskon yang berlaku (variabel bantu) |
| `nominal_diskon` | Real | Nilai rupiah diskon |
| `total_bayar` | Real | Total akhir yang harus dibayar |

**Struktur kontrol yang digunakan:**
1. **Sequence** — urutan proses input → validasi → hitung diskon → hitung total → output.
2. **Iteration (Repeat-Until)** — pengulangan input selama `total_awal < 0` atau `jumlah_buku < 1`.
3. **Selection (IF bersarang/nested IF)** — percabangan status member, lalu percabangan syarat diskon tambahan/diskon non-member.

---

## B. Pseudocode

```
PROGRAM HitungTransaksiTokoBuku

KAMUS:
  is_member      : Boolean
  jumlah_buku    : Integer
  total_awal     : Real
  persen_diskon  : Real
  nominal_diskon : Real
  total_bayar    : Real

DESKRIPSI:
  1.  REPEAT
  2.      INPUT(total_awal)
  3.      INPUT(jumlah_buku)
  4.      IF (total_awal < 0) OR (jumlah_buku < 1) THEN
  5.          OUTPUT("Input tidak valid, silakan masukkan ulang")
  6.      ENDIF
  7.  UNTIL (total_awal >= 0) AND (jumlah_buku >= 1)

  8.  INPUT(is_member)

  9.  IF is_member = True THEN
  10.     IF (total_awal >= 200000) AND (jumlah_buku >= 3) THEN
  11.         persen_diskon <- 0.15
  12.     ELSE
  13.         persen_diskon <- 0.10
  14.     ENDIF
  15. ELSE
  16.     IF total_awal >= 300000 THEN
  17.         persen_diskon <- 0.05
  18.     ELSE
  19.         persen_diskon <- 0.0
  20.     ENDIF
  21. ENDIF

  22. nominal_diskon <- total_awal * persen_diskon
  23. total_bayar    <- total_awal - nominal_diskon

  24. OUTPUT(nominal_diskon)
  25. OUTPUT(total_bayar)

END PROGRAM
```

---

## C. Trace Table (Tabel Penelusuran)

### Kasus A — `is_member = True`, `total_awal = 250000`, `jumlah_buku = 4`

| Baris | Instruksi | total_awal | jumlah_buku | is_member | persen_diskon | nominal_diskon | total_bayar | Output |
|---|---|---|---|---|---|---|---|---|
| 2 | Input total_awal | 250000 | - | - | - | - | - | |
| 3 | Input jumlah_buku | 250000 | 4 | - | - | - | - | |
| 4 | Cek `total_awal<0 OR jumlah_buku<1` → **False** | 250000 | 4 | - | - | - | - | *(langsung keluar loop, tidak masuk baris 5)* |
| 8 | Input is_member | 250000 | 4 | True | - | - | - | |
| 9 | Cek `is_member = True` → **True** | 250000 | 4 | True | - | - | - | |
| 10 | Cek `total_awal>=200000 AND jumlah_buku>=3` → **True** (250000≥200000 & 4≥3) | 250000 | 4 | True | - | - | - | |
| 11 | `persen_diskon <- 0.15` | 250000 | 4 | True | 0.15 | - | - | |
| 22 | `nominal_diskon <- 250000*0.15` | 250000 | 4 | True | 0.15 | 37500 | - | |
| 23 | `total_bayar <- 250000-37500` | 250000 | 4 | True | 0.15 | 37500 | 212500 | |
| 24-25 | Output | | | | | | | **Diskon = 37500, Total Bayar = 212500** |

---

### Kasus B — `is_member = False`, `total_awal = 350000`, `jumlah_buku = 2`

| Baris | Instruksi | total_awal | jumlah_buku | is_member | persen_diskon | nominal_diskon | total_bayar | Output |
|---|---|---|---|---|---|---|---|---|
| 2 | Input total_awal | 350000 | - | - | - | - | - | |
| 3 | Input jumlah_buku | 350000 | 2 | - | - | - | - | |
| 4 | Cek `total_awal<0 OR jumlah_buku<1` → **False** | 350000 | 2 | - | - | - | - | *(keluar loop)* |
| 8 | Input is_member | 350000 | 2 | False | - | - | - | |
| 9 | Cek `is_member = True` → **False** | 350000 | 2 | False | - | - | - | *(masuk ELSE)* |
| 16 | Cek `total_awal>=300000` → **True** (350000≥300000) | 350000 | 2 | False | - | - | - | |
| 17 | `persen_diskon <- 0.05` | 350000 | 2 | False | 0.05 | - | - | |
| 22 | `nominal_diskon <- 350000*0.05` | 350000 | 2 | False | 0.05 | 17500 | - | |
| 23 | `total_bayar <- 350000-17500` | 350000 | 2 | False | 0.05 | 17500 | 332500 | |
| 24-25 | Output | | | | | | | **Diskon = 17500, Total Bayar = 332500** |

---

### Kasus C — Input awal `total_awal = -50000` (salah), dikoreksi menjadi `100000`, `is_member = False`, `jumlah_buku = 1`

| Baris | Instruksi | total_awal | jumlah_buku | is_member | persen_diskon | nominal_diskon | total_bayar | Output |
|---|---|---|---|---|---|---|---|---|
| **Iterasi ke-1 (input tidak valid)** |
| 2 | Input total_awal | -50000 | - | - | - | - | - | |
| 3 | Input jumlah_buku | -50000 | 1 | - | - | - | - | |
| 4 | Cek `total_awal<0 OR jumlah_buku<1` → **True** (-50000<0) | -50000 | 1 | - | - | - | - | |
| 5 | OUTPUT pesan error | -50000 | 1 | - | - | - | - | **"Input tidak valid, silakan masukkan ulang"** |
| 7 | Cek UNTIL: `(total_awal>=0) AND (jumlah_buku>=1)` → **False** → ulangi REPEAT | -50000 | 1 | - | - | - | - | |
| **Iterasi ke-2 (input dikoreksi)** |
| 2 | Input total_awal (koreksi) | 100000 | 1 | - | - | - | - | |
| 3 | Input jumlah_buku | 100000 | 1 | - | - | - | - | |
| 4 | Cek `total_awal<0 OR jumlah_buku<1` → **False** | 100000 | 1 | - | - | - | - | |
| 7 | Cek UNTIL: `(100000>=0) AND (1>=1)` → **True** → keluar loop | 100000 | 1 | - | - | - | - | |
| 8 | Input is_member | 100000 | 1 | False | - | - | - | |
| 9 | Cek `is_member = True` → **False** | 100000 | 1 | False | - | - | - | *(masuk ELSE)* |
| 16 | Cek `total_awal>=300000` → **False** (100000<300000) | 100000 | 1 | False | - | - | - | |
| 19 | `persen_diskon <- 0.0` | 100000 | 1 | False | 0.0 | - | - | |
| 22 | `nominal_diskon <- 100000*0.0` | 100000 | 1 | False | 0.0 | 0 | - | |
| 23 | `total_bayar <- 100000-0` | 100000 | 1 | False | 0.0 | 0 | 100000 | |
| 24-25 | Output | | | | | | | **Diskon = 0, Total Bayar = 100000** |

---

### Ringkasan Hasil Uji

| Kasus | Nominal Diskon | Total Bayar |
|---|---|---|
| A | Rp 37.500 | Rp 212.500 |
| B | Rp 17.500 | Rp 332.500 |
| C | Rp 0 | Rp 100.000 |

Kasus C secara khusus membuktikan bahwa **loop validasi (Repeat-Until)** bekerja dengan benar: sistem menolak input negatif pada iterasi pertama dan baru melanjutkan proses perhitungan setelah pengguna memasukkan nilai valid pada iterasi kedua.
