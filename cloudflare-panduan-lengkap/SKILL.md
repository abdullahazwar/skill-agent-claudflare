---
name: cloudflare-panduan-lengkap
description: Panduan Cloudflare berbahasa Indonesia untuk belajar dari nol, membangun dan memperbaiki Workers atau Pages, Wrangler, D1, KV, R2, Durable Objects, Queues, Workflows, Cron, Workers AI, Vectorize, AI Gateway, DNS, TLS, Access, Tunnel, WAF, Turnstile, observability, biaya, backup, CI/CD GitHub, dan bot Telegram. Gunakan untuk permintaan Cloudflare atau claudflare, worker, deploy, binding, free tier, request saat idle, webhook, database Cloudflare, atau pemindahan domain aplikasi Cloudflare.
---

# Cloudflare Panduan Lengkap

Selesaikan kebutuhan Cloudflare sampai hasil dapat diperiksa. Gunakan bahasa Indonesia sederhana. Jelaskan akibat perubahan besar sebelum eksekusi. Bedakan bukti dari dugaan. Ikuti format percakapan pengguna dan gunakan Markdown untuk berkas teknis.

## Alur kerja inti

1. Tentukan hasil: belajar, rancangan, implementasi, perbaikan, audit, atau deployment. Bila pengguna meminta rancangan saja, jangan mengubah akun.
2. Baca AGENTS.md, status git, konfigurasi Wrangler, package.json, lockfile, entrypoint, migrasi, dan test terkait. Cari dengan rg dahulu. Pertahankan perubahan pengguna.
3. Temukan akun, Worker, environment, domain, binding, resource, dan repositori dari konfigurasi atau alat. Jangan menebak ID. Pertahankan sistem yang sedang berjalan.
4. Periksa dokumentasi resmi terkini untuk API, perintah, harga, batas, model AI, dan konfigurasi yang digunakan. Baca [sumber resmi](references/sumber-resmi.md) dan hanya referensi topik yang diperlukan.
5. Pilih komponen sesedikit kebutuhan. Pertimbangkan satu Worker dengan Static Assets untuk aplikasi ringan baru. Pertahankan Pages pada proyek yang sudah memakainya.
6. Bentuk modul dengan interface kecil dan perilaku lengkap. Letakkan validasi, data, serta aturan bisnis pada seam yang jelas. Pakai adapter untuk layanan luar. Hindari modul yang hanya meneruskan panggilan.
7. Buat perubahan lokal, migrasi tambahan, dan jalur pemulihan. Lindungi data dan kontrak lama. Cadangkan data sebelum perubahan skema produksi yang berisiko.
8. Jalankan pemeriksaan sesuai perubahan: tipe, test perilaku, SQL lokal, build, dan wrangler deploy --dry-run. Gunakan environment terpisah untuk integrasi.
9. Deploy hanya bila instruksi pengguna mencakupnya. Membuat skill atau panduan tidak memberi izin deploy aplikasi ke Cloudflare.
10. Periksa health, domain, binding, log, alur utama, dan metrik setelah deploy. Laporkan perubahan, pengujian nyata, URL atau commit, dan batas yang tersisa.

## Peta panduan

| Kebutuhan | Referensi |
| --- | --- |
| Dari nol, dashboard, login CLI, memasang skill | [Mulai dan pemasangan](references/mulai-dan-instalasi.md) |
| Memilih layanan dan arsitektur satu Worker | [Arsitektur produk](references/arsitektur-produk.md) |
| JSONC/TOML, binding, environment, CLI | [Wrangler dan konfigurasi](references/wrangler-konfigurasi.md) |
| Runtime, API, Static Assets, Pages, UI HP | [Workers dan web](references/workers-dan-web.md) |
| SQL, stok, keuangan, migrasi, multi-user | [D1 dan data](references/d1-dan-data.md) |
| Cache, konsistensi, TTL, auto hapus | [KV dan cache](references/kv-dan-cache.md) |
| Foto menu, upload, object storage | [R2 dan media](references/r2-dan-media.md) |
| Jadwal, antrean, koordinasi, jobs panjang | [Jadwal dan background](references/jadwal-dan-background.md) |
| Bot Telegram, webhook, request saat diam | [Bot dan diagnosis idle](references/bot-telegram-dan-idle.md) |
| DNS, workers.dev, TLS, timeout | [Domain dan jaringan](references/domain-dns-dan-tls.md) |
| Secret, login, CORS, WAF, Turnstile, Tunnel | [Keamanan dan akses](references/keamanan-dan-akses.md) |
| AI, RAG, Vectorize, Gateway, PDF | [AI dan otomasi](references/ai-dan-otomasi.md) |
| GitHub, CI/CD, deploy, rollback | [GitHub dan deploy](references/github-dan-deploy.md) |
| Log, error, pengujian, performa | [Debugging dan observability](references/debugging-dan-observability.md) |
| Free tier, estimasi, tagihan | [Biaya dan kuota](references/biaya-dan-kuota.md) |
| Backup, restore, retensi, hapus data | [Backup dan operasi](references/backup-dan-operasi.md) |
| Latihan dan contoh proyek | [Resep proyek](references/resep-proyek.md) |
| API, harga, batas, changelog | [Sumber resmi](references/sumber-resmi.md) |

