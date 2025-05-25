# Ujian Tengah Semester Jaringan Komputer 2
Berikut adalah langkah-langkah untuk konfigurasi file /etc/dhcp/dhcpd.conf<br>
```bash
#**Masukan perintah berikut**
sudo nano /etc/dhcp/dhcpd.conf

#**Tambahkan konfigurasi berikut**
subnet 192.168.10.0 netmask 255.255.255.0 {
  range 192.168.10.100 192.168.10.200;
  option routers 192.168.10.1;
  option subnet-mask 255.255.255.0;
  option domain-name-servers 8.8.8.8;
  option domain-name "praktikum.local;
}```
---
#azis ganteng
