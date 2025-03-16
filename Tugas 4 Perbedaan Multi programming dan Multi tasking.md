# TUGAS PERBEDAAN MULTI PROGRAMMING DAN MULTI TASKING, FUNGSI OS, dan VIRTUALISASI CONTAINER

## Nama: Mukhamad Aditya Rizq Qiya Mullail
## NRP: 3124500050
## Dosen Pengajar: Dr Ferry Astika Saputra ST, M.Sc
## PROGRAM STUDI D3 TEKNIK INFORMATIKA POLITEKNIK ELEKTRONIKA NEGERI SURABAYA (PENS)
## TAHUN 2025

---

## Perbedaan Multi Programming dan Multi Tasking

### Multi-programming

#### Definisi:
Multi-programming adalah teknik di mana beberapa program (proses) dimuat ke dalam memori utama (RAM) secara bersamaan, tetapi hanya satu program yang dijalankan oleh CPU pada satu waktu.

Ketika program yang sedang berjalan menunggu (misalnya, menunggu operasi I/O), CPU beralih ke program lain yang siap dijalankan.

#### Tujuan:
- Meningkatkan utilisasi CPU dengan memastikan CPU selalu sibuk mengerjakan suatu proses.
- Mengurangi waktu idle CPU dengan memanfaatkan waktu tunggu suatu proses untuk menjalankan proses lain.

#### Cara Kerja:
1. Beberapa program disimpan dalam memori utama.
2. CPU hanya menjalankan satu program pada satu waktu.
3. Jika program yang sedang berjalan membutuhkan operasi I/O atau menunggu sumber daya, CPU akan beralih ke program lain yang siap dijalankan.

#### Karakteristik:
- Biasanya digunakan dalam sistem batch processing.
- Tidak interaktif; pengguna tidak dapat berinteraksi langsung dengan program yang sedang berjalan.
- Switching antar proses relatif lambat karena hanya terjadi ketika proses aktif menunggu.

#### Contoh:
- Sistem operasi lama yang menjalankan job secara berurutan, seperti sistem batch pada komputer mainframe.

### Multi-tasking

#### Definisi:
Multi-tasking adalah teknik di mana CPU menjalankan beberapa tugas (task) atau proses secara bersamaan dengan cara membagi waktu (time-sharing).
Setiap proses mendapatkan slot waktu (time slice) untuk dijalankan oleh CPU.

#### Tujuan:
- Memberikan ilusi bahwa beberapa program berjalan secara bersamaan.
- Memungkinkan pengguna untuk berinteraksi dengan beberapa aplikasi sekaligus.

#### Cara Kerja:
1. CPU membagi waktu eksekusi di antara beberapa proses.
2. Setiap proses mendapatkan jatah waktu tertentu (time slice) untuk dijalankan.
3. Proses beralih dengan sangat cepat, sehingga terlihat seperti semua proses berjalan bersamaan.

#### Karakteristik:
- Interaktif; pengguna dapat berinteraksi langsung dengan program yang sedang berjalan.
- Switching antar proses sangat cepat karena menggunakan mekanisme time-sharing.
- Dirancang untuk sistem yang membutuhkan respons cepat, seperti sistem operasi modern.

#### Contoh:
- Sistem operasi modern seperti Windows, Linux, atau macOS yang memungkinkan pengguna menjalankan beberapa aplikasi sekaligus (misalnya, browser, pemutar musik, dan editor teks).

### Perbedaan Utama:

| Aspek | Multi-programming | Multi-tasking |
|---|---|---|
| **Tujuan** | Meningkatkan utilisasi CPU | Memberikan ilusi bahwa beberapa proses berjalan bersamaan |
| **Jumlah Proses yang Dijalankan** | Beberapa program dimuat dalam memori, tetapi hanya satu yang dijalankan oleh CPU pada satu waktu | Beberapa proses dijalankan secara bergantian dengan cepat |
| **Interaksi Pengguna** | Tidak interaktif (batch processing) | Interaktif (time-sharing) |
| **Kecepatan Switching** | Relatif lambat | Sangat cepat |
| **Contoh Penerapan** | Sistem batch processing pada komputer mainframe | Sistem operasi modern seperti Windows, Linux, atau macOS |

---

## Fungsi OS

Sistem operasi (OS) adalah perangkat lunak yang menghubungkan perangkat keras dengan pengguna atau aplikasi. Fungsi utamanya adalah mengelola sumber daya komputer dan menyediakan lingkungan untuk menjalankan aplikasi.

1. **Manajemen Proses**: Mengatur bagaimana proses dibuat, dijalankan, dihentikan, dan dihapus dari memori.
2. **Manajemen Memori**: Mengatur alokasi memori untuk proses yang sedang berjalan.
3. **Manajemen File dan Penyimpanan**: Mengelola penyimpanan, pengorganisasian, dan pengaksesan data.
4. **Manajemen Perangkat**: Mengatur komunikasi antara perangkat keras dan sistem operasi.
5. **Antarmuka Pengguna**: Menyediakan CLI atau GUI untuk memudahkan interaksi pengguna dengan komputer.
6. **Keamanan dan Proteksi**: Menggunakan autentikasi, otorisasi, dan enkripsi untuk melindungi sistem.
7. **Dukungan Jaringan**: Mengatur komunikasi antara komputer di jaringan.
8. **Manajemen Sumber Daya**: Memastikan CPU, memori, penyimpanan, dan perangkat keras lainnya digunakan secara efisien.
9. **Dukungan Aplikasi**: Menyediakan API yang memungkinkan pengembang berinteraksi dengan perangkat keras tanpa perlu memahami detail teknisnya.

---

## Virtualisasi Container

### Definisi
Teknologi yang memungkinkan aplikasi dan dependensinya (seperti library, framework, atau konfigurasi) dijalankan dalam lingkungan yang terisolasi, disebut **container**, di atas sistem operasi yang sama. 

### Konsep Dasar Virtualisasi Container

- **Container**: Paket yang berisi aplikasi beserta semua dependensi yang dibutuhkan untuk menjalankannya.
- **Isolasi**: Aplikasi dalam satu container tidak dapat mengganggu aplikasi di container lain.
- **Efisiensi**: Container lebih ringan dan cepat dibandingkan mesin virtual.
- **Portabilitas**: Container dapat dijalankan di berbagai lingkungan.

### Keuntungan Virtualisasi Container

1. **Efisiensi Sumber Daya**: Tidak memerlukan sistem operasi lengkap untuk setiap instance.
2. **Portabilitas**: Dapat dijalankan di berbagai lingkungan, mulai dari laptop lokal hingga cloud.
3. **Konsistensi**: Menghindari masalah "works on my machine".
4. **Skalabilitas**: Dapat di-scale secara horizontal atau vertikal.
5. **Isolasi**: Masalah dalam satu container tidak memengaruhi container lain.

### Contoh Penggunaan Virtualisasi Container

1. **Pengembangan Aplikasi**: Membantu developer dalam membuat lingkungan pengembangan yang konsisten.
2. **Microservices**: Memungkinkan setiap layanan dijalankan dalam container terpisah.
3. **CI/CD (Continuous Integration/Continuous Deployment)**: Memungkinkan otomatisasi proses build, test, dan deployment.
4. **Cloud Computing**: Digunakan di platform cloud seperti AWS, Google Cloud, dan Azure untuk menjalankan aplikasi secara efisien dan scalable.
