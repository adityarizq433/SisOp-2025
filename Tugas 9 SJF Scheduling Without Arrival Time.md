# SJF Scheduling Algorithm Without Arrival Time

## Kelompok
- Musthofa Agung Distyawan (3124500031)
- Mukhamad Aditya Rizq Qiya Mullail (3124500050)
- Ferry Ferdiansyah (3124500051)

## FCFS Scheduling Algorithm Without Arrival Time

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
    printf("<--SJF Scheduling Algorithm Without Arrival Time (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)
            if(p[j].bt>p[j+1].bt)
            {
				tmp=p[j];
				p[j]=p[j+1];
				p[j+1]=tmp;
            }
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
![image url](https://github.com/Msthfaa/SisOp_2025/blob/main/assets/tugas9_hasil.png)

### SJF scheduling chart
![image url](https://github.com/Msthfaa/SisOp_2025/blob/main/assets/tugas9_chart.png)

### Analisa
### 1. Struct `proc`
```c
struct proc {
    int no, bt, ct, tat, wt;
};
```
| Field | Arti |
|-------|------|
| `no`  | Nomor proses |
| `bt`  | Burst Time (lama proses berjalan) |
| `ct`  | Completion Time (waktu proses selesai) |
| `tat` | Turnaround Time = CT (karena arrival time = 0) |
| `wt`  | Waiting Time = TAT − BT |

---

### 2. Fungsi Input
```c
struct proc read(int i) {
    struct proc p;
    printf("\nProcess No: %d\n", i);
    p.no = i;
    printf("Enter Burst Time: ");
    scanf("%d", &p.bt);
    return p;
}
```
Membaca burst time dari pengguna dan mengisi struct.

---

### 3. Pengurutan Proses
```c
// Bubble sort berdasarkan burst time
for (int i = 0; i < n-1; i++)
    for (int j = 0; j < n-i-1; j++)
        if (p[j].bt > p[j+1].bt) {
            tmp = p[j];
            p[j] = p[j+1];
            p[j+1] = tmp;
        }
```
Menjamin proses dengan burst time paling kecil berada di depan.

---

### 4. Perhitungan Waktu
```c
int ct = 0;
for (int i = 0; i < n; i++) {
    ct += p[i].bt;      // kumulatif waktu selesai
    p[i].ct  = ct;
    p[i].tat = ct;      // arrival time = 0
    p[i].wt  = p[i].tat - p[i].bt;
}
```

- **Completion Time (CT)**: waktu proses selesai dieksekusi.
- **Turnaround Time (TAT)**: total waktu sejak proses masuk hingga selesai (karena arrival = 0, sama dengan CT).
- **Waiting Time (WT)**: waktu menunggu di ready queue sebelum dieksekusi.

---

### 5. Rata‑rata
```c
avgtat /= n;
avgwt  /= n;
```
Menghitung rata‑rata TAT dan WT untuk semua proses.

---


### 6.Kesimpulan
Algoritma SJF non-preemptive tanpa arrival time mem‐prioritaskan proses berdurasi paling pendek, sehingga rata-rata waiting time dan turnaround time turun signifikan dibanding FCFS. Dengan semua proses dianggap tiba di waktu 0, setiap turnaround time sama dengan completion time, dan waiting time dihitung sebagai selisihnya dengan burst time. Hasilnya, eksekusi berurutan dari burst terpendek ke terpanjang memberi efisiensi maksimal pada metrik kinerja utama
