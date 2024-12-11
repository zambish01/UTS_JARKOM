Rangkuman Jaringan Komputer

Langkah Pertama
1.	Matikan Firewall seperti Windows Defender atau Antivirus lainnya
2.	Sambungkan Laptop dengan MikroTik menggunakan kabel LAN
3.	Buka WinBox → Neighbors → Cari yang MikroTik → Connect

Static (Manual)
1.	WinBox → IP → Addresses
2.	Tambahkan IP Address baru → Contohnya 192.168.10.1/24 → Sesuaikan interface dengan ether dari sambungan kabel LAN → Apply → Ok
3.	Buka Control Panel untuk mengatur IP Laptop
Control Panel → Network and Internet → Network and Sharing Center → Ethernet → Properties
4.	Ubah IPv4 dengan double click → Use the following IP Address → Isi dengan 192.168.10.2 (2 karena 1 sudah digunakan MikroTik) → Tab untuk kolom yang lain → Ok
5.	Lakukan Ping terhadap IP Laptop dalam Terminal WinBox

DHCP (Otomatis)
1.	WinBox → IP → Addresses
2.	Tambahkan IP Address baru → Contohnya 192.168.10.1/24 → Sesuaikan interface dengan ether dari sambungan kabel LAN → Apply → Ok
3.	Buka Control Panel untuk mengatur IP Laptop
Control Panel → Network and Internet → Network and Sharing Center → Ethernet → Properties
4.	Ubah IPv4 dengan double click → Obtain an IP Address automatically → Ok
5.	Dalam WinBox → IP → DHCP Server
6.	Tambahkan DHCP dengan DHCP Setup → Sesuaikan interface dengan ether yang digunakan → Klik Next sampai selesai
7.	Buka bagian Leases dalam DHCP Server → Lihat IP dalam bagian Active Addresses
8.	Lakukan Ping terhadap IP Address yang ada dalam Leases di Terminal WinBox


Bridge
1.	Dalam WinBox → Bridge
2.	Tambahkan Bridge baru → Apply → Ok
3.	Tambahkan Bridge Port → Sesuaikan interface dengan ether yang digunakan → Sesuaikan Bridge dengan Bridge yang sudah dibuat → Apply → Ok
4.	Tambahkan IP Address → Ubah interface dengan Bridge yang sudah dibuat → Apply → Ok
5.	Tambahkan DHCP dengan DHCP Setup → Sesuaikan interface dengan Bridge yang sudah dibuat → Klik Next → Pada bagian DNS Servers ubah menjadi 8.8.8.8 → Klik Next sampai selesai
6.	Buka Command Prompt → ipconfig → Lihat IPv4 Address → Lakukan Ping terhadap sesama Laptop (Laptop A melakukan Ping terhadap IP Laptop B dan sebaliknya)
7.	Buka XAMPP dan nyalakan → Salin IP Address Laptop satu sama lain untuk melihat web XAMPP jika sudah tersambung
Static Routing
1.	Sambungkan Laptop dengan MikroTik seperti berikut:
•	Hubungkan MikroTik A → Laptop A → ether1
•	Hubungkan MikroTik B → Laptop B → ether1
•	Hubungkan kedua MikroTik → ether3
2.	Dalam WinBox → IP → Addresses → Tambahkan IP Address seperti berikut:
•	Laptop A → 192.168.1.1/24
•	Laptop B → 192.168.10.1/24
Tambahkan IP Address untuk MikroTik seperti berikut:
•	Laptop A → 192.168.100.1/24
•	Laptop B → 192.168.100.2/24
3.	Tambahkan DHCP dengan DHCP Setup → Buat 2 DHCP dan sesuaikan dengan interface yang digunakan IP Address ether1 dan IP MikroTik ether3 → Klik Next → Pada bagian DNS Servers ubah menjadi 8.8.8.8 → Klik Next sampai selesai
4.	Buka Control Panel → Network and Internet → Network and Sharing Center → Ethernet → Disable → Change adapter settings → Double click Ethernet untuk Enable kembali
5.	Dalam WinBox → IP → Routes → Tambahkan Routes seperti berikut:
•	Laptop A → Isi Destination dengan 192.168.10.0/24 dan Gateway dengan 192.168.100.2
•	Laptop B → Isi Destination dengan 192.168.1.0/24 dan Gateway dengan 192.168.100.1
6.	Buka Command Prompt → ipconfig → Lihat IPv4 Address → Lakukan Ping terhadap sesama Laptop (Laptop A melakukan Ping terhadap IP Mikrotik B dan Laptop B dan sebaliknya)
7.	Lakukan “tracert -d (IP tujuan)” untuk mengecek jalur apa saja yang dilewati untuk mencapai IP tujuan → Contohnya Laptop A melakukan “tracert -d 192.168.10.1/24” dan Laptop B melakukan “tracert -d 192.168.1.1/24

