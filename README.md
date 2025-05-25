# Ujian Tengah Semester Jaringan Komputer 2
## Berikut adalah langkah-langkah untuk konfigurasi file /etc/dhcp/dhcpd.conf<br>
```bash
#Masukan perintah berikut
sudo nano /etc/dhcp/dhcpd.conf

#Tambahkan konfigurasi berikut
subnet 192.168.10.0 netmask 255.255.255.0 {
  range 192.168.10.100 192.168.10.200;
  option routers 192.168.10.1;
  option subnet-mask 255.255.255.0;
  option domain-name-servers 8.8.8.8;
  option domain-name "praktikum.local;
}
```
---
## Berikut adalah langkah-langkah untuk konfigurasi file /etc/bind/named.conf.local
```bash
#Masukan Perintah berikut
sudo nano /etc/bind/named.conf.local

#Tambahkan

zone "praktikum.local" {
    type master;
    file "/etc/bind/db.praktikum.local";
};
```
---

## Script firewall Iptables
```bash
#Hapus semua aturan sebelumnya
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT DROP
sudo iptables -P INPUT FORWARD DROP
sudo iptables -P INPUT OUTPUT ACCEPT

#Izinkan loopback (localhost)
sudo iptables -A INPUT -i lo -j ACCEPT

#Izinkan koneksi yang sudah established
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#Izinkan paket icmp dari alamat IP 192.168.100.0
sudo iptables -A INPUT -p icmp -s 192.168.100.0/24 -j ACCEPT
 
#Izinkan koneksi SSH (port 22)
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

#Izinkan HTTP (port 80)
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT

#Izinkan HTTPS (port 443)
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT

```
---
