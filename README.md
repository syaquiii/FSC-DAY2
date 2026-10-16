# FSC Day 2 Starter: Innova Space

Frontend Starter Camp 2026, Basic Computing Community, Fakultas Ilmu Komputer, Universitas Brawijaya.

## Tentang project ini

Ini adalah website **Innova Space** hasil Day 1 (HTML, CSS, Flexbox). Kamu tidak perlu menulis ulang apa pun dari Day 1. Hari ini kamu menambahkan dua fitur memakai JavaScript:

1. **Hamburger menu** untuk navbar di layar mobile
2. **Dark mode** untuk seluruh halaman

## Hasil akhir yang dituju

- Di layar mobile (lebar 768px ke bawah), menu navbar tersembunyi. Menu muncul saat ikon hamburger diklik dan hilang saat diklik lagi.
- Tombol **Dark Mode** mengganti tampilan seluruh halaman menjadi tema gelap, dan bisa dikembalikan ke tema terang.

## Persiapan

1. **VS Code** sudah terpasang.
2. Ekstensi **Live Server** (dari Ritwick Dey) sudah terpasang di VS Code. Cari "Live Server" di tab Extensions.
3. Browser **Chrome** (disarankan, karena DevTools-nya dipakai di panduan ini).

## Cara mengambil project (tanpa Git)

1. Di halaman repository ini, klik tombol hijau **Code**, lalu pilih **Download ZIP**.
2. Ekstrak file ZIP ke folder yang mudah kamu temukan.
3. Buka VS Code, pilih **File > Open Folder**, lalu pilih folder hasil ekstrak.
4. Klik kanan file `index.html`, pilih **Open with Live Server**.
5. Browser akan terbuka dan menampilkan halaman Innova Space. Setiap kali kamu menyimpan file (Ctrl+S), halaman memuat ulang otomatis.

Dua hal yang akan sering dipakai hari ini:

- **Console:** tekan `F12`, buka tab **Console** untuk melihat pesan dan error JavaScript.
- **Tampilan mobile:** di DevTools, tekan `Ctrl+Shift+M` (Mac: `Cmd+Shift+M`) untuk mengaktifkan device toolbar, lalu pilih ukuran seperti iPhone atau lebar 375px.

## Struktur folder

| File / folder | Isi |
|---|---|
| `index.html` | Struktur halaman (hasil Day 1). Ada komentar `TODO Day 2` di dalam navbar sebagai tempat tombol baru. |
| `style.css` | Seluruh styling (hasil Day 1). Kode CSS barumu ditulis di bagian paling bawah, di bawah garis komentar `DAY 2`. |
| `script.js` | File JavaScript yang masih hampir kosong. Sudah terhubung ke `index.html`. Di sinilah fokus utama hari ini. |
| `assets/` | Logo dan ikon (SVG). Tidak perlu diubah. |

## Cara memakai panduan ini

Setiap requirement punya pola yang sama: **Tujuan**, **Konsep singkat**, **Langkah**, **Cek hasil**, dan **Kesalahan umum**. Di bawahnya ada petunjuk bertahap yang bisa dibuka satu per satu.

Saranku, urutannya begini:

1. Baca Tujuan dan Langkah, lalu coba kerjakan sendiri.
2. Kalau buntu, buka **Hint 1** (arah berpikir, tanpa kode).
3. Masih buntu, buka **Hint 2** (kerangka kode).
4. Terakhir, buka **Kode lengkap** untuk mencocokkan hasilmu.

Mengetik sendiri jauh lebih berguna daripada menyalin. Kalau kamu menyalin, baca dulu tiap barisnya sampai paham.

---

## Misi Day 2 (checklist Time to Code)

Kerjakan berurutan dari 1 sampai 4.

- [ ] **Requirement 1:** Buat elemen navbar dengan ikon hamburger. Pastikan menu tertutup secara default di layar mobile.
- [ ] **Requirement 2:** Gunakan `classList.toggle` agar hamburger menu bisa dibuka dan ditutup.
- [ ] **Requirement 3:** Buat tombol Dark Mode.
- [ ] **Requirement 4:** Hubungkan tombol dengan class `dark` pada `body` menggunakan event listener.

---

## Requirement 1: Navbar dengan ikon hamburger

**Tujuan:** Di layar mobile, navbar menampilkan ikon hamburger (tiga garis) dan daftar menu tersembunyi. Di desktop, ikon hamburger tidak terlihat dan menu tampil seperti biasa.

**Konsep singkat:** Ikon hamburger adalah sebuah `<button>` yang berisi tiga `<span>`. Tiap `<span>` digaya menjadi satu garis. Tombol ini disembunyikan di desktop (`display: none`) dan baru ditampilkan di dalam `@media (max-width: 768px)`. Daftar menu `.nav-links` disembunyikan dengan cara yang sama, hanya di dalam media query mobile.

