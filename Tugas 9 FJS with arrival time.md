# Shortest Job First (SJF) Scheduling Algorithm With Arrival Time

## Kelompok
- Musthofa Agung Distyawan (3124500031)
- Mukhamad Aditya Rizq Qiya Mullail (3124500050)
- Ferry Ferdiansyah (3124500051)

### Source Code
```c
#include<stdio.h>
struct proc
{
    int no,at,bt,it,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Arrival Time: ");
    scanf("%d",&p.at);
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    return p;
}
int main()
{
    int  n,j,min=0;
    float avgtat=0,avgwt=0;
    struct proc p[10],temp;
    printf("<--SJF Scheduling Algorithm (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(j=0;j<n-i-1;j++)
            if(p[j].at>p[j+1].at)
            {
            temp=p[j];
            p[j]=p[j+1];
            p[j+1]=temp;
            }
    for(j=1;j<n&&p[j].at==p[0].at;j++)
        if(p[j].bt<p[min].bt)
            min=j;
    temp=p[0];
    p[0]=p[min];
    p[min]=temp;
    p[0].it=p[0].at;
    p[0].ct=p[0].it+p[0].bt;
    for(int i=1;i<n;i++)
    {
        for(j=i+1,min=i;j<n&&p[j].at<=p[i-1].ct;j++)
            if(p[j].bt<p[min].bt)
                min=j;
        temp=p[i];
        p[i]=p[min];
        p[min]=temp;
        if(p[i].at<=p[i-1].ct)
            p[i].it=p[i-1].ct;
        else
            p[i].it=p[i].at;
        p[i].ct=p[i].it+p[i].bt;
    }
    printf("\nProcess\t\tAT\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        p[i].tat=p[i].ct-p[i].at;
        avgtat+=p[i].tat;
        p[i].wt=p[i].tat-p[i].bt;
        avgwt+=p[i].wt;
        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\t%d\n",p[i].no,p[i].at,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].wt);
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}

```
### Hasil
![image url](https://github.com/Msthfaa/SisOp_2025/blob/main/assets/tugas9_hasil2.jpg)

### SJF scheduling chart
![image url](https://github.com/Msthfaa/SisOp_2025/blob/main/assets/tugas9_chart2.png)

### Analisa
## 1. Struktur Data `proc`

```c
struct proc {
    int no;  // Nomor proses (misalnya P1, P2, ...)
    int at;  // Arrival Time – waktu kedatangan proses
    int bt;  // Burst Time – durasi eksekusi proses
    int it;  // Initial Time – saat proses mulai dijalankan
    int ct;  // Completion Time – saat proses selesai
    int tat; // Turnaround Time = CT - AT
    int wt;  // Waiting Time = TAT - BT
};
```

Struktur ini menyimpan semua informasi penting untuk simulasi penjadwalan proses.

---

## 2. Fungsi `read(int i)`

Fungsi ini digunakan untuk mengisi data proses:

* `p.no`: nomor proses
* `p.at`: waktu kedatangan
* `p.bt`: burst time

---

## 3. Alur Logika di `main()`

### a. Input dan Pengurutan

1. Meminta input jumlah proses `n`.
2. Mengisi array `p[n]` dengan data proses.
3. Mengurutkan proses berdasarkan `arrival time`.

### b. Pemilihan Proses Pertama

* Dari proses-proses yang memiliki waktu datang sama dengan proses pertama, pilih yang burst time-nya paling kecil sebagai proses pertama dieksekusi.
* Tetapkan:

  * `it` (initial time) = waktu datang
  * `ct` (completion time) = `it + bt`

### c. Penjadwalan Sisa Proses

Untuk proses ke‑i (dari i=1 sampai n):

1. Cari proses berikutnya yang sudah datang (`at <= ct sebelumnya`) dan memiliki burst time terkecil.
2. Tukar posisi proses saat ini dengan proses tersebut.
3. Tentukan:

   * Jika `at <= ct sebelumnya`, maka `it = ct sebelumnya`
   * Jika belum datang, maka `it = at`
   * `ct = it + bt`

---

## 4. Perhitungan Metrik

Setelah semua proses dijadwalkan:

* `TAT = CT - AT`
* `WT = TAT - BT`
* `RT = WT` (karena proses tidak dipreempt)

Ditampilkan dalam bentuk tabel:

```
Process  AT  BT  CT  TAT  WT  RT
P1       0   4   4   4    0   0
...
```

---

## 5. Rata‑rata

Rata-rata Turnaround Time dan Waiting Time dihitung dan ditampilkan:

```c
avgtat /= n;
avgwt  /= n;
```

---

## 6. Inti Algoritma

| Komponen | Penjelasan                                           |
| -------- | ---------------------------------------------------- |
| Urutan   | Berdasarkan proses yang telah datang dan BT terkecil |
| TAT      | CT - AT                                              |
| WT       | TAT - BT                                             |
| RT       | Sama dengan WT (karena non-preemptive)               |

---

## 7. Catatan

* **Non-Preemptive:** Setelah proses dimulai, tidak bisa diganggu sampai selesai.
* **Arrival Time diperhitungkan,** jadi proses tidak langsung dieksekusi hanya karena BT kecil.
* Cocok untuk simulasi dunia nyata di mana proses datang di waktu berbeda.

---

## 8. Kesimpulan

SJF (Shortest Job First) non-preemptive berfungsi untuk mengatur eksekusi proses berdasarkan burst time terpendek, di mana proses yang sudah berjalan tidak dapat diinterupsi oleh proses lain. Program ini menerima input berupa arrival time dan burst time untuk setiap proses, kemudian mengurutkannya berdasarkan arrival time dan memilih proses dengan burst time terpendek untuk dijalankan terlebih dahulu. Setelah proses selesai, program menghitung completion time (CT), turn around time (TAT), waiting time (WT), dan response time (RT), serta menampilkan hasilnya dalam bentuk tabel beserta rata-rata TAT dan WT. Kelebihan kode ini adalah implementasi SJF yang efisien dengan pengurutan proses dan pemilihan proses terpendek, namun memiliki keterbatasan dalam hal tidak adanya penanganan error untuk input yang tidak valid dan penggunaan bubble sort yang kurang optimal untuk data berukuran besar.

---

