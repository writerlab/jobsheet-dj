# Jobsheet 3
## Membuat Apps
masuk ke folder projek ```Desktop/pengaduan/```
```python
cd Desktop/pengaduan
```

buat apps: ```app_pengaduan```
```python
django-admin startapp app_pengaduan
```

buka projek dengan teks editor
```python
code .
```

daftarkan apps yang sudah dibuat di ```pengaduan/settings.py```
```python
...
INSTALLED_APPS = [
  ...
  'app_pengaduan',
]
```