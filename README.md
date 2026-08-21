# Penilaian Karakter BaKu (Baik & Kuat)
**SMP Daarut Tauhiid Boarding School (DTBS) Putra**

Aplikasi web instrumen evaluasi dan pembinaan karakter BaKu (Baik & Kuat) berbasis client-server serverless, mengintegrasikan antarmuka modern responsif dengan basis data Google Sheets via Google Apps Script (GAS) Universal API.

---

## 📌 Fitur Utama

### 1. Peran & Hak Akses (Multi-Role Auth Guard)
* **Administrator**:
  * Monitoring ringkasan sistem (Total Siswa, Wali Kelas, Bank Pertanyaan, Periode Aktif).
  * Manajemen CRUD data Siswa dan Wali Kelas.
  * Manajemen 24 Indikator Bank Pertanyaan Karakter BaKu.
  * Manajemen Periode Penilaian (Buka/Tutup akses, set semester otomatis, pemilihan pilar aktif: Baik/Kuat, dan fokus: Jaga Lisan/BR3T).
* **Wali Kelas**:
  * Dashboard monitoring status kelengkapan observasi siswa binaan.
  * Formulir Observasi Karakter per siswa (nama siswa disematkan langsung pada kalimat indikator).
  * Rekapitulasi Nilai Akhir dengan filter dinamis per **Semester** (Ganjil/Genap) dan per **Fokus** (Jaga Lisan/BR3T/Semua).
  * Fitur salin cepat:
    * **Copy Nama**: Menyalin daftar nama siswa satu per baris.
    * **Copy Nilai (Leger)**: Menyalin murni matriks angka skor karakter (Tab-Separated) siap tempel ke sheet leger Excel.
* **Siswa**:
  * Dashboard capaian predikat karakter pribadi (Ikhlas, Jujur, Tawadhu, Berani, Disiplin, Tangguh).
  * **Penilaian Diri (Muthala'ah An-Nafs)**: Pengisian instrumen mandiri satu kali per periode dengan mekanisme penguncian permanen (*locked on submit*).
  * **Penilaian Antar Teman**: Penilaian objektif terhadap tepat 4 rekan sekelas berdasarkan rotasi urutan absen (*wrap-around*).

---

## 🛠️ Arsitektur & Teknologi

* **Frontend**: HTML5, Tailwind CSS, JavaScript (Vanilla ES6+), FontAwesome Icons.
* **Backend**: Google Apps Script (GAS) dengan Router Universal API `doPost(e)`.
* **Database**: Google Sheets.
* **Keamanan**:
  * Password hashing: SHA-256 + Private Salt.
  * Token session UUID (kedaluwarsa 8 jam).
  * LockService anti-race condition saat eksekusi data batch.
  * Formula Anti-CORS menggunakan pipeline header `text/plain`.
  * DOM-level Auth Guard (komponen privat tidak dirender sebelum autentikasi valid).
* **Deployment Target**: GitHub Pages.
