# Restoran Teal - Aplikasi Manajemen Restoran

Aplikasi restoran modern dengan tema Teal dan Putih yang profesional, dibangun dengan Next.js 15, TypeScript, dan Prisma.

## 🎨 Desain & Tema

- **Warna Dominan**: Teal (biru kehijauan) dan Putih
- **Tema**: Profesional dan bersih
- **Layout**: Responsif dengan kartu menu dan border-radius halus
- **Navigasi**: Compact sidebar untuk Admin Dashboard

## 📊 Struktur Database

### MenuItems
- ID (String)
- Nama Item (String)
- Kategori (Makanan/Minuman)
- Harga (Number)
- Status (Tersedia/Habis)
- Deskripsi (Opsional)

### Customers
- ID (String)
- Nama (String)
- Email (String, Unique)
- Nomor Telepon (String, Opsional)

### Orders
- ID Pesanan (String)
- ID Customer (String)
- Total Harga (Number)
- Tanggal Pemesanan (DateTime)
- Status (Diproses/Selesai/Dibatalkan)

### OrderItems (Junction Table)
- ID (String)
- ID Order (String)
- ID Menu Item (String)
- Quantity (Number)
- Price (Number)

## 🚀 Fitur

### Customer View (/)
- Tampilan menu makanan dan minuman
- Keranjang belanja real-time
- Status ketersediaan item
- Desain responsif dengan tema Teal

### Admin Dashboard (/admin)
- Dashboard dengan statistik
- Manajemen menu (CRUD)
- Manajemen pesanan
- Navigasi samping yang dapat di-collapse
- Update status pesanan real-time

## 🛠️ Teknologi

- **Frontend**: Next.js 15 dengan App Router
- **Bahasa**: TypeScript 5
- **Styling**: Tailwind CSS 4
- **UI Components**: shadcn/ui
- **Database**: SQLite dengan Prisma ORM
- **Icons**: Lucide React

## 📁 Struktur Proyek

```
src/
├── app/
│   ├── admin/                 # Admin Dashboard
│   ├── api/                   # API Routes
│   │   ├── menu-items/        # Menu CRUD API
│   │   ├── customers/         # Customer API
│   │   ├── orders/           # Order API
│   │   └── seed/             # Database seeding
│   ├── page.tsx              # Customer View
│   └── layout.tsx            # Root Layout
├── components/
│   └── ui/                   # shadcn/ui components
├── lib/
│   └── db.ts                 # Prisma client
└── ...
prisma/
└── schema.prisma             # Database schema
```

## 🗄️ API Endpoints

### Menu Items
- `GET /api/menu-items` - Ambil semua menu
- `POST /api/menu-items` - Tambah menu baru
- `GET /api/menu-items/[id]` - Ambil menu by ID
- `PUT /api/menu-items/[id]` - Update menu
- `DELETE /api/menu-items/[id]` - Hapus menu

### Customers
- `GET /api/customers` - Ambil semua customers
- `POST /api/customers` - Tambah customer baru

### Orders
- `GET /api/orders` - Ambil semua orders
- `POST /api/orders` - Buat order baru
- `GET /api/orders/[id]` - Ambil order by ID
- `PUT /api/orders/[id]` - Update status order

### Database Seeding
- `POST /api/seed` - Seed database dengan data awal

## 🚀 Cara Menjalankan

1. Install dependencies:
```bash
npm install
```

2. Push database schema:
```bash
npm run db:push
```

3. Seed database (opsional):
```bash
curl -X POST http://localhost:3000/api/seed
```

4. Jalankan development server:
```bash
npm run dev
```

5. Buka [http://localhost:3000](http://localhost:3000) untuk customer view
6. Buka [http://localhost:3000/admin](http://localhost:3000/admin) untuk admin dashboard

## 📝 Notes

- Aplikasi menggunakan tema Teal yang konsisten di seluruh interface
- Database menggunakan SQLite untuk development (dapat diubah ke PostgreSQL/MySQL untuk production)
- Admin sidebar dapat di-collapse untuk layar yang lebih kecil
- Status pesanan dapat di-update langsung dari admin dashboard
- Harga ditampilkan dalam format Rupiah (IDR)

## 🎯 Status

Sesi 1: Desain & Struktur Dasar ✅
- ✅ Desain tema Teal dan Putih
- ✅ Struktur database dengan Prisma
- ✅ API endpoints lengkap
- ✅ Admin Dashboard dengan navigasi samping
- ✅ Customer view dengan menu dan keranjang