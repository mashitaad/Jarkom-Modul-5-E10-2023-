# Jarkom-Modul-5-E10-2023

Laporan Resmi Praktikum Modul 5 Jaringan Komputer 2023

### Kelompok E10

|                       Nama                        |    NRP     |
| :-----------------------------------------------: | :--------: |
|   [Mashita Dewi](https://github.com/mashitaad)    | 5025211036 |
| [Mavaldi Rizqy Hazdi](https://github.com/mavaldi) | 5025211086 |

## Daftar Isi
- [VLSM](#vlsm)
  - [Topologi GNS3](#topologi-gns3)
  - [Topologi VLSM](#topologi-vlsm)
  - [VLSM Tree](#vlsm-tree)
  - [Pembagian Subnet VLSM](#pembagian-subnet-vlsm)
  - [Pembagian IP VLSM](#pembagian-ip-vlsm)
  - [Subnetting](#subnetting)
  - [Routing](#routing)
  - [Konfigurasi](#konfigurasi)
  - [Testing](#testing)
- [Soal 1](#soal-1)
  - [Script](#script)
  - [Testing](#testing)
- [Soal 2](#soal-2)
  - [Script](#script)
  - [Testing](#testing)
- [Soal 3](#soal-3)
  - [Script](#script)
  - [Testing](#testing)


## VLSM

### Topologi GNS3
<img width="476" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/f1cd63f2-e6e5-42ae-a843-6ba741baa344">

### Topologi VLSM
![vlsmmodul5](https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/8e9b9c47-a44d-48d8-a22a-645bc433bb7d)

### VLSM Tree
![Tree CIDR (1)](https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/00956f0c-f2a3-4edb-8b7d-8089d7958b38)

### Pembagian Subnet VLSM
<img width="413" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/7634c881-c1c4-414b-8797-64c372cbb414">

### Pembagian IP VLSM
<img width="407" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/7ac75a88-6f09-4319-a872-c44abc6ad846">

### Subnetting
Aura
```ruby
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#A8
auto eth1
iface eth1 inet static
	address 192.211.0.21
	netmask 255.255.255.252

#A6
auto eth2
iface eth2 inet static
	address 192.211.0.17
	netmask 255.255.255.252
```

Heiter
```ruby
#A8
auto eth0
iface eth0 inet static
	address 192.211.0.22
	netmask 255.255.255.252
	gateway 192.211.0.21

#A9  
auto eth1
iface eth1 inet static
	address 192.211.8.1
	netmask 255.255.248.0

#A10  
auto eth2
iface eth2 inet static
	address 192.211.4.1
	netmask 255.255.252.0
```

Sein
```ruby
#A10
auto eth0
iface eth0 inet static
	address 192.211.4.2
	netmask 255.255.252.0
	gateway 192.211.4.1
```

Frieren
```ruby
#A6
auto eth0
iface eth0 inet static
	address 192.211.0.18
	netmask 255.255.255.252
	gateway 192.211.0.17

#A7  
auto eth1
iface eth1 inet static
	address 192.211.0.13
	netmask 255.255.255.252

#A5  
auto eth2
iface eth2 inet static
	address 192.211.0.9
	netmask 255.255.255.252
```

Himmel
```ruby
#A5
auto eth0
iface eth0 inet static
	address 192.211.0.10
	netmask 255.255.255.252
	gateway 192.211.0.9

#A4  
auto eth1
iface eth1 inet static
	address 192.211.2.1
	netmask 255.255.254.0

#A3  
auto eth2
iface eth2 inet static
	address 192.211.0.129
	netmask 255.255.255.128
```

Fern
```ruby
#A3
auto eth0
iface eth0 inet static
	address 192.211.0.130
	netmask 255.255.255.128
	gateway 192.211.0.129

#A2  
auto eth1
iface eth1 inet static
	address 192.211.0.5
	netmask 255.255.255.252

#A1  
auto eth2
iface eth2 inet static
	address 192.211.0.1
	netmask 255.255.255.252
```

Richter
```ruby
#A2
auto eth0
iface eth0 inet static
	address 192.211.0.6
	netmask 255.255.255.252
	gateway 192.211.0.5
```

Revolte
```ruby
#A1
auto eth0
iface eth0 inet static
	address 192.211.0.2
	netmask 255.255.255.252
	gateway 192.211.0.1
```

Stark
```ruby
auto eth0
iface eth0 inet static
	address 192.211.0.14
	netmask 255.255.255.252
	gateway 192.211.0.13
```

Client
```ruby
auto eth0
iface eth0 inet dhcp
```

### Routing
Aura
```ruby
#Kanan
route add -net 192.211.8.0 netmask 255.255.248.0 gw 192.211.0.22 #A9
route add -net 192.211.4.0 netmask 255.255.252.0 gw 192.211.0.22 #A10

#Bawah
route add -net 192.211.0.0 netmask 255.255.255.252 gw 192.211.0.18 #A1
route add -net 192.211.0.4 netmask 255.255.255.252 gw 192.211.0.18 #A2
route add -net 192.211.0.128 netmask 255.255.255.128 gw 192.211.0.18 #A3
route add -net 192.211.2.0 netmask 255.255.254.0 gw 192.211.0.18 #A4
route add -net 192.211.0.8 netmask 255.255.255.252 gw 192.211.0.18 #A5
route add -net 192.211.0.12 netmask 255.255.255.252 gw 192.211.0.18 #A7
```

Himmel
```ruby
echo nameserver 192.168.122.1 > /etc/resolv.conf

route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.211.0.9 #default
route add -net 192.211.0.0 netmask 255.255.255.252 gw 192.211.0.130 #A1
route add -net 192.211.0.4 netmask 255.255.255.252 gw 192.211.0.130 #A2

echo '
net.ipv4.ip_forward=1' > /etc/sysctl.conf

apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start

echo '
SERVERS="192.211.0.2"
INTERFACES="eth0 eth1 eth2"
OPTIONS=' > /etc/default/isc-dhcp-relay

service isc-dhcp-relay restart
```

Heiter
```ruby
echo nameserver 192.168.122.1 > /etc/resolv.conf

route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.211.0.21 #default

apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start

echo '
SERVERS="192.211.0.2"
INTERFACES="eth0 eth1 eth2"
OPTIONS=' > /etc/default/isc-dhcp-relay

echo '
net.ipv4.ip_forward=1' > /etc/sysctl.conf

service isc-dhcp-relay restart
```

Frieren
```ruby
echo nameserver 192.168.122.1 > /etc/resolv.conf

route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.211.0.17 #default
route add -net 192.211.0.0 netmask 255.255.255.252 gw 192.211.0.10 #A1
route add -net 192.211.0.4 netmask 255.255.255.252 gw 192.211.0.10 #A2
route add -net 192.211.0.128 netmask 255.255.255.128 gw 192.211.0.10 #A3
route add -net 192.211.2.0 netmask 255.255.254.0 gw 192.211.0.10 #A4

echo '
net.ipv4.ip_forward=1' > /etc/sysctl.conf

apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start

echo '
SERVERS="192.211.0.2"
INTERFACES="eth0 eth1 eth2"
OPTIONS=' > /etc/default/isc-dhcp-relay

service isc-dhcp-relay restart
```

Fern
```ruby
echo nameserver 192.168.122.1 > /etc/resolv.conf

route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.211.0.129 #default

apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start

echo '
SERVERS="192.211.0.2"
INTERFACES="eth0 eth1 eth2"
OPTIONS=' > /etc/default/isc-dhcp-relay

echo '
net.ipv4.ip_forward=1' > /etc/sysctl.conf

service isc-dhcp-relay restart
```

Richter
```ruby
echo 'nameserver 192.168.122.1' >/etc/resolv.conf

apt update
apt install netcat -y
apt install bind9 -y
```

Client
```ruby
echo 'nameserver 192.168.122.1' >/etc/resolv.conf
```

### Konfigurasi
Revolte sebagai DHCP Server
```ruby
echo nameserver 192.168.122.1 > /etc/resolv.conf

apt-get update
apt install netcat -y
apt-get install isc-dhcp-server -y

echo 'INTERFACES="eth0"' > /etc/default/isc-dhcp-server

echo '
subnet 192.211.0.0 netmask 255.255.255.252 {

}

subnet 192.211.0.4 netmask 255.255.255.252 {

}

subnet 192.211.0.8 netmask 255.255.255.252 {

}

subnet 192.211.0.16 netmask 255.255.255.252 {

}

subnet 192.211.0.12 netmask 255.255.255.252 {

}

subnet 192.211.0.20 netmask 255.255.255.252 {

}

# SchwerMountain
subnet 192.211.0.128 netmask 255.255.255.128 {
    range 192.211.0.131 192.211.0.195;
    option routers 192.211.0.129;
    option broadcast-address 192.211.0.255;
    option domain-name-servers 192.211.0.6;
    default-lease-time 600;
    max-lease-time 7200;
}

# LaubHills
subnet 192.211.2.0 netmask 255.255.254.0 {
    range 192.211.2.2 192.211.3.2;
    option routers 192.211.2.1;
    option broadcast-address 192.211.3.255;
    option domain-name-servers 192.211.0.6;
    default-lease-time 600;
    max-lease-time 7200;
}

# TurkRegion
subnet 192.211.8.0 netmask 255.255.248.0 {
    range 192.211.8.2 192.211.12.34;
    option routers 192.211.8.1;
    option broadcast-address 192.211.15.255;
    option domain-name-servers 192.211.0.6;
    default-lease-time 600;
    max-lease-time 7200;
}

# GrobeForest
subnet 192.211.4.0 netmask 255.255.252.0 {
    range 192.211.4.2 192.211.6.4;
    option routers 192.211.4.1;
    option broadcast-address 192.211.7.255;
    option domain-name-servers 192.211.0.6;
    default-lease-time 600;
    max-lease-time 7200;
}' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server start
```

Sein dan Stark
```ruby
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt update
apt install netcat -y
apt install apache2 -y
service apache2 start
```

### Testing
Berikut kami lakukan testing untuk memastikan routing yang kami bagikan benar
- Revolte ke Aura
  <img width="697" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/23267311-07f4-403b-a817-3e18e9d82cde">

- Fern ke Revolte
  <img width="691" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/a8b7ba1a-9f51-4ccf-97bd-55a0bdbc70f3">

- Aura ke Richter
  <img width="691" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/93a3b3ad-421a-4e1c-81a6-9f6261ed7cbe">

- Heiter ke Himmel
  <img width="672" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/2cba3f68-6ba6-47e2-b60d-7bebcb98cffe">

## Soal 1
> Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Aura menggunakan iptables, tetapi tidak ingin menggunakan MASQUERADE.

### Script
Kami memasukkan script ini di `bashrc` node Aura
```ruby
ETH0_IP=$(ip -4 addr show eth0 | grep -oP '(?<=inet\s)\d+(\.\d+){3}')

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source $ETH0_IP
```

### Testing
- ping `google` di Aura
  
  <img width="550" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/0bc82adc-d8bc-47c2-96d9-69cd46bb2b0f">

- ping `google` di Fern
  
  <img width="547" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/b0faba42-08dc-446e-9fac-795f723d833f">

- ping `google` di Himmel
  
  <img width="536" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/6613e592-1f8c-47e8-aca9-b042ab171793">

- ping `google` di Richter
  
  <img width="552" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/04457a0c-64f3-4970-ad60-f02d1f8ac453">


## Soal 2
> Kalian diminta untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP.

### Script
Kami memasukkan script ini di `SchewerMountain`
```ruby
iptables -A INPUT -p tcp –dport 8080 -j ACCEPT
iptables -A INPUT -p tcp ! --dport 8080 -j DROP

iptables -A INPUT -p udp -j DROP
```

### Testing
- Buka port di `SchewerMountain`
  ```ruby
  nc -l -p 8080
  ```

  <img width="547" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/37eae595-4b18-410e-ae55-1c316d09af40">
  
- Testing di `Laubhills`
  ```ruby
  nc 192.211.0.134 8080
  ```

  <img width="245" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/c32a9afc-93c7-43f2-a92c-41d585c06683">


## Soal 2
> Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.

### Script
Kami masukkan script dibawah pada `Revolte` dan `Richter`
```ruby
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
```

### Testing
- Lakukan `ping 192.211.0.6` yangmana mengarah ke Richter
  
  <img width="399" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/be7f3283-d254-48e3-8745-46cc02fb60cb">

  <img width="404" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/7b4ae5ee-1319-4f45-8a29-01163d2a023c">

  <img width="403" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/52847d8e-692f-4b6e-9bcd-aa0412f773f7">

  <img width="731" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/fd913a59-dc27-4065-a26f-747c777e1f13">

- Lakukan `ping 192.211.0.2` yangmana mengarah ke Revolte

  <img width="509" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/98b36217-2dba-443f-a2e2-139e392bfd4c">

  <img width="426" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/00df70de-7686-4068-b747-c1f2ff6013c9">

  <img width="443" alt="image" src="https://github.com/mashitaad/Jarkom-Modul-5-E10-2023/assets/87978863/3bdbafc5-2074-4f09-a276-a18df66ee59c">
