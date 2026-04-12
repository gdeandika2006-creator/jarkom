# Laporan Praktikum Minggu 1

Nama       : Gde Andika Ananta Putra  
NIM        : 103072400014  
Kelas      : IF-04-05  
Mata Kuliah: Jaringan Komputer  
__________________________________________


# MODUL 4 (DNS)
Domain Name System (DNS) memiliki peran penting dalam infrastruktur internet, yaitu untuk mentranslasikan nama domain menjadi alamat IP. Pada modul ini, kita mempelajari bagaimana DNS bekerja dari sisi klien, yaitu dengan cara mengirim permintaan ke server DNS dan menerima respon balik.

## MODUL 4.2 Nslookup
Nslookup adalah tool yang digunakan untuk mencari informasi DNS, seperti mengetahui alamat IP dari sebuah domain maupun sebaliknya. Tool ini sering digunakan untuk troubleshooting jaringan.

### Langkah - Langkah Percobaan

1.Buka Command Prompt, lalu masukan command berikut: nslookup www.mit.edu
![tampilanCMD](foto/cmd_nslookup%20www.mit.edu.png)
Fungsi: untuk mengetahui alamat IP dari domain


2.lalu masukan command ini juga: nslookup -type=NS mit.edu

![tampilanCMD](foto/CMD_nslookup%20-type=NS%20mit.edu.png)

Fungsi: untuk mengetahui DNS server (authoritative server)

3.lalu masukan lagi command nslookup "www.aiit.or.kr bitsy.mit.edu" ini di cmd
![tampilanCMD](foto/CMDwww.aiit.or.kr%20bitsy.mit.edu.png)
Fungsi: melakukan query ke DNS tertentu

## Pertanyaan

1.Mencari IP server web di Asia
- Perintah : nslookup www.u-tokyo.ac.jp
- Domain : www.u-tokyo.ac.jp
- Alamat IP : 210.152.243.234
![tampilanCMD](foto/CMDnslookup%20www.u-tokyo.ac.jp.png)
command "nslookup www.u-tokyo.ac.jp" ini mengirim request ke DNS server untuk menerjemahkan domain menjadi IP address

2.Mencari DNS otoritatif universitas di Eropa
- Perintah : nslookup -type=MX gmail.com dns0.cam.ac.uk
![tampilanCMD](foto/CMDnslookup%20-type=NS%20cam.ac.uk.png)
command "nslookup -type=NS cam.ac.uk" ini untuk Menampilkan server DNS yang bertanggung jawab terhadap domain tersebut.

3.Mencari mail server
![tampilanCMD](foto/CMDnslookup%20-type=MX%20gmail.com%20dns0.cam.ac.uk.png)
command "nslookup -type=MX gmail.com dns0.cam.ac.uk" ini untuk Menampilkan mail server (MX record) dari domain tertentu melalui DNS tertentu.

## Modul 4.3 Ipconfig
Ipconfig adalah perintah pada Windows untuk melihat dan mengelola konfigurasi jaringan seperti IP address, DNS, dan gateway.

### Langkah - Langkah Percobaan
1.Sama seperti cara di awal buka cmd lalu masukan command:ipconfig /all
![tampilanCMD](foto/CMDipconfig%20all.png)
fungsi:Menampilkan IP address, DNS server, dan informasi jaringan lainnya.

2.lalu masukan command "ipconfig /all > savefile.txt" ini jika ingin save semua hasil yang tadi kita sudah coba
![tampilanCMD](foto/CMDipconfig%20all%20%20savefile.txt.png)

3.lalu hasil yang save tadi akan masuk ke path "C:\Users\gdean" untuk di leptop saya
![tampilanExplorer](foto/pathCUsersgdean.png)

4.lalu masukan command "ipconfig /displaydns" untuk Menampilkan cache DNS
![tampilanCMD](foto/CMDipconfig%20displaydns.png)

5.lalu jika ingin menghapus chache bisa menggunakan command "ipconfig /flushdns"
![tampilanCMD](foto/CMDipconfig%20flushdns.png)

## Modul 4.4 Tracing DNS dengan Wireshark
Tracing DNS digunakan untuk melihat proses request dan response DNS menggunakan Wireshark.

## A. Analisis DNS Request dan Response pada Akses Website (www.ietf.org)

### Langkah - Langkah Percobaan
1.buka cmd dan masukan command "ipconfig" jika ingin melihat IPv4 address 
![tampilanCMD](foto/CMDipconfig.png)

2.setelah mendapatkan IPv4 address masing-masing lalu buka wireshark dan click wifi kemudian masukkan di filter ip.addr == 192.168.1.4 (sesuai IPv4 masing-masing)
![tampilanwireshark](foto/WiresharkIPaddres.png)

3.lalu masuk ke web "https://www.ietf.org/" 
![tampilanweb](foto/webhttpswww.ietf.org.png)

4.kemudian masuk kembali ke wireshark dan masukkan di filter dengan " ip.addr == 192.168.1.4 && dns.qry.name contains "ietf" "
![tampilanwireshark](foto/wiresharkhttpswww.ietf.org.png)

