# Laporan Praktikum Kriptografi
Minggu ke-: 5
Topik: [Chiper klasik]  
Nama: [Muhammad Syaiful Anhar]  
NIM: [230202818]  
Kelas: [5IKRA]  

---

## 1. Tujuan
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:

Menerapkan algoritma Caesar Cipher untuk enkripsi dan dekripsi teks.
Menerapkan algoritma Vigenère Cipher dengan variasi kunci.
Mengimplementasikan algoritma transposisi sederhana.
Menjelaskan kelemahan.

---

## 2. Dasar Teori
(Ringkas teori relevan (cukup 2–3 paragraf).  
Contoh: definisi cipher klasik, konsep modular aritmetika, dll.  )

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
- Pertanyaan 1: Kelemahan Algoritma caesar cipher:
- Ruang kunci sangat kecil hanya mod 25 bisa dipecahkan dengan bruterforce
- pola huruf masih terlihat biasanya ewakili huruf E dan A pada plaintext
- Tetap berulang katanya seperti lemon setiap perhitungan alphabet dan huruf jika di posisisikan maka kata lemon akan terus berulang.
  vignere cipher:
-sama dengan caesar cipher pola muncul
-Masih rentan terhadap analisis frekuensi blok
-kunci sering tidak di acak
- Pertanyaan 2:
- karena tidak di sembunyikan alias mudah ditebak penyerang tinggal melihat pola huruf nya saja
- pertanyaan 3:
|Aspek   |cipher Substitusi|
| **Aspek** | **Cipher Substitusi** |
|------------|------------------------|
| **Cara kerja** | Mengganti setiap huruf dengan huruf lain |
| **Contoh** | Caesar, Vigenère |
| **Tujuan utama** | Menyamarkan makna huruf |
| **Pola frekuensi huruf** | Masih dapat terlihat meskipun berubah simbol |
| **Analisis frekuensi** | Lebih mudah diserang karena distribusi huruf tetap |
| **Kelebihan** | Sederhana, mudah diimplementasikan |
| **Kelemahan** | Pola bahasa masih bisa dikenali |

Cipher Transposisi
------------------
Mengubah urutan huruf tanpa menggantinya
------------------------
Rail Fence,Columnar Transpotation
------------------------
Menyamarkan urutan huruf
------------------------
Distribusi huruf tetap sama,hanya urutannya berubah
-----------‐-------------
sedikit lebih sulit tapi masih bisa dipecahkan dengan pola posisi
-------------------------
tidak mengubah isi huruf,hanya struktur
-------------------------
mudah dipecahkan jika pola transposisi diketahui

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
