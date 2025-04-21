# Project 0
## Monitoring-Health-System

Proyek ini bertujuan untuk mengembangkan sistem pengecekan kesehatan tubuh untuk Smart Building, menggunakan komponen utama seperti Arduino, Sensor 30102, DS18B20, LCD 12C. Arduiino Uno bertindak sebagai mikroprosesor utama yang mengontrol komunikasi antar sensor dan perangkat, memungkinkan pemantauan dan pengontrolan secara real-time.

Dalam rankaian ini komponen utama sensor DS18B20 dan MAX 30100 sebagai pendeteksi detak jantung, Suhu, dan Oksigen. Pada output UART ditampilkan pada LCD I2C. Sehingga pemantauan dapat dilakukan secara langsung setelah itu akan dimasukkan kedalam rule sehingga dapat di sebutkan bahwa orang tersebut sehat atau tidak.

Dengan bantuan teknologi pemantauan kesehatan dapat  dilakukan secara efisien sehingga dapat mengantisipasi berbagai penyakit atau kondisi tubuh sakit secara singkat. 

## Support By :
>- Dosen Pengampu : Akhmad Hendriawan ST., MT. (NIP.197501272002121003)
>- Mata kuliah : Mikrokontroller 
>- Program Studi : D4 Teknik Elektronika
>- Politeknik Elektronika Negeri Surabaya<br>

