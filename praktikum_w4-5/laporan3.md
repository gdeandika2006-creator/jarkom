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
1.Buka Command Prompt, lalu masukan code berikut: nslookup www.mit.edu
![tampilanCMD](foto/cmd_nslookup%20www.mit.edu.png)
Fungsi: untuk mengetahui alamat IP dari domain
2.lalu masukan code ini juga: nslookup -type=NS mit.edu
![tampilanCMD](foto/CMD_nslookup%20-type=NS%20mit.edu.png)
Fungsi: untuk mengetahui DNS server (authoritative server)

