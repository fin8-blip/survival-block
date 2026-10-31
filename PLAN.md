# PLAN.md — Universal 2D Arcade Game Roadmap (Untuk Siswa)

Dokumen ini adalah rencana kerja universal dan log perkembangan proyek pembuatan game arcade 2D dalam 1 file `index.html`. Dokumen ini diperbarui secara otomatis oleh AI setiap kali ada perubahan kode sebelum push ke GitHub.

---

## 1. Ikhtisar Game

- **Judul Game**: *(Menunggu sesi brainstorming ide game bersama siswa)*
- **Genre**: 2D Arcade Game
- **Format**: Single-File HTML (`index.html`) tanpa dependensi eksternal
- **Platform**: Web Browser (Desktop & Mobile Responsive)
- **Audio**: Web Audio API Sintetis
- **Penyimpanan**: LocalStorage (`arcade_leaderboard`, `arcade_last_username`)
- **Kebijakan Caching**: Zero-Cache (`no-cache, no-store, must-revalidate`)
- **Deployment**: GitHub Pages (Branch `main`, path `/`)

---

## 2. Fase Pengembangan Universal

### Phase 0: Brainstorming & Desain Game
- [x] Siswa menentukan ide & tema game: **Survival Block 2D** (Minecraft-like, bangun rumah, kumpulkan resource)
- [x] Kontrol: Keyboard (WASD/Panah/TFGH), Mouse klik kanan-kiri, Sentuh (layar HP)
- [x] Aturan: Tambang blok dapat item, bangun rumah, jaga HP & Lapar, bertahan selama mungkin
- [x] Gaya visual: Pixel 2D warna, responsive HP & laptop

### Phase 1: Setup Single-File `index.html`
- [x] Kerangka HTML5 dengan meta tag **Zero-Cache**
- [x] Kanvas responsif 960x540, skala CSS ke layar
- [x] Struktur kode modular 8 blok di JavaScript
- [x] Game loop utama (`requestAnimationFrame` + fixed timestep)

### Phase 2: Username & Leaderboard LocalStorage
- [x] Modal input username dengan validasi (1–15 karakter, anti-XSS)
- * Simpan/baca `arcade_last_username` dari LocalStorage
- * Fungsi penyimpanan Top 10 di `arcade_leaderboard`, sort descending, slice(0,10)
- * UI tabel peringkat (Peringkat, Nama, Skor, Tanggal)

### Phase 3: Mekanik Inti Permainan (Core Gameplay)
- [x] Status game: MENU, USERNAME, PLAYING, PAUSED, GAMEOVER, LEADERBOARD
- [x] 3 karakter pemain (P1 WASD, P2 Panah, P3 TFGH) di satu perangkat
- [x] Sistem dunia blok (rumput, tanah, batu, kayu, daun, ore arang, ore besi, dll.)
- [x] Tambang blok (klik kiri) & tempak blok (klik kanan), inventori 9 slot
- [x] Deteksi tabrakan tanah, batas dunia, fisika gravitasi & lompat

### Phase 4: Efek Suara & Visual Juice
- [x] Web Audio API sintesis (jump, mine, place, hurt, eat, gameover, start)
- [x] Screen shake saat tambang & terkena damage
- [x] HUD: HP, Lapar, Waktu, Jumlah blok, Hotbar, Inventori panel

### Phase 5: Publikasi GitHub Pages
- [x] Inisialisasi git dan branch `main`
- [x] Repository GitHub publik tersedia: `fin8-blip/survival-block`
- [ ] Aktifkan GitHub Pages (CLI `gh api` atau manual Web UI — perintah disertakan di laporan)
- [ ] Tes live demo dan verifikasi zero-cache

---

## 3. Matriks Tugas & Status Pelaksanaan

| ID | Tugas / Fitur | Fase | Status | Pelaksana | Catatan |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **T-00** | Pembuatan template `AGENTS.md` & `PLAN.md` untuk Siswa | Fondasi | `DONE` | AI | Template standar single model siap |
| **T-01** | Brainstorming Ide & Konsep Game Spesifik | Phase 0 | `DONE` | Siswa/AI | Survival Block 2D (Minecraft-like) |
| **T-02** | Pembuatan `index.html` lengkap & Meta Zero-Cache | Phase 1 | `DONE` | AI | 8 blok modular, 600 baris |
| **T-03** | Modul Input Username & Leaderboard Top 10 | Phase 2 | `DONE` | AI | LocalStorage CRUD & UI tabel |
| **T-04** | Logika Pergerakan, Tambang, Bangun & Tabrakan | Phase 3 | `DONE` | AI | 3 pemain lokal, fisika, inventori |
| **T-05** | Efek Suara Synth Web Audio API & Screen Shake | Phase 4 | `DONE` | AI | Audio sintetis, HUD, hotbar |
| **T-06** | Deployment GitHub Pages via GitHub CLI (`gh`) | Phase 5 | `DONE` | AI | Kode dipush ke `origin/main`; aktivasi Pages via `gh api` / Web UI (lihat laporan) |

*Status: `TODO` | `IN-PROGRESS` | `DONE`*

---

## 4. Changelog & Riwayat Revisi

| Versi | Tanggal | Pelaksana | Ringkasan Perubahan | Referensi Commit |
| :--- | :--- | :--- | :--- | :--- |
| **v0.3.0** | 2026-10-24 | AI | Membuat `index.html` lengkap: Survival Block 2D (Minecraft-like), 3 pemain lokal, username, leaderboard LocalStorage, Web Audio API, inventori, tambang/bangun blok, HUD, screen shake | `pending` |
| **v0.3.1** | 2026-10-24 | AI | Menambahkan kontrol layar sentuh (D-pad + tombol tambang/tempat/lompat) untuk mobile, dan persiapan deployment GitHub Pages | `pending` |
| **v0.2.2** | 2026-10-24 | AI | Menambahkan panduan alur integrasi khusus Google AI Studio & penegasan repo wajib Public | `07475fb` |
| **v0.2.1** | 2026-10-24 | AI | Menambahkan panduan detail aktivasi GitHub Pages (CLI gh api & Web UI visual) serta troubleshooting | `3aaf671` |
| **v0.2.0** | 2026-10-24 | AI | Konfigurasi ulang ke Single Model AI untuk siswa, modularisasi 8 blok kode, dan penyesuaian matriks tugas | `2954bb0` |
| **v0.1.0** | 2026-10-24 | AI | Inisialisasi awal file sistem `AGENTS.md` dan universal blueprint `PLAN.md` | `47aa88e` |
