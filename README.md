# Jarkom-Modul-3-2025-K37
| Nama                         | NRP        |
| ---------------------------- | ---------- |
| Azaria Raissa Maulidinnisa   | 5027241043 |
| Daniswara Fausta Novanto     | 5027241050 |

# Soal 1
Membuat topologi jaringan sesuai soal yang diberikan. 

<img width="784" height="486" alt="image" src="https://github.com/user-attachments/assets/016ffab2-1c78-4935-816d-4e7085a35397" />

Selanjutnya adalah membangun jaringan komunikasi awal, memastikan setiap node dapat terhubung ke internet. Konfigurasi router utama yaitu Durin, sebagai gateway untuk semua subnet internal dan melakukan NAT ke jaringan luar. 
```
auto eth0
iface eth0 inet dhcp

# Subnet 1 – Laravel Workers
auto eth1
iface eth1 inet static
    address 10.82.1.1
    netmask 255.255.255.0

# Subnet 2 – Clients
auto eth2
iface eth2 inet static
    address 10.82.2.1
    netmask 255.255.255.0

# Subnet 3 – DNS & DHCP
auto eth3
iface eth3 inet static
    address 10.82.3.1
    netmask 255.255.255.0

# Subnet 4 – Database & Forwarder
auto eth4
iface eth4 inet static
    address 10.82.4.1
    netmask 255.255.255.0

# Subnet 5 – PHP Workers
auto eth5
iface eth5 inet static
    address 10.82.5.1
    netmask 255.255.255.0
```
Setelah memastikan konfigurasi, jalankan perintah ``apt update && apt install iptables -y`` dan jalankan ``iptables -t nat -A POSTROUTING -s 10.82.0.0/16 -o eth0 -j MASQUERADE``. Lalu, lakukan konfigurasi untuk setiap node statis yang ada berdasarkan topologi yang telah dibuat. 
```

#Elendil 
auto eth0
iface eth0 inet static
    address 10.82.1.10
    netmask 255.255.255.0
    gateway 10.82.1.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Isildur
auto eth0
iface eth0 inet static
    address 10.82.1.11
    netmask 255.255.255.0
    gateway 10.82.1.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Anarion
auto eth0
iface eth0 inet static
    address 10.82.1.12
    netmask 255.255.255.0
    gateway 10.82.1.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Miriel
auto eth0
iface eth0 inet static
    address 10.82.1.20
    netmask 255.255.255.0
    gateway 10.82.1.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Elros
auto eth0
iface eth0 inet static
    address 10.82.1.50
    netmask 255.255.255.0
    gateway 10.82.1.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Galadriel
auto eth0
iface eth0 inet static
    address 10.82.2.10
    netmask 255.255.255.0
    gateway 10.82.2.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Celeborn
auto eth0
iface eth0 inet static
    address 10.82.2.11
    netmask 255.255.255.0
    gateway 10.82.2.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf   

#Oropher
auto eth0
iface eth0 inet static
    address 10.82.2.12
    netmask 255.255.255.0
    gateway 10.82.2.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Pharazon
auto eth0
iface eth0 inet static
    address 10.82.2.50
    netmask 255.255.255.0
    gateway 10.82.2.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Celebrimbor
auto eth0
iface eth0 inet static
    address 10.82.2.20
    netmask 255.255.255.0
    gateway 10.82.2.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Erendis
auto eth0
iface eth0 inet static
    address 10.82.3.2
    netmask 255.255.255.0
    gateway 10.82.3.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Amdir
auto eth0
iface eth0 inet static
    address 10.82.3.3
    netmask 255.255.255.0
    gateway 10.82.3.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Aldarion
auto eth0
iface eth0 inet static
    address 10.82.4.2
    netmask 255.255.255.0
    gateway 10.82.4.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Palantir
auto eth0
iface eth0 inet static
    address 10.82.4.3
    netmask 255.255.255.0
    gateway 10.82.4.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Narvi
auto eth0
iface eth0 inet static
    address 10.82.4.4
    netmask 255.255.255.0
    gateway 10.82.4.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf

#Minastir
auto eth0
iface eth0 inet static
    address 10.82.5.2
    netmask 255.255.255.0
    gateway 10.82.5.1
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
   //up echo "nameserver 10.82.3.2" >> /etc/resolv.conf
```
Kemudian, lakukan konfigurasi juga pada node dinamis.
```
# Gilgalad
auto eth0
iface eth0 inet dhcp
     up echo "nameserver 192.168.122.1" > /etc/resolv.conf

# Amandil
auto eth0
iface eth0 inet dhcp
     up echo "nameserver 192.168.122.1" > /etc/resolv.conf

# Khamul
auto eth0
iface eth0 inet dhcp
    hwaddress ether 16:1c:1f:1a:15:5b
    up echo "nameserver 192.168.122.1" > /etc/resolv.conf
```
Selanjutnya, lakukan verifikasi dengan menjalankan perintah ``ping`` ke gateway.

<img width="702" height="227" alt="Screenshot 2025-11-04 104556" src="https://github.com/user-attachments/assets/24c88aab-66df-44f7-952e-48b0f78d09fa" />

Jalankan ``ping`` antar subnet. 

<img width="666" height="186" alt="Screenshot 2025-11-04 104809" src="https://github.com/user-attachments/assets/fe9de296-c4df-4596-9bca-56e5ff0abdad" />

<img width="698" height="197" alt="Screenshot 2025-11-04 104946" src="https://github.com/user-attachments/assets/de41237e-ec7c-49b6-998c-17a740fd7e4f" />

Terakhir, lakukan ``ping`` ke ``google.com``.

<img width="856" height="183" alt="Screenshot 2025-11-04 104616" src="https://github.com/user-attachments/assets/a11b2513-70f4-4d43-a4c3-4f16b29fbcc5" />

<img width="887" height="184" alt="Screenshot 2025-11-04 104634" src="https://github.com/user-attachments/assets/0e7f2f81-5458-4c52-a33f-19b410e97823" />

<img width="899" height="188" alt="Screenshot 2025-11-04 105023" src="https://github.com/user-attachments/assets/6632d5a3-b6fd-4b67-8c66-45b1d049018f" />

<img width="877" height="182" alt="Screenshot 2025-11-04 105007" src="https://github.com/user-attachments/assets/b9c3dd0e-244b-4412-ba4b-65b410eb9423" />

# Soal 2 
# Soal 3
# Soal 4
# Soal 5
