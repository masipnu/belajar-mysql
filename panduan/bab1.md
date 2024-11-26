## Bab-1
### Mendefinisikan Data dengan DML
    Create - Alter - Drop
---

#### Membuat database "buku_db"
```sql
CREATE DATABASE buku_db;
```

#### Mengaktifkan database "buku_db"
```sql
USE buku_db;
```

#### Membuat tabel kategori
```sql
CREATE TABLE kategori(
kategori_id int not null auto_increment,
kategori_nama varchar(25),
primary key(kategori_id)
);
```

#### Membuat tabel pengarang
```sql
CREATE TABLE pengarang(
pengarang_id char(3) not null,
pengarang_nama varchar(30),
primary key(pengarang_id)
);
```

#### Membuat tabel penerbit
```sql
CREATE TABLE penerbit(
penerbit_id char(4) not null,
penerbit_nama varchar(50),
primary key(penerbit_id)
);
```

#### Membuat tabel buku
```sql
CREATE TABLE buku(
buku_isbn char(13) not null,
buku_judul varchar(75),
penerbit_id char(4),
buku_tglterbit date,
buku_jmlhalaman int,
buku_deskripsi text,
buku_harga decimal,
primary key(buku_isbn),
foreign key(penerbit_id)
	references penerbit(penerbit_id)
);
```

#### Membuat tabel 'link_buku_pengarang'
```sql
CREATE TABLE link_buku_pengarang(
buku_isbn char(13) not null,
pengarang_id char(3) not null,
primary key(buku_isbn, pengarang_id),
foreign key(buku_isbn)
	references buku(buku_isbn),
foreign key(pengarang_id)
	references pengarang(pengarang_id)
);
```

#### Membuat tabel 'link_buku_kategori'
```sql
CREATE TABLE link_buku_kategori(
buku_isbn char(13) not null,
kategori_id int not null,
primary key(buku_isbn, kategori_id),
foreign key(buku_isbn)
	references buku(buku_isbn),
foreign key(kategori_id)
	references kategori(kategori_id)
);
```

### Query Tambahan
#### Mengubah nama tabel
```sql
ALTER TABLE kategori RENAME TO kategori_buku;
```

#### Menambah kolom
```sql
ALTER TABLE buku ADD COLUMN buku_sinopsis text;
```

#### Mengubah Kolom
```sql
ALTER TABLE buku
	CHANGE buku_isbn buku_id char(15);
```

#### Menghapus kolom
```sql
ALTER TABLE buku DROP buku_sinopsis;
```

#### Menambah primary key
```sql
ALTER TABLE buku
	ADD primary key(buku_judul);
```

#### Menambah foreign key
```sql
ALTER TABLE link_buku_kategori
	ADD foreign key(buku_isbn)
	references buku(buku_isbn);
```

#### Menghapus primary key
```sql
ALTER TABLE buku DROP primary key;
```

#### Menghapus foreign key
```sql
ALTER TABLE fk_link_buku_kategori;
```

#### Menambah indeks
```sql
ALTER TABLE buku ADD INDEX idx_judul(buku_judul);
```

#### Menghapus indeks
```sql
ALTER TABLe buku DROP INDEX idx_judul;
```

#### Menghapus Tabel
```sql
DROP TABLE IF EXIST link_buku_kategori;
DROP TABLE link_buku_kategori, link_buku_pengarang;
```