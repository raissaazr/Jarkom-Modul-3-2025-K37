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
Implementasi DHCP untuk membagi alamat IP secara dinamis berdasarkan alokasi subnet, serta menetapkan alamat tetap untuk Khamul. Konfigurasi DHCP Server di Aldarion. Mendistribusikan alamat IP sesuai dengan aturan yang ditetapkan. Sebelumnya lakukan instalasi service DHCP pada Aldarion.
```
apt update && apt install -y isc-dhcp-server
```
Setelahnya buat file konfigurasi utama di ``/root/start-aldarion.sh``. 
```
nano /root/start-aldarion.sh

#!/bin/bash
# 🛠️ DHCP SERVER CONFIGURATION – Aldarion (Kelompok K37)
# Prefix jaringan: 10.82

PREFIX="10.82"
INTERFACE="eth0"               # interface yang terhubung ke Durin
DNS_MASTER="${PREFIX}.3.2"     # Erendis (DNS Master)

echo "[1/4] Menulis konfigurasi DHCP..."
cat <<EOF > /etc/dhcp/dhcpd.conf
authoritative;
default-lease-time 600;
max-lease-time 7200;

# Keluarga Manusia (Subnet 1)
subnet ${PREFIX}.1.0 netmask 255.255.255.0 {
    range ${PREFIX}.1.6 ${PREFIX}.1.34;
    range ${PREFIX}.1.68 ${PREFIX}.1.94;
    option routers ${PREFIX}.1.1;
    option broadcast-address ${PREFIX}.1.255;
    option domain-name-servers ${DNS_MASTER};
}

# Keluarga Peri (Subnet 2)
subnet ${PREFIX}.2.0 netmask 255.255.255.0 {
    range ${PREFIX}.2.35 ${PREFIX}.2.67;
    range ${PREFIX}.2.96 ${PREFIX}.2.121;
    option routers ${PREFIX}.2.1;
    option broadcast-address ${PREFIX}.2.255;
    option domain-name-servers ${DNS_MASTER};
}

# Subnet 3 (DNS & Fixed IP)
subnet ${PREFIX}.3.0 netmask 255.255.255.0 {
    option routers ${PREFIX}.3.1;
    option broadcast-address ${PREFIX}.3.255;
    option domain-name-servers ${DNS_MASTER};

    host khamul {
        hardware ethernet 16:1c:1f:1a:15:5b;
        fixed-address ${PREFIX}.3.95;
    }
}

# Subnet 4 (Database & DHCP Server)
subnet ${PREFIX}.4.0 netmask 255.255.255.0 {
    option routers ${PREFIX}.4.1;
    option broadcast-address ${PREFIX}.4.255;
    option domain-name-servers ${DNS_MASTER};
}

# Subnet 5 (PHP Workers)
subnet ${PREFIX}.5.0 netmask 255.255.255.0 { }
EOF

echo "[2/4] Mengatur interface DHCP server..."
sed -i "s/^INTERFACESv4=.*/INTERFACESv4=\"${INTERFACE}\"/" /etc/default/isc-dhcp-server

echo "[3/4] Menyiapkan database lease..."
mkdir -p /var/lib/dhcp
touch /var/lib/dhcp/dhcpd.leases

echo "[4/4] Menjalankan DHCP server..."
pkill dhcpd 2>/dev/null
dhcpd -4 -f -d ${INTERFACE} &
sleep 2
echo "✅ DHCP Server Aldarion aktif dan melayani seluruh subnet K37."
```

<img width="573" height="334" alt="Bash Aldarion" src="https://github.com/user-attachments/assets/08ce8511-0c06-42ff-9ab2-7f47b81108bb" />

Selanjutnya untuk konfigurasi DHCP Relay dilakukan di Durin. Install dan jalankan DHCP Relay untuk meneruskan permintaan client ke Aldarion. Untuk instalasi paket jalankan:
```
apt update && apt install -y isc-dhcp-relay
```
Setelahnya lakukan konfigurasi untuk DHCP Relay pada file ``/root/start-durin.sh``
```
nano /root/start-durin.sh

#!/bin/bash
# 🔁 DHCP RELAY CONFIGURATION – Durin (Kelompok K37)
# Prefix jaringan: 10.82

PREFIX="10.82"
DHCP_SERVER="${PREFIX}.4.2"       # IP Aldarion (DHCP Server)
INTERFACES="eth1 eth2 eth3 eth4 eth5"  # Interface antar subnet

echo "[1/3] Menulis konfigurasi DHCP Relay..."
cat <<EOF > /etc/default/isc-dhcp-relay
SERVERS="${DHCP_SERVER}"
INTERFACES="${INTERFACES}"
OPTIONS=""
EOF

echo "[2/3] Menjalankan DHCP relay..."
pkill dhcrelay 2>/dev/null
dhcrelay -d ${DHCP_SERVER} ${INTERFACES} &
sleep 2

echo "[3/3] DHCP Relay Durin aktif dan meneruskan permintaan ke Aldarion (${DHCP_SERVER})."

```

<img width="561" height="59" alt="Bash Durin" src="https://github.com/user-attachments/assets/abd209bb-9d7c-42f4-84d6-75466ebb6f63" />

Setelah kedua skrip dijalankan, client dinamis harus meminta IP. 
```
# Jalankan di Amandil, Gilgalad, dan Khamul
dhclient eth0
ip a
```
Hasil yang diharapkan berupa IP Dinamis sesuai range yang ditetapkan untuk Amandil dan Gilgalad. Sedangkan IP Fixed ``10.82.3.95`` untuk Khamul. 

