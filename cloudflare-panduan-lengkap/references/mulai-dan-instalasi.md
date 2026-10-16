# Memakai panduan Cloudflare

Repo skill-agent-claudflare memuat folder cloudflare-panduan-lengkap. Isinya hanya SKILL.md dan referensi Markdown. Tidak ada kode, konfigurasi, installer atau workflow yang perlu dijalankan.

## Pemasangan

Salin folder skill ke lokasi discovery yang didukung agent. Untuk OpenCode, gunakan direktori skill proyek .opencode/skills atau direktori global sesuai dokumentasi instalasi. Pertahankan nama folder dan metadata. Bandingkan file jika versi bernama sama sudah ada, tanpa menimpa perubahan pengguna.

Muat SKILL.md dahulu dan baca referensi sesuai topik. Pemasangan dokumen tidak memerlukan token, login Cloudflare, Account ID atau perubahan permission.

## Belajar

Mulai dari arsitektur produk, Workers/web, lalu layanan data yang diperlukan. Gunakan keamanan, biaya, debugging dan operasi data sebagai pelengkap. Harga, batas dan API selalu diperiksa pada sumber resmi terkini.

## Pekerjaan aplikasi kelak

Jika pengguna meminta implementasi nyata, tentukan repo aplikasi serta batas tugas secara terpisah. Gunakan toolchain proyek dan dokumentasi resmi. Jangan membuat resource, menghubungkan akun, mengubah DNS/billing atau deploy hanya karena skill dipasang.

## Dashboard sebagai referensi konsep

Workers dan Pages menunjukkan aplikasi serta deployment. Pengaturan binding menghubungkan resource. Metrics/observability membantu diagnosis. Storage berisi layanan data. Billing menampilkan pemakaian aktual. DNS dan TLS mengatur domain. Baca informasi akun hanya ketika memang diperlukan dalam tugas yang diizinkan, dan jangan menerbitkan identitasnya pada repo skill.

Sumber: https://opencode.ai/docs/skills/
Sumber: https://developers.cloudflare.com/workers/
