# 🌿 Git Workflow

Panduan alur kerja Git untuk tim **NIITS WorkSpace**.

---

## Model Branch

```text
        ┌──────────────┐
        │     main     │
        │  Production  │
        └──────┬───────┘
               │
               │ Pull Request
               ▼
        ┌──────────────┐
        │   develop    │  (belum tersedia saat ini)
        │  Integration │
        └──────┬───────┘
               │
        ┌──────┴───────┐
        ▼              ▼
   feature/*       fix/*
        │              │
        └──────┬───────┘
               ▼
         Pull Request
               ▼
           develop
```

> ⚠️ **Status saat ini:** branch `develop` belum dibuat. Sementara ini buat branch dari `main` dan ajukan PR ke `main`. Setelah `develop` tersedia, gunakan alur di atas.

---

## Naming Convention

```text
feature/<feature-name>     # fitur baru
fix/<bug-name>             # perbaikan bug
refactor/<area-name>       # perbaikan struktur tanpa mengubah perilaku
docs/<documentation-name>  # dokumentasi
chore/<task-name>          # tooling, config, housekeeping
```

Contoh:

```text
feature/authentication
feature/dashboard-filter
fix/login-validation
refactor/api-service
docs/setup-guide
chore/eslint-setup
```

---

## Alur Kontribusi

### 1. Sinkronkan branch lokal

```bash
git checkout main
git pull upstream main
```

### 2. Buat branch baru

```bash
git checkout -b feature/nama-fitur
```

### 3. Kerjakan & commit

```bash
git add .
git commit -m "feat: tambah filter dashboard"
```

Gunakan **Conventional Commits** (lihat [CONTRIBUTING.md](../CONTRIBUTING.md#konvensi-commit)).

### 4. Push ke fork

```bash
git push origin feature/nama-fitur
```

### 5. Buka Pull Request

- Target: `main` (sementara) atau `develop` bila sudah tersedia.
- Jelaskan **apa**, **mengapa**, dan **bagaimana mengujinya**.

### 6. Review & merge

Tunggu proses review. Perubahan lanjutan cukup di-push ke branch yang sama.

---

## Menjaga Fork Tetap Update

```bash
git checkout main
git pull upstream main
git push origin main
```

---

## Rebase / Resolve Konflik

Bila branch tertinggal dari `main`:

```bash
git checkout feature/nama-fitur
git fetch upstream
git rebase upstream/main
# selesaikan konflik bila ada
git push origin feature/nama-fitur --force-with-lease
```

> Gunakan `--force-with-lease` (bukan `--force`) setelah rebase pada branch pribadi, dan **jangan** force-push ke branch bersama (`main`, `develop`).

---

## Yang Harus Dihindari

- ❌ Push langsung ke `main` atau `develop`.
- ❌ Commit `.env`, token, atau API key.
- ❌ Commit `node_modules` atau hasil build.
- ❌ Force-push ke branch bersama.
- ❌ Commit message seperti `update`, `fix`, atau `test` tanpa konteks.
