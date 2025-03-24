# TUGAS FLOPS dan IOPS

## Nama
Mukhamad Aditya Rizq Qiya Mullail

## NRP
3124500050

## Dosen Pengajar
Dr Ferry Astika Saputra ST, M.Sc

## PROGRAM STUDI D3 TEKNIK INFORMATIKA POLITEKNIK ELEKTRONIKA NEGERI SURABAYA (PENS)

## TAHUN 2025

---

## Tujuan Pembelajaran

### Memahami Konsep Dasar
- Menjelaskan pengertian FLOPS (operasi floating point per detik) dan IOPS (operasi baca/tulis per detik).
- Memahami perbedaan dan konteks penggunaan FLOPS (komputasi) dan IOPS (penyimpanan).

### Mengenal Alat Pengujian
- Mengidentifikasi alat pengujian FLOPS (contoh: LINPACK, HPL) dan IOPS (contoh: FIO, Iometer).
- Memahami cara kerja dan penggunaan alat-alat tersebut.

### Melakukan Pengujian
- Menyiapkan lingkungan dan menjalankan pengujian FLOPS pada sistem komputasi.
- Menyiapkan lingkungan dan menjalankan pengujian IOPS pada sistem penyimpanan (HDD, SSD).
- Menganalisis hasil pengujian dan mengidentifikasi faktor yang memengaruhi kinerja.

---

## Dasar Teori

### Pengertian FLOPS (Floating Point Operations Per Second)
FLOPS adalah metrik yang digunakan untuk mengukur kinerja komputasi suatu sistem, khususnya dalam melakukan operasi floating point (bilangan pecahan) per detik.

### Pengertian IOPS (Input/Output Operations Per Second)
IOPS adalah metrik yang mengukur kinerja sistem penyimpanan dalam melakukan operasi baca/tulis per detik.

### Perbedaan FLOPS dan IOPS
- **FLOPS**: Berkaitan dengan kinerja komputasi (CPU/GPU).
- **IOPS**: Berkaitan dengan kinerja penyimpanan (HDD/SSD).

---

## Langkah-langkah

1. Buka terminal Linux dan lakukan clone repository flops-iops:
   ```sh
   git clone https://github.com/ferryastika/flops-iops.git
   ```
2. Masuk ke direktori flops-iops:
   ```sh
   cd flops-iops
   ```
3. Build Program Benchmark:
   ```sh
   make
   ```
4. Jalankan pengujian FLOPS dan IOPS:
   ```sh
   ./iops32 $(nproc)
   ./iops64 $(nproc)
   ./flops32 $(nproc)
   ./flops64 $(nproc)
   ```

---

## Hasil

### CPU: AMD Ryzen 7 7435HS

#### 32 Bit Integer Operations Per Second
```sh
./iops32 $(nproc)
Benchmarking for 32 Bit Integer operations per second
1 | Tr 1: 15477088351 Tr 2: 15391333267 Tr 3: 15485343585 IOPS = 46353765203
Maximum CPU Throughput: 46.353764 Gigaiops.
Maximum Single Core Throughput: 15.485844 Gigaiops.
```

#### 64 Bit Integer Operations Per Second
```sh
./iops64 $(nproc)
Benchmarking for 64 Bit Integer operations per second
1| Tr 1: 43473578720 Tr 2: 43305846454 Tr 3: 43555439304 IOPS = 130334864478
Maximum CPU Throughput: 130.334869 Gigaiops.
Maximum Single Core Throughput: 43.555439 Gigaiops.
```

#### 32 Bit Floating Point Operations Per Second
```sh
./flops32 $(nproc)
Benchmarking for 32 Bit Floating point operations per second
1| Tr 1: 5627075432 Tr 2: 5524270671 Tr 3: 5498892562 FLOPS = 16650238665
Maximum CPU Throughput: 16.650238 Gigaflops.
Maximum Single Core Throughput: 5.627076 Gigaflops.
```

#### 64 Bit Floating Point Operations Per Second
```sh
./flops64 $(nproc)
Benchmarking for 64 Bit Floating point operations per second
1| Tr 1: 11557878748 Tr 2: 11205021022 Tr 3: 10784198178 FLOPS = 33547097948
Maximum CPU Throughput: 33.547096 Gigaflops.
Maximum Single Core Throughput: 11.557878 Gigaflops.
