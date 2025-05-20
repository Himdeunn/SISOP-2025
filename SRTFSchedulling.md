# Analisis Algoritma Penjadwalan: SRTF vs SJF

Dalam dokumen ini, saya akan membahas dua hal secara **terpisah** agar lebih mudah dipahami:

<br>

## 🔍 Bagian 1: Analisis Output Gambar — **SRTF (Preemptive)**

Gambar yang kamu lampirkan menunjukkan hasil dari algoritma **Shortest Remaining Time First (SRTF)**. Berikut detailnya:

### **Input Proses:**

| Process | Arrival Time (AT) | Burst Time (BT) |
| ------- | ----------------- | --------------- |
| P1      | 0                 | 7               |
| P2      | 2                 | 4               |
| P3      | 4                 | 1               |
| P4      | 5                 | 4               |

### **Cara Kerja Algoritma SRTF:**

* SRTF adalah versi **preemptive** dari algoritma SJF.
* Di setiap unit waktu, CPU memilih proses dengan **sisa waktu eksekusi (burst time) paling sedikit**.
* Proses baru bisa **menginterupsi proses yang sedang berjalan** jika memiliki burst time yang lebih kecil.

### **Simulasi Langkah CPU:**

1. **t = 0** → P1 dieksekusi (hanya dia yang tersedia).
2. **t = 2** → P2 datang. Sisa waktu P1 = 5, BT P2 = 4 → **P2 menggantikan P1**.
3. **t = 4** → P3 datang. Sisa waktu P2 = 2, BT P3 = 1 → **P3 menggantikan P2**.
4. **t = 5** → P3 selesai. P4 datang. Tersisa: P1=5, P2=2, P4=4 → **P2 dipilih**.
5. **t = 7** → P2 selesai.
6. **t = 7** → Bandingkan P1 (sisa 5) dan P4 (BT 4) → **P4 dipilih**.
7. **t = 11** → P4 selesai.
8. **t = 11** → **P1 dilanjutkan**.
9. **t = 16** → P1 selesai.

### **Perhitungan TAT (Turnaround Time) dan WT (Waiting Time):**

| Process | AT | BT | CT | TAT = CT-AT | WT = TAT-BT |
| ------- | -- | -- | -- | ----------- | ----------- |
| P3      | 4  | 1  | 5  | 1           | 0           |
| P2      | 2  | 4  | 7  | 5           | 1           |
| P4      | 5  | 4  | 11 | 6           | 2           |
| P1      | 0  | 7  | 16 | 16          | 9           |

📌 **Rata-rata:**

* Turnaround Time = (1 + 5 + 6 + 16) / 4 = **7.00**
* Waiting Time = (0 + 1 + 2 + 9) / 4 = **3.00**

<br>

## 🧠 Bagian 2: Analisis Source Code — **SJF Non-Preemptive**

Sekarang mari kita lihat source code C milikmu yang menggunakan **SJF Non-Preemptive**.

### 🔧 Struktur Program:

```c
struct proc {
    int no, at, bt, it, ct, tat, wt;
};
```

* `no`: nomor proses
* `at`: waktu kedatangan (arrival time)
* `bt`: burst time (lama proses)
* `it`: waktu mulai eksekusi (initial time)
* `ct`: waktu selesai (completion time)
* `tat`: turnaround time
* `wt`: waiting time

### 🧭 Alur Kerja Program:

1. **Input jumlah dan data proses**, disimpan dalam array `p[10]`.

2. **Sortir berdasarkan Arrival Time (AT):**

   ```c
   for (int i = 0; i < n-1; i++)
       for (j = 0; j < n-i-1; j++)
           if (p[j].at > p[j+1].at)
               swap(p[j], p[j+1]);
   ```

3. **Jika beberapa proses datang bersamaan, pilih burst time terkecil:**

   ```c
   for (j = 1; j < n && p[j].at == p[0].at; j++)
       if (p[j].bt < p[min].bt)
           min = j;
   ```

4. **Tentukan waktu mulai (`it`) dan selesai (`ct`) untuk setiap proses:**

   * Jika proses datang **sebelum proses sebelumnya selesai**, maka dimulai setelah proses sebelumnya selesai (`it = prev.ct`).
   * Jika datang **setelah proses sebelumnya selesai**, maka langsung dimulai saat datang (`it = at`).

   ```c
   if (p[i].at <= p[i-1].ct)
       p[i].it = p[i-1].ct;
   else
       p[i].it = p[i].at;
   p[i].ct = p[i].it + p[i].bt;
   ```

5. **Hitung Turnaround Time dan Waiting Time:**

   ```c
   p[i].tat = p[i].ct - p[i].at;
   p[i].wt = p[i].tat - p[i].bt;
   ```

<br>

## ⚠️ Perbedaan Utama:

| Aspek                   | Output Gambar (SRTF) | Kode Program (SJF Non-Preemptive)          |
| ----------------------- | -------------------- | ------------------------------------------ |
| Jenis Algoritma         | Preemptive (SRTF)    | Non-Preemptive (SJF)                       |
| Proses Bisa Diinterupsi | Ya                   | Tidak                                      |
| Penjadwalan tiap unit   | Ya (dinamis)         | Tidak (langsung dijalankan sampai selesai) |

<br>

🧑‍💻 6. Output Kode

<img src="./img/SRTF-SchedullingAlgorithms.png"></img>