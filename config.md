# Konfigurasi Topologi Jaringan Menggunakan RIP

## Penjelasan Topologi

### Komponen Utama

- *3 Router:*
  - R1 KHI
  - R2 KJ
  - R3 CR
- *3 PC* yang terhubung pada setiap router dengan subnet berbeda:
  - PC dengan subnet 192.168.10.1/24 terhubung ke R1 KBJ
  - PC dengan subnet 192.168.20.1/24 terhubung ke R2 KCR
  - PC dengan subnet 192.168.30.1/24 terhubung ke R3 KHI

### Subnet dan Interface

- *Router R1 KBJ*
  - *Ethernet 2:* Terhubung ke PC dengan subnet 192.168.10.1/24
  - *Ethernet 3:* Terhubung ke jaringan 14.14.14.1, menghubungkan ke R3 KHI
  - *Ethernet 4:* Terhubung ke jaringan 11.11.11.1, menghubungkan ke R2 KCR
- *Router R2 KCR*
  - *Ethernet 2:* Terhubung ke PC dengan subnet 192.168.20.1/24
  - *Ethernet 3:* Terhubung ke jaringan 11.11.11.1, menghubungkan ke R1 KBJ
  - *Ethernet 4:* Terhubung ke jaringan 17.17.17.2, menghubungkan ke R3 KHI
- *Router R3 KHI*
  - *Ethernet 2:* Terhubung ke PC dengan subnet 192.168.30.1/24
  - *Ethernet 3:* Terhubung ke jaringan 17.17.17.2, menghubungkan ke R2 KCR
  - *Ethernet 4:* Terhubung ke jaringan 14.14.14.2, menghubungkan ke R1 KBJ

### Jaringan Antar-Router

- *Jaringan 11.11.11.0/24:* Menghubungkan R1 KBJ dan R2 KCR
- *Jaringan 14.14.14.0/24:* Menghubungkan R1 KBJ dan R2 KHI
- *Jaringan 17.17.17.0/24:* Menghubungkan R2 KCR dan R3 KHI

## Kontributor
- **Nama**: Hafidz Azam Bishiddqi
- **NIM**: 20210801262
- **Mata Kuliah**: Jaringan Komputer Lanjut (UTS)


