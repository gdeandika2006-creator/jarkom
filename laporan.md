# Laporan Praktikum Minggu 1

Nama       : Gde Andika Ananta Putra  
NIM        : 103072400014  
Kelas      : IF-04-05  
Mata Kuliah: Jaringan Komputer  
__________________________________________

## Instalasi Wireshark (Modul 1)

### Cara singkat pasang Wireshark:
1. Buka https://www.wireshark.org/download.html
2. Pilih installer yang cocok untuk OS masing-masing, lalu download (pakai versi terbaru)
3. Jalankan file installer yang sudah di-download
4. Ikuti step instalasi sampai selesai (pilih lokasi instalasi kalau diminta)

### Lampiran instalasi
- Download page  
![Wireshark Website](asset/image/wiresharkWebsite.png)
- Installation Part 1  
![install setup part 1](asset/image/installationSetupPart1.png)
- Installation Part 2  
![install setup part 2](asset/image/installationSetupPart2.png)
- Installation Part 3  
![install setup part 3](asset/image/installationSetupPart3.png)
- Installation Part 4  
![install setup part 4](asset/image/installationSetupPart4.png)
- Installation Part 5  
![install setup part 5](asset/image/installationSetupPart5.png)
- Installation Part 6  
![install setup part 6](asset/image/installationSetupPart6.png)
- Installation Part 7  
![install setup part 7](asset/image/installationSetupPart7.png)
- Installation Part 8  
![install setup part 8](asset/image/installationSetupPart8.png)
- Installation Part 9  
![install setup part 9](asset/image/installationSetupPart9.png)
- Installation Part 10  
![install setup part 10](asset/image/installationSetupPart10.png)
- Installation Done  
![install setup done](asset/image/installationSetupDone.png)

## Tugas Praktikum Minggu 1 (Modul 2)

### Cara cek HTTP request/response (basic):
1. Buka Wireshark
2. Pilih interface yang mau dipakai untuk capture (mis. Wi‑Fi). Kalau pakai VPN, matikan dulu
3. Buka link ini di browser: http://gaia.cs.umass.edu/wireshark-labs/INTRO-wireshark-file1.html (pakai HTTP)
4. Halaman akan menampilkan teks singkat: "Congratulations! You've downloaded the first Wireshark lab file!"
5. Di Wireshark, ketik `http` di kolom filter
6. Cari paket yang bertipe `(text/html)`
7. Buka bagian "Line-based text data" untuk lihat isi HTML:

Kalau mau berhenti merekam, klik tombol stop capture lalu tutup file capture.

### Lampiran hasil
 - Tampilan Wireshark
 ![Tampilan Wireshark](asset/image/tampilanWireshark.png)
 - Capture dari Wi‑Fi
 ![Tampilan Capture from Wi-Fi](asset/image/tampilanCaptureFromWifi.png)
 - Tampilan browser pada halaman contoh
 ![Tampilan Browser pada link html](asset/image/tampilanBrowserPadaLinkHtml.png)
 - Capture Wi‑Fi dengan filter HTTP
 ![Tampilan Capture from Wi-Fi With Filter HTTP](asset/image/tampilanCaptureFromWifiWithFilterHTTP.png)
 - Line-based text data (response `text/html`)
 ![Line-Based Text Data: text/html](asset/image/lineBasedTextDataHtmlVer.png)
