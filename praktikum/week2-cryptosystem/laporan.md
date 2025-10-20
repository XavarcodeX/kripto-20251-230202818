# Laporan Praktikum Kriptografi
Minggu ke-: 2
Topik: [Cryptosystem]  
Nama: [Muhammad Syaiful Anhar]  
NIM: [230202818]  
Kelas: [5IKRA]  

---

## 1. Tujuan
Setelah mengikuti praktikum ini, mahasiswa diharapkan mampu:
1.Mengidentifikasi komponen dasar kriptosistem (plaintext, ciphertext, kunci, algoritma).
2.Menggambarkan proses enkripsi dan dekripsi sederhana.
3.Mengklasifikasikan jenis kriptosistem (simetris dan asimetris).

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


## 5. Source Code
(Salin kode program utama yang dibuat atau dimodifikasi.  


def encrypt(plaintext, key):
    result = ""
    for char in plaintext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift + key) % 26 + shift)
        else:
            result += char
    return result


def decrypt(ciphertext, key):
    result = ""
    for char in ciphertext:
        if char.isalpha():
            shift = 65 if char.isupper() else 97
            result += chr((ord(char) - shift - key) % 26 + shift)
        else:
            result += char
    return result


if __name__ == "__main__":
    message = "<230202818><Muhammad Syaiful Anhar >"
    key = 5

    enc = encrypt(message, key)
    dec = decrypt(enc, key)

    print("Plaintext :", message)
    print("Ciphertext:", enc)
    print("Decrypted :", dec)



---

## 6. Hasil dan Pembahasan
dari hasil yang saya dapatkan untuk encrypt nya sendiri hasilnya
Plaintext : <230202818><Muhammad Syaiful Anhar >
Ciphertext: <230202818><Rzmfrrfi Xdfnkzq Fsmfw >
Decrypted : <230202818><Muhammad Syaiful Anhar >

## 7. Jawaban Pertanyaan
(Jawab pertanyaan diskusi yang diberikan pada modul.  
- Pertanyaan 1: Komponen utama dalam kriptosistem adalah:
plaintext --> pesan asli yang akan di enkripsi
Ciphertext --> Pesan yang sudah dienkripsi.
Algortitma enkripsi --> proses atau rumus untuk mengubah plaintext menjadi ciphertext.
Algoritma dekripsi --> proses untuk mengembalikan ciphertext menjadi plaintext.
- Pertanyaan 2: Kelebihan:
-lebih cepat dan efisien untuk data besar
-Algoritmanya lebih sederhana
-Tidak perlu berbagi kunci rahasia secara langsung
-Lebih aman untuk komunikasi terbuka
Kelemahan:
-Distribusi kunci sulit (harus dikirim secara aman).
-Tidak cocok untuk komunikasi terbuka banyak pihak
-Proses enkripsi atau decrypt lebih lambat
>Pertanyaan 3
Distribusi kunci menjadi masalah utama karena :
dalam sistem simetris,pengirim dan penerima harus memiliki kunci yang sama,dan kunci tersebut harus dijaga kerahasiaannya. jika kunci disadap saat dikirim,maka seluruh komunikasi dapat dibobol karena pihak penyadap dapat mengenkripsi dan mendecrypt pesan kesemula.
)
---

## 8. Kesimpulan
Cryptosistem adalah sistem untuk melindungi kerahasiaan data 
Terdiri dari komponen plaintext,ciphertext kunci dan algoritma 
Proses enkripsi mengamankan data,sementara dekripsi mengembalikannya

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
Author: Muhammad Syaiful Anhar<ipuleditor007@gmail.com>
Date:   2025-09-20

    week2-cryptosystem: implementasi Caesar Cipher dan laporan )
```