## Aturan pelaksanaan

- Simpan nilai rahasia sebagai secret. Jangan menaruh token, password, private key, atau webhook secret asli di kode, log, chat, URL debug, dan commit. Minta nama variabel saja bila pengguna dapat mengisi nilainya melalui dashboard.
- Pakai binding dari dalam Worker. Pakai API Cloudflare untuk administrasi resource, bukan setiap operasi data aplikasi.
- Pakai D1 atau Durable Objects untuk koordinasi kuat. Jangan memakai baca-lalu-tulis KV sebagai lock, pengurang stok, atau perlindungan transaksi ganda.
- Pisahkan data utama dari cache. TTL cache bukan retensi transaksi. SQL tidak menghapus data lama dengan sendirinya.
- Filter identitas pemilik yang diverifikasi server pada baca, edit, hapus, ekspor, job, cache key, dan object key.
- Validasi input, ukuran payload, metode HTTP, dan otorisasi. Bind parameter SQL. Kendalikan SSRF untuk input URL.
- Tunggu operasi penting. Pakai ctx.waitUntil hanya dalam batas runtime. Pakai antrean atau workflow untuk pekerjaan yang harus bertahan.
- Jangan menambah polling, cron, self-fetch, atau Worker tanpa kebutuhan. Pakai webhook untuk bot. Hentikan tick jadwal setelah query due kosong.
- Kembalikan API 404/405 yang benar. Jangan membiarkan API salah mengembalikan HTML SPA dengan status 200.
- Jangan menjamin gratis, tepat satu kali, atau nol request saat idle tanpa bukti. Cron, monitor, retry, dan traffic publik dapat memicu aktivitas.
- Gunakan tanggal kompatibilitas nyata pada proyek baru. Uji pembaruan tanggal pada proyek lama.
- Bila akses alat terbatas, tuntaskan pekerjaan lokal yang dapat dilakukan. Laporkan blocker spesifik. Jangan mengaku membuat repo atau deploy tanpa hasil terverifikasi.

## Resource siap pakai

| Resource | Pemakaian |
| --- | --- |
| [Starter Worker dan web](assets/worker-starter/package.json) | Salin seluruh assets/worker-starter ke aplikasi baru. Starter tidak membuat database atau cron. |
| [Contoh skema D1](assets/sql/0001_initial.sql) | Gunakan pada database baru setelah model bisnis cocok. Jangan jalankan mentah pada database produksi lama. |
| [Fragmen binding](assets/bindings.example.jsonc) | Ambil bagian yang perlu, isi ID dari hasil alat, lalu generate tipe. Ini bukan config proyek utuh. |
| [Workflow deploy](assets/deploy-worker.yml.example) | Salin ke repo aplikasi setelah package dan lockfile siap. Sesuaikan direktori dan secret. |
| [Pemeriksa proyek](scripts/doctor.py) | Jalankan python3 <skill-dir>/scripts/doctor.py <project-dir>. Tambahkan --json untuk hasil terstruktur. Alat tidak mengubah berkas atau resource. |
| [Estimasi pemakaian](scripts/estimasi.py) | Jalankan python3 <skill-dir>/scripts/estimasi.py --help. Hasil berupa proyeksi, bukan tagihan atau batas paket. |

## Rute cepat

- Bot terus meminta request: bedakan fetch, scheduled, queue, alarm, outbound fetch, dan operasi storage sebelum mengubah trigger.
- Bot lambat: ukur tiap tahap, kecilkan round trip, batch SQL, batasi data, dan pisahkan AI dari konfirmasi transaksi.
- Domain gagal setelah subdomain akun diganti: cek hostname baru, DNS, route, sertifikat, webhook, origin, dan URL frontend.
- Menu, stok, produksi, belanja tidak sinkron: tentukan ID relasi dan transaksi perubahan. Simpan snapshot harga penjualan.
- Banyak pengguna: uji isolasi dua akun, callback, konflik update, kuota agregat, dan batas provider.

## Bentuk hasil

Untuk panduan, berikan langkah, perintah yang dapat disalin, hasil yang diharapkan, dan langkah berikutnya. Untuk implementasi, berikan hasil nyata, test yang dijalankan, commit atau deployment, serta batas yang belum diuji. Jangan memasukkan rincian internal ke UI produk jika tidak membantu pemakai.
