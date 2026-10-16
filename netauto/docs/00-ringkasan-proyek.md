# Ringkasan Proyek (untuk mentor)

**Judul:** Enterprise Network Automation & Monitoring Platform
**Pengerjaan:** individu, dimulai 12 Oktober 2026
**Lingkungan:** lab virtual pada satu laptop (tanpa perangkat fisik)

## 1. Masalah yang ingin dijawab

Konfigurasi jaringan enterprise yang dilakukan manual perangkat demi perangkat mudah salah, sulit diulang, dan sulit diaudit. Perubahan kecil seperti menambah VLAN harus diketik berulang di banyak perangkat, dan penyimpangan konfigurasi baru ketahuan saat ada gangguan. Proyek ini mencoba menunjukkan alur kerja yang lebih baik pada skala lab: konfigurasi dideklarasikan sebagai data, disebarkan secara otomatis, lalu dipantau.

## 2. Tujuan

1. Membangun topologi enterprise kecil dengan segmentasi VLAN dan routing antar-VLAN.
2. Mengotomasi konfigurasi dari satu sumber kebenaran (YAML) dengan template.
3. Memantau status jaringan dan memberi alert untuk kondisi yang ditentukan.
4. Menambahkan segmen IoT yang terisolasi, lengkap dengan trafik sensor simulasi.
5. Mendokumentasikan proses sehingga dapat direproduksi.

## 3. Ruang lingkup

**Termasuk:** topologi virtual, VLAN, routing, ACL dasar, otomasi konfigurasi, backup dan deteksi penyimpangan, pemantauan SNMP dan dashboard, segmen IoT dengan MQTT, dokumentasi.

**Tidak termasuk:** perangkat fisik, kinerja pada skala produksi, integrasi dengan sistem eksternal (ITSM, cloud), dan klaim keamanan tingkat produksi.

## 4. Hasil yang dituju (deliverable)

| # | Hasil | Cara membuktikan |
|---|---|---|
| 1 | Topologi lab yang dapat dijalankan ulang dari definisi di repositori | Panduan di `lab/` dapat diikuti dari awal |
| 2 | Konfigurasi perangkat dihasilkan dari data dan template | Satu perintah menyebarkan perubahan ke semua perangkat target |
| 3 | Deteksi penyimpangan konfigurasi | Perubahan manual yang disengaja terdeteksi dan dilaporkan |
| 4 | Dashboard dan alert | Mematikan satu link menghasilkan alert yang tercatat |
| 5 | Segmen IoT terisolasi | Pengujian akses antar-segmen sesuai kebijakan yang ditulis |
| 6 | Dokumentasi dan demo | README, diagram, dan rekaman demo |

Target ukur yang lebih rinci (misalnya waktu penyebaran dan waktu deteksi) ditetapkan setelah lab berjalan dan diukur, bukan ditebak sebelumnya.

## 5. Risiko dan batasan

| Risiko | Mitigasi |
|---|---|
| RAM laptop terbatas (16 GB) | Topologi dibuat kecil dan bertahap; pilih image ringan; ukur pemakaian sebelum menambah node |
| Image perangkat vendor bersifat berlisensi | Catat keputusan platform di ADR; pertimbangkan image yang boleh dipakai bebas |
| Cakupan membengkak | Kerjakan per fase; fase berikutnya hanya dimulai bila fase sebelumnya terdokumentasi |
| Waktu terbatas karena perkuliahan | Target commit 3–4 hari per minggu, ukuran kecil dan rutin |

## 6. Pertanyaan untuk mentor

1. Apakah ruang lingkup di atas terlalu luas atau terlalu sempit untuk bahan portofolio magang?
2. Apa yang paling dihargai perusahaan dari proyek seperti ini: otomasi, pemantauan, atau keamanan segmen?
3. Adakah alat yang sebaiknya dipelajari lebih dulu (misalnya Ansible atau Prometheus)?
4. Bagaimana sebaiknya hasil ini disajikan pada CV dan GitHub?
