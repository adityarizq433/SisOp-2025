# First Come First Served (FCFS) Scheduling Algorithm

## Kelompok
- Musthofa Agung Distyawan (3124500031)
- Mukhamad Aditya Rizq Qiya Mullail (3124500050)
- Ferry Ferdiansyah (3124500051)

## 1. FCFS Scheduling Algorithm With Arrival Time

### Source Code
```c
#include<stdio.h>
struct proc
{
    int no,at,bt,ct,tat,wt;
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
    struct proc p[10],tmp;
    float avgtat=0,avgwt=0;
    int n,ct=0;
    printf("<--FCFS Scheduling Algorithm (Non-Preemptive)-->");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)    
            if(p[j].at>p[j+1].at)
            {
            tmp=p[j];
            p[j]=p[j+1];
            p[j+1]=tmp;
            }
    printf("\nProcessNo\tAT\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        ct+=p[i].bt;
		p[i].ct=ct;
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
![image url](https://github.com/Msthfaa/SisOp_2025/blob/main/assets/img1.png)

### a. Analisa Mendetail
Algoritma **First-Come First-Served (FCFS)** secara **non-preemptive** bekerja dengan menyusun proses berdasarkan waktu kedatangan (arrival time). Proses yang datang terlebih dahulu akan diproses duluan hingga selesai, tanpa bisa diganggu oleh proses lain yang mungkin datang belakangan namun memiliki burst time lebih kecil.

#### Struktur Data
- `no`: Nomor proses.
- `at`: Waktu kedatangan.
- `bt`: Burst time (lama eksekusi).
- `ct`: Completion time (waktu proses selesai dieksekusi).
- `tat`: Turnaround time (waktu total di sistem).
- `wt`: Waiting time (waktu mengantre sebelum dieksekusi).

#### Proses Eksekusi
1. Data proses diinput oleh pengguna.
2. Proses diurutkan berdasarkan arrival time menggunakan bubble sort.
3. Untuk setiap proses:
   - Completion time dihitung dengan menjumlahkan burst time dari proses sebelumnya.
   - Turnaround time dihitung sebagai selisih antara completion time dan arrival time.
   - Waiting time adalah selisih turnaround time dan burst time.
   - Response time dalam FCFS sama dengan waiting time karena tidak ada preemption.

### b. Hasil Simulasi

#### Timeline Eksekusi
- **P1 (AT=0, BT=8)**: t=0 → t=8
- **P2 (AT=1, BT=4)**: t=8 → t=12
- **P3 (AT=2, BT=9)**: t=12 → t=21
- **P4 (AT=3, BT=5)**: t=21 → t=26

#### Turnaround Time (TAT = CT - AT)
- **P1**: 8 - 0 = 8
- **P2**: 12 - 1 = 11
- **P3**: 21 - 2 = 19
- **P4**: 26 - 3 = 23

#### Waiting Time (WT = TAT - BT)
- **P1**: 8 - 8 = 0
- **P2**: 11 - 4 = 7
- **P3**: 19 - 9 = 10
- **P4**: 23 - 5 = 18

#### Response Time (RT = Start Time - AT)
- **P1**: 0 - 0 = 0
- **P2**: 8 - 1 = 7
- **P3**: 12 - 2 = 10
- **P4**: 21 - 3 = 18

---

## 2. FCFS Scheduling Algorithm Without Arrival Time

### Source Code
```c
#include<stdio.h>
struct proc
{
    int no,bt,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    return p;
}
int main()
{
    struct proc p[10],tmp;
    float avgtat=0,avgwt=0;
    int n,ct=0;
    printf("<--FCFS Scheduling Algorithm Without Arrival Time (Non-Preemptive)-->");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    printf("\nProcessNo\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        ct+=p[i].bt;
		p[i].ct=p[i].tat=ct;
        avgtat+=p[i].tat;
        p[i].wt=p[i].tat-p[i].bt;
        avgwt+=p[i].wt;
        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n",p[i].no,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].wt);
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}
```
### Hasil
![image url](https://github.com/Msthfaa/SisOp_2025/blob/main/assets/img2.png)

### a. Analisa Mendetail
Versi ini adalah implementasi FCFS yang disederhanakan, karena tidak mempertimbangkan waktu kedatangan. Seluruh proses dianggap datang bersamaan di waktu 0, sehingga eksekusi dilakukan sesuai urutan input.

#### Struktur Data
- Tidak menggunakan arrival time.
- Fokus pada burst time dan hasil komputasi.

#### Proses Eksekusi
1. Data burst time dimasukkan secara berurutan.
2. Setiap proses langsung dijadwalkan setelah proses sebelumnya selesai.
3. Karena arrival time dianggap 0, turnaround time = completion time.
4. Waiting time dihitung seperti biasa: TAT - BT.
5. Response time sama dengan waiting time.

### b. Hasil Simulasi

#### Timeline Eksekusi
- **P1 (BT=24)**: t=0 → t=24
- **P2 (BT=3)**: t=24 → t=27
- **P3 (BT=3)**: t=27 → t=30

#### Turnaround Time (TAT = CT)
- **P1**: 24
- **P2**: 27
- **P3**: 30

#### Waiting Time (WT = TAT - BT)
- **P1**: 0
- **P2**: 24
- **P3**: 27

#### Response Time (RT = WT)
- **P1**: 0
- **P2**: 24
- **P3**: 27

---

## Kesimpulan
Algoritma **FCFS** merupakan salah satu algoritma penjadwalan CPU paling sederhana yang mengeksekusi proses berdasarkan urutan kedatangannya. Dalam versi dengan arrival time, FCFS mampu mencerminkan skenario nyata secara lebih akurat karena mempertimbangkan waktu masuk proses ke sistem. Namun, kelemahan utama FCFS adalah **proses dengan burst time besar dapat menyebabkan proses kecil menunggu terlalu lama**, yang dikenal sebagai *convoy effect*.

Sementara itu, versi tanpa arrival time lebih cocok untuk kasus simulasi atau sistem di mana semua proses diasumsikan tersedia secara serempak pada awal waktu. Kedua implementasi menghasilkan nilai average turnaround time dan waiting time yang bisa dievaluasi untuk mengukur efisiensi sistem.

**FCFS cocok untuk sistem batch processing** yang tidak memerlukan interaktivitas tinggi. Namun untuk sistem real-time atau multitasking, FCFS kurang efisien dan bisa menyebabkan kelambatan eksekusi proses kecil.
