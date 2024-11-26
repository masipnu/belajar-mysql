
### Bab-5
### Seleksi Data - Bagian 2
---

#### Pengelompokan Data menggunakan GROUP BY

Penggunaan kalusa GROUP BY disertakan dalam perintah SELECT
- Contoh 1
```sql
SELECT
	penerbit_id,
	COUNT(*)
FROM
	buku
GROUP BY
	penerbit_id;
```
Jumlah buku yang ditampilkan dari hasil kode di atas adalah hasil dari proses pengelompokan brdasarkan penerbit (dalam hal ini kolom penerbit_id).

- Contoh 2
```sql
SELECT
	a.penerbit_id as 'Kode Penerbit',
	b.penerbit_nama as 'Nama Penerbit',
	COUNT(a.penerbit_id) as 'Jumlah Buku'
FROM
	buku a,
	penerbit b
WHERE
	a.penerbit_id = b.penerbit_id
GROUP BY
	a.penerbit_id,
	b.penerbit_nama;
```
Pada kode di atas ditambahkan kolom penerbit_nama agar lebih jelas.

- Contoh 3
```sql
SELECT
	a.pengarang_id as 'ID Pengarang',
	a.pengarang_nama as 'Nama Pengarang',
	GROUP_CONCAT(b.buku_judul) as 'Daftar Judul Buku'
FROM
	pengarang a,
	buku b,
	link_buku_pengarang c
WHERE
	a.pengarang_id = c.pengarang_id AND
	b.buku_isbn = c.buku_isbn
GROUP BY
	a.pengarang_id,
	a.pengarang_nama;
```
Kode terebut akan menampilkan daftar judul buku yagn dikelompokkan berdasarkan pengarang.

GROUP CONCAT() adalah fungsi agregasi yagn berguna untuk mengelompokkan baris data
menjadi satu teks (string) tunggal.

#### Menggabungkan Data

Proses menggabungkan 2 query select menjadi 1 dengan perintah UNION dengan syarat masing-masing query select menghasilkan jumlah row data yang sama.

- Query 1
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
WHERE
	buku_harga <= 40000;
```
Kode di atas akan menghasilkan 6 row data.


- Query 2
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
WHERE buku_harga >= 50000;
```
Kode tersebut menghasilkan 10 row data.


- Query 3 : Penggabungan Query menggunakan UNION
```sql
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
WHERE
	buku_harga <= 40000
UNION
SELECT
	buku_isbn,
	buku_judul,
	buku_harga
FROM
	buku
WHERE buku_harga >= 50000;
```

#### Join : Seleksi Data dari 2 Tabel atau Lebih
Seleksi data dari 2 tabel atau lebih, lebih rumit dibandingkan seleksi data dari 1 tabel. Syarat utamanya adalah adanya kolom relasi. Kolom relasi adalah kolom yang digunakan sebagai kunci untuk menghubungkan antara tabel yang satu dengan tabel yang lain.

- Contoh 1
Seleksi data dari 2 tabel (sederhana)
```sql
SELECT
	a.buku_isbn,
	a.buku_judul,
	b.penerbit_nama
FROM
	buku a,
	penerbit b
WHERE
	a.penerbit_id = b.penerbit_id;
```
Tampilkan data dari kolom buku_isbn dan buku_judul pada tabel buku
dengan nama alias a, serta kolom penerbit nama pada tabel penerbit
dengan nama alias b yang nilai penerbit_id nya sama.