Static ( Manual )
Langkah - Langkah 

1.	Matikan Firewall jika ingin menggunakan winbox seperti windows defender atau antivirus lainnya. 
2.	Buka winbox dan buat IP ADDRESS ( IP > Adresses > Apply > Ok )
3.	Lanjutkan Ke Control Panel untuk mengatur IP Laptop  Network Intermet > Network and sharing center > ethernet > Properties > Kemudian klik 2 kali bagian IPv4
Kemudian atur IP adress seperti diawal (192.168.10.2 ) kenapa 2 karena 1 sudah di gunakan di mikrotik lalu tab saja klik OK.
4.	Lakukan ping terhadap Ip tersebut 

DHCP ( Otomatis )
1.	Lakukan tahap 1 - 3 
2.	Pastikan ip yang dibuat tidak sama dengan ip yang telah dibuat sebelumnya 
3.	Lalu buka lagi control panel, Lalu ubah menjadi Obtain an Ip address automatically, Klik ok.
4.	Lalu buka winbox > Ip > DHCP server > DHCP setup > Pilih ether yang digunakan, Klik, Kemudian Lanjut ke Leases, Lakukan ping terhadap ip tersebut (192.168.40.254) Tanda IP sudah aktid atau work.
Bridge
1.	Buat Bridge > Klik ikon + Buat port, Pada saat membuat port sesuaikan dengan ether yang digunakan.
2.	Setelah itu buat Ip Adreess > Ubah interface bridge.
3.	Buka DHCP server lalu setting ke bridge, Pada saat di bagian DNS ubah menjadi 8.8.8.8
4.	Buka XAMPP kemudian buka cmd lakukan IPCONFIG di laptop yang menyalakan XAMPP. Salin hasil IPv4 Address seperti gambar diatas yaitu 192.168.20.253.
5.	Cek IP yang telah didapatkan di laptop satunya.
6.	Cek ip yang disalin di laptop satunya.

 routing
Butuh Laptop azam (Mikrotik A)  dan Laptop Bagus (Mikrotik B)
Langkah-langkah :
1.	Hubungkan Laptop Nopal dengan Mikrotik A di ether 1. 
2.	Hubungkan Laptop Imam dengan Mikrotik B di ether 1.
3.	Hubungkan kedua mikrotik di ether 3.

