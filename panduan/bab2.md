### Bab-2
### Manipulasi Data Dengan DML
    INSERT, UPDATE, DELETE
---

#### Memasukkan data tabel 'kategori'
```sql
INSERT INTO kategori (kategori_nama) VALUES
('Database'),
('Desain Grafis'),
('Jaringan Komputer'),
('Pemrograman'),
('Web dan Internet'),
('Office Application');
```

#### Memasukkan data tabel 'pengarang'
```sql
INSERT INTO pengarang VALUES
('P01','Andi Setiawan'),
('P02','Rudi Wicaksono'),
('P03','Beni Tito'),
('P04','Prasetya'),
('P05','Erik Rusdianto'),
('P06','Rosdiana'),
('P07','Fredi Hidayat'),
('P08','Hasanudin'),
('P09','Ahmad hanafi'),
('P10','Iwan Gunardi'),
('P11','Iman Teguh'),
('P12','Abdul Ghozali'),
('P13','Tegar Sanjaya');
```

#### Memasukkan data tabel 'penerbit'
```sql
INSERT INTO penerbit VALUES
('PB01','Angkasa Raya'),
('PB02','Cahaya Ilmu Persada'),
('PB03','Sinar Ilmu Perkasa'),
('PB04','Intan'),
('PB05','Sinar Raya'),
('PB06','Informatika'),
('PB07','Tiga Sekawan'),
('PB08','Cipta Ilmu');
```

#### Memasukkan data tabel 'buku'
```sql
INSERT INTO buku VALUES
('222-34222-1-0','Belajar Photoshop','PB01','2019/07/02',300,NULL,42000),
('222-34222-1-1','Panduan CorelDRAW','PB02','2020/03/15',400,NULL,55000),
('979-96446-9-0','Belajar SQL','PB06','2019/10/12',346,NULL,45000),
('979-96446-9-1','Panduan Basis Data','PB01','2017/03/02',257,NULL,37000),
('979-96446-9-2','Perancangan Sistem','PB03','2013/09/20',403,NULL,37000),
('979-96446-9-3','Microsoft Access','PB06','2015/07/13',400,NULL,48500),
('888-96771-3-0','Pemrograman Pascal','PB08','2014/11/01',350,NULL,50000),
('888-96771-3-1','Pemrograman Java','PB06','2017/01/23',450,NULL,72000),
('888-96771-3-2','Pemrograman C untuk Hardware','PB05','2016/12/25',398,NULL,47000),
('888-96771-3-3','Panduan C++','PB06','2015/07/15',490,NULL,65000),
('888-96771-3-4','Belajar Delphi','PB05','2018/08/11',328,NULL,50000),
('888-96771-3-5','Visual Basic','PB02','2017/10/14',250,NULL,50000),
('666-96771-2-0','Panduan Membangun Jaringan TCP/IP','PB08','2016/08/02',200,NULL,60000),
('666-96771-2-1','Implementasi TCP/IP di Linux','PB08','2018/11/21',230,NULL,350000),
('777-76723-5-0','Belajar PHP 8','PB07','2020/05/02',600,NULL,95000),
('777-76723-5-1','Aplikasi Web dengan Python','PB07','2014/08/01',180,NULL,30000),
('777-76723-5-2','Internet Marketing','PB07','2017/01/24',150,NULL,38500),
('777-76723-5-3','Panduan Menjadi Youtuber','PB07','2017/01/24','243',NULL,38500),
('999-11555-2-0','Microsoft Power Point','PB06','2018/11/23',300,NULL,57500),
('999-11555-2-1','Microsoft Word','PB04','2017/12/01',270,NULL,60000);
```

#### Memasukkan data tabel 'link_buku_pengarang'
```sql
INSERT INTO link_buku_pengarang VALUES
('222-34222-1-0','P01'),
('222-34222-1-1','P04'),
('666-96771-2-0','P04'),
('666-96771-2-0','P07'),
('666-96771-2-0','P06'),
('666-96771-2-1','P04'),
('666-96771-2-1','P01'),
('777-76723-5-0','P02'),
('777-76723-5-0','P04'),
('777-76723-5-1','P03'),
('777-76723-5-1','P12'),
('777-76723-5-1','P10'),
('777-76723-5-2','P13'),
('777-76723-5-3','P08'),
('777-76723-5-3','P09'),
('888-96771-3-0','P04'),
('888-96771-3-1','P02'),
('888-96771-3-1','P11'),
('888-96771-3-2','P01'),
('888-96771-3-2','P06'),
('888-96771-3-3','P02'),
('888-96771-3-4','P10'),
('888-96771-3-4','P09'),
('888-96771-3-5','P02'),
('979-96446-9-0','P11'),
('979-96446-9-0','P02'),
('979-96446-9-1','P07'),
('979-96446-9-2','P13'),
('979-96446-9-2','P10'),
('979-96446-9-2','P12'),
('979-96446-9-2','P03'),
('979-96446-9-3','P11'),
('999-11555-2-0','P11'),
('999-11555-2-0','P13'),
('999-11555-2-1','P08'),
('999-11555-2-1','P09'),
('999-11555-2-1','P10'),
('999-11555-2-1','P06');
```

#### Memasukkan data tabel 'link_buku_kategori'
```sql
INSERT INTO link_buku_kategori VALUES
('222-34222-1-0',2),
('222-34222-1-1',2),
('979-96446-9-0',1),
('979-96446-9-1',1),
('979-96446-9-2',1),
('979-96446-9-2',4),
('979-96446-9-3',1),
('888-96771-3-0',4),
('888-96771-3-1',4),
('888-96771-3-2',4),
('888-96771-3-3',4),
('888-96771-3-4',4),
('888-96771-3-5',4),
('666-96771-2-0',3),
('666-96771-2-1',3),
('777-76723-5-0',4),
('777-76723-5-0',5),
('777-76723-5-1',4),
('777-76723-5-1',5),
('777-76723-5-2',5),
('777-76723-5-3',5),
('999-11555-2-0',6),
('999-11555-2-1',6);
```

### Query Tambahan


#### Mengubah data di dalam tabel penerbit
```sql
UPDATE penerbit
	SET penerbit_nama = 'Informatika Bandung'
WHERE
	penerbit_id = 'PB06';
```

#### Mengubah data di dalam tabel buku
```sql
UPDATE buku
	SET buku_judul = 'Tuntunan Praktis Menggunakan Microsoft Word 2010',
		penerbit_id = 'PB02'
WHERE
	buku_isbn = '999-11555-2-1';
```

#### Menghapus satu row data dalam tabel
```sql
DELETE FROM buku
WHERE buku_isbn = '888-96771-3-5';
```

#### Menghapus seluruh row data dalam tabel
```sql
DELETE FROM buku;
```

#### Menghapus tabel beserta isinya, lalu mere-build ulang tabel tanpa data
```sql
TRUNCATE table buku;
```