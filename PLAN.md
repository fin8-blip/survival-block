# PLAN.md — Universal Arcade Game Roadmap (Untuk Siswa)

Dokumen ini adalah rencana kerja universal dan log perkembangan proyek pembuatan game arcade voxel 3D dalam 1 file `index.html`. Dokumen ini diperbarui secara otomatis oleh AI setiap kali ada perubahan kode sebelum push ke GitHub.

---

## 1. Ikhtisar Game

- **Judul Game**: **Survival Block 3D**
- **Genre**: Voxel Sandbox / Survival 3D (Minecraft-like)
- **Format**: Single-File HTML (`index.html`) tanpa dependensi eksternal (WebGL ditulis manual)
- **Platform**: Web Browser — Desktop/Laptop (keyboard + mouse) & HP/Tablet (touch, deteksi otomatis)
- **Mode**: Bertahan, Kreatif (terbang + blok tak terbatas), Tantangan 3 Menit (skor 2x)
- **Audio**: Web Audio API Sintetis
- **Penyimpanan**: LocalStorage (`arcade_leaderboard`, `arcade_last_username`, `arcade_mode`)
- **Kebijakan Caching**: Zero-Cache (`no-cache, no-store, must-revalidate`)
- **Deployment**: GitHub Pages (Branch `main`, path `/`)

---

## 2. Fase Pengembangan Universal

### Phase 0: Brainstorming & Desain Game
- [x] Siswa menentukan ide & tema game: **Survival Block 3D** (voxel Minecraft-like: tambang, bangun, bertahan)
- [x] Kontrol: First-person (WASD + mouse look + pointer lock), klik kiri tambang, klik kanan pasang, sentuh untuk mobile
- [x] Kontrol HP/Tablet: geser layar untuk lihat, D-pad, tombol Tambang/Pasang/Lompat/Makan, Lari, Terbang, Turun, dan pause
- [x] Aturan: Tambang blok dapat item, bangun, jaga HP & Lapar, fall damage, bertahan selama mungkin
- [x] Mode: Bertahan (sandbox survival), Kreatif (terbang + blok tak terbatas), Tantangan 3 Menit (skor 2x, lapar cepat)
- [x] Gaya visual: Voxel 3D bertekstur pixel, fog, ambient occlusion, kaca transparan, responsif HP & laptop

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
- [x] Status game: MENU, USERNAME, PLAYING, PAUSED, GAMEOVER, LEADERBOARD + pemilihan mode
- [x] Pemain first-person 3D: WASD, mouse look (pointer lock), sprint, lompat, terbang (Kreatif)
- [x] Dunia voxel 192x48x192 dengan terrain noise, pohon, ore arang & besi, bedrock
- [x] Tambang blok (klik kiri) & pasang blok (klik kanan), raycast DDA, hotbar 9 slot, blok highlight
- [x] Fisika AABB per-sumbu: gravitasi, tabrakan, step, fall damage, batas dunia
- [x] Resource: air (laut/danau + berenang), pasir pantai, kayu + apel dari pohon
- [x] Tangan karakter first-person memegang blok/alat terpilih (animasi ayun & bob)
- [x] Inventori 36 slot + hotbar 9 slot, tukar item lewat panel inventori, palet kreatif
- [x] 22 tipe blok dan 19 item: kayu, papan, tongkat, batu, arang, besi, apel, 12 alat 3 tier
- [x] 26 resep crafting: meja kerajinan, peti, tungku, kaca, bata batu, batu poles, blok besi, lampu, alat, makanan
- [x] Stasiun crafting: resep alat butuh Meja Kerajinan terdekat, resep peleburan butuh Tungku terdekat
- [x] Tekstur HD 32px (atlas 8x8), kaca transparan, awan voxel, matahari, dan ikan berenang di air
- [x] Dunia diperluas 2x (192x48x192, 144 chunk) dengan loading bertahap

### Phase 4: Efek Suara & Visual Juice
- [x] Web Audio API sintesis (jump, mine, place, hurt, eat, gameover, start)
- [x] Screen shake saat tambang & terkena damage
- [x] HUD: HP, Lapar, Waktu, Jumlah blok, Hotbar, Inventori panel

### Phase 5: Publikasi GitHub Pages
- [x] Inisialisasi git dan branch `main`
- [x] Repository GitHub publik tersedia: `fin8-blip/survival-block`
- [x] Aktifkan GitHub Pages (CLI `gh api` atau manual Web UI — perintah disertakan di laporan)
- [x] Tes live demo dan verifikasi zero-cache

