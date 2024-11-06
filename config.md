## Kontributor
- **Nama**: Hafidz Azam Bishiddqi
- **NIM**: 20210801262
- **Mata Kuliah**: Jaringan Komputer Lanjut (UTS)

## Gambaran Umum Topologi Jaringan

- **Setiap Kampus**: Menggunakan topologi bintang.
  - Semua komputer di lab terhubung ke switch pusat.
  - Switch terhubung ke router, yang menyediakan akses internet dan konektivitas antar kampus.

- **Konektivitas Antar Kampus**: Dicapai melalui VPN (Virtual Private Network) atau MPLS (Multiprotocol Label Switching).

## Langkah-Langkah untuk Menghubungkan Antar Kampus

### 1. **Menyusun Jaringan Lokal di Setiap Kampus**
   - Sambungkan semua komputer di setiap lab ke switch pusat.
   - Hubungkan switch ke router.
   - Konfigurasikan router untuk menyediakan akses internet bagi setiap kampus.

### 2. **Membangun Konektivitas Antar Kampus**
   - **Pengaturan VPN**:
     - Konfigurasikan gateway VPN di setiap router kampus.
     - Atur tunnel VPN antara router di tiga kampus.
     - Pastikan enkripsi untuk transmisi data yang aman.
   - **Pilihan MPLS**:
     - Gunakan layanan MPLS yang disediakan oleh ISP.
     - Konfigurasikan router MPLS untuk memprioritaskan lalu lintas dan memastikan komunikasi antar kampus yang efisien.

### 3. **Layanan Terpusat**
   - Tempatkan layanan penting (seperti database, aplikasi) di server pusat di kampus utama (Kampus 1).
   - Konfigurasikan akses ke server ini untuk kampus lain melalui VPN/MPLS.

### 4. **Manajemen dan Pemantauan Jaringan**
   - Implementasikan alat pemantauan jaringan (misalnya, Nagios, Zabbix) untuk mengelola dan memantau kesehatan jaringan.
   - Pasang firewall untuk mengamankan jaringan di setiap kampus.
   - Gunakan load balancer jika diperlukan untuk mendistribusikan lalu lintas dan menghindari kemacetan.


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
