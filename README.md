# **LAPRES_MODUL 4_JARKOM** 
-----------------------------------
## **KELOMPOK T_16**
## Bagus Farhan Abdillah (05311840000016)
## I Gede Pradhana Indra Widnyana (05311840000031)

-----------------------------------
### SOAL
<img src="https://cdn.discordapp.com/attachments/777146787336290354/787584269308264478/Soal_Shift_Modul_4.png" width="800" height="400">

```
Catatan
1. Deadline hari Rabu, 9 Desember 2020 pukul 22.00
2. Soal shift dikerjakan pada Cisco Packet Tracer dan UML menggunakan metode
perhitungan CLASSLESS yang berbeda.
Keterangan: Bila di CPT menggunakan VLSM, maka di UML menggunakan CIDR
atau Sebaliknya
3. Jika tidak ada pemberitahuan revisi soal dari asisten, berarti semua soal BERSIFAT BENAR
dan DAPAT DIKERJAKAN.
4. CLOUD diberikan IP TUNTAP.
5. Server diberikan IP DMZ.
6. Berikan memori sebesar 64MB pada setiap UML.
7. Pembagian IP dan routing harus SE-EFISIEN MUNGKIN.
8. Pastikan semua UML dapat melakukan ping ke its.ac.id
```

# Cisco Packet Tracker menggunakan metode CIDR

- Topologi di CPT dan tentukan subnet.

<img src="https://cdn.discordapp.com/attachments/777146787336290354/787586455567597609/CIDR-Topologi.JPG" width="800" height="400">

- Lakukan penghitungan IP seperti dibawah ini.

<img src="https://cdn.discordapp.com/attachments/777146787336290354/787587891370131456/Pembagian_IP-CIDR.png" width="800" height="400">

- Kemudian masukan ke pengaturan CPT seperti biasa, lalu lakukan tes satu persatu apakah sudah bisa terhubung dengan benar.

- Setelah itu lakukan penghitungan IP Address yang dibutuhkan (Jumlah Host, Router, dan Server). Terdapat 5841 IP Address maka subnet yang dipakai untuk membuat pohon IP yaitu subnet 19.

<img src="https://cdn.discordapp.com/attachments/777146787336290354/787587817437790218/Pembagian_Subnet.JPG" width="400" height="500">

- Berikut merupakan tampilan topologi setelah berhasil melakukan konfigurasi pada CPT menggunakan metode CIDR

<img src="https://cdn.discordapp.com/attachments/777146787336290354/787677157538398228/1607866370559.jpg" width="800" height="400">

# UML menggunakan metode VLSM

- Kemudian lakukan konfigurasi UML seperti pada gambar dibawah ini. 

```
# Switch
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch5 > /dev/null < /dev/null &
uml_switch -unix switch13 > /dev/null < /dev/null &
uml_switch -unix switch15 > /dev/null < /dev/null &
uml_switch -unix switch16 > /dev/null < /dev/null &
uml_switch -unix switch17 > /dev/null < /dev/null &
uml_switch -unix switch18 > /dev/null < /dev/null &
uml_switch -unix switch19 > /dev/null < /dev/null &
uml_switch -unix switch20 > /dev/null < /dev/null &
uml_switch -unix switch21 > /dev/null < /dev/null &
uml_switch -unix switch22 > /dev/null < /dev/null &
uml_switch -unix switch25 > /dev/null < /dev/null &

# Router
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.70.88 eth1=daemon,,,switch0 eth2=daemon,,,switch1 eth3=daemon,,,switch1  mem=64M &
xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch19 eth1=daemon,,,switch0 eth2=daemon,,,switch2 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch16 eth1=daemon,,,switch15 eth2=daemon,,,switch2 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch25  eth1=daemon,,,switch22 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch3 eth1=daemon,,,switch4 eth2=daemon,,,switch21 eth3=switch22 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch17 eth1=daemon,,,switch4 eth2=daemon,,,switch18 mem=64M &
xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch20  eth1=daemon,,,switch17 mem=64M &

# Server
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch18 mem=64M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch13 mem=64M &

# Klien
xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch25 mem=64M &
xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch15 mem=64M &
xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch17 mem=64M &
xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch21 mem=64M &
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch19 mem=64M &
xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch20 mem=64M &
xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch1 mem=64M &
xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch16 mem=64M &
xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch16 mem=64M &
```

<img src="https://cdn.discordapp.com/attachments/777146787336290354/787677493939011614/1.1_setting_uml.png" width="800" height="400">

- Beriku merupakan gambar sukses melakukan konfigurasi pada UML

<img src="https://cdn.discordapp.com/attachments/777146787336290354/787684481468334100/1.2_berhasil_membuat_uml.png" width="800" height="400">

- Topologi VLSM

<img src="https://cdn.discordapp.com/attachments/777146787336290354/787677157538398228/1607866370559.jpg" width="800" height="400">

- Setelah itu lakukan penghitungan IP Address yang dibutuhkan (Jumlah Host, Router, dan Server). Terdapat 5841 IP Address maka subnet yang dipakai untuk membuat pohon IP yaitu subnet 19.

<img src="https://cdn.discordapp.com/attachments/777146787336290354/787587817437790218/Pembagian_Subnet.JPG" width="400" height="500">




