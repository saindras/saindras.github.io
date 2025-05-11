# Pengembangan Lokal Blog Jekyll dengan Tema Chirpy

Dokumen ini merangkum langkah-langkah setup dan konfigurasi pengembangan blog berbasis Jekyll dengan tema **Chirpy**, termasuk linting, formatting, dan CI/CD untuk GitHub Pages.

---

## 📦 Persiapan Lingkungan

1. **Instalasi Tools**

   * Node.js `>=18` (disarankan `v20` atau lebih baru)
   * Git
   * Ruby `3.3` (melalui GitHub Actions)
   * Docker (jika ingin pakai container)
   * VSCode + ekstensi Remote - Containers

2. **Clone Repository**

   ```bash
   git clone https://github.com/<user>/saindras.github.io.git
   cd saindras.github.io
   ```

3. **Instalasi Dependency**

   ```bash
   npm install
   ```

---

## 🚀 Menjalankan Secara Lokal

1. **Build dan Serve**

   ```bash
   bundle install
   bundle exec jekyll build
   bundle exec jekyll serve
   ```

2. **Akses Lokal**
   Buka di browser:

   ```
   http://127.0.0.1:4000/
   ```

---

## 🧼 Pre-Commit Otomatis

### Struktur Hook

File `.husky/pre-commit`:

```sh
#!/bin/sh
npm run lint:html
npm run format:md
npm run lint:fix:scss
```

### Script di `package.json`

```json
"scripts": {
  "lint:html": "htmlhint _site/**/*.html",
  "format:md": "prettier --write '**/*.md'",
  "lint:fix:scss": "npm run lint:scss -- --fix",
  "lint:scss": "stylelint _sass/**/*.scss"
}
```

### Konfigurasi HTMLHint

File `.htmlhintrc`:

```json
{
  "tagname-lowercase": true,
  "attr-lowercase": true,
  "attr-value-double-quotes": true,
  "doctype-first": false,
  "tag-pair": true,
  "spec-char-escape": true,
  "id-unique": true,
  "src-not-empty": true,
  "alt-require": true
}
```

### Menjalankan Manual

```bash
npm run lint:html
npm run format:md
npm run lint:fix:scss
```

---

## 🔁 CI/CD: GitHub Pages + Workflow

### Lokasi File

`.github/workflows/pages-deploy.yml`

### Alur Build

1. Checkout repo dan setup Ruby
2. Build Jekyll
3. (Opsional) Jalankan `htmlproofer`
4. Upload artifact
5. Deploy ke GitHub Pages

### Menonaktifkan htmlproofer

Jika build gagal karena gambar tanpa `alt`, hapus atau beri komentar langkah berikut di YAML:

```yaml
- name: Test site
  run: |
    bundle exec htmlproofer _site \
      --disable-external \
      --ignore-urls "/^http:\/\/127.0.0.1/,/^http:\/\/0.0.0.0/,/^http:\/\/localhost/"
```

---

## 🔒 Validasi Commit

Commit akan divalidasi menggunakan **Commitlint** dan **Conventional Commits**:

* Contoh benar:

  ```
  feat: tambahkan fitur baru
  fix: perbaiki tampilan navbar di mobile
  chore: update dependensi dan konfigurasi husky
  ```
* Commit yang tidak sesuai akan **digagalkan secara otomatis**.

---

## 📝 Tips Tambahan

* Gunakan command `git commit --no-verify` hanya jika yakin linting bisa diabaikan.
* Gunakan `git status` untuk melihat file yang dimodifikasi (M) atau belum dilacak (U).
* Jalankan ulang `npm install` jika file `package-lock.json` berubah atau workflow error.

---

Disusun dan dikonfigurasi oleh: **Gede Saindra Santyadiputra**

Untuk kontribusi, silakan pull request ke repositori ini.
