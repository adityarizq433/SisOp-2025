# SRTF preemptive with arrival time

## Kelompok
- Musthofa Agung Distyawan (3124500031)
- Mukhamad Aditya Rizq Qiya Mullail (3124500050)
- Ferry Ferdiansyah (3124500051)

### Source Code
```c
#include<stdio.h>
#define MAX 9999
struct proc
{
    int no,at,bt,rt,ct,tat,wt;
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
    p.rt=p.bt;
    return p;
}
int main()
{
    struct proc p[10],temp;
    float avgtat=0,avgwt=0;
    int n,s,remain=0,time;
    printf("<--SRTF Scheduling Algorithm (Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)
            if(p[j].at>p[j+1].at)
            {
            temp=p[j];
            p[j]=p[j+1];
            p[j+1]=temp;
            }
    printf("\nProcess\t\tAT\tBT\tCT\tTAT\tWT\n");
    p[9].rt=MAX;
    for(time=0;remain!=n;time++)
    {
        s=9;
        for(int i=0;i<n;i++)
            if(p[i].at<=time&&p[i].rt<p[s].rt&&p[i].rt>0)
                s=i;
        p[s].rt--;
        if(p[s].rt==0)
        {
            remain++;
            p[s].ct=time+1;
            p[s].tat=p[s].ct-p[s].at;
            avgtat+=p[s].tat;
            p[s].wt=p[s].tat-p[s].bt;
            avgwt+=p[s].wt;
            printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n",p[s].no,p[s].at,p[s].bt,p[s].ct,p[s].tat,p[s].wt);
        }
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}

```
### Hasil
![image url](https://github.com/Msthfaa/SisOp_2025/blob/main/assets/tugas9_hasil3.jpg)

### SRTF scheduling chart
![image url](https://github.com/Msthfaa/SisOp_2025/blob/main/assets/Tugas9_chart3.png)

### Analisa
## 1. Struktur Data `proc`

```c
struct proc {
    int no;  // Nomor proses (P1, P2, ...)
    int at;  // Arrival Time – waktu proses masuk ke sistem
    int bt;  // Burst Time – lama proses berjalan total
    int rt;  // Remaining Time – waktu eksekusi yang masih tersisa
    int ct;  // Completion Time – waktu proses selesai
    int tat; // Turnaround Time = CT - AT
    int wt;  // Waiting Time = TAT - BT
};
```

---

## 2. Fungsi `read(int i)`

Fungsi untuk mengisi data proses:

* Menentukan arrival time (AT)
* Menentukan burst time (BT)
* Mengatur remaining time (RT) = BT

---

## 3. Alur Utama `main()`

### a. Input & Pengurutan

* Input jumlah proses `n`
* Simpan data proses ke array `p[n]`
* Urutkan proses berdasarkan waktu kedatangan (`arrival time`)

### b. Penjadwalan Proses (SRTF Logic)

* `remain` menyimpan jumlah proses yang sudah selesai
* Iterasi `time` dimulai dari 0 dan terus berjalan sampai semua proses selesai (`remain == n`)
* Pada setiap satuan waktu:

  1. Proses dengan waktu kedatangan <= current time dan waktu tersisa terkecil akan dipilih
  2. Remaining time (`rt`) dari proses tersebut dikurangi 1
  3. Jika proses selesai (`rt == 0`), hitung:

     * Completion Time (`ct`)
     * Turnaround Time (`tat` = `ct - at`)
     * Waiting Time (`wt` = `tat - bt`)

---

## 4. Rata‑rata

```c
avgtat /= n;
avgwt  /= n;
```

Menghitung rata-rata waktu turnaround dan waktu tunggu.

---

## 5. Ciri Khas Algoritma

| Komponen       | Penjelasan                                                                                        |
| -------------- | ------------------------------------------------------------------------------------------------- |
| **Preemptive** | Proses bisa digantikan oleh proses lain kapan saja jika ada yang lebih singkat waktu sisanya      |
| **Responsif**  | Baik untuk sistem real-time karena selalu menjalankan proses tercepat yang tersedia               |
| **Complexity** | Sedikit lebih kompleks dari SJF karena harus mengecek setiap saat proses mana yang paling singkat |

---

## 6. Output Contoh

```
Process     AT  BT  CT  TAT  WT
P1          0   8   12  12   4
P2          1   4   5   4    0
...
Average TurnAroundTime = 8.25
Average WaitingTime = 3.25
```

---

## 7. Kesimpulan

SRTF (Shortest Remaining Time First) preemptive bekerja dengan memprioritaskan proses yang memiliki sisa waktu eksekusi (remaining time) terpendek pada setiap satuan waktu, di mana proses yang sedang berjalan dapat diinterupsi jika ada proses baru dengan sisa waktu lebih pendek. Program menerima input arrival time dan burst time untuk setiap proses, mengurutkannya berdasarkan arrival time, kemudian mensimulasikan eksekusi proses secara preemptive dengan terus memantau remaining time dan memilih proses terpendek setiap satuan waktu. Setelah proses selesai, program menghitung completion time (CT), turn around time (TAT), dan waiting time (WT), serta menampilkan hasilnya dalam bentuk tabel beserta rata-rata TAT dan WT. Kelebihan kode ini adalah implementasi SRTF yang efisien dengan penjadwalan dinamis berdasarkan remaining time, namun memiliki keterbatasan dalam hal tidak adanya penanganan error untuk input yang tidak valid dan penggunaan array statis yang membatasi jumlah proses maksimum.

---

