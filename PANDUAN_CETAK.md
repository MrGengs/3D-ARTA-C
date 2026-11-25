# Panduan Cetak 3D: ARTA-C Portable v2 (v5)

Untuk file di folder `stl_urut/`, disiapkan untuk **Bambu Lab A1 mini (bed 180 × 180 × 180 mm)**. Semua file sudah dalam posisi cetak. Jangan diputar, kecuali yang disebut di bawah.

## Ringkasan

| | |
|---|---|
| Jumlah file | 33 STL. Semuanya sudah diaudit: satu bagian utuh, 0 non-manifold, tanpa permukaan dobel |
| Nozzle / layer | 0,4 mm / 0,2 mm (roda gigi: 0,12–0,16 mm) |
| Dinding besar | Dicetak dalam dua bagian (bawah dan atas) agar muat bed, lalu disambung |

## Jangan dicetak dulu

Part berikut belum didesain ulang untuk v5: `03_rel_kereta`, `05_pelatuk`, `06_engkol_servo3`, `07_tuas_servo2`, `08_braket_servo2`, `16_corong_baki`. File `04_kereta` memang belum ada. Part ini tetap ada di folder hanya sebagai arsip.

## 1. Bahan

| Bahan | Part |
|---|---|
| **PETG** (disarankan) | `10` G1, `11` G2 |
| PLA | semua part lain. `21_kantong_jari` pakai **PLA hitam** (kedap cahaya untuk sensor PPG) |

Bila hanya ada PLA, roda gigi tetap bisa dicetak PLA, tetapi giginya lebih cepat aus.

## 2. Setelan slicer (Bambu Studio, profil A1 mini)

| Setelan | Nilai |
|---|---|
| Layer | 0,2 mm. Roda gigi (`10`, `11`) dan **rack di `19`**: 0,12–0,16 mm |
| Perimeter | 3 (lubang sekrup kuat). Top/bottom 4/4 |
| Infill | 20 % gyroid. Roda gigi 40–50 % |
| Suhu | PLA 200–210 °C / bed 60 °C. PETG 230–245 °C / bed 75–80 °C |
| Elephant foot compensation | **0,15 mm** (wajib untuk roda gigi dan wadah) |
| XY hole compensation | 0,1 mm bila ada |
| Support | Tidak perlu untuk part yang sudah diaudit (pasang hanya bila slicer menandai overhang pada `15`) |
| Brim | 5 mm untuk `12_spacer_G2` dan pemandu yang tinggi/ramping |

Part yang diputar: `14_pemandu_kanan` (180 mm) **diletakkan diagonal** di bed.

## 3. Cetak uji dulu (kecil, ±20 menit)

1. **`12_spacer_G2`**: baut M3 harus lewat tanpa dipaksa.
2. **`26-A` dan `26-B` (pasak wadah)**: cetak dua-duanya, lalu pilih yang pas.
   - `26-A` Ø1,9 mm × 8 pcs, `26-B` Ø2,0 mm × 8 pcs. Pasak menggantikan baut M2 yang menyatukan wadah depan dan belakang.
   - Pasak harus masuk dengan tekanan jari dan tidak lepas sendiri. Pakai set yang pas, set satunya cadangan.

Cocokkan juga `20_wadah_depan` dengan blister asli (103,5 × 179 mm) sebelum mencetak part besar.

## 4. Urutan cetak

| Tahap | File | Bahan |
|---|---|---|
| 1. Mekanisme wadah | 10 G1, 11 G2, 12 spacer, 09 braket servo 1 | PETG (gear), PLA |
| 2. Wadah | 19 wadah belakang (rack), 20 wadah depan, 26-A + 26-B pasak | PLA |
| 3. Jalur | 13 pemandu kiri, 14 pemandu kanan (diagonal), 15 landasan | PLA |
| 4. Blok sudut | 02-A, 02-B, 02-C, 02-D | PLA |
| 5. Dinding | 01-A atas, 01-B bawah, 01-C/D belakang, 01-E/F depan, 01-G/H kanan, 01-I/J kiri | PLA |
| 6. Layar dan sensor | 17 klem layar (4 pcs), 21 kantong jari PPG | PLA, PLA hitam |

Mulai dari tahap 1–3 agar gerak wadah, rack, dan kecocokan blister bisa diuji lebih dulu. Dinding dicetak belakangan. Waktu dan berat filamen lihat hasil slicing di Bambu Studio (angka lama di dokumen ini sudah dihapus karena tidak sesuai v5).

## 5. Perhatian khusus per part

