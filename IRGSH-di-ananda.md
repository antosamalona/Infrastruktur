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