**Langkah:**

1. Buka `index.html`. Cari komentar `TODO Day 2` di dalam `<div class="nav-actions">`.
2. Di bawah komentar itu, tulis elemen `<button>` dengan class `hamburger`. Di dalamnya ada tiga `<span></span>`.
3. Beri atribut `type="button"`, `aria-label="Buka menu"`, dan `aria-expanded="false"`. Atribut `aria` membantu pengguna pembaca layar.
4. Buka `style.css`, scroll ke paling bawah (di bawah garis komentar `DAY 2`).
5. Tulis aturan `.hamburger`: sembunyikan dengan `display: none`, susun tiga garis secara vertikal dengan Flexbox (`flex-direction: column` dan `gap`), lalu hilangkan background dan border bawaan tombol.
6. Tulis aturan `.hamburger span`: `display: block`, lebar 24px, tinggi 3px, warna `var(--primary-color)`, dan sudut membulat.
7. Buat `@media (max-width: 768px)` baru. Di dalamnya:
   - `.navbar` diberi `flex-wrap: nowrap` supaya logo dan tombol tetap satu baris.
   - `.hamburger` diberi `display: flex` agar tampil di mobile.
   - `.nav-links` diberi `display: none` agar menu tertutup. Tempatkan dengan `position: absolute; top: 100%; left: 0; right: 0` supaya menu turun tepat di bawah header, dan susun vertikal dengan `flex-direction: column`.
8. Simpan dan lihat hasilnya di browser.

**Cek hasil:**

- Lebar jendela lebih dari 768px: tidak ada ikon hamburger, menu tampil normal di tengah navbar.
- Lebar 768px ke bawah: ikon hamburger muncul di kanan atas, daftar menu hilang.
- Klik hamburger: belum terjadi apa-apa. Itu normal, tombolnya baru berfungsi di Requirement 2.

**Kesalahan umum:**

| Gejala | Penyebab | Solusi |
|---|---|---|
| Hamburger tidak muncul di mobile | `display: flex` untuk `.hamburger` belum ada di dalam `@media`, atau tertulis sebelum aturan `display: none` | Pastikan aturan di dalam `@media` ditulis **setelah** aturan dasar `.hamburger` |
| Tiga garis berjajar menyamping | Lupa `flex-direction: column` | Tambahkan pada `.hamburger` |
| Garis tidak terlihat | `span` belum diberi `display: block`, lebar, dan tinggi | Lengkapi aturan `.hamburger span` |
| Menu hilang juga di desktop | `display: none` untuk `.nav-links` tertulis di luar media query | Pindahkan ke dalam `@media (max-width: 768px)` |
| Menu masih tampil di mobile | Aturan `.nav-links` di mobile tertimpa aturan lain | Tulis kode barumu di paling bawah `style.css` |

<details>
<summary>Hint 1: arah berpikir</summary>

Tombol hamburger butuh dua keadaan `display`: tidak tampil di desktop, tampil di mobile. Pikirkan mana yang ditulis di luar media query (aturan dasar) dan mana yang ditulis di dalamnya. Hal yang sama berlaku untuk menyembunyikan menu: hanya di mobile.

</details>

<details>
<summary>Hint 2: kode HTML</summary>

```html
<button class="hamburger" type="button" aria-label="Buka menu" aria-expanded="false">
  <span></span>
  <span></span>
  <span></span>
</button>
```

Tempel di dalam `<div class="nav-actions">`, menggantikan komentar `TODO`.

</details>

<details>
<summary>Kode lengkap: CSS</summary>

Tulis di paling bawah `style.css`:

```css
/* ===== Requirement 1: Hamburger ===== */
.hamburger {
  display: none;              /* disembunyikan di desktop */
  flex-direction: column;
  gap: 5px;
  padding: 6px;
  background: none;
  border: none;
  cursor: pointer;
}

.hamburger span {
  display: block;
  width: 24px;
  height: 3px;
  background-color: var(--primary-color);
  border-radius: 2px;
}

@media (max-width: 768px) {
  .navbar {
    flex-wrap: nowrap;        /* menu sudah tidak memakan tempat, jadi tidak perlu pindah baris */
  }

  .hamburger {
    display: flex;            /* tampil di mobile */
  }

  .nav-links {
    display: none;            /* menu tertutup secara default */
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    flex-direction: column;
    gap: 0;
    padding: 8px 16px 16px;
    background-color: var(--bg-color);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
  }

  .nav-links li {
    padding: 12px 0;
    border-bottom: 1px solid rgba(128, 128, 128, 0.25);
  }
}
```

</details>

---

## Requirement 2: Buka dan tutup menu dengan `classList.toggle`

**Tujuan:** Klik ikon hamburger membuka menu. Klik lagi menutupnya.

