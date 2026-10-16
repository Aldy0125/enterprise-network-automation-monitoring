# ADR-0001: Platform lab virtual

- **Status:** Diusulkan (belum diputuskan)
- **Tanggal:** 12 Oktober 2026

## Konteks

Proyek memakai lab virtual pada satu laptop (RAM 16 GB, prosesor Intel i7, Windows dengan Ubuntu). Platform yang dipilih memengaruhi image perangkat yang dapat dipakai, kemudahan otomasi, dan seberapa mudah lab dibuat ulang.

## Kriteria

1. Pemakaian RAM dan CPU per node
2. Ketersediaan dan lisensi image perangkat
3. Dukungan akses otomasi (SSH, API) ke perangkat
4. Kemudahan menyimpan topologi sebagai kode di Git
5. Kedekatan dengan keterampilan yang sudah dimiliki (Cisco)

## Opsi yang dipertimbangkan

| Opsi | Catatan awal |
|---|---|
| Cisco Packet Tracer | Mudah dan sudah dikenal, tetapi dukungan otomasi terbatas dan topologi sulit disimpan sebagai kode |
| GNS3 | Fleksibel; image Cisco perlu diperoleh secara sah |
| EVE-NG (Community) | Berbasis web; image perlu diperoleh sendiri |
| Containerlab | Topologi sebagai kode (YAML), cocok untuk Git; memakai image kontainer sehingga ringan; perlu Linux/WSL dan image yang tersedia |
| Cisco CML (edisi gratis) | Image resmi; batas jumlah node, perlu dicek ketentuan terbarunya |

Seluruh catatan di atas adalah pertimbangan awal dan perlu diverifikasi terhadap dokumentasi resmi sebelum diputuskan.

## Keputusan

Belum ada. Langkah berikutnya: coba platform yang sudah terpasang atau paling mudah, ukur pemakaian RAM dengan topologi tiga node, lalu perbarui dokumen ini.

## Konsekuensi

Akan diisi setelah keputusan diambil.
