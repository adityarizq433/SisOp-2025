# TUGAS APPENDIX A dan TIMELINE OS

## Nama : Mukhamad Aditya Rizq Qiya Mullail  
## NRP : 3124500050  
## Dosen Pengajar : Dr Ferry Astika Saputra ST, M.Sc  
## PROGRAM STUDI D3 TEKNIK INFORMATIKA POLITEKNIK ELEKTRONIKA NEGERI SURABAYA (PENS)  
## TAHUN 2025  

# PROGRAM STUDI D3 TEKNIK INFORMATIKA POLITEKNIK ELEKTRONIKA NEGERI SURABAYA (PENS)  
# TAHUN 2025  

## 1. Migrasi Fitur  

### a. Migrasi Fitur  
Fitur yang awalnya hanya ada di sistem besar (mainframe) akhirnya diadopsi oleh sistem yang lebih kecil (microcomputer). Ini menunjukkan bagaimana konsep yang awalnya dirancang untuk sistem besar dapat diterapkan pada sistem yang lebih kecil seiring dengan perkembangan teknologi.  

### b. Contoh  
MULTICS, sistem operasi yang dikembangkan pada 1960-an, mempengaruhi perkembangan sistem operasi modern seperti UNIX. MULTICS memperkenalkan konsep seperti proteksi berbasis ring dan sistem file hierarkis, yang kemudian diadopsi oleh sistem operasi modern.  

## 2. Sistem Awal  

### a. Sistem Dedikasi  
Pada awal perkembangan komputer, programmer juga berperan sebagai operator. Mereka harus memuat program secara manual ke dalam memori menggunakan panel depan, pita kertas, atau kartu berlubang. Program kemudian dijalankan dan dimonitor melalui lampu display di konsol.  

### b. Sistem Berbagi  
Untuk meningkatkan efisiensi, operator profesional diperkenalkan. Operator ini memiliki pengalaman lebih dalam mengelola sistem, sehingga mengurangi waktu setup. Selain itu, pekerjaan dengan kebutuhan serupa dikelompokkan (batching) untuk mengurangi waktu setup.  

### c. I/O Tumpang Tindih  
Untuk mengatasi masalah kecepatan I/O yang lambat, tape magnetik digunakan sebagai perantara antara perangkat input/output (seperti pembaca kartu dan printer) dengan CPU. Ini memungkinkan CPU untuk bekerja lebih efisien tanpa harus menunggu perangkat I/O yang lambat.  

## 3. Atlas  

### a. Atlas  
Dikembangkan di Universitas Manchester pada akhir 1950-an, Atlas adalah salah satu sistem operasi pertama yang menggunakan manajemen memori dengan paging.  

### b. Fitur Utama  
- **Spooling**: Atlas menggunakan spooling untuk menjadwalkan pekerjaan berdasarkan ketersediaan perangkat periferal.  
- **Manajemen Memori**: Atlas menggunakan drum sebagai memori utama dan sejumlah kecil memori inti sebagai cache. Sistem ini juga menggunakan demand paging untuk mentransfer informasi antara memori inti dan drum secara otomatis.  

## 4. XDS-940  

### a. XDS-940  
Sistem operasi time-sharing yang dikembangkan di UC Berkeley pada awal 1960-an.  

### b. Fitur Utama  
- **Paging**: XDS-940 menggunakan paging untuk relokasi, meskipun tidak menggunakan demand paging.  
- **Time-Sharing**: Sistem ini memungkinkan beberapa pengguna untuk berbagi sumber daya komputer secara bersamaan.  

## 5. THE  

### a. THE  
Dikembangkan di Technische Hogeschool Eindhoven pada pertengahan 1960-an.  

### b. Fitur Utama  
- **Struktur Lapisan**: THE memiliki desain yang bersih dengan struktur lapisan yang jelas.  
- **Sinkronisasi Proses**: Sistem ini menggunakan semaphore untuk sinkronisasi proses.  
- **Deadlock Control**: THE menggunakan algoritma banker untuk menghindari deadlock.  

## 6. RC 4000  

### a. RC 4000  
Dikembangkan oleh Brinch-Hansen pada akhir 1960-an.  

### b. Fitur Utama  
- **Kernel**: RC 4000 dirancang sebagai kernel yang dapat digunakan untuk membangun sistem operasi lengkap.  
- **Sistem Pesan**: Komunikasi antar proses dilakukan melalui sistem pesan, yang disimpan dalam buffer dari pool buffer umum.  

## 7. CTSS  

### a. CTSS  
Sistem time-sharing eksperimental yang dikembangkan di MIT pada 1961.  

### b. Fitur Utama  
- **Multilevel Feedback Queue**: CTSS menggunakan algoritma penjadwalan CPU dengan multilevel feedback queue untuk mengelola waktu CPU yang diberikan kepada setiap pengguna.  
- **Swapping**: Memori pengguna ditukar antara memori utama dan drum yang cepat.  

## 8. MULTICS  

### a. MULTICS  
Dikembangkan oleh MIT, GE, dan Bell Labs dari 1965 hingga 1970.  

