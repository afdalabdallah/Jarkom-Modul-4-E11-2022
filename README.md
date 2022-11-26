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


## Pembuatan Topologi 

> Pembuatan topologi dibuat sesuai dengan arahan modul, perbedaan hanya ada pada port tambahan pada beberapa router. sebagai contoh, router `the Resonance` memerlukan 3 port tambahan. Hanya ada pilihan 1, 2, 4, dst port, maka kita tambahkan 4 port dengan `NM-4E`. Sesuai dengan gambar berikut:

![image](https://user-images.githubusercontent.com/103357229/204108443-c68ad654-e614-4439-814a-136ecbe03c24.png)

> Hasil topologi sebagai berikut:

<img width="571" alt="image" src="https://user-images.githubusercontent.com/103357229/204108374-890ad649-d51d-4911-a8ea-fc4c5570dd3e.png">

## Subnetting

### Pembagian IP

![E11_Praktikum Modul 4-VLSM](https://user-images.githubusercontent.com/90978855/204093910-a5d75d57-32df-4dfc-95da-a2e90c10fc15.jpg)


> Dari pembagian IP tersebut bisa didapati tabel sebagai berikut:

| SUBNET | NID    | NETMASK | Broadcast Address |
| :---:   | :---: | :---: | :---: |
| A1 |  10.27.2.0 |  255.255.255.0  | 10.27.2.255 |
| A2 | 10.27.0.0 | 255.255.255.252 | 10.27.0.3 |
| A3 | 10.27.8.0 | 255.255.252.0 | 10.27.11.255 |
| A4 | 10.27.0.4 | 255.255.255.252 | 10.27.0.7 |
| A5 | 10.27.0.64 | 255.255.255.192 | 10.27.0.127 |
| A6 | 10.27.0.8 | 255.255.255.252 | 10.27.0.11 |
| A7 | 10.27.3.0 | 255.255.255.0 | 10.27.3.255 |
| A8 | 10.27.4.0 | 255.255.254.0 | 10.27.5.255 |
| A9 | 10.27.0.12 | 255.255.255.252 | 10.27.0.15 |
| A10 | 10.27.0.16 | 255.255.255.252 | 10.27.0.19 |
| A11 | 10.27.0.128 | 255.255.255.128 | 10.27.0.255 |
| A12 | 10.27.1.0 | 255.255.255.128 | 10.27.1.127 |
| A13 | 10.27.0.20 | 255.255.255.128 | 10.27.1.255 |
| A14 | 10.27.65.0 | 255.255.255.252 | 10.27.0.23 |
| A15 | 10.27.6.0 | 255.255.254.0 | 10.27.7.255 |
| A16 | 10.27.0.24 | 255.255.255.252 | 10.27.0.27 |
| A17 | 10.27.0.28 | 255.255.255.252 | 10.27.0.31 |
| A18 | 10.27.0.32 | 255.255.255.252 | 10.27.0.35 |

### Konfigurasi

> dari tabel di atas, maka bisa kita implementasikan pada router, PC, dan server yang ada. Sebagai contoh berikut:

#### Konfigurasi untuk A6 pada router

> Pada eth1/0 The Refonance mengarah pada subnet A6 yang memiliki NID `10.27.0.8`. Sehingga IP untuk the Refonance menuju A6 berisi `10.27.0.9`. Pada FastEth0/0 the Order mengarah menuju A6, yakni `10.27.0.8`, sedangkan `10.27.0.9` telah digunakan oleh the Refonance, sehingga kita pada the Order kiat dapat menggunakan `10.27.0.10`

![image](https://user-images.githubusercontent.com/103357229/204108565-ff306bf6-3d9d-45c4-b4d3-07fc9303b8d5.png)

![image](https://user-images.githubusercontent.com/103357229/204108748-484ab8a0-6a28-42b0-811f-f73bb8ff7729.png)

> Pada PC dan Server dilakukan konfigurasi dengan cara yang sama, sebagai contoh pada server `the Beast` dan PC `Phanora` dan `Johan`

#### server `the Beast`

> the Beast terletak pada subnet A18, dimana NID nya adalah `10.27.0.32`, kita akan menggunakan address `10.27.0.34` untuk the beast. Sedangkan, pada router the Refonance kita gunakan address `10.27.0.33` (untuk FA0/1). Sehingga, gateway pada the Beast  menjadi `10.27.0.33` juga.

![image](https://user-images.githubusercontent.com/103357229/204108906-03c4f48b-0aee-427b-8ed0-39b018e076fd.png)

#### PC `Phanora` dan `Johan`

> Pada subnet A1, terdapat 2 PC sekaligus, yakni Phanora dan Johan. Kita dapat melakukan konfigurasi dengan membedakan IP address untuk masing-masing PC, tetapi dengan gateway yang sama, yakni FA0/1 dari The Dauntless. NID untuk A1 adalah 10.27.2.0, sehingga pada FA0/1 the Dauntless diisi `10.27.2.1` dan pada Phanora diisi `10.27.2.2` dan pada PC Johan kita isi `10.27.2.3`. Sesuai dengan hasil screenshot berikut:

![image](https://user-images.githubusercontent.com/103357229/204109057-563b70ab-676d-41c0-bab8-d4752d00ac92.png)

![image](https://user-images.githubusercontent.com/103357229/204109060-412c9a3f-800b-470c-9ec9-30cee564c47f.png)

![image](https://user-images.githubusercontent.com/103357229/204109064-39e03d65-f00c-4c6d-a1bd-bca336cf6777.png)

> Lakukan konfigurasi pada node-node lainnya sesuai dengan tabel pembagian IP yang sudah dibuat

## Routing

> Routing dilakukan dengan menambahkan static routing pada setiap router yang ada

### the Refonance

```
10.27.0.64/26 via 10.27.0.10
10.27.0.0/30 via 10.27.0.10
10.27.8.0/24 via 10.27.0.10
10.27.2.0/24 via 10.27.0.10
10.27.0.4/30 via 10.27.0.10
10.27.0.24/30 via 10.27.0.26
10.27.6.0/23 via 10.27.0.26
10.27.0.128/25 via 10.27.0.18
10.27.0.20/30 via 10.27.0.18
10.27.1.128/25 via 10.27.0.18
10.27.1.0/25 via 10.27.0.18
10.27.0.12/30 via 10.27.0.18
10.27.4.0/23 via 10.27.0.18
10.27.3.0/24 via 10.27.0.18
10.27.0.28/30 via 10.27.0.18
```

### the Magical

```
0.0.0.0/0 via 10.27.0.25
```

### the Order

```
0.0.0.0/0 via 10.27.0.9
10.27.8.0/22 via 10.27.0.6
10.27.0.0/30 via 10.27.0.6
10.27.2.0/24 via 10.27.0.6
```

### the Minister

```
0.0.0.0/0 via 10.27.0.5
10.27.2.0/24 via 10.27.0.2
```

### the Dauntless

```
0.0.0.0/0 via 10.27.0.1
```

### the Instrument

```
0.0.0.0/0 via 10.27.0.17
10.27.1.128/25 via 10.27.0.22
10.27.1.0/25 via 10.27.0.22
10.27.4.0/23 via 10.27.0.14
10.27.3.0/24 via 10.27.0.14
10.27.0.28/30 via 10.27.0.14
```

### the Profound

```
0.0.0.0/0 via 10.27.0.21
```

### the FireFist

```
0.0.0.0/0 via 10.27.0.13
10.27.0.28/30 via 10.27.3.3
```

### the Queen

```
0.0.0.0/0 via 10.27.3.1
```

## Testing

> Testing dapat dilakukan dengan melakukan message dari node satu ke node lainnya. Berikut hasil tangkap dari beberapa percobaan yang dilakukan. (Apabila pada file PKT yang tertaut masih menghasilkan failed, maka harap tunggu dan bisa dicoba lagi)

![image](https://user-images.githubusercontent.com/103357229/204109437-d9b00a32-c1de-4b71-a138-4509df3a1050.png)

![image](https://user-images.githubusercontent.com/103357229/204109476-ee188f07-d83d-477a-ba99-95e9b1968f7b.png)

![image](https://user-images.githubusercontent.com/103357229/204109502-58d2814f-820e-4b1c-87b4-30adea6b1829.png)


# CIDR dengan GNS3

## Topologi pada GNS3
> Untuk dapat menghubungkan 5 eth, maka ubah jumlah adapter menjadi 5 (Pada the Refinance)

![messageImage_1669447786411](https://user-images.githubusercontent.com/103357229/204077715-4949330d-3f24-4011-8157-b725bbf73c22.jpg)

## Subnetting

### Pembagian Subnet Topologi
![Untitled](https://user-images.githubusercontent.com/90848018/204092102-b4dbe396-2205-4a04-a68d-8e823b20555f.jpg)

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