Langkah-langkah pada Winbox : 
1.	Buka winbox lalu buka Ip address lalu bikin Ip 
Laptop azam : 192.168.1.1/24
Laptop bagus : 192.168.10.1/24
2.	Buat Ip untuk mikrotik 
Laptop azam : 192.168.100.1/24
Laptop bagus : 192.168.100.2/24
3.	Buat dhcp server > Dhcp setup > Buat 2 Dhcp setup sesuaikan ip address di ether 1 dan ip mikrotik di ether 3  > Dns server ubah menjadi 8.8.8.8 . 
4.	Buka control panel > Internet/Network > Properties > Ethernet > Disable > Change adaptor setting > Double klik ethernet > enable.
5.	Masuk winbox > Buka Ip > Routes > Tambah routes +
Laptop azam : Isi destination dengan 192.168.10.0/24 dan gateway dengan 192.168.100.2 . 
Laptop bagus : Isi destination dengan 192.168.1.0/24 dan gateway dengan 192.168.100.1 . 
6.	Masuk cmd lalu lakukan ipconfig di kedua laptop.
7.	Setelah mendapatkan ip masing-masing laptop, lakukan ping di laptop azam dengan ip laptop bagus dan mikrotik B dan lakukan ping di laptop imam dengan ip laptop Nopal dan mikrotik A.
8.	lakukan tracert -d (masukan ip laptop azam di laptop bagus, sedangkan ip laptop bagus di laptop azam).


Routing Dynamic
1.	Siapkan 2 mikrotik
2.	Laptop bagus dan pandu  : mikrotik 1
Laptop azam dan restu : mikrotik 2
3.	Buatkan Ip Address
Laptop bagus > ether 1 > 192.168.1.1/24
laptop pandu > ether 3 > 192.168.3.1/24
Laptop untuk router > ether 2 > 10.10.10.1/24
dan , 
Laptop azam > ether 1 > 192.168.2.1/24
Laptop restu > ether 3 > 192.168.4.1/24
Laptop untuk router > ether 2 > 10.10.10.2/24
4.	Buka routing > rip
Buat interface masing - masing yaitu ether 1 dan ether 2 serta ether 3 (atau setting all )
Network > laptop bagus > 10.10.10.0/24 dan 192.168.1.0/24
Network > laptop azam > 10.10.10.0/24 dan 192.168.2.0/24
Network > laptop pandu > 10.10.10.0/24 dan 192.168.3.0/24
Network > laptop restu > 10.10.10.0/24 dan 192.168.4.0/24
5.	Buka dhcp server > dhcp setup > buat ip untuk masing masing laptop baik mikrotik 1 ataupun 2 (ip mikrotik tidak perlu dibuat)
6.	 Buka cmd lakukan ipconfig lalu lakukan ping dari beberapa laptop.

Subnet Mask
Jenis-jenis Subnet Mask
•	Kelas A: Default mask 255.0.0.0 atau /8
o	Mendukung hingga 16 juta alamat host.
•	Kelas B: Default mask 255.255.0.0 atau /16
o	Mendukung hingga 65 ribu alamat host.
•	Kelas C: Default mask 255.255.255.0 atau /24
o	Mendukung hingga 254 alamat host.
Perhitungan Subnet
•	Subnet Mask: Menentukan jumlah subnet dan host per subnet.
•	Rumus:
o	Jumlah subnet: 2n2^n2n, di mana nnn adalah jumlah bit subnet yang dipinjam.
o	Jumlah host per subnet: 2h−22^h - 22h−2, di mana hhh adalah jumlah bit host (dikurangi 2 untuk alamat network dan broadcast).
RIP (Routing Information Protocol)
1. Menghubungkan IP Saya dengan IP Teman pada Satu MikroTik
Menggunakan RIP:
1.	Setup Address:
o	Konfigurasikan IP di masing-masing perangkat (laptop azam dan bagus) melalui WinBox: 
o	IP → Addresses → Tambahkan IP Address
Contoh: 
	azam: 192.168.1.1/24 pada interface ether1
	bagus: 192.168.2.1/24 pada interface ether2
2.	Aktifkan RIP:
o	Masuk ke Routing → RIP.
o	Tambahkan interface yang digunakan (ether1 dan ether2) pada menu Interfaces.
3.	Tambahkan Jaringan:
o	Masuk ke Routing → RIP → Networks dan tambahkan jaringan Saya dan bagus: 
	192.168.1.0/24
	192.168.2.0/24
