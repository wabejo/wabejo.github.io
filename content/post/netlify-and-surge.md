+++
author = "bejo"
title = "Apakah Bisa Menggunakan Subdomain Gratis di Netlify?"
date = "2023-01-24T18:04:27+07:00"
description = "Netlify dan Surge.sh using custom subdomain"
tags = [
    "static site",
    "hosting",
    "custom-subdomain"
]
categories = [
    "my-story"
]
+++

Pada [posting sebelumnya](/post/perjalanan-hosting-blog/) saya sudah mencoba beberapa static site hosting terkenal yang banyak digunakan orang. Blog ini salah satu yang termasuk menggunakan hosting tersebut yaitu Github Pages.

## Bisakah Netlify Menggunakan Custom Subdomain?

![Netlify Homepage](https://assets-bejo.netlify.app/v1674560888/img/netlify_home_page.jpg)
Permasalahan yang masih belum terpecahkan diposting kemaren adalah apakah netlify bisa digunakan untuk hosting dengan custom domain yang domainnya berasal dari service dynamic DNS?

Jawaban singkatnya : Tidak bisa!

Percobaannya saya lakukan ketika saya ingin membuat sub dari subdomain blog ini yang tujuannya untuk me*redirect* gambar dari cdn gambar cloudinary dengan alamat assets.bejo.work.gd.

Saat ingin menginput alamat domainnya menu custom domain netlify, muncul error yang menyebutkan `pengguna lain sudah memakai domain work.gd di netlify`

Karena saya ingin menggunakan fitur redirect dari netlify, akhirnya saya mengalah dengan menggunakan subdomain bawaan dari netlify.

## Surge.sh?

![Surge.sh homepage](https://assets-bejo.netlify.app/v1674561825/img/surge.sh_home_page.jpg)
Satu lagi layanan hosting untuk statik site adalah surge.sh, cara deploynya cukup gampang, tinggal mengetikkan `surge public/folder` blog akan langsung dideploy ke alamat-blog-baru.surge.sh

Fitur ini sangat cocok bagi yang hanya ingin mendeploy web statis tanpa memperhatikan alamat domainnya, tapi jika ingin menggunakan custom domain milik sendiri bahkan custom subdomain dari layanan subdomain *dynamic dns*. Jawabannya tidak bisa.

 Untuk menggunakan custom domain dan fitur SSL, surge.sh men-*charge* sebesar $30/bulan per akun.

Harga yang lumayan mahal hanya untuk sekedar hosting web statis, apalagi blog yang anda miliki tidak terlalu banyak pengunjungnya yang berarti resource yang dibutuhkan belum terlalu banyak. Overprice!

## Kesimpulan

Ada sedikit sekali pilihan menggunakan custom subdomain gratisan bagi pengguna web statis, kecuali anda memiliki hosting sendiri atau vps.

Saat ini satu-satunya yang bisa masih Github pages.

Selanjutnya saya akan mencoba layanan dari fleek.co