**Konsep singkat:** JavaScript tidak mengatur tampilan secara langsung. Tugas JavaScript hanya menyalakan dan mematikan sebuah class (`open`). CSS-lah yang menentukan seperti apa tampilan menu saat class itu ada. `classList.toggle("open")` bekerja seperti saklar: kalau class belum ada maka ditambahkan, kalau sudah ada maka dihapus.

**Langkah:**

1. Di `style.css` (paling bawah), tambahkan `@media (max-width: 768px)` berisi aturan `.nav-links.open` dengan `display: flex`. Selector `.nav-links.open` berarti elemen yang punya **kedua** class sekaligus, jadi tidak ada spasi di antaranya.
2. Buka `script.js`. Cari komentar `TODO Requirement 2`.
3. Ambil tombol hamburger: `document.querySelector(".hamburger")`, simpan ke variabel `hamburger` dengan `const`.
4. Ambil daftar menu: `document.querySelector(".nav-links")`, simpan ke variabel `navLinks`.
5. Pasang event listener pada `hamburger`: `addEventListener("click", function () { ... })`.
6. Di dalam function, panggil `navLinks.classList.toggle("open")`.
7. Simpan, lalu coba klik hamburger di tampilan mobile.

**Cek hasil:**

- Klik pertama: menu turun di bawah navbar.
- Klik kedua: menu tertutup lagi.
- Buka DevTools tab **Elements**, lihat `<ul class="nav-links">`. Setiap kali kamu klik, class `open` muncul dan hilang bergantian.

**Kesalahan umum:**

| Gejala | Penyebab | Solusi |
|---|---|---|
| Console: `Cannot read properties of null (reading 'addEventListener')` | `querySelector` tidak menemukan elemen. Selector salah ketik, atau tombol hamburger belum ada di HTML | Cek tulisan `".hamburger"` (pakai titik) dan pastikan Requirement 1 sudah selesai |
| Menu tidak berubah, class `open` juga tidak muncul | Penulisan `toggle(".open")` memakai titik | Di `classList`, tulis nama class **tanpa titik**: `toggle("open")` |
| Class `open` muncul di DevTools tapi menu tidak tampil | Aturan CSS `.nav-links.open` belum ditulis atau salah ketik | Cek langkah 1 |
| Tidak ada reaksi sama sekali | `script.js` tidak terbaca | Pastikan pesan "script.js terhubung" muncul di Console |
| Menu terbuka lalu langsung tertutup | Listener yang sama tertulis dua kali, sehingga `toggle` jalan dua kali | Hapus salah satunya |

<details>
<summary>Hint 1: arah berpikir</summary>

Ada tiga hal yang harus kamu lakukan di JavaScript: (1) ambil elemen tombol, (2) ambil elemen menu, (3) saat tombol diklik, ubah class di elemen menu. Nama class yang dipakai harus sama persis dengan yang ada di CSS.

</details>

<details>
<summary>Hint 2: kerangka kode (isi bagian yang kosong)</summary>

```js
const hamburger = document.querySelector("____");
const navLinks = document.querySelector("____");

hamburger.addEventListener("____", function () {
  navLinks.classList.____("open");
});
```

</details>

<details>
<summary>Kode lengkap: CSS dan JavaScript</summary>

Tambahkan di paling bawah `style.css`:

```css
/* ===== Requirement 2: menu terbuka ===== */
@media (max-width: 768px) {
  .nav-links.open {
    display: flex;
  }
}
```

Tulis di `script.js`:

```js
const hamburger = document.querySelector(".hamburger");
const navLinks = document.querySelector(".nav-links");

hamburger.addEventListener("click", function () {
  navLinks.classList.toggle("open");
});
```

</details>

---

## Requirement 3: Buat tombol Dark Mode

**Tujuan:** Tombol "Dark Mode" tampil rapi di navbar, baik di desktop maupun mobile. Pada tahap ini tombol belum berfungsi, itu dikerjakan di Requirement 4.

**Konsep singkat:** Elemen `<button>` tidak otomatis memakai font halaman, jadi perlu `font-family: inherit`. Warna tombol memakai variabel (`var(--primary-color)`, `var(--accent-color)`) supaya ikut berubah saat dark mode aktif nanti.

**Langkah:**

1. Di `index.html`, di dalam `<div class="nav-actions">`, tambahkan `<button>` dengan class `dark-toggle`, teks `Dark Mode`, serta atribut `type="button"` dan `aria-label="Ganti mode tampilan"`. Letakkan **di atas** tombol hamburger, supaya urutannya: tombol Dark Mode, lalu hamburger.
2. Di `style.css` (paling bawah), tulis aturan `.dark-toggle`: padding, `font-family: inherit`, ukuran font 14px, `white-space: nowrap`, warna teks `var(--primary-color)`, background transparan, border 1.5px berwarna `var(--accent-color)`, `border-radius: 999px` (bentuk kapsul), `cursor: pointer`, dan `transition`.
3. Tulis `.dark-toggle:hover`: background `var(--accent-color)` dan warna teks gelap (`#1F1B18`).
4. Tambahkan `@media (max-width: 768px)` untuk `.dark-toggle` dengan padding dan ukuran font lebih kecil, supaya logo, tombol, dan hamburger muat dalam satu baris di HP.
5. Simpan dan periksa di tampilan desktop dan mobile.

