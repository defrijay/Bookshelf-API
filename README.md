# Bookshelf API

Bookshelf API adalah sebuah RESTful API sederhana untuk mengelola koleksi buku. Proyek ini dibuat sebagai bagian dari submission kelas **Belajar Membuat Aplikasi Back-End untuk Pemula** dari Dicoding.

## 📦 Fitur

- Menambahkan buku ke rak.
- Melihat daftar semua buku.
- Melihat detail buku berdasarkan ID.
- Mengubah informasi buku.
- Menghapus buku dari rak.
- Filter buku berdasarkan `name`, `reading`, dan `finished`.

## 🛠️ Teknologi

- [Node.js](https://nodejs.org/)
- [Hapi.js](https://hapi.dev/)
- [nanoid](https://github.com/ai/nanoid) untuk membuat ID unik.

## 🚀 Cara Menjalankan

1. Clone repository ini:
   ```bash
   git clone <repository-url>
   cd bookshelf-api

2. Install dependencies:
    ```bash
    npm install
    ```

3. Jalankan server:
    ```bash
    node server.js
    ```

4. Server akan berjalan di:
    ```bash
    http://localhost:9000
    ```

## 🔗 Endpoint
1. **Menambahkan Buku**
    
    Method: `POST`

    URL: `/books`

    Body:

    ```json
    {
        "name": "string (wajib)",
        "year": 2020,
        "author": "Penulis Buku",
        "summary": "Ringkasan Buku",
        "publisher": "Nama Penerbit",
        "pageCount": 100,
        "readPage": 25,
        "reading": true
    }
    ```
    
2. **Menampilkan Semua Buku**
    
    Method: `GET`

    URL: `/books`

    Query Parameters (opsional):

    - `name` → Filter berdasarkan nama buku (case-insensitive)

    - `reading` → `0` atau `1` (boolean)

    - `finished` → `0` atau `1` (boolean)

    Response:

    ```json
    {
        "status": "success",
        "data": {
            "books": [
                {
                    "id": "string",
                    "name": "Nama Buku",
                    "publisher": "Nama Penerbit"
                }
            ]
        }
    }
    ```

3. **Menampilkan Detail Buku**
    
    Method: `GET`

    URL: `/books/{bookId}`

    Response:

    ✅ 200 → Buku ditemukan

    ❌ 404 → Buku tidak ditemukan

4. **Mengubah Buku**
    
    Method: `PUT`

    URL: `/books/{bookId}`

    Body:

    ```json
    {
        "name": "string (wajib)",
        "year": 2021,
        "author": "Penulis Baru",
        "summary": "Ringkasan baru",
        "publisher": "Penerbit Baru",
        "pageCount": 150,
        "readPage": 150,
        "reading": false
    }
    ```

    Response:

    ✅ 200 → Buku berhasil diperbarui

    ❌ 400 → Gagal memperbarui buku. Mohon isi nama buku

    ❌ 400 → Gagal memperbarui buku. readPage tidak boleh lebih besar dari pageCount
    
    ❌ 404 → Gagal memperbarui buku. Id tidak ditemukan

5. **Menghapus Buku**
    
    Method: `DELETE`

    URL: `/books/{bookId}`

    Response:

    ✅ 200 → Buku berhasil dihapus

    ❌ 404 → Buku gagal dihapus. Id tidak ditemukan

## 📁 Struktur Folder
```bash
.
├── books.js         # Data sementara (in-memory)
├── handler.js       # Logika setiap endpoint
├── routes.js        # Daftar rute
└── server.js        # Konfigurasi dan inisialisasi server

```

## 🧑‍💻 Author

Submission oleh **Defrizal Yahdiyan Risyad** untuk Dicoding - Belajar Membuat Aplikasi Back-End untuk Pemula.