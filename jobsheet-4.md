# Jobsheet 4
## Templates Bagian 1

Atur direktori default Template. Buka file ```pengaduan/settings.py```.
Tambahkan ```'templates'``` kedalam list ```DIRS```.
```python
...
TEMPLATES = [
        ...
        'DIRS': ['templates'],
        ...
]
...
```

Buat folder ```templates/``` di root folder.
Didalam folder templates inilah dokumen-dokumen HTML disimpan.
```python
-pengaduan/
  |- app_pengaduan/
  |- pengaduan/
  |- templates/ # folder templates harus satu level dengan yang lain
  |- manage.py
```

Buat file ```registrasi.html``` difolder ```templates/```. Contoh isinya seperti berikut.
```html
<!DOCTYPE html>
<html lang="id">
<head>
  <title>APLIKASI PELAPORAN PENGADUAN MASYARAKAT</title>
</head>
<body>
  
  <h1>REGISTRASI...</h1>

</body>
</html>
```

Buat Views ```registrasi()``` di file ```app_pengaduan/views.py``` agar me-render dokumen HTML. Persis seperti berikut.
```python
from django.shortcuts import render

def registrasi(request):
  template = "registrasi.html"
  return render(request, template)
```


Buat URL baru untuk mengakses halaman registrasi.
Buka file ```pengaduan/urls.py```.
```python
...
from app_pengaduan.views import registrasi

urlpatterns = [
  ...
  path('registrasi/', registrasi),
]
```

Jangan lupa *save* dan jalankan *server*-nya.
```python
python manage.py runserver
```

Buka [http://127.0.0.1:8000/registrasi](http://127.0.0.1:8000/registrasi).
