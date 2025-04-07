
# Tugas Referensi Indonesia - Nomor 3 dan 4

**Nama:** Mukhamad Aditya Rizq Qiya Mullail  
**NRP:** 3124500050  
**Dosen Pengajar:** Dr Ferry Astika Saputra ST, M.Sc  
**Program Studi:** D3 Teknik Informatika  
**Institusi:** Politeknik Elektronika Negeri Surabaya (PENS)  
**Tahun:** 2025  

---

## 1. Proses

### a. Jelaskan tindakan yang diambil oleh sebuah kernel ketika alih konteks antar proses

Tindakan yang diambil yaitu penyimpanan status proses yang sedang berjalan, termasuk nilai register, counter program, dan informasi lainnya ke dalam Process Control Block (PCB) proses tersebut. Kemudian, kernel memuat status proses yang baru akan dijalankan dari PCB-nya ke dalam CPU, termasuk register dan alamat memori yang sesuai. Kernel juga mengatur penjadwalan agar proses baru dapat dijalankan, serta memastikan bahwa sumber daya sistem seperti memori dan I/O dialokasikan dengan benar. Proses ini memungkinkan multitasking dengan efisien dan transparan bagi pengguna.

### b. Informasi apa saja yang disimpan pada tabel proses saat alih konteks dari satu proses ke proses lain

Informasi yang disimpan dalam tabel proses (PCB) meliputi:
- Status register CPU seperti program counter, stack pointer, dan register umum
- Status memori yang mencakup alamat memori dan tabel page/segment
- Informasi manajemen sumber daya seperti file yang sedang dibuka dan izin akses
- Metadata proses seperti ID proses (PID), status proses (running, ready, blocked), dan prioritas

Informasi ini memungkinkan kernel untuk mengembalikan proses ke keadaan semula ketika nanti dijadwalkan kembali, sehingga eksekusi dapat berlanjut tanpa kehilangan data atau konteks sebelumnya.

---

## 2. Thread

### a. Sebutkan dua perbedaan antara user level thread dan kernel thread

1. **Manajemen Thread:**  
   - User-Level Thread (ULT): Dikelola sepenuhnya oleh library thread di user space (misalnya, POSIX threads/Pthreads).  
   - Kernel-Level Thread (KLT): Dikelola langsung oleh kernel sistem operasi.

2. **Blokir Sistem:**  
   - ULT: Jika satu thread melakukan system call yang blocking, seluruh proses akan terblokir karena kernel tidak mengenali ULT.  
   - KLT: Jika satu thread terblokir, thread lain dalam proses yang sama tetap bisa berjalan karena kernel mengetahui masing-masing thread.

### b. Jelaskan tindakan yang diambil oleh sebuah kernel saat alih konteks antara kernel level thread

1. **Menyimpan Status Thread yang Sedang Berjalan:**  
   Kernel menyimpan register CPU, program counter, stack pointer, dan state thread ke dalam Thread Control Block (TCB).

2. **Memilih Thread Baru:**  
   Scheduler kernel memutuskan thread mana yang akan dijalankan berikutnya.

3. **Memuat Status Thread Baru:**  
   Kernel memuat kembali register, program counter, dan state dari TCB thread baru ke CPU.

4. **Perubahan Memori (Jika Diperlukan):**  
   Jika thread berasal dari proses berbeda, kernel juga mengganti address space ke proses tersebut.

5. **Melanjutkan Eksekusi:**  
   CPU melanjutkan eksekusi dari titik terakhir yang disimpan di TCB.

---

## 3. Penjadualan CPU

### a. Keuntungan menggunakan time quantum size di level yang berbeda dari sebuah antrian sistem multilevel

- Meningkatkan Responsivitas Proses Interaktif
- Mengurangi Overhead Context Switching pada Proses Batch/Lama
- Penjadwalan yang Lebih Efisien Berdasarkan Kebutuhan Proses
- Mencegah Starvation pada Proses Prioritas Rendah

---

### b. Gambarkan 4 diagram Chart yang mengilustrasikan eksekusi dari proses-proses tersebut menggunakan FCFS, SJF, prioritas nonpreemptive dan round robin.

| Proses | Burst Time | Prioritas |
|--------|------------|-----------|
| P1     | 10         | 3         |
| P2     | 1          | 1         |
| P3     | 2          | 3         |
| P4     | 1          | 4         |
| P5     | 5          | 2         |

---

### 1. First-Come, First-Served (FCFS)

**Urutan Kedatangan:** P1 → P2 → P3 → P4 → P5

**Gantt Chart:**

```
| P1 (10) | P2 (1) | P3 (2) | P4 (1) | P5 (5) |
0         10       11       13       14      19
```

---

### 2. Shortest Job First (SJF) Non-Preemptive

**Urutan Eksekusi:** P2 → P4 → P3 → P5 → P1

**Gantt Chart:**

```
| P2 (1) | P4 (1) | P3 (2) | P5 (5) | P1 (10) |
0        1        2        4        9        19
```

---

### 3. Prioritas Non-Preemptive

**Urutan Eksekusi:** P2 (prioritas=1) → P5 (2) → P1 (3) → P3 (3) → P4 (4)  
*(Jika prioritas sama, digunakan FCFS)*

**Gantt Chart:**

```
| P2 (1) | P5 (5) | P1 (10) | P3 (2) | P4 (1) |
0        1        6         16       18      19
```

---

### 4. Round Robin (Quantum = 2)

**Urutan Eksekusi:**  
P1 → P2 → P3 → P4 → P5 → P1 → P5 → P1 → P5 → P1 → P1 → P1

**Gantt Chart:**

```
| P1 (2) | P2 (1) | P3 (2) | P4 (1) | P5 (2) | P1 (2) | P5 (2) | P1 (2) | P5 (1) | P1 (2) | P1 (2) |
0        2        3        5        6        8        10       12       14       15       17      19
```

**Penjelasan:**
- Quantum = 2
- Jika burst time ≤ quantum, proses selesai
- Proses dengan sisa waktu dikembalikan ke antrian

---
