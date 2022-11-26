# Jarkom-Modul-4-E11-2022

<table>
<tr>
<th>Nama</th>
<th>NRP </th>
</tr>
<tr>
<td>Surya Abdillah</td>
<td>5025201229 </td>
</tr>
<tr>
<td>Muhammad Afdal Abdallah</td>
<td>5025201163 </td>
</tr>
<tr>
<td>Kadek Ari Dharmika</td>
<td>5025201239 </td>
</tr>
</table>

# Soal

![soal shift 4 1](https://user-images.githubusercontent.com/103357229/203995895-d9ce437d-91ad-48c3-8c6a-47ab90fbf29b.png)

> Keterangan:

- Prefix kelompok: 10.27
- Pada Cisco menggunakan metode classless VLSM
- Pada GNS3 menggunakan metode classless CIDR

# VLSM dengan Cisco

# CIDR dengan GNS3

## Topologi pada GNS3
> Untuk dapat menghubungkan 5 eth, maka ubah jumlah adapter menjadi 5 (Pada the Refinance)

![messageImage_1669447786411](https://user-images.githubusercontent.com/103357229/204077715-4949330d-3f24-4011-8157-b725bbf73c22.jpg)

## Subnetting

### Penggabungan subnet
> Penamaan subnet sama seperti VLSM

![Praktikum Modul 4 (6)](https://user-images.githubusercontent.com/103357229/204079015-d0a2faf2-d4a2-4f3d-b7a2-4791ba5b8a99.jpg)
![Praktikum Modul 4 (5)](https://user-images.githubusercontent.com/103357229/204079020-8429d0bd-db13-4515-b205-a39c7bbe0846.jpg)
![Praktikum Modul 4 (4)](https://user-images.githubusercontent.com/103357229/204079022-e7237620-4b9b-4224-8b75-f3ca84778a82.jpg)
![Praktikum Modul 4 (3)](https://user-images.githubusercontent.com/103357229/204079023-ee6b4777-71b4-422c-9b73-012b3cccd816.jpg)
![Praktikum Modul 4 (2)](https://user-images.githubusercontent.com/103357229/204079032-339256dd-0f97-4d7a-8b8c-f0be553ee5c6.jpg)
![Praktikum Modul 4 (1)](https://user-images.githubusercontent.com/103357229/204079033-48c7b0b0-ff72-4a90-915d-44895ec1ccf4.jpg)
![Praktikum Modul 4](https://user-images.githubusercontent.com/103357229/204079036-d70a5160-4b5b-4956-86c4-5f71318b0d8e.jpg)

### Pembagian IP
> Berdasar penggabungan subnet di atas, maka bisa didapatkan pohon CIDR sebagai berikut:

![E11_Praktikum Modul 4-CIDR](https://user-images.githubusercontent.com/103357229/204079200-57bb1c66-433d-473d-b9e0-6cb73fb7ef30.jpg)

> Daru pembagian IP tersebut bisa didapati tabel sebagai berikut:

| SUBNET | NID    | NETMASK | Broadcast Address |
| :---:   | :---: | :---: | :---: |
| A1 |  10.27.4.0  |  255.255.255.0  | 10.27.4.255 |
| A2 | 10.27.5.0 | 255.255.255.252 | 10.27.5.3 |
| A3 | 10.27.0.0 | 255.255.252.0 | 10.27.3.255 |
| A4 | 10.27.8.0 | 255.255.255.252 | 10.27.8.3 |
| A5 | 10.27.16.0 | 255.255.255.192 | 10.27.16.63 |
| A6 | 10.27.32.0 | 255.255.255.252 | 10.27.32.3 |
| A7 | 10.27.68.0 | 255.255.255.0 | 10.27.68.255 |
| A8 | 10.27.70.0 | 255.255.254.0 | 10.27.71.255 |
| A9 | 10.27.66.0 | 255.255.255.252 | 10.27.66.3 |
| A10 | 10.27.88.0 | 255.255.248.0 | 10.27.95.255 |
| A11 | 10.27.72.0 | 255.255.248.0 | 10.27.79.255 |
| A12 | 10.27.64.0 | 255.255.255.128 | 10.27.64.127 |
| A13 | 10.27.64.128 | 255.255.255.128 | 10.27.64.255 |
| A14 | 10.27.65.0 | 255.255.255.252 | 10.27.65.3 |
| A15 | 10.27.80.0 | 255.255.254.0 | 10.27.81.255 |
| A16 | 10.27.82.0 | 255.255.255.252 | 10.27.82.3 |
| A17 | 10.27.69.0 | 255.255.255.252 | 10.27.69.3 |
| A18 | 10.27.84.0 | 255.255.255.252 | 10.27.84.3 |

### Konfigurasi

#### ROUTER

> The Resonance

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 10.27.32.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 10.27.88.1
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 10.27.82.1
netmask 255.255.255.252

auto eth4
iface eth4 inet static
address 10.27.84.1
netmask 255.255.255.252
```

> The Order

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.27.32.2
netmask 255.255.255.252
gateway 10.27.32.1

auto eth1
iface eth1 inet static
address 10.27.16.1
netmask 255.255.255.192

auto eth2
iface eth2 inet static
address 10.27.8.1
netmask 255.255.255.252
```

> The Minister

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.27.8.2
netmask 255.255.255.252
gateway 10.27.8.1

auto eth1
iface eth1 inet static
address 10.27.0.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 10.27.5.1
netmask 255.255.255.252
```

> The Dauntless

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.27.5.2
netmask 255.255.255.252
gateway 10.27.5.1

auto eth1
iface eth1 inet static
address 10.27.4.1
netmask 255.255.255.0
```

> The Magical

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.27.82.2
netmask 255.255.255.252
gateway 10.27.130.1

auto eth1
iface eth1 inet static
address 10.27.80.1
netmask 255.255.254.0
```

> The Instrument

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.27.88.2
netmask 255.255.255.252
gateway 10.27.88.1

auto eth1
iface eth1 inet static
address 10.27.72.1
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 10.27.66.1
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 10.27.65.1
netmask 255.255.255.252
```

> The Profound

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.27.64.129
netmask 255.255.255.128

auto eth1
iface eth1 inet static
address 10.27.64.1
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 10.27.65.2
netmask 255.255.255.252
gateway 10.27.65.1
```

> Teh FireFist

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.27.66.2
netmask 255.255.255.252
gateway 10.27.66.1

auto eth1
iface eth1 inet static
address 10.27.68.1
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 10.27.70.1
netmask 255.255.254.0
```

> The Queen

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.27.68.3
netmask 255.255.255.0
gateway 10.27.68.1

auto eth1
iface eth1 inet static
address 10.27.69.1
netmask 255.255.255.252
```

#### PC

> Ashaf

```
auto eth0
iface eth0 inet static
address 10.27.16.2
netmask 255.255.255.192
gateway 10.27.16.1
```

> Guidae

```
auto eth0
iface eth0 inet static
address 10.27.0.2
netmask 255.255.252.0
gateway 10.27.0.1
```

> Phanora

```
auto eth0
iface eth0 inet static
address 10.27.4.2
netmask 255.255.255.0
gateway 10.27.4.1
```

> Johan

```
auto eth0
iface eth0 inet static
address 10.27.4.3
netmask 255.255.255.0
gateway 10.27.4.1
```

> Corvekt

```
auto eth0
iface eth0 inet static
address 10.27.80.2
netmask 255.255.254.0
gateway 10.27.80.1
```

> Haines

```
auto eth0
iface eth0 inet static
address 10.27.80.3
netmask 255.255.254.0
gateway 10.27.80.1
```

> MattCugat

```
auto eth0
iface eth0 inet static
address 10.27.72.2
netmask 255.255.255.128
gateway 10.27.72.1
```

> Spendrow

```
auto eth0
iface eth0 inet static
address 10.27.64.130
netmask 255.255.255.128
gateway 10.27.64.129
```

> Helga

```
auto eth0
iface eth0 inet static
address 10.27.64.2
netmask 255.255.255.128
gateway 10.27.64.1
```

> Oakleave

```
auto eth0
iface eth0 inet static
address 10.27.70.2
netmask 255.255.254.0
gateway 10.27.70.1
```

> Keith

```
auto eth0
iface eth0 inet static
address 10.27.68.2
netmask 255.255.255.0
gateway 10.27.68.1
```

#### SERVER

> The Beast

```
auto eth0
iface eth0 inet static
address 10.27.84.2
netmask 255.255.255.252
gateway 10.27.84.1
```

> The Witch

```
auto eth0
iface eth0 inet static
address 10.27.69.2
netmask 255.255.255.252
gateway 10.27.69.1
```

## Routing

> Melakukan routing pada setiap router untuk menuju subnet-subnet. NB: file subnet terdapat pada folder `root` pada GNS3 project yang terlampir di github

### The Resonance

```
route add -net 10.27.16.0 netmask 255.255.255.192 gw 10.27.32.2
route add -net 10.27.8.0 netmask 255.255.255.252 gw 10.27.32.2
route add -net 10.27.0.0 netmask 255.255.252.0 gw 10.27.32.2
route add -net 10.27.5.0 netmask 255.255.255.252 gw 10.27.32.2
route add -net 10.27.4.0 netmask 255.255.255.0 gw 10.27.32.2

route add -net 10.27.80.0 netmask 255.255.254.0 gw 10.27.82.2

route add -net 10.27.72.0 netmask 255.255.248.0 gw 10.27.88.2
route add -net 10.27.65.0 netmask 255.255.255.252 gw 10.27.88.2
route add -net 10.27.64.0 netmask 255.255.255.128 gw 10.27.88.2
route add -net 10.27.64.128 netmask 255.255.255.128 gw 10.27.88.2

route add -net 10.27.66.0 netmask 255.255.255.252 gw 10.27.88.2
route add -net 10.27.70.0 netmask 255.255.254.0 gw 10.27.88.2
route add -net 10.27.69.0 netmask 255.255.255.252 gw 10.27.88.2
route add -net 10.27.68.0 netmask 255.255.255.0 gw 10.27.88.2
```

### The Order

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.27.32.1

route add -net 10.27.0.0 netmask 255.255.252.0 gw 10.27.8.2
route add -net 10.27.5.0 netmask 255.255.255.252 gw 10.27.8.2
route add -net 10.27.4.0 netmask 255.255.255.0 gw 10.27.8.2
```

### The Minister

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.27.8.1
route add -net 10.27.4.0 netmask 255.255.255.0 gw 10.27.5.2
```

### The Dauntless

```
route add 0.0.0.0 netmask 0.0.0.0 gw 10.27.5.1
```

### The Magical

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.27.82.1
```

### The Instrument

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.27.88.1

route add -net 10.27.64.0 netmask 255.255.255.128 gw 10.27.65.2
route add -net 10.27.64.128 netmask 255.255.255.128 gw 10.27.65.2

route add -net 10.27.68.0 netmask 255.255.255.0 gw 10.27.66.2
route add -net 10.27.70.0 netmask 255.255.254.0 gw 10.27.66.2
route add -net 10.27.69.0 netmask 255.255.255.252 gw 10.27.66.2
```

### The Profound

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.27.65.1
```

### The FireFist

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.27.66.1
route add -net 10.27.69.0 netmask 255.255.255.252 gw 10.27.68.3
```

### The Queen

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.27.68.1
```

## Testing 

> Testing dapat dilakukan dengan melakukan ping terhadap IP address subnet / node lain

### The Witch ke Phanora

![image](https://user-images.githubusercontent.com/103357229/204080684-27f14aa5-3b24-4f8f-b305-b3b762506a92.png)

### The Witch ke The Beast

![image](https://user-images.githubusercontent.com/103357229/204080716-07139e84-9d21-4d04-bae8-0e0dc7a3d21e.png)

### Guidae ke Helga

![image](https://user-images.githubusercontent.com/103357229/204080745-09da2ad1-4c25-4170-abb4-3191c011fa22.png)

### Phanora ke Spendrow

![image](https://user-images.githubusercontent.com/103357229/204080778-79045845-8cb4-4869-a23e-33fb9a24b81d.png)


### The Queen ke the Dauntless

![image](https://user-images.githubusercontent.com/103357229/204080819-a72eeb01-cbe1-49d3-92bf-17945c46492c.png)

### The Minister ke The Magical

![image](https://user-images.githubusercontent.com/103357229/204080851-901e61ee-64c9-4adc-880e-46ab5f824a79.png)

### The Resonance ke The Witch

![image](https://user-images.githubusercontent.com/103357229/204080887-9deb78fb-9bf3-4b52-b815-cb71ec7229b7.png)

# Kendala yang dialami

- Pembuatan tree untuk CIDR yang terhitung lebih susah dari pada VLSM
- Kesalahan dalam pemilihan IP hasil pecahan sehingga bertabrakan

# Kontribusi tim

- Pengerjaan dilakukan bersama-sama di tempat dan device yang sama
