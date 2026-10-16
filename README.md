# Enterprise Network Automation & Monitoring Platform

Platform jaringan enterprise **virtual** yang dikonfigurasi secara otomatis dan dipantau secara terus-menerus, termasuk satu segmen IoT yang terisolasi. Dibangun sendiri sebagai proyek portofolio jaringan komputer.

> **Status: Fase 0 (perencanaan).** Belum ada konfigurasi atau kode yang berjalan. Repositori ini berisi rancangan, rencana kerja, dan kerangka folder. Status tiap fase diperbarui di [roadmap](docs/02-roadmap.md) seiring pekerjaan selesai.

## Tujuan

1. Membangun topologi enterprise kecil (edge, core, access) dengan VLAN, routing antar-VLAN, dan segmentasi.
2. Mengganti konfigurasi manual dengan **otomasi berbasis kode**: satu sumber kebenaran (YAML), template konfigurasi, dan deployment yang dapat diulang.
3. Memantau kesehatan jaringan (interface, trafik, ketersediaan) dengan dashboard dan alert.
4. Menambahkan **segmen IoT** (broker MQTT dan sensor simulasi) yang terisolasi dengan kebijakan akses yang jelas.
5. Mendokumentasikan semuanya sehingga orang lain dapat mereproduksi lab ini.

## Batasan (dinyatakan sejak awal)

- Seluruh lab berjalan di **lingkungan virtual** pada satu laptop; tidak ada perangkat fisik.
- Ini bukan sistem produksi. Skala dan kinerja yang dilaporkan hanya berlaku untuk lab ini.
- Pilihan platform lab (GNS3, EVE-NG, Containerlab, dan lainnya) belum diputuskan; lihat [ADR-0001](docs/decisions/ADR-0001-platform-lab.md).

## Dokumen

| Dokumen | Isi |
|---|---|
| [docs/00-ringkasan-proyek.md](docs/00-ringkasan-proyek.md) | Garis besar proyek untuk mentor: masalah, ruang lingkup, ukuran keberhasilan |
| [docs/01-arsitektur-dan-ip-plan.md](docs/01-arsitektur-dan-ip-plan.md) | Topologi logis, VLAN, dan rencana alamat IP |
| [docs/02-roadmap.md](docs/02-roadmap.md) | Fase kerja dan daftar periksa |
| [docs/decisions/](docs/decisions/) | Catatan keputusan teknis (ADR) |

## Struktur repositori

```text
.
├── docs/            dokumentasi dan catatan keputusan
├── lab/             definisi topologi dan cara menjalankan lab
├── automation/      sumber kebenaran, template, playbook, skrip
├── monitoring/      konfigurasi pemantauan dan dashboard
├── iot/             broker MQTT, sensor simulasi, kebijakan akses
└── scripts/         skrip bantu (setup, backup, pemeriksaan)
```

## Teknologi yang direncanakan

Belum final; setiap pilihan dicatat sebagai keputusan di `docs/decisions/`.

- **Jaringan:** VLAN, routing antar-VLAN, OSPF, ACL
- **Otomasi:** Ansible, template Jinja2, Python (Netmiko/NAPALM jika perlu)
- **Pemantauan:** SNMP, Prometheus, Grafana (alternatif: LibreNMS atau Zabbix)
- **IoT:** MQTT (Mosquitto), sensor simulasi dengan Python
- **Kualitas:** linting dan pengujian render template di CI

## Roadmap singkat

- [ ] Fase 0: repositori, dokumen, keputusan platform lab
- [ ] Fase 1: topologi dan konfigurasi dasar manual yang terdokumentasi
- [ ] Fase 2: sumber kebenaran dan otomasi konfigurasi
- [ ] Fase 3: pemantauan dan alert
- [ ] Fase 4: segmen IoT
- [ ] Fase 5: pengerasan, deteksi penyimpangan konfigurasi, CI
- [ ] Fase 6: dokumentasi akhir dan demo

Rincian ada di [docs/02-roadmap.md](docs/02-roadmap.md).

## Lisensi

MIT. Lihat [LICENSE](LICENSE).
