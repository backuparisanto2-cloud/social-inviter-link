# Impor repo twinkle-thread-sync ke proyek ini

Repo `backuparisanto2-cloud/twinkle-thread-sync` bisa diakses publik dan sudah berhasil diunduh. Isinya aplikasi manajemen kos/gedung (kamar, tenant, pendapatan, pengeluaran, jurnal umum, laporan, denah lantai) dengan stack yang sama persis dengan proyek ini (TanStack Start + Tailwind v4 + shadcn + Supabase). Proyek saat ini masih template kosong (hanya halaman index placeholder, tanpa backend).

## Yang akan dikerjakan

1. **Aktifkan Lovable Cloud** di proyek ini — repo memakai database, autentikasi, dan penyimpanan file, jadi backend baru harus dibuat lebih dulu.
2. **Salin seluruh kode aplikasi** dari repo: 12 halaman (`/`, kamar, kamar detail, tenant, pendapatan, pengeluaran, jurnal, laporan, denah, fasilitas, kelola), ~25 komponen aplikasi, komponen UI shadcn, dan seluruh isi `src/lib` (logika jurnal, ekspor Excel/PDF, kompresi gambar, kolom laporan, dsb).
3. **Salin aset publik**: ikon aplikasi, manifest PWA, gambar denah lantai 1–3 + rooftop, gambar splash.
4. **Pasang dependensi tambahan** yang belum ada di proyek ini (jspdf, jspdf-autotable, dan paket lain dari `package.json` repo).
5. **Terapkan ulang 5 migrasi database** dari `supabase/migrations` repo ke backend baru, berikut bucket storage dan kebijakan akses yang didefinisikan di dalamnya.
6. **Verifikasi**: build bersih, halaman utama tampil, dan navigasi antar halaman berfungsi.

## Catatan penting

- **Data tidak ikut**: repo hanya berisi struktur tabel, bukan isi database atau file yang sudah diunggah. Backend baru akan kosong. Kalau data lama perlu dibawa, itu proses ekspor/impor terpisah.
- File `.env` bawaan repo tidak dipakai; kredensial backend baru digenerate otomatis.
- Kalau ada fitur AI di repo (analisis pengeluaran & format jurnal), itu akan diarahkan ke AI Gateway proyek ini.

## Detail teknis

- Sumber: `https://github.com/backuparisanto2-cloud/twinkle-thread-sync.git`, branch `main`.
- `src/routeTree.gen.ts` tidak disalin manual — akan digenerate ulang oleh router plugin.
- `src/integrations/supabase/*` akan memakai versi yang dihasilkan Cloud, bukan versi repo (kecuali `types.ts` yang diselaraskan setelah migrasi jalan).
- Migrasi dijalankan berurutan sesuai timestamp; setiap `CREATE TABLE` di schema `public` dicek punya GRANT + RLS + policy sesuai isi migrasi asli.
