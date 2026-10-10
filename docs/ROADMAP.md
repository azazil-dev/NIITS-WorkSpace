# 🗺️ Roadmap

Backlog pengembangan **NIITS WorkSpace**, disusun berdasarkan prioritas. Item dapat berubah mengikuti kebutuhan tim.

---

## 🔴 Prioritas Tinggi — Perbaikan & Integrasi

- [ ] **Perbaiki bug unread notification** — `Frontend/src/App.tsx` memakai `notifications.filter(n => !n.read)`, padahal field pada `NotificationItem` adalah `baru`. Akibatnya badge unread selalu menghitung semua notifikasi.
- [ ] **Konsolidasi data notifikasi** — `App.tsx` memakai `INITIAL_NOTIFICATIONS` (mockData) sementara `InboxView.tsx` memakai `SEED_INBOX_ITEMS` sendiri. Satukan sumber data.
- [ ] **Integrasi Frontend ↔ Backend** —
  - [ ] Buat API client (mis. `Frontend/src/lib/api.ts`).
  - [ ] Bangun struktur backend: `routes/`, `controllers/`, `middleware/`, `services/`.
  - [ ] Migrasikan satu domain dulu (disarankan: **Tasks**) dari mock ke REST.
  - [ ] Tambahkan indikator koneksi backend (health check).
- [ ] **Perkuat backend** — global error handler, 404 handler, validasi environment, batasi CORS ke `CLIENT_URL`, dan graceful shutdown.

---

## 🟡 Prioritas Menengah — Tooling & Kualitas

- [ ] **Root workspace** — `package.json` di root dengan npm workspaces + `concurrently` agar `npm run dev` menjalankan frontend & backend sekaligus.
- [ ] **Linting & formatting** — setup ESLint + Prettier (saat ini `npm run lint` hanya `tsc --noEmit`).
- [ ] **TypeScript strict** — aktifkan `strict` di `Frontend/tsconfig.json` secara bertahap.
- [ ] **Bersihkan Frontend** —
  - Hapus dependensi tak terpakai: `express`, `@types/express`, `tsx`, `esbuild`, `dotenv`, `@google/genai` (tidak diimpor).
  - Perbaiki script `clean` yang menghapus `server.js` (file tidak ada, sisa template).
  - Bersihkan `Frontend/.env.example` dari variabel template (`GEMINI_API_KEY`, `APP_URL`).
- [ ] **Test** —
  - [ ] Frontend: Vitest + React Testing Library.
  - [ ] Backend: `node:test` atau Jest + Supertest.
- [ ] **CI** — GitHub Actions: install → lint → build → test pada setiap PR.
- [ ] **Template GitHub** — `PULL_REQUEST_TEMPLATE.md`, issue template, dan `CODEOWNERS`.
- [ ] **Persistensi state** — sebagian besar state hilang saat refresh; pertimbangkan `localStorage` atau backend.

---

## 🟢 Prioritas Rendah — Polesan

- [ ] **Aksesibilitas** — atribut ARIA, focus trap pada modal/drawer, navigasi keyboard.
- [ ] **Responsif** — audit tampilan di berbagai ukuran layar.
- [ ] **Konsistensi UI** — satukan token warna dan spacing.
- [ ] **Dokumentasi API** — buat `docs/API.md` setelah endpoint tersedia.

---

## ✅ Sudah Selesai

- [x] Tambah `README.md` yang komprehensif.
- [x] Tambah `.gitignore` untuk Backend & Frontend.
- [x] Inisialisasi struktur backend Express.
- [x] Tambah `CONTRIBUTING.md` dan `CODE_OF_CONDUCT.md`.
- [x] Tambah `LICENSE` (proprietary/internal).
- [x] Tambah folder `docs/` (setup, arsitektur, workflow, roadmap).