### Pertanyaan

1.Apakah DNS menggunakan UDP atau TCP?

![tampilanwireshark](foto/dnsudp.png)

Jawab: Dns menggunakan UDP

2.Port tujuan pada DNS request & port sumber pada DNS response 

Jawab:

-DNS REQUEST -> Source Port (client): 63768 & Destination Port (server): 53

DNS RESPONSE -> Source Port (server): 53 & Destination Port (client): 63768 

![tampilanwireshark](foto/dnsudp.png)

## Analisis DNS Menggunakan Perintah nslookup (www.mit.edu)

### Langkah - Langkah Percobaan

1.buka cmd lalu masukan command nslookup www.mit.edu
![tampilanCMD](foto/CMDhttpswww.mit.edu.png)

2.kemudian masuk kembali ke wireshark dan masukkan di filter dengan DNS, lalu ambil data dari Standard query (request) dan Standard query response dari www.mit.edu
![tampilanwireshark](foto/wiresharkhttpswww.mit.edu.png)

### Pertanyaan

1.Port tujuan request dan port sumber dari response Jawab:

- DNS REQ -> port 53
![tampilanwireshark](foto/dnsreq.png)
- DNS RESPONSE ->
![tampilanwireshark](foto/wiresharkresponse.png)

2.Ke  alamat  IP  manakah  pesan  permintaan  DNS  dikirimkan?
jawab:
Request DNS dikirim ke alamat IP 2001:448a:c0f0:11ff:66fd:5060:b249:bd9f, alamat tersebut merupakan alamat lokal (IPv6) yang digunakan sebagai DNS server dalam jaringan
![tampilanwireshark](foto/wiresharkipaddresdns.png)

3.Periksa pesan permintaan DNS. Apa ”jenis” atau ”type” dari pesan tersebut? Apakah pesan tersebut mengandung ”jawaban” atau ”answers”?
Jawab:
Tipe DNS request adalah A (Address Record). Pesan ini tidak mengandung jawaban karena hanya berupa permintaan 
![tampilanwireshark](foto/dnsreq.png)

4.Periksa pesan balasan DNS. Berapa banyak ”jawaban” atau “answers” yang terdapat di dalamnya. Apa saja isi yang terkandung dalam setiap jawaban tersebut? 
jawab:
Terdapat 3 jawaban
- Jawaban pertama menunjukkan bahwa domain www.mit.edu merupakan alias (CNAME) ke www.mit.edu.edgekey.net, yang berarti domain utama diarahkan ke domain lain.
- Jawaban kedua menunjukkan alias lanjutan, yaitu www.mit.edu.edgekey.net kembali diarahkan (CNAME) ke e9566.dscb.akamaiedge.net.
- Jawaban ketiga merupakan hasil akhir berupa A record, yaitu alamat IP 23.217.163.122, yang menjadi tujuan sebenarnya dari proses resolusi domain tersebut. 
![tampilanwireshark](foto/wiresharkjawaban.png)

## Analisis DNS Record NS Menggunakan nslookup (mit.edu)
1.buka cmd lalu masukan command nslookup -type=NS mit.edu 

![tampilanCMD](foto/CMD_nslookup%20-type=NS%20mit.edu.png)

2.kemudian masuk kembali ke wireshark dan masukkan di filter dengan DNS, lalu ambil data dari Standard query (request) dari www.mit.edu
![tampilanwireshark](foto/nsmitedu.png)

### Langkah - Langkah Percobaan

1.Ke  alamat  IP  manakah  pesan  permintaan  DNS  dikirimkan?
Jawab: Request DNS dikirim ke alamat IP 2001:4489: yang merupakan DNS default pada jaringan
![tampilanwireshark](foto/nsmitedu.png)

2.apakah pesan tersebut mengandung ”jawaban” atau ”answers”?  
Jawab: Tipe DNS request adalah NS. Pesan ini tidak mengandung jawaban karena hanya berupa permintaan 
![tampilanwireshark](foto/nsmitedu.png)

3.Apakah pesan balasan ini juga memberikan alamat IP untuk server MIT tersebut? 
jawab: Pada DNS response, diperoleh beberapa nama server MIT. Pesan balasan ini umumnya hanya menampilkan nama server (NS record), dan tidak alamat IP secara langsung pada bagian answers 
![tampilanwireshark](foto/nsmitjawaban.png)

## Analisis DNS Menggunakan Server Tertentu, misal (www.aiit.or.kr bitsy.mit.edu)
1.buka cmd lalu masukan command nslookup www.aiit.or.kr bitsy.mit.edu 
![tampilanCMD](foto/CMDwww.aiit.or.kr%20bitsy.mit.edu.png)

2.kemudian masuk kembali ke wireshark dan masukkan di filter dengan DNS, lalu ambil data dari Standard query (request) dari nslookup www.aiit.or.kr bitsy.mit.edu 
![tampilanwireshark](foto/wiresharkwww.aiit.or.kr%20bitsy.mit.edu%20.png)

