# Perbedaan Multiprogramming vs Multitasking

## 1. Multiprogramming
Multiprogramming adalah teknik di mana beberapa program dimuat ke dalam memori utama dan dieksekusi secara bergantian oleh CPU. Sistem operasi akan memilih program yang siap dieksekusi dan menggantinya dengan program lain ketika program sebelumnya sedang menunggu operasi input/output (I/O). Ini meningkatkan efisiensi CPU karena CPU tidak menganggur saat satu program menunggu proses I/O.

**Contoh:**
Saat kita menjalankan beberapa program dalam sistem operasi berbasis batch, seperti satu program sedang mencetak dokumen sementara program lain sedang melakukan perhitungan.

**Ciri-ciri Multiprogramming:**
- CPU selalu memiliki tugas untuk dikerjakan.
- Tidak ada eksekusi program secara bersamaan, tetapi terjadi pergantian cepat antar program.
- Digunakan pada sistem operasi lama seperti batch processing.

<br>
<br>
<br>

## 2. Multitasking
Multitasking adalah teknik di mana beberapa tugas atau proses dapat dijalankan secara bersamaan dengan membagi waktu CPU secara cepat di antara tugas-tugas tersebut (time-sharing). Setiap proses diberikan sejumlah kecil waktu CPU (quantum), sehingga pengguna merasa seolah-olah semua proses berjalan secara bersamaan.

**Contoh:**
Saat kita membuka dan menggunakan browser, mendengarkan musik, dan mengetik di Microsoft Word secara bersamaan pada komputer modern.

**Ciri-ciri Multitasking:**
- Beberapa proses dapat berjalan secara bersamaan dalam sistem operasi.
- Menggunakan konsep **time-sharing**, di mana CPU berpindah antar proses dengan sangat cepat.
- Digunakan dalam sistem operasi modern seperti Windows, Linux, dan macOS.

<br>
<br>
<br>

## Perbedaan Utama

| **Aspek**          | **Multiprogramming** | **Multitasking** |
|--------------------|---------------------|------------------|
| **Konsep Dasar**   | Beberapa program dimuat ke memori dan dieksekusi secara bergantian. | Beberapa program berjalan secara bersamaan dengan pembagian waktu CPU. |
| **Eksekusi**       | Bergantian (tidak bersamaan). | Seolah-olah berjalan bersamaan. |
| **Penggunaan CPU** | CPU tidak menganggur, tetapi hanya satu program yang berjalan dalam satu waktu. | CPU berganti-ganti tugas dengan cepat sehingga beberapa program bisa berjalan sekaligus. |
| **Contoh Penggunaan** | Sistem batch processing. | Sistem operasi modern dengan GUI. |

Jadi, **multiprogramming** lebih fokus pada efisiensi CPU dalam menjalankan beberapa program tanpa eksekusi simultan, sementara **multitasking** memungkinkan banyak proses berjalan secara bersamaan dengan berbagi waktu CPU.

