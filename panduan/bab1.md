## Bab-1
    Mendefinisikan Data dengan DML
    Create - Alter - Drop


- Membuat database "buku_db"
`CREATE DATABASE buku_db;`
<br><br>
- Mengaktifkan database "buku_db"
`USE buku_db;`
<br><br>
- Membuat tabel kategori
`CREATE TABLE kategori(
kategori_id int not null auto_increment,
kategori_nama varchar(25),
primary key(kategori_id)
);`
<br><br>
- Membuat tabel pengarang
`CREATE TABLE pengarang(
pengarang_id char(3) not null,
pengarang_nama varchar(30),
primary key(pengarang_id)
);`
<br><br>
- Membuat tabel penerbit
`CREATE TABLE penerbit(
penerbit_id char(4) not null,
penerbit_nama varchar(50),
primary key(penerbit_id)
);`
<br><br>
- Membuat tabel buku
`CREATE TABLE buku(
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
);`
<br><br>
- Membuat tabel 'link_buku_pengarang'
`CREATE TABLE link_buku_pengarang(
buku_isbn char(13) not null,
pengarang_id char(3) not null,
primary key(buku_isbn, pengarang_id),
foreign key(buku_isbn)
	references buku(buku_isbn),
foreign key(pengarang_id)
	references pengarang(pengarang_id)
);`
<br><br>
- Membuat tabel 'link_buku_kategori'
`CREATE TABLE link_buku_kategori(
buku_isbn char(13) not null,
kategori_id int not null,
primary key(buku_isbn, kategori_id),
foreign key(buku_isbn)
	references buku(buku_isbn),
foreign key(kategori_id)
	references kategori(kategori_id)
);`