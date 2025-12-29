# Laporan Praktikum Kriptografi
Minggu ke-: X  
Topik: [public key infrastructure]  
Nama: [Muhammad Syaiful Anhar]  
NIM: [230202818]  
Kelas: [5IKRA]  

---

## 1. Tujuan
(1.Membuat sertifikat digital sederhana.
2.Menjelaskan peran Certificate Authority (CA) dalam sistem PKI.
3.Mengevaluasi fungsi PKI dalam komunikasi aman (contoh: HTTPS, TLS)..)

---

## 2. Dasar Teori
(1.Definisi Public Key Infrastructure (PKI)
Public Key Infrastructure (PKI) adalah sebuah sistem, kebijakan, prosedur, serta teknologi yang digunakan untuk mengelola, mendistribusikan, dan memverifikasi kunci kriptografi (public key dan private key) guna menjamin keamanan komunikasi digital.
PKI memungkinkan:

Enkripsi data agar informasi tidak dapat dibaca oleh pihak yang tidak berwenang

Autentikasi identitas untuk memastikan identitas pengguna atau sistem

Integritas data agar data tidak diubah selama proses pengiriman

Non-repudiation (tidak dapat disangkal) terhadap transaksi digital

PKI bekerja dengan memanfaatkan kriptografi kunci publik, di mana:

Public key dibagikan secara umum

Private key disimpan secara rahasia oleh pemiliknya.

2. Definisi Sertifikat CA (Certificate Authority)
Certificate Authority (CA) adalah lembaga atau pihak tepercaya yang bertugas menerbitkan, memverifikasi, dan mengelola sertifikat digital dalam sistem PKI.
Sedangkan sertifikat CA (sertifikat digital) adalah dokumen elektronik yang digunakan untuk:

Mengaitkan identitas pemilik (individu, organisasi, atau server) dengan public key

Menjamin bahwa public key tersebut benar-benar milik entitas yang bersangkutan

Sertifikat digital biasanya berisi:

Identitas pemilik sertifikat

Public key pemilik

Informasi CA penerbit

Masa berlaku sertifikat

Tanda tangan digital dari CA)

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
import os
from cryptography import x509
from cryptography.x509.oid import NameOID
from cryptography.hazmat.primitives import hashes, serialization
from cryptography.hazmat.primitives.asymmetric import rsa
from datetime import datetime, timedelta

#Generate key pair
key=rsa.generate_private_key(public_exponent=65537,key_size=3000)

#Buat subject & issue (CA sederhana = self-signed)
subject = issuer =x509.Name([
x509.NameAttribute(NameOID.COUNTRY_NAME,u"ID"),
x509.NameAttribute(NameOID.
ORGANIZATION_NAME, u"UPB Kriptografi"),
x509.NameAttribute(NameOID.COMMON_NAME, u"example.com"),
])

#Buat sertifikat
cert =(
x509.CertificateBuilder()
.subject_name(subject)
.issuer_name(issuer)
.public_key(key.public_key())
.serial_number(x509.random_serial_number())
.not_valid_before(datetime.now())
.not_valid_after(datetime.now() + timedelta(days=365))
.sign(key, hashes.SHA256())
)

#simpan sertifikat
with open ("cert.pem", "wb") as f:
    f.write(cert.public_bytes(serialization.Encoding.PEM))
    
    print("Sertifikat berhasil di buat: cert.pem")
    print(os.getcwd())
    print(os.listdir())
output:sertifikat berhasil dibuat:cert.pem
/storage/emulated/0/Android/data/ru.iiec.pydroid3/files.
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
- Pertanyaan 1:Fungsi utama Certificate Authority (CA) adalah sebagai pihak tepercaya yang bertugas untuk:

Memverifikasi identitas entitas (website, organisasi, atau individu) sebelum menerbitkan sertifikat digital

Menerbitkan sertifikat digital yang mengaitkan identitas pemilik dengan public key

Menandatangani sertifikat secara digital, sehingga sertifikat tersebut dapat dipercaya oleh sistem dan browser

Mengelola siklus hidup sertifikat, termasuk pembaruan (renewal), pencabutan (revocation), dan masa berlaku

Dengan adanya CA, pengguna dapat yakin bahwa public key yang digunakan dalam komunikasi benar-benar milik pihak yang sah.  
- Pertanyaan 2:Self-signed certificate adalah sertifikat yang ditandatangani oleh pemiliknya sendiri, bukan oleh CA tepercaya. Sertifikat ini tidak cukup untuk sistem produksi karena:

Tidak ada pihak ketiga tepercaya yang memverifikasi identitas pemilik sertifikat

Browser dan sistem operasi tidak mempercayainya secara default, sehingga menampilkan peringatan keamanan

Rentan terhadap serangan MITM, karena penyerang dapat dengan mudah membuat sertifikat palsu

Sulit dikelola dalam skala besar, terutama untuk banyak pengguna atau layanan publik

Self-signed certificate hanya cocok untuk pengujian, pembelajaran, atau lingkungan internal terbatas. 
-pertanyaan 3:PKI mencegah serangan Man-in-the-Middle (MITM) dalam TLS/HTTPS melalui beberapa mekanisme utama:

Verifikasi sertifikat oleh CA
Browser memeriksa apakah sertifikat server ditandatangani oleh CA tepercaya dan masih berlaku.

Validasi identitas server
Nama domain pada sertifikat harus sesuai dengan domain yang diakses. Jika tidak cocok, koneksi akan ditolak.

Tanda tangan digital
Sertifikat yang diubah atau dipalsukan akan terdeteksi karena tanda tangan digital CA tidak valid.

Pertukaran kunci terenkripsi
Proses handshake TLS menggunakan public key server untuk membuat session key rahasia, sehingga penyerang tidak dapat membaca atau memodifikasi data.
)
---

## 8. Kesimpulan
(Sertifikat CA mampu melindungi pengguna dari serangan MITM khususnya serangan seperti Remote acces spyware trojan ibaratnya ada rumah dan penghuni dan ada pintu yang berfungsi untuk keluar dan masuk sertifikat CA nya itu kita ibaratkan kunci rumah dia berfungsi sebagai key nya yang boleh mengakses hanya keluarga yang memiliki kunci tersebut   )

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
Author: Muhammad Syaiful Anhar <email>
Date:   2025-12-29

    week10-PKI:public key infrastructure )
```