**Cek hasil:**

- Tombol berbentuk kapsul dengan garis tepi berwarna aksen (`--accent-color`) muncul di navbar.
- Di desktop: tombol berada di kanan, sejajar dengan logo dan menu.
- Di mobile: logo di kiri, tombol Dark Mode dan hamburger di kanan, semuanya satu baris.
- Arahkan kursor ke tombol: warnanya terisi.

**Kesalahan umum:**

| Gejala | Penyebab | Solusi |
|---|---|---|
| Font tombol berbeda dari halaman | Lupa `font-family: inherit` | Tambahkan pada `.dark-toggle` |
| Tombol turun ke baris kedua di mobile | Padding dan ukuran font belum dikecilkan di media query, atau `flex-wrap: nowrap` dari Requirement 1 belum ada | Cek langkah 4 dan Requirement 1 |
| Teks tombol tidak terbaca saat dark mode nanti | Warna ditulis hex tetap (misalnya `#000`) | Pakai `var(--primary-color)` |
| Tombol tampil di atas hamburger, bukan di sebelahnya | Tombol diletakkan di luar `.nav-actions` | Pindahkan ke dalam `<div class="nav-actions">` |

<details>
<summary>Hint 1: arah berpikir</summary>

Cara menggayakan tombol ini mirip dengan hamburger: reset tampilan bawaan, lalu atur sendiri. Warna yang kamu pakai sebaiknya selalu lewat `var(...)` supaya otomatis ikut tema.

</details>

<details>
<summary>Hint 2: kode HTML</summary>

```html
<button class="dark-toggle" type="button" aria-label="Ganti mode tampilan">Dark Mode</button>
```

Letakkan di dalam `.nav-actions`, di atas tombol hamburger.

</details>

<details>
<summary>Kode lengkap: CSS</summary>

Tambahkan di paling bawah `style.css`:

```css
/* ===== Requirement 3: tombol Dark Mode ===== */
.dark-toggle {
  padding: 8px 16px;
  font-family: inherit;
  font-size: 14px;
  font-weight: 500;
  white-space: nowrap;
  color: var(--primary-color);
  background-color: transparent;
  border: 1.5px solid var(--accent-color);
  border-radius: 999px;
  cursor: pointer;
  transition: background-color 0.3s ease, color 0.3s ease;
}

.dark-toggle:hover {
  background-color: var(--accent-color);
  color: #1F1B18;
}

@media (max-width: 768px) {
  .dark-toggle {
    padding: 6px 10px;
    font-size: 12px;
  }
}
```

</details>

---

## Requirement 4: Hubungkan tombol dengan class `dark` pada `body`

**Tujuan:** Klik tombol Dark Mode mengubah seluruh halaman menjadi tema gelap. Klik lagi mengembalikannya ke tema terang.

**Konsep singkat:** Semua warna di halaman ini disimpan sebagai variabel CSS di `:root` (itu yang kamu pelajari di Day 1). Jika sebuah elemen mendefinisikan ulang variabel yang sama, semua elemen di dalamnya ikut memakai nilai baru. Maka cukup buat aturan `body.dark` yang menimpa nilai variabel, lalu JavaScript hanya perlu menyalakan dan mematikan class `dark` pada `<body>`. Pola ini sama dengan hamburger: JavaScript hanya jadi saklar, CSS yang mengatur tampilan.

**Langkah:**

1. Di `style.css` (paling bawah), tulis aturan `body.dark` (tanpa spasi, artinya `body` yang punya class `dark`).
2. Di dalamnya, timpa empat variabel dengan nilai berikut:

   | Variabel | Nilai dark mode |
   |---|---|
   | `--primary-color` | `#F5F5F5` |
   | `--bg-color` | `#1A1A1A` |
   | `--card-bg` | `#2A2725` |
   | `--muted-color` | `#B8B0A8` |

   Nama variabel harus sama persis dengan yang ada di `:root`.
3. Buka `script.js`. Cari komentar `TODO Requirement 4`.
4. Ambil tombol dark mode: `document.querySelector(".dark-toggle")`, simpan ke variabel `darkToggle`.
5. Pasang event listener `click` pada `darkToggle`.
6. Di dalam function, panggil `document.body.classList.toggle("dark")`. `document.body` adalah elemen `<body>`.
7. Simpan, lalu klik tombol Dark Mode.

