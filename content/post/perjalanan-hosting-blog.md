+++
author = "bejo"
title = "Perjalanan hosting blog ini dari Cloudflare Pages akhirnya ke Github Pages"
date = "2023-01-19"
description = "Pindah-pindah penyedia hosting static site"
tags = [
    "cloudflare pages",
    "vercel",
    "netlify",
    "hugo",
]
categories = [
    "my-story"
]
+++
Awalnya target utama blog ini dihost ke **Cloudflare pages**, saat mencoba menghubungkan ke subdomain bejo.line.pm ternyata cloudflare meminta verifikasi TXT ke host utama, alias ke line.pm. 

Karena hanya diberikan akses ke subdomainnya, proses verifikasi domain tidak bisa dilakukan, pindah ke netlify.

Saat mendaftar menggunakan sso dari github, saya tidak bisa login ke **Netlify**. Karena merasa ada kesalahan, saya coba ganti signup menggunakan email yang sama menggunakan github yaitu email dengan domain bejo.line.pm.

Ternyata di netlify akun baru saya dianggap spam dan harus mengontak support terlebih dahulu. Prosesnya lebih dari satu hari dan membuat saya mengubah haluan lagi ke vercel.

Di **Vercel**, menurut pengalaman saya yang pernah menggunakan subdomain dari noip.com, tidak ada masalah saat proses verifikasi domain.

Ternyata anggapan saya keliru, subdomain saya yang beralamat di bejo.line.pm belum dimasukkan vercel ke penyedia subdomain gratis, jadi verifikasi CNAMEnya harus ke domain utama yang berujung tidak bisa host domain ini di Vercel.

Tidak patah arang, saya lalu memberdayakan hosting gratis dari **Natamedia**. Tapi saat proses penambahan subdomain tidak bisa dilakukan karena harus ganti DNS ke DNS punya Natamedia yang hal ini tidak bisa saya lakukan, paling banter saya hanya bisa mengubah A record saja.

### Berlabuh ke Github Pages

Selanjutnya saya mencoba github pages, sebelumnya saya pernah membuat blog Hugo di github pages yang beralamat di [ekblog.github.io](https://ekblog.github.io). Prosesnya deploynya masih manual yaitu :

- Build folder public dengan perintah `hugo --minify` dan ubah alamat public ke nama repository yaitu `ekblog.github.io`
- Punya dua git repository, pertama untuk hugo dengan nama ekblog dan kedua untuk halaman statis dengan nama ekblog.github.io
- Ketika kedua repository tadi diupdate dengan push terbaru, jadilah blog tersebut

Proses yang lumayan panjang, membingungkan dan tidak efektif. Karena pada saat itu tidak ada (belum ada) github actions.

Sekarang dengan github actions, kita cukup push ke repository utama dan nanti pada saat deployment tinggal ke menu setting repository > pages > Build and Development, pilih github actions dan cari Hugo sebagai cmsnya. 

Nanti akan dibuatkan file yml dengan nama `hugo.yml` di folder `.github/workflows`

Setelah file tersebut dibuat tinggal update repository lagi dan nanti otomatis github akan mendeploy hasilnya ke github pages kita.

### Domain tidak https

Masalah selanjutnya domain tidak https sepenuhnya, saat ini https adalah hal yang penting untuk sebuah website karena semua browser akan menampilkan pesan tidak aman jika blog belum memilikinya.

Github sendiri membuatkan sertifikat https dari Letsencrypt dan memberikan pilihan untuk *enforce Https*.

Setelah propagasi selesai dan menggunakan *enforce https*. tampilan blog jadi kacau karena ada konten dan link yang masih http.

Ternyata dipengaturan pagesnya saya harus mengubah alamat awal dari `bejo.line.pm` menjadi `https://bejo.line.pm` 

Setelah mengupdate pengaturannya, blog masih error. Saya coba mentrigger perubahan dengan rebuild ulang dengan mengupdate halaman kontak dan about, barulah blog ini bisa diakses dengan sempurna.

### Kesimpulan

Subdomain dari dnsexit saat ini hanya bisa menggunakan Github pages untuk hosting web statis seperti Hugo. Untuk netlify belum saya coba karena udah males duluan akun saya dianggap spam, mungkin diposting selanjutnya akan saya reveal bagaimana hasil percobaan hosting disana.

Untuk Vercel dan Cloudflare Pages, harus menggunakan domain utama. Jika ingin menggunakan subdomain kita harus memiliki akses ke domain utama.

Sebenarnya ada satu step percobaan lagi yang tidak saya sebutkan diatas, saya juga menggunakan hosting dari **Render** tapi karena untuk menggunakannnya harus meng-input data kartu kredit, saya tidak melanjutkan prosesnya.

Referensi :
- https://dev.to/github/how-to-host-a-static-nextjs-site-on-github-pages-4pe0