| File | Catatan |
|---|---|
| 01-A dinding atas | Celah wadah 119,75 × 10,5 mm dengan bibir miring 0,8 mm. Cek wadah masuk tanpa sesak |
| 01-C/D belakang | Banyak lubang baut, termasuk lubang G2 dan braket servo 1. Bed bersih, tanpa angin |
| 01-E depan bawah | Memuat jendela layar 69,4 × 50,4 mm, kantong DHT22, kantong LiPo 2 × 803040, dan celah kabel baterai. Bersihkan semua kantong dari sisa filamen |
| 01-F depan atas | Dudukan ESP32-CAM |
| 01-G kanan bawah | Lubang USB-C tegak 4,6 × 10 mm |
| 01-H kanan atas | Lubang saklar geser 7,5 × 3,9 mm dengan bingkai 12,9 × 6,9 mm |
| 01-I/J kiri | Polos, tanpa lubang |
| 02-A…D blok sudut | **Arah pasang berbeda.** 02-A dan 02-B: lubang tegak menghadap BAWAH. Lihat `DAFTAR_FILE.md` |
| 10 G1 44T | Lubang spline Ø4,7 mm untuk servo |
| 11 G2 36T + 12T | Tebal total 14,6 mm. Gigi 12T diperpanjang 10 mm |
| 13/14 pemandu | Permukaan dalam harus halus. Ampelas bila seret. Celah kiri-kanan wadah hanya 0,25 mm per sisi |
| 15 landasan | Jarak celah 25,0 mm. Empat celah miring "/" harus bersih |
| 17 klem layar | 4 klem: 2 pendek di sisi USB layar, 2 panjang di seberangnya. Baut M3 × 6 |
| 19 wadah belakang | Satu potong utuh 119,25 × 176 mm dengan rack. Rack ditipiskan 0,1 mm (backlash). Gigi harus bersih tanpa undakan |
| 20 wadah depan | 28 jendela, kubah miring "/". Cek dengan blister asli |
| 21 kantong jari PPG | PLA hitam. Jendela sensor harus bersih |

## 6. Setelah dicetak

1. Bersihkan stringing, bibir bawah (elephant foot), terutama di roda gigi, rack, dan tab sambungan.
2. **Coba pasang sambungan puzzle tanpa lem.** Kelonggaran desain 0,10–0,15 mm. Tab harus masuk dengan tekanan ringan. Bila sesak, amplas tipis tonjolannya.
3. Dinding bagian bawah dan atas dari satu sisi disambung dengan lem CA atau epoksi, muka luar rata di atas kaca.
4. Lubang M3: putar sekrup M3 sekali untuk mengulir plastik, lalu lepas.
5. Uji fungsi: wadah masuk dan turun di pemandu tanpa seret, G2 dan rack berputar tanpa melompat gigi.
6. Lanjut ke [PANDUAN_RAKIT.md](PANDUAN_RAKIT.md).

## 7. Masalah yang sering terjadi

| Masalah | Solusi |
|---|---|
| Dinding melengkung (warping) | Bed 60 °C, PEI bersih, brim 5 mm, tutup printer |
| Roda gigi macet atau berisik | Kompensasi 0,15 mm, layer 0,12 mm, ampelas gigi, sedikit grease silikon |
| Lubang sekrup terlalu kecil | Kalibrasi flow atau bor Ø2,5 mm |
| G1 longgar di spline servo | Lem horn bawaan servo ke part |
| Kubah blister tidak pas di jendela | Ukur blister lagi dan kabari agar wadah disesuaikan |

## 8. Bahan non-cetak (yang sudah pasti)

- Baut M3 × 10 countersink (dinding ke blok sudut, part dalam ke dinding belakang, tutup atas), M3 × 8 (pemandu kanan), M3 × 6 (klem layar), M3 × 45 + mur nyloc + ring (poros G2), M3 × 12 + mur (kantong jari PPG). Jumlah pasti ada di PANDUAN_RAKIT.
- Pasak wadah dicetak (tidak perlu baut M2).
- MG90S × 3, PCA9685, ESP32-2432S028, ESP32-CAM, ESP32-C3, DHT22 + resistor 10 kΩ, LiPo 803040 × 2, modul IP5306 (USB-C), saklar geser 3 kaki 12,5 × 6,5 × 6 mm, MAX30102, buzzer, kapasitor 1000 µF.
- Lem CA atau epoksi untuk sambungan dinding; lem tembak untuk ESP32-CAM, DHT22, dan MAX30102.
