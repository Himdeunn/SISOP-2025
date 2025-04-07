# Code Compilation and Explanation of Each Thread Process

<br>

Kode `print123thread.c` merupakan program C yang menggunakan tiga thread untuk mencetak angka secara paralel. Setiap thread bertanggung jawab mencetak satu angka, yaitu 1, 2, atau 3. Program ini digunakan untuk memahami bagaimana thread bekerja dalam sistem multitasking, serta bagaimana sinkronisasi dapat mempengaruhi urutan eksekusi thread.

Pada kode `print123thread.c`, terdapat tiga thread yang dibuat untuk mencetak angka 1, 2, dan 3. Setiap thread memiliki fungsi yang berbeda-beda, dan berikut adalah penjelasan masing-masing thread secara terpisah:

<br>

## Kode `print123thread.c`

```bash
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

void *print1(void *arg) {
    printf("1\n");
    return NULL;
}

void *print2(void *arg) {
    printf("2\n");
    return NULL;
}

void *print3(void *arg) {
    printf("3\n");
    return NULL;
}

int main() {
    pthread_t t1, t2, t3;

    pthread_create(&t1, NULL, print1, NULL);
    pthread_create(&t2, NULL, print2, NULL);
    pthread_create(&t3, NULL, print3, NULL);

    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
    pthread_join(t3, NULL);

    return 0;
}
```

<br>

## Thread 1 (`t1`) — Mencetak Angka 1

- Thread ini menjalankan fungsi yang mencetak angka 1 ke layar.
- Thread ini biasanya dianggap sebagai thread pertama yang harus selesai sebelum thread berikutnya berjalan, terutama jika disinkronkan.
- Jika terdapat mekanisme sinkronisasi (misalnya menggunakan mutex atau condition variable), maka thread ini bisa menjadi trigger untuk membangunkan thread 2.

<br>

## Thread 2 (t2) — Mencetak Angka 2

- Bertugas untuk mencetak angka 2.
- Bergantung pada logika kode, bisa jadi thread ini hanya akan mencetak setelah thread 1 selesai.
- Jika tidak ada sinkronisasi eksplisit, urutan pencetakan bisa tidak menentu.

<br>

## Thread 3 (t3) — Mencetak Angka 3

- Thread ini mencetak angka 3.
- Sama seperti thread lainnya, bisa jadi berjalan sebelum atau sesudah yang lain tergantung pada jadwal CPU.

<br>

## Mekanisme Sinkronisasi (Jika Ada)

- Jika kode menggunakan mutex, semaphore, atau condition variable, maka pencetakan angka akan tertib sesuai urutan yang diinginkan: 1 → 2 → 3.
- Jika tidak ada sinkronisasi, maka hasil output bisa acak tergantung pada bagaimana OS menjadwalkan thread-thread tersebut.

<br>

## Contoh Output (Tanpa Sinkronisasi)

```
3
1
2

```

### atau

```
1
2
3
```

### Contoh Output (Dengan Sinkronisasi)

```
1
2
3
```

<br>

## Kesimpulan

- Ketiga thread berjalan secara konkuren.
- Urutan hasil bisa dikontrol hanya jika ada mekanisme sinkronisasi.
- Tanpa kontrol, hasil akhir bisa berbeda setiap kali dijalankan.