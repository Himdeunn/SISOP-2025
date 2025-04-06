# Penjelasan tentang Forking dan Analisis Kode

<br>

## Apa itu Forking?

Forking adalah proses di mana sebuah parent process membuat salinan dirinya sendiri, yang disebut child process. Ini dilakukan menggunakan sistem call `fork()` dalam bahasa C. Setelah `fork()` dipanggil, dua proses akan berjalan secara independen: satu dengan ID proses asli (induk), dan satu lagi dengan ID baru (anak). Keduanya melanjutkan eksekusi dari titik setelah `fork()` dipanggil.

<br>

## Cara Melakukan Forking di C

```bash
#include <stdio.h>
#include <unistd.h>

int main() {
    pid_t pid = fork();

    if (pid < 0) {
        perror("Fork gagal");
        return 1;
    } else if (pid == 0) {
        printf("Ini adalah proses anak dengan PID %d\n", getpid());
    } else {
        printf("Ini adalah proses induk dengan PID %d dan anak dengan PID %d\n", getpid(), pid);
    }

    return 0;
}
```

### Dalam contoh di atas:

- `fork()` dipanggil untuk membuat proses anak.
- Jika pid bernilai negatif, berarti terjadi kesalahan saat forking.
- Jika pid bernilai 0, maka kode sedang dieksekusi dalam proses anak.
- Jika pid bernilai positif, maka kode sedang dieksekusi dalam proses induk, dan pid tersebut adalah ID dari proses anak.

<br>

## Apakah Kode di `print123thread.c` Menggunakan Fork?

Tidak. Kode pada [print123thread.c](https://github.com/ferryastika/SisOp-24/blob/main/print123thread.c) menggunakan threading (bukan forking) dengan pustaka pthread untuk menjalankan 3 thread secara sinkron.

<br>

## Analisis Kode pada `print123thread.c`

Setelah meninjau kode yang terdapat pada tautan tersebut, ternyata kode tersebut tidak menggunakan mekanisme forking (`fork()`), melainkan menggunakan threading dengan pustaka pthread untuk mencetak angka 1, 2, dan 3 secara bergantian tanpa henti. Berikut adalah penjelasan langkah kerjanya:

1. Inisialisasi: Kode mengimpor pustaka yang diperlukan dan mendeklarasikan variabel global, termasuk mutex (`pthread_mutex_t`) dan variabel kondisi (`pthread_cond_t`) untuk sinkronisasi antar thread.

2. Variabel Global:
   1. `pthread_mutex_t lock`: Mutex untuk menghindari kondisi balapan (race condition).
   2. `pthread_cond_t cond1, cond2, cond3`: Variabel kondisi untuk sinkronisasi antar thread.
   3. `int done = 1`: Menentukan thread mana yang seharusnya aktif.

3. Fungsi Thread (`foo`):
   1. Fungsi ini menerima argumen berupa pointer ke integer yang menunjukkan nomor thread (1, 2, atau 3).
   2. Dalam loop tak hingga, thread akan mencoba mengunci mutex.
   3. Jika nilai `done` tidak sesuai dengan nomor thread, thread akan menunggu pada variabel kondisi yang sesuai.
   4. Jika nilai `done` sesuai, thread akan mencetak nomornya, memperbarui nilai `done` ke thread berikutnya, dan memberi sinyal ke variabel kondisi thread berikutnya.****
   5. Setelah itu, mutex dilepas.

4. Fungsi `main`:
   1. Membuat tiga thread (`tid1`, `tid2`, `tid3`) yang menjalankan fungsi `foo` dengan argumen masing-masing 1, 2, dan 3.
   2. Thread utama menunggu ketiga thread selesai dengan memanggil `pthread_join`.