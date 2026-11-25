# Panduan Merakit ARTA-C Portable v2 (v5)

Panduan ini mengikuti file di `stl_urut/` versi v5. Bagian **kereta pelatuk, servo 2, dan corong baki belum didesain ulang**, jadi perakitannya baru sampai mekanisme wadah dan kotak. Gambar `rakit/langkah_*.png` dan `GAMBAR_TEKNIK_...pdf` masih versi lama dan **tidak sesuai v5**.

> ARTA-C masih prototipe. Ukur ulang blister dan setiap modul sebelum merakit. Hasil PPG hanya untuk pemantauan, bukan diagnosis.

## 1. Daftar yang perlu disiapkan

### Elektronik

| Komponen | Jml | Catatan |
|---|---|---|
| ESP32-2432S028 (CYD 2,8") | 1 | Layar sentuh, jendela 69 × 50 mm |
| ESP32-C3 | 1 | Belum ada dudukannya di kotak |
| ESP32-CAM | 1 | Dudukan di `01-F` |
| MG90S | 3 | Servo 1 = wadah, servo 2 = kereta, servo 3 = pelatuk |
| PCA9685 | 1 | Posisi di dalam kotak belum dicek di CAD |
| DHT22 (sensor saja) | 1 | + resistor pull-up 10 kΩ |
| LiPo 803040 | 2 | Ditumpuk, paralel |
| Modul IP5306 (USB-C) | 1 | Konektor menghadap dinding kanan |
| Saklar geser 3 kaki 12,5 × 6,5 × 6 mm | 1 | Hanya hidup/mati daya |
| MAX30102, buzzer, kapasitor 1000 µF, kabel | | |

### Baut (lubang pilot Ø2,6 mm, jangan dikencangkan berlebihan)

| Baut | Dipakai untuk |
|---|---|
| M3 × 10 countersink | Dinding ke blok sudut, braket servo 1, pemandu kiri, landasan (dari luar dinding belakang), tutup atas ke blok sudut TL/TR |
| M3 × 8 | Pemandu kanan (dari luar dinding kanan) |
| M3 × 6 | Klem sudut layar `17` (4 pcs) |
| M3 × 45 + mur nyloc + ring | Poros G2: dinding 3 + spacer 17,3 + G2 14,6 + ring + mur |
| M3 × 12 + mur ×4 | Kantong jari PPG |
| Pasak cetak `26-A`/`26-B` | Menyatukan wadah depan dan belakang (8 pcs) |

Jumlah M3 × 10 total sebaiknya dihitung ulang dari lubang di STL sebelum membeli. Angka lama (±37) berasal dari desain sebelum v5.

## 2. Siapkan elektronik di meja

1. Program CYD dan ESP32-CAM (CAM lewat FTDI, GPIO 0 ke GND). Update berikutnya lewat OTA.
2. Sambungkan dua LiPo **paralel** (samakan tegangan dulu, selisih kecil), ke BAT IP5306, lalu saklar di jalur output 5 V. Ukur output 5,0–5,2 V sebelum disambung ke modul.
3. Hubungkan semua GND jadi satu. Kapasitor 1000 µF paralel di V+/GND PCA9685.
4. DHT22: data ke pin dengan pull-up 10 kΩ ke 3V3.
5. Uji servo dan setel posisi nol sebelum memasang lengan:

| Servo | Kanal PCA9685 | Posisi nol |
|---|---|---|
| Servo 1 (G1) | 0 | **0°** = posisi masuk wadah |
| Servo 2 | 1 | 90° = tuas tegak lurus |
| Servo 3 | 2 | 0° = pelatuk mundur penuh |

Pembagian pin detail (I2C CYD GPIO 27/22, DHT dan buzzer di ESP32-CAM, ESP-NOW) mengikuti rancangan awal; sesuaikan bila ESP32-C3 yang jadi pengendali utama. Sisakan kabel ±15 cm dan pakai konektor pada kabel yang menyeberang dari dinding depan.

## 3. Rangka belakang dan mekanisme wadah

1. Letakkan dinding belakang (`01-C` + `01-D`) dengan sisi dalam menghadap atas. Pasang blok sudut bawah **02-A** (kiri) dan **02-B** (kanan), lubang tegak menghadap bawah.
2. **Servo 1** ke `09-B_braket_servo1`, lalu braket ke dinding belakang (M3 × 10 dari luar, lubang lama dipakai). Servo di 0°, tekan **G1 44T** (`10`) ke spline.
3. Poros G2: baut M3 × 45 dari luar dinding belakang, ring, **spacer `12`**, **G2** (`11`; pinion 12T di sisi depan, sebidang dengan G1), ring, mur nyloc. G2 berputar bebas tanpa goyang. Putar dengan tangan: G1 dan G2 berkait halus.
4. **Pemandu kiri `13`** dan **landasan `15`**: M3 × 10 dari luar dinding belakang. Celah miring landasan naik ke kanan dilihat dari depan, searah kubah blister.
5. (Belum) servo 2, braket 08, tuas 07, corong 16: desain ulang dulu.

## 4. Kotak

1. Pasang **01-B** (bawah), dinding kiri (**01-I** + **01-J**, polos) dan dinding kanan (**01-G** + **01-H**, USB-C dan saklar) ke blok sudut. Masukkan tab puzzle antar dinding dulu, baru kencangkan baut. Ada 36 tab, kelonggaran 0,10–0,15 mm.
2. Pasang **pemandu kanan `14`** (M3 × 8 dari luar dinding kanan).
3. Pemasangan blok sudut atas **02-C** (kanan) dan **02-D** (kiri).
4. (Belum) rel kereta 03, kereta 04, pelatuk, engkol.

## 5. Wadah dan tutup atas

1. Letakkan blister (103,5 × 179 mm) di `19_wadah_belakang`, kubah menghadap depan.
2. Tutup dengan `20_wadah_depan`; tiap kubah masuk jendelanya. Kunci dengan pasak `26-A` atau `26-B` (pilih yang pas).
3. Pasang **tutup atas `01-A`** (M3 × 10 countersink ke blok sudut TL/TR).
4. Servo 1 di 0°. Masukkan wadah dari celah atas, rack di sisi kiri, sampai rack menyentuh G2. Putar servo pelan ke baris 1. Wadah harus turun rata. **Jangan lewati 158°.**

## 6. Dinding depan

1. **CYD**: masukkan layar ke jendela 69,4 × 50,4 mm dari dalam. Papan bertumpu pada tonjolan, kaca rata dengan dinding luar. Jepit dengan 4 klem sudut `17` (M3 × 6; 2 pendek di sisi USB, 2 panjang di seberangnya). Pastikan kaca tidak menonjol dan tidak terlalu ke dalam.
2. **DHT22**: dorong ke kantong 25 × 15 × 7,7 mm (sensor saja).
3. **LiPo 2 × 803040** ditumpuk di kantong 44 × 31 mm. Kabel keluar lewat satu celah di satu ujung.
4. **Modul IP5306**: pasang agar port USB-C tepat di lubang tegak dinding kanan. *Cek dengan modul asli sebelum mengencangkan.*
5. **Saklar geser** di lubang dinding kanan atas (`01-H`): nub keluar lewat lubang 7,5 × 3,9 mm, badan tertahan di bingkai 12,9 × 6,9 mm.
6. **ESP32-CAM** di `01-F`, lensa di lubang kamera. Double tape busa.
7. **Kantong jari PPG** (`21`, PLA hitam) dari luar, 4 × M3 × 12 + mur. MAX30102 masuk dari bawah.
8. **ESP32-C3 dan PCA9685**: belum punya dudukan. Tempel sementara dan jangan sampai kabel masuk jalur wadah.
9. Rapikan kabel, lalu tutup dinding depan ke blok sudut (M3 × 10). Pastikan tidak ada kabel terjepit.

## 7. Kalibrasi servo 1

| Posisi | Sudut |
|---|---|
| Masuk/keluar wadah | 0° |
| Baris 1…7 | 21,0° · 42,5° · 64,1° · 85,6° · 107,1° · 128,7° · 150,2° (+21,53° per baris) |
| Batas | maksimum 158° |

Sudut dihitung dari model (66 mm per radian = 1,152 mm per derajat; satu baris 24,8 mm). Geser ±3° saat uji dengan blister asli. Servo 2 dan servo 3 dikalibrasi setelah desain kereta selesai.

## 8. Checklist uji

- ☐ USB-C bisa mengecas, saklar geser mematikan semua modul
- ☐ Layar menyala dan sentuhan bekerja, kaca rata dengan dinding
- ☐ DHT22 membaca suhu dan kelembapan
- ☐ Wadah masuk dari atas tanpa sesak dan turun baris 1–7 dengan rata
- ☐ Rack dan G2 tidak melompat gigi, tidak ada tabrakan sampai 158°
- ☐ Sambungan puzzle antar dinding rapat
- ☐ (Setelah kereta selesai) satu patukan = satu kaplet di baki

## 9. Masalah umum

| Masalah | Solusi |
|---|---|
| Wadah tersendat | Amplas gigi rack dan pemandu, cek G2 tidak goyang |
| Wadah sesak masuk | Cek bibir tutup atas dan pemandu; celah kiri-kanan hanya 0,25 mm |
| Tab dinding tidak masuk | Amplas tipis tonjolan tab |
| USB-C tidak pas lubang | Geser modul IP5306 atau perbesar lubang sedikit |
| Alat mati saat servo bergerak | Kapasitor 1000 µF di PCA9685, cek baterai |
