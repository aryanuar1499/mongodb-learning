# MongoDB Fundamentals

Dokumentasi pembelajaran **MongoDB Fundamentals** sebagai bagian dari roadmap MongoDB Developer.

Pada tahap ini, pembelajaran berfokus pada pemahaman dasar MongoDB sebagai **NoSQL Document Database**, struktur data MongoDB, serta praktik dasar menggunakan MongoDB secara lokal melalui `mongosh`.

---

## 1. Learning Objectives

Pada tahap Fundamentals, tujuan pembelajaran adalah memahami:

* Konsep dasar MongoDB.
* MongoDB sebagai **Document Database**.
* Struktur **Database → Collection → Document → Field → Value**.
* Perbedaan MongoDB dengan relational database seperti PostgreSQL.
* Konsep `_id` dan `ObjectId`.
* Perbedaan `_id` dengan field `id` yang dibuat sendiri.
* Struktur document sederhana dan nested document.
* Cara berinteraksi dengan database dan collection menggunakan `mongosh`.

---

## 2. MongoDB as a Document Database

MongoDB merupakan database **NoSQL** yang menggunakan pendekatan **document-oriented**.

Data disimpan dalam bentuk document yang memiliki struktur seperti JSON, tetapi MongoDB menggunakan format penyimpanan **BSON (Binary JSON)**.

Contoh document:

```javascript
{
  id: 1001,
  nama: "Laptop ASUS",
  harga: 8500000,
  stok: 10
}
```

Berbeda dengan relational database yang menggunakan tabel dan baris, MongoDB mengorganisasi data menggunakan **collection** dan **document**.

---

## 3. MongoDB Data Structure

Struktur dasar yang dipelajari:

```text
Database
└── Collection
    └── Document
        └── Field : Value
```

Dalam latihan:

```text
toko_latihan
└── produk
    └── Document
        ├── _id
        ├── id
        ├── nama
        ├── harga
        └── stok
```

### Database

Database digunakan sebagai tempat utama untuk menyimpan dan mengorganisasi data.

Database yang digunakan dalam pembelajaran:

```text
toko_latihan
```

### Collection

Collection merupakan kumpulan document.

Collection yang digunakan:

```text
produk
```

### Document

Document merupakan satu unit data dalam MongoDB.

Contoh:

```javascript
{
  id: 1001,
  nama: "Laptop ASUS",
  harga: 8500000,
  stok: 10
}
```

### Field dan Value

Document terdiri dari pasangan **field dan value**.

Contoh:

```javascript
nama: "Laptop ASUS"
harga: 8500000
stok: 10
```

`nama`, `harga`, dan `stok` merupakan field, sedangkan nilai yang berada setelahnya merupakan value.

---

## 4. `_id` vs `id`

Salah satu konsep penting yang dipelajari adalah perbedaan antara `_id` dan `id`.

Ketika document dimasukkan ke MongoDB tanpa memberikan `_id`, MongoDB akan membuat `_id` secara otomatis.

Contoh hasil document:

```javascript
{
  _id: ObjectId("..."),
  id: 1001,
  nama: "Laptop ASUS",
  harga: 8500000,
  stok: 10
}
```

### `_id`

`_id` merupakan identifier khusus pada document MongoDB dan digunakan untuk mengidentifikasi document secara unik.

MongoDB secara otomatis dapat membuat `_id` dengan tipe **ObjectId**.

### `id`

Berbeda dengan `_id`, field `id` merupakan field biasa yang dibuat sendiri.

Dalam latihan digunakan:

```javascript
id: 1001
```

Sehingga:

```text
_id → identifier MongoDB
id  → field yang dibuat untuk kebutuhan data/aplikasi
```

Memahami perbedaan ini menjadi salah satu checkpoint penting pada tahap Fundamentals.

---

## 5. Nested Document

MongoDB juga memungkinkan data disimpan dalam struktur bertingkat.

Contoh nested document yang dipelajari:

