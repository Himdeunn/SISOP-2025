# Sistem Bilangan, Desimal, Biner, Oktal, dan Heksadesimal

**Nama** : Tegar Aprilian Wibowo  
**NRP** : 3124500049  
**Kelas** : 1 D3 IT B  

---

# Latihan

## 1. 

- **Bilangan biner** adalah bilangan yang berbasis **dua**.
- **Bilangan heksadesimal** adalah bilangan yang berbasis **enam belas**.

---

## 2. Konversikan bilangan desimal ke bilangan biner

### Soal:
- a. 1234<sub>10</sub>
- b. 5670<sub>10</sub>
- c. 2321<sub>10</sub>

### Jawaban:

#### a. 1234<sub>10</sub>

| Bilangan | Dibagi dengan 2 | Hasil | Sisa |
|----------|----------------|-------|------|
| 1234     | 2              | 617   | 0    |
| 617      | 2              | 308   | 1    |
| 308      | 2              | 154   | 0    |
| 154      | 2              | 77    | 0    |
| 77       | 2              | 38    | 1    |
| 38       | 2              | 19    | 0    |
| 19       | 2              | 9     | 1    |
| 9        | 2              | 4     | 1    |
| 4        | 2              | 2     | 0    |
| 2        | 2              | 1     | 0    |
| 1        | 2              | 0     | 1    |

Jadi, jawabannya adalah **10011010010<sub>2</sub>**.

---

## 3. Konversikan bilangan biner ke bilangan desimal

### Soal:
- a. 10101010
- b. 01010101
- c. 11001100
- d. 10011111

### Jawaban:

| No  | Bilangan Biner | Desimal |
|-----|---------------|---------|
| a   | 10101010      | 170     |
| b   | 01010101      | 85      |
| c   | 11001100      | 204     |
| d   | 10011111      | 159     |

#### a. 10101010

Perhitungan:
```
1 x (128) + 0 x (64) + 1 x (32) + 0 x (16)  + 1 x (8) + 0 x (4) + 1 x (2) + 0 x (1) = 170
```

---

## 4. Konversikan bilangan biner ke bilangan oktal

### Soal:
- a. 101011111001<sub>2</sub>
- b. 110010110111<sub>2</sub>

### Jawaban:

| Bilangan Biner | Bilangan Oktal |
|---------------|---------------|
| 110<sub>2</sub> 010<sub>2</sub> 110<sub>2</sub> 111<sub>2</sub> | 6267<sub>8</sub> |

---

## 5. Konversikan bilangan oktal ke bilangan biner

### Soal:
- a. 2170<sub>8</sub>
- b. 3571<sub>8</sub>

### Jawaban:

#### a. 2170<sub>8</sub>

| Bilangan Oktal | Bilangan Biner |
|---------------|---------------|
| 2<sub>8</sub> | 010<sub>2</sub> |
| 1<sub>8</sub> | 001<sub>2</sub> |
| 7<sub>8</sub> | 111<sub>2</sub> |
| 0<sub>8</sub> | 000<sub>2</sub> |

Jadi, jawabannya adalah **010001111000<sub>2</sub>**.

---

## 6. Konversikan bilangan desimal ke bilangan heksadesimal

### Soal:
- a. 1780<sub>10</sub>
- b. 3666<sub>10</sub>
- c. 5230<sub>10</sub>
- d. 6744<sub>10</sub>

### Jawaban:

#### c. 5230<sub>10</sub>

| Bilangan Desimal | Dibagi dengan 16 | Hasil | Sisa | Heksadesimal |
|------------------|------------------|-------|------|-------------|
| 5230            | 16               | 326   | 14   | E           |
| 326             | 16               | 20    | 6    | 6           |
| 20              | 16               | 1     | 4    | 4           |
| 1               | 16               | 0     | 1    | 1           |

Jadi, jawabannya adalah **146E<sub>16</sub>**.

---

## 7. Konversikan bilangan heksadesimal ke bilangan desimal

### Soal:
- a. ABCD<sub>16</sub>
- b. 2170<sub>16</sub>
- c. B75F<sub>16</sub>
- d. EBED<sub>16</sub>

### Jawaban:

#### b. 2170<sub>16</sub>

| Bilangan Heksadesimal | Perhitungan       | Hasil |
|----------------------|-------------------|------|
| 2                    | 2 x (16³)        | 8192 |
| 1                    | 1 x (16²)        | 256  |
| 7                    | 7 x (16¹)        | 112  |
| 0                    | 0 x (16⁰)        | 0    |

