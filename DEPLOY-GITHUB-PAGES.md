# Panduan Upload & Deploy SakuArab ke Repo Baru

ZIP ini berisi **isi proyek langsung di root ZIP**. Setelah diekstrak, folder yang terlihat harus mencakup `index.html`, `package.json`, `src/`, `public/`, dan `.github/`. Jangan mengunggah ZIP ini sebagai satu file ke repositori.

## Cara paling mudah di Windows

1. Unduh `SakuArab-Repository-Ready.zip`, klik kanan, pilih **Extract All / Ekstrak Semua**.
2. Buat repositori baru di GitHub. Disarankan gunakan branch `main`; nama repo bebas, misalnya `sakuarab`.
3. Install dan buka **GitHub Desktop** jika belum ada: https://desktop.github.com/
4. Pada GitHub Desktop, pilih **File → Clone repository**, lalu clone repo baru ke komputer.
5. Buka folder hasil clone. Salin **semua isi folder hasil ekstrak ZIP** ke folder repo hasil clone. Pastikan folder `.github` ikut tersalin; file workflow harus berada di `.github/workflows/deploy.yml`.
6. Kembali ke GitHub Desktop, tulis summary `Set up SakuArab PWA`, klik **Commit to main**, lalu **Push origin**.
7. Di GitHub, buka repo → **Settings → Pages**. Jika diminta, pilih **GitHub Actions** sebagai Build and deployment source.
8. Buka tab **Actions** dan tunggu workflow **Deploy SakuArab to GitHub Pages** selesai dengan status hijau pada job `build` dan `deploy`.
9. URL publik biasanya `https://USERNAME.github.io/NAMA-REPO/`. Nama repo boleh berbeda: workflow menentukan base path otomatis berdasarkan nama repo.

## Jangan lakukan ini

- Jangan unggah ZIP sebagai satu file; GitHub tidak akan mengekstraknya menjadi proyek.
- Jangan hanya menyalin `index.html`; folder `src`, `public`, berkas konfigurasi, data, `package.json`, dan `.github/workflows` juga dibutuhkan.
- Jangan gunakan deployment Jekyll / `Deploy from a branch`. Proyek ini perlu proses build Vite melalui **GitHub Actions**.

## Menjalankan di komputer sendiri (opsional)

Butuh Node.js 20 atau yang lebih baru. Buka terminal pada folder proyek, lalu jalankan:

```bash
npm install
npm run dev
```

Untuk build produksi:

```bash
npm run build
npm run preview
```

## Jika workflow gagal

Buka **Actions → Deploy SakuArab to GitHub Pages → job yang merah**. Baca langkah pertama yang gagal. Pastikan seluruh isi proyek telah dipush ke branch `main`, Pages menggunakan GitHub Actions, dan repo tidak hanya berisi ZIP.
