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

### 3.1. Ulanish tezligi
Hisobotga o‘tkazib yozish:

8 Mbps = 1 MB/s (megabit/s dan megabayt/s ga)
100 MB/s = 819200 Kbps (megabayt/s dan kilobit/s ga)
1 Gbps = 1024 Mbps (gigabit/s dan megabit/s ga)

### 3.2. iperf3 utilitasi
ws1 va ws2 o‘rtasidagi ulanish tezligini o‘lchash
![img](rasim/3.1.png)
![img](rasim/3.2.png)


## 4-qism. Tarmoq devori

### 4.1. iptables utilitasi
ws1 va ws2 kompyuterlarida faylni yarating: /etc/firewall.sh, bu fayl firewallni imitatsiya qiladi:

Faylga ketma-ket quyidagi qoidalarni qo‘shish kerak:

ws1 da shunday strategiyani qo‘llash kerakki, bunda boshida taqiqlovchi qoida yoziladi, oxirida esa ruxsat beruvchi qoida yoziladi (bu 4 va 5-bandlarga tegishli).

ws2 da shunday strategiyani qo‘llash kerakki, bunda boshida ruxsat beruvchi qoida yoziladi, oxirida esa taqiqlovchi qoida yoziladi (bu 4 va 5-bandlarga tegishli).

Mashinalarda 22-port (SSH) va 80-port (HTTP) uchun kirishni ochish.