## Team Member : 
|      NRP      |       Nama      |    Jobdesk    |   Akun |
| :-----------:|:----------------:| :------------:| :-----:|
| 2123600033    | Fiqinnajach Al Makhi          | 3D Designer       | [Fiqhin](https://github.com/Raditya-G)
| 2123600038    | Akmal Aditya                  |   Software Developer | [Akmal](https://github.com/nataratungga)
| 2123600045    | Farhan Bayu Pamungkas         |    Hardware Specialist      | [Farhan](https://github.com/Bismaap)
| 2123600049    | Dariel Afron Zah Maulana      | Software Developer | [Dariel](https://github.com/NurRohmatHidayat)
| 2123600054    | Sahid Zuhdi Karuniawan Kelana | Project Manager     | [Sahid](https://github.com/EzarPrasetya)
| 2123600057    | Muhammad Ammar Tsaqif         | PCB Designer     |[Ammar](https://github.com/Yadnur)

## Preview Slide Presentasi

https://www.canva.com/design/DAGlLzyWL-8/5bgNkGYzvLAk4_L8IqqjvA/edit

## Link YouTube 
Preview Video
https://www.youtube.com/watch?v=sizFK8IugYw

## Daftar Isi
- [Komponen Yang Digunakan](#Komponen-Yang-Digunakan)
- [Wiring Plan](#Wiring-Plan)
- [Hardware](#Hardware)
- [Desain 3D](#Desain-3D)
- [Program ESP32](#Program-ESP32)
- [Program Design UI/UX](#Pogram-Design-UI/UX)

 
## Komponen Yang Digunakan
1. **Hardware**<br>
    a. Arduino UNo<br>
    b. Sensor DS18B20<br>
    c. Sensor MAX30100<br>
    d. Kabel Jumper<br>
    e. LCD I2C<br>
    f. Bread Board<br>
    g. LED display<br>

2. **Software**<br>
    a. Arduino ide<br>
    b. KiCad<br>
    c. Visual Studio Code (VSC)<br>

3. **Alat**<br>
    a. Solder<br>
    b. Timah solder<br>

## Diagram Block
<img src="Dokumentasi/Diagram Block.png">

## Diagram Arsitektur System
Berikut adalah alur Diagram untuk mengirim data sensor dari publisher ke database
<img src="Dokumentasi/Diagram System.png">

## Preview Penggunaan OTA

<div align="center"
<img src="https://raw.githubusercontent.com/ayushsharma82/ElegantOTA/master/docs/demo.gif" width="600">
</div>


## Program ESP32

Program utama dari projek ini :
- [Arduino dengan C](https://github.com/NurRohmatHidayat/Smart-Building-Solution/tree/main/Program%20ESP32/Smart%20Building/Smart%20Building/src)

Berikut adalah video demontrasi prototype hardware. 

https://github.com/user-attachments/assets/7abacf07-8daf-47ce-86e2-667d23beedc0

Simulasi ini kami menggunakan ESP32 untuk mengontrol sensor dan modul yang terhubung di breadboard. Simulasi dilakukan menggunakan Wokwi, yang memudahkan pengujian rangkaian secara virtual sebelum implementasi fisik. Rangkaian melibatkan sensor DHT11, modul relay, LED indikator, potensiometer, dan RTC untuk sinkronisasi waktu.

Relay digunakan untuk mengontrol perangkat eksternal, sementara LED menunjukkan status sistem. Simulasi ini membantu dalam debugging dan memastikan komunikasi antar komponen berjalan baik. Meskipun Wokwi tidak menyediakan semua komponen, platform ini sangat berguna untuk pengujian dan visualisasi fungsi dasar rangkaian, membantu mengidentifikasi masalah sebelum produksi fisik.


Berikut adalah video demontrasi alat menggunakan wokwi. Klik link [Video Simulasi Software](https://youtu.be/oXDYyiHHBaU "Video Simulasi Software")

## [Alur Komunikasi]

Pada proyek ini, ESP32 menggunakan Wi-Fi Manager untuk mempermudah proses koneksi ke jaringan Wi-Fi. Wi-Fi Manager memungkinkan pengguna untuk memilih dan menghubungkan ESP32 ke jaringan internet tanpa harus mengubah kode sumber setiap kali ada perubahan pada jaringan.
Berikut tampilan pada wifi manager untuk menghubungkan ESP32 ke jaringan internet

<div align="center">
<img src="Dokumentasi/wifi manager.png">
</div>

Setelah ESP32 terhubung ke internet, modul ini akan mengirim data secara berkala ke broker MQTT (dalam hal ini menggunakan broker Cool MQTT). Broker MQTT berfungsi sebagai perantara yang memungkinkan ESP32 mengirim data ke sistem lain dalam arsitektur ini.
berikut tampilan broker.mqtt.cool yang menerima data sensor dari publisher ESP32
<img src="Dokumentasi/broker mqtt cool.jpg">

Node-RED digunakan sebagai back end untuk proyek web kami, yang berfungsi mengelola aliran data dan pemrosesannya. Data yang ditampilkan pada antarmuka web berasal dari broker MQTT di mqtt.cool, di mana Node-RED berlangganan ke topik yang relevan, memproses data sesuai kebutuhan, dan menyajikannya ke front end. Pengaturan ini memungkinkan penanganan data secara real-time dan integrasi yang efisien dengan platform web kami.

Berikut adalah alur dari program Node Red yang berfungsi untuk menerima data mqtt.cool kemudian disimpan pada database Mysql.
<img src="Dokumentasi/Node Red.png">

Berikut ini adalah program untuk Back-end Smart Building System IoT menggunakan Node-RED [Node-RED](https://github.com/NurRohmatHidayat/Smart-Building-Solution/tree/main/UI/UX%20Designer)

Berikut ini adalah program untuk WEB Smart Building System IoT menggunakan bahasa HTML [Program](https://github.com/NurRohmatHidayat/Smart-Building-Solution/tree/main/UI/UX%20Designer/node-red)

## Design Protitype Figma

<div align="center">
<img src="Dokumentasi/Figma.jpg">
</div>

## [Langkah-Langkah Penggunaan]
Berikut adalah langkah-langkah menggunakan produk "smart building" untuk para pelanggan:

1. Mengaktifkan Perangkat
  -Pastikan perangkat sudah terisi daya atau menggunakan baterai bawaan.
  -Tekan tombol Power untuk menghidupkan perangkat. Indikator lampu akan menyala sebagai tanda bahwa perangkat aktif.

2. Menghubungkan Perangkat ke Wi-Fi
  -Setelah perangkat aktif, buka smartphone atau laptop Anda.
  -Cari jaringan Wi-Fi dengan nama (ESP32_AP) sesuai perangkat, misalnya: SmartBuilding-Setup.
  -Hubungkan perangkat Anda ke Wi-Fi tersebut.
  -Secara otomatis, halaman konfigurasi Wi-Fi Manager akan terbuka. Jika tidak terbuka, buka browser dan masukkan alamat IP: 192.168.4.1.
  -Pada halaman Wi-Fi Manager:
     Pilih jaringan Wi-Fi gedung Anda.
     Masukkan kata sandi Wi-Fi.
     Klik Connect.
  -Tunggu hingga perangkat terhubung ke internet. Indikator lampu hijau akan menyala jika koneksi berhasil.

3. Memastikan Perangkat Aktif dan Berfungsi
  -Perangkat akan mulai membaca data seperti tegangan, arus, daya listrik, dan suhu ruangan.
  -Pastikan semua sensor bekerja dengan benar dengan melihat indikator status pada perangkat.

4. Mengakses Web untuk Memantau Data Sensor
  -Buka browser Anda dan masukkan alamat web yang telah diberikan, misalnya: [http://d4elkasmartbuilding.rf.gd/?i=1] atau IP tertentu.
  -Masuk ke dashboard menggunakan kredensial yang sudah disediakan.

5. Mengelola dan Memantau Data
  -Pada dashboard web, Anda dapat:
  -Melihat Data Real-Time: Tegangan, arus, daya, dan suhu.
  -Mengontrol Perangkat: Atur suhu ruangan dengan AC atau kipas.
  -Jadwalkan Lampu: Tentukan kapan lampu dinyalakan/dimatikan.
  -Semua perubahan yang Anda lakukan akan langsung diterapkan pada perangkat.
