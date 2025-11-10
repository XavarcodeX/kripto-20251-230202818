# Laporan Praktikum Kriptografi
Minggu ke-: 4  
Topik: [Entropy unicity]  
Nama: [Muhammad Syaiful Anhar]  
NIM: [230202818]  
Kelas: [5IKRA]  

---

## 1. Tujuan
(Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:

Menyelesaikan perhitungan sederhana terkait entropi kunci.
Menggunakan teorema Euler pada contoh perhitungan modular & invers.
Menghitung unicity distance untuk ciphertext tertentu.
Menganalisis kekuatan kunci berdasarkan entropi dan unicity distance.
Mengevaluasi potensi serangan brute force pada kriptosistem sederhana.

)

---

## 2. Dasar Teori
Cipher klasik merupakan metode kriptografi awal yang digunakan untuk menjaga kerahasiaan pesan sebelum era komputer. Prinsip kerjanya adalah mengubah pesan asli (plaintext) menjadi pesan tersandi (ciphertext) melalui aturan tertentu. Pada cipher klasik, bentuk dasar penyandian dilakukan dengan memanipulasi huruf dalam alfabet menggunakan proses substitusi atau transposisi.

Jenis cipher klasik yang paling umum digunakan adalah Substitution Cipher dan Transposition Cipher. Pada Substitution Cipher, setiap huruf pada plaintext diganti dengan huruf lain. Contohnya adalah Caesar Cipher dan Monoalphabetic Cipher, di mana pergeseran atau penggantian huruf dilakukan secara tetap. Ada juga Vigenère Cipher yang termasuk dalam Polyalphabetic Cipher, menggunakan lebih dari satu alfabet pengganti sehingga lebih sulit dianalisis karena pola huruf tidak mudah ditebak.

Sementara itu, Transposition Cipher tidak mengganti huruf, tetapi mengubah posisi huruf dalam pesan. Huruf-huruf yang sama tetap digunakan, namun urutannya diacak sehingga maknanya tidak dapat langsung dipahami tanpa mengetahui aturan pengacakannya. Contoh teknik ini seperti Rail Fence Cipher dan Columnar Transposition.

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
import math

def entropy(A):
    return math.log2(A)

def unicity_distance(HK, R=0.75, A=26):
    return HK / (R * math.log2(A))

HK = entropy(26)
print("Unicity Distance untuk Caesar Cipher =", unicity_distance(HK))

Unicity Distance untuk Caesar Cipher = 1.3333333333333333

[Program finished]

# contoh potongan kode 2
import math

def entropy(keyspace_size):
    return math.log2(keyspace_size)

print("Entropy ruang kunci 26 =", entropy(26), "bit")
print("Entropy ruang kunci 2^128 =", entropy(2**128), "bit")

Entropy ruang kunci 26 = 4.700439718141092 bit
Entropy ruang kunci 2^128 = 128.0 bit

[Program finished]

# contoh potongan kode 3
def brute_force_time(keyspace_size, attempts_per_second=1e6):
    seconds = keyspace_size / attempts_per_second
    days = seconds / (3600*24)
    return days

print("Waktu brute force Caesar Cipher (26 kunci) =", brute_force_time(26), "hari")
print("Waktu brute force AES-128 =", brute_force_time(2**128), "hari")

Waktu brute force Caesar Cipher (26 kunci) = 3.0092592592592593e-10 hari
Waktu brute force AES-128 = 3.938453320844195e+27 hari

[Program finished]

```
)

---

## 6. Hasil dan Pembahasan
(Kode tersebut menghitung Unicity Distance dari Caesar Cipher, yaitu ukuran banyaknya ciphertext yang dibutuhkan untuk menebak kunci secara unik.
Hasil perhitungannya menunjukkan Unicity Distance = 1, artinya cipher ini sangat lemah, karena cukup satu huruf terenkripsi saja kuncinya sudah bisa ditebak. Caesar Cipher tidak aman digunakan dalam kriptografi modern.

![Hasil Eksekusi](screenshots/output.png)
![Hasil Input](screenshots/input.png)
![Hasil Output](screenshots/output.png)
)

---

## 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1: Entropy berfusngsi untuk mengukur ketidak pastian atau keacakan dari suatu fungsi semakin tinggi entrophy nya maka semakin susah untuk ditebak 
- Pertanyaan 2: unicity distance sangat penting untuk menentukan jumlah minimal chipher text yang di butuhkan untuk dapat menentukan kunci secara unik
- pertanyaan 3:karena bruteforce sendiri merupakan serangan yang umum digunakan nah selain itu masih banyak orang orang yang menggunakan password dengan entropy rendah 
)
---

## 8. Kesimpulan
( )

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
commit abc12345
Author: Nama Mahasiswa <email>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