### Langkah - Langkah Percobaan
1.Apakah  alamat  IP  tersebut merupakan default alamat IP server DNS lokal Anda? 
Jawab: Pesan permintaan DNS dikirim ke alamat IP 18.0.72.3. Alamat tersebut merupakan server bitsy.mit.edu yang ditentukan secara manual pada perintah nslookup, sehingga bukan merupakan DNS server lokal 
![tampilanwireshark](foto/wiresharkwww.aiit.or.kr%20bitsy.mit.edu%20.png)

2.Apakah pesan tersebut mengandung ”jawaban” atau ”answers”? 
Jawab: Type dan answers request Jawab: Tipe DNS request adalah A (Address Record). Pesan ini tidak mengandung jawaban karena hanya berupa permintaan 
![tampilanwireshark](foto/wiresharkwww.aiit.or.kr%20bitsy.mit.edu%20.png)

3.Periksa pesan balasan DNS. Berapa banyak ”jawaban” atau “answers” yang terdapat di 
dalamnya. Apa saja isi yang terkandung dalam setiap jawaban tersebut?
jawab: tidak ada pesan balasan DNS karena DNS request timeout sehingga server bitsy.mit.edu tidak memberikan respon terhadap query yang dikirimkan. Akibatnya, tidak terdapat answers yang dapat dianalisis 
![tampilanCMD](foto/CMDwww.aiit.or.kr%20bitsy.mit.edu.png)

# MODUL UDP 5
UDP (User Datagram Protocol) adalah salah satu protokol pada layer transport dalam model TCP/IP yang digunakan untuk mengirimkan data tanpa koneksi (connectionless). Artinya, UDP tidak melakukan proses pembentukan koneksi terlebih dahulu sebelum mengirim data.

### Langkah - Langkah Percobaan
1.Download file http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip
2.Extract file dan cari file http-ethereal-trace-5
3.lalu drag n drop file http-ethereal-trace-5 ke wireshark yang sudah di stop mengambil data
4.lalu lakukan filter UDP dan pilih 1 paket UDP (bebas)
![tampilanwireshark](foto/wiresharkUDP.png)

### pertanyaan

1.berapa banyak “field” yang terdapat pada header UDP?
jawab: terdapat 4 field yaitu Source Port, Destination Port, Length, Checksum
![tampilanwireshark](foto/wiresharkUDP.png)

2.Berapa panjang (dalam satuan byte) masing-masing “field” yang terdapat pada header UDP? 
jawab:
Panjang tiap field Bedasarkan teori UDP :

- Source Port = 2 byte
- Destination Port = 2 byte
- Length = 2 byte
- Checksum = 2 byte Maka total = 8 byte

3.Nilai yang tertera pada ”Length” menyatakan nilai apa?
![tampilanwireshark](foto/wiresharkUDP.png)
jawab:
Nilai Length (59) pada protokol UDP menunjukkan keseluruhan panjang segmen UDP yang terdiri dari header sebesar 8 byte dan data/payload. Untuk mengetahui ukuran data yang dikirim, maka panjang total dikurangi ukuran header, yaitu 59 - 8 = 51 byte. Dengan demikian, ukuran data yang dibawa oleh paket UDP tersebut adalah 51 byte, dan hasil ini sesuai dengan informasi yang ditampilkan pada Wireshark yaitu UDP payload (51 byte).

4.Berapa  jumlah  maksimum  byte  yang  dapat  disertakan  dalam  payload  UDP?
Jawab:Header UDP memiliki ukuran tetap sebesar 8 byte, sedangkan ukuran maksimum paket IP adalah 65535 byte. Dalam paket IPv4, header IP standar berukuran 20 byte. Oleh karena itu, kapasitas maksimum data (payload) UDP dapat dihitung dengan mengurangi ukuran total IP dengan header IP dan header UDP: 65535 - 20 - 8 = 65507 byte. Jadi, ukuran maksimum payload yang dapat dikirim melalui UDP adalah 65507 byte.

5.Berapa nomor port terbesar yang dapat menjadi port sumber?
Jawab: Nomor port terbesar yang dapat digunakan pada protokol UDP adalah 65535. Hal ini karena field source port dan destination port pada header UDP masing-masing berukuran 16 bit. Dengan panjang 16 bit, jumlah nilai maksimum yang dapat direpresentasikan adalah 2¹⁶ - 1 = 65535. Oleh sebab itu, rentang nomor port UDP adalah 0 sampai 65535.

6.Berapa nomor protokol untuk UDP? 
![tampilanwireshark](foto/wiresharkprotocol.png)
jawab:Nomor protokol UDP adalah 17 (desimal) atau 0x11 (heksadesimal)

7.Periksa pasangan paket UDP di mana host Anda mengirimkan paket UDP pertama dan paket 
UDP kedua merupakan balasan dari paket UDP yang pertama
![tampilanwireshark](foto/wiresharkUDP.png)
Jawab:

- REQUEST -> Source Port : 4336 & Destination Port : 161
- RESPONSE -> Source Port : 161 & Destination Port : 4336
- Nomor port pada paket balasan merupakan kebalikan dari paket permintaan, di mana port sumber dan tujuan saling bertukar
