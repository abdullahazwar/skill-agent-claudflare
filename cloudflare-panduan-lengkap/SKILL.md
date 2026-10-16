---
name: cloudflare-panduan-lengkap
description: Panduan Cloudflare berbahasa Indonesia dalam Markdown saja untuk Workers, Pages, Wrangler, D1, KV, R2, Durable Objects, Queues, Workflows, Cron, Workers AI, Vectorize, AI Gateway, DNS, TLS, Access, Tunnel, WAF, Turnstile, observability, biaya, backup, GitHub dan bot Telegram. Gunakan untuk belajar, merancang, mengaudit atau memandu pekerjaan Cloudflare/claudflare. Paket tidak memuat kode, konfigurasi, script, credential atau identitas akun pengguna.
---

# Cloudflare Panduan Lengkap

Gunakan bahasa Indonesia sederhana. Muat referensi sesuai tugas. Paket ini hanya instruksi Markdown, bukan aplikasi, konfigurasi atau akses ke akun. Baca [privasi dan batas paket](references/privasi-dan-batas-skill.md) sebelum mengubah atau membagikannya.

## Alur inti

1. Tentukan hasil: belajar, rancangan, audit, atau pekerjaan aplikasi yang diminta terpisah.
2. Untuk panduan, jelaskan tujuan, pilihan layanan, langkah, hasil yang diharapkan dan cara memeriksa, tanpa kode/config siap jalan.
3. Jangan login, membuat resource, mengubah DNS/billing atau deploy hanya karena membuat/memasang skill.
4. Jika kelak ada permintaan aplikasi nyata, baca aturan repo, status, arsitektur dan test secara terarah. Pertahankan perubahan serta data pengguna.
5. Tentukan target secara privat dari alat resmi, tanpa menebak atau menerbitkan ID akun/resource dan endpoint pribadi.
6. Periksa dokumentasi resmi terkini untuk sintaks, API, harga, batas dan model.
7. Pilih layanan sesedikit kebutuhan dan siapkan validasi serta pemulihan sesuai dampak.
8. Verifikasi pekerjaan yang memang diizinkan. Laporkan bukti, pengujian nyata dan batas yang tersisa.

## Peta panduan

| Kebutuhan | Referensi |
| --- | --- |
| Dari nol dan pemasangan | [Dari nol dan pemasangan](references/mulai-dan-instalasi.md) |
| Pemilihan layanan | [Pemilihan layanan](references/arsitektur-produk.md) |
| Wrangler, binding dan environment | [Wrangler, binding dan environment](references/wrangler-konfigurasi.md) |
| Workers, Static Assets dan Pages | [Workers, Static Assets dan Pages](references/workers-dan-web.md) |
| D1, relasi, stok dan transaksi | [D1, relasi, stok dan transaksi](references/d1-dan-data.md) |
| KV, cache dan TTL | [KV, cache dan TTL](references/kv-dan-cache.md) |
| R2, upload dan media | [R2, upload dan media](references/r2-dan-media.md) |
| Cron, DO, Queues dan Workflows | [Cron, DO, Queues dan Workflows](references/jadwal-dan-background.md) |
| Bot Telegram dan request saat idle | [Bot Telegram dan request saat idle](references/bot-telegram-dan-idle.md) |
| DNS, domain dan TLS | [DNS, domain dan TLS](references/domain-dns-dan-tls.md) |
| Secret, Access, WAF dan Turnstile | [Secret, Access, WAF dan Turnstile](references/keamanan-dan-akses.md) |
| AI, RAG, Vectorize dan Gateway | [AI, RAG, Vectorize dan Gateway](references/ai-dan-otomasi.md) |
| GitHub dan deployment terpisah | [GitHub dan deployment terpisah](references/github-dan-deploy.md) |
| Log, pengujian dan performance | [Log, pengujian dan performance](references/debugging-dan-observability.md) |
| Biaya dan kuota | [Biaya dan kuota](references/biaya-dan-kuota.md) |
| Backup, retensi dan pemulihan | [Backup, retensi dan pemulihan](references/backup-dan-operasi.md) |
| Resep proyek konseptual | [Resep proyek konseptual](references/resep-proyek.md) |
| Dokumentasi resmi | [Dokumentasi resmi](references/sumber-resmi.md) |
| Privasi dan batas publikasi | [Privasi dan batas publikasi](references/privasi-dan-batas-skill.md) |

## Prinsip teknis

- Gunakan binding untuk akses data di Worker dan alat administrasi untuk pengelolaan resource.
- Pilih D1 atau Durable Objects untuk koordinasi kuat; KV bukan lock atau sumber stok/saldo atomik.
- Pisahkan data utama, cache, retensi dan backup. TTL cache tidak menghapus transaksi D1.
- Verifikasi identitas pemilik pada seluruh operasi server, ekspor, job dan akses media.
- Gunakan webhook serta penerimaan tahan gangguan untuk bot. Bedakan HTTP, cron, retry dan operasi storage saat mendiagnosis idle.
- Tangani pekerjaan penting dengan mekanisme durable yang sesuai; jangan menjanjikan tepat satu kali pengiriman eksternal tanpa dukungan end-to-end.
- Pisahkan staging dan produksi. Deployment kode tidak otomatis memulihkan data atau secret.
- Jangan menjamin gratis, nol request, atau keberhasilan runtime tanpa bukti.

## Isi dan batas

Pertahankan hanya SKILL.md serta referensi .md. Jangan menambahkan kode contoh, script, JSON/JSONC/TOML, workflow YAML, skema SQL, installer, auth store atau environment file. Jangan menaruh nilai credential, Account ID, Zone ID, resource ID, domain pribadi, atau data pelanggan dalam dokumen.

Jika pengguna meminta panduan saja, hasilnya adalah penjelasan tertulis. Implementasi atau deployment aplikasi memerlukan tugas yang jelas pada repo aplikasi dan tidak disimpan di paket skill ini.
