# Sistem Guru Bertugas (SIGAP)

[![Lesen: MIT](https://img.shields.io/badge/lesen-MIT-green.svg)](LICENSE)

**Demo:** https://sistem-guru-bertugas.pages.dev

> 🇬🇧 *Open-source weekly duty-teacher reporting system for Malaysian schools. Pure HTML/CSS/JS, no build step. Contributions welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).*
>
> 🇬🇧 *English version for private & international schools: [duty-teacher-system](https://github.com/dontopa/duty-teacher-system) · [demo](https://duty-teacher-system.pages.dev).*

Sistem laporan **guru bertugas mingguan** untuk sekolah. Guru bertugas mengisi laporan **mengikut hari** (Isnin–Jumaat) dalam 9 langkah, dan pihak pengurusan menyemak serta mengesahkannya.

## Aliran laporan harian (9 langkah)

1. Laporan kehadiran guru
2. Laporan kehadiran pelajar (mengikut kelas, peratus dikira automatik)
3. Laporan pelajar tidak sihat & ke klinik
4. Laporan keadaan sekeliling sekolah
5. Laporan kehadiran pelawat (jika ada)
6. Laporan disiplin (lewat hadir, ponteng, dll.)
7. Laporan aktiviti harian
8. Pengesahan pihak pengurusan (akuan guru → sahkan / kembalikan oleh pentadbir)
9. Tamat (ringkasan, sedia dicetak)

## Peranan

| Peranan | Boleh buat |
|---|---|
| **Guru** (tema hijau teal) | Urus 2–3 kelas sahaja. Lihat minggu bertugas & status setiap hari, isi laporan, hantar untuk pengesahan, buat pembetulan, cetak laporan |
| **Pentadbir** (tema indigo) | Papan pemuka analitik, sahkan / kembalikan laporan dengan ulasan, urus jadual bertugas, urus pengguna & kelas yang diurus setiap guru, **tambah / buang pelajar**, tetapan sekolah |

### Mudah untuk guru
- **Pilih, bukan taip:** untuk kes kesihatan & disiplin, guru pilih kelas dahulu, kemudian pilih nama pelajar dari dropdown. Hanya kelas guru itu dipaparkan.
- **Kehadiran ikut nama:** semua pelajar dianggap hadir; guru ketik nama yang tidak hadir, kemudian tanda "Kehadiran disemak".
- **Simpan progres & sambung semula:** setiap langkah ada butang *Simpan progres*, dan semua perubahan juga disimpan automatik. Jika aplikasi tertutup, guru dibawa terus ke langkah terakhir apabila membukanya semula.
- **Tiada mod gelap:** paparan cerah dan tulisan lebih besar supaya mudah dibaca.

## Akaun demo

| Peranan | E-mel | Kata laluan |
|---|---|---|
| Pentadbir (Pengetua) | `admin@sigap.edu.my` | `admin123` |
| Pentadbir (PK HEM) | `kamal@sigap.edu.my` | `admin123` |
| Guru (bertugas minggu ini) | `aminah@sigap.edu.my` | `guru123` |
| Guru (bertugas minggu ini) | `lim@sigap.edu.my` | `guru123` |
| Guru lain | `rajesh@`, `nurul@`, `faizal@`, `mariam@sigap.edu.my` | `guru123` |

Data contoh: 6 kelas × 10 pelajar, setiap guru mengurus 2–3 kelas, jadual 7 minggu, dan laporan dalam semua status (disahkan / menunggu / perlu pembetulan / draf), dijana relatif kepada tarikh hari ini.

## Cara jalankan

Tiada build step — HTML, CSS & JavaScript tulen.

```bash
python3 -m http.server 8000
# buka http://localhost:8000
```

## Deploy ke Cloudflare Pages (percuma)

Laman ini statik, jadi Cloudflare Pages boleh hos terus dari GitHub dengan domain percuma `*.pages.dev`.

1. Log masuk ke [dash.cloudflare.com](https://dash.cloudflare.com) → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Pilih repo `sistem-guru-bertugas`.
3. Tetapan build:
   - Framework preset: **None**
   - Build command: *(kosongkan)*
   - Build output directory: `/`
4. **Save and Deploy**. Laman akan siap di `https://<nama-projek>.pages.dev`, dan setiap `git push` ke `main` akan deploy semula secara automatik.

Atau guna CLI:

```bash
npx wrangler pages deploy . --project-name sistem-guru-bertugas
```

## Struktur

```
index.html          Landing page (animasi & motion)
login.html          Log masuk + akaun demo
app.html            Papan pemuka (SPA, hash routing)
assets/css/         landing.css, app.css (tema guru/pentadbir & paparan mudah alih)
assets/js/data.js   Lapisan data + penjana data contoh
assets/js/app.js    Logik aplikasi (dashboard, wizard 9 langkah, pengesahan, jadual, kelas & pelajar, pengguna, tetapan)
assets/img/         logo.svg, favicon.svg
```

> **Nota:** Ini versi demo — data disimpan dalam `localStorage` pelayar dan kata laluan tidak disulitkan. Untuk kegunaan sebenar, lapisan `assets/js/data.js` perlu disambungkan ke backend (cth. Laravel / Supabase / Firebase) dengan pengesahan selamat.

## Sumbangan

Cikgu, pelajar dan developer dialu-alukan menyumbang — laporkan bug, cadangkan ciri, atau hantar pull request. Baca [CONTRIBUTING.md](CONTRIBUTING.md) dahulu.

## Lesen

[MIT](LICENSE) © 2026 dontopa ([designbywan.com](https://designbywan.com))
