
# Programming Exercise

Sumber: [osc10e - ch4](https://github.com/ferryastika/osc10e/tree/master/ch4)

---

## a. Penerapan Thread pada `SumTask.java` (Java)

### Penjelasan

File SumTask.java menggunakan framework Fork/Join di Java untuk membagi tugas penjumlahan array besar menjadi sub-tugas yang lebih kecil. Kelas ini memperluas RecursiveTask<Long> dan mengimplementasikan metode compute() untuk memproses bagian dari array. Jika ukuran bagian lebih kecil dari ambang batas tertentu, penjumlahan dilakukan secara langsung; jika tidak, tugas dibagi lagi dan diproses secara rekursif. Pendekatan ini memanfaatkan kemampuan multi-core untuk meningkatkan kinerja komputasi.​

### Code: `SumTask.java`

```java
public class SumTask implements Runnable {
    private int[] array;
    private int start;
    private int end;
    private int sum;

    public SumTask(int[] array, int start, int end) {
        this.array = array;
        this.start = start;
        this.end = end;
    }

    public int getSum() {
        return sum;
    }

    @Override
    public void run() {
        sum = 0;
        for (int i = start; i < end; i++) {
            sum += array[i];
        }
    }
}
```

---

## b. Penerapan Thread di Linux (`thrd-posix.c`) dan Windows (`thrd-win32.c`)

### 1. Penerapan Thread di Linux (`thrd-posix.c`)

#### Penjelasan

File thrd-posix.c menunjukkan penggunaan thread di Linux menggunakan pustaka POSIX Threads (pthread). Program ini membuat beberapa thread dengan pthread_create(), di mana setiap thread menjalankan fungsi tertentu. Setelah eksekusi, pthread_join() digunakan untuk menunggu penyelesaian setiap thread. Penerapan ini menunjukkan bagaimana multitasking dapat dicapai di lingkungan Linux dengan efisien menggunakan pthread.

### 2. Penerapan Thread di Microsoft Windows (`thrd-win32.c`)

#### Penjelasan

File thrd-win32.c menggambarkan pembuatan thread di lingkungan Windows menggunakan API Win32. Thread dibuat dengan fungsi CreateThread(), yang memerlukan pointer ke fungsi yang akan dijalankan oleh thread. Setelah thread selesai, WaitForSingleObject() digunakan untuk menunggu penyelesaian, dan CloseHandle() digunakan untuk membersihkan sumber daya.
