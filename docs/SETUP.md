# ⚙️ Setup Guide

Panduan lengkap menyiapkan environment development **NIITS WorkSpace** di mesin lokal.

---

## 1. Persyaratan

| Kebutuhan | Versi disarankan | Cek |
| --- | --- | --- |
| Node.js | v18+ | `node --version` |
| npm | v9+ | `npm --version` |
| Git | terbaru | `git --version` |

---

## 2. Clone Repository

### Opsi A — Kontributor (melalui fork)

```bash
git clone https://github.com/<username>/NIITS-WorkSpace.git
cd NIITS-WorkSpace
git remote add upstream https://github.com/niitsinovasiteknologi/NIITS-WorkSpace.git
git fetch upstream
```

### Opsi B — Anggota tim (akses langsung)

```bash
git clone git@github.com:niitsinovasiteknologi/NIITS-WorkSpace.git
cd NIITS-WorkSpace
```

---

## 3. Menjalankan Frontend

```bash
cd Frontend
npm install
npm run dev
```

- Berjalan di **http://localhost:3000**
- Perintah tersedia:

| Script | Fungsi |
| --- | --- |
| `npm run dev` | Jalankan dev server (Vite, port 3000) |
| `npm run build` | Build produksi ke `dist/` |
| `npm run preview` | Preview hasil build |
| `npm run lint` | Type-check dengan `tsc --noEmit` |

---

## 4. Menjalankan Backend

Di terminal **terpisah**:

```bash
cd Backend
npm install
npm run dev
```

- Berjalan di **http://localhost:5000**
- Endpoint tersedia saat ini:
  - `GET /` → teks status API
  - `GET /api/health` → health check JSON

| Script | Fungsi |
| --- | --- |
| `npm run dev` | Jalankan dengan `node --watch` |
| `npm start` | Jalankan tanpa watch |

---

## 5. Environment Variables

Jangan pernah commit file `.env`. Gunakan `.env.example` sebagai template.

```bash
cp Backend/.env.example Backend/.env
cp Frontend/.env.example Frontend/.env
```

### Backend (`Backend/.env`)

| Variabel | Deskripsi | Default |
| --- | --- | --- |
| `PORT` | Port server backend | `5000` |
| `NODE_ENV` | Mode environment | `development` |
| `CLIENT_URL` | Origin frontend untuk CORS | `http://localhost:3000` |

> Catatan: `Frontend/.env.example` masih berisi variabel bawaan template (mis. `GEMINI_API_KEY`, `APP_URL`) yang belum dipakai aplikasi. Akan dibersihkan pada tahap integrasi.

---

## 6. Troubleshooting

**Port sudah dipakai**

```bash
# cari proses yang memakai port
lsof -i :3000
lsof -i :5000
```

**Perintah `cd frontend` gagal**
Nama folder bersifat case-sensitive: gunakan `Frontend` dan `Backend` (huruf besar).

**Perubahan tidak terdeteksi / HMR mati**
Pastikan variabel `DISABLE_HMR` tidak di-set ke `true`.

**Error module tidak ditemukan**
Jalankan ulang `npm install` di folder terkait (`Frontend/` atau `Backend/`).

**Ingin menyinkronkan fork dengan repo utama**

```bash
git checkout main
git pull upstream main
git push origin main
```

---

Lihat juga: [ARCHITECTURE.md](./ARCHITECTURE.md) · [GIT-WORKFLOW.md](./GIT-WORKFLOW.md) · [ROADMAP.md](./ROADMAP.md)
