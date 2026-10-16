# Roadmap

Mulai: 12 Oktober 2026. Magang dijadwalkan Juni 2027, jadi tujuannya memiliki proyek yang terdokumentasi dengan baik sebelum itu. Jadwal di bawah adalah perkiraan awal dan akan diperbarui setelah ada data kecepatan kerja yang nyata.

Ritme kerja: **3–4 hari per minggu dengan commit kecil dan rutin.** Setiap fase selesai bila dokumentasinya ada, bukan sekadar kodenya.

## Fase 0: Fondasi (minggu 1–2)
- [ ] Repositori GitHub dibuat dan README awal ada
- [ ] Ringkasan proyek untuk mentor ditulis
- [ ] Rencana VLAN dan IP ditulis
- [ ] Keputusan platform lab dicatat (ADR-0001)

## Fase 1: Topologi dan konfigurasi dasar (kira-kira Nov 2026)
- [ ] Lab berjalan dan dapat dibuat ulang dari panduan
- [ ] VLAN, trunk, routing antar-VLAN, dan routing ke luar dikonfigurasi manual
- [ ] Konfigurasi dasar tersimpan di repositori beserta penjelasan
- [ ] Pengujian konektivitas didokumentasikan

## Fase 2: Sumber kebenaran dan otomasi (kira-kira Des 2026)
- [ ] Inventori dan data perangkat dalam YAML
- [ ] Template Jinja2 untuk konfigurasi dasar
- [ ] Playbook penyebaran yang dapat diulang tanpa efek samping
- [ ] Backup konfigurasi otomatis

## Fase 3: Pemantauan (kira-kira Jan 2027)
- [ ] SNMP aktif pada perangkat
- [ ] Prometheus dan Grafana berjalan
- [ ] Dashboard status interface dan trafik
- [ ] Alert untuk link down diuji

## Fase 4: Segmen IoT (kira-kira Feb 2027)
- [ ] Broker MQTT di VLAN IOT
- [ ] Sensor simulasi menerbitkan data
- [ ] ACL isolasi segmen diuji sesuai kebijakan
- [ ] Data IoT dan kesehatan segmen tampil di dashboard

## Fase 5: Pengerasan dan kualitas (kira-kira Mar 2027)
- [ ] Deteksi penyimpangan konfigurasi
- [ ] Pengerasan dasar (akses manajemen, port tidak terpakai)
- [ ] CI: linting dan pengujian render template

## Fase 6: Penyelesaian (Apr–Mei 2027)
- [ ] README akhir dengan diagram dan hasil ukur
- [ ] Rekaman demo
- [ ] Ringkasan untuk CV

## Catatan

Fase 1 memanfaatkan keterampilan yang sudah dimiliki (konfigurasi router/switch dan VLAN), sedangkan Ansible dan Prometheus dipelajari selama proyek. Bila ada fase yang molor, fase 5 dan 6 yang dipadatkan lebih dulu, bukan fase 1 dan 2.
