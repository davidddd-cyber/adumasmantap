# ADUMAS — Aduan Mahasiswa

Realisasi UI mockup "Aduan Mahasiswa" (ADUMAS) menjadi aplikasi web statis yang
siap dideploy ke GitHub Pages. Dibuat dengan HTML/CSS/JS murni (tanpa build
step, tanpa backend) — data disimpan di `localStorage` browser sehingga demo
langsung berfungsi begitu file dibuka atau dideploy.

## Fitur

**Sisi mahasiswa**
- Sign in (mock auth berbasis email)
- Buat aduan (judul + isi)
- Konfirmasi "Aduan Terkirim"
- Riwayat aduan (status selesai / diproses)
- Tracking aduan
- Bottom navigation (Home / Tracking)

**Sisi admin**
- Login dengan email `admin@mhs.id` (password bebas)
- Dashboard: total aduan, jumlah minggu ini, jumlah yang masih diproses
- Daftar semua aduan dari seluruh mahasiswa
- Tandai aduan selesai / hapus aduan
- Cari aduan berdasarkan nomor atau judul

## Struktur folder

```
adumas/
├── index.html      # Sign In
├── home.html       # Home (Buat Aduan / Riwayat Aduan)
├── create.html      # Buat Aduan
├── success.html    # Aduan Terkirim
├── history.html     # Riwayat Aduan
├── tracking.html    # Tracking Aduan
├── admin.html       # Dashboard admin
├── assets/
│   ├── css/style.css
│   └── js/app.js    # storage & session helpers (localStorage)
└── README.md
```

## Login demo

| Peran      | Email               | Password       |
|------------|---------------------|-----------------|
| Mahasiswa  | yesking0000@mhs.id  | apa saja        |
| Admin      | admin@mhs.id        | apa saja        |

(Auth ini hanya mock untuk keperluan demo UI — belum ada verifikasi password
sungguhan. Untuk produksi, sambungkan `assets/js/app.js` ke API/backend asli.)

## Menjalankan secara lokal

Tidak perlu instalasi apa pun. Cukup buka `index.html` langsung di browser,
atau jalankan server statis sederhana:

```bash
python3 -m http.server 8000
# lalu buka http://localhost:8000
```

## Deploy ke GitHub Pages

1. Buat repository baru di GitHub, misal `adumas`.
2. Push seluruh isi folder ini ke branch `main`:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: ADUMAS app"
   git branch -M main
   git remote add origin https://github.com/<username>/adumas.git
   git push -u origin main
   ```
3. Di GitHub: buka **Settings → Pages**.
4. Pada **Build and deployment**, pilih **Source: Deploy from a branch**,
   branch **main**, folder **/ (root)** → **Save**.
5. Tunggu 1-2 menit, situs akan tersedia di:
   `https://<username>.github.io/adumas/`

Karena aplikasi ini murni statis (HTML/CSS/JS tanpa dependency build), tidak
diperlukan workflow Actions tambahan — GitHub Pages langsung menyajikan file
apa adanya.

## Mengembangkan lebih lanjut

- Ganti mock storage di `assets/js/app.js` dengan pemanggilan API/backend
  (misalnya Firebase, Supabase, atau REST API sendiri) agar data aduan
  tersimpan permanen dan bisa diakses lintas perangkat.
- Tambahkan validasi login sungguhan (hash password, JWT, dsb).
- Tambahkan halaman detail aduan bila ingin menampilkan riwayat status/komentar.