<img width="579" height="348" alt="Cek IP a Node Dinamis" src="https://github.com/user-attachments/assets/17ffe223-e46d-45b8-9dec-b7903f82c8a5" />

# Soal 3
Mengubah Ministir menjadi DNS Forwarder Sentral untuk mengontrol semua arus informasi yang keluar ke internet. Semua node harus menggunakan Minastir ``10.82.5.2`` sebagai nameserver utama. Minastir sendiri berada di subnet 5 dan bertindak sebagai perantara untuk semua permintaan DNS. Sebelumnya, instalasi service ``BIND9`` untuk pengujian. 
```
apt-get update && apt-get install -y bind9 dnsutils
```
Kemudian lakukan konfigurasi pada ``/root/start-minastir.sh``.
```
nano /root/start-minastir.sh

#!/bin/bash
# ==========================================
# 🌐 Konfigurasi Minastir – DNS Forwarder K37
# ==========================================
# Jaringan internal: 10.82.0.0/16
# Minastir terhubung ke Durin melalui eth0 (10.82.5.2)
# Gateway: 10.82.5.1 (Durin)
# Forward DNS eksternal: 192.168.122.1 (host DNS)

FORWARD_DNS="192.168.122.1"
BIND_CONF="/etc/bind/named.conf.options"

echo "[1/6] Memastikan paket bind9 dan dnsutils terpasang..."
apt-get update -y >/dev/null
apt-get install -y bind9 dnsutils >/dev/null

echo "[2/6] Menulis konfigurasi BIND9 sebagai forwarder..."
cat > $BIND_CONF <<EOF
options {
    directory "/var/cache/bind";

    # Forward semua query keluar ke DNS eksternal (host)
    forwarders {
        ${FORWARD_DNS};
    };

    allow-query { any; };
    allow-recursion { any; };
    listen-on { any; };
    listen-on-v6 { any; };
    recursion yes;
};

logging {
    channel query_log {
        file "/var/log/named_queries.log" versions 3 size 5m;
        severity info;
        print-time yes;
    };
    category queries { query_log; };
};
EOF

echo "[3/6] Menyetel resolv.conf agar Minastir resolve ke dirinya sendiri..."
rm -f /etc/resolv.conf
echo "nameserver 127.0.0.1" > /etc/resolv.conf

echo "[4/6] Mengaktifkan IP forwarding (opsional untuk routing kecil)..."
echo "net.ipv4.ip_forward=1" > /etc/sysctl.conf
sysctl -p >/dev/null

echo "[5/6] Menjalankan ulang layanan BIND9..."
pkill named 2>/dev/null
/usr/sbin/named -g -u bind &
sleep 2


echo "[6/6] Pengujian DNS Forwarder lokal..."
dig google.com @127.0.0.1 +short | head -n 3
STATUS=$?
if [ $STATUS -eq 0 ]; then
    echo "✅ Minastir berhasil resolve domain eksternal (via ${FORWARD_DNS})"
else
    echo "⚠️  Cek kembali koneksi gateway (${FORWARD_DNS})"
fi

echo
echo "📘 Detail Konfigurasi Minastir:"
echo "   - IP Address : 10.82.5.2"
echo "   - Gateway    : 10.82.5.1 (Durin)"
echo "   - Forwarders : ${FORWARD_DNS}"
echo "   - Jaringan   : 10.82.0.0/16"
echo "   - Service    : BIND9 (mode forwarder)"

chmod +x /root/start-minastir.sh
bash /root/start-minastir.sh
```
Setelah Minastir berjalan, semua node internal diubah untuk menggunakan Minastir sebagai nameserver utama. Pada semua node statis, jalankan :
```
echo "nameserver 10.82.5.2" > /etc/resolv.conf
```
Di Aldarion, ubah nilai ``option domain-name-servers`` dari yang sebelumnya ``10.82.3.2`` menjadi ``10.82.5.2`` di ``/etc/dhcp/dhpcd.conf``. Setelahnya restart DHCP server dan minta IP baru di client. 
```
# Di Aldarion's /etc/dhcp/dhcpd.conf:
# ...
option domain-name-servers 10.82.5.2; # Ganti Erendis dengan Minastir!
```
Pengujian harus dijalankan dari client untuk memastikan Minastir bekerja. Misal di ELros, jalankan :
```
#Tes dari Client: Elros

apt update
apt install -y bind9 dnsutils net-tools

# Pastikan konfigurasi tidak rusak

# Hapus file lama: rm -f /etc/bind/named.conf.options

# Buat ulang file: nano /etc/bind/named.conf.options

# options {
#    directory "/var/cache/bind";
#
#    forwarders {
#        192.168.122.1;
#    };
#
#    allow-query { any; };
#    allow-recursion { any; };
#    recursion yes;
#
#    listen-on { any; };
#    listen-on-v6 { any; };
# };

# Hapus cache & periksa error: rm -f /var/cache/bind/*

# Hapus cache & periksa error: named-checkconf /etc/bind/named.conf

# Stop yang lama: pkill named 2>/dev/null

# Jalankan manual: /usr/sbin/named -g -u bind &

# Cek service jalan: netstat -tulnp | grep 53

# Uji di Minastir: dig google.com @127.0.0.1

echo "nameserver 10.82.5.2" > /etc/resolv.conf
ping -c 3 google.com
dig google.com
```
Jika berhasil menampilkan IP, berarti semua lalu lintas informasi keluar telah melewati pemeriksaan di Ministir. 

<img width="570" height="165" alt="Bash Minastir" src="https://github.com/user-attachments/assets/a0f210da-981a-4912-ae1d-977852f026ce" />

# Soal 4
# Soal 5
