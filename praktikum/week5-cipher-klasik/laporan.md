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
def caesar_encrypt(plaintext, key):
    result = ""
    for char in plaintext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift + key) % 26 + shift)
        else:
            result += char
    return result

def caesar_decrypt(ciphertext, key):
    return caesar_encrypt(ciphertext, -key)

# Contoh uji
msg = "CLASSIC CIPHER"
key = 3
enc = caesar_encrypt(msg, key)
dec = caesar_decrypt(enc, key)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)

Hasil=
Plaintext : CLASSIC CIPHER
Ciphertext: FODVVLF FLSKHU
Decrypted : CLASSIC CIPHER

[Program finished]
#contoh potongan kode vignere
def vigenere_encrypt(plaintext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in plaintext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base + shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

def vigenere_decrypt(ciphertext, key):
    result = []
    key = key.lower()
    key_index = 0
    for char in ciphertext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - 97
            base = 65 if char.isupper() else 97
            result.append(chr((ord(char) - base - shift) % 26 + base))
            key_index += 1
        else:
            result.append(char)
    return "".join(result)

# Contoh uji
msg = "KRIPTOGRAFI"
key = "KEY"
enc = vigenere_encrypt(msg, key)
dec = vigenere_decrypt(enc, key)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)

Plaintext : KRIPTOGRAFI
Ciphertext: UVGZXMQVYPM
Decrypted : KRIPTOGRAFI

[Program finished]

#contoh ke 3
def transpose_encrypt(plaintext, key=5):
    ciphertext = [''] * key
    for col in range(key):
        pointer = col
        while pointer < len(plaintext):
            ciphertext[col] += plaintext[pointer]
            pointer += key
    return ''.join(ciphertext)

def transpose_decrypt(ciphertext, key=5):
    num_of_cols = int(len(ciphertext) / key + 0.9999)
    num_of_rows = key
    num_of_shaded_boxes = (num_of_cols * num_of_rows) - len(ciphertext)
    plaintext = [''] * num_of_cols
    col = 0
    row = 0
    for symbol in ciphertext:
        plaintext[col] += symbol
        col += 1
        if (col == num_of_cols) or (col == num_of_cols - 1 and row >= num_of_rows - num_of_shaded_boxes):
            col = 0
            row += 1
    return ''.join(plaintext)

# Contoh uji
msg = "TRANSPOSITIONCIPHER"
enc = transpose_encrypt(msg, key=5)
dec = transpose_decrypt(enc, key=5)
print("Plaintext :", msg)
print("Ciphertext:", enc)
print("Decrypted :", dec)

Plaintext : TRANSPOSITIONCIPHER
Ciphertext: TPIPROOHASNENICRSTI
Decrypted : TRANSPOSITIONCIPHER

[Program finished]
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