```javascript
{
  nama: "Yanuar",
  alamat: {
    kota: "Tuban",
    kode_pos: "623xx"
  }
}
```

Pada contoh tersebut, `alamat` merupakan field yang memiliki document lain di dalamnya.

Konsep ini menjadi salah satu karakteristik penting dari document model MongoDB.

---

## 6. Basic MongoDB Practice

Pembelajaran dilakukan menggunakan MongoDB secara lokal melalui `mongosh`.

Database latihan:

```text
toko_latihan
```

Collection:

```text
produk
```

Salah satu document yang digunakan dalam latihan:

```javascript
db.produk.insertOne({
  id: 1001,
  nama: "Laptop ASUS",
  harga: 8500000,
  stok: 10
})
```

Document kemudian dapat dilihat menggunakan:

```javascript
db.produk.find()
```

Hasilnya menunjukkan bahwa MongoDB menambahkan `_id` secara otomatis:

```javascript
{
  _id: ObjectId("..."),
  id: 1001,
  nama: "Laptop ASUS",
  harga: 8500000,
  stok: 10
}
```

Database dan collection juga diamati melalui MongoDB Compass untuk membantu memahami hubungan antara database, collection, dan document secara visual.

---

## 7. Basic Database & Collection Commands

Beberapa command dasar yang dipelajari:

### Memilih database

```javascript
use toko_latihan
```

### Melihat database

```javascript
show dbs
```

### Mengetahui database yang sedang digunakan

```javascript
db
```

### Melihat collection

```javascript
show collections
```

Contoh struktur yang digunakan:

```text
MongoDB
└── toko_latihan
    └── produk
```

---

## 8. MongoDB and PostgreSQL

Pembelajaran MongoDB dilakukan secara paralel dengan PostgreSQL sehingga konsep keduanya digunakan sebagai pembanding.

| PostgreSQL       | MongoDB        |
| ---------------- | -------------- |
| Database         | Database       |
| Table            | Collection     |
| Row              | Document       |
| Column           | Field          |
| Primary Key      | `_id`          |
| Relational Model | Document Model |

Perbandingan ini membantu memahami bahwa MongoDB bukan sekadar relational database dengan syntax yang berbeda, tetapi menggunakan **model data yang berbeda**.

---

## 9. Key Understanding

Dari tahap Fundamentals, konsep utama yang dipahami adalah:

```text
Database
    ↓
Collection
    ↓
Document
    ↓
Field
    ↓
Value
```

Contoh implementasinya:

```text
toko_latihan
    ↓
produk
    ↓
{
    _id: ObjectId(...),
    id: 1001,
    nama: "Laptop ASUS",
    harga: 8500000,
    stok: 10
}
```

Dengan memahami struktur tersebut, document MongoDB tidak lagi dilihat hanya sebagai objek `{ ... }`, tetapi sebagai bagian dari struktur database yang lebih besar.

---

## 10. Key Takeaways

* MongoDB adalah **NoSQL Document Database**.
* MongoDB menyimpan data dalam bentuk **document**.
* Document dikumpulkan dalam **collection**.
* Collection berada di dalam **database**.
* Document terdiri dari **field dan value**.
* MongoDB menggunakan **BSON** sebagai format data.
* `_id` merupakan identifier khusus pada setiap document.
* `ObjectId` dapat digunakan sebagai nilai `_id`.
* `id` dan `_id` merupakan dua hal yang berbeda.
* MongoDB mendukung struktur **nested document**.
* MongoDB dapat digunakan dan dipelajari melalui `mongosh` serta MongoDB Compass.
* Pemahaman struktur document menjadi fondasi sebelum mempelajari operasi MongoDB yang lebih lanjut.

---

## 11. Learning Progress

**Status: Completed**

Fundamentals telah selesai dipelajari dan dipraktikkan sebagai dasar untuk melanjutkan ke tahap berikutnya dalam roadmap MongoDB Developer.

### Next Topic

**CRUD — Create, Read, Update, Delete**
