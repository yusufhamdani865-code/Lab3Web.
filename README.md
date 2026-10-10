# Laporan Praktikum 3 – CSS Dasar

**Nama** : Yusuf Hamdani
**NIM** : 312510049
**Mata Kuliah** : Pemrograman Web
**Program Studi** : Teknik Informatika, Universitas Pelita Bangsa

---

## Tujuan Praktikum

1. Memahami konsep dasar CSS.
2. Memahami aturan penulisan CSS.
3. Memahami selector sebagai pengontrol CSS.
4. Mampu membuat pengaturan CSS pada HTML.

## Langkah 1 – Membuat Dokumen HTML

Pada langkah pertama, saya membuat file `index.html` sebagai halaman praktikum. Struktur halamannya terdiri dari tiga bagian:

- `<header>` berisi judul halaman,
- `<nav>` berisi tiga link menu (CSS Dasar, CSS Eksternal, HTML Dasar),
- `<div id="intro">` berisi judul "Hello World", satu paragraf, dan tombol "Informasi selengkapnya" yang memakai class `button btn-primary`.

Karena belum ada CSS sama sekali, halaman masih tampil dengan gaya bawaan browser: teks hitam, link biru bergaris bawah, dan semua elemen rata kiri.

![Langkah 1](screenshots/ss1.png)

---

## Langkah 2 – Mendeklarasikan CSS Internal

Pada langkah ini, saya menambahkan CSS internal dengan menulis tag `<style>` di dalam `<head>`. Aturan yang saya buat:

| Selector | Fungsi |
|---|---|
| `body` | Mengatur font seluruh halaman menjadi `Open Sans` (cadangan `sans-serif`) |
| `header` | Memberi tinggi minimal 80px dan garis bawah berwarna biru muda |
| `h1` | Ukuran 24px, warna biru tua `#0F189F`, rata tengah, dan padding `20px 10px` |
| `h1 i` | Hanya untuk teks miring (`<i>`) di dalam `<h1>`, diberi warna abu-abu `#6d6a6b` |

Selector `h1 i` disebut *descendant selector*, yaitu selector yang hanya berlaku pada elemen `<i>` yang berada di dalam `<h1>`. Karena itu, hanya tulisan "Inline CSS" pada judul yang berubah menjadi abu-abu, sedangkan tulisan "CSS Internal dan" tetap biru.

Setelah file disimpan dan browser di-refresh, judul menjadi biru dan rata tengah, serta muncul garis tipis di bawah header.

![Langkah 2](screenshots/ss2.png)

---

## Langkah 3 – Menambahkan Inline CSS

Inline CSS ditulis langsung pada tag HTML melalui atribut `style`. Pada langkah ini saya menambahkannya pada tag `<p>`:

```html
<p style="text-align: center; color: #ccd8e4;">
```

Dengan kode tersebut, paragraf menjadi rata tengah dan berwarna abu-biru muda. Perubahan ini hanya berlaku pada paragraf tersebut, tidak mempengaruhi elemen lain. Inilah yang membedakan inline CSS dari internal dan eksternal, yang bisa mengatur banyak elemen sekaligus.

Warna teks terlihat pucat dan sulit dibaca pada latar putih. Hal ini memang disengaja karena warna tersebut dirancang untuk latar biru yang baru ditambahkan pada Langkah 5.

![Langkah 3](screenshots/ss3.png)

---

## Langkah 4 – Membuat CSS Eksternal

Pada langkah ini, saya membuat file baru bernama `style_eksternal.css` di folder yang sama dengan `index.html`. Isinya adalah aturan untuk elemen `nav`:

```css
nav {
    background: #20A759;
    color: #fff;
    padding: 10px;
}
nav a {
    color: #fff;
    text-decoration: none;
    padding: 10px 20px;
}
nav .active,
nav a:hover {
    background: #0B6B3A;
}
```

Penjelasan singkatnya:

- `nav` memberi latar hijau pada seluruh bar menu.
- `nav a` mengubah link di dalam menu menjadi putih, menghilangkan garis bawah, dan menambah jarak antar menu.
- `nav .active, nav a:hover` memberi warna hijau tua pada menu yang aktif dan pada menu yang sedang disorot kursor (`:hover`). Tanda koma berarti dua selector memakai satu aturan yang sama.

Agar file CSS terbaca, saya menghubungkannya dengan tag `<link>` di dalam `<head>`:

```html
<link rel="stylesheet" href="style_eksternal.css" type="text/css">
```

Atribut `rel="stylesheet"` menunjukkan jenis file yang dihubungkan, sedangkan `href` berisi lokasi file CSS. Setelah browser di-refresh, menu berubah menjadi bar hijau dengan tulisan putih.

![Langkah 4](screenshots/ss4.png)

---

## Langkah 5 – Menambahkan CSS Selector (ID dan Class)

Pada `style_eksternal.css`, saya menambahkan dua jenis selector.