**Cek hasil:**

- Latar halaman, navbar, kartu, dan footer berubah gelap. Teks berubah terang.
- Bagian hero dan Tentang Kami tidak ikut berubah, karena warnanya ditulis langsung (hex), bukan lewat variabel. Itu disengaja. Di tema bawaan keduanya memang sudah gelap, jadi perubahannya tidak terlihat. Kalau kamu mengubah warna hero atau Tentang Kami menjadi terang, kedua bagian itu akan tetap terang saat dark mode aktif.
- Klik lagi: semuanya kembali terang.
- Di tampilan mobile, menu hamburger yang terbuka ikut menjadi gelap.
- Di DevTools tab **Elements**, `<body>` mendapat dan kehilangan `class="dark"` bergantian.

**Kesalahan umum:**

| Gejala | Penyebab | Solusi |
|---|---|---|
| Tombol diklik, class `dark` muncul, tapi tampilan tidak berubah | Selector salah: `.dark`, `body .dark` (dengan spasi), atau `.body.dark` | Tulis `body.dark` tanpa spasi |
| Sebagian warna tidak berubah | Nama variabel salah ketik, atau bagian itu memakai warna hex tetap | Samakan nama variabel dengan `:root`; pakai `var(...)` untuk warna |
| Console: `Cannot read properties of null` | `.dark-toggle` tidak ditemukan | Pastikan tombol sudah ada di HTML (Requirement 3) dan namanya sama |
| Tombol harus diklik dua kali untuk bereaksi | Listener terpasang dua kali | Hapus salah satu |

<details>
<summary>Hint 1: arah berpikir</summary>

Kamu butuh dua bagian yang saling bertemu lewat satu nama class: bagian CSS yang berlaku **hanya ketika** `body` punya class `dark`, dan bagian JavaScript yang menambah atau menghapus class itu setiap tombol diklik.

</details>

<details>
<summary>Hint 2: kerangka kode (isi bagian yang kosong)</summary>

```css
body.dark {
  --primary-color: ____;
  --bg-color: ____;
  --card-bg: ____;
  --muted-color: ____;
}
```

```js
const darkToggle = document.querySelector("____");

darkToggle.addEventListener("click", function () {
  document.body.classList.____("dark");
});
```

</details>

<details>
<summary>Kode lengkap: CSS dan JavaScript</summary>

Tambahkan di paling bawah `style.css`:

```css
/* ===== Requirement 4: tema gelap ===== */
body.dark {
  --primary-color: #F5F5F5;
  --bg-color: #1A1A1A;
  --card-bg: #2A2725;
  --muted-color: #B8B0A8;
}
```

Tambahkan di `script.js`:

```js
const darkToggle = document.querySelector(".dark-toggle");

darkToggle.addEventListener("click", function () {
  document.body.classList.toggle("dark");
});
```

</details>

---

## Cek akhir Day 2

Sebelum selesai, pastikan semua ini benar:

- [ ] Desktop (lebar lebih dari 768px): tidak ada hamburger, menu tampil normal, tombol Dark Mode berfungsi.
- [ ] Mobile (lebar 768px ke bawah): menu tertutup saat halaman dibuka.
- [ ] Klik hamburger membuka menu, klik lagi menutupnya.
- [ ] Klik Dark Mode mengubah seluruh halaman menjadi gelap, klik lagi mengembalikannya.
- [ ] Dark mode juga berlaku saat menu hamburger terbuka.
- [ ] Console (F12) tidak menampilkan error berwarna merah.

---

## Tantangan opsional

Kerjakan kalau misi utama sudah selesai.

**Penting untuk tantangan 2 dan 3:** kode tantangan ini **menggantikan** listener yang sudah kamu tulis, bukan ditambahkan di bawahnya. Jika dua listener `toggle` terpasang pada tombol yang sama, setiap klik akan membuka lalu langsung menutup menu (hasilnya seperti tidak terjadi apa-apa).

### Tantangan 1: Menu menutup otomatis setelah link diklik

Saat ini, setelah memilih menu di HP, daftar menu tetap terbuka. Buat menu tertutup begitu salah satu link diklik.

<details>
<summary>Hint</summary>

Ada empat link di menu, jadi kamu butuh `querySelectorAll` (bukan `querySelector`) dan `forEach` untuk memasang listener ke tiap link. Di dalam listener, hapus class `open`: `classList.remove("open")`.

</details>

<details>
<summary>Kode</summary>

Tambahkan di bawah kode Requirement 2 (variabel `hamburger` dan `navLinks` sudah ada di atas):

```js
const menuLinks = document.querySelectorAll(".nav-links a");

menuLinks.forEach(function (link) {
  link.addEventListener("click", function () {
    navLinks.classList.remove("open");
    hamburger.setAttribute("aria-expanded", "false");
  });
});
```

