# Mulai dan pemasangan

## Isi

- Memasang dan memanggil skill
- Menyiapkan akun dan komputer
- Menjalankan starter
- Membaca dashboard

## Memasang dan memanggil skill

Repo distribusi bernama skill-agent-claudflare. Folder skill bernama cloudflare-panduan-lengkap. Pertahankan ejaan keduanya.

Pada Codex dengan discovery skill lokal, salin folder cloudflare-panduan-lengkap ke direktori skills yang digunakan instalasi. Contoh umum ialah ~/.codex/skills/cloudflare-panduan-lengkap. Pada Work Mode, gunakan skill yang tersimpan di halaman Skills. Periksa instruksi produk bila lokasi discovery berbeda.

Muat SKILL.md dahulu, lalu referensi sesuai tugas. Berkas assets ialah template aplikasi, bukan aplikasi yang otomatis terpasang.

    Gunakan $cloudflare-panduan-lengkap. Ajarkan setup Cloudflare dari nol.
    Gunakan $cloudflare-panduan-lengkap. Buat bot Telegram satu Worker.
    Gunakan $cloudflare-panduan-lengkap. Audit request bot saat tidak dipakai.
    Gunakan $cloudflare-panduan-lengkap. Deploy tanpa mengubah data lama.

## Menyiapkan akun

1. Buat akun Cloudflare dan aktifkan autentikasi tambahan yang tersedia.
2. Pilih akun yang benar. Account ID berbeda dari Zone ID dan nama subdomain.
3. Mulai dari Workers & Pages. Domain pribadi tidak wajib untuk percobaan dengan workers.dev.
4. Lihat paket, billing dan ketersediaan produk sebelum menambah layanan. Beberapa produk memerlukan aktivasi tersendiri.
5. Untuk tim, gunakan anggota dan role. Hindari berbagi password utama.

## Menyiapkan komputer

Gunakan Node.js yang didukung Wrangler saat pemasangan, npm, git dan editor. Jalankan perintah dalam folder aplikasi. Pada Windows, perintah npm sama. Sesuaikan perintah salin berkas dengan PowerShell atau WSL.

    node --version
    npm --version
    git --version
    npm create cloudflare@latest -- aplikasi-baru
    cd aplikasi-baru
    npx wrangler --version
    npx wrangler login
    npx wrangler whoami

Wizard dapat menanyakan template, TypeScript, git dan deploy. Pilih deploy nanti bila kode masih perlu ditinjau. Login membuka autentikasi resmi. Jangan menyalin token login ke percakapan.

Untuk proyek lama, gunakan lockfile dan package manager proyek. Untuk npm dengan package-lock.json, gunakan npm ci. Jangan menjalankan generator pada folder aplikasi lama.

## Menjalankan starter

1. Salin seluruh assets/worker-starter ke folder aplikasi baru.
2. Ubah name pada wrangler.jsonc sesuai Worker.
3. Tetapkan compatibility_date pada tanggal nyata saat membuat proyek.
4. Instal dependency dari lockfile. Starter menargetkan Node 24 untuk test TypeScript native. Periksa dukungan Wrangler yang dipasang.

    npm ci
    npm run types
    npm run check
    npm test
    npm run dev

Buka http://localhost:8787, /healthz dan /api/hello. Health menghasilkan JSON dengan ok: true. API salah menghasilkan JSON 404. Test lokal starter tidak membutuhkan token bot atau database.

Starter menyertakan versi toolchain yang telah diuji dan package-lock.json. Untuk memperbarui toolchain, jalankan npm install --save-dev wrangler@latest typescript@latest, uji ulang, lalu commit perubahan package dan lockfile.

Sebelum deploy yang diminta pengguna:

    npm run build
    npx wrangler whoami
    npm run deploy

Gunakan URL hasil deploy. Jangan menebak subdomain.

## Membaca dashboard

| Area | Yang diperiksa |
| --- | --- |
| Workers & Pages | Aplikasi, deployment aktif, domain |
| Bindings/Settings | Nama binding, resource tujuan, secret |
| Metrics | Invocation, error, CPU, durasi |
| Observability | Log dan trace sesuai sampling |
| Storage & databases | D1, KV, R2 dan pemakaian |
| Billing | Paket, layanan aktif, biaya aktual |
| Domain/DNS | Record, proxy, sertifikat, route |

Label menu dapat berubah. Cari nama produk bila letaknya berbeda. Selaraskan perubahan dashboard ke konfigurasi sumber agar deploy berikutnya tidak menimpanya.

Sumber: https://developers.cloudflare.com/workers/get-started/guide/
Sumber: https://developers.cloudflare.com/workers/wrangler/install-and-update/
Sumber: https://developers.cloudflare.com/fundamentals/account/find-account-and-zone-ids/
