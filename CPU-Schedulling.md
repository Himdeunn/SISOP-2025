# ANALYSIS ABOUT CODE FSCS SCHEDULLING ALGORITM WITH ARRIVAL TIME AND WITHOUT ARRIVAL TIME

| NO                   | NAMA                          | NRP                       | KELAS                          |
|----------------------------|--------------------------------------------|-------------------------------------------|-------------------------------------------|
| 1 | TEGAR APRILIAN WIBOWO | 3124500049 | 1 D3 IT B |
| 2 | MUHAMMAD YOGA ANANDA SATRIA  | 3124500039 | 1 D3 IT B |
| 3 | AQILAH SALAMATUDDIN | 3124500054 | 1 D3 IT B |

<br>
<br>
<br>

# RINGKASAN KODE FSCS SCHEDULLING ALGORITHM WITHOUT ARRIVAL TIME 

Kode yang dianalisis mengimplementasikan algoritma penjadwalan FCFS (First-Come, First-Served) tanpa waktu kedatangan (non-preemptive). Algoritma ini merupakan salah satu algoritma penjadwalan CPU yang paling sederhana, di mana proses dieksekusi sesuai dengan urutan kedatangannya.

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
    printf("<--FCFS Scheduling Algorithm Without Arrival Time (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
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

## Struktur Data

Kode menggunakan struktur data `proc` yang mendefinisikan:

- `no`: Nomor proses
- `bt`: Burst Time (waktu eksekusi yang dibutuhkan proses)
- `ct`: Completion Time (waktu penyelesaian proses)
- `tat`: Turn Around Time (waktu total dari awal hingga selesai)
- `wt`: Waiting Time (waktu menunggu sebelum dieksekusi)

## Alur Program

1. Program meminta pengguna memasukkan jumlah proses (`n`)
2. Untuk setiap proses, program meminta waktu eksekusi (Burst Time)
3. Program menghitung:
   - Completion Time (CT) untuk setiap proses
   - Turn Around Time (TAT) untuk setiap proses
   - Waiting Time (WT) untuk setiap proses
4. Program mencetak tabel hasil dan rata-rata TAT dan WT

## Perhitungan Metrik

Algoritma menghitung metrik-metrik penting dalam penjadwalan proses:

1. **Completion Time (CT)**: Waktu ketika suatu proses selesai dieksekusi
   - Dihitung dengan menjumlahkan burst time semua proses sebelumnya dan burst time proses saat ini
   - `ct += p[i].bt`

2. **Turn Around Time (TAT)**: Waktu total dari awal hingga proses selesai dieksekusi
   - Dalam kode ini, TAT sama dengan CT karena arrival time dianggap 0 untuk semua proses
   - `p[i].tat = p[i].ct`

3. **Waiting Time (WT)**: Waktu total proses menunggu di ready queue
   - Dihitung dengan rumus: `WT = TAT - BT`
   - `p[i].wt = p[i].tat - p[i].bt`

4. **Response Time (RT)**: Waktu dari kedatangan proses hingga eksekusi pertama
   - Dalam kode ini, RT sama dengan WT karena tidak ada preemption

## Kelebihan dan Kekurangan Algoritma FCFS

### Kelebihan:
- Sederhana dan mudah diimplementasikan
- Tidak ada starvation (semua proses pasti akan dieksekusi)
- Adil berdasarkan urutan kedatangan

### Kekurangan:
- Efek konvoi: jika proses awal memiliki burst time panjang, semua proses di belakangnya harus menunggu
- Tidak optimal dalam meminimalkan waktu tunggu
- Tidak cocok untuk sistem interaktif atau real-time

## Observasi Tambahan

1. Kode ini tidak memperhitungkan arrival time (waktu kedatangan), sehingga diasumsikan semua proses tiba pada waktu 0
2. Variabel `tmp` dideklarasikan tetapi tidak digunakan
3. Dalam output, Response Time (RT) ditampilkan sama dengan Waiting Time (WT), yang benar untuk algoritma FCFS tanpa preemption
4. Kode membatasi jumlah maksimal proses hingga 10 (`struct proc p[10]`)

## Contoh Perhitungan

Misalkan ada 3 proses dengan burst time: P1=5, P2=3, P3=8

Maka perhitungannya:
- P1: CT=5, TAT=5, WT=0
- P2: CT=8, TAT=8, WT=5
- P3: CT=16, TAT=16, WT=8

Rata-rata TAT = (5+8+16)/3 = 9.67
Rata-rata WT = (0+5+8)/3 = 4.33

## Kesimpulan

Kode tersebut merupakan implementasi dasar dari algoritma penjadwalan FCFS yang mengasumsikan semua proses tiba bersamaan (arrival time = 0). Algoritma ini paling sederhana namun tidak selalu efisien karena dapat menyebabkan waktu tunggu yang lama jika proses dengan burst time besar dieksekusi lebih dulu.

<br>
<br>

# RINGKASAN KODE FSCS SCHEDULLING ALGORITHM WITH ARRIVAL TIME 

## Ringkasan Kode

Kode ini mengimplementasikan algoritma penjadwalan FCFS (First-Come, First-Served) dengan mempertimbangkan waktu kedatangan (arrival time). Algoritma ini mengeksekusi proses sesuai dengan urutan kedatangannya, di mana proses yang tiba lebih dulu akan dieksekusi terlebih dahulu.

```c
#include<stdio.h>
struct proc
{
    int no,at,bt,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Arrival Time: ");
    scanf("%d",&p.at);
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    return p;
}
int main()
{
    struct proc p[10],tmp;
    float avgtat=0,avgwt=0;
    int n,ct=0;
    printf("<--FCFS Scheduling Algorithm (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)    
            if(p[j].at>p[j+1].at)
            {
            tmp=p[j];
            p[j]=p[j+1];
            p[j+1]=tmp;
            }
    printf("\nProcessNo\tAT\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        ct+=p[i].bt;
		p[i].ct=ct;
        p[i].tat=p[i].ct-p[i].at;
        avgtat+=p[i].tat;
        p[i].wt=p[i].tat-p[i].bt;
        avgwt+=p[i].wt;
        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\t%d\n",p[i].no,p[i].at,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].wt);
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}
```

## Struktur Data

Kode menggunakan struktur data `proc` yang mendefinisikan:

- `no`: Nomor proses
- `at`: Arrival Time (waktu kedatangan proses)
- `bt`: Burst Time (waktu eksekusi yang dibutuhkan proses)
- `ct`: Completion Time (waktu penyelesaian proses)
- `tat`: Turn Around Time (waktu total dari kedatangan hingga selesai)
- `wt`: Waiting Time (waktu menunggu sebelum dieksekusi)

## Alur Program

1. Program meminta pengguna memasukkan jumlah proses (`n`)
2. Untuk setiap proses, program meminta waktu kedatangan (Arrival Time) dan waktu eksekusi (Burst Time)
3. **Sorting**: Program mengurutkan proses berdasarkan waktu kedatangan (Arrival Time) menggunakan algoritma Bubble Sort
4. Program menghitung:
   - Completion Time (CT) untuk setiap proses
   - Turn Around Time (TAT) untuk setiap proses
   - Waiting Time (WT) untuk setiap proses
5. Program mencetak tabel hasil dan rata-rata TAT dan WT

## Perhitungan Metrik

Algoritma menghitung metrik-metrik penting dalam penjadwalan proses:

1. **Completion Time (CT)**: Waktu ketika suatu proses selesai dieksekusi
   - Dihitung dengan menambahkan burst time proses saat ini ke CT sebelumnya
   - `ct += p[i].bt`

2. **Turn Around Time (TAT)**: Waktu total dari kedatangan hingga proses selesai dieksekusi
   - Dihitung dengan rumus: `TAT = CT - AT`
   - `p[i].tat = p[i].ct - p[i].at`

3. **Waiting Time (WT)**: Waktu total proses menunggu di ready queue
   - Dihitung dengan rumus: `WT = TAT - BT`
   - `p[i].wt = p[i].tat - p[i].bt`

4. **Response Time (RT)**: Waktu dari kedatangan proses hingga eksekusi pertama
   - Dalam kode ini, RT sama dengan WT karena tidak ada preemption

## Analisis Algoritma Pengurutan

Kode menggunakan algoritma Bubble Sort untuk mengurutkan proses berdasarkan waktu kedatangan:

```c
for(int i=0;i<n-1;i++)
    for(int j=0;j<n-i-1;j++)    
        if(p[j].at>p[j+1].at)
        {
            tmp=p[j];
            p[j]=p[j+1];
            p[j+1]=tmp;
        }
```

Kompleksitas waktu algoritma ini adalah O(n²), yang cukup untuk jumlah proses yang kecil tetapi tidak efisien untuk jumlah proses yang besar.

## Masalah Potensial dalam Kode

1. **Idle Time Tidak Diperhitungkan**: Kode ini memiliki kelemahan karena tidak memperhitungkan idle time CPU ketika tidak ada proses yang tersedia. Jika terdapat jeda antara completion time terakhir dan arrival time proses berikutnya, algoritma seharusnya menyesuaikan completion time.

   Contoh masalah:
   - Jika P1 selesai pada t=5, tetapi P2 baru tiba pada t=8, maka CT P2 seharusnya dimulai dari t=8, bukan t=5.
   
   Solusi yang benar:
   ```c
   for(int i=0;i<n;i++)
   {
       if(i==0 || ct<p[i].at)
           ct=p[i].at;
       ct+=p[i].bt;
       // Perhitungan lainnya...
   }
   ```

2. **Response Time**: Response time ditampilkan sama dengan waiting time, yang hanya benar untuk kasus non-preemptive.

## Kelebihan dan Kekurangan Algoritma FCFS dengan Arrival Time

### Kelebihan:
- Sederhana dan mudah diimplementasikan
- Tidak ada starvation (semua proses pasti akan dieksekusi)
- Adil berdasarkan urutan kedatangan

### Kekurangan:
- Efek konvoi: jika proses awal memiliki burst time panjang, semua proses di belakangnya harus menunggu
- Tidak optimal dalam meminimalkan waktu tunggu
- Tidak cocok untuk sistem interaktif karena proses dengan burst time pendek bisa terjebak di belakang proses dengan burst time panjang

## Contoh Perhitungan (Dengan Koreksi untuk Idle Time)

Misalkan ada 3 proses dengan:
- P1: AT=0, BT=5
- P2: AT=3, BT=3
- P3: AT=9, BT=8

Perhitungan yang benar (dengan mempertimbangkan idle time):
- P1: CT=5, TAT=5, WT=0
- P2: CT=8, TAT=5, WT=2
- P3: CT=17, TAT=8, WT=0

Namun, dengan implementasi kode saat ini, kita akan mendapatkan:
- P1: CT=5, TAT=5, WT=0
- P2: CT=8, TAT=5, WT=2
- P3: CT=16, TAT=7, WT=-1 (hasil yang salah karena idle time tidak diperhitungkan)

## Saran Perbaikan

1. Perbaiki perhitungan completion time untuk menangani idle time:
   ```c
   if(i==0)
       ct = p[i].at + p[i].bt;
   else
       ct = (ct > p[i].at) ? ct + p[i].bt : p[i].at + p[i].bt;
   ```

2. Pertimbangkan untuk menampilkan idle time CPU dalam output untuk analisis yang lebih lengkap

3. Tambahkan komentar untuk memperjelas alur algoritma

## Kesimpulan

Kode ini mengimplementasikan algoritma penjadwalan FCFS dengan mempertimbangkan waktu kedatangan, namun memiliki kelemahan dalam menangani idle time CPU. Algoritma FCFS sederhana untuk diimplementasikan tetapi tidak selalu optimal dalam hal kinerja, terutama jika terdapat proses dengan burst time yang besar di awal urutan.

<br>
<br>

# PERBANDINGAN ANTARA PAKAI ARRIVAL TIME DENGAN YANG TIDAK PAKAI ARRIVAL TIME

    Dibawah ini adalah foto berupa perbandingan FSCS tanpa waktu kedatangan dan FSCS waktu kedatangan yang dimana saya lampirkan dengan sebuah lampiran sebuah gambar. Berikut gambarnya :


## FSCS ALGORITHM WITHOUT ARRIVAL TIME
<img src="./img/FSCS-WithoutArrivalTime.jpg"></img>

## FSCS ALGORITHM WITH ARRIVAL TIME
<img src="./img/FSCS-WithArrivalTime.jpg"></img>

<br>

### Analisa dari kedua gambar tersebut

1. Gantt Chart
   - Dengan Arrival Time
        ```
        0-8 (P1) | 8-12 (P2) | 12-21 (P3) | 21-26 (P4)
        ```
        Proses dimulai sesuai waktu kedatangan (P1→P2→P3→P4).

   - Tanpa Arrival Time
        ```
        0-8 (P1) | 8-12 (P2) | 12-21 (P3) | 21-26 (P4)
        ```
        Proses dijalankan berurutan (semua dianggap tiba di waktu 0).

2. Perbedaan Utama
    | Metric         | Dengan AT | Tanpa AT |
    |----------------|-----------|----------|
    | Rata-rata TAT  | 15.25     | 16.75    |
    | Rata-rata WT   | 8.75      | 10.25    |

 - Alasan Perbedaan:
   - Dengan AT: Proses tidak harus menunggu sejak waktu 0 (misal, P2 mulai di 8, bukan 0).
   - Tanpa AT: Proses belakangan (P4) menunggu lebih lama karena dianggap tiba di 0.


3. Kesimpulan
   - Dengan AT lebih efisien karena waktu tunggu dan TAT lebih rendah.
   - Tanpa AT meningkatkan waktu tunggu untuk proses yang sebenarnya "datang belakangan".