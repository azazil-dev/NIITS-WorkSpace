# 🚀 NIITS WorkSpace

<p align="center">
  <strong>Central workspace for NIITS development team</strong><br>
  A collaborative environment for building, managing, and maintaining NIITS digital products.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Frontend-React-61DAFB?style=for-the-badge&logo=react&logoColor=white" />
  <img src="https://img.shields.io/badge/Backend-Express-000000?style=for-the-badge&logo=express&logoColor=white" />
  <img src="https://img.shields.io/badge/Runtime-Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Language-JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" />
</p>

---

## 🏢 About

**NIITS WorkSpace** is the central development repository used by the **NIITS team** to collaborate on software development, experimentation, internal tools, and digital products.

The workspace is designed to make development more:

* ⚡ **Efficient**
* 🤝 **Collaborative**
* 🧩 **Modular**
* 🔐 **Organized**
* 🚀 **Scalable**

This repository may contain multiple applications, services, experiments, and shared development resources.

---

## 🛠️ Tech Stack

### Frontend

| Technology   | Purpose                                |
| ------------ | -------------------------------------- |
| ⚛️ **React** | User interface & frontend applications |
| JavaScript   | Primary frontend language              |
| HTML5        | Application structure                  |
| CSS3         | Styling & layout                       |

### Backend

| Technology        | Purpose                     |
| ----------------- | --------------------------- |
| 🟢 **Node.js**    | JavaScript runtime          |
| 🚂 **Express.js** | REST API & backend services |
| JavaScript        | Backend development         |

### Development Tools

| Tool    | Purpose                             |
| ------- | ----------------------------------- |
| Git     | Version control                     |
| GitHub  | Repository & collaboration          |
| npm     | Package management                  |
| VS Code | Recommended development environment |

---

## 📁 Workspace Structure

```text
NIITS-WorkSpace/
│
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── ...
│
├── backend/
│   ├── src/
│   ├── routes/
│   ├── controllers/
│   ├── middleware/
│   ├── package.json
│   └── ...
│
├── docs/
│   └── ...
│
├── .gitignore
├── README.md
└── ...
```

> Struktur dapat berkembang mengikuti kebutuhan project dan standar tim.

---

# 🤝 Team Collaboration

Repository ini bersifat **team workspace**.

Setiap anggota tim diharapkan mengikuti workflow Git yang telah disepakati agar perubahan kode tetap terorganisir dan mudah direview.

### Development Flow

```text
        ┌──────────────┐
        │     main     │
        │  Production  │
        └──────┬───────┘
               │
               │ Pull Request
               ▼
        ┌──────────────┐
        │   develop    │
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
               │
               ▼
           develop
```

---

## 🌿 Branch Convention

Gunakan branch sesuai dengan jenis pekerjaan:

```text
main
develop

feature/<feature-name>
fix/<bug-name>
refactor/<area-name>
docs/<documentation-name>
```

### Examples

```bash
feature/authentication
feature/dashboard
fix/login-validation
refactor/api-service
docs/setup-guide
```

---

## 🔄 Recommended Git Workflow

### 1. Update local branch

```bash
git checkout develop
git pull origin develop
```

### 2. Create a new branch

```bash
git checkout -b feature/nama-feature
```

### 3. Develop

Kerjakan perubahan pada branch masing-masing.

### 4. Commit

Gunakan commit message yang jelas:

```bash
git add .
git commit -m "feat: add authentication"
```

Contoh lainnya:

```text
feat: add dashboard
fix: resolve login validation
refactor: improve api structure
docs: update setup guide
style: improve navbar layout
```

### 5. Push

```bash
git push origin feature/nama-feature
```

### 6. Pull Request

Setelah selesai:

```text
feature/* → develop
```

Buat **Pull Request** dan tunggu proses review sebelum melakukan merge.

---

# 📌 Development Rules

### ✅ Do

* Pull perubahan terbaru sebelum mulai bekerja.
* Gunakan branch sendiri untuk setiap feature/fix.
* Buat commit yang jelas dan terstruktur.
* Review kode sebelum membuat Pull Request.
* Jangan mengubah kode anggota lain tanpa koordinasi.
* Pastikan project dapat dijalankan sebelum melakukan PR.
* Dokumentasikan perubahan penting.

### ❌ Don't

* Jangan langsung push feature ke `main`.
* Jangan commit `.env`.
* Jangan commit `node_modules`.
* Jangan menggunakan commit message seperti `update`, `fix`, atau `test` tanpa konteks.
* Jangan merge PR sendiri tanpa review jika perubahan bersifat penting.

---

# ⚙️ Getting Started

## Prerequisites

Pastikan sudah terinstall:

* Node.js
* npm
* Git

Cek instalasi:

```bash
node --version
npm --version
git --version
```

---

## 📦 Installation

Clone repository:

```bash
git clone https://github.com/niitsinovasiteknologi/NIITS-WorkSpace.git
```

Masuk ke directory:

```bash
cd NIITS-WorkSpace
```

### Frontend

```bash
cd frontend
npm install
npm run dev
```

### Backend

Buka terminal baru:

```bash
cd backend
npm install
npm run dev
```

> Command dapat berubah mengikuti konfigurasi masing-masing project.

---

# 🔐 Environment Variables

Jangan pernah commit file `.env` ke repository.

Contoh:

```env
PORT=5000
DATABASE_URL=
JWT_SECRET=
```

Gunakan file:

```text
.env.example
```

sebagai template konfigurasi environment.

---

# 🧱 Architecture

Secara umum, aplikasi menggunakan pendekatan:

```text
┌─────────────────────────────┐
│           Client            │
│          React.js           │
└──────────────┬──────────────┘
               │
               │ HTTP / REST API
               ▼
┌─────────────────────────────┐
│          Express.js         │
│            API              │
├─────────────────────────────┤
│ Routes                      │
│ Controllers                 │
│ Middleware                  │
│ Services                    │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│          Database           │
└─────────────────────────────┘
```

Frontend bertanggung jawab terhadap **UI dan user interaction**, sedangkan backend menangani **API, business logic, authentication, dan data processing**.

---

# 🧪 Development Checklist

Sebelum membuat Pull Request:

```text
[ ] Feature berjalan dengan baik
[ ] Tidak ada error di console
[ ] Tidak ada credential / secret
[ ] Tidak ada node_modules yang ter-commit
[ ] Code sudah dirapikan
[ ] Commit message jelas
[ ] Branch sudah menggunakan naming convention
[ ] Sudah pull perubahan terbaru
[ ] Dokumentasi diperbarui jika diperlukan
```

---

# 📋 Project Status

| Area               | Status         |
| ------------------ | -------------- |
| Repository         | 🟢 Active      |
| Frontend           | ⚛️ React       |
| Backend            | 🟢 Express.js  |
| Team Collaboration | 🤝 Enabled     |
| Documentation      | 📝 In Progress |

---

# 👥 NIITS Team

> This repository is maintained and developed collaboratively by the **NIITS team**.

### Contributors

<a href="https://github.com/niitsinovasiteknologi">
  <img src="https://img.shields.io/badge/NIITS-Nova%20Teknologi-181717?style=for-the-badge&logo=github" />
</a>

---

# 📜 License

This project and its source code are intended for **NIITS internal development and team collaboration** unless otherwise specified.

---

<p align="center">
  <strong>Built with ❤️ by NIITS Team</strong>
  <br>
  <sub>Build • Collaborate • Ship</sub>
</p>