### Phase 6: Multi-Perangkat, Mode & Crafting Dalam (v0.9.0)
- [x] Deteksi otomatis HP/tablet (`pointer: coarse`) vs laptop; kontrol sentuh tidak muncul di laptop
- [x] UI responsif: safe-area, hotbar 9 slot muat di layar 360px, panel inventori/crafting bisa discroll
- [x] D-pad, tombol Tambang/Pasang/Lompat/Makan, Lari, Terbang, Turun, pause sentuh, screen shake
- [x] Mode Bertahan, Kreatif (terbang + palet 16 blok), dan Tantangan 3 Menit dengan hadiah 500 poin
- [x] Leaderboard dipisah per mode (10 skor per mode) + filter Semua/Bertahan/Tantangan
- [x] Pohon menjatuhkan kayu + apel; daun punya drop acak apel/tongkat
- [x] Tool tier Kayu/Batu/Besi dengan syarat alat, kecepatan, durability, dan drop bijih yang benar
- [x] Atlas tekstur diperluas ke 8x8 dan pass render kaca transparan ditambahkan

---

## 3. Matriks Tugas & Status Pelaksanaan

| ID | Tugas / Fitur | Fase | Status | Pelaksana | Catatan |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **T-00** | Pembuatan template `AGENTS.md` & `PLAN.md` untuk Siswa | Fondasi | `DONE` | AI | Template standar single model siap |
| **T-01** | Brainstorming Ide & Konsep Game Spesifik | Phase 0 | `DONE` | Siswa/AI | Survival Block 3D (Minecraft-like) |
| **T-02** | Pembuatan `index.html` lengkap & Meta Zero-Cache | Phase 1 | `DONE` | AI | 8 blok modular, 600 baris |
| **T-03** | Modul Input Username & Leaderboard Top 10 | Phase 2 | `DONE` | AI | LocalStorage CRUD & UI tabel |
| **T-04** | Logika Pergerakan, Tambang, Bangun & Tabrakan | Phase 3 | `DONE` | AI | Fisika AABB 3D, inventori 36 slot, hotbar 9 |
| **T-05** | Efek Suara Synth Web Audio API & Screen Shake | Phase 4 | `DONE` | AI | Audio sintetis, HUD, hotbar |
| **T-06** | Deployment GitHub Pages via GitHub CLI (`gh`) | Phase 5 | `DONE` | AI | Kode dipush ke `origin/main`; Pages aktif di https://fin8-blip.github.io/survival-block/ |
| **T-07** | Perbaikan bug fatal "game tidak bisa dimulai" | Phase 3 | `DONE` | AI | `new Array(62.5)` RangeError, inisialisasi grid dunia, satu game loop, koordinat mouse vs kamera, CSS HUD/kontrol mobile |
| **T-08** | Migrasi total ke voxel 3D first-person (WebGL) | Phase 3 | `DONE` | AI | Renderer WebGL manual, texture atlas prosedural, AO, fog, pointer lock, raycast tambang/pasang, fisika AABB, dunia 96x48x96 |
| **T-09** | Resource air + tebang pohon + tangan karakter | Phase 3 | `DONE` | AI | Laut/danau transparan + berenang, pasir pantai, pohon tumbang sekali tebang, hand viewmodel + animasi swing/bob |
| **T-10** | Crafting & dunia HD | Phase 3 | `DONE` | AI | Panel kerajinan (papan/tongkat/kapak/beliung/sekop), durability alat, atlas 32px, awan, matahari, ikan animasi |
| **T-11** | Perluas dunia 2x + loading bertahap | Phase 3 | `DONE` | AI | 192x192 area (144 chunk), progress bar, build chunk per batch agar tidak freeze |
| **T-12** | Kontrol HP/Tablet + UI responsif | Phase 6 | `DONE` | AI | Deteksi pointer coarse, safe-area, D-pad, 4 tombol aksi, Lari/Terbang/Turun, pause sentuh, hotbar muat 360px |
| **T-13** | Tiga mode permainan + leaderboard per mode | Phase 6 | `DONE` | AI | Bertahan, Kreatif (terbang + 16 blok palet), Tantangan 3 Menit (skor 2x + bonus 500); filter papan peringkat |
| **T-14** | Crafting dalam ala Minecraft | Phase 6 | `DONE` | AI | 26 resep, 22 blok, 19 item, stasiun Meja/Tungku, tool 3 tier, durability, syarat alat & drop bijih |
| **T-15** | Inventori 36 slot + hotbar swap | Phase 6 | `DONE` | AI | Grid 9x4 desktop / 6 kolom mobile, klik baris 2+ untuk tukar ke hotbar, palet kreatif |
| **T-16** | Pohon menghasilkan apel + tekstur blok baru | Phase 6 | `DONE` | AI | Tebang pohon dapat kayu + apel, daun drop acak, atlas 8x8, kaca transparan, meja/tungku/peti/lampu/bata/besi |

