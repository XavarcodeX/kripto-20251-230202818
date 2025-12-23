# Laporan Praktikum Kriptografi
Minggu ke-: 9
Topik: [digital-signature]  
Nama: [Muhammad Syaiful Anhar]  
NIM: [230202818]  
Kelas: [5IKRA]  

---

## 1. Tujuan
(Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:

1.Mengimplementasikan tanda tangan digital menggunakan algoritma RSA/DSA.
2.Memverifikasi keaslian tanda tangan digital.
3.Menjelaskan manfaat tanda tangan digital dalam otentikasi pesan dan integritas data.)

---

## 2. Dasar Teori
Digital signature (tanda tangan digital) adalah mekanisme kriptografi yang digunakan untuk memverifikasi keaslian, keutuhan, dan keabsahan suatu dokumen atau pesan elektronik.

Secara sederhana, digital signature memastikan bahwa:

Pengirimnya benar (autentikasi),

Isi tidak diubah sejak ditandatangani (integritas),

Pengirim tidak bisa menyangkal telah menandatangani dokumen tersebut (non-repudiation).

Digital signature biasanya menggunakan kriptografi kunci publik, yaitu:

Kunci privat untuk menandatangani dokumen

Kunci publik untuk memverifikasi tanda tangan

Contoh penggunaan:

Penandatanganan dokumen PDF secara elektronik

Transaksi perbankan online

Email resmi dan sertifikat digital

Kalau mau, aku bisa jelaskan versi yang lebih sederhana atau versi akademik untuk tugas sekolah.

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

from Crypto.PublicKey import RSA
from Crypto.Signature import pkcs1_15
from Crypto.Hash import SHA256

# Generate pasangan kunci RSA
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Pesan yang akan ditandatangani
message = b"Hello, ini pesan penting."
h = SHA256.new(message)

# Buat tanda tangan dengan private key
signature = pkcs1_15.new(private_key).sign(h)
print("Signature:", signature.hex())

hasil:7f23f61c836c21f5b815ad23d5505a4cd2ee36d70998e2d2211310395283ee38ce8be89704591cf44a50bf580d404a406fd942f90de5c78aee89fa90340febeff22d88050864b0c60d8de21f1db302c0baa046ab2ec40f9d7599b849e7fd1119d22f808a45bb4365ec90057370c4d9a3260cefc6601e5bd0d78379b8be002d4d5a78b6e733298d023384b2abf90b8cbf243b5661595a93e58e5b2d4242685f2aead498c1cb192407b119ea35e83729e7fcdbce73bf37a1c78374bf379de8fe2629d89b8f25da6242b5b54d0d7f385f2c5c3303e89d4ab50f2f9165d86c86f82f59e2b0a9fa9bd59c2fa1fc8b046696d2a17810fdfcfabd841cc42ba993b25da7.

from Crypto.PublicKey import RSA
from Crypto.Signature import pkcs1_15
from Crypto.Hash import SHA256

# Generate pasangan kunci RSA
key = RSA.generate(2048)
private_key = key
public_key = key.publickey()

# Pesan asli
message = b"Hello, ini pesan penting."
h = SHA256.new(message)

# Buat tanda tangan
signature = pkcs1_15.new(private_key).sign(h)
print("Signature:", signature.hex())

# Verifikasi pesan asli
try:
    pkcs1_15.new(public_key).verify(h, signature)
    print("Verifikasi berhasil: tanda tangan valid cuy.")
except (ValueError, TypeError):
    print("Verifikasi gagal: tanda tangan ngga valid.")

# Pesan palsu
fake_message = b"Hello, ini pesan palsu."
h_fake = SHA256.new(fake_message)

# Verifikasi pesan palsu
try:
    pkcs1_15.new(public_key).verify(h_fake, signature)
    print("Verifikasi berhasil (seharusnya gagal).")
except (ValueError, TypeError):
    print("Verifikasi gagal: tanda tangan tidak cocok dengan pesan.")

    Verifikasi berhasil: tanda tangan valid cuy.
Verifikasi gagal: tanda tangan tidak cocok dengan pesan.

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
- Pertanyaan 1:
Enkripsi RSA
Digunakan untuk menjaga kerahasiaan data agar hanya penerima yang berhak dapat membaca pesan.

Tanda tangan digital RSA
Digunakan untuk menjamin keaslian pengirim, keutuhan data, dan non-repudiation (pengirim tidak bisa menyangkal).  
- Pertanyaan 2: Tanda tangan digital menjamin integritas karena perubahan pesan dapat terdeteksi melalui hash, dan menjamin otentikasi karena hanya pemilik kunci privat yang dapat membuat tanda tangan yang valid.
- pertanyaan 3:CA memastikan bahwa kunci publik benar-benar milik identitas yang sah, sehingga tanda tangan digital dapat dipercaya dalam skala besar di internet.
)
---

## 8. Kesimpulan
( **Kesimpulan singkat:**

Enkripsi RSA dan tanda tangan digital RSA memiliki tujuan yang berbeda, di mana enkripsi RSA berfokus pada **kerahasiaan pesan**, sedangkan tanda tangan digital RSA berfungsi untuk **menjamin keaslian, keutuhan, dan non-repudiation**. Tanda tangan digital dapat menjamin **integritas dan otentikasi pesan** karena menggunakan fungsi hash dan kunci privat yang hanya dimiliki pengirim. Dalam sistem modern, **Certificate Authority (CA)** berperan sebagai pihak tepercaya yang **memverifikasi identitas dan mengaitkannya dengan kunci publik**, sehingga tanda tangan digital dapat dipercaya dan digunakan secara luas dengan aman.
 )

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
Author: Muhammad Syaiful Anhar <ipuleditor007@gmail.com>
Date:   2025-09-20

    week9-digital-signature: implementasi digital-signature )
```
