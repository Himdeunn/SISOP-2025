# References Indonesian Thread, Task Number 3-4

## 2.11.1. Proses

### 3. Jelaskan tindakan yang diambil oleh sebuah kernel ketika alih konteks antar proses.
Alih konteks (context switching) adalah proses ketika sistem operasi menyimpan status proses yang sedang berjalan agar dapat dilanjutkan kembali, dan memuat status proses lain yang sebelumnya dihentikan. Tindakan yang dilakukan oleh kernel mencakup:
- Menyimpan konteks proses saat ini, seperti isi register CPU dan program counter.
- Memperbarui Process Control Block (PCB) dari proses yang disimpan.
- Memuat konteks dari proses baru yang akan dijalankan.
- Memperbarui data manajemen memori bila diperlukan.
- Mengatur ulang register CPU untuk proses baru.

### 4. Informasi apa saja yang disimpan pada tabel proses saat alih konteks dari satu proses ke proses lain.
Informasi yang disimpan pada tabel proses (Process Control Block/PCB) saat alih konteks meliputi:
- Register CPU (general purpose dan special purpose)
- Program Counter (alamat instruksi selanjutnya)
- Stack Pointer
- Informasi status proses (ready, running, waiting, dll)
- Informasi manajemen memori (base dan limit register, page table)
- Informasi akun (UID, GID, kuota, waktu CPU)
- Informasi I/O dan file yang digunakan

---

## 2.11.2. Thread

### 3. Sebutkan dua perbedaan antara user level thread dan kernel thread. Saat kondisi bagaimana salah satu dari thread tersebut lebih baik.
| Perbedaan                   | User-Level Thread                          | Kernel-Level Thread                       |
|----------------------------|--------------------------------------------|-------------------------------------------|
| Manajemen Thread           | Diatur oleh pustaka pengguna               | Diatur langsung oleh kernel               |
| Overhead Context Switching | Lebih cepat (tidak perlu interupsi kernel) | Lebih lambat (butuh interupsi kernel)     |

**Kapan lebih baik:**
- *User-level thread* lebih baik digunakan saat aplikasi memerlukan banyak thread ringan dan efisien, tanpa sering menggunakan blocking system call.
- *Kernel-level thread* lebih baik digunakan ketika thread perlu memanfaatkan banyak CPU secara paralel (multi-core).

### 4. Jelaskan tindakan yang diambil oleh sebuah kernel saat alih konteks antara kernel level thread.
Saat alih konteks antar kernel-level thread, kernel akan melakukan:
- Menyimpan register dan program counter thread lama ke struktur PCB/Teknik data thread.
- Memuat kembali nilai register dan program counter dari thread baru.
- Memperbarui scheduler kernel untuk menentukan thread aktif selanjutnya.
- Memastikan konsistensi memori, termasuk cache dan TLB (Translation Lookaside Buffer) bila diperlukan.

---

## 2.11.3. Penjadualan CPU

### 3. Apakah keuntungan menggunakan time quantum size di level yang berbeda dari sebuah antrian sistem multilevel?
Keuntungan penggunaan time quantum berbeda di sistem multilevel queue antara lain:
- Menyesuaikan prioritas dan jenis proses: Proses interaktif bisa diberi quantum kecil untuk respons cepat, sedangkan proses batch diberi quantum besar agar efisien.
- Menghindari starvation: Proses dengan prioritas rendah tetap mendapat kesempatan dieksekusi.
- Meningkatkan efisiensi CPU: Proses berat tidak terlalu sering berpindah konteks (overhead berkurang).
- Fleksibilitas tinggi: Dapat disesuaikan dengan kebutuhan spesifik tiap level queue.

### 4. Ilustrasi Eksekusi Proses (Gantt Chart)

**Diketahui:**

| Proses | Burst Time | Prioritas |
|--------|------------|-----------|
| P1     | 10         | 3         |
| P2     | 1          | 1         |
| P3     | 2          | 4         |
| P4     | 1          | 4         |
| P5     | 5          | 2         |

**Asumsi: Semua proses datang di t = 0**

#### a) FCFS (First Come First Serve)
Gantt Chart:  
`P1 | P2 | P3 | P4 | P5`  
Waktu:  
`0   10  11  13  14  19`

#### b) SJF (Shortest Job First)
Urutan berdasarkan burst time: P2 (1), P4 (1), P3 (2), P5 (5), P1 (10)  
Gantt Chart:  
`P2 | P4 | P3 | P5 | P1`  
Waktu:  
`0   1   2   4   9   19`

#### c) Prioritas Non-Preemptive
Urutan prioritas (semakin kecil = lebih tinggi):  
P2 (1), P5 (2), P1 (3), P3/P4 (4)  
Gantt Chart:  
`P2 | P5 | P1 | P3 | P4`  
Waktu:  
`0   1   6   16  18  19`

#### d) Round Robin (Quantum = 2)
Awal: [P1(10), P2(1), P3(2), P4(1), P5(5)]  
Gantt Chart:  
`P1 | P2 | P3 | P4 | P5 | P1 | P5 | P1 | P5 | P1 | P1`  
Waktu:  
`0   2   3   5   6   8   10  12  13  15  17  19`

---