*Status: `TODO` | `IN-PROGRESS` | `DONE`*

---

## 4. Changelog & Riwayat Revisi

| Versi | Tanggal | Pelaksana | Ringkasan Perubahan | Referensi Commit |
| :--- | :--- | :--- | :--- | :--- |
| **v0.9.0** | 2026-11-07 | AI | **Mobile + laptop**: deteksi kontrol sentuh, UI safe-area responsif, D-pad + tombol Tambang/Pasang/Lompat/Makan/Lari/Terbang/Turun/pause, hotbar muat 360px. **3 mode**: Bertahan, Kreatif (terbang, tambang instan, palet 16 blok), Tantangan 3 Menit (skor 2x, bonus 500). **Crafting dalam**: 26 resep, 22 blok, 19 item, Meja Kerajinan + Tungku sebagai stasiun, 12 alat 3 tier, durability, syarat alat, drop arang/bijih besi, apel dari pohon, kaca transparan, atlas 8x8, inventori 36 slot + swap hotbar, leaderboard per mode | `-` |
| **v0.3.0** | 2026-10-24 | AI | Membuat `index.html` lengkap: Survival Block 2D (Minecraft-like), 3 pemain lokal, username, leaderboard LocalStorage, Web Audio API, inventori, tambang/bangun blok, HUD, screen shake | `8666244` |
| **v0.3.1** | 2026-10-24 | AI | Menambahkan kontrol layar sentuh (D-pad + tombol tambang/tempat/lompat) untuk mobile, dan persiapan deployment GitHub Pages | `c9c3cc0` |
| **v0.3.2** | 2026-10-31 | AI | GitHub Pages aktif (branch `main`, root) dan live di https://fin8-blip.github.io/survival-block/ | - |
| **v0.4.0** | 2026-10-31 | AI | Fix fatal: `new Array(62.5)` RangeError pada `initWorld`, grid dunia diinisialisasi sebelum generate pohon, ukuran dunia 2048x540, satu game loop (`ensureLoop`), koordinat mouse memakai kamera, kurung `ctx.save/restore`, tambang/tempat tidak lagi diblokir cooldown ganda, kecepatan pemain di-clamp, CSS HUD/hotbar/inventori/kontrol mobile, kolom waktu leaderboard | - |
| **v0.5.0** | 2026-10-31 | AI | **Rewritten to 3D**: engine voxel WebGL manual (shader, matriks, texture atlas 16px prosedural, ambient occlusion, fog), dunia 96x48x96 + pohon + ore, first-person pointer lock, DDA raycast tambang/pasang, fisika AABB + fall damage, highlight blok, hotbar 9 slot, kontrol mobile touch-look, leaderboard & username tetap | - |
| **v0.6.0** | 2026-10-31 | AI | Menambahkan resource air: laut/danau transparan (pass blend terpisah), pantai pasir, berenang + kabut bawah air; menebang pohon sekali klik (batang tumbang + daun hilang, drop kayu); tangan karakter first-person memegang blok terpilih dengan animasi ayun saat tambang/pasang dan bob saat berjalan | - |
| **v0.7.0** | 2026-10-31 | AI | Crafting ala Minecraft: panel kerajinan (C), resep papan/tongkat/kapak/beliung/sekop, alat punya durability & mempercepat tambang; tekstur HD 32px; awan voxel, matahari, ikan beranimasi di air; perbaikan render air setelah pass ikan | - |
| **v0.8.0** | 2026-10-31 | AI | Dunia diperluas 2x menjadi 192x48x192 (144 chunk), pohon/awan/ikan diskalakan, jarak pandang & kabut dinaikkan, serta loading screen bertahap (progress bar) agar generate dunia tidak membekukan browser | - |
| **v0.2.2** | 2026-10-24 | AI | Menambahkan panduan alur integrasi khusus Google AI Studio & penegasan repo wajib Public | `07475fb` |
| **v0.2.1** | 2026-10-24 | AI | Menambahkan panduan detail aktivasi GitHub Pages (CLI gh api & Web UI visual) serta troubleshooting | `3aaf671` |
| **v0.2.0** | 2026-10-24 | AI | Konfigurasi ulang ke Single Model AI untuk siswa, modularisasi 8 blok kode, dan penyesuaian matriks tugas | `2954bb0` |
| **v0.1.0** | 2026-10-24 | AI | Inisialisasi awal file sistem `AGENTS.md` dan universal blueprint `PLAN.md` | `47aa88e` |
