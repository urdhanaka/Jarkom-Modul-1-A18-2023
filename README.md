# Jarkom-Modul-1-A18-2023

- [Jarkom-Modul-1-A18-2023](#jarkom-modul-1-a18-2023)
  - [Anggota](#anggota)
    - [Soal 1](#soal-1)
    - [Soal 2](#soal-2)
    - [Soal 3](#soal-3)
    - [Soal 4](#soal-4)
    - [Soal 5](#soal-5)
    - [Soal 6](#soal-6)
    - [Soal 7](#soal-7)
    - [Soal 8](#soal-8)
    - [Soal 9](#soal-9)
    - [Soal 10](#soal-10)

## Anggota

|     | Nama                      | NRP        |
| --- | ------------------------- | ---------- |
| 1   | SATRIA SULTHAN SABILILLAH | 5025201267 |
| 2   | Urdhanaka Aptanagi        | 5025211123 |

### Soal 1

Di soal ini terdapat statement:
> User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.

Mengunggah melalui protokol FTP menggunakan perintah STOR, sehingga kita perlu mencari string STOR pada paket yang berisi request dan response-nya. Ditemukan seperti berikut:

![1](https://user-images.githubusercontent.com/46347836/269847268-af767915-247d-4cfa-813f-1428f207f996.png)

> A. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut?
>
> B. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut?

Kita periksa deskripsi dari paket bernomor 147 yang kita temukan tadi dan kita temukan sequence number (raw) dan acknowledge number (raw)

![1AB](https://user-images.githubusercontent.com/46347836/269847749-baee2bd8-ac36-42d5-a278-6d94c70f7a0c.png)

> C. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
>
> D. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

Kita peruksa deskripsi dari paket bernomor 149 dan kita temukan sequence number (raw) dan acknowledge number (raw)

![1CD](https://user-images.githubusercontent.com/46347836/269848101-10ff1972-362f-4964-9976-4a683b674b8e.png)

![1Flag](https://user-images.githubusercontent.com/46347836/269854135-6f8fe16c-a6e2-4f02-9edb-36bbd1cc16e4.png)

### Soal 2

> Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

Karena web server yang diakses biasanya menggunakan protokol HTTP, maka kita search paket yang menggunakan protokol HTTP

![2](https://user-images.githubusercontent.com/46347836/269849052-ed3eea50-2f15-4313-90c3-5b8922eebe03.png)

Kemudian kita pilih salah satu paket tersebut, sebagai contoh kita pilih paket 1092 dan kemudian kita follow HTTP Stream nya dan kita dapat mengetahui web server apa yang digunakan yaitu gunicorn

![2Answer](https://user-images.githubusercontent.com/46347836/269849379-191c9132-b15f-4e45-b45b-4a3c1803058f.png)

![2Flag](https://user-images.githubusercontent.com/46347836/269854860-d402224e-7d37-4d79-b448-500dc64dea86.png)

### Soal 3

> A. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?

Untuk soal ini kita menggunakan Display Filter berupa "ip.addr == 239.255.255.250 && (tcp.port == 3702 || udp.port == 3702)".

![3](https://user-images.githubusercontent.com/46347836/269851060-30d21381-bac1-43f0-8002-5e75ffd581cd.png)

> B. Protokol layer transport apa yang digunakan?

Dapat dilihat bahwa semua paket yang telah difilter tadi menggunakan protokol UDP

![3Flag](https://user-images.githubusercontent.com/46347836/269855297-10594373-3c5c-4d75-bd12-f1af1af24f9e.png)

### Soal 4

> Berapa nilai checksum yang didapat dari header pada paket nomor 130?

Untuk soal ini, kita pilih paket nomor 130 dan kemudian kita cek bagian User Datagram Protocol dan kita temukan nilai dari checksum

![4](https://user-images.githubusercontent.com/46347836/269851601-d284fa2a-cd30-45d0-9b76-5f1ab00b6853.png)

![4Flag](https://user-images.githubusercontent.com/46347836/269856980-b4774370-c97b-45e0-a18a-2ab4649ae4c6.png)

### Soal 5

Untuk soal ini kita tidak diberi IP dan port untuk menjawabnya, namun kita diberikan sebuah file yang dienkripsi. Untuk mendapatkan password ini kita perlu melakukan follow TCP stream ke paket yang menggunakan protokol SMTP dan kita temukan passwordnya

![5](https://user-images.githubusercontent.com/46347836/269853578-ca1686f3-b0fc-4a84-a87c-22524d59b67c.png)

Setelah kita decode ke Base64 dan kita buka file yang dienkripsi tadi, kita mendapatkan IP dan port untuk menjawab pertanyaan-pertanyaan di bawah

> A. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?

Untuk soal ini kita buka file pcap nya kemudian kita dapatkan banyak paket yang ada

![5A](https://user-images.githubusercontent.com/46347836/269852078-b0596b81-0c07-4918-bf2b-560bdce3f9d4.png)

> B. Port berapakah pada server yang digunakan untuk service SMTP?

Kita filter paket yang menggunakan protokol SMTP kemudian kita cek bagian Transmission Control Protocol nya, yaitu port 25

![5B](https://user-images.githubusercontent.com/46347836/269852678-1b57fd48-e971-4c3f-bbac-c9643e684328.png)

> C. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

Untuk mencari mana IP yang merupakan public IP, kita perlu memeriksa beberapa paket yang ada yang kemudian public IP tersebut adalah 74.53.140.153

![5Flag](https://user-images.githubusercontent.com/46347836/269906097-998d1319-9d81-4073-b4ee-2aec2dfd488f.png)

### Soal 6

Untuk soal ini terdapat sebuah error “server SOURCE ADDRESS 7812 is invalid”. Error ini merupakan sebuah petunjuk untuk melihat paket bernomor 7812 kemudian melihat source addressnya atau IP sourcenya. Kemudian pesan a1 e5 u21 bila kita lihat baik baik, setiap huruf berpasangan dengan angka yang menunjukkan urutan huruf tersebut dalam alfabet (a == 1 yang berarti menunjukkan huruf ke-1 dalam alfabet, e == 5 yang berarti menunjukkan huruf ke-5 dalam alfabet, dst.) yang berarti kita dapat mensubstitusi angka menjadi huruf ataupun huruf menjadi angka

![6](https://user-images.githubusercontent.com/46347836/269906424-5586bd8d-2fd1-487f-8e5c-a572fb51f8f8.png)

Kita lihat sourcenya adalah 104.18.14.101. Kemudian kita substitusi angka-angka tersebut ke huruf yang berkaitan. Karena terdapat banyak kemungkinan dalam substitusi (18 bisa dianggap 18 saja atau 1 dan 8), kita anggap setiap angka yang terpisah oleh titik merupakan satu huruf. Hasil akhirnya adalah 10 4 18 14 10 1, jika kita substitusi menjadi jdrnja. Ini merupakan jawaban dari nomor 6 tersebut.

![6Flag](https://user-images.githubusercontent.com/46347836/269906689-2b23f7e8-adb9-41ef-ae6a-7f17ed04f00d.png)

### Soal 7

> Berapa jumlah packet yang menuju IP 184.87.193.88?

Untuk mengerjakan soal ini, Display Filter digunakan untuk mencari paket-paket tersebut. Filter yang digunakan adalah "ip.dst == 184.87.193.88". Dapat dilihat bahwa jumlah paketnya adalah 6

![7](https://user-images.githubusercontent.com/46347836/269907061-2340c7c6-a6a6-4842-bf6a-193a78bba887.png)

![7Flag](https://user-images.githubusercontent.com/46347836/269907528-017644b9-7145-46c6-bf44-565f98e0a1a7.png)

### Soal 8

> Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

Kueri yang dibutuhkan adalah "tcp.dstport == 80 || udp.dstport == 80"

![8Flag](https://user-images.githubusercontent.com/46347836/269907882-6570728f-5665-4cfe-826f-640008c14786.png)

### Soal 9

> Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

Untuk mengerjakan hal ini, kueri yang dibutuhkan adalah "ip.src == 10.51.40.1 && ip.dst != 10.39.55.34"

![9Flag](https://user-images.githubusercontent.com/46347836/269908329-ccd7b85e-dbbd-40da-9ce9-5451ac6a6077.png)

### Soal 10

> Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

Untuk mencari paket yang menggunakan protokol TELNET, kita masukkan telnet ke dalam display filter

![10Filter](https://user-images.githubusercontent.com/46347836/269908798-f7981d37-0872-4869-ad46-520f2c5936a7.png)

Dari semua paket tersebut, terdapat beberapa paket yang mengandung username dan password, namun akhirnya kami menemukan username dan password yang dibutuhkan

![10Username](https://user-images.githubusercontent.com/46347836/269910640-25630d5b-026a-4b39-8b0a-8fa5dd407532.png)

![10Flag](https://user-images.githubusercontent.com/46347836/269910950-1e17afa2-fcf9-4511-a584-a054d367720c.png)