Baris `setAttribute` menjaga nilai `aria-expanded` tetap sesuai. Tanpa baris itu, kalau kamu juga mengerjakan Tantangan 3, menu sudah tertutup tetapi `aria-expanded` masih `"true"`. Kalau belum mengerjakan Tantangan 3, baris ini tidak merugikan.

</details>

### Tantangan 2: Teks tombol berganti sesuai mode

Saat mode gelap aktif, teks tombol berubah menjadi "Light Mode". Saat mode terang, kembali menjadi "Dark Mode".

<details>
<summary>Hint</summary>

Gunakan `document.body.classList.contains("dark")` di dalam `if`. Fungsi ini mengembalikan `true` kalau class `dark` sedang ada. Ubah teks tombol lewat `darkToggle.textContent`.

</details>

<details>
<summary>Kode (ganti listener dark mode yang lama)</summary>

```js
darkToggle.addEventListener("click", function () {
  document.body.classList.toggle("dark");

  if (document.body.classList.contains("dark")) {
    darkToggle.textContent = "Light Mode";
  } else {
    darkToggle.textContent = "Dark Mode";
  }
});
```

</details>

### Tantangan 3: Perbarui `aria-expanded`

Atribut `aria-expanded` memberi tahu pembaca layar apakah menu sedang terbuka. Perbarui nilainya setiap kali tombol diklik.

<details>
<summary>Hint</summary>

Setelah `toggle`, cek apakah `navLinks` punya class `open` dengan `contains`. Simpan hasilnya ke variabel, lalu pasang ke tombol dengan `setAttribute("aria-expanded", ...)`. Buka DevTools Elements untuk melihat nilainya berubah.

</details>

<details>
<summary>Kode (ganti listener hamburger yang lama)</summary>

```js
hamburger.addEventListener("click", function () {
  navLinks.classList.toggle("open");

  const isOpen = navLinks.classList.contains("open");
  hamburger.setAttribute("aria-expanded", isOpen);
});
```

</details>

---

## Kode akhir `script.js` (misi utama)

<details>
<summary>Buka untuk mencocokkan hasilmu</summary>

```js
// Frontend Starter Camp Day 2 - script.js

console.log("script.js terhubung. Siap mulai Day 2!");

// Requirement 2: hamburger membuka dan menutup menu
const hamburger = document.querySelector(".hamburger");
const navLinks = document.querySelector(".nav-links");

hamburger.addEventListener("click", function () {
  navLinks.classList.toggle("open");
});

// Requirement 4: tombol dark mode
const darkToggle = document.querySelector(".dark-toggle");

darkToggle.addEventListener("click", function () {
  document.body.classList.toggle("dark");
});
```

</details>

---

## Troubleshooting umum

| Gejala | Penyebab umum | Solusi |
|---|---|---|
| Halaman tidak berubah setelah kamu mengedit | File belum disimpan, atau Live Server belum berjalan | Tekan `Ctrl+S`. Pastikan tombol **Go Live** di pojok kanan bawah VS Code aktif |
| Pesan "script.js terhubung" tidak muncul di Console | `script.js` tidak terbaca | Pastikan namanya tepat `script.js` dan berada satu folder dengan `index.html` |
| Error merah di Console: `Cannot read properties of null` | `querySelector` tidak menemukan elemen | Periksa penulisan class (pakai titik, tanpa typo) dan pastikan elemennya sudah ada di HTML |
| Class berubah di DevTools tapi tampilan tidak | Aturan CSS untuk class itu belum ada atau salah selector | Periksa `.nav-links.open` dan `body.dark` (tanpa spasi) |
| Error `Identifier 'navLinks' has already been declared` | Variabel yang sama dideklarasikan dua kali dengan `const` | Hapus salah satu deklarasi, jangan menulis `const navLinks` lebih dari sekali |
| Hamburger tidak terlihat di desktop | Ini perilaku yang benar | Perkecil jendela hingga 768px atau gunakan device toolbar |
| Menu hilang di desktop | `display: none` untuk `.nav-links` ada di luar media query | Pindahkan ke dalam `@media (max-width: 768px)` |
| Menu tidak mau terbuka, tetapi tidak ada error | Ada dua listener `toggle` pada tombol yang sama | Hapus salah satu |

---

## Lampiran: Panduan checklist Time to Code Day 1

Project ini sudah berisi hasil lengkap dari checklist Day 1. Lampiran ini untuk kamu yang belum selesai di Day 1, atau ingin tahu cara membuat halaman ini dari nol. Kode di bawah diambil dari `index.html` dan `style.css` di project ini, dengan beberapa bagian disederhanakan (misalnya aturan `.header` dan `.logo` pada navbar tidak ditulis ulang). Kalau ada perbedaan kecil dengan file aslinya, file di project inilah yang dipakai.

