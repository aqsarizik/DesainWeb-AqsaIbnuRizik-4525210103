# Laporan Tugas Individu — Form Registrasi Event

**Nama :** Aqsa Ibnu Rizik
**NPM:** 4525210103
**Mata kuliah:** Praktikum Desain Web — Pertemuan 7 
**Studi kasus:** Registrasi peserta *Pekan Web Nusantara 2026*



## 1. Kontrol form yang dipakai

| Kontrol | Elemen | Nama field |
|---|---|---|
| Teks, email, telepon, tanggal | `<input type="text/email/tel/date">` | `nama`, `email`, `telepon`, `tgl_lahir` |
| **Radio** | `<input type="radio">` | `gender` |
| **Select** | `<select>` | `kategori` |
| **Checkbox** | `<input type="checkbox">` (grup) + persetujuan | `sesi`, `setuju` |
| **Textarea** | `<textarea>` | `alasan` |
| **Upload** | `<input type="file">` | `bukti` |
| Tombol | `type="submit"` dan `type="reset"` | — |

Setiap input memakai `<label for>` + `id` (aksesibilitas) dan atribut `name` (key data saat dikirim). Form memakai `method="post"` dan `enctype="multipart/form-data"` karena ada upload file.

## 2. Aturan validasi (11 aturan, syarat minimal 4)

| No | Aturan | Atribut HTML5 | Field |
|---|---|---|---|
| 1 | Wajib diisi | `required` | semua field bertanda * |
| 2 | Format email | `type="email"` | email |
| 3 | Pola nama (huruf saja) | `pattern="[A-Za-z .'\-]{3,60}"` | nama |
| 4 | Pola nomor seluler Indonesia | `pattern="(\+62\|62\|0)8[1-9][0-9]{7,10}"` | telepon |
| 5 | Panjang minimum | `minlength="3"` / `minlength="20"` | nama, alasan |
| 6 | Panjang maksimum | `maxlength="60"` / `maxlength="300"` | nama, alasan |
| 7 | Batas tanggal (usia minimal 17 tahun) | `min` dan `max="2009-11-11"` | tanggal lahir |
| 8 | Pilih salah satu radio | `required` pada radio | jenis kelamin |
| 9 | Pilihan select tidak boleh kosong | `required` + `<option value="">` | kategori |
| 10 | Persetujuan wajib dicentang | `required` pada checkbox | setuju |
| 11 | Filter jenis file (hanya pembatas dialog) | `accept` | bukti |



### screenshot bukti (desktop dan mobile)

## dekstop

![alt text](<gambar ss/dekstop 1.png>)

![alt text](<gambar ss/dekstop 2.png>)

## mobail
![alt text](<gambar ss/mobile.png>)

## 5. Perubahan, masalah, dan solusi

| Masalah | Solusi |
|---|---|
| Versi awal memakai JavaScript, padahal tugas diminta tanpa JavaScript | Semua validasi dipindah ke atribut HTML5; folder `js/` dan `tests/` dihapus |
| Bubble error bawaan browser tidak bisa diubah teksnya tanpa JS | Memakai atribut `title` pada field ber-`pattern`, dan teks bantu (`.hint`) di bawah field |
| Field tampil merah sebelum pengguna mengisi apa pun jika memakai `:invalid` | Memakai pseudo-class `:user-invalid` yang hanya aktif setelah pengguna berinteraksi |
| Checkbox "minimal 1 sesi" tidak bisa dibuat dengan HTML saja (`required` pada tiap checkbox akan memaksa semuanya dicentang) | Sesi dibuat opsional ("boleh lebih dari satu"); aturan minimal-1 dicek di server bila dibutuhkan |
| Ukuran dan tipe file tidak bisa divalidasi HTML | `accept` + teks petunjuk untuk pengguna; validasi sebenarnya dilakukan di server (TC-12, TC-13) |
| Batas usia 17 tahun memakai `max="2009-11-11"` bersifat statis | Perlu diperbarui tiap tahun, atau dihitung ulang di server |
| `action="#"` belum menuju backend | Placeholder; ganti dengan URL pemrosesan saat backend tersedia |
| Layout harus nyaman di ponsel | CSS responsif: grid dua kolom jadi satu kolom pada lebar ≤ 860 px, dan tombol penuh lebar pada ≤ 540 px |