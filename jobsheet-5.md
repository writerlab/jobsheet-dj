# Jobsheet 5
## Membuat Models

Buat models ```Pengguna```, ```Pengaduan``` dan ```Tanggapan```.
Buka file ```app_pengaduan/models.py```.
```python
...
from django.contrib.auth.models import User

class Pengguna(models.Model):
  pilih_level = (
    ('admin', 'admin'),
    ('petugas', 'petugas'),
    ('masyarakat', 'masyarakat'),
  )

  nik      = models.CharField(max_length=16)
  nama     = models.CharField(max_length=35)
  username = models.ForeignKey(User, on_delete=models.CASCADE)
  telp     = models.CharField(max_length=13)
  level    = models.CharField(max_length=8, choices=pilih_level)

  def __str__(self):
    return self.nama


class Pengaduan(models.Model):
  pilih_status = (
    ('pending', 'pending'),
    ('proses', 'proses'),
    ('selesai', 'selesai'),
  )

  tanggal     = models.DateField(auto_now=True)
  nik         = models.ForeignKey(Pengguna, on_delete=models.CASCADE)
  judul       = models.CharField(max_length=100)
  isi_laporan = models.TextField()
  foto        = models.ImageField(max_length=13)
  status      = models.CharField(max_length=8, choices=pilih_status)

  def __str__(self):
    return self.judul


class Tanggapan(models.Model):
  pilih_status = (
    ('pending', 'pending'),
    ('proses', 'proses'),
    ('selesai', 'selesai'),
  )

  pengaduan   = models.ForeignKey(Pengaduan, on_delete=models.CASCADE)
  tanggal     = models.DateField(auto_now=True)
  tanggapan   = models.TextField()
  petugas     = models.ForeignKey(Pengguna, on_delete=models.CASCADE)

  def __str__(self):
    return self.pengaduan.judul
```

Buat migrasi untuk models diatas.
Buka cmd.
```python
python manage.py makemigrations
```

```python
python manage.py migrate
```

## Daftarkan Models ke Dj.Admin
Tes models yang dibuat. 
Buka file ```app_pengaduan/admin.py```.
```python
...
from app_pengaduan.models import *

admin.site.register(Pengguna)
admin.site.register(Pengaduan)
admin.site.register(Tanggapan)
```

## Buat Super User
Buat Super User untuk login ke Django Admin.
```python
python manage.py createsuperuser
username: admin
email: admin@pengaduan.id
password: adm12345
password (again): adm12345
```

Coba jalankan server.
```python
python manage.py runserver
```

Buka [http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin)
Masukkan Username dan Password yang telah dibuat sebelumnya.