### Day 1, Checklist 1: Struktur file HTML5 dan tag semantik

**Langkah:**

1. Buat folder proyek dengan tiga file: `index.html`, `style.css`, `script.js`.
2. Di `index.html`, ketik `!` lalu tekan `Tab`. VS Code membuat kerangka HTML5. Ubah `lang` menjadi `"id"` dan isi `<title>`.
3. Pastikan ada `<meta name="viewport" ...>` di dalam `<head>`. Tanpa ini halaman tidak responsif di HP.
4. Hubungkan CSS di dalam `<head>`: `<link rel="stylesheet" href="style.css">`.
5. Di dalam `<body>`, susun kerangka semantik: `<header>` berisi `<nav>`, lalu `<main>` berisi tiga `<section>`, lalu `<footer>`.
6. Beri `id` pada tiap section dan footer (`beranda`, `tentang`, `langganan`, `kontak`), lalu hubungkan dengan link `<a href="#id">` di navbar.
7. Gunakan **satu** `<h1>` saja, yaitu di hero.

**Kerangka:**

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Innova Space</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <nav>
      <!-- logo dan daftar link -->
    </nav>
  </header>

  <main>
    <section id="beranda"></section>
    <section id="tentang"></section>
    <section id="langganan"></section>
  </main>

  <footer id="kontak"></footer>
</body>
</html>
```

**Cek hasil:** klik link di navbar, halaman meloncat ke section yang sesuai. **Kesalahan umum:** lebih dari satu `<h1>`, `id` yang sama dipakai dua kali, atau lupa `<meta viewport>`.

### Day 1, Checklist 2: Reset CSS dan variabel warna di `:root`

**Langkah:**

1. Di `style.css`, tulis reset dengan selector `*` (margin 0, padding 0, `box-sizing: border-box`).
2. Buat blok `:root` berisi variabel warna. Nama variabel diawali dua tanda strip (`--`).
3. Pakai variabel itu lewat `var(--nama)`, mulai dari `body`.
4. Tambahkan font Poppins lewat `<link>` Google Fonts di `<head>`, lalu pakai di `body`.

```css
/* 1. Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* 2. Variabel warna */
:root {
  --primary-color: #2E2A26;
  --accent-color: #C97B4A;
  --bg-color: #FFFFFF;
  --card-bg: #FBF4EE;
  --muted-color: #6B645C;
}

body {
  font-family: 'Poppins', sans-serif;
  font-size: 16px;
  line-height: 1.6;
  color: var(--primary-color);
  background-color: var(--bg-color);
  transition: background-color 0.3s ease, color 0.3s ease;
}
```

**Cek hasil:** warna teks dan latar mengikuti variabel. Coba ubah nilai `--accent-color`, semua yang memakainya ikut berubah. **Kesalahan umum:** menulis satu strip (`-primary-color`), salah ketik nama saat `var(...)`, atau lupa `box-sizing: border-box` sehingga lebar elemen melebihi perhitungan.

### Day 1, Checklist 3: Navbar dengan Flexbox (logo kiri, link kanan)

**Langkah:**

1. Beri class pada HTML: `navbar` untuk `<nav>`, `nav-links` untuk `<ul>`.
2. Pada `.navbar`, aktifkan `display: flex`, `justify-content: space-between`, dan `align-items: center`.
3. Pada `.nav-links`, aktifkan `display: flex`, beri `gap`, dan hilangkan bullet dengan `list-style: none`.
4. Hilangkan garis bawah link dengan `text-decoration: none`.

```html
<header class="header">
  <nav class="navbar" aria-label="Menu utama">
    <a href="#beranda" class="logo">
      <img src="assets/logo.svg" alt="Logo Innova Space" width="32" height="32">
      <span>Innova Space</span>
    </a>

    <ul class="nav-links">
      <li><a href="#beranda">Beranda</a></li>
      <li><a href="#tentang">Tentang</a></li>
      <li><a href="#langganan">Langganan</a></li>
      <li><a href="#kontak">Kontak</a></li>
    </ul>
  </nav>
</header>
```

```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1100px;
  margin: 0 auto;
  padding: 14px 24px;
}

.nav-links {
  display: flex;
  gap: 28px;
  list-style: none;
}

.nav-links a {
  color: var(--primary-color);
  font-weight: 500;
  text-decoration: none;
  transition: color 0.3s ease;
}
```

**Cek hasil:** logo di kiri, daftar menu di tengah dan kanan, semua sejajar vertikal. **Kesalahan umum:** `display: flex` dipasang pada elemen yang salah (harus pada **parent** dari item yang ingin disusun), dan lupa `list-style: none`.

### Day 1, Checklist 4: Hero section (teks rata tengah)

**Langkah:**

1. Pada `.hero`, aktifkan `display: flex` dengan `flex-direction: column`.
2. Pusatkan isinya dengan `justify-content: center` (sumbu vertikal) dan `align-items: center` (sumbu horizontal).
3. Tambahkan `text-align: center`, `min-height`, dan `padding`.
4. Beri latar gradasi gelap lewat `background: linear-gradient(...)`.

```html
<section class="hero" id="beranda">
  <h1>Innova Space</h1>
  <p>Find your space and innovate</p>
  <a href="#langganan" class="btn">Lihat Paket</a>
