# ARTA-C Portable v2: dispenser obat TB konsep "pemanggang roti"

Pembaruan terakhir: 26 Nov 2026 (mengikuti isi folder `stl_urut/` versi v5).

Ukuran luar kotak **168 × 226 × 54 mm** (lebar × tinggi × tebal). Dicetak 3D di **Bambu Lab A1 mini** (bed 180 mm).

## Status singkat

| Bagian | Status |
|---|---|
| Kotak (dinding, blok sudut, sambungan puzzle) | Selesai, sudah diaudit (1 bagian utuh, 0 non-manifold, 25/25 lubang baut bertemu pasangannya) |
| Wadah + rack, roda gigi G1/G2, braket servo 1, pemandu, landasan, tutup atas | Selesai, diuji tabrakan di Blender dari 0° sampai 165° |
| Layar CYD, DHT22, LiPo 2 × 803040, USB-C, saklar geser | Selesai |
| Kereta pelatuk (04), servo 2, rel, pelatuk, engkol, corong baki | **Belum didesain ulang. Jangan dicetak dulu** (file 04 belum ada) |
| Dudukan ESP32-C3 | Belum ada. Di dalam kotak belum ada tempat khusus |
| Animasi (`animasi/`) | Masih memakai dinding versi lama, belum ada sambungan puzzle dan fitur terbaru |
| `GAMBAR_TEKNIK_...pdf` dan gambar `rakit/langkah_*.png` | Masih versi lama (sebelum v5), jangan dijadikan acuan |

## Cara kerja

1. Blister obat tetap utuh. PMO menjepitnya di **wadah** (`19` belakang + `20` depan, dikunci pasak).
2. Wadah dimasukkan **dari celah di atas** (celah tutup atas 119,75 × 10,5 mm). Wadah menyembul di atas seperti roti di pemanggang.
3. **Servo 1** memutar G1 (44T) → G2 (36T) dengan pinion 12T yang menggigit **rack di sisi kiri wadah belakang**. Wadah turun satu baris per langkah (24,8 mm = 21,53° di servo).
4. **Servo 2** menggerakkan kereta pelatuk ke kolom 1–4 (jarak kolom 25,0 mm). *(belum final)*
5. **Servo 3** menekan pelatuk ke kubah sampai kaplet tembus foil ke belakang. **Landasan** (`15`) menahan dorongan dan punya 4 celah miring "/" untuk kaplet jatuh. *(pelatuk belum final)*
6. Kaplet meluncur lewat corong ke baki ambil. *(corong belum final)*

### Ukuran blister dan wadah (terukur)

- Blister 103,5 × 179 mm, 4 kolom × 7 baris = 28 kaplet, kubah miring "/".
- Jarak pusat kubah **25,0 mm (kiri-kanan) × 24,8 mm (atas-bawah)**.
- Wadah 117 × 176 mm. Kelonggaran kiri-kanan 0,25 mm per sisi, depan-belakang 0,5 mm per sisi.
- Tutup atas menyisakan tinggi kubah maksimal ±7,7 mm dari papan blister (tinggi kubah asli belum diukur).

## Isi di dinding depan

