# PANDUAN LENGKAP REKAMAN VIDEO TUGAS PRAKTIKUM PBO
**Sistem Informasi Perpustakaan (SiPerpus) - Laravel 11 × OOP**

Dokumen ini adalah sontekan (*cheat sheet*) lengkap untuk Anda gunakan saat merekam video YouTube (durasi 10–15 menit).

---

## 🚀 1. CARA MENJALANKAN APLIKASI
Buka Terminal / PowerShell di folder proyek ini (`tugas 5`), lalu jalankan perintah:
```bash
php artisan serve
```
Buka browser Anda dan akses:
- **Katalog Buku & Sirkulasi:** `http://127.0.0.1:8000`
- **Halaman Visual 8 Konsep PBO:** `http://127.0.0.1:8000/oop-analysis` *(Sangat bagus untuk ditunjukkan di video!)*

---

## ⏱️ 2. SUSUNAN WAKTU & NASKAH VIDEO (10 - 15 MENIT)

### 📍 Menit 00:00 – 01:00 | Perkenalan Diri (Webcam Penuh)
- **Tampilan:** Wajah mahasiswa terlihat jelas di webcam.
- **Hal yang Diucapkan:**
  > *"Halo semuanya! Perkenalkan nama saya **[Nama Anda]** dengan NPM **[NPM Anda]** dari kelas **[Kelas Anda]**, Program Studi Teknik Informatika, Universitas **[Nama Kampus]**. Video ini saya buat untuk memenuhi Tugas Praktikum Pemrograman Berorientasi Objek (PBO). Pada video ini, saya akan menganalisis penerapan konsep PBO pada website berbasis framework PHP Laravel, mendemonstrasikan fiturnya, serta melakukan live modifikasi kode. Mari kita mulai pembahasannya."*

---

### 📍 Menit 01:00 – 02:30 | Pengenalan Website & Fungsinya
- **Tampilan:** Buka browser di halaman `http://127.0.0.1:8000/books`.
- **Hal yang Diucapkan:**
  > *"Website yang saya bangun dan analisis adalah **SiPerpus (Sistem Informasi Perpustakaan)** berbasis Laravel 11. Website ini dirancang untuk mengelola sirkulasi buku secara modular dan terstruktur.*
  > *Fitur-fitur utamanya mencakup:*
  > 1. *Manajemen Katalog Buku (CRUD Buku, pengecekan stok fisik, pencarian data).*
  > 2. *Sirkulasi Peminjaman Buku dengan pencatatan durasi dan tanggal jatuh tempo.*
  > 3. *Kalkulasi Denda Otomatis berbasis multi-strategi polimorfis sesuai jenis anggota (Mahasiswa, Umum, Dosen).*
  > 4. *Halaman Diagnostik PBO untuk memvalidasi eksekusi OOP di balik layar."*

---

### 📍 Menit 02:30 – 04:00 | Penjelasan Laravel & Struktur MVC Kaitannya dengan PBO
- **Tampilan:** Buka VS Code, perlihatkan struktur folder `app/Models`, `resources/views`, dan `app/Http/Controllers`.
- **Hal yang Diucapkan:**
  > *"Laravel merupakan framework PHP modern yang 100% berbasis Pemrograman Berorientasi Objek dan menganut arsitektur **MVC (Model-View-Controller)**.*
  > *Bagaimana korelasi MVC dengan PBO?*
  > - **Model** (`app/Models`): *Menerapkan pola Active Record. Setiap tabel database dipetakan ke dalam sebuah Class Model. Setiap baris data di database menjadi sebuah Objek di memori yang mengenkapsulasi data dan relasi.*
  > - **View** (`resources/views`): *Merupakan lapisan presentasi menggunakan Blade Engine yang menerima objek-objek data dari Controller lalu menampilkannya ke pengguna.*
  > - **Controller** (`app/Http/Controllers`): *Merupakan class orchestrator yang menerima HTTP request, membuat instance objek Model atau Service, memanggil method-method bisnis, lalu mengirimkan objek hasil ke View.*
  > *Dengan demikian, seluruh alur aplikasi di Laravel dijalankan melalui interaksi antar-objek."*

---

### 📍 Menit 04:00 – 07:00 | Analisis 8 Konsep PBO dalam Source Code (INTI MATERI)
Buka file-file berikut di VS Code dan tunjukkan baris kodenya ke kamera:

#### 1. Class
- **File:** `app/Models/Book.php`
- **Tunjukkan:** Baris `class Book extends Model`
- **Penjelasan:** *"Class adalah blueprint atau cetak biru. Di sini `Book` adalah class yang mendefinisikan seluruh struktur dan perilaku entitas buku."*

