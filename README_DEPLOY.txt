PORTAL CAMSTUDY FINAL — PETUNJUK DEPLOY

1. Upload file HTML, file SERVER.js, dan package.json ke repository yang digunakan oleh layanan Render.
2. Di Render, Build Command: npm install
3. Di Render, Start Command: npm start
4. Pada Environment Render, atur variabel berikut (isi nilainya langsung di dashboard Render; jangan masukkan ke HTML atau commit ke GitHub):
   - TEACHER_PASSWORD = password utama login guru yang kamu tentukan
   - TEACHER_ALT_PASSWORD = password alternatif (opsional)
   - OPENAI_API_KEY = API key OpenAI asli
   - OPENAI_MODEL = gpt-4.1-mini (opsional; dapat dikosongkan untuk memakai default)
5. Agar data tidak hilang ketika instance server diganti, atur persistent disk Render dan DATA_DIR sesuai lokasi mount disk jika paket hosting mendukungnya.
6. Tes https://alamat-portal/health. Jika respons berisi status ok, server berjalan.
7. Uji login guru, tambah materi, sinkronisasi siswa, impor soal, dan pembuatan soal AI setelah deployment.

KEAMANAN
- Jangan menaruh API key atau password dalam file HTML, GitHub, atau screenshot.
- Server menolak login guru jika TEACHER_PASSWORD belum diatur. Username guru bebas sesuai permintaan.
- TEACHER_ALT_PASSWORD hanya aktif bila diatur pada Environment.
- Materi dan lampiran disimpan sebagai data portal; ukuran lampiran dibatasi 1,5 MB per file.

CATATAN
Status online mengandalkan heartbeat dan sinyal tab ditutup. Browser atau jaringan yang mati mendadak dapat menunda status Offline hingga heartbeat kedaluwarsa. Pembuatan soal AI memiliki batas waktu 45 detik supaya loading tidak berjalan tanpa batas.