- **Layar ESP32-2432S028 (CYD 2,8")**: jendela 69 × 50 mm, papan 1,5 mm, papan + kaca 5,5 mm. Kaca rata dengan dinding luar, sentuh bisa dipakai. Dijepit 4 klem sudut (`17`, M3 × 6).
- **DHT22** (sensor saja, tanpa papan): kantong 25 × 15 × 7,7 mm.
- **LiPo 2 × 803040** ditumpuk, paralel (±2000 mAh): kantong 44 × 31 mm. Celah kabel hanya di satu ujung (8 mm).
- **Lubang keluar obat** di bawah DHT22 dan **kantong jari PPG** (`21`) di bawah layar.
- **ESP32-CAM** di dinding depan atas (`01-F`).

## Isi di dinding samping

- **Dinding kanan**: lubang **USB-C tegak** (4,6 × 10 mm) di `01-G`, **saklar geser** di `01-H` (lubang 7,5 × 3,9 mm, bingkai 12,9 × 6,9 mm). Saklar hanya memutus daya (hidup/mati).
- **Dinding kiri**: polos, tanpa lubang (`01-I`, `01-J`). Lubang USB-C dan saklar lama sudah ditutup.

## Part cetak (folder `stl_urut/`, 33 file)

Daftar lengkap dan arah pasang blok sudut ada di `stl_urut/DAFTAR_FILE.md`. Cara mencetak ada di [PANDUAN_CETAK.md](PANDUAN_CETAK.md), cara merakit di [PANDUAN_RAKIT.md](PANDUAN_RAKIT.md).

| Kelompok | File |
|---|---|
| Dinding (10) | 01-A atas, 01-B bawah, 01-C/D belakang bawah/atas, 01-E/F depan bawah/atas, 01-G/H kanan bawah/atas, 01-I/J kiri bawah/atas |
| Blok sudut (4) | 02-A bawah kiri, 02-B bawah kanan, 02-C atas kanan, 02-D atas kiri |
| Mekanisme wadah v5 | 09 braket servo 1, 10 G1 44T, 11 G2 36T/12T, 12 spacer G2, 13 pemandu kiri, 14 pemandu kanan, 15 landasan |
| Wadah | 19 wadah belakang (rack), 20 wadah depan (28 jendela), 26-A/26-B pasak wadah |
| Layar dan sensor | 17 klem layar (4 pcs), 21 kantong jari PPG |
| **Belum didesain ulang** | 03 rel, 05 pelatuk, 06 engkol servo 3, 07 tuas servo 2, 08 braket servo 2, 16 corong baki (04 kereta belum ada) |

Dinding bawah+atas dari satu sisi dicetak terpisah (supaya muat bed 180 mm) lalu disambung. Antar dinding memakai **sambungan puzzle/tab** (36 tab, kelonggaran 0,10–0,15 mm), jadi dinding samping tidak sekadar dibaut ke blok sudut.

## Elektronik

| Komponen | Letak | Catatan |
|---|---|---|
| ESP32-2432S028 (CYD) | dinding depan, jendela layar | otak utama + layar LVGL |
| ESP32-C3 | **belum ada dudukan** | pengendali utama menurut rencana proyek; posisi perlu ditentukan |
| ESP32-CAM | dinding depan atas | verifikasi wajah, komunikasi ESP-NOW |
| DHT22 | kantong DHT22 di dinding depan | butuh pull-up 10 kΩ pada pin data (sensor tanpa papan) |
| LiPo 2 × 803040 paralel | kantong baterai di dinding depan | ±2000 mAh. Samakan tegangan kedua sel sebelum diparalel |
| Modul pengisi daya (IP5306) | di balik dinding kanan | USB-C tegak keluar lewat `01-G`. Posisi konektor terhadap lubang **belum dicek dengan modul asli** |
| Saklar geser 3 kaki (12,5 × 6,5 × 6 mm) | dinding kanan atas | daya hidup/mati |
| MG90S × 3, PCA9685, MAX30102, buzzer, kapasitor 1000 µF | lihat PANDUAN_RAKIT | sama seperti rencana sebelumnya |

Catatan: pembagian pin (CYD I2C GPIO 27/22, DHT dan buzzer di pin ESP32-CAM, komunikasi ESP-NOW) di PANDUAN_RAKIT masih mengikuti rancangan awal dan perlu disesuaikan bila ESP32-C3 dipakai sebagai pengendali.

## Gerakan servo (untuk firmware)

| Servo | Posisi |
|---|---|
| Servo 1 (wadah) | 0° = masuk/keluar wadah. Baris 1 ≈ 21,0° (kalibrasi ±3°), lalu **+21,53° per baris**: 21,0 · 42,5 · 64,1 · 85,6 · 107,1 · 128,7 · 150,2°. **Batas maksimum 158°** (di atas ±160° ujung bawah wadah menabrak blok sudut kanan bawah). |
| Servo 2 (kereta) | Jarak kolom 25,0 mm. Dengan tuas 133 mm: kolom 1…4 ≈ −16,4° / −5,4° / +5,4° / +16,4° dari tengah. *Perkiraan; desain servo 2 belum final.* |
| Servo 3 (pelatuk) | 0° = naik, 180° = tembus. Gerak pelan, tahan 0,5 detik, kembali. *Desain engkol lama, belum final.* |

Simpan baris dan kolom terakhir di NVS agar tidak hilang saat mati daya.

## Yang masih terbuka

- Desain ulang kereta pelatuk (04), servo 2 (lubang braket 08 di dinding belakang berjarak 22 mm, braketnya 30,8 mm), corong baki dan lubangnya di dinding belakang.
- Apakah tinggi kotak 226 mm cukup untuk jarak turun wadah ±325 mm (wadah menyembul di atas tutup).
- Dudukan ESP32-C3 dan ESP32-CAM (ukuran modul belum dikonfirmasi).
- Posisi USB-C terhadap modul IP5306 asli, dan tinggi kubah blister.
- Pembaruan animasi dan gambar teknik.

## Catatan

- Gaya untuk menembus foil blister sekitar 20–30 N. Uji dengan blister asli. Bila MG90S kurang kuat, pertimbangkan MG946R pada braket yang lebih besar.
- Hasil PPG (nadi, SpO₂) hanya untuk pemantauan, bukan diagnosis. Tekanan darah dan gula darah dari PPG hanya estimasi eksperimental.
