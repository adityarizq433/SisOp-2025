# TUGAS COMPILE THREAD 3

**Nama** : Mukhamad Aditya Rizq Qiya Mullail  
**NRP** : 3124500050  
**Dosen Pengajar** : Dr Ferry Astika Saputra ST, M.Sc  
**Program Studi** : D3 Teknik Informatika  
**Politeknik Elektronika Negeri Surabaya (PENS)**  
**Tahun** : 2025

---

## Compile Thread 3

### Code

```c
#include <stdio.h>
#include <pthread.h>

pthread_cond_t cond1 = PTHREAD_COND_INITIALIZER;
pthread_cond_t cond2 = PTHREAD_COND_INITIALIZER;
pthread_cond_t cond3 = PTHREAD_COND_INITIALIZER;
pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
int done = 1;

void *foo(void *arg) {
    int thread_num = *(int *)arg;
    while (1) {
        pthread_mutex_lock(&lock);
        while (done != thread_num) {
            if (thread_num == 1) {
                pthread_cond_wait(&cond1, &lock);
            } else if (thread_num == 2) {
                pthread_cond_wait(&cond2, &lock);
            } else {
                pthread_cond_wait(&cond3, &lock);
            }
        }

        printf("%d ", thread_num);
        fflush(stdout);

        if (done == 3) {
            done = 1;
            pthread_cond_signal(&cond1);
        } else if (done == 1) {
            done = 2;
            pthread_cond_signal(&cond2);
        } else if (done == 2) {
            done = 3;
            pthread_cond_signal(&cond3);
        }

        pthread_mutex_unlock(&lock);
    }
    return NULL;
}

int main() {
    pthread_t tid1, tid2, tid3;
    int n1 = 1, n2 = 2, n3 = 3;

    pthread_create(&tid1, NULL, foo, &n1);
    pthread_create(&tid2, NULL, foo, &n2);
    pthread_create(&tid3, NULL, foo, &n3);

    pthread_join(tid1, NULL);
    pthread_join(tid2, NULL);
    pthread_join(tid3, NULL);

    return 0;
}
```

---

### Output

Program akan mencetak angka `1 2 3` secara terus menerus dalam urutan berulang.  
Untuk menghentikan program, tekan `Ctrl+C`.

---

### Cara Menjalankan Program

1. Buka terminal di Linux.
2. Ketik perintah berikut untuk membuat file C:
   ```bash
   nano print-123.c
   ```
3. Tempelkan kode program ke dalam file tersebut.
4. Simpan dan keluar dengan `Ctrl + X`, tekan `Y`, lalu `Enter`.
5. Kompilasi program dengan perintah:
   ```bash
   gcc -pthread print-123.c -o print-123
   ```
6. Jalankan program:
   ```bash
   ./print-123
   ```

---

## Analisa Program

### Variabel Global

```c
pthread_cond_t cond1 = PTHREAD_COND_INITIALIZER;
pthread_cond_t cond2 = PTHREAD_COND_INITIALIZER;
pthread_cond_t cond3 = PTHREAD_COND_INITIALIZER;
pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
int done = 1;
```

- `cond1`, `cond2`, `cond3`: Condition variable yang digunakan untuk mengatur kapan masing-masing thread boleh dijalankan.
- `lock`: Mutex yang menjaga agar hanya satu thread yang bisa mengakses variabel `done` pada satu waktu.
- `done`: Menentukan giliran thread mana yang boleh berjalan.

### Fungsi Thread (`foo`)

```c
void *foo(void *arg) {
    int thread_num = *(int *)arg;
    while (1) {
        pthread_mutex_lock(&lock);
        while (done != thread_num) {
            if (thread_num == 1) {
                pthread_cond_wait(&cond1, &lock);
            } else if (thread_num == 2) {
                pthread_cond_wait(&cond2, &lock);
            } else {
                pthread_cond_wait(&cond3, &lock);
            }
        }
        printf("%d ", thread_num);
        fflush(stdout);

        if (done == 3) {
            done = 1;
            pthread_cond_signal(&cond1);
        } else if (done == 1) {
            done = 2;
            pthread_cond_signal(&cond2);
        } else if (done == 2) {
            done = 3;
            pthread_cond_signal(&cond3);
        }
        pthread_mutex_unlock(&lock);
    }
    return NULL;
}
```

- Fungsi ini menerima argumen berupa angka 1, 2, atau 3 sebagai identitas thread.
- Looping tak berhingga (`while(1)`) untuk mencetak angka secara terus menerus.
- Menggunakan `pthread_mutex_lock` untuk masuk ke bagian kritis.
- Mengecek apakah sekarang adalah giliran thread tersebut (`done == thread_num`). Jika tidak, menunggu (`pthread_cond_wait`) pada condition variable masing-masing.
- Setelah mendapat giliran, thread akan mencetak angkanya, lalu mengatur `done` ke giliran berikutnya dan memberi sinyal ke thread tersebut (`pthread_cond_signal`).
- Terakhir, mutex dilepas (`pthread_mutex_unlock`).

### Fungsi `main`

```c
  int n1 = 1, n2 = 2, n3 = 3;
    pthread_create(&tid1, NULL, foo, &n1);
    pthread_create(&tid2, NULL, foo, &n2);
    pthread_create(&tid3, NULL, foo, &n3);
```

- Membuat tiga thread menggunakan `pthread_create`.
- Masing-masing thread diberi nomor unik: 1, 2, dan 3.
- Thread akan dijalankan secara bergantian sesuai urutan berdasarkan variabel `done`.

### Urutan Eksekusi

1. Thread 1 dijalankan terlebih dahulu karena `done = 1`.
2. Setelah mencetak `1`, `done` diubah ke `2`, dan `cond2` diberi sinyal.
3. Thread 2 mencetak `2`, lalu mengubah `done` ke `3`, memberi sinyal ke `cond3`.
4. Thread 3 mencetak `3`, lalu mengubah `done` kembali ke `1`, dan memberi sinyal ke `cond1`.
5. Proses ini berulang tanpa henti.

---