Jadi, jawabannya adalah **8560<sub>10</sub>**.

---

## 8. Konversikan bilangan pecahan desimal ke bilangan biner

### Soal:
- a. 0,3125<sub>10</sub>
- b. 0,65625<sub>10</sub>
- c. 0,34375<sub>10</sub>
- d. 0,140625<sub>10</sub>

### Jawaban:

#### a. 0,3125<sub>10</sub>

| Pecahan Desimal | Dikali dengan 2 | Hasil | Sisa  |
|---------------|---------------|------|------|
| 0,3125       | 2             | 0    | 0,625 |
| 0,625        | 2             | 1    | 0,25  |
| 0,25         | 2             | 0    | 0,5   |
| 0,5          | 2             | 1    | 0     |

Jadi, jawabannya adalah **0,0101<sub>2</sub>**.

---

## 9. Konversikan bilangan desimal ke bilangan biner

- a. 11,625<sub>10</sub>
- b. 0,6875<sub>10</sub>
- c. 0,75<sub>10</sub>
- d. 25,75<sub>10</sub>

### Jawaban dan Cara:

#### d. 25,75<sub>10</sub>

**Jawaban:**

1. Bilangan bulat (25)
   25 / 2 = 12 sisa 1  
   12 / 2 = 6 sisa 0  
   6 / 2 = 3 sisa 0  
   3 / 2 = 1 sisa 1  
   1 / 2 = 0 sisa 1  
   11001<sub>2</sub>

2. Bilangan pecahan (0,75)
   0,75 x 2 = 1 sisa 0,5  
   0,5 x 2 = 1 sisa 0  
   0,11<sub>2</sub>

Jadi, jawabannya adalah 11001,11<sub>2</sub>

---

## 10. Konversikan bilangan desimal di bawah ini ke dalam bilangan heksadesimal

- a. 348,654<sub>10</sub>
- b. 1784,240<sub>10</sub>

### Jawaban dan Cara:

#### b. 1784,240<sub>10</sub>

**Jawaban:**

    1. Bilangan Bulat (1784)
       1784 / 16 = 111 sisa 8 -> 8
       111 / 16 = 6 sisa 15 -> F
       6 / 16 = 0 sisa 6 -> 6
       Hasil: 6F8₁₆

    2. Bilangan Pecahan (0,240)
       0,240 x 16 = 3 -> 3 sisa 0,84
       0,84 x 16 = 13 -> D sisa 0,44
       0,44 x 16 = 7 -> 7 sisa 0,04
       Hasil: 0,3D7₂

Jadi, jawabannya adalah 6F8,3D7₁₆

---

## 11. Konversikan bilangan di bawah ini ke dalam bilangan desimal

- a.  010100011,001111101<sub>2</sub>
- b.  654,276<sub>8</sub>
- c.  4C5,2B8<sub>16</sub>

### Jawaban dan Cara:

#### a.  010100011,001111101<sub>2</sub>

**Jawaban:**

    1. Bilangan Bulat Biner (010100011)
       0 x (256) + 1 x (128) + 0 x (64) + 1 x (32) + 0 x (16) + 0 x (8) + 0 x (4) + 1 x 
       (2) + 1 x (1) = 163₁₀
       Hasil: 163₁₀

    2. Bilangan Pecahan Biner (001111101)
       0 × 2⁻¹ + 0 × 2⁻² + 1 × 2⁻³ + 1 × 2⁻⁴ + 1 × 2⁻⁵ + 1 × 2⁻⁶ + 1 × 2⁻⁷ + 0 × 2⁻⁸ = 0,246
       Hasil: 0,246₁₀

Jadi, jawabannya adalah 163,125₁₀

---

## 12. Rubahlah bilangan biner di bawah ini ke dalam bentuk BCD

- a. 10 1001 1000 0111<sub>2</sub>
- b. 1 0101 0110 0011<sub>2</sub>

### Jawaban dan Cara:

#### a. 10 1001 1000 01112 (BCD)

**Jawaban:**

        0010₂ = 2₁₀
        1001₂ = 9₁₀
        1000₂ = 8₁₀
        0111₂ = 7₁₀

Jadi, jawabannya adalah 2984₁₀ (a)

## 13. Rubahlah bentuk BCD di bawah ini ke dalam bilangan biner 

- a.  1987
- b. 2346
- c. 501

### Jawaban dan Cara:

#### a. 1987

**Jawaban:**

