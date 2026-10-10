# 🏛️ Architecture

Dokumen ini menjelaskan arsitektur **NIITS WorkSpace** sesuai kondisi repository saat ini, beserta arah pengembangannya.

---

## Ringkasan

NIITS WorkSpace adalah monorepo berisi dua aplikasi:

| Bagian | Teknologi | Port | Status |
| --- | --- | --- | --- |
| `Frontend/` | React 19 + Vite + TypeScript + Tailwind CSS 4 | 3000 | Aktif (UI + data mock) |
| `Backend/` | Node.js + Express (ES Modules) | 5000 | Stub (health check) |

> **Penting:** Saat ini frontend **belum** terhubung ke backend. Seluruh data masih berasal dari file mock di `Frontend/src/data/`. Integrasi API adalah salah satu item prioritas di [ROADMAP.md](./ROADMAP.md).

---

## Struktur Repository

```text
NIITS-WorkSpace/
├── Frontend/
│   ├── src/
│   │   ├── components/        # Komponen UI reusable
│   │   │   ├── Sidebar.tsx
│   │   │   ├── CommandPalette.tsx
│   │   │   ├── NewTaskModal.tsx
│   │   │   ├── TaskDetailDrawer.tsx
│   │   │   └── ...
│   │   ├── views/             # Halaman utama (routing via state)
│   │   │   ├── DashboardView.tsx
│   │   │   ├── ProjectWorkspaceView.tsx
│   │   │   ├── LearningView.tsx
│   │   │   ├── ArticlesView.tsx
│   │   │   └── ...
│   │   ├── data/
│   │   │   ├── mockData.ts    # Data mock utama
│   │   │   └── membersData.ts # Data profil anggota
│   │   ├── types/             # Tipe domain (learning, case management)
│   │   ├── types.ts           # Tipe domain inti
│   │   ├── App.tsx            # Root + router berbasis state
│   │   ├── main.tsx           # Entry point React
│   │   └── index.css          # Tailwind + styling global
│   ├── index.html
│   ├── vite.config.ts
│   └── package.json
│
├── Backend/
│   ├── src/
│   │   └── index.js           # Setup Express + endpoint
│   ├── .env.example
│   └── package.json
│
├── docs/
│   ├── SETUP.md
│   ├── ARCHITECTURE.md
│   ├── GIT-WORKFLOW.md
│   └── ROADMAP.md
│
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── LICENSE
├── README.md
└── .gitignore
```

---

## Frontend

### Pola Navigasi

Aplikasi tidak memakai React Router. Navigasi dikelola oleh state di `App.tsx`:

- `currentPage` menentukan view yang dirender (`renderCurrentView()`).
- Parameter navigasi (`room`, `role`, `chatId`, `tab`) disimpan sebagai state.
- `handleNavigate()` menjadi pusat perpindahan halaman.
- Beberapa state dipersist ke `localStorage` (mis. cover project: `niits_project_covers`).

### Alur Data (saat ini)

```text
mockData.ts / membersData.ts
        │
        ▼
  App.tsx (useState)  ──►  Views  ──►  Components
        │
        ▼
  localStorage (sebagian kecil state)
```

Seluruh operasi (tambah/ubah/hapus tugas) hanya mengubah state di memori — **hilang saat refresh**, kecuali yang dipersist manual.

---

## Backend

Setup Express minimal:

```text
Backend/src/index.js
├── helmet()            # Security headers
├── cors()              # CORS (saat ini terbuka)
├── express.json()      # Body parser
├── morgan('dev')       # Request logging
├── GET /               # Teks status
└── GET /api/health     # Health check JSON
```

Struktur yang direncanakan (lihat ROADMAP):

```text
Backend/src/
├── routes/         # Definisi endpoint
├── controllers/    # Handler request/response
├── middleware/     # Auth, validasi, error handling
├── services/       # Business logic
└── index.js        # Bootstrap aplikasi
```

---

## Arsitektur Target

```text
┌─────────────────────────────┐
│           Client            │
│     React + TypeScript      │
└──────────────┬──────────────┘
               │
               │ HTTP / REST API (JSON)
               ▼
┌─────────────────────────────┐
│          Express.js         │
│            API              │
├─────────────────────────────┤
│ Routes → Controllers        │
│ Middleware → Services       │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│          Database           │
└─────────────────────────────┘
```

Frontend bertanggung jawab atas UI dan interaksi pengguna; backend menangani API, business logic, autentikasi, dan pengolahan data.

---

## Prinsip

- **Modular** — pisahkan komponen, view, dan tipe dengan jelas.
- **Konsisten** — ikuti pola yang sudah ada di sekitar kode.
- **Aman** — jangan pernah commit secret; batasi CORS; validasi input di backend.
- **Teruji** — tambahkan test saat menyentuh logika bisnis baru.
