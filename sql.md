## SQL
**Update isi tabel dari tabel yang berbeda**

Ilustrasi:

Saya memiliki tabel pegawai yang sudah berisi ribuan data, salah satu field yang bernama alamat sebagian sudah ada yang terisi sebagian belum, suatu ketika saya punya data alamat yang lebih lengkap. Saya ingin mengupdate semua data alamat baik yang sudah terisi atau belum terisi dari tabel lain yang memiliki data alamat lebih lengkap.

```
UPDATE tb_pegawai pegawai  
SET pegawai.alamat = (  
SELECT alamat FROM coba  
WHERE pegawai.nip = coba.nip  
)  
WHERE pegawai.nip in (SELECT nip FROM coba)
```
atau bisa juga dengan perintah dibawah ini:
```
UPDATE tb_pegawai, coba SET tb_pegawai.alamat=coba.alamat 
WHERE tb_pegawai.nip=coba.nip;
```