#### 2. Object
- **File:** `app/Http/Controllers/BookController.php` (method `store`)
- **Tunjukkan:** Baris `$book = new Book();`
- **Penjelasan:** *"Object adalah instance konkret dari class yang menempati memori nyata. Di method `store()`, objek baru dibuat dengan kata kunci `new Book()`."*

#### 3. Property
- **File:** `app/Models/Book.php` & `app/Services/Strategies/RegularFineStrategy.php`
- **Tunjukkan:** `protected $fillable = [...]` dan `private float $baseMultiplier = 1.0;`
- **Penjelasan:** *"Property adalah variabel yang melekat pada class yang menyimpan state objek."*

#### 4. Method
- **File:** `app/Models/Book.php`
- **Tunjukkan:** Method `public function isAvailable(): bool` dan `public function decreaseStock(): bool`
- **Penjelasan:** *"Method adalah fungsi di dalam class yang mendefinisikan aksi atau perilaku yang dapat dilakukan oleh objek tersebut."*

#### 5. Encapsulation (Enkapsulasi)
- **File:** `app/Services/Strategies/RegularFineStrategy.php` & `BaseFineStrategy.php`
- **Tunjukkan:** Penggunaan `public`, `protected`, dan `private`:
  - `public function calculate()`: Dapat dipanggil dari luar class.
  - `protected float $dailyRate`: Hanya bisa diakses di class itu dan turunannya.
  - `private float $baseMultiplier`: Terkunci rapat, hanya class `RegularFineStrategy` yang bisa mengaksesnya langsung.

#### 6. Inheritance (Pewarisan)
- **File:** `app/Models/Book.php` & `app/Services/Strategies/RegularFineStrategy.php`
- **Tunjukkan:** Kata kunci `extends`:
  - `class Book extends Model`
  - `class RegularFineStrategy extends BaseFineStrategy`
- **Penjelasan:** *"Class anak mewarisi seluruh method dan property dari class induk tanpa perlu menulis ulang kodenya."*

#### 7. Polymorphism (Polimorfisme)
- **File:** `app/Services/Strategies/RegularFineStrategy.php` & `StudentFineStrategy.php`
- **Tunjukkan:** Method `calculate(int $daysLate)` di kedua file.
- **Penjelasan:** *"Keduanya memiliki nama method yang sama yaitu `calculate()`, namun perilakunya berbeda: Mahasiswa mendapatkan diskon tarif 50% (Rp 1.000/hari), sedangkan Reguler Rp 2.000/hari. Satu interface, banyak bentuk implementasi."*

#### 8. Abstraction (Abstraksi)
- **File:** `app/Contracts/FineStrategyInterface.php` & `BaseFineStrategy.php`
- **Tunjukkan:** `interface FineStrategyInterface` dan `abstract class BaseFineStrategy`.
- **Penjelasan:** *"Abstraksi menyembunyikan detail implementasi dan hanya mendefinisikan 'kontrak'. Controller cukup bergantung pada interface tanpa perlu tahu rumus internal masing-masing strategi."*

---

### 📍 Menit 07:00 – 10:00 | Demonstrasi Website dan Fitur
Buka browser dan demonstrasikan:
1. **Katalog Buku (`/books`):**
   - Tunjukkan daftar buku hasil seed.
   - Gunakan fitur pencarian (contoh: ketik "Clean Code").
   - Klik **"Tambah Buku Baru"** -> isi form -> simpan -> tunjukkan buku baru berhasil masuk (bukti Object Creation & Persistence).
2. **Sirkulasi Peminjaman (`/borrows`):**
   - Tunjukkan tabel peminjaman aktif.
   - Klik **"Kembalikan"** pada peminjaman milik Mahasiswa (Dimas Pratama).
   - Masukkan tanggal pengembalian (simulasikan terlambat 3 hari).
   - Klik Proses -> Tunjukkan perhitungan denda mahasiswa: Rp 3.000 (3 hari × Rp 1.000).
3. **Halaman Khusus Analisis OOP (`/oop-analysis`):**
   - Buka menu **Analisis 8 Konsep PBO**.
   - Tunjukkan tabel visual polimorfisme denda (Reguler Rp 10.000, Mahasiswa Rp 5.000, Dosen Rp 2.500 untuk 5 hari telat).

---

