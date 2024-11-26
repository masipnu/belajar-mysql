### Bab-3
### Kontrol Hak Akses & Transaksi Data
    TCL : Grant, Revoke, Commit, Rollback
---

- Memberikan seluruh jenis akses pada 1 database
```sql
GRANT ALL
on buku_db.*
TO 'adi'@'localhost'
IDENTIFIED BY 's3cr3t';
```

- Menampilkan hak akses yang dimiliki oleh satu user
```sql
SHOW GRANTS FOR 'adi'@'localhost';
```

- Mencabut seluruh jenis akses pada 1 user
```sql
REVOKE ALL on buku_db.* FROM adi;
```

- Menonaktifkan fungsi COMMIT
```sql
SET AUTOCOMMIT=0;
```

- Mengaktifkan fungsi COMMIT
```sql
SET AUTOCOMMIT=1;
```

- Menggunakan ROLLBACK
Untuk menggunakan fungsi ROLLBACK, AUTOCOMMIT harus diset OFF terlebih dahulu
```sql
SET AUTOCOMMIT=0;
```
```sql
CREATE TABLE test(
kode integer not null primary key,
keterangan varchar(50)
);
```

```sql
INSERT INTO test VALUES
(1,'Baris Pertama'),
(2,'Baris Ke dua'),
(3,'Baris ke tiga');
```

```sql
COMMIT;
```

```sql
INSERT INTO test VALUES
(4,'Baris ke empat'),
(5,'Baris ke lima'),
(6,'Baris ke enam');
```

```sql
ROLLBACK;
```