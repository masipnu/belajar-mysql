
### Bab-4
### Seleksi Data - Bagian 1
---

#### Perintah SELECT
- Menampilkan seluruh kolom dan data dalam tabel
```sql
SELECT * FROM buku;
```

- Menampilkan beberapa kolom dari tabel buku
```sql
SELECT 	buku_isbn,
		buku_judul,
		penerbit_id,
		buku_tglterbit,
		buku_jmlhalaman,
		buku_deskripsi,
		buku_harga
FROM
	buku;
```

- Menampilkan beberapa kolom dari tabel buku dan memberi alias
```sql
SELECT 	buku_isbn ISBN,
		buku_judul JUDUL,
		penerbit_id PENERBIT,
		buku_tglterbit TERBIT,
		buku_jmlhalaman HALAMAN,
		buku_deskripsi DESKRIPSI,
		buku_harga HARGA
FROM
	buku;
```

- Menampilkan seluruh data dari beberapa kolom
```sql
SELECT buku_harga, buku_judul FROM buku;
```

- Menampilkan seluruh data dari beberapa kolom dan memberi alias
```sql
SELECT buku_harga HARGA, buku_judul JUDUL FROM buku;
```

- Menyertakan nama database dan tabel dalam perintah SELECT
```sql
SELECT
	buku.buku_isbn,
	buku.buku_judul,
	buku.buku_harga
FROM
	buku_db.buku;
```

- Menggunakan Alias tabel
```sql
SELECT
	a.buku_isbn,
	a.buku_judul,
	a.buku_harga
FROM
	buku a;
```

- Menggunakan Alias pada nama kolom
```sql
SELECT
	buku_isbn as 'ISBN',
	buku_judul as 'JUDUL BUKU',
	buku_harga as 'HARGA'
FROM
	buku;
```


#### Menyaring Data
Data yang ditampilkan dapat disaring (filter) berdasarkan kebutuhan informasi yang akan disajikan. Untuk menyaring data, perlu didefinisikan kondisi yang akan dijadikans ebagai kriteria penyaringan. Dalam perintah **SELECT** ditambah klausa **WHERE** setelahnya.

- Contoh 1
Menampilkan data buku yang harganya kurang dari Rp. 45.000
```sql
SELECT
	buku_isbn as 'ISBN',
	buku_judul as 'JUDUL BUKU',
	buku_harga as 'HARGA'
FROM
	buku
WHERE
	buku_harga < 45000;
```

- Menampilkan data buku yang harganya kurang dari Rp. 45.000 dan ISBN diawali oleh angka 777
```sql
SELECT
	buku_isbn as 'ISBN',
	buku_judul as 'JUDUL BUKU',
	buku_harga as 'HARGA'
FROM
	buku
WHERE
	(buku_harga < 45000) AND
	(buku_isbn LIKE '777%');
```

Menampilkan data dengan rentang tertentu Menggunakan klausa BETWEEN

- Contoh BETWEEN 1
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
WHERE
	buku_harga BETWEEN 50000 AND 60000;
```

- Contoh BETWEEN 2
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
WHERE
	(buku_harga >= 50000) AND
	(buku_harga <= 60000);
```

#### Klausa LIMIT
LIMIT digunakan untuk membatasi data yang disajikan sesuai batas limit yang ditentukan terurut dari atas.

- Contoh LIMIT 1
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
LIMIT 5;
```

LIMIT juga bisa membatasi data yang dimulai dari baris tertentu.
- Contoh LIMIT 2
Membatasi 10 data dimulai dari urutan ke-6
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
LIMIT 5,10;
```

#### Klausa DISTINCT
Klausa ini berfungsi untuk menghilangkan data yang dobel saat disajikan.

- Contoh sebelum diberi DISTINCT
```sql
SELECT penerbit_id FROM buku;
```

- Setelah diberi klausa DISTINCT
```sql
SELECT DISTINCT penerbit_id FROM buku;
```

#### Mengurutkan Data
Secara default data yang disajikan menggunakan printah SELECT akan ditmpilkan sesuai urutan data dimasukkan, kecuali pada kolom yang diatur sebagai primary key, maka dia akan urut sesui bilangan. Untuk mengurutkan data sesuai kolom tertentu kita bisa menggunakan klausa ORDER BY.

**Contoh Penggunaan ORDER BY**
- Mengurutkan datan sesuai kolom 'buku_judul'
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
ORDER BY
	buku_judul;
```

- Pengurutan data dari terkecil ke terbesar (Ascending)
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
ORDER BY
	buku_judul ASC;
```

- Pengurutan data dari terbesar ke terkecil (Descending)
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
ORDER BY
	buku_judul DESC;
```