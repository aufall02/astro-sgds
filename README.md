# Astro + SGDS Landing Page

Template ini dibuat dengan:

- **Astro** untuk arsitektur website yang cepat dan content-driven.
- **SGDS Web Components** (`@govtechsg/sgds-web-component`) untuk komponen UI dan foundation style.

Proyek ini cocok untuk landing page layanan digital pemerintah: cepat, konsisten, dan mudah dikembangkan.

## Tech Stack

- Astro `^6.1.1`
- SGDS Web Components `^3.15.0`
- Tailwind CSS `^4.2.2` (untuk utility flow tambahan)

## Prasyarat

- Node.js **>= 22.12.0**
- npm

## Setup Cepat

1. Install dependency:

```sh
npm install
```

2. Jalankan dev server:

```sh
npm run dev
```

3. Build production:

```sh
npm run build
```

4. Preview hasil build:

```sh
npm run preview
```

## Struktur Proyek

```text
/
├── public/
├── src/
│   ├── components/
│   │   └── AnimateOnScroll.astro
│   ├── layouts/
│   │   └── MainLayout.astro
│   ├── pages/
│   │   └── index.astro
│   └── styles/
│       └── global.css
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

## Cara Kerja Astro + SGDS di Proyek Ini

### 1) Foundation style SGDS

Di `src/styles/global.css`, style SGDS di-import berurutan:

```css
@import "@govtechsg/sgds-web-component/themes/day.css";
@import "@govtechsg/sgds-web-component/css/sgds.css";
@import "@govtechsg/sgds-web-component/css/utility.css";
```

### 2) Registrasi web components SGDS

Di `src/layouts/MainLayout.astro`, komponen SGDS diaktifkan lewat script:

```ts
import "@govtechsg/sgds-web-component";
```

Setelah itu, kamu bisa langsung pakai tag seperti:

- `<sgds-mainnav>`
- `<sgds-card>`
- `<sgds-button>`
- `<sgds-footer>`

### 3) Routing Astro

Semua file `.astro` di folder `src/pages` otomatis menjadi route.

- `src/pages/index.astro` -> `/`

## Tutorial Pemakaian

### A. Menambah section baru di landing page

1. Buka `src/pages/index.astro`.
2. Tambahkan section baru di dalam `<MainLayout>`.
3. Gunakan komponen SGDS + kelas utility SGDS agar konsisten.

Contoh:

```astro
<section aria-label="Section contoh" class="sgds:py-layout-xl">
	<div class="sgds-container">
		<h2 class="sgds:text-heading-lg sgds:font-bold">Judul Section</h2>
		<p class="sgds:text-body-md sgds:text-muted">Deskripsi singkat section.</p>
		<sgds-button variant="primary">Aksi Utama</sgds-button>
	</div>
</section>
```

### B. Menambah item layanan (cards)

1. Tambahkan object baru ke array `features` di `src/pages/index.astro`.
2. Card akan ter-render otomatis via `features.map(...)`.

Contoh object:

```ts
{
	icon: "bi-briefcase",
	title: "Perizinan Usaha",
	description: "Ajukan dan pantau proses perizinan usaha secara digital."
}
```

### C. Menyesuaikan warna brand

Override token warna SGDS di `src/styles/global.css` pada blok `:root`.

## Command Ringkas

| Command | Kegunaan |
| :-- | :-- |
| `npm install` | Install dependency |
| `npm run dev` | Menjalankan local server Astro |
| `npm run build` | Build production ke folder `dist/` |
| `npm run preview` | Preview hasil build |

## Referensi Dokumentasi

- Astro docs: https://docs.astro.build
- SGDS Web Components docs: https://www.webcomponent.designsystem.tech.gov.sg
