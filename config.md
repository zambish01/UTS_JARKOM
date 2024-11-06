## Kontributor
- **Nama**: Hafidz Azam Bishiddqi
- **NIM**: 20210801262
- **Mata Kuliah**: Jaringan Komputer Lanjut (UTS)

## Gambaran Umum Topologi Jaringan

- **Setiap Kampus**: Menggunakan topologi bintang.
  - Semua komputer di lab terhubung ke switch pusat.
  - Switch terhubung ke router, yang menyediakan akses internet dan konektivitas antar kampus.

- **Konektivitas Antar Kampus**: Dicapai melalui MPLS (Multiprotocol Label Switching).

## Langkah-Langkah untuk Menghubungkan Antar Kampus

### 1. **Menyusun Jaringan Lokal di Setiap Kampus**
   - Sambungkan semua komputer di setiap lab ke switch pusat.
   - Hubungkan switch ke router.
   - Konfigurasikan router untuk menyediakan akses internet bagi setiap kampus.

### 2. **Membangun Konektivitas Antar Kampus**
   - **Pengaturan **:
     - Konfigurasikan gateway di setiap router kampus.
     - Atur tunnel VPN antara router di tiga kampus.
     - Pastikan enkripsi untuk transmisi data yang aman.
   - **Pilihan MPLS**:
     - Gunakan layanan MPLS yang disediakan oleh ISP.
     - Konfigurasikan router MPLS untuk memprioritaskan lalu lintas dan memastikan komunikasi antar kampus yang efisien.

### 3. **Central Server**
   - Tempatkan layanan penting (seperti database, aplikasi) di server pusat di kampus utama (Kampus 1).
   - Konfigurasikan akses ke server ini untuk kampus lain melalui MPLS.

### 4. **Manajemen dan Pemantauan Jaringan**
   - Implementasikan alat pemantauan jaringan (misalnya, Nagios, Zabbix) untuk mengelola dan memantau kesehatan jaringan.
   - Pasang firewall untuk mengamankan jaringan di setiap kampus.
   - Gunakan load balancer jika diperlukan untuk mendistribusikan lalu lintas dan menghindari kemacetan.

![topologi jaringan](https://github.com/user-attachments/assets/4286eb40-0787-49dc-be05-6c061048599a)


# Konfigurasi Topologi Jaringan Menggunakan RIP

## Penjelasan Topologi

![Topologi Jarkom](https://github.com/user-attachments/assets/f13693d6-d857-4e0e-977a-96fdcc954a82)


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

- First Steps
Matikan Firewall seperti Windows Defender atau Antivirus lainnya
Sambungkan Laptop dengan MikroTik menggunakan kabel LAN
Buka WinBox → Neighbors → Cari yang MikroTik → Connect
- Static (Manual)
1. Dalam WinBox → IP → Addresses
2. Tambahkan IP Address baru → Contohnya 192.168.10.1/24 → Sesuaikan interface dengan ether dari sambungan kabel LAN → Apply → Ok
3. Buka Control Panel untuk mengatur IP Laptop
4. Control Panel → Network and Internet → Network and Sharing Center → Ethernet → Properties
5. Ubah IPv4 dengan double click → Use the following IP Address → Isi dengan 192.168.10.2 (2 karena 1 sudah digunakan MikroTik) → Tab untuk kolom yang lain → Ok
6. Lakukan Ping terhadap IP Laptop dalam Terminal WinBox
- DHCP (Otomatis)
1. Dalam WinBox → IP → Addresses
2. Tambahkan IP Address baru → Contohnya 192.168.10.1/24 → Sesuaikan interface dengan ether dari sambungan kabel LAN → Apply → Ok
3. Buka Control Panel untuk mengatur IP Laptop
4. Control Panel → Network and Internet → Network and Sharing Center → Ethernet → Properties
5. Ubah IPv4 dengan double click → Obtain an IP Address automatically → Ok
6. Dalam WinBox → IP → DHCP Server
7. Tambahkan DHCP dengan DHCP Setup → Sesuaikan interface dengan ether yang digunakan → Klik Next sampai selesai
8. Buka bagian Leases dalam DHCP Server → Lihat IP dalam bagian Active Addresses
9. Lakukan Ping terhadap IP Address yang ada dalam Leases di Terminal WinBox
- Bridge
1. Dalam WinBox → Bridge
2. Tambahkan Bridge baru → Apply → Ok
3. Tambahkan Bridge Port → Sesuaikan interface dengan ether yang digunakan → Sesuaikan Bridge dengan Bridge yang sudah dibuat → Apply → Ok
4. Tambahkan IP Address → Ubah interface dengan Bridge yang sudah dibuat → Apply → Ok
5. Tambahkan DHCP dengan DHCP Setup → Sesuaikan interface dengan Bridge yang sudah dibuat → Klik Next → Pada bagian DNS Servers ubah menjadi 8.8.8.8 → Klik Next sampai selesai
6. Buka Command Prompt → ipconfig → Lihat IPv4 Address → Lakukan Ping terhadap sesama Laptop (Laptop A melakukan Ping terhadap IP Laptop B dan sebaliknya)
7. Buka XAMPP dan nyalakan → Salin IP Address Laptop satu sama lain untuk melihat web XAMPP jika sudah tersambung
