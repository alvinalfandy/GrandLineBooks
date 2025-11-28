# 📚 GRANDLINEBOOKS - TOKO BUKU & STATIONERY ONLINE

<div align="center">

<img src="https://github.com/user-attachments/assets/44193b85-fc64-41fe-9297-5c2128ee78d8" alt="GrandLineBooks Banner" width="50">

[![ASP.NET Core](https://img.shields.io/badge/ASP.NET%20Core-9.0-512BD4?style=for-the-badge&logo=.net&logoColor=white)](https://dotnet.microsoft.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6.0+-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)](https://getbootstrap.com/)

**UTS Pemrograman Visual - Semester Ganjil 2024/2025**

</div>

---

## 👤 PROFIL MAHASISWA

| Field | Keterangan |
|-------|-----------|
| **Nama** | Alvin Alfandy |
| **NIM** | 312310473 |
| **Kelas** | TI.23.A.5 |
| **Mata Kuliah** | Pemrograman Visual |
| **Semester** | Ganjil 2024/2025 |

---

## 📋 DAFTAR ISI

1. [Cara Setting Web Service dan Configuration Web](#1-cara-setting-web-service-dan-configuration-web)
2. [Nama Project & Alasan Pemilihan](#2-nama-project--alasan-pemilihan)
3. [Business Process (Proses Bisnis)](#3-business-process-proses-bisnis)
4. [Model Data (Data Modeling)](#4-model-data-data-modeling)
5. [Schema Team (Struktur Tim)](#5-schema-team-struktur-tim)
6. [Mockup Project](#6-mockup-project)

---

## 1. CARA SETTING WEB SERVICE DAN CONFIGURATION WEB

### 📹 Video Tutorial Setup & Konfigurasi

l[!Youtube](https://img.shields.io/badge/YouTube-Watch%20Video-red)](https://youtu.be/ZAnYfGCxrlo?si=vzxxP92l9Bq7zQVs)

---

## 2. NAMA PROJECT & ALASAN PEMILIHAN

### 📖 Nama Project: **GrandLineBooks**

**GrandLineBooks** adalah sistem e-commerce berbasis web untuk toko buku dan stationery online yang memungkinkan customer untuk berbelanja buku secara online dan admin untuk mengelola toko dengan mudah.

---

### 🎯 Alasan Menggunakan Project Ini

#### **A. Relevansi dengan Kebutuhan Pasar**

- **Tren Digital**: Di era digital, transaksi online meningkat pesat. Toko buku perlu hadir secara online untuk menjangkau lebih banyak customer.
- **Kemudahan Akses**: Customer dapat berbelanja kapan saja, dimana saja tanpa harus datang ke toko fisik.
- **Efisiensi Operasional**: Admin dapat mengelola inventori, pesanan, dan customer dalam satu platform terpusat.

#### **B. Pembelajaran Komprehensif**

Project ini mencakup berbagai aspek pemrograman yang penting:

- **Backend Development**: Implementasi CRUD operations, business logic, authentication
- **Database Management**: Desain schema, query optimization dengan MongoDB NoSQL
- **Frontend Development**: User interface design, responsive layout dengan Bootstrap
- **Full-Stack Integration**: Koneksi antara backend (ASP.NET Core) dan frontend (Razor)
- **Security**: Authentication, authorization, password hashing
- **State Management**: Session handling, shopping cart

#### **C. Kompleksitas yang Sesuai**

- **Multi-Role System**: Admin dan Customer dengan hak akses berbeda
- **Transaction Flow**: Complete order lifecycle dari cart hingga delivery
- **Real-world Application**: Mirip dengan aplikasi e-commerce sesungguhnya (Tokopedia, Shopee)

#### **D. Teknologi Modern**

- **ASP.NET Core 9**: Framework terbaru dari Microsoft untuk web development
- **MongoDB**: Database NoSQL yang flexible dan scalable
- **MVC Pattern**: Separation of concerns yang clean dan maintainable

---

### 🛠️ Tech Stack

| Layer | Technology | Version |
|-------|------------|---------|
| **Backend** | ASP.NET Core MVC | 9.0 |
| **Database** | MongoDB | 6.0+ |
| **Frontend** | Razor Pages + Bootstrap | 5.3 |
| **Authentication** | Session-based | Built-in |
| **Language** | C# | 12.0 |

---

## 3. BUSINESS PROCESS (PROSES BISNIS)

### 🔄 A. CUSTOMER BUSINESS PROCESS

#### **1. Registration & Authentication Process**

```
START
  ↓
Customer mengakses website
  ↓
Pilih Register
  ↓
Input data: Name, Email, Password, Phone, Address
  ↓
[Validasi]
  ├─ Email sudah terdaftar? → Error: "Email sudah digunakan"
  └─ Email valid? → Lanjut
  ↓
Password di-hash (BCrypt)
  ↓
Data disimpan ke database (collection: users)
  ↓
Auto-login dengan session
  ↓
Redirect ke Customer Dashboard
  ↓
END
```

**Penjelasan:**
- Customer mendaftar dengan data lengkap
- System validasi email agar tidak duplicate
- Password di-hash untuk keamanan (tidak simpan plain text)
- Session dibuat untuk keep user logged in
- Customer langsung bisa mulai belanja

---

#### **2. Shopping & Cart Process**

```
START (Customer sudah login)
  ↓
Browse Catalog
  ↓
[Lihat Detail Produk]
  - Title, Author, Price, Description, Stock
  ↓
Klik "Add to Cart"
  ↓
[Cek Stock]
  ├─ Stock habis? → Alert: "Stok tidak tersedia"
  └─ Stock ada? → Lanjut
  ↓
Item masuk ke Cart (Session Storage)
  ↓
[Customer bisa:]
  ├─ Update Quantity
  ├─ Remove Item
  └─ Continue Shopping
  ↓
Klik "Checkout"
  ↓
END (lanjut ke Checkout Process)
```

**Penjelasan:**
- Customer browse katalog buku dengan filter/search
- Bisa lihat detail produk lengkap sebelum beli
- Cart menggunakan session storage (temporary)
- Customer bisa update/remove item sebelum checkout
- Real-time calculation total price

---

#### **3. Checkout & Order Process**

```
START (dari Cart)
  ↓
Customer klik "Checkout"
  ↓
Input/Verify Shipping Address
  ↓
[Validasi]
  ├─ Cart kosong? → Error: "Cart masih kosong"
  ├─ Address kosong? → Error: "Alamat harus diisi"
  └─ Valid? → Lanjut
  ↓
[Hitung Total]
  - Total = Sum(Item Price × Quantity)
  ↓
[Buat Order]
  - Generate Order ID
  - Status: PENDING
  - Save ke database (collection: orders)
  ↓
[Clear Cart]
  - Cart session di-hapus
  ↓
Show Success Page
  - Order Number
  - Total Amount
  - Estimated Delivery
  ↓
Customer bisa track order di "My Orders"
  ↓
END
```

**Penjelasan:**
- Customer input alamat pengiriman lengkap
- System validasi cart tidak kosong & address valid
- Order dibuat dengan status PENDING (menunggu admin process)
- Cart otomatis clear setelah checkout sukses
- Customer dapat order number untuk tracking

---

#### **4. Order Tracking Process**

```
START
  ↓
Customer akses "My Orders"
  ↓
[Tampilkan List Orders]
  - Order Number
  - Date
  - Total Amount
  - Status (Badge colored)
  ↓
Customer klik order untuk detail
  ↓
[Show Order Detail]
  - Order Info
  - Shipping Address
  - Items List (Book Title, Qty, Price)
  - Total Payment
  - Status dengan keterangan:
    • Pending: "Menunggu konfirmasi"
    • Processing: "Sedang diproses"
    • Shipped: "Dalam pengiriman"
    • Delivered: "Sudah sampai"
    • Cancelled: "Dibatalkan"
  ↓
END
```

**Penjelasan:**
- Customer bisa lihat semua order history
- Status order di-update real-time oleh admin
- Detail order lengkap dengan breakdown harga
- Customer bisa monitor progress pengiriman

---

### 🔄 B. ADMIN BUSINESS PROCESS

#### **1. Login Process**

```
START
  ↓
Admin akses "/Account/Login"
  ↓
Input Email & Password
  ↓
[Validasi Credentials]
  ├─ Email tidak ditemukan? → Error: "Email tidak terdaftar"
  ├─ Password salah? → Error: "Password salah"
  ├─ Role bukan Admin? → Error: "Akses ditolak"
  └─ Valid & Role = Admin? → Lanjut
  ↓
Create Admin Session
  ↓
Redirect ke Admin Dashboard
  ↓
END
```

**Penjelasan:**
- Hanya user dengan role ADMIN yang bisa akses
- Multi-layer validation untuk security
- Session-based authentication

---

#### **2. Book Management Process (CRUD)**

##### **CREATE Book**

```
START
  ↓
Admin klik "Tambah Buku"
  ↓
[Input Data Book]
  - Title
  - Author
  - Category
  - Description
  - Price
  - Stock
  - Image Upload
  ↓
[Validasi]
  ├─ Field kosong? → Error: "Semua field harus diisi"
  ├─ Price < 0? → Error: "Harga harus positif"
  ├─ Stock < 0? → Error: "Stok tidak valid"
  └─ Valid? → Lanjut
  ↓
[Upload Image]
  - Save to /wwwroot/images/books/
  - Get image URL
  ↓
Save to database (collection: books)
  - isActive = true
  - createdAt = DateTime.Now
  ↓
Success: "Buku berhasil ditambahkan"
  ↓
Redirect ke Book List
  ↓
END
```

##### **READ/VIEW Books**

```
START
  ↓
Admin akses "Kelola Buku"
  ↓
[Load All Books from DB]
  - Join dengan category (jika ada)
  - Sort by createdAt DESC
  ↓
[Display Table]
  - Book ID
  - Title
  - Author
  - Category
  - Price
  - Stock
  - Status (Active/Inactive)
  - Actions (Edit, Delete)
  ↓
[Admin bisa:]
  ├─ Search by title/author
  ├─ Filter by category
  └─ Sort by price/stock
  ↓
END
```

##### **UPDATE Book**

```
START
  ↓
Admin klik "Edit" pada buku
  ↓
Load existing data ke form
  ↓
Admin ubah data yang perlu
  ↓
[Validasi] (sama seperti CREATE)
  ↓
Update database (collection: books)
  - Keep createdAt
  - Update other fields
  ↓
Success: "Buku berhasil diupdate"
  ↓
Redirect ke Book List
  ↓
END
```

##### **DELETE Book**

```
START
  ↓
Admin klik "Hapus" pada buku
  ↓
[Confirmation Dialog]
  - "Yakin hapus buku ini?"
  ↓
[Cek Dependencies]
  ├─ Ada di order yang belum selesai? → Soft Delete (isActive = false)
  └─ Tidak ada? → Hard Delete
  ↓
[Execute Delete]
  - Soft: UPDATE isActive = false
  - Hard: DELETE dari database
  ↓
Success: "Buku berhasil dihapus"
  ↓
Redirect ke Book List
  ↓
END
```

**Penjelasan CRUD:**
- **CREATE**: Admin tambah buku baru dengan upload image
- **READ**: View semua buku dengan filter & search
- **UPDATE**: Edit detail buku existing
- **DELETE**: Soft delete untuk maintain referential integrity

---

#### **3. Order Management Process**

```
START
  ↓
Admin akses "Kelola Pesanan"
  ↓
[Load All Orders]
  - Join dengan users (customer data)
  - Sort by orderDate DESC
  ↓
[Display Orders Table]
  - Order Number
  - Customer Name
  - Date
  - Total Amount
  - Status (Badge colored)
  - Actions (View Detail, Update Status)
  ↓
[Filter Options]
  ├─ By Status (Pending, Processing, Shipped, Delivered, Cancelled)
  ├─ By Date Range
  └─ By Customer
  ↓
Admin klik "Detail" pada order
  ↓
[Show Order Detail Page]
  - Order Info (ID, Date, Status)
  - Customer Info (Name, Email, Phone)
  - Shipping Address
  - Items List dengan qty & price
  - Total Payment
  ↓
[Update Status Buttons]
  ├─ Processing → Status = "Processing"
  ├─ Shipped → Status = "Shipped"
  ├─ Delivered → Status = "Delivered"
  └─ Cancel → Status = "Cancelled"
  ↓
Admin pilih status baru
  ↓
[Confirmation]
  - "Update status ke [Status]?"
  ↓
Update database (collection: orders)
  - Set new status
  - Update timestamp
  ↓
Success: "Status order berhasil diupdate"
  ↓
Notification ke Customer (jika ada email feature)
  ↓
END
```

**Penjelasan:**
- Admin bisa lihat semua order dari semua customer
- Filter & search untuk cari order spesifik
- Update status order sesuai progress pengiriman
- Customer otomatis lihat perubahan status di akun mereka

---

#### **4. User Management Process**

```
START
  ↓
Admin akses "Kelola User"
  ↓
[Load All Users]
  - Filter: Role, isActive
  - Sort by createdAt DESC
  ↓
[Display Users Table]
  - User ID
  - Name
  - Email
  - Phone
  - Role (Admin/Customer)
  - Status (Active/Inactive)
  - Actions (View, Edit, Activate/Deactivate)
  ↓
[Admin bisa:]
  ├─ View user detail
  ├─ Edit user data
  ├─ Change role
  ├─ Activate/Deactivate account
  └─ Delete user (jika diperlukan)
  ↓
END
```

**Penjelasan:**
- Admin manage semua user (customer & admin)
- Bisa activate/deactivate account untuk suspend user
- Role management untuk promote/demote user

---

### 📊 C. FLOW DIAGRAM LENGKAP

```
┌─────────────────────────────────────────────────────────────────┐
│                       GRANDLINEBOOKS SYSTEM                      │
└─────────────────────────────────────────────────────────────────┘
                                ↓
                ┌───────────────┴───────────────┐
                ↓                               ↓
        ┌──────────────┐                ┌──────────────┐
        │   CUSTOMER   │                │    ADMIN     │
        └──────────────┘                └──────────────┘
                ↓                               ↓
        ┌──────────────┐                ┌──────────────┐
        │ Register/    │                │    Login     │
        │    Login     │                └──────────────┘
        └──────────────┘                        ↓
                ↓                       ┌──────────────────┐
        ┌──────────────┐                │    Dashboard     │
        │   Browse     │                │  (View Stats)    │
        │   Catalog    │                └──────────────────┘
        └──────────────┘                        ↓
                ↓                       ┌──────────────────┐
        ┌──────────────┐                │  Kelola Buku     │
        │ View Product │                │  (CRUD Books)    │
        │   Detail     │                └──────────────────┘
        └──────────────┘                        ↓
                ↓                       ┌──────────────────┐
        ┌──────────────┐                │ Kelola Pesanan   │
        │  Add to Cart │                │ (Update Status)  │
        └──────────────┘                └──────────────────┘
                ↓                               ↓
        ┌──────────────┐                ┌──────────────────┐
        │  View Cart   │                │  Kelola User     │
        │ (Update Qty) │                │  (Manage Users)  │
        └──────────────┘                └──────────────────┘
                ↓
        ┌──────────────┐
        │   Checkout   │
        │ (Input Addr) │
        └──────────────┘
                ↓
        ┌──────────────┐
        │ Order Created│
        │(Status:Pending)│
        └──────────────┘
                ↓
        ┌──────────────┐
        │  My Orders   │
        │(Track Status)│
        └──────────────┘
```

---

## 4. MODEL DATA (DATA MODELING)

### 🗄️ Database: MongoDB (NoSQL Document-Oriented)

MongoDB dipilih karena:
- **Flexible Schema**: Mudah modifikasi struktur data
- **Scalable**: Support horizontal scaling
- **JSON-like**: Easy integration dengan aplikasi web
- **Performance**: Fast read/write operations

---

### 📦 A. COLLECTION: `users`

**Deskripsi:** Menyimpan data semua user (Admin & Customer)

```json
{
  "_id": ObjectId("67890abcdef1234567890abc"),
  "name": "John Doe",
  "email": "john.doe@example.com",
  "password": "$2a$11$hashed_password_here",
  "phone": "081234567890",
  "address": "Jl. Sudirman No. 123, Jakarta Pusat",
  "role": "Customer",
  "isActive": true,
  "createdAt": ISODate("2025-01-15T08:30:00Z")
}
```

#### **Field Explanation:**

| Field | Type | Description | Constraint |
|-------|------|-------------|------------|
| `_id` | ObjectId | Primary key unik otomatis dari MongoDB | Auto-generated |
| `name` | String | Nama lengkap user | Required, min 3 chars |
| `email` | String | Email untuk login | Required, unique, valid email format |
| `password` | String | Password ter-hash (BCrypt) | Required, min 6 chars, hashed |
| `phone` | String | Nomor telepon | Optional, numeric |
| `address` | String | Alamat lengkap user | Optional, dibutuhkan saat checkout |
| `role` | String | Role user | Required, enum: ["Admin", "Customer"] |
| `isActive` | Boolean | Status aktif/nonaktif | Default: true |
| `createdAt` | DateTime | Tanggal registrasi | Auto-generated |

#### **Business Rules:**
- Email harus unique (tidak boleh duplicate)
- Password minimum 6 karakter dan di-hash dengan BCrypt
- Role default untuk registrasi adalah "Customer"
- Admin hanya bisa dibuat manual atau promote dari existing user
- User dengan isActive = false tidak bisa login

---

### 📦 B. COLLECTION: `books`

**Deskripsi:** Menyimpan data produk (buku & stationery)

```json
{
  "_id": ObjectId("67890def1234567890abcdef"),
  "title": "Clean Code: A Handbook of Agile Software Craftsmanship",
  "author": "Robert C. Martin",
  "category": "Programming",
  "description": "Even bad code can function. But if code isn't clean...",
  "price": 250000,
  "stock": 15,
  "imageUrl": "/images/books/clean-code.jpg",
  "isActive": true,
  "createdAt": ISODate("2025-01-10T10:00:00Z")
}
```

#### **Field Explanation:**

| Field | Type | Description | Constraint |
|-------|------|-------------|------------|
| `_id` | ObjectId | Primary key unik buku | Auto-generated |
| `title` | String | Judul buku | Required, min 3 chars |
| `author` | String | Nama penulis | Required |
| `category` | String | Kategori buku | Required, e.g., "Fiction", "Programming" |
| `description` | String | Deskripsi lengkap buku | Optional, max 1000 chars |
| `price` | Decimal | Harga buku dalam Rupiah | Required, min 0 |
| `stock` | Integer | Jumlah stok tersedia | Required, min 0 |
| `imageUrl` | String | Path gambar cover buku | Optional, default placeholder |
| `isActive` | Boolean | Status produk (aktif/nonaktif) | Default: true |
| `createdAt` | DateTime | Tanggal produk ditambahkan | Auto-generated |

#### **Business Rules:**
- Price harus positif (> 0)
- Stock tidak boleh negatif
- isActive = false berarti produk tidak tampil di katalog (soft delete)
- Image upload disimpan di `/wwwroot/images/books/`
- Category bisa di-expand jadi collection terpisah untuk normalization

---

### 📦 C. COLLECTION: `orders`

**Deskripsi:** Menyimpan data pesanan customer

```json
{
  "_id": ObjectId("67890xyz1234567890abcxyz"),
  "customerId": ObjectId("67890abcdef1234567890abc"),
  "orderDate": ISODate("2025-01-20T14:30:00Z"),
  "status": "Processing",
  "totalAmount": 575000,
  "shippingAddress": "Jl. Gatot Subroto No. 45, Bandung, Jawa Barat",
  "items": [
    {
      "bookId": ObjectId("67890def1234567890abcdef"),
      "bookTitle": "Clean Code",
      "quantity": 2,
      "price": 250000
    },
    {
      "bookId": ObjectId("67891def1234567890abcxxx"),
      "bookTitle": "Design Patterns",
      "quantity": 1,
      "price": 75000
    }
  ]
}
```

#### **Field Explanation:**

| Field | Type | Description | Constraint |
|-------|------|-------------|------------|
| `_id` | ObjectId | Primary key unik order | Auto-generated |
| `customerId` | ObjectId | Reference ke users collection | Required, foreign key |
| `orderDate` | DateTime | Tanggal & waktu order dibuat | Auto-generated |
| `status` | String | Status pesanan | Required, enum: ["Pending", "Processing", "Shipped", "Delivered", "Cancelled"] |
| `totalAmount` | Decimal | Total harga keseluruhan | Required, calculated |
| `shippingAddress` | String | Alamat pengiriman lengkap | Required |
| `items` | Array of Objects | List produk yang dipesan | Required, min 1 item |
| `items.bookId` | ObjectId | Reference ke books collection | Required |
| `items.bookTitle` | String | Judul buku (denormalized) | Required |
| `items.quantity` | Integer | Jumlah item dipesan | Required, min 1 |
| `items.price` | Decimal | Harga per item saat order | Required (immutable) |

#### **Status Flow:**

```
Pending → Processing → Shipped → Delivered
   ↓
Cancelled (bisa dari Pending atau Processing)
```

#### **Business Rules:**
- Order hanya bisa dibuat oleh logged-in customer
- customerId otomatis dari session user
- Status awal selalu "Pending"
- totalAmount = SUM(items.quantity × items.price)
- items.price disimpan saat order dibuat (immutable) untuk historical accuracy
- shippingAddress wajib diisi saat checkout
- Order tidak bisa diedit setelah dibuat (hanya status yang bisa diupdate)
- bookTitle di-denormalize untuk performa read (tidak perlu join)

---

### 🔗 D. RELATIONSHIP DIAGRAM

```
┌─────────────────┐
│     USERS       │
│  (Collection)   │
├─────────────────┤
│ _id (PK)        │◄──────────┐
│ name            │           │
│ email (unique)  │           │ customerId (FK)
│ password        │           │
│ role            │           │
│ isActive        │           │
└─────────────────┘           │
                              │
                              │
                    ┌─────────┴────────┐
                    │     ORDERS       │
                    │  (Collection)    │
                    ├──────────────────┤
                    │ _id (PK)         │
                    │ customerId (FK)  │
                    │ orderDate        │
                    │ status           │
                    │ totalAmount      │
                    │ shippingAddress  │
                    │ items []         │─┐
                    └──────────────────┘ │
                                         │
                                         │ bookId (FK)
                    ┌────────────────────┘
                    │
                    ↓
         ┌─────────────────┐
         │     BOOKS       │
         │  (Collection)   │
         ├─────────────────┤
         │ _id (PK)        │
         │ title           │
         │ author          │
         │ category        │
         │ price           │
         │ stock           │
         │ isActive        │
         └─────────────────┘
```

**Relationship Type:**
- **users ↔ orders**: One-to-Many (1 customer bisa punya banyak orders)
- **books ↔ orders**: Many-to-Many (melalui embedded array `items` di orders)

---

### 📊 E. SAMPLE DATA EXAMPLE

#### **Sample User (Customer):**

```json
{
  "_id": ObjectId("674a1b2c3d4e5f6789012345"),
  "name": "Budi Santoso",
  "email": "budi.santoso@gmail.com",
  "password": "$2a$11$X8Y9Z...",
  "phone": "08123456789",
  "address": "Jl. Merdeka No. 100, Jakarta Selatan 12345",
  "role": "Customer",
  "isActive": true,
  "createdAt": ISODate("2025-01-15T10:30:00Z")
}
```

#### **Sample Book:**

```json
{
  "_id": ObjectId("674b2c3d4e5f678901234567"),
  "title": "Laskar Pelangi",
  "author": "Andrea Hirata",
  "category": "Novel",
  "description": "Novel tentang kehidupan 10 anak dari keluarga miskin di Belitung",
  "price": 85000,
  "stock": 25,
  "imageUrl": "/images/books/laskar-pelangi.jpg",
  "isActive": true,
  "createdAt": ISODate("2025-01-10T08:00:00Z")
}
```

#### **Sample Order:**

```json
{
  "_id": ObjectId("674c3d4e5f67890123456789"),
  "customerId": ObjectId("674a1b2c3d4e5f6789012345"),
  "orderDate": ISODate("2025-01-20T15:45:00Z"),
  "status": "Shipped",
  "totalAmount": 335000,
  "shippingAddress": "Jl. Merdeka No. 100, Jakarta Selatan 12345",
  "items": [
    {
      "bookId": ObjectId("674b2c3d4e5f678901234567"),
      "bookTitle": "Laskar Pelangi",
      "quantity": 2,
      "price": 85000
    },
    {
      "bookId": ObjectId("674b2c3d4e5f678901234999"),
      "bookTitle": "Bumi Manusia",
      "quantity": 1,
      "price": 165000
    }
  ]
}
```

---

## 5. SCHEMA TEAM (STRUKTUR TIM)

### 👥 A. STRUKTUR ORGANISASI TIM

```
                    ┌─────────────────────┐
                    │   PROJECT MANAGER   │
                    │   (Team Leader)     │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              ↓                ↓                ↓
    ┌─────────────────┐ ┌─────────────┐ ┌─────────────────┐
    │ BACKEND DEV     │ │ FRONTEND    │ │ DATABASE        │
    │ (2 orang)       │ │ DEVELOPER   │ │ ADMINISTRATOR   │
    └─────────────────┘ │ (2 orang)   │ └─────────────────┘
                        └─────────────┘
              ↓                ↓                ↓
    ┌─────────────────┐ ┌─────────────┐ ┌─────────────────┐
    │ QA/TESTER       │ │ UI/UX       │ │ DOCUMENTATION   │
    │ (1 orang)       │ │ DESIGNER    │ │ SPECIALIST      │
    │                 │ │ (1 orang)   │ │ (1 orang)       │
    └─────────────────┘ └─────────────┘ └─────────────────┘
```

**Total Tim: 8 Orang**

---

### 📋 B. DETAIL ROLE & TANGGUNG JAWAB

#### **1. Project Manager / Team Leader** (1 orang)

**Tanggung Jawab:**
- 📌 Koordinasi keseluruhan project
- 📌 Planning & scheduling timeline
- 📌 Distribusi task ke anggota tim
- 📌 Monitoring progress development
- 📌 Quality assurance & code review
- 📌 Meeting coordination & reporting
- 📌 Risk management & problem solving

**Tools:**
- Trello/Jira untuk task management
- GitHub Projects untuk development tracking
- Google Meet/Zoom untuk meeting
- Google Docs untuk documentation

**Deliverables:**
- Project timeline & milestone
- Weekly progress report
- Risk assessment document
- Final project report

---

#### **2. Backend Developer** (2 orang)

**Backend Dev 1 - Authentication & User Management:**
- 🔧 Implement authentication system (register, login, logout)
- 🔧 Session management
- 🔧 Password hashing & security
- 🔧 User CRUD operations
- 🔧 Role-based authorization middleware

**Backend Dev 2 - Business Logic & API:**
- 🔧 Implement book management (CRUD)
- 🔧 Shopping cart logic
- 🔧 Order processing & management
- 🔧 Status update logic
- 🔧 Data validation & error handling

**Shared Responsibilities:**
- MongoDB integration & queries
- ASP.NET Core MVC controllers
- Business logic implementation
- API endpoint creation
- Unit testing
- Code documentation

**Tech Stack:**
- C# & ASP.NET Core 9 MVC
- MongoDB.Driver
- BCrypt untuk password hashing
- Entity Framework (optional)

**Deliverables:**
- Functional controllers
- Service layer classes
- MongoDB queries
- API documentation
- Unit test cases

---

#### **3. Frontend Developer** (2 orang)

**Frontend Dev 1 - Customer Interface:**
- 🎨 Home page & landing page
- 🎨 Catalog & product listing
- 🎨 Product detail page
- 🎨 Shopping cart interface
- 🎨 Checkout form
- 🎨 Customer dashboard & order tracking

**Frontend Dev 2 - Admin Interface:**
- 🎨 Admin dashboard
- 🎨 Book management interface (CRUD forms)
- 🎨 Order management interface
- 🎨 User management interface
- 🎨 Statistics & reports visualization

**Shared Responsibilities:**
- Razor views (.cshtml) development
- Responsive design (mobile & desktop)
- Bootstrap 5 styling
- JavaScript for interactivity
- Form validation (client-side)
- UI/UX consistency
- Cross-browser compatibility

**Tech Stack:**
- HTML5, CSS3, JavaScript
- Razor syntax
- Bootstrap 5
- jQuery
- Font Awesome icons

**Deliverables:**
- All Razor views
- CSS stylesheets
- JavaScript files
- Responsive layouts
- UI component library

---

#### **4. Database Administrator** (1 orang)

**Tanggung Jawab:**
- 💾 MongoDB database design & schema
- 💾 Collection structure planning
- 💾 Index optimization untuk performance
- 💾 Data seeding untuk testing
- 💾 Backup & recovery strategy
- 💾 Query optimization
- 💾 Database documentation
- 💾 Data migration (jika ada)

**Tech Stack:**
- MongoDB
- MongoDB Compass
- Aggregation pipeline
- Indexing strategy

**Deliverables:**
- Database schema documentation
- Collection structure diagram
- Sample data seeds
- Backup procedures
- Performance tuning report

---

#### **5. UI/UX Designer** (1 orang)

**Tanggung Jawab:**
- 🎨 User interface mockups & wireframes
- 🎨 Design system & style guide
- 🎨 Color scheme & typography selection
- 🎨 Icon & asset creation
- 🎨 User flow diagram
- 🎨 Usability testing
- 🎨 Design feedback & iteration

**Tools:**
- Figma/Adobe XD untuk mockup
- Balsamiq untuk wireframes
- Adobe Photoshop untuk image editing
- ColorHunt untuk color palette

**Deliverables:**
- UI mockups (high-fidelity)
- Wireframes (low-fidelity)
- Style guide document
- Asset files (images, icons)
- User flow diagrams

---

#### **6. QA/Tester** (1 orang)

**Tanggung Jawab:**
- 🧪 Manual testing semua features
- 🧪 Bug reporting & tracking
- 🧪 Test case creation
- 🧪 Regression testing
- 🧪 User acceptance testing (UAT)
- 🧪 Performance testing
- 🧪 Cross-browser testing
- 🧪 Security testing

**Test Scenarios:**
- Authentication flow (login, register, logout)
- CRUD operations (books, orders, users)
- Shopping cart functionality
- Checkout process
- Order status updates
- Error handling
- Edge cases

**Tools:**
- Manual testing
- Browser dev tools
- Postman (untuk API testing)
- Bug tracking (GitHub Issues)

**Deliverables:**
- Test case document
- Bug report list
- Test result summary
- UAT report

---

#### **7. Documentation Specialist** (1 orang)

**Tanggung Jawab:**
- 📝 Technical documentation
- 📝 User manual (admin & customer)
- 📝 API documentation
- 📝 Installation guide
- 📝 Code comments review
- 📝 README creation
- 📝 Video tutorial script
- 📝 Presentation slides

**Deliverables:**
- README.md
- User manual PDF
- Technical documentation
- API reference
- Installation guide
- Video tutorial (optional)
- Presentation slides

---

### 📅 C. TIMELINE & MILESTONE

```
┌─────────────────────────────────────────────────────────────┐
│                   PROJECT TIMELINE (8 Weeks)                │
└─────────────────────────────────────────────────────────────┘

Week 1-2: PLANNING & DESIGN
  ├─ Requirement gathering
  ├─ Database design
  ├─ UI/UX mockups
  └─ Project setup

Week 3-4: DEVELOPMENT PHASE 1 (Core Features)
  ├─ Authentication system
  ├─ Book management (CRUD)
  ├─ Basic UI implementation
  └─ Database setup

Week 5-6: DEVELOPMENT PHASE 2 (Advanced Features)
  ├─ Shopping cart
  ├─ Checkout & order processing
  ├─ Order management
  └─ Admin dashboard

Week 7: TESTING & BUG FIXING
  ├─ Manual testing
  ├─ Bug fixing
  ├─ Performance optimization
  └─ UAT

Week 8: DEPLOYMENT & DOCUMENTATION
  ├─ Final testing
  ├─ Documentation completion
  ├─ Deployment
  └─ Presentation preparation
```

---

### 🔄 D. WORKFLOW & COLLABORATION

#### **Development Workflow:**

```
1. Task Assignment (Project Manager)
   ↓
2. Development (Developers)
   ↓
3. Code Review (Project Manager + Peers)
   ↓
4. Testing (QA/Tester)
   ↓
5. Bug Fixing (Developers)
   ↓
6. Documentation (Documentation Specialist)
   ↓
7. Deployment
```

#### **Meeting Schedule:**

**Daily Standup:** 15 menit setiap pagi
- What did you do yesterday?
- What will you do today?
- Any blockers?

**Weekly Review:** 1 jam setiap Jumat
- Progress review
- Demo completed features
- Sprint planning

**Sprint Planning:** Awal setiap sprint (2 weeks)
- Task breakdown
- Assignment
- Timeline adjustment

---

### 🛠️ E. TOOLS & TECHNOLOGIES

#### **Collaboration Tools:**
- **Version Control**: Git + GitHub
- **Task Management**: Trello/Jira
- **Communication**: Slack/Discord + WhatsApp
- **Meeting**: Google Meet/Zoom
- **Documentation**: Google Docs/Notion
- **Design**: Figma/Balsamiq

#### **Development Tools:**
- **IDE**: Visual Studio 2022 / VS Code
- **Database**: MongoDB Compass
- **API Testing**: Postman
- **Browser**: Chrome DevTools

---

### 📊 F. PEMBAGIAN TASK DETAIL

#### **Sprint 1 (Week 1-2): Setup & Core**

| Developer | Task | Estimated Time |
|-----------|------|----------------|
| Backend Dev 1 | Setup project, authentication | 16 hours |
| Backend Dev 2 | MongoDB integration, models | 16 hours |
| Frontend Dev 1 | Layout templates, home page | 14 hours |
| Frontend Dev 2 | Admin dashboard layout | 14 hours |
| DB Admin | Schema design, seeding | 10 hours |
| UI/UX | Mockups & wireframes | 16 hours |
| QA | Test plan creation | 6 hours |
| Docs | Technical spec draft | 8 hours |

#### **Sprint 2 (Week 3-4): Main Features**

| Developer | Task | Estimated Time |
|-----------|------|----------------|
| Backend Dev 1 | User management CRUD | 12 hours |
| Backend Dev 2 | Book management CRUD | 12 hours |
| Frontend Dev 1 | Catalog, product detail | 16 hours |
| Frontend Dev 2 | Book management UI | 14 hours |
| DB Admin | Query optimization | 8 hours |
| UI/UX | Style guide, assets | 10 hours |
| QA | Feature testing | 12 hours |
| Docs | User manual draft | 10 hours |

#### **Sprint 3 (Week 5-6): Advanced Features**

| Developer | Task | Estimated Time |
|-----------|------|----------------|
| Backend Dev 1 | Shopping cart logic | 14 hours |
| Backend Dev 2 | Order processing | 16 hours |
| Frontend Dev 1 | Cart, checkout UI | 18 hours |
| Frontend Dev 2 | Order management UI | 16 hours |
| DB Admin | Performance tuning | 8 hours |
| UI/UX | UI refinement | 8 hours |
| QA | Integration testing | 16 hours |
| Docs | API documentation | 12 hours |

#### **Sprint 4 (Week 7-8): Polish & Deploy**

| Developer | Task | Estimated Time |
|-----------|------|----------------|
| Backend Dev 1 | Bug fixing, optimization | 10 hours |
| Backend Dev 2 | Bug fixing, validation | 10 hours |
| Frontend Dev 1 | UI polish, responsive | 12 hours |
| Frontend Dev 2 | UI polish, accessibility | 12 hours |
| DB Admin | Backup, deployment | 8 hours |
| UI/UX | Final design review | 6 hours |
| QA | UAT, final testing | 16 hours |
| Docs | Final documentation | 14 hours |

---

### 🎯 G. SUCCESS METRICS

#### **Team Performance KPIs:**
- ✅ Task completion rate: Target 95%
- ✅ Code review completion: 100%
- ✅ Bug resolution time: Max 48 hours
- ✅ Test coverage: Min 80%
- ✅ Meeting attendance: Min 90%
- ✅ On-time delivery: 100%

#### **Project Success Criteria:**
- ✅ All core features implemented
- ✅ Zero critical bugs
- ✅ < 5 minor bugs remaining
- ✅ Performance: Page load < 3 seconds
- ✅ Mobile responsive: 100%
- ✅ Documentation: Complete
- ✅ User satisfaction: > 85%

---

## 6. MOCKUP PROJECT

### 🎨 Desain Interface Aplikasi

Mockup dibuat menggunakan **Balsamiq Wireframes** untuk visualisasi interface sebelum development.

---

### 📱 A. PUBLIC PAGES

#### **1. Dashboard (Landing Page)**

![Dashboard](https://github.com/user-attachments/assets/e28bd7e5-d5a3-4dae-b685-d32e5ac3d9ad)

**Deskripsi:**
- Halaman utama yang ditampilkan saat pertama kali mengakses website
- Menampilkan banner welcome dan navigasi utama
- Quick access ke fitur Register/Login
- Featured books atau promo (optional)

---

#### **2. Login Page**

![Login](https://github.com/user-attachments/assets/496e52fb-5a84-40be-b788-90905370a1b5)

**Deskripsi:**
- Halaman login untuk customer dan admin
- User memasukkan email dan password untuk autentikasi
- Link ke halaman Register untuk user baru
- Forgot password (optional)

---

#### **3. Register Page**

![Register](https://github.com/user-attachments/assets/6345f08c-55dc-417c-a24c-0540e95c6d01)

**Deskripsi:**
- Halaman registrasi untuk customer baru
- Input data: Nama, Email, Password, Phone, Alamat
- Validasi form (email format, password length)
- Auto-redirect ke dashboard setelah register sukses

---

### 👨‍💼 B. ADMIN PAGES

#### **1. Dashboard Admin**

![Dashboard Admin](https://github.com/user-attachments/assets/92cc08b2-3b6e-4ffc-8cd3-dcff3f1fa6be)

**Deskripsi:**
- Dashboard admin menampilkan statistik real-time:
  - Total Produk
  - Total Pesanan
  - Total Customer
  - Revenue (optional)
- Grafik penjualan bulanan
- Quick access ke manajemen utama

---

#### **2. Kelola Buku (Admin)**

![Kelola Buku](https://github.com/user-attachments/assets/4c605cd8-9c1f-46bf-8df3-db94fd494b5f)

**Deskripsi:**
- Halaman manajemen buku dengan tabel lengkap
- Kolom: ID, Judul, Penulis, Kategori, Harga, Stok, Status
- Fitur search dan filter kategori
- Tombol aksi: Tambah, Edit, Hapus untuk setiap buku
- Pagination untuk data banyak

---

#### **3. Tambah Buku Baru (Admin)**

![Tambah Buku](https://github.com/user-attachments/assets/940b38e2-eb59-486d-8d6a-2140f3e7b905)

**Deskripsi:**
- Form untuk menambah buku baru ke katalog
- Input fields: Judul, Penulis, Kategori, Deskripsi, Harga, Stok
- Upload gambar cover buku
- Validasi form sebelum submit
- Button: Simpan atau Cancel

---

#### **4. Edit Buku (Admin)**

![Edit Buku](https://github.com/user-attachments/assets/e476ca77-50f7-4368-b463-9e8049969a1e)

**Deskripsi:**
- Form edit buku existing
- Data sebelumnya ter-load otomatis
- Admin dapat mengubah field yang diperlukan
- Preview image lama, bisa upload image baru
- Button: Update atau Cancel

---

#### **5. Kelola User (Admin)**

![Kelola User](https://github.com/user-attachments/assets/71b38259-4615-4684-b8c2-519487d3e0bd)

**Deskripsi:**
- Halaman manajemen user (customer & admin)
- Tabel menampilkan: ID, Nama, Email, Phone, Role, Status
- Admin dapat:
  - View detail user
  - Edit data user
  - Change role (Customer ↔ Admin)
  - Activate/Deactivate akun
- Search & filter by role

---

#### **6. Kelola Pesanan (Admin)**

![Kelola Pesanan](https://github.com/user-attachments/assets/4c8275b7-88ac-47db-ba38-c00b5d658c05)

**Deskripsi:**
- Halaman manajemen semua pesanan
- Tabel: Order Number, Customer, Date, Total, Status
- Status dengan color badge:
  - Pending: Yellow
  - Processing: Blue
  - Shipped: Purple
  - Delivered: Green
  - Cancelled: Red
- Filter berdasarkan status dan date range
- Tombol aksi: View Detail, Update Status

---

#### **7. Detail Pesanan (Admin)**

![Detail Pesanan Admin](https://github.com/user-attachments/assets/aec4ec18-1578-45af-9531-da45bd67fe99)

**Deskripsi:**
- Detail lengkap pesanan yang dipilih
- Info customer: Nama, Email, Phone
- Alamat pengiriman lengkap
- List item yang dipesan (judul, qty, harga)
- Total pembayaran
- Tombol update status dengan konfirmasi
- Timeline status order

---

### 👤 C. CUSTOMER PAGES

#### **1. Dashboard Customer**

![Dashboard Customer](https://github.com/user-attachments/assets/e44d55ad-f6c5-439b-89f3-2b40aa565433)

**Deskripsi:**
- Dashboard customer dengan welcome message
- Quick access menu:
  - Browse Catalog
  - My Cart
  - My Orders
  - My Profile
- Recent orders summary
- Recommended books (optional)

---

#### **2. Katalog Buku (Customer)**

![Katalog Buku](https://github.com/user-attachments/assets/fec54971-2a51-438e-95ba-999e96169ae2)

**Deskripsi:**
- Halaman browse katalog buku
- Grid/List view produk dengan:
  - Cover image
  - Judul
  - Penulis
  - Harga
  - Stock status
- Search bar untuk cari buku
- Filter kategori (Fiction, Non-fiction, Programming, etc)
- Sort by: Price, Title, Newest
- Tombol "Add to Cart" pada setiap produk
- Pagination

---

#### **3. Keranjang (Shopping Cart)**

![Keranjang](https://github.com/user-attachments/assets/0874ae59-4dc5-4100-96b7-1d5e46eaa74a)

**Deskripsi:**
- Shopping cart menampilkan list item yang akan dibeli
- Setiap item menampilkan:
  - Image produk
  - Judul buku
  - Harga satuan
  - Quantity selector (+ / -)
  - Subtotal
  - Tombol Remove
- Summary box:
  - Subtotal
  - Tax (optional)
  - Total Amount
- Button: Continue Shopping atau Checkout
- Cart kosong warning jika tidak ada item

---

#### **4. Checkout (Customer)**

**Deskripsi:**
- Form checkout untuk finalisasi pesanan
- Review items yang akan dibeli
- Input/verify shipping address:
  - Nama penerima
  - Alamat lengkap
  - Phone
- Payment method selection (optional)
- Order summary dengan total
- Button: Place Order atau Back to Cart
- Terms & conditions checkbox

---

#### **5. Pesanan Berhasil (Order Success)**

![Pesanan Berhasil](https://github.com/user-attachments/assets/ef701a96-a57f-476c-b6a3-29be7187ca74)

**Deskripsi:**
- Success page setelah checkout berhasil
- Konfirmasi pesanan dengan:
  - ✅ Success message
  - Order Number unik
  - Total pembayaran
  - Estimasi pengiriman
- Button: View Order Detail atau Continue Shopping
- Email confirmation (optional)

---

#### **6. Pesanan Saya (My Orders)**

![Pesanan Saya](https://github.com/user-attachments/assets/797f3daa-4a8a-4fd9-a87a-8ddd554d3b7b)

**Deskripsi:**
- Halaman order history customer
- List semua pesanan dengan:
  - Order Number
  - Date
  - Total Amount
  - Status (dengan color badge)
- Filter by status
- Search by order number
- Klik order untuk lihat detail
- Empty state jika belum ada order

---

#### **7. Detail Pesanan (Customer)**

![Detail Pesanan Customer](https://github.com/user-attachments/assets/5612dfc8-4025-4e91-a16c-5420395b5d81)

**Deskripsi:**
- Detail pesanan customer view
- Order information:
  - Order Number
  - Order Date
  - Status dengan progress bar/timeline
- Shipping address
- List items yang dipesan (judul, qty, harga per item)
- Payment summary:
  - Subtotal
  - Shipping (optional)
  - Total
- Status tracking dengan keterangan
- Button: Back to Orders atau Print (optional)

---

#### **8. Profile Saya (My Profile)**

![Profile Customer](https://github.com/user-attachments/assets/6a5aaba4-ef90-4449-a1b4-4a619458f143)

**Deskripsi:**
- Halaman profile customer
- View dan edit data pribadi:
  - Nama lengkap
  - Email (read-only)
  - Phone
  - Alamat
- Change password form
- Button: Update Profile atau Cancel
- Profile picture upload (optional)
- Account settings (optional)

---

### 📊 D. SUMMARY MOCKUP

Total **18 mockup screens** mencakup:

| Category | Jumlah | Screens |
|----------|--------|---------|
| **Public** | 3 screens | Dashboard, Login, Register |
| **Admin** | 7 screens | Dashboard, Kelola Buku (List/Create/Edit), Kelola User, Kelola Pesanan (List/Detail) |
| **Customer** | 8 screens | Dashboard, Katalog, Keranjang, Checkout, Success, Pesanan Saya (List/Detail), Profile |

---

### 🎯 E. MOCKUP FEATURES HIGHLIGHT

**✅ User Flow yang Jelas:**
```
Landing → Register → Login → Browse → Add to Cart → 
Checkout → Order Success → Track Order
```

**✅ Admin Flow yang Lengkap:**
```
Login → Dashboard → Manage Books/Orders/Users → 
Update Status → View Reports
```

**✅ Design Principles:**
- Responsive design consideration
- Consistent layout dan navigation
- Clear call-to-action buttons
- User-friendly interface
- Intuitive navigation flow
- Color-coded status (visual feedback)

---

### 🛠️ F. TOOLS USED FOR MOCKUP

- **Balsamiq Wireframes** - Low-fidelity wireframing
- **Figma** (optional) - High-fidelity design
- **Draw.io** - Flow diagrams

---

## 📌 KESIMPULAN

### Summary Project:

**1. Web Service & Configuration:**
- Video tutorial lengkap tersedia di YouTube
- Setup ASP.NET Core 9 + MongoDB
- Configuration dengan Dependency Injection
- Session management untuk authentication

**2. Nama Project:**
- **GrandLineBooks** dipilih karena:
  - Relevansi dengan kebutuhan pasar digital
  - Pembelajaran komprehensif full-stack development
  - Kompleksitas yang sesuai dengan real-world application
  - Menggunakan teknologi modern (.NET 9, MongoDB)

**3. Business Process:**
- **Customer Flow**: Register → Browse → Cart → Checkout → Track Order
- **Admin Flow**: Login → Manage Books/Orders/Users → Update Status
- Complete lifecycle management dari order creation hingga delivery

**4. Model Data:**
- MongoDB NoSQL dengan 3 collections utama:
  - **users**: Authentication & user data
  - **books**: Product catalog
  - **orders**: Transaction records
- Relationship: One-to-Many (users-orders), Many-to-Many (books-orders)
- Denormalization strategy untuk performance optimization

**5. Schema Team:**
- Tim terdiri dari **8 orang** dengan role spesifik:
  - 1 Project Manager
  - 2 Backend Developers
  - 2 Frontend Developers
  - 1 Database Administrator
  - 1 UI/UX Designer
  - 1 QA/Tester
  - 1 Documentation Specialist (bisa overlap)
- Timeline: **8 minggu** dengan 4 sprint
- Workflow terstruktur dengan daily standup & weekly review

**6. Mockup Project:**
- **18 mockup screens** lengkap untuk semua user journey
- Balsamiq wireframes untuk low-fidelity design
- User flow yang clear dan intuitive
- Responsive design consideration

---

### 🎯 Project Goals Achieved:

✅ **Comprehensive E-Commerce Platform** untuk toko buku online  
✅ **Multi-Role System** (Admin & Customer) dengan clear separation  
✅ **Complete Transaction Flow** dari browsing hingga delivery  
✅ **Modern Tech Stack** dengan ASP.NET Core 9 dan MongoDB  
✅ **Scalable Architecture** dengan MVC pattern dan clean code  
✅ **User-Friendly Interface** dengan responsive Bootstrap design  
✅ **Secure Authentication** dengan BCrypt password hashing  
✅ **Session Management** untuk cart dan login state  

---

### 📚 Pembelajaran yang Didapat:

1. **Backend Development**: CRUD operations, business logic, authentication
2. **Database Design**: NoSQL modeling, relationships, optimization
3. **Frontend Development**: Responsive UI, user experience design
4. **Full-Stack Integration**: Backend-Frontend connectivity
5. **Team Collaboration**: Agile workflow, version control dengan Git
6. **Project Management**: Timeline planning, task distribution

---

## 📄 LISENSI

Project ini dibuat untuk keperluan **UTS Pemrograman Visual** - Semester Ganjil 2024/2025

**© 2025 Alvin Alfandy - TI.23.A.5**

---

<div align="center">

**📧 Contact:** [alvinalfandy@student.ac.id](mailto:alvinalfandy@student.ac.id)

**🔗 Repository:** [GitHub - GrandLineBooks](https://github.com/yourusername/grandlinebooks)

---

**⭐ Jika dokumentasi ini membantu, jangan lupa berikan star! ⭐**

*Last Updated: November 2025*

</div>