### 📍 Menit 10:00 – 13:00 | Tantangan Wajib: Demonstrasi Modifikasi Kode
- **Tampilan:** Buka VS Code di file `app/Http/Controllers/BorrowController.php` (method `returnBook`).
- **Yang Ditunjukkan:**
  1. **Kondisi Sebelum Modifikasi (BEFORE):**
     Tunjukkan komentar kode lama di baris 115-128:
     ```php
     // Kode lama prosedural di dalam Controller:
     $fine = 0;
     if ($daysLate > 0) {
         if ($borrow->member_type === 'student') {
             $fine = $daysLate * 1000;
         } else {
             $fine = $daysLate * 2000;
         }
     }
     ```
     *Jelaskan kelemahan kode lama:* "Logika denda bercampur aduk di controller, melanggar Single Responsibility Principle dan tidak modular."
  2. **Kondisi Sesudah Modifikasi (AFTER):**
     Tunjukkan pemanggilan service polimorfis di baris 133:
     ```php
     $fineCalculation = $this->fineService->computeFine($borrow->member_type, $daysLate);
     $totalFine = $fineCalculation['total_fine'];
     ```
  3. **Live Coding / Uji Perubahan Kecil:**
     Buka `app/Services/Strategies/LecturerFineStrategy.php`, ubah diskon dosen dari `0.75` menjadi `0.80` (diskon 80%), simpan file, lalu refresh halaman `/oop-analysis` di browser untuk membuktikan tarif denda dosen langsung berubah menjadi Rp 400/hari secara otomatis tanpa perlu mengubah Controller!
     *Jelaskan dampaknya:* "Inilah kekuatan **Open/Closed Principle** dan **Polymorphism**. Kita bisa mengubah aturan bisnis di class strategi tanpa menyentuh satu baris pun kode Controller."

---

### 📍 Menit 13:00 – 15:00 | Kesimpulan & Refleksi Pembelajaran
- **Tampilan:** Webcam penuh kembali.
- **Hal yang Diucapkan:**
  > *"Sebagai kesimpulan, eksplorasi ini membuktikan bahwa Laravel dibangun sepenuhnya di atas pondasi Object-Oriented Programming. Penerapan 8 konsep PBO—mulai dari Class, Object, Encapsulation, hingga Abstraction dan Polymorphism—membuat arsitektur kode kita menjadi jauh lebih rapi, terisolasi, mudah diuji (testable), dan mudah dikembangkan di masa mendatang.*
  > *Refleksi saya adalah bahwa memisahkan logika ke dalam Service Class dan Strategy Pattern sangat membantu mencegah Controller menjadi 'Fat Controller' dan membuat aplikasi siap untuk skala enterprise.*
  > *Sekian presentasi dan demonstrasi tugas PBO saya. Terima kasih banyak atas perhatian Bapak/Ibu dosen dan asisten praktikum. Wassalamu'alaikum wr. wb. dan salam sejahtera!"*

---

## 📋 3. TEMPLATE COPY-PASTE UNTUK YOUTUBE

### Format Judul Video:
```text
[PBO] Analisis Penerapan Konsep OOP pada Website Laravel – [Nama Anda] – [NPM Anda]
```

### Deskripsi Video:
```text
TUGAS PRAKTIKUM PEMROGRAMAN BERORIENTASI OBJEK (PBO)
Nama: [Nama Lengkap Anda]
NPM: [NPM Anda]
Kelas: [Kelas Anda]
Program Studi: Teknik Informatika
Mata Kuliah: Pemrograman Berorientasi Objek

Judul: Analisis Penerapan Konsep PBO pada Website Berbasis Framework Laravel
Website yang Dianalisis: SiPerpus (Sistem Informasi Perpustakaan & Manajemen Buku) - Laravel 11

Dalam video ini, saya membedah penerapan 8 konsep utama Object-Oriented Programming (OOP) pada aplikasi Laravel:
1. Class (Model Book, Controllers, Services)
2. Object (Instansiasi objek di memori)
3. Property (Protected & Private attributes)
4. Method (Business logic functions)
5. Encapsulation (Access modifiers: public, protected, private)
6. Inheritance (Extends Model & Base Strategy)
7. Polymorphism (Multiple fine strategy behaviors)
8. Abstraction (Contracts & Abstract Classes)
Serta korelasi arsitektur MVC Laravel dengan PBO dan live demonstrasi modifikasi kode (Refactoring ke Strategy Pattern).

Timestamps:
00:00 - Perkenalan Diri & Identitas Mahasiswa
01:05 - Pengenalan Website SiPerpus & Fitur Utama
02:35 - Konsep MVC Laravel & Kaitannya dengan PBO
04:10 - Analisis 8 Konsep PBO dalam Source Code (Bukti Line-by-Line)
07:15 - Demonstrasi Website, Katalog Buku, & Sirkulasi
10:10 - Demonstrasi Modifikasi Kode (Tantangan Wajib: Before vs After)
13:15 - Kesimpulan & Refleksi Pembelajaran

#Laravel #PHP #PBO #OOP #ObjectOrientedProgramming #PemrogramanBerorientasiObjek #WebDevelopment #TeknikInformatika
```
