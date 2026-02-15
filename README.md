# 2026 Sistem Peminjaman Ruangan - Documentation

Dokumentasi utama untuk pengembangan dan operasional project peminjaman ruangan.

## Komponen Sistem

- `2026-room-booking-frontend` - React + TypeScript (web app)
- `2026-Sistem-Peminjaman-Ruangan-backend/RoomBooking.Api` - ASP.NET Core API
- `2026-Sistem-Peminjaman-Ruangan-mobile` - Flutter mobile app
- `2026-Sistem-Peminjaman-Ruangan-infrastructure` - panduan infrastruktur/devops

## Arsitektur Singkat

1. Frontend dan mobile memanggil endpoint backend.
2. Backend menyimpan data ke SQL Server.
3. Login menghasilkan JWT berisi role.
4. Client mengirim `Authorization: Bearer <token>` untuk endpoint terproteksi.

## Setup Lokal (Ringkas)

### Opsi A - Docker Compose

Jalankan dari root workspace:

```powershell
docker compose up --build
```

Service default:

- Frontend: `http://localhost:3000`
- Backend: `http://localhost:5271`
- SQL Server: `localhost:1433`

### Opsi B - Per Service

- Backend
  - `dotnet restore`
  - `dotnet run`
- Frontend
  - `npm install`
  - `npm start`
- Mobile
  - `flutter pub get`
  - `flutter run`

## Authentication & Authorization

- Authentication: JWT token dari endpoint login.
- Authorization: role-based access (`Admin`, `Borrower`).
- Frontend dan mobile merender halaman sesuai role setelah login.

## Validasi Minimal Sebelum Merge

- Frontend build sukses.
- Backend build sukses.
- Mobile `flutter analyze` dan `flutter test` sukses.
- Login + role redirect berfungsi.

## Workflow Git yang Direkomendasikan

- Branch dasar: `develop`
- Feature: `feature/<scope>`
- Bugfix: `bugfix/<scope>`
- PR harus menyertakan:
  - Ringkasan perubahan
  - Langkah verifikasi
  - Link issue (`Closes #<id>`)

## Roadmap Dokumentasi Lanjutan

- API spec per endpoint (request/response)
- ERD + migration strategy
- Deployment environment matrix (dev/staging/prod)
- Observability (logging, health check, alerting)
