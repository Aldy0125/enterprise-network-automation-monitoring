# Arsitektur Logis dan Rencana IP

> Rancangan awal. Nama perangkat dan jumlah node akan disesuaikan dengan platform lab yang dipilih (lihat ADR-0001) dan batas RAM laptop.

## Topologi logis

```text
                       [ Internet / NAT lab ]
                                 |
                            +----+----+
                            | edge-r1 |  routing keluar, NAT
                            +----+----+
                                 |
                     +-----------+-----------+
                     |                       |
                +----+----+             +----+----+
                | core-sw1|=============| core-sw2|   routing antar-VLAN
                +----+----+             +----+----+
                     |                       |
             +-------+-------+       +-------+-------+
             |               |       |               |
        +----+----+     +----+----+ ...
        |access-sw1|    |access-sw2|
        +----+----+     +----+----+
             |               |
   segmen USERS, SERVERS, IOT, GUEST (VLAN di bawah)

   Host layanan (Linux): ansible/monitoring (VLAN MGMT), mqtt + sensor simulasi (VLAN IOT)
```

Jumlah node awal sengaja kecil (satu edge, satu core, satu access) dan baru diperluas bila RAM mengizinkan.

## Rencana VLAN dan subnet

| VLAN | Nama | Subnet | Fungsi |
|---|---|---|---|
| 10 | MGMT | 10.10.10.0/24 | Manajemen perangkat, Ansible, pemantauan |
| 20 | SERVERS | 10.10.20.0/24 | Layanan internal (DNS, NTP, syslog) |
| 30 | USERS | 10.10.30.0/24 | Klien pengguna |
| 40 | IOT | 10.10.40.0/24 | Broker MQTT dan sensor simulasi |
| 50 | GUEST | 10.10.50.0/24 | Tamu, hanya akses keluar (opsional) |
| 99 | UNUSED | - | Port tidak terpakai (dimatikan) |

| Kebutuhan | Rentang |
|---|---|
| Loopback perangkat | 10.255.0.0/24 |
| Link point-to-point | 10.254.0.0/24 (/31 atau /30) |

## Kebijakan akses awal (rencana)

| Dari \ Ke | MGMT | SERVERS | USERS | IOT | Internet |
|---|---|---|---|---|---|
| MGMT | ya | ya | ya | ya | ya |
| SERVERS | tidak | ya | balasan saja | tidak | ya |
| USERS | tidak | layanan tertentu | ya | tidak | ya |
| IOT | tidak | MQTT/NTP/DNS saja | tidak | ya | tidak |
| GUEST | tidak | tidak | tidak | tidak | ya |

Kebijakan ini akan dituangkan sebagai ACL dan diuji pada Fase 4 dan 5. Tabel ini rencana, bukan hasil pengujian.

## Layanan pendukung (rencana)

- **NTP, DNS, syslog:** host Linux di VLAN SERVERS.
- **Pemantauan:** SNMP dari perangkat, dikumpulkan Prometheus, ditampilkan Grafana.
- **Otomasi:** node kontrol Ansible di VLAN MGMT.
- **IoT:** Mosquitto (MQTT) dan skrip Python yang menerbitkan data sensor palsu.
