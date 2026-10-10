# 🤝 Panduan Berkontribusi

Terima kasih telah berkontribusi pada **NIITS WorkSpace**! Dokumen ini menjelaskan cara menyiapkan environment, standar kode, dan alur kontribusi agar setiap perubahan mudah di-review dan di-merge.

---

## Daftar Isi

- [Persyaratan](#persyaratan)
- [Setup Development](#setup-development)
- [Alur Kerja Git](#alur-kerja-git)
- [Konvensi Commit](#konvensi-commit)
- [Standar Kode](#standar-kode)
- [Checklist Pull Request](#checklist-pull-request)
- [Proses Review](#proses-review)

---

## Persyaratan

Pastikan sudah terpasang:

- **Node.js** (disarankan v18 ke atas)
- **npm**
- **Git**

Cek instalasi:

```bash
node --version
npm --version
git --version
```

---

## Setup Development

### 1. Fork & Clone

Fork repository ini di GitHub, lalu clone **fork milikmu**:

```bash
git clone https://github.com/<username>/NIITS-WorkSpace.git
cd NIITS-WorkSpace
```

### 2. Hubungkan ke repo utama

```bash
git remote add upstream https://github.com/niitsinovasiteknologi/NIITS-WorkSpace.git
git fetch upstream
```

Sinkronkan perubahan terbaru dari upstream:

```bash
git checkout main
git pull upstream main
```

### 3. Install dependencies

Frontend (port **3000**):

```bash
cd Frontend
npm install
npm run dev
```

Backend (port **5000**), di terminal terpisah:

```bash
cd Backend
npm install
npm run dev
```

### 4. Environment variables

Salin file contoh dan sesuaikan bila perlu **tanpa** meng-commit `.env`:

```bash
cp Backend/.env.example Backend/.env
```

> Lihat [docs/SETUP.md](./docs/SETUP.md) untuk panduan setup yang lebih detail dan troubleshooting.

---

## Alur Kerja Git

Kami **tidak** menerima commit langsung ke `main`. Semua perubahan masuk melalui Pull Request.

```text
main
 └── feature/<nama>     # fitur baru
 └── fix/<nama>         # perbaikan bug
 └── docs/<nama>        # dokumentasi
 └── refactor/<nama>    # perbaikan struktur tanpa mengubah perilaku
 └── chore/<nama>       # tooling, config, housekeeping
```

> Catatan: branch `develop` belum tersedia. Sementara ini buat branch dari `main` dan ajukan PR ke `main`.

### Langkah

```bash
# 1. Ambil perubahan terbaru
git checkout main
git pull upstream main

# 2. Buat branch baru
git checkout -b feature/nama-fitur

# 3. Kerjakan perubahan & commit
git add .
git commit -m "feat: tambah autentikasi"

# 4. Push ke fork
git push origin feature/nama-fitur

# 5. Buka Pull Request ke repository utama
```

---

## Konvensi Commit

Gunakan format **Conventional Commits**:

```text
<tipe>(<scope opsional>): <deskripsi singkat>
```

| Tipe | Kegunaan |
| --- | --- |
| `feat` | Fitur baru |
| `fix` | Perbaikan bug |
| `docs` | Perubahan dokumentasi |
| `style` | Formatting, tanpa perubahan logika |
| `refactor` | Perbaikan struktur tanpa mengubah perilaku |
| `test` | Menambah atau memperbaiki test |
| `chore` | Tooling, config, dependency, housekeeping |

Contoh:

```text
feat: add dashboard filter
fix: resolve login validation on empty email
docs: add contributing guide
refactor: extract task API client
chore: setup eslint and prettier
```

Hindari pesan seperti `update`, `fix`, atau `test` tanpa konteks.

---

## Standar Kode

- **Frontend**: React + TypeScript. Gunakan komponen fungsional dan hook. Ikuti gaya yang sudah ada di `Frontend/src`.
- **Backend**: Node.js + Express (ES Modules). Kelompokkan berdasarkan tanggung jawab (`routes`, `controllers`, `middleware`, `services`).
- **Gaya penulisan**: konsisten dengan file di sekitarnya (nama variabel, indentation, urutan import).
- **Tanpa secret**: jangan pernah commit `.env`, token, atau API key.
- **Node modules**: jangan commit `node_modules` atau hasil build (`dist/`, `build/`).
- Sebelum PR, pastikan aplikasi dapat dijalankan dan tidak ada error di console.

---

## Checklist Pull Request

Sebelum membuka PR, pastikan:

```text
[ ] Feature/perbaikan berjalan dengan baik
[ ] Tidak ada error di console
[ ] Tidak ada credential / secret yang ter-commit
[ ] Tidak ada node_modules / build artifact yang ter-commit
[ ] Kode sudah dirapikan dan konsisten
[ ] Commit message jelas (Conventional Commits)
[ ] Branch mengikuti naming convention
[ ] Sudah pull perubahan terbaru dari upstream
[ ] Dokumentasi diperbarui bila diperlukan
```

Saat membuka PR, jelaskan **apa**, **mengapa**, dan **bagaimana mengujinya**. Sertakan screenshot untuk perubahan UI.

---

## Proses Review

1. Reviewer akan meninjau kode, memberi komentar, dan bila perlu meminta perubahan.
2. Perubahan lanjutan cukup di-push ke branch yang sama — PR akan otomatis ter-update.
3. Setelah disetujui, maintainer akan melakukan merge.
4. Jangan merge PR sendiri untuk perubahan yang bersifat penting.

---

Terima kasih sudah berkontribusi! 🎉
