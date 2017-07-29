### Memperbarui daftar paket di dalam chroot

```
# sudo pbuilder update
```

### Login ke dalam base.tgz

```
# sudo pbuilder login
```

### LOgin ke dalam base.tgz, kemudian simpan saat logout

```
# sudo pbuilder login --save-after-login
```

### LOgin ke dalam base.tgz spesifik, kemudian simpan saat logout

```
# sudo pbuilder login --save-after-login --basetgz /path/to/base.tgz
```
