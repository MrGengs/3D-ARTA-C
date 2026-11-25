# Daftar file STL ARTA-C

Aturan nama: **nomor kelompok - huruf urutan _ nama part**. Semua file sudah diaudit (satu bagian utuh, 0 non-manifold, tanpa permukaan dobel). 25 lubang baut dinding sudah diuji bertemu pasangannya.

## Kotak (dinding), sambungan tab/puzzle antar dinding
| File | Isi |
|---|---|
| 01-A_dinding_atas | Tutup atas, celah wadah |
| 01-B_dinding_bawah | |
| 01-C_dinding_belakang_bawah, 01-D_dinding_belakang_atas | |
| 01-E_dinding_depan_bawah | Layar CYD rata dinding, DHT22, LiPo 2 x 803040, kotak IP5306 |
| 01-F_dinding_depan_atas | ESP32-CAM |
| 01-G_dinding_kanan_bawah | Lubang USB-C tegak |
| 01-H_dinding_kanan_atas | Saklar geser 12,5 x 6,5 |
| 01-I_dinding_kiri_bawah, 01-J_dinding_kiri_atas | Polos |

## Blok sudut (perhatikan posisi pasang)
- 02-A_sudut_bawah_kiri: lubang tegak menghadap BAWAH
- 02-B_sudut_bawah_kanan: lubang tegak menghadap BAWAH
- 02-C_sudut_atas_kanan
- 02-D_sudut_atas_kiri

## Mekanisme wadah
09_braket_servo1, 10_gear_G1 (44T, PETG), 11_gear_G2 (36T + 12T, PETG), 12_spacer_G2, 13_pemandu_kiri, 14_pemandu_kanan, 15_landasan

## Wadah
- 19_wadah_belakang (dengan rack), 20_wadah_depan (28 jendela)
- 26-A_pasak_1.9mm (8 pcs) dan 26-B_pasak_2.0mm (8 pcs): cetak keduanya, pakai yang pas

## Layar dan sensor
- 17_klem_layar (4 pcs: 2 pendek di sisi USB layar, 2 panjang di seberangnya)
- 21_kantong_jari (PLA hitam)

## Belum didesain ulang, jangan dicetak dulu
03_rel_kereta, 05_pelatuk, 06_engkol_servo3, 07_tuas_servo2, 08_braket_servo2, 16_corong_baki. Kereta (04) belum ada.

## Batas firmware servo 1
Maksimum 158 derajat (di atas ±160 ujung bawah wadah menabrak blok sudut kanan bawah). Baris 1 ≈ 21°, +21,53° per baris, baris 7 ≈ 150°.
