# Programming Exercises

<br>

## a. Penerapan Thread pada `SumTask.java`

Contoh `SumTask.java` adalah ilustrasi yang bagus tentang bagaimana Java menggunakan thread untuk mempercepat proses komputasi. Dalam program ini, tugas menjumlahkan elemen-elemen dari sebuah array besar dibagi ke dalam beberapa bagian, dan setiap bagian dihitung oleh thread yang berbeda. Kelas `SumTask` mengimplementasikan `Runnable`, yang artinya objeknya bisa dijalankan dalam thread. Dengan membagi pekerjaan ke beberapa thread, program bisa berjalan lebih cepat karena dapat memanfaatkan prosesor multi-core untuk menghitung beberapa bagian secara paralel.

Keuntungan dari pendekatan ini adalah efisiensi dan peningkatan performa, terutama untuk tugas-tugas berat seperti perhitungan dalam jumlah besar. Tapi perlu diperhatikan, penggunaan thread juga membawa tantangan seperti potensi konflik data. Dalam kasus ini, koordinasi antar thread dijaga agar hasil perhitungan tetap benar dan tidak saling tumpang tindih.

<br>

## b. Penerapan Thread di Linux (`thrd-posix.c`) dan Microsoft Windows (`thrd-win32.c`)

Contoh `thrd-posix.c` dan `thrd-win32.c` menunjukkan cara penggunaan thread di dua sistem operasi yang berbeda: Linux dan Windows. Di `thrd-posix.c`, threading dilakukan menggunakan pustaka POSIX (pthreads), yang merupakan standar di sistem operasi berbasis Unix. Thread dibuat dengan fungsi `pthread_create`, lalu bekerja menjalankan fungsi tertentu. Untuk mencegah konflik saat mengakses data bersama, program ini menggunakan mutex sebagai mekanisme sinkronisasi.

Sementara itu, di `thrd-win32.c`, proses pembuatan thread menggunakan fungsi dari Windows API seperti `CreateThread`. Meskipun tujuannya sama, yaitu menjalankan beberapa proses secara paralel, caranya berbeda sesuai dengan sistem operasi. Perbedaan ini penting untuk dipahami karena setiap OS punya gaya dan cara sendiri dalam mengatur thread, meskipun prinsip dasarnya tetap sama: membagi tugas agar bisa dikerjakan lebih efisien secara bersamaan.