### b. Fitur Utama  
- **Sistem File Hierarkis**: MULTICS memperkenalkan sistem file hierarkis yang memungkinkan pengguna untuk membuat struktur direktori mereka sendiri.  
- **Proteksi Berbasis Ring**: Sistem ini menggunakan proteksi berbasis ring untuk mengontrol akses ke sumber daya sistem.  

## 9. IBM OS/360  

### a. OS/360  
Dikembangkan oleh IBM pada pertengahan 1960-an.  

### b. Fitur Utama  
- **Keluarga Komputer**: OS/360 dirancang untuk keluarga komputer IBM/360, yang mencakup berbagai ukuran dan kemampuan.  
- **Kompleksitas**: OS/360 mencoba untuk menjadi sistem operasi yang serbaguna, tetapi mengalami masalah kompleksitas dan performa.  

## 10. TOPS-20  

### a. TOPS-20  
Dikembangkan oleh DEC pada 1970-an.  

### b. Fitur Utama  
- **Manajemen Memori Virtual**: TOPS-20 menggunakan manajemen memori virtual untuk meningkatkan efisiensi penggunaan memori.  
- **Time-Sharing**: Sistem ini dirancang untuk mendukung banyak pengguna secara bersamaan.  

## 11. CP/M dan MS-DOS  

### a. CP/M  
Sistem operasi awal untuk komputer mikro yang dikembangkan oleh Gary Kildall.  

### b. MS-DOS  
Dikembangkan oleh Microsoft untuk IBM PC, menjadi sistem operasi dominan pada 1980-an.  

### c. Fitur Utama  
- **Kemudahan Penggunaan**: MS-DOS memiliki set perintah yang lebih kaya dibandingkan CP/M, membuatnya lebih mudah digunakan.  

## 12. Macintosh Operating System dan Windows  

### a. Mac OS  
Sistem operasi dengan antarmuka grafis (GUI) yang dirilis pada 1984.  

### b. Windows  
Sistem operasi yang dikembangkan oleh Microsoft, menjadi pesaing utama Mac OS.  

### c. Fitur Utama  
- **Antarmuka Grafis**: Kedua sistem operasi ini memperkenalkan antarmuka grafis yang memudahkan pengguna untuk berinteraksi dengan komputer.  

## 13. Mach  

### a. Mach  
Dikembangkan di Carnegie Mellon University pada 1980-an.  

### b. Fitur Utama  
- **Kernel Mikro**: Mach dirancang sebagai kernel mikro yang mendukung multiprosesor dan komunikasi berbasis pesan.  
- **Kompatibilitas dengan UNIX**: Mach dirancang untuk meniru 4.3 BSD UNIX, memungkinkan file executable dari sistem UNIX untuk berjalan di Mach.  

## 14. Sistem Berbasis Kemampuan (Capability-based Systems)  

### a. Hydra  
Sistem proteksi berbasis kemampuan yang fleksibel, memungkinkan pengguna untuk mendefinisikan hak akses mereka sendiri.  

### b. CAP  
Sistem proteksi berbasis kemampuan yang lebih sederhana dibandingkan Hydra, tetapi masih dapat digunakan untuk melindungi objek yang didefinisikan oleh pengguna.  

## 15. Sistem Lainnya  

### a. MCP dan SCOPE  
Sistem operasi awal yang mendukung multiprosesor dan memiliki desain yang baik untuk koordinasi dan sinkronisasi proses.  

# Timeline Sistem Operasi  

| Tahun | Sistem Operasi | Keterangan |
|-------|----------------|------------|
| 1949  | Manchester Mark 1 | Komputer stored-program pertama yang berhasil dijalankan. |
| 1951  | Ferranti Mark 1 | Komputer komersial pertama. |
| 1961  | CTSS | Sistem time-sharing eksperimental pertama di MIT. |
| 1962  | XDS-940 | Sistem time-sharing dengan paging untuk relokasi. |
| 1965  | MULTICS | Sistem operasi time-sharing dengan sistem file hierarkis. |
| 1966  | THE | Sistem batch dengan struktur lapisan dan semaphore untuk sinkronisasi. |
| 1969  | UNIX | Dikembangkan oleh Bell Labs, menjadi dasar banyak sistem operasi modern. |
| 1970  | TOPS-20 | Sistem time-sharing dengan manajemen memori virtual. |
| 1974  | CP/M | Sistem operasi untuk komputer mikro. |
| 1981  | MS-DOS | Sistem operasi untuk IBM PC, menjadi dominan pada 1980-an. |
| 1984  | Mac OS | Sistem operasi dengan antarmuka grafis untuk Macintosh. |
| 1985  | Windows 1.0 | Versi pertama Microsoft Windows. |
| 1987  | Mach | Kernel mikro yang mendukung multiprosesor dan komunikasi berbasis pesan. |
| 1991  | Linux | Sistem operasi open-source yang dikembangkan oleh Linus Torvalds. |
| 2000  | Windows 2000 | Versi Windows yang ditujukan untuk pasar bisnis. |
| 2001  | macOS X | Sistem operasi Apple yang berbasis UNIX. |