</section>
```

```css
.hero {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 16px;
  min-height: 70vh;
  padding: 80px 24px;
  text-align: center;
  color: #FFFFFF;
  background:
    radial-gradient(circle at 80% 20%, rgba(201, 123, 74, 0.35), transparent 45%),
    linear-gradient(135deg, #1B1816 0%, #2E2A26 55%, #4A3A2E 100%);
}

.hero h1 {
  font-size: 56px;
  line-height: 1.1;
}

.hero p {
  max-width: 480px;
  margin-bottom: 8px;
  font-size: 20px;
  color: #E9E2DB;
}
```

**Cek hasil:** judul, deskripsi, dan tombol tersusun ke bawah di tengah halaman. **Kesalahan umum:** karena `flex-direction: column`, arah `justify-content` dan `align-items` menjadi terbalik. `justify-content` mengatur vertikal, `align-items` mengatur horizontal.

### Day 1, Checklist 5: Tiga card layanan (responsif, menumpuk di HP)

**Langkah:**

1. Bungkus tiga `<article class="card">` dengan satu `<div class="card-container">`.
2. Pada `.card-container`, aktifkan `display: flex` dan beri `gap`.
3. Pada `.card`, tambahkan `flex: 1` supaya ketiga card berbagi lebar sama rata.
4. Beri padding, warna latar, `border-radius`, dan `box-shadow` pada `.card`.
5. Di `@media (max-width: 768px)`, ubah `.card-container` menjadi `flex-direction: column` agar card menumpuk ke bawah di HP.

```html
<div class="card-container">
  <article class="card">
    <img src="assets/icon-weekly.svg" alt="Ikon paket mingguan" width="48" height="48">
    <h3>Weekly Premium</h3>
    <p>Cocok untuk mencoba suasana Innova Space. Akses ruang kerja, internet cepat, dan area diskusi selama 7 hari.</p>
    <p class="price">Rp 75.000 / minggu</p>
  </article>

  <article class="card">
    <img src="assets/icon-monthly.svg" alt="Ikon paket bulanan" width="48" height="48">
    <h3>Monthly Premium</h3>
    <p>Pilihan untuk produktivitas rutin. Akses penuh ruang kerja ditambah sesi mentoring setiap bulan.</p>
    <p class="price">Rp 250.000 / bulan</p>
  </article>

  <article class="card">
    <img src="assets/icon-annual.svg" alt="Ikon paket tahunan" width="48" height="48">
    <h3>Annual Premium</h3>
    <p>Paling hemat untuk komunitas jangka panjang. Akses penuh, mentoring prioritas, dan undangan event eksklusif.</p>
    <p class="price">Rp 2.400.000 / tahun</p>
  </article>
</div>
```

```css
.card-container {
  display: flex;
  gap: 20px;
  max-width: 1000px;
  margin: 40px auto;
}

.card {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  padding: 32px 24px;
  background-color: var(--card-bg);
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease, background-color 0.3s ease;
}

@media (max-width: 768px) {
  .card-container {
    flex-direction: column;
  }
}
```

**Cek hasil:** di desktop tiga card sejajar. Perkecil jendela hingga 768px, card menumpuk satu kolom. **Kesalahan umum:** lupa `flex: 1` (lebar card tidak sama), atau aturan media query ditulis sebelum aturan dasar sehingga tertimpa.

### Day 1, Checklist 6: Efek `:hover` yang halus pada card

**Langkah:**

1. Pada `.card`, tambahkan `transition` untuk properti yang akan berubah (`transform` dan `box-shadow`). Inilah yang membuat perubahan terasa halus, bukan melompat.
2. Tulis aturan `.card:hover` yang menaikkan card sedikit dengan `transform: translateY(-8px)` dan memperbesar bayangan.

```css
.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 14px 28px rgba(0, 0, 0, 0.18);
}
```

Baris `transition` sudah ada di dalam aturan `.card` pada Checklist 5.

**Cek hasil:** saat kursor berada di atas card, card naik pelan dan bayangannya menebal. **Kesalahan umum:** `transition` ditulis di `.card:hover` (seharusnya di `.card`), sehingga animasi hanya berjalan satu arah, atau lupa titik pada selector (`card:hover` harusnya `.card:hover`).

---

Selamat belajar. Kalau ada yang tidak jelas, tanyakan ke mentor di ruangan.