**ID selector** (diawali tanda `#`) untuk elemen yang bersifat unik:

```css
#intro {
    background: #418fb1;
    border: 1px solid #099249;
    min-height: 100px;
    padding: 10px;
}
#intro h1 {
    text-align: left;
    border: 0;
    color: #fff;
}
```

`#intro` mengubah `div` menjadi kotak biru berbingkai hijau. Sementara `#intro h1` hanya mengenai judul "Hello World" yang berada di dalam kotak tersebut, sehingga warnanya putih dan rata kiri.

**Class selector** (diawali tanda titik) untuk gaya yang bisa dipakai berulang:

```css
.button {
    padding: 15px 20px;
    background: #bebcbd;
    color: #fff;
    display: inline-block;
    margin: 10px;
    text-decoration: none;
}
.btn-primary {
    background: #E42A42;
}
```

Tombol memakai dua class sekaligus (`class="button btn-primary"`). Class `.button` mengatur bentuk dasar tombol, lalu `.btn-primary` menimpa warna latarnya dari abu-abu menjadi merah. Hasil akhirnya sama dengan Gambar 6 pada modul.

![Langkah 5](screenshots/ss5.png)

---

## Pertanyaan dan Tugas

### 1. Eksperimen Properti CSS

Pada `style_eksternal.css`, saya mencoba menambah beberapa properti:

```css
.button {
    border-radius: 6px;
    font-weight: bold;
}
.btn-primary:hover {
    background: #B01E32;
}
```

- `border-radius: 6px` membuat sudut tombol membulat.
- `font-weight: bold` menebalkan tulisan pada tombol.
- `.btn-primary:hover` membuat tombol berubah menjadi merah yang lebih gelap saat kursor diarahkan ke atasnya.

Selain itu, saya menambahkan `class="active"` pada link "CSS Dasar" agar menu yang sedang dibuka tampil dengan warna hijau tua.

### 2. Perbedaan `h1 {...}` dengan `#intro h1 {...}`

Perbedaannya ada pada **cakupan** dan **tingkat prioritas** selector.

| | `h1 {...}` | `#intro h1 {...}` |
|---|---|---|
| Jenis selector | Element selector | Descendant selector (ID + elemen) |
| Cakupan | Semua `<h1>` di halaman | Hanya `<h1>` yang berada di dalam elemen ber-id `intro` |
| Specificity | (0,0,1) | (1,0,1), lebih tinggi |

Pada praktikum ini ada dua `<h1>`. Aturan `h1` mengenai keduanya (biru tua dan rata tengah). Akan tetapi, `#intro h1` hanya mengenai "Hello World" dan menimpa warna serta posisinya menjadi putih dan rata kiri, karena specificity-nya lebih tinggi. Judul pada `<header>` tidak terpengaruh dan tetap biru tua rata tengah.

### 3. Prioritas Internal, Eksternal, dan Inline

Deklarasi yang ditampilkan browser adalah **inline CSS**, karena inline memiliki prioritas tertinggi. Untuk internal dan eksternal, tingkat prioritasnya sama, sehingga yang dipakai adalah yang **ditulis paling akhir** pada dokumen (prinsip *cascade*).

Contoh pada elemen `<p>` yang sama:

```css
/* eksternal (style_eksternal.css) */
p { color: green; }
```
```html
<!-- internal -->
<style> p { color: blue; } </style>

<!-- inline -->
<p style="color: red;">Teks</p>
```

Teks akan tampil **merah** karena inline mengalahkan yang lain. Jika atribut inline dihapus, hasilnya bergantung pada urutan penulisan: bila `<link>` ditulis sebelum `<style>`, teks menjadi **biru** (internal menang), tetapi bila `<link>` ditulis sesudah `<style>`, teks menjadi **hijau** (eksternal menang).

### 4. Prioritas ID dan Class pada Elemen yang Sama

Deklarasi yang ditampilkan adalah milik **ID selector**. ID memiliki specificity (1,0,0), sedangkan class hanya (0,1,0), sehingga ID selalu lebih kuat tanpa memandang urutan penulisannya.

Contoh pada `<p id="paragraf-1" class="textparagraf">`:

```css
#paragraf-1   { color: red; }
.textparagraf { color: blue; }
```

Teks akan tampil **merah**. Namun, property yang tidak bertabrakan tetap digabungkan. Misalnya, bila `.textparagraf` juga memiliki `font-size` yang tidak diatur oleh `#paragraf-1`, ukuran font dari class tetap dipakai.


## Kesimpulan

Dari praktikum ini, saya dapat memahami bahwa CSS dapat diterapkan dengan tiga cara, yaitu inline, internal, dan eksternal. Cara eksternal paling efisien karena satu file CSS dapat dipakai oleh banyak halaman. Selain itu, saya juga memahami bahwa selector berfungsi menentukan elemen mana yang terkena aturan, dan ketika beberapa aturan bertabrakan, browser menentukan pemenangnya berdasarkan specificity dan urutan penulisan.