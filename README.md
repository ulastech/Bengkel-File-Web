# Bengkel File (versi web)

Versi murni client-side dari Bengkel Berkas — jalan sepenuhnya di peramban (browser), tanpa server, tanpa Python, tanpa LibreOffice. Cocok untuk hosting statis (GitHub + Cloudflare).

Semua proses (buka proteksi, konversi format) terjadi **di komputer/perangkat pengguna sendiri** — tidak ada file yang dikirim ke server manapun.

## Fitur

- **Buka Proteksi PDF** — untuk PDF yang bisa dibuka tanpa password tapi dibatasi print/copy/edit: merender ulang tiap halaman jadi PDF baru tanpa enkripsi. Untuk PDF yang perlu password saat dibuka, password yang benar wajib diisi.
- **Buka Proteksi DOCX/XLSX** — menghapus pengaturan "Restrict Editing" / "Protect Sheet/Workbook" dari file yang tidak terenkripsi penuh.
- **Konversi format** — PDF → DOCX (teks) / gambar per halaman, DOCX → PDF / TXT, XLSX → CSV/JSON, CSV → XLSX, gambar → PDF.

## Batasan penting

Ini **bukan** alat pembobol password. Kalau file dienkripsi dengan password buka yang tidak diketahui, alat ini tidak bisa membukanya. Gunakan hanya untuk file milik sendiri atau yang izin mengubahnya sudah didapat.

## Deploy

Sama seperti Suratku/MarginXL: push ke GitHub, hubungkan ke Cloudflare (Workers & Pages → Continue with GitHub → pilih repo ini), build command kosong, deploy command `npx wrangler deploy` (sudah ada `wrangler.toml`).

## package.json

File `package.json` di repo ini **hanya untuk keperluan tracking versi oleh GitHub Dependabot** (supaya dapat alert kalau ada CVE baru di salah satu library yang dipakai). Ini bukan untuk build atau instalasi — aplikasi tetap murni client-side, semua library dimuat langsung dari CDN (cdnjs, cdn.sheetjs.com) lewat tag `<script>` di `index.html`, dengan Subresource Integrity (SRI). Tidak perlu `npm install` untuk menjalankan atau mengembangkan project ini.
