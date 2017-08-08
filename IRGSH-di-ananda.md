# Sertifikat

Sertifikat-sertifikat untuk keperluan irgsh terletak di `/cert/`.

# Cara menyalakan irgsh di ananda :

## irgsh-web

### web

Masuk sebagai user irgsh, pindah ke `/home/irgsh/irgsh-web/`, lalu :

```
$ python manage.py runfcgi method=prefork host=0.0.0.0 port=8001
```

### taskinit

Masuk sebagai user irgsh, pindah ke `/home/irgsh/irgsh-web/`, bikin screen baru, lalu :

```
$ python manage.py celeryd -n taskinit -l DEBUG
```

## irgsh-node

Masuk sebagai user builder, pindah ke `/home/builder/irgsh-node`, bikin screen baru, lalu :

```
$ ./bin/irgsh-node -l DEBUG
```

Untuk uploader, bikin screen baru, lalu :

```
$ ./bin/irgsh-uploader -l DEBUG
```

## irgsh-repo
Masuk sebagai user irgsh-repo, pindah ke `/home/irgsh-repo/irgsh-repo`, bikin screen baru, lalu :

```
$ sudo ./bin/irgsh-repo -l DEBUG
```


## Sidik gangguan

### Kode sumber tidak dapat diunduh

Galatnya seperti berikut

```
[2017-08-07 06:59:41,400: WARNING/PoolWorker-7] [Errno 13] Permission denied: '/run/irgsh-logs'
```
dan 
```
Specification initialization failed: 'NoneType' object has no attribute 'write'
```

Dikarenakan direktori `/run/irgsh-logs` tidak ada. Setelah dibuat lalu mesin dimulai-ulang, direktori ini akan hilang dan perlu dibuat lagi. Jalan lupa permission baca tulisnya disetel juga.

### Galat memori'Memory exeption'

Jika terjadi galat memori akan tampil pesan ```<type> memory exeption ``` solusinya adalah dengan menambah kapasitas memori di mesin.