echo reply ni taqiqlash (ping qilish mumkin emas, ya'ni OUTPUT’da bloklash bo‘lishi kerak).

echo reply ga ruxsat berish (ping qilish mumkin).

![img](rasim/4.0.png)
![img](rasim/4.1.png)



Ikkala mashinada fayllarni quyidagi buyruqlar yordamida ishga tushiring:


`chmod +x /etc/firewall.sh` va `/etc/firewall.sh`
![img](rasim/4.2.png)
![img](rasim/4.3.png)



Farqi shundaki, buyruqlar ketma-ket bajariladi. Shuning uchun ws1 da ping taqiqlanadi (chunki ruxsat berish taqiqlashdan keyin qo‘yilgan), ws2 da esa ruxsat beriladi, chunki ruxsat berish birinchi o‘rinda.

### 4.2. nmap utilitasi
ping buyruği bilan ping qilinmayotgan mashinani toping, shundan keyin nmap utilitasi bilan mashina xostining ishga tushganini ko‘rsating. Tekshiruv: nmap chiqishida "Host is up" degan yozuv bo‘lishi kerak.

Hisobotga ping va nmap buyruqlarining chaqirilishi va chiqishini skrinshot qilib qo‘ying.
![img](rasim/4.4.png)
![img](rasim/4.5.png)
![img](rasim/4.6.png)



Virtual mashinalarning tasvirlarini saqlang.

![img](rasim/4.7.png)


## 5-qism. Statik tarmoq marshrutlash


### 5.1 Uchta ishchi stansiya (ws11, ws21, ws22) va ikkita router (r1, r2) ishga tushiring.

Rasmga muvofiq, mashinalar konfiguratsiyasini /etc/netplan/00-installer-config.yaml faylida sozlang. 
![img](rasim/4.0.png)
![img](rasim/4.1.png)
![img](rasim/4.2.png)
![img](rasim/4.3.png)
![img](rasim/4.4.png)

Tarmoq xizmatini qayta ishga tushiring. Agar xato bo‘lmasa, ip -4 a buyrug‘i bilan mashina manzili to‘g‘ri berilganini tekshiring.

Qayta ishga tushirish buyrug‘i:


`sudo systemctl restart NetworkManager`
![img](rasim/4.5.png)
![img](rasim/4.6.png)
![img](rasim/4.7.png)
![img](rasim/4.8.png)
![img](rasim/4.9.png)


Shuningdek, ws21 dan ws22 ni ping qiling. Xuddi shunday, ws11 dan r1 ni ping qiling. 
![img](rasim/4.10.png)
![img](rasim/4.12.png)
![img](rasim/4.13.png)
![img](rasim/4.14.png)


### 5.2. IP manzillarni yo‘naltirishni yoqish
IP manzillarni yo‘naltirishni yoqish uchun routerlarda quyidagi buyruqni bajaring:

`sysctl -w net.ipv4.ip_forward=1`
![img](rasim/4.15.png)
![img](rasim/4.16.png)


/etc/sysctl.conf faylini oching va quyidagi satrni qo‘shing:

`net.ipv4.ip_forward = 1`
![img](rasim/4.17.png)
![img](rasim/4.18.png)


### 5.3. Default marshrutni o‘rnatish
Ishchi stansiyalar uchun default marshrutni (gateway) sozlang. Buning uchun konfiguratsiya faylida router IP-manzilidan oldin default ni qo‘shing. 
![img](rasim/4.19.png)
![img](rasim/4.20.png)
![img](rasim/4.21.png)


ip r buyrug‘ini chaqirib, marshrutlash jadvaliga marshrut qo‘shilganini ko‘rsating. 
![img](rasim/4.22.png)
![img](rasim/4.23.png)
![img](rasim/4.24.png)


ws11 dan r2 routerni ping qiling va r2 da ping yetib borayotganini ko‘rsating. Buning uchun quyidagi buyruqdan foydalaning:


`tcpdump -tn -i eth1`
![img](rasim/4.25.png)
![img](rasim/4.26.png)


### 5.4. Statik marshrutlarni qo‘shish
Routerlar r1 va r2 ga konfiguratsiya faylida statik marshrutlar qo‘shing. 
![img](rasim/4.27.png)
![img](rasim/4.28.png)


ip r buyrug‘ini chaqirib, ikkala routerda marshrutlash jadvallarini ko‘rsating. 

![img](rasim/4.29.png)
![img](rasim/4.30.png)


ws11 da quyidagi buyruqlarni bajaring:

`ip r list 10.10.0.0`/[tarmoq maskasi]
`ip r list 0.0.0.0/0`
![img](rasim/4.31.png)

10.10.0.0/[tarmoq maskasi] uchun 0.0.0.0/0 dan boshqacha marshrut tanlanganini tushuntiring, garchi u default marshrutga kirsa ham:

Birinchisi netplandagi yozuv bilan berilgan va maskasi uzun bo‘lgani uchun tanlangan.

### 5.5. Routerlar ro‘yxatini tuzish
r1 da quyidagi buyruq bilan tarmoq trassasini tahlil qiling:

`tcpdump -tnv -i eth0`
![img](rasim/4.32.png)

traceroute utilitasi yordamida ws11 dan ws21 gacha bo‘lgan marshrutni aniqlang. 
![img](rasim/4.33.png)


### 5.6. ICMP protokolidan foydalanish
r1 da eth0 orqali o‘tadigan tarmoq trafigini quyidagi buyruq yordamida ushlang:


`tcpdump -n -i eth0 icmp`
ws11 dan mavjud bo‘lmagan IP-ga (masalan, 10.30.0.111) ping buyrug‘i yuboring:

bash
Copy code
ping -c 1 10.30.0.111
![img](rasim/4.34.png)
![img](rasim/4.35.png)


Virtual mashinalarning tasvirlarini saqlang.
![img](rasim/4.36.png)

## 6-qism. DHCP yordamida dinamik IP sozlamalari

r2 da `/etc/dhcp/dhcpd.conf` faylida DHCP xizmatining konfiguratsiyasini sozlang:

Default marshrutlash manzilini, DNS-server va ichki tarmoq manzilini ko‘rsating. 

![img](rasim/5.0.png)


`resolv.conf` faylida quyidagini kiriting:


`nameserver 8.8.8.8`
![img](rasim/5.1.png)


DHCP xizmatini qayta ishga tushirish uchun quyidagi buyrug‘ni bajaring:


`systemctl restart isc-dhcp-server`
ws21 mashinasini reboot buyrug‘i bilan qayta ishga tushiring va ip a buyrug‘i yordamida manzil olinganini ko‘rsating. Shuningdek, ws21 dan ws22 ni ping qiling. 
![img](rasim/5..png)
![img](rasim/5..png)
![img](rasim/5..png)


ws11 da MAC manzilini ko‘rsating, buning uchun /etc/netplan/00-installer-config.yaml fayliga quyidagilarni qo‘shing:


```bash
macaddress: 10:10:10:10:10:BA
dhcp4: true
```

![img](rasim/5..png)


r1 ni r2 ga o‘xshash qilib sozlang, lekin IP manzillarni MAC manziliga qattiq bog‘lab bering (ws11 uchun). Shu kabi testlarni o‘tkazing. ![img](rasim/5..png)


ws21 da IP manzilni yangilashni so‘rang. 
![img](rasim/5..png)


Virtual mashinalarning tasvirlarini saqlang. 
![img](rasim/5..png)


```bash
sudo dhclient -r   # IP-ni o‘chirish
sudo dhclient -v   # IP-ni qo‘shish
```
## 7-qism. NAT



## 8-qism. Qo'shimcha(Bonus). SSH tunnellariga kirish
