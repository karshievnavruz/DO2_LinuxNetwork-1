[1-qism. ipcalc asbobi](#1-qism-ipcalc-asbobi)
[2-qism. Ikki qurilma o'rtasida statik marshrutlash](#2-qism-ikki-qurilma-ortasida-statik-marshrutlash)
[3-qism. iperf3 utilitasi](#3-qism-iperf3-utilitasi)
[4-qism. Tarmoq devori](#4-qism-tarmoq-devori)
[5-qism. Statik tarmoq marshrutlash](#5-qism-statik-tarmoq-marshrutlash)
[6-qism. DHCP yordamida dinamik IP sozlamalari](#6-qism-dhcp-yordamida-dinamik-ip-sozlamalari)
[7-qism. NAT](#7-qism-nat)
[8-qism. Qo'shimcha(Bonus). SSH tunnellariga kirish](#8-qism-qoshimchabonus-ssh-tunnellariga-kirish)


## 1-qism. ipcalc asbobi.

### 1.1. Networks and Masks(Tarmoqlar va niqoblar)
`ipcalc o‘rnatish`

![img](rasim/1.0.png)

**Tarmoq manzili 192.167.38.54/13**


![img](rasim/1.1.png)

**255.255.255.0 ni prefiks va ikkilik shaklga o‘zgartirish:**

`255:`

![img](rasim/1.2.png)

`15:`

![img](rasim/1.3.png)

`11111111.11111111.11111111.11110000:`

![img](rasim/1.4.png)



**Minimum and maximum host in the network 122.167.38.4 with the following masks:**

`/8:`

![img](rasim/1.5.png)

`11111111.11111111.00000000.00000000:`

![img](rasim/1.4.png)

`255.255.254.0:`

![img](rasim/1.4.png)

`/4:`

![img](rasim/1.4.png)

### 1.2. localhost

To'g'ri, localhost faqat 127.0.0.1 dan 127.255.255.254 gacha bo'lgan IP manzillarni qabul qiladi.

Mumkin:

127.0.0.2
127.1.0.1
Mumkin emas:

194.34.23.100
128.0.0.1
Chunki localhost faqat 127.0.0.1 — 127.255.255.254 diapazonidagi manzillar uchun ishlaydi.

### 1.3. Network ranges and segments
Xususiy tarmoqlar quyidagi diapazonlarga kiradi:

10.0.0.0 — 10.255.255.255
100.64.0.0 — 100.127.255.255
172.16.0.0 — 172.31.255.255
192.168.0.0 — 192.168.255.255
Qolgan manzillar umumiy (jamoat) sifatida ishlatiladi.

Manzillarni tasniflash:

10.0.0.45 - xususiy
134.43.0.2 - jamoat
192.168.4.2 - xususiy
172.20.250.4 - xususiy
172.0.2.1 - jamoat
192.172.0.1 - jamoat
172.68.0.2 - jamoat
172.16.255.255 - xususiy
10.10.10.10 - xususiy
192.169.168.1 - jamoat
2. IP manzillarni 10.10.0.0/18 tarmog‘i uchun shlyuz sifatida ishlatish

Shlyuz manzili 10.10.0.1 — 10.10.63.254 diapazonida bo‘lishi kerak.

Tasnif:

10.0.0.1 - mos emas
10.10.0.2 - mos
10.10.10.10 - mos
10.10.100.1 - mos emas
10.10.1.255 - mos

## 2-qism. Ikki qurilma o'rtasida statik marshrutlash.

**Ikkita virtual mashina (keyingi o‘rinlarda -- ws1 va ws2)ni ishga tushirish**

![img](rasim/2.0.png)

ip a buyrug‘i yordamida mavjud tarmoq interfeyslarini ko‘rish
![img](rasim/2.1.png)

![img](rasim/2.2.png)

Ikkala mashinada ham ichki tarmoqqa mos keladigan tarmoq interfeysini tavsiflab, quyidagi IP manzillar va niqoblarni o‘rnating:

ws1 - 192.168.100.10, niqob /16
ws2 - 172.24.116.8, niqob /12

ws1:
netplan  o‘zgartirish

![img](rasim/2.3.png)

O'zgarishlarni saqlash

![img](rasim/2.4.png)

saqlangandan keyin

![img](rasim/2.5.png)

ws2:

netplan  o‘zgartirish

![img](rasim/2.6.png)

O'zgarishlarni saqlash

![img](rasim/2.7.png)

saqlangandan keyin

![img](rasim/2.8.png)

![img](rasim/2.9.png)


## 3-qism. iperf3 utilitasi




## 4-qism. Tarmoq devori



## 5-qism. Statik tarmoq marshrutlash



## 6-qism. DHCP yordamida dinamik IP sozlamalari



## 7-qism. NAT



## 8-qism. Qo'shimcha(Bonus). SSH tunnellariga kirish
