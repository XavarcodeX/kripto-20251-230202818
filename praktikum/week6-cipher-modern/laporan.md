# Laporan Praktikum Kriptografi
Minggu ke-: 6
Topik: [cipher modern]  
Nama: [Muhammad Syaiful Anhar]  
NIM: [230202818]  
Kelas: [5IKRA]  

---

## 1. Tujuan
(Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:  
1. Mengimplementasikan algoritma **DES** untuk blok data sederhana.  
2. Menerapkan algoritma **AES** dengan panjang kunci 128 bit.  
3. Menjelaskan proses pembangkitan kunci publik dan privat pada algoritma **RSA**.  
.)

---

## 2. Dasar Teori
(Cipher klasik merupakan metode kriptografi awal yang digunakan untuk menjaga kerahasiaan pesan sebelum era komputer. Prinsip kerjanya adalah mengubah pesan asli (plaintext) menjadi pesan tersandi (ciphertext) melalui aturan tertentu. Pada cipher klasik, bentuk dasar penyandian dilakukan dengan memanipulasi huruf dalam alfabet menggunakan proses substitusi atau transposisi.

Jenis cipher klasik yang paling umum digunakan adalah Substitution Cipher dan Transposition Cipher. Pada Substitution Cipher, setiap huruf pada plaintext diganti dengan huruf lain. Contohnya adalah Caesar Cipher dan Monoalphabetic Cipher, di mana pergeseran atau penggantian huruf dilakukan secara tetap. Ada juga Vigenère Cipher yang termasuk dalam Polyalphabetic Cipher, menggunakan lebih dari satu alfabet pengganti sehingga lebih sulit dianalisis karena pola huruf tidak mudah ditebak.

Sementara itu, Transposition Cipher tidak mengganti huruf, tetapi mengubah posisi huruf dalam pesan. Huruf-huruf yang sama tetap digunakan, namun urutannya diacak sehingga maknanya tidak dapat langsung dipahami tanpa mengetahui aturan pengacakannya. Contoh teknik ini seperti Rail Fence Cipher dan Columnar Transposition.  )

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
from Crypto.Cipher import DES
from Crypto.Random import get_random_bytes

key = get_random_bytes(8)  # kunci 64 bit (8 byte)
cipher = DES.new(key, DES.MODE_ECB)

plaintext = b"ABCDEFGH"
ciphertext = cipher.encrypt(plaintext)
print("Ciphertext:", ciphertext)

decipher = DES.new(key, DES.MODE_ECB)
decrypted = decipher.decrypt(ciphertext)
print("Decrypted:", decrypted)

Ciphertext: b'\xc5{\xf8\xeb\xf0\xf1\x9eT'
Decrypted: b'ABCDEFGH'

[Program finished]

#contoh potongan kode

from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

key = get_random_bytes(16)  # 128 bit key
cipher = AES.new(key, AES.MODE_EAX)

plaintext = b"Modern Cipher AES Example"
ciphertext, tag = cipher.encrypt_and_digest(plaintext)

print("Ciphertext:", ciphertext)

# Dekripsi
cipher_dec = AES.new(key, AES.MODE_EAX, nonce=cipher.nonce)
decrypted = cipher_dec.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())

from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP

# Generate key pair
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Enkripsi dengan public key
cipher_rsa = PKCS1_OAEP.new(public_key)
plaintext = b"RSA Example"
ciphertext = cipher_rsa.encrypt(plaintext)
print("Ciphertext:", ciphertext)

# Dekripsi dengan private key
decipher_rsa = PKCS1_OAEP.new(private_key)
decrypted = decipher_rsa.decrypt(ciphertext)
print("Decrypted:", decrypted.decode())
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
- Pertanyaan 1: Berikut deskripsi ringkas dan jelas tentang perbedaan mendasar antara DES, AES, dan RSA:


---

📌 Deskripsi Perbedaan DES, AES, dan RSA

DES (Data Encryption Standard) adalah algoritma enkripsi simetris yang menggunakan satu kunci yang sama untuk enkripsi dan dekripsi. Panjang kuncinya hanya 56 bit, sehingga sekarang dianggap tidak aman karena mudah dipecahkan dengan serangan brute-force. DES dulu digunakan secara luas, tetapi sekarang hanya dipakai untuk tujuan pembelajaran atau sistem lama (legacy).

AES (Advanced Encryption Standard) juga merupakan algoritma simetris, tetapi jauh lebih kuat dan modern dibanding DES. AES menggunakan kunci yang jauh lebih panjang, yaitu 128 bit, 192 bit, atau 256 bit, sehingga keamanan AES sangat tinggi dan masih digunakan sebagai standar global untuk enkripsi data, termasuk oleh pemerintah, bank, aplikasi komunikasi, hingga protokol internet modern.

RSA (Rivest–Shamir–Adleman) berbeda dari DES dan AES karena merupakan algoritma asimetris. RSA memakai dua kunci: public key untuk enkripsi dan private key untuk dekripsi. Ukuran kunci RSA jauh lebih besar, biasanya 2048 bit atau lebih, karena metode keamanannya berdasarkan kesulitan memfaktorkan bilangan prima besar. RSA tidak digunakan untuk mengenkripsi data dalam jumlah besar, tetapi dipakai untuk pertukaran kunci, tanda tangan digital, dan otentikasi.


---

DES: Simetris, kunci kecil, tidak aman.

AES: Simetris, kunci panjang, sangat aman dan cepat.

RSA: Asimetris, dua kunci, digunakan untuk keamanan komunikasi, bukan untuk enkripsi data besar.

- Pertanyaan 2:
AES lebih banyak digunakan dibanding DES karena DES sudah tidak aman, sementara AES menawarkan keamanan yang jauh lebih tinggi dengan performa yang lebih cepat dan efisien. DES hanya memiliki kunci 56 bit, yang membuatnya sangat mudah dipecahkan menggunakan brute-force dengan komputer modern. Serangan yang butuh bertahun-tahun di era 1980–1990 kini bisa diselesaikan dalam hitungan jam atau bahkan menit.

Pertanyaan 3:
RSA disebut algoritma asimetris karena menggunakan dua kunci yang berbeda:

Public key → digunakan untuk enkripsi atau memverifikasi tanda tangan.

Private key → digunakan untuk dekripsi atau membuat tanda tangan digital.


Kedua kunci ini berkaitan secara matematis, tetapi tidak mungkin mendapatkan private key hanya dari public key.
Inilah yang membuat RSA disebut asimetris — tidak seperti algoritma simetris (DES, AES) yang memakai satu kunci yang sama.
)
---

## 8. Kesimpulan
hasilnya menunjukan bahwa Aes menawarkan bit yang banyak daripada DES karena saya mencobanya di handphone menggunakan py android
dengan output 
Ciphertext: b'\xad\x181\x8d\xfb\x93\xd9\xcb'
Decrypted: b'ABCDEFGH'

[Program finished]
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
Author: Muhammad Syaiful Anhar<ipuleditor007@gmail.com>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
