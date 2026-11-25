# Daftar file STL ARTA-C (versi terbaru, sudah diaudit)

Semua file di folder ini: satu bagian utuh, 0 non-manifold, tidak ada permukaan dobel.
Semua 25 lubang baut dinding sudah diuji bertemu pasangannya di rakitan Blender.

## Kotak (dinding) — semua pakai sambungan tab/puzzle antar dinding
- 01-A3_dinding_atas_v5 (tutup atas, celah wadah)
- 01-B_dinding_bawah
- 01-C_dinding_belakang_bawah, 01-D_dinding_belakang_atas
- 01-E4_dinding_depan_bawah (layar CYD rata dinding, DHT22, LiPo 2x803040 paralel, kotak IP5306)
- 01-F_dinding_depan_atas (ESP32-CAM)
- 01-G2_dinding_kanan_bawah (lubang USB-C tegak)
- 01-H2_dinding_kanan_atas (saklar geser 12,5 x 6,5)
- 01-I_dinding_kiri_bawah, 01-J_dinding_kiri_atas

## Blok sudut (perhatikan posisi pasang)
- 02-A_blok_sudut_bawah_kiri  -> sudut kiri bawah, lubang tegak menghadap BAWAH
- 02-B_blok_sudut_bawah_kanan -> sudut kanan bawah, lubang tegak menghadap BAWAH
- 02-C_blok_sudut_atas_kanan  -> sudut kanan atas (depan)
- 02-D_blok_sudut_atas_kiri   -> sudut kiri atas (depan)

## Mekanisme wadah v5
- 09-B_braket_servo1_v5, 10-B_gear_G1_44T_v5 (PETG), 11-B_gear_G2_36T-12T_v5 (PETG), 12_spacer_G2
- 13-C_pemandu_kiri_v5, 14-C_pemandu_kanan_v5, 15-B_landasan_v5
- 19-D_wadah_belakang_v5_rack, 20-C_wadah_depan_v4_FULL_28_jendela
- 26-A / 26-B pasak wadah (pilih ukuran yang pas)

## Layar & sensor
- 17-B_klem_sudut_layar_4pcs (2 pendek di sisi USB layar, 2 panjang di seberangnya)
- 21_kantong_jari_ppg (PLA hitam)

## Kepala patuk (belum didesain ulang — jangan cetak dulu)
- 03_rel_kereta, 05_pelatuk, 06_engkol_servo3, 07_tuas_servo2, 08_braket_servo2, 16_corong_baki
- Kereta 04 tidak ada filenya.

## Batas firmware servo 1
- Jangan lebih dari 158 derajat: di atas ~160 derajat ujung bawah wadah menabrak blok sudut kanan bawah.
- Baris 1 ~21 derajat, per baris 21,53 derajat, baris 7 ~150 derajat.