a. 1987₁₀ (BCD)

        1₁₀ = 0001₂
        9₁₀ = 1001₂
        8₁₀ = 1000₂
        7₁₀ = 0111₂

Jadi, jawabannya adalah 0001 1001 1000 0111₂ (a)

---

## 14. Rubahlah bilangan biner di bawah ini ke dalam BCO

- a.  11111101001<sub>2</sub>
- b. 101110 010100<sub>2</sub>
- c. 1100000010<sub>2</sub>

### Jawaban dan Cara:

#### a. 11 111 101 001₂ (BCO)

**Jawaban:**

a. 11 111 101 001₂ (BCO)

    011₂ = 3₈
    111₂ = 7₈
    101₂ = 5₈
    001₂ = 1₈

Jadi, jawabannya adalah 3751₈ (a)

---

## 15. Rubahlah bilangan biner di bawah ini ke dalam BCH

- a. 1101 1111 0010 1110<sub>2</sub>
- b. 110 1001 1000 0001<sub>2</sub>

### Jawaban dan Cara:

#### b. 110 1001 1000 0001<sub>2</sub>

**Jawaban:**

b. 110 1001 1000 0001₂ (BCH)

    0110₂ = 6₁₀ -> 6₁₆
    1001₂ = 9₁₀ -> 9₁₆
    1000₂ = 8₁₀ -> 8₁₆
    0001₂ = 1₁₀ -> ₁₆

Jadi, jawabannya adalah 6981₈ (c)

---

## 16. Rubahlah Bentuk BCH di bawah ini ke dalam bilangan heksadesimal

- a. F0DE
- b. 1CAB
- c. 834

### Jawaban dan Cara:

#### b. 1CAB<sub>16</sub> (BCH)

**Jawaban:**

    1₁₆ = 1₁₀ -> 0001₂
    C₁₆ = 12₁₀ -> 1100₂
    A₁₆ = 10₁₀ -> 1010₂
    B₁₆ = 11₁₀ -> 1011₂

Jadi, jawabannya adalah 0001 1100 1010 1011<sub>2</sub> **(b)**

---

## 17. Nyatakan positip atau negatip bilangan biner di bawah ini

- a. 01111111
- b. 10000000
- c. 01111011

### Jawaban dan Cara:

#### c. 01111011<sub>2</sub>

**Jawaban:**

c. 01111011<sub>2</sub>

    0 = Positif (+)
    111 1011= 123

Jadi, jawabannya adalah Positip 123 (c)

---

## 18. Nyatakan bilangan biner negatip di bawah ini ke dalam bilangan desimal 

- a.  10001000
- b. 11110111
- c. 10000101
- d. 10011100


### Jawaban dan Cara:

#### b. 11110111₂

**Jawaban:**

b. 11110111₂

    1 = Negatif (-)
    111 0111 = 9 (Two’s complement)

Jadi, jawabannya adalah -9 (b)

---

## 19. Nyatakan ASCII Code di bawah ini dalam bentuk karakter 

- a. 41<sub>16</sub>
- b. 5A<sub>16</sub>
- c. 24<sub>16</sub>
- d. 77<sub>16</sub>

### Jawaban dan Cara:

#### c. 24<sub>16</sub>

**Jawaban:**

c. 24₁₆

    2 x 16 + 4 x 1 = 36₁₀ -> ‘$’

Jadi, jawabannya adalah $ (c)

---

## 20. Nyatakan Karakter di bawah ini dalam ASCII Code

- a. a
- b. x
- c. m
- d. H

### Jawaban dan Cara:

#### d. H

**Jawaban:**

d. H = 48₁₆

Jawab:

    4 x 16¹ = 64
    8 x 16⁰ = 8

Total = 72 (H)

---

## 21. Dengan Keyboard standard ASCII, pada layar monitor nampak tulisan sebagai berikut

<p align="center" font="10px"><strong>PRINT X</strong></p>

Nyatakan Keluaran pada Keyboard tersebut.

    P (101 0000)
    R (101 0010)
    I (100 1001)
    N (100 1110)
    T (101 0100)
    Space (010 0000)
    X (101 1000)

### Jawaban dan Cara:

**Jawaban:**

    P ➝ 50₁₆
    Biner ➝ 0101000

    R ➝ S 2
    0101 0010

    I ➝ 6 9
    0100 1001

    N ➝ 4 E
    0100 1110

    T ➝ S 4
    0101 0100

    SPACE ➝ 20₁₆
    0010 0000

    X ➝ 4 8
    0101 1000
