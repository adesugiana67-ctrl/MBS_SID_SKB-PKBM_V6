# SKB/PKBM Sumedang 2026 — Versi Statis untuk GitHub Pages

Versi static (HTML + CSS + JS murni) dari aplikasi **Standar Pengelolaan Satuan Pendidikan Non Formal SKB/PKBM 2026** Dinas Pendidikan Kabupaten Sumedang. Folder ini siap di-host di **GitHub Pages** tanpa server / database.

---

## 📂 Struktur File

```
docs/
├── index.html           # Beranda + grafik laporan 3 kategori
├── akreditasi.html      # Tabel Data Akreditasi
├── peserta-didik.html   # Tabel Peserta Didik SPMB ATS/APS
├── e-rapor.html         # Tabel E-Rapor 8 SNP
├── keterangan.html      # Halaman Keterangan + Reset Data
└── assets/
    ├── styles.css       # Style + print rules
    ├── data.js          # localStorage "DB" + seed data
    ├── components.js    # Navbar, Modal, Toolbar (Cetak/PDF/Input)
    └── charts.js        # SVG charts (bar + donut)
```

---

## 🚀 Cara Hosting di GitHub Pages

### Opsi 1 — Folder `/docs` (paling mudah, sudah disiapkan)

1. Push project ke repository GitHub kamu.
2. Buka **Settings → Pages**.
3. Pada **Source** pilih **Deploy from a branch**.
4. Pilih branch `main` dan folder **`/docs`**, klik **Save**.
5. Tunggu 1–2 menit, situs akan tersedia di:
   `https://<username>.github.io/<nama-repo>/`

### Opsi 2 — Branch `gh-pages`

1. Salin isi folder `docs/` ke root branch `gh-pages`.
2. Settings → Pages → Source: `gh-pages` → `/ (root)`.

### Opsi 3 — Repo khusus user/organization

Beri nama repo `<username>.github.io`, salin isi `docs/` ke root branch `main`. Akan otomatis live di `https://<username>.github.io/`.

---

## ✨ Fitur

- Navbar dropdown **Beranda / Informasi ▼ / Keterangan**
- **Beranda** menampilkan 4 KPI + 3 grafik laporan (Akreditasi, Peserta Didik, E-Rapor)
- **Tabel** dengan tombol:
  - 🖨️ **Cetak** (print-friendly, navbar otomatis disembunyikan)
  - 📄 **Unduh PDF** (jsPDF + AutoTable, kop dinas + timestamp)
  - ➕ **Input Data** (modal dengan dropdown opsi)
  - ✏️ **Edit** & 🗑️ **Hapus** per baris
- Data tersimpan otomatis di **localStorage** browser
- Mobile-friendly (Tailwind responsive)
- Tidak butuh server / database

---

## 🧠 Prompt Generator (untuk dipakai di AI-builder lain)

Jika kamu ingin AI lain meng-generate ulang versi statis ini, gunakan prompt berikut:

> **Buatkan versi static HTML (siap di-host di GitHub Pages) untuk aplikasi "Dinas Pendidikan Kabupaten Sumedang – Standar Pengelolaan Satuan Pendidikan Non Formal SKB/PKBM Tahun 2026", dengan struktur file di folder `docs/`:**
>
> 1. **Tema warna**: navbar gelap (`bg-slate-900`) dengan border bawah biru (`border-blue-500`), background `bg-slate-100`, kartu putih dengan shadow.
> 2. **Navbar**: logo bulat + menu **Beranda**, dropdown **Informasi ▼** (Data Akreditasi / Data Peserta Didik SPMB ATS/APS / Data E-Rapor 8 SNP SKB/PKBM), dan **Keterangan**. Responsif (hamburger di mobile).
> 3. **Halaman `index.html` (Beranda)**:
>    - Header card biru dengan judul lembaga.
>    - 4 KPI card (Total Lembaga, Total Peserta Didik, Sudah Verval, Lembaga E-Rapor).
>    - 3 grafik SVG murni: bar chart distribusi akreditasi (A/B/C/TT/Belum), 2 donut (gender + verval), bar chart rata-rata 8 SNP berwarna (Baik/Cukup/Sedang/Kurang).
> 4. **Halaman `akreditasi.html`** — tabel kolom: No, NPSN, Nama Sekolah, Alamat, Kepala Sekolah, Akreditasi (A/B/C/TT/Belum, berwarna), Tahun Akreditasi, Berakhir Tahun (badge merah jika expired, hijau jika ≥3 tahun lagi), Nomor SK, Aksi.
> 5. **Halaman `peserta-didik.html`** — tabel dengan header bertingkat: Peserta Didik (Laki-Laki, Perempuan), Jumlah otomatis (badge amber), Verval (badge hijau "Sudah" / merah "Belum"), Wilayah Kecamatan & Zonasi (badge berwarna).
> 6. **Halaman `e-rapor.html`** — tabel 8 kolom SNP (SKL, S.Isi, S.Proses, S.Penilaian, S.PTK, S.Sapras, S.Pengelolaan, S.Pembiayaan), masing-masing menampilkan persentase + label kategori berwarna otomatis (≥80 Baik hijau / ≥60 Cukup amber muda / ≥40 Sedang amber / <40 Kurang merah). Kolom Keterisian: LENGKAP/BELUM LENGKAP.
> 7. **Setiap tabel** wajib punya toolbar di pojok kanan atas:
>    - Tombol **Cetak** (abu-abu, ikon printer) → `window.print()` dengan `@media print` yang menyembunyikan navbar/footer/kolom Aksi.
>    - Tombol **Unduh PDF** (merah, ikon download) → jsPDF + jspdf-autotable (CDN), landscape A4, kop "DINAS PENDIDIKAN KABUPATEN SUMEDANG", judul laporan, timestamp, header biru, baris zebra.
>    - Tombol **+ Input Data** (biru) → modal form dengan dropdown opsi sesuai kategori.
> 8. **Setiap baris tabel** punya kolom **Aksi** dengan tombol **Edit** (amber, ikon pensil) dan **Hapus** (merah, ikon trash, dengan `confirm()`).
> 9. **Halaman `keterangan.html`** — tentang sistem, kategori, fitur, legenda warna, dan tombol **Reset Semua Data**.
> 10. **Persistensi data**: gunakan `localStorage` (key `sumedang.akreditasi.v1`, `sumedang.pesertaDidik.v1`, `sumedang.eRapor.v1`) dengan seed data contoh saat pertama kali dibuka.
> 11. **Library via CDN**: Tailwind CSS Play CDN, jsPDF UMD, jspdf-autotable. Tidak ada build step, tidak ada framework.
> 12. Sertakan `README.md` dengan instruksi GitHub Pages (Settings → Pages → branch `main`, folder `/docs`).

---

## 🔧 Pengembangan Lokal

Karena ini murni static, cukup buka langsung file `docs/index.html` di browser, **atau** jalankan server kecil:

```bash
# Python 3
cd docs && python -m http.server 8080

# atau Node
npx serve docs
```

Kemudian buka `http://localhost:8080`.

---

## 📜 Lisensi

Bebas digunakan untuk lingkungan Dinas Pendidikan Kabupaten Sumedang. © 2026.