4.	Uji Koneksi:
o	Gunakan perintah ping dari terminal untuk memastikan IP Saya dapat berkomunikasi dengan IP bagus.
Menggunakan OSPF:
1.	Setup Address:
o	Sama seperti konfigurasi pada RIP.
2.	Aktifkan OSPF:
o	Masuk ke Routing → OSPF → Interfaces.
o	Tambahkan interface Saya (ether1) dan teman (ether2) ke dalam OSPF.
3.	Tambahkan Area:
o	Masuk ke Routing → OSPF → Networks.
o	Masukkan jaringan Anda dan teman dalam Area 0 (Backbone).
4.	Verifikasi:
o	Lihat tabel routing OSPF dan gunakan ping untuk memastikan konektivitas.

Menggunakan BGP:
1.	Setup Address:
o	Sama seperti konfigurasi RIP atau OSPF.
2.	Aktifkan BGP Instance:
o	Masuk ke Routing → BGP → Instances.
o	Tambahkan instance dengan Router ID (misalnya 192.168.1.1) dan AS Number (misalnya 65001).
3.	Tetapkan Peer:
o	Masuk ke Routing → BGP → Peers.
o	Tambahkan tetangga (IP teman) dengan AS Number yang sama (65001).
4.	Tambahkan Jaringan:
o	Masuk ke Routing → BGP → Networks dan tambahkan jaringan Anda serta teman.
5.	Verifikasi:
o	Gunakan tabel BGP Sessions untuk melihat status koneksi.

2. Menghubungkan IP Anda dengan IP Teman di MikroTik Berbeda
dengan menggunakan dua MikroTik yang dihubungkan menggunakan interface (misalnya, ether3).
Menggunakan RIP:
1.	Setup Address:
o	Konfigurasikan IP antar-MikroTik melalui interface penghubung: 
	MikroTik A (Anda): 192.168.10.1/24 pada ether3
	MikroTik B (teman): 192.168.10.2/24 pada ether3
2.	Aktifkan RIP pada Kedua MikroTik:
o	Tambahkan ether1, ether3 di MikroTik A, dan ether3, ether1 di MikroTik B ke dalam menu Interfaces di Routing → RIP.
3.	Tambahkan Jaringan:
o	Tambahkan semua jaringan (misalnya, 192.168.1.0/24 dan 192.168.2.0/24) pada menu Networks.
4.	Uji Koneksi:
o	Pastikan semua rute ditambahkan dengan menggunakan ping antar laptop.

Menggunakan OSPF:
1.	Setup Address:
o	Sama seperti langkah pada RIP.
2.	Aktifkan OSPF pada Kedua MikroTik:
o	Tambahkan interface (ether1, ether3) ke dalam Routing → OSPF → Interfaces pada kedua MikroTik.
o	Pastikan semua jaringan berada dalam Area 0 melalui Routing → OSPF → Networks.
3.	Uji Koneksi:
o	Gunakan ping atau perintah traceroute untuk memastikan jalur terhubung.
Menggunakan BGP:
1.	Setup Address:
o	Sama seperti langkah pada RIP.
2.	Aktifkan BGP Instance di Kedua MikroTik:
o	Tambahkan instance dengan Router ID masing-masing (misalnya, 192.168.1.1 dan 192.168.2.1) dan AS Number berbeda.
3.	Tambahkan Peer:
o	Di MikroTik A, tambahkan IP MikroTik B (192.168.10.2) sebagai Neighbor dengan AS Number MikroTik B.
o	Di MikroTik B, tambahkan IP MikroTik A (192.168.10.1) sebagai Neighbor dengan AS Number MikroTik A.
4.	Tambahkan Jaringan:
o	Pastikan semua jaringan diiklankan menggunakan Routing → BGP → Networks.
5.	Verifikasi:
o	Lihat status BGP Sessions untuk memastikan hubungan aktif.

