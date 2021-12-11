# PRAKTIKUM 5 JARINGAN KOMUNIKASI - T15

Penyelesaian Soal Shift 5 Jaringan Komunikasi 2021\
Kelompok T15
  * Muhammad Yasykur Rafii (05311940000017)
  * Stefanus Lionel Carlo Nugroho (05311940000027)

---

## Topologi pada GNS3
![messageImage_1639182165216](https://user-images.githubusercontent.com/63065991/145656516-ff4469b6-cda5-4268-a857-21757363e02a.jpg)

## Pembagian Subnetting(CIDR)
![Group 2Pembagian Subnet IP  (1)](https://user-images.githubusercontent.com/63065991/145656498-3cdfa432-fef1-4ed9-aacd-b584d4d76e10.png)

## Perhitungan Subnet
| Subnet | Netmask |
|-----------|--------------|
| A1        |  /29         |
| A2        |  /25         |
| A3        |  /22         |
| A4        |  /30         |
| A5        |  /30         |
| A6        |  /23         |
| A7        |  /24         |
| A8        |  /29         |

## CIDR Tree
![Group 4Subnet Tree Modul 5](https://user-images.githubusercontent.com/63065991/145657781-c05b80b4-2d99-4dab-9f59-6f609581e9ed.jpg)

## Pembagian IP
| Subnet | Network ID | Netmask |
|-----------|--------------|------------------|
| A1        |  10.49.4.0   | 255.255.255.248  |
| A2        |  10.49.8.0   | 255.255.255.128  |
| A3        |  10.49.0.0   | 255.255.252.0    |
| A4        |  10.49.16.0  | 255.255.255.252  |
| A5        |  10.49.36.0  | 255.255.255.252  |
| A6        |  10.49.34.0  | 255.255.254.0    |
| A7        |  10.49.32.0  | 255.255.255.0    |
| A8        |  10.49.33.0  | 255.255.255.248  |

---
## Setting GNS
### FOOSHA (sebagai Router/DHCP Relay)
```
auto eth0
iface eth0 inet static
address 192.168.122.2
netmask 255.255.255.0
gateway 192.168.122.1

auto eth1
iface eth1 inet static
address 10.49.16.1
netmask 255.255.255.128
broadcast 10.49.16.3

auto eth2
iface eth2 inet static
address 10.49.36.1
netmask 255.255.252.0
broadcast 10.49.36.3
```

### WATER7 (sebagai Router/DHCP Relay)
```
auto eth0
iface eth0 inet static
address 10.49.16.2
netmask 255.255.255.252
broadcast 10.49.16.3
gateway 10.49.16.1

auto eth1
iface eth1 inet static
address 10.49.8.1
netmask 255.255.255.128
broadcast 10.49.8.127
gateway 10.49.16.1

auto eth2
iface eth2 inet static
address 10.49.0.1
netmask 255.255.252.0
broadcast 10.49.3.255
gateway 10.49.16.1

auto eth3
iface eth3 inet static
address 10.49.4.1
netmask 255.255.255.248
broadcast 10.49.4.7
gateway 10.49.16.1
```

### GUANHAO (sebagai Router/DHCP Relay)
```
auto eth0
iface eth0 inet static
address 10.49.36.2
netmask 255.255.255.252
broadcast 10.49.36.3
gateway 10.49.36.1

auto eth1
iface eth1 inet static
address 10.49.34.1
netmask 255.255.254.0
broadcast 10.49.35.255
gateway 10.49.36.1

auto eth2
iface eth2 inet static
address 10.49.32.1
netmask 255.255.255.0
broadcast 10.49.32.255
gateway 10.49.36.1

auto eth3
iface eth3 inet static
address 10.49.33.1
netmask 255.255.255.248
broadcast 10.49.3.7
gateway 10.49.36.1
```

### DORIKI (sebagai DNS Server)
```
auto eth0
iface eth0 inet static
    address 10.49.4.2
    netmask 255.255.255.248
    broadcast 10.49.4.7
    gateway 10.49.4.1
```

### JIPANGU (sebagai DHCP Server)
```
auto eth0
iface eth0 inet static
address 10.49.4.3
netmask 255.255.255.248
broadcast 10.49.4.7
gateway 10.49.4.1
```

### JORGE (sebagai Web Server)
```
auto eth0
iface eth0 inet static
address 10.49.33.2
netmask 255.255.255.248
broadcast 10.49.33.7
gateway 10.49.33.1
```

### MAINGATE (sebagai Web Server)
```
auto eth0
iface eth0 inet static
address 10.49.33.3
netmask 255.255.255.248
broadcast 10.49.33.7
gateway 10.49.33.1
```

### BLUENO (sebagai Client)
```
auto eth0
iface eth0 inet dhcp
```

### CIPHER (sebagai Client)
```
auto eth0
iface eth0 inet dhcp
```

### ELENA (sebagai Client)
```
auto eth0
iface eth0 inet dhcp
```

### FUKUROU (sebagai Client)
```
auto eth0
iface eth0 inet dhcp
```

---
## Routing
### FOOSHA
![image](https://user-images.githubusercontent.com/63065991/145660290-c0f89722-50d0-43b4-9978-e5084d8e312c.png)

---
## Setting DHCP Relay
### Pada Water7
Melakukan instalasi aplikasi isc-dhcp-relay dengan perintah `apt-get install isc-dhcp-relay -y`
Selanjutnya melakukan edit pada file /etc/default/isc-dhcp-relay seperti pada gambar :
![image](https://user-images.githubusercontent.com/63065991/145660355-3d247120-90a5-4b5c-83fd-adc171dd3d3f.png)

Kemudian melakukan restart DHCP Relay dengan perintah `service isc-dhcp-relay restart`

### Pada Guanhao
Melakukan instalasi aplikasi isc-dhcp-relay dengan perintah `apt-get install isc-dhcp-relay -y`
Selanjutnya melakukan edit pada file /etc/default/isc-dhcp-relay seperti pada gambar :
![image](https://user-images.githubusercontent.com/63065991/145660378-e879ca4f-d79e-47a7-87f6-66c099b80aa0.png)

Kemudian melakukan restart DHCP Relay dengan perintah `service isc-dhcp-relay restart`

---
## Setting DHCP Server
### pada Jipangu
Melakukan instalasi aplikasi isc-dhcp-relay dengan perintah `apt-get install isc-dhcp-relay -y`
Selanjutnya melakukan edit pada file `/etc/default/isc-dhcp-server` seperti pada gambar :
![image](https://user-images.githubusercontent.com/63065991/145660409-be0ef2e6-4d43-48ae-b98f-2ee9dd1e2bf0.png)

Dilanjutkan dengan melakukan edit pada file `/etc/dhcp/dhcpd.conf` untuk menambahkan subnet sebagai berikut:
![image](https://user-images.githubusercontent.com/63065991/145660456-c8237ffb-7dbb-49fe-901e-bcfcea4e0a5e.png)
![image](https://user-images.githubusercontent.com/63065991/145660463-3b9887c1-d700-4409-b17e-08b38f2abc7e.png)

Kemudian melakukan restart DHCP Relay dengan perintah `service isc-dhcp-server restart`

---
## Soal 1
Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.

### pada Foosha
```
iptables -t nat -A POSTROUTING -s 10.49.0.0/18 -o eth0 -j SNAT --to-source 192.$
```

### pada Bueno
![image](https://user-images.githubusercontent.com/63065991/145660575-a980352f-7612-4d48-a03f-9783185cd7f3.png)

---
## Soal 2
Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang merupakan DHCP Server dan DNS Server demi menjaga keamanan.

### pada Foosha
```
iptables -A FORWARD -d 10.49.4.0/29 -i eth0 -p tcp -m tcp --dport 80 -j DROP
```

### pada Jipangu dan Doriki
Melakukan instalasi aplikasi netcat dengan perintah `apt-get install netcat`

### pada Elena
Kemudian pengujian dilakukan pada Elena dengan menjalankan perintah berikut
```
nmap -p 80 10.49.4.2
nmap -p 80 10.49.4.3
```

Berikut adalah dokumentasi hasil pengujian pada Elena dengan menjalankan perintah di atas
![image](https://user-images.githubusercontent.com/63065991/145660911-71bdac67-8c80-49ef-a961-230723adf625.png)

---
## Soal 3
Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

### pada Jipangu dan Doriki
```
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
```

### Testing

Berikut adalah dokumentasi hasil pengujian dengan melakukan ping ke Jipangu pada 4 node secara bersamaan
![image](https://user-images.githubusercontent.com/63065991/145661017-bc8ea3c6-75a9-42a8-8ab1-a19ab6ac7d67.png)
![image](https://user-images.githubusercontent.com/63065991/145661027-738d0c81-69da-4c90-8e3a-8dd8ece15776.png)
![image](https://user-images.githubusercontent.com/63065991/145661033-0883001e-632a-4518-8451-b8f16bf1a459.png)
![image](https://user-images.githubusercontent.com/63065991/145661096-016569fb-b970-4a82-866b-718096a290bc.png)


---
## Soal 4
Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis.

### pada Doriki
Melakukan konfigurasi untuk mengatur batas hari dan waktu sebagai berikut
```
iptables -A INPUT -s 10.49.0.0/19 -m time --timestart 00:00 --timestop 06:59 --$
iptables -A INPUT -s 10.49.0.0/19 -m time --timestart 15:01 --timestop 23:59 --$
iptables -A INPUT -s 10.49.0.0/19 -m time --weekdays Sat,Sun -j REJECT
```

### Testing
Berikut adalah dokumentasi hasil pengujian pada Blueno dengan mengubah waktu menggunakan perintah `date -s "3 DEC 2021 13:00:00"` lalu melakukan ping ke Doriki
![image](https://user-images.githubusercontent.com/63065991/145661218-3a111fc4-6c77-4b96-b07b-2b36cfe583ab.png)

Berikut adalah dokumentasi hasil pengujian pada Cipher dengan mengubah waktu menggunakan perintah `date -s "3 DEC 2021 13:00:00"` lalu melakukan ping ke Doriki
![image](https://user-images.githubusercontent.com/63065991/145661249-2dc1948f-8b74-4f74-9596-c188ba76210a.png) 

---
## Soal 5
Akses dari subnet Elena dan Fukurou hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.

### pada Doriki
Melakukan konfigurasi untuk mengatur batas waktu sebagai berikut
```
iptables -A INPUT -s 10.49.32.0/21 -m time --timestart 07:00 --timestop 14:59 -$
```
### Testing
Berikut adalah dokumentasi hasil pengujian pada Elena dengan mengubah waktu menggunakan perintah `date -s "8 DEC 2021 13:00:00"` lalu melakukan ping ke Doriki
![image](https://user-images.githubusercontent.com/63065991/145661374-70261890-87dd-4441-91ea-45462f0abf3d.png)

Berikut adalah dokumentasi hasil pengujian pada Blueno dengan mengubah waktu menggunakan perintah `date -s "8 DEC 2021 18:00:00"` lalu melakukan ping ke Doriki
![image](https://user-images.githubusercontent.com/63065991/145661385-c5e45b3e-fc97-4780-ba97-f6dc00b8b5e1.png)

---
## Kendala
Bingung untuk pengerjaan soal nomor 6



