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
def encrypt(text, key):
    return ...
```
)

---

## 6. Hasil dan Pembahasan
(- Lampirkan screenshot hasil eksekusi program (taruh di folder `screenshots/`).  
- Berikan tabel atau ringkasan hasil uji jika diperlukan.  
- Jelaskan apakah hasil sesuai ekspektasi.  
- Bahas error (jika ada) dan solusinya. 

Hasil eksekusi program Caesar Cipher:

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
(Tuliskan kesimpulan singkat (2–3 kalimat) berdasarkan percobaan.  )

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
