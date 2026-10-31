# PLAN.md — Universal Arcade Game Roadmap (Untuk Siswa)

Dokumen ini adalah rencana kerja universal dan log perkembangan proyek pembuatan game arcade voxel 3D dalam 1 file `index.html`. Dokumen ini diperbarui secara otomatis oleh AI setiap kali ada perubahan kode sebelum push ke GitHub.

---

## 1. Ikhtisar Game

- **Judul Game**: **Survival Block 3D**
- **Genre**: Voxel Sandbox / Survival 3D (Minecraft-like)
- **Format**: Single-File HTML (`index.html`) tanpa dependensi eksternal (WebGL ditulis manual)
- **Platform**: Web Browser (Desktop & Mobile Responsive)
- **Audio**: Web Audio API Sintetis
- **Penyimpanan**: LocalStorage (`arcade_leaderboard`, `arcade_last_username`)
- **Kebijakan Caching**: Zero-Cache (`no-cache, no-store, must-revalidate`)
- **Deployment**: GitHub Pages (Branch `main`, path `/`)

---

## 2. Fase Pengembangan Universal

### Phase 0: Brainstorming & Desain Game
- [x] Siswa menentukan ide & tema game: **Survival Block 3D** (voxel Minecraft-like: tambang, bangun, bertahan)
- [x] Kontrol: First-person (WASD + mouse look + pointer lock), klik kiri tambang, klik kanan pasang, sentuh untuk mobile
- [x] Aturan: Tambang blok dapat item, bangun, jaga HP & Lapar, fall damage, bertahan selama mungkin
- [x] Gaya visual: Voxel 3D bertekstur pixel, fog, ambient occlusion, responsive HP & laptop

### Phase 1: Setup Single-File `index.html`
- [x] Kerangka HTML5 dengan meta tag **Zero-Cache**
- [x] Kanvas fullscreen WebGL + renderer voxel buatan sendiri (tanpa library eksternal)
- [x] Struktur kode modular (config, audio, input, world gen, meshing, fisika, leaderboard, UI, loop)
- [x] Game loop utama (`requestAnimationFrame` + fixed timestep)

### Phase 2: Username & Leaderboard LocalStorage
- [x] Modal input username dengan validasi (1–15 karakter, anti-XSS)
- * Simpan/baca `arcade_last_username` dari LocalStorage
- * Fungsi penyimpanan Top 10 di `arcade_leaderboard`, sort descending, slice(0,10)
- * UI tabel peringkat (Peringkat, Nama, Skor, Waktu, Tanggal)

### Phase 3: Mekanik Inti Permainan (Core Gameplay)
- [x] Status game: MENU, USERNAME, PLAYING, PAUSED, GAMEOVER, LEADERBOARD
- [x] Pemain first-person 3D: WASD, mouse look (pointer lock), sprint, lompat
- [x] Dunia voxel 96x48x96 dengan terrain noise, pohon, ore arang & besi, bedrock
- [x] Tambang blok (klik kiri) & pasang blok (klik kanan), raycast DDA, inventori 9 slot, blok highlight
- [x] Fisika AABB per-sumbu: gravitasi, tabrakan, step, fall damage, batas dunia

### Phase 4: Efek Suara & Visual Juice
- [x] Web Audio API sintesis (jump, mine, place, hurt, eat, gameover, start)
- [x] Screen shake saat tambang & terkena damage
- [x] HUD: HP, Lapar, Waktu, Jumlah blok, Hotbar, Inventori panel

### Phase 5: Publikasi GitHub Pages
- [x] Inisialisasi git dan branch `main`
- [x] Repository GitHub publik tersedia: `fin8-blip/survival-block`
- [x] Aktifkan GitHub Pages (CLI `gh api` atau manual Web UI — perintah disertakan di laporan)
- [x] Tes live demo dan verifikasi zero-cache

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
| **T-06** | Deployment GitHub Pages via GitHub CLI (`gh`) | Phase 5 | `DONE` | AI | Kode dipush ke `origin/main`; Pages aktif di https://fin8-blip.github.io/survival-block/ |
| **T-07** | Perbaikan bug fatal "game tidak bisa dimulai" | Phase 3 | `DONE` | AI | `new Array(62.5)` RangeError, inisialisasi grid dunia, satu game loop, koordinat mouse vs kamera, CSS HUD/kontrol mobile |
| **T-08** | Migrasi total ke voxel 3D first-person (WebGL) | Phase 3 | `DONE` | AI | Renderer WebGL manual, texture atlas prosedural, AO, fog, pointer lock, raycast tambang/pasang, fisika AABB, dunia 96x48x96 |

*Status: `TODO` | `IN-PROGRESS` | `DONE`*

---

## 4. Changelog & Riwayat Revisi

| Versi | Tanggal | Pelaksana | Ringkasan Perubahan | Referensi Commit |
| :--- | :--- | :--- | :--- | :--- |
| **v0.3.0** | 2026-10-24 | AI | Membuat `index.html` lengkap: Survival Block 2D (Minecraft-like), 3 pemain lokal, username, leaderboard LocalStorage, Web Audio API, inventori, tambang/bangun blok, HUD, screen shake | `8666244` |
| **v0.3.1** | 2026-10-24 | AI | Menambahkan kontrol layar sentuh (D-pad + tombol tambang/tempat/lompat) untuk mobile, dan persiapan deployment GitHub Pages | `c9c3cc0` |
| **v0.3.2** | 2026-10-31 | AI | GitHub Pages aktif (branch `main`, root) dan live di https://fin8-blip.github.io/survival-block/ | - |
| **v0.4.0** | 2026-10-31 | AI | Fix fatal: `new Array(62.5)` RangeError pada `initWorld`, grid dunia diinisialisasi sebelum generate pohon, ukuran dunia 2048x540, satu game loop (`ensureLoop`), koordinat mouse memakai kamera, kurung `ctx.save/restore`, tambang/tempat tidak lagi diblokir cooldown ganda, kecepatan pemain di-clamp, CSS HUD/hotbar/inventori/kontrol mobile, kolom waktu leaderboard | - |
| **v0.5.0** | 2026-10-31 | AI | **Rewritten to 3D**: engine voxel WebGL manual (shader, matriks, texture atlas 16px prosedural, ambient occlusion, fog), dunia 96x48x96 + pohon + ore, first-person pointer lock, DDA raycast tambang/pasang, fisika AABB + fall damage, highlight blok, hotbar 9 slot, kontrol mobile touch-look, leaderboard & username tetap | - |
| **v0.2.2** | 2026-10-24 | AI | Menambahkan panduan alur integrasi khusus Google AI Studio & penegasan repo wajib Public | `07475fb` |
| **v0.2.1** | 2026-10-24 | AI | Menambahkan panduan detail aktivasi GitHub Pages (CLI gh api & Web UI visual) serta troubleshooting | `3aaf671` |
| **v0.2.0** | 2026-10-24 | AI | Konfigurasi ulang ke Single Model AI untuk siswa, modularisasi 8 blok kode, dan penyesuaian matriks tugas | `2954bb0` |
| **v0.1.0** | 2026-10-24 | AI | Inisialisasi awal file sistem `AGENTS.md` dan universal blueprint `PLAN.md` | `47aa88e` |
