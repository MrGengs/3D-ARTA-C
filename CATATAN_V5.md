# ARTA-C v5 — mekanisme wadah, rack, dan roda gigi (sudah diuji tabrakan di Blender)

## Yang salah di desain lama
- Servo 1 di braket lama (09) berjarak ±39 mm dari G2, padahal G1 harus berkait ke 12T (jarak 26 mm). Roda gigi tidak akan pernah berkait.
- Wadah belakang tidak punya rack sama sekali.
- G1 40T tidak muat di antara dinding kiri dan wadah (butuh 42 mm, tersedia 41 mm).
- Celah pemandu kiri/kanan dan tutup atas tidak sesuai tebal wadah + rack.

## Part baru yang perlu dicetak (folder stl_urut, awalan v5)
| File | Isi | Bahan | Jml |
|---|---|---|---|
| 19_wadah_belakang | Wadah belakang + rack m1 di sisi kiri, satu potong 119,25 x 176 | PLA | 1 |
| 10_gear_G1 | G1 44 gigi, m1, lubang spline Ø4,7 | PETG | 1 |
| 11_gear_G2 | G2 dengan 12T diperpanjang jadi 10 mm (total tebal 14,6) | PETG | 1 |
| 09_braket_servo1 | Braket servo 1, pakai lubang dinding belakang yang sama | PLA | 1 |
| 13_pemandu_kiri | Jalur kiri untuk wadah + rack | PLA | 1 |
| 14_pemandu_kanan | Jalur kanan (180 mm, taruh diagonal di bed) | PLA | 1 |
| 15_landasan | Landasan jarak 25,0 mm, 4 celah miring "/", ruang jatuh kapsul di belakang | PLA | 1 |
| 01-A_dinding_atas | Tutup atas: celah 119,75 x 10,5 dengan bibir miring 0,8 mm | PLA | 1 |
Wadah depan tetap 20 (sudah lolos uji).

## Celah (kelonggaran) wadah saat masuk dan turun
- Kiri-kanan: 0,25 mm tiap sisi (tutup atas, pemandu kiri ke ujung gigi rack, pemandu kanan ke tepi wadah).
- Depan-belakang di pemandu: 0,5 mm tiap sisi. Ke landasan: 0,5 mm.
- Tutup atas sisi depan 1,4 mm → kubah boleh setinggi maksimal ±7,7 mm dari papan.
- Rack: gigi ditipiskan 0,1 mm (backlash ±0,9° di G2). Di Blender: 0 mm³ tumpang tindih dari 0° sampai 165°.

## Firmware servo 1 (berubah karena G1 sekarang 44T)
- 66 mm per radian = 1,152 mm per derajat; 1 baris (24,8 mm) = 21,53°.
- Baris 1 ≈ 21,0° (kalibrasi ±3°), baris k = 21,0 + 21,53 x (k-1); baris 7 ≈ 150,2°. 0° = masuk/keluar wadah.
- Titik patuk (tengah landasan) di tinggi z = 186,5 mm dari lantai.

## Baut
- G2: M3 x 45 (dinding 3 + spacer 17,3 + G2 14,6 + ring + mur nyloc).
- Braket servo 1, pemandu kiri, landasan: M3 x 10 dari luar dinding belakang (lubang lama dipakai).
- Pemandu kanan: M3 x 8 dari luar dinding kanan (lubang lama).
- Tutup atas: M3 x 10 countersink ke blok sudut TL/TR.

## Belum selesai
- Kereta pelatuk (04) tidak ada filenya; di animasi masih kotak pengganti.
- Lubang braket servo 2 di dinding belakang (jarak 22 mm) tidak cocok dengan braket 08 (30,8 mm), dan tuas servo 2 harus lewat di depan wadah. Bagian kereta/servo 2/corong perlu didesain ulang berikutnya.
- (Sudah selesai) Lubang baut dinding dan blok sudut: 25/25 bertemu pasangannya, dinding memakai sambungan tab/puzzle. Lihat DAFTAR_FILE.md.
- Dudukan ESP32-C3 belum ada.
- Batas servo 1: maksimum 158°.
