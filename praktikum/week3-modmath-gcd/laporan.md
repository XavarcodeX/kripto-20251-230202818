# Laporan Praktikum Kriptografi
Minggu ke-: 3
Topik: [mood math]  
Nama: [Muhammad Syaiful Anhar]  
NIM: [230202818]  
Kelas: [5IKRA]  

---

## 1. Tujuan
1.Meneyelesaikan operasi aritmatika modular
2. Menentukan bilangan prima dan menghitung GCD (Greatest Common Divisor).  
3. Menerapkan logaritma diskrit sederhana dalam simulasi kriptografi.  

---

## 2. Dasar Teori
Dalam Kriptografi,sandi klasik adalah jenis sandi yang digunakan pada zaman dahulu,namun sekarang telah jarang dan hampir tidak pernah digunakan
Berbeda dengan algoritma modern banyak sandi klasik dapat dipecahkan melalui perhitungan dan diselesaikan tanpa bantuan mesin meskipun demikian sandi klasik juga biasanya dapat sengan mudah dipecahkan melalui teknologi modern.Definisi umum Aritmatika modullar adalah sistem operasi matematika yang berhubungan dengan sisa hasil pembagian suatu bilangan dengan kata lain,dua bilangan dikatakan kongruen apabila jika keduanya memiliki sisa yang sama apabila dibagi oleh n
---

## 3. Alat dan Bahan
(- Python 3.x  
- Visual Studio Code / editor lain  
- Git dan akun GitHub  
- Library tambahan (misalnya pycryptodome, jika diperlukan)  )

---

## 4. Langkah Percobaan
(Tuliskan langkah yang dilakukan sesuai instruksi.  
Contoh format:
1. Membuat file `caesar_cipher.py` di folder `praktikum/week2-cryptosystem/src/`.
2. Menyalin kode program dari panduan praktikum.
3. Menjalankan program dengan perintah `python caesar_cipher.py`.)

---

## 5. Source Code
(Salin kode program utama yang dibuat atau dimodifikasi.  
Gunakan blok kode:

```python
# contoh potongan kode
def mod_add(a,b,n):return (a+b) % n
def mod_sub(a,b,n):return (a-b) % n
def mod_mul(a,b,n):return (a*b) % n
def mod_exp(base,exp,n)return pow (base,exp,n) //eksponisasi modular

print("7+5 mod 12=", mod_add (7,5,12))#hasilnya 0 karena sisanya 0
print("7*5 mod 12=", mod_mul(7,5,12))#hasilnya 11 karena 35-24 hasilnya=11 
print("7^128 mod 13=", mod_exp(7,128,13))

```python
def egcd(a,b):
    while b!=0:
        a,b=b,a % b
        return a
    print ("gcd(54,24)=", gcd(54,24))#hasilnya 6 karena 54:24=2 24 x 2 hasilnya 48 maka hasilnya adalah = 6

---


## 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1: Aritmatika modular berperan krusial dalam kriptografi modern dengan menyediakan kerangka kerja untuk perhitungan yang aman dan efisien, terutama pada algoritma kunci seperti RSA dan Diffie-Hellman,serta mendukung algoritma kunci simetris seperti AES   
- Pertanyaan 2: Invers modular sangat penting dalam algoritma kunci publik karena digunakan untuk menghitung kunci privat dari kunci publik dalam algoritma seperti RSA.
-pertanyaan 3:di perhitungannya juga tergantung angkanya berapa. 
)
---

## 8. Kesimpulan
(Kesimpulannya adalah aritmatika modular, invers modular sangat penting karena masing masing memiliki peran penting dalam menghitung kunci privat dan publik.  )

---

## 9. Daftar Pustaka
(Cantumkan referensi yang digunakan.  
Contoh:  
- Katz, J., & Lindell, Y. *Introduction to Modern Cryptography*.  
- Stallings, W. *Cryptography and Network Security*.  )

---

## 10. Commit Log
(Tuliskan bukti commit Git yang relevan.  
Contoh:
```
commit week3_moodmath
Author: Muhammad Syaiful Anhar <ipuleditor007@gmail.com>
Date:   2025-09-20

    week3-modmath: implementasi Caesar Cipher dan laporan )
```