- Contoh 2
Seleksi data yang melibatkan 4 tabel
```sql
SELECT
	a.buku_isbn,
	a.buku_judul,
	b.penerbit_nama,
	GROUP_CONCAT(d.pengarang_nama)
FROM
	buku a,
	penerbit b,
	link_buku_pengarang c,
	pengarang d
WHERE
	a.penerbit_id = b.penerbit_id AND
	a.buku_isbn = c.buku_isbn AND
	c.pengarang_id = d.pengarang_id
GROUP BY
	a.buku_isbn,
	a.buku_judul,
	b.penerbit_nama;
```
- Contoh 3
Seleksi data Tambahan
```sql
SELECT
	a.buku_isbn,
	a.buku_judul,
	b.penerbit_nama,
	GROUP_CONCAT(d.kategori_nama)
FROM
	buku a,
	penerbit b,
	link_buku_kategori c,
	kategori d
WHERE
	a.penerbit_id = b.penerbit_id AND
	a.buku_isbn = c.buku_isbn AND
	c.kategori_id = d.kategori_id
GROUP BY
	a.buku_isbn,
	a.buku_judul,
	b.penerbit_nama;
```
#### Pengurangan dan Interseksi Data
Hal ini dilakukan untuk menyeleksi sekelompok data dari satu tabel lalu dikurangi dengan sekelompok data dari tabel lain.

- Contoh 1 : Menggunakan INNER JOIN
1. Masukkan data dulu ke tabel penerbit
```sql
INSERT INTO penerbit
VALUES ('PB09', 'MODULA');
```

2. Lihat data penerbit_id pada tabel penerbit
```sql
SELECT
	a.penerbit_id
FROM
	penerbit a;
```

3. Lihat data penerbit_id pada tabel buku ditambah klausa DISTINCT
```sql
SELECT DISTINCT
	b.penerbit_id
FROM
	buku b;
```

3. Lakukan interseksi data dengan query berikut
```sql
SELECT DISTINCT
	a.penerbit_id
FROM
	penerbit a
INNER JOIN
	buku b
USING
	(penerbit_id);
```
Hasil yang muncul merupakan irisan dari data query pertama dan query ke dua.


- Contoh 2 : Menggunakan MINUS / NOT IN
1. Lihat data penerbit_id pada tabel penerbit
```sql
SELECT
	a.penerbit_id
FROM
	penerbit a;
```

2. Lihat data penerbit_id dari tabel buku, gunakan  klausa DISTINCT
```sql
SELECT DISTINCT
	b.penerbit_id
FROM
	buku b;
```

3. Lakukan pengurangan data query 1 dengan query 2
```sql
SELECT DISTINCT
	a.penerbit_id
FROM
	penerbit a
WHERE
	(a.penerbit_id) NOT IN
	(SELECT b.penerbit_id FROM buku b);
```
Hasilnya adalah data penerbit_id pada tabel penerbit yang tidak ada pada data penerbit_id tabel buku.

#### Sub-query
Subquery adalah perintah SELECT yang terdapat dalam perintah SELECT lain. Hal ini memudahkan kita untuk membuat berbagai format laporan semisal crosstab query.


- Contoh 1
Membuat query yang dapat menampilkan jumlah buku yang diterbitkan oleh masing-masing penerbit. kita akan menggunakan tabel buku dan tabel penerbit.
```sql
SELECT
	a.penerbit_id,
	a.penerbit_nama,
	(SELECT
		COUNT(*)
	FROM
		buku
	WHERE
		penerbit_id = a.penerbit_id)
	as 'Jumlah Buku'
FROM
	penerbit a;
```
Pada contoh tersebut perintah SELECT bagian luar digunakan untuk menyeleksi data dari tabel penerbit, sedangkan bagian dalam digunakan untuk menyeleksi data dari tabel buku.

Subquery juga biasa digunakan sebagai kolom penentu kondisi query (di bagian WHERE).

- Contoh 2 : Subquery sebagai penentu bagian WHERE
```sql
SELECT
	penerbit_id,
	penerbit_nama
FROM
	penerbit
WHERE
	penerbit_id NOT IN
	(SELECT
		penerbit_id
	FROM
		buku);
```
Perintah di atas digunakan untuk menampilkan data pada tabel 'penerbit' (kolom 'penerbit_id' dan 'penerbit_nama') yang datanya tidak terdapat pada tabel buku.