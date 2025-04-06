# TUGAS FORKING

**Nama**: Mukhamad Aditya Rizq Qiya Mullail  
**NRP**: 3124500050  
**Dosen Pengajar**: Dr Ferry Astika Saputra ST, M.Sc  
**Program Studi**: D3 Teknik Informatika  
**Politeknik Elektronika Negeri Surabaya (PENS)**  
**Tahun**: 2025

---

## Apa itu Forking

Forking adalah mekanisme dalam sistem operasi berbasis Unix/Linux yang memungkinkan sebuah proses membuat salinan dirinya sendiri, sehingga menghasilkan dua proses yang berjalan secara paralel: proses induk (parent process) dan proses anak (child process). 

Ketika sistem call `fork()` dipanggil, sistem menyalin seluruh konteks proses induk, termasuk memori, register CPU, dan status program, sehingga proses anak menjadi replika persis dari induknya pada saat pemanggilan `fork()`. Setelah pemanggilan `fork()`, kedua proses melanjutkan eksekusi dari titik yang sama, tetapi dapat dibedakan melalui nilai kembalian `fork()`: 

- Proses induk menerima PID (Process ID) dari proses anak.  
- Proses anak menerima nilai 0.  
- Jika `fork()` gagal, nilai -1 dikembalikan.

Forking sering digunakan dalam pemrograman sistem untuk multitasking, seperti menjalankan tugas latar belakang (daemon), membuat server yang menangani banyak klien, atau mengimplementasikan pipeline shell.

---

## Code

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    pid_t pid = fork();  

    if (pid == -1) {
        printf("Gagal fork!\n");
        return 1;
    }
    else if (pid == 0) {
        printf("Proses Anak (PID: %d)\n", getpid());
    }
    else {
        printf("Proses Induk (PID: %d), Anak PID: %d\n", getpid(), pid);
    }

    return 0;
}
```

---

## Analisa

```c
pid_t pid = fork();  
```

- `fork()` digunakan untuk menduplikasi proses.
- Nilai kembaliannya:
  - `0` di dalam proses anak,
  - `PID` dari anak di proses induk,
  - `-1` jika gagal fork.

```c
if (pid == -1) {
    printf("Gagal fork!\n");
    return 1;
}
```

- Jika `fork()` gagal, tampilkan pesan dan keluar.

```c
else if (pid == 0) {
    printf("Proses Anak (PID: %d)\n", getpid());
}
```

- Di proses anak, tampilkan PID proses anak.

```c
else {
    printf("Proses Induk (PID: %d), Anak PID: %d\n", getpid(), pid);
}
```

- Di proses induk, tampilkan PID induk dan PID anak.
