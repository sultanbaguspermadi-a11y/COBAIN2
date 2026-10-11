# SakuArab — Kamus Arab Vokasi

**Arab buat dunia kerja, bukan cuma hafalan.**

Progressive Web App (PWA) kamus Arab–Indonesia untuk siswa SMK. Aplikasi menggunakan React + Vite, dirancang mobile-first, dan menyimpan bookmark/progres secara lokal pada perangkat.

## Fitur

- Pencarian kosakata Arab, Latin, Indonesia, dan kategori dengan normalisasi tulisan Arab.
- Jalur RPL, Akuntansi, TBKR, TSM, serta Umum.
- Kartu kata dengan harakat yang dapat diaktifkan/nonaktifkan, transliterasi, makna, contoh Arab–Indonesia, dan tag pelafalan.
- Kata hari ini, riwayat, bookmark, progres, streak, flashcard, kuis singkat, susun huruf, dan pasangan kata mirip.
- Tema gelap/terang/otomatis, pengaturan ukuran teks Arab, serta warna aksen per jurusan.
- Penyimpanan lokal dengan IndexedDB/Dexie, ekspor/impor progres, dan berbagi kartu gambar.
- PWA dengan service worker dan file kosakata jurusan yang dimuat secara dinamis.
- Deployment otomatis GitHub Pages melalui GitHub Actions + Vite build.

## Jalankan secara lokal

Persyaratan: Node.js 20 atau lebih baru.

```bash
npm install
npm run dev
```

Build lokal:

```bash
npm run build
npm run preview
```

## Deploy ke repo GitHub baru

1. Ekstrak ZIP ini di komputer; jangan unggah ZIP sebagai satu file.
2. Salin semua isi hasil ekstrak ke folder repo lokal (GitHub Desktop direkomendasikan) dan push ke branch `main`.
3. Buka **Settings → Pages** dan pilih **GitHub Actions** jika belum terpilih.
4. Tab **Actions** menjalankan `.github/workflows/deploy.yml`. Workflow memasang dependensi, menjalankan `npm run build`, lalu menerbitkan folder `dist`.
5. Nama repo tidak harus `muhapen`: `VITE_BASE_PATH` ditentukan otomatis dari nama repo saat build.

Langkah upload yang lebih rinci ada di [DEPLOY-GITHUB-PAGES.md](./DEPLOY-GITHUB-PAGES.md).

## Data & konfigurasi

- `src/data/config.json`: tema, jurusan, warna, fitur, konfigurasi Arab/PWA.
- `src/data/rpl.json`, `akuntansi.json`, `tbkr.json`, `tsm.json`, `umum.json`: kosakata per jalur.
- `src/data/similar.json`: pasangan kata yang mirip.
- `words-structured.json`: gabungan kosakata format objek.
- `words-expanded-legacy.json`: ekspor format lama untuk kompatibilitas.

Jumlah pada dataset saat dikemas: 600 entri RPL, 600 Akuntansi, 600 TBKR, 600 TSM, 102 Umum, dan 24 pasangan kata mirip. Contoh kalimat, transliterasi, dan istilah teknis tetap sebaiknya ditinjau guru Bahasa Arab/guru produktif sebelum digunakan sebagai bahan ajar resmi.

## Privasi dan batasan

Tidak memakai login atau backend. Bookmark, riwayat, streak, dan progres disimpan secara lokal pada browser. Pemindahan perangkat dilakukan lewat ekspor/impor file JSON.
