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

```
sudo mkdir -p /run/irgsh-logs && sudo chmod a+rw /run/irgsh-logs
```


### X not installed

```
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: amd64
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder and should
Depends: cdbs, debhelper (>= 10), dpkg-dev (>= 1.16.1~), libaccountsservice-dev (>= 0.6.39), desktop-file-utils, gnome-common, gnome-pkg-tools (>= 0.10), gnome-settings-daemon-dev (>= 3.19.1), gsettings-desktop-schemas-dev (>= 3.21.4), gtk-doc-tools, intltool (>= 0.37.1), libcanberra-gtk3-dev, libcheese-gtk-dev (>= 3.5.91), libcolord-dev (>= 0.1.29), libcolord-gtk-dev (>= 0.1.24), libcups2-dev, libgdk-pixbuf2.0-dev (>= 2.23.0), libgirepository1.0-dev, libglib2.0-dev (>= 2.44.0), libgnome-desktop-3-dev (>= 3.21.2), libgnomekbd-dev (>= 2.91.91), libgnome-bluetooth-dev (>= 3.18.0), libibus-1.0-dev (>= 1.5.2), libgoa-1.0-dev (>= 3.21.5), libgrilo-0.3-dev (>= 0.3.0), libgtk-3-dev (>= 3.22.0), libgtop2-dev, libgudev-1.0-dev, libkrb5-dev, libnm-dev (>= 1.2.0), libnma-dev (>= 1.2.0), libmm-glib-dev, libpolkit-gobject-1-dev (>= 0.103), libpulse-dev, libpwquality-dev, libsmbclient-dev (>= 2:3.6.12-1~), libupower-glib-dev (>= 0.99.0), libwacom-dev (>= 0.7), libxi-dev (>= 2:1.2), libx11-dev, libxft-dev (>= 2.1.2), libxklavier-dev (>= 5.1), libxml2-dev, locales, shared-mime-info, tzdata
dpkg-deb: building package 'pbuilder-satisfydepends-dummy' in '/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Reading package lists...
Building dependency tree...
Reading state information...
aptitude is already the newest version (0.8.7-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously unselected package pbuilder-satisfydepends-dummy.
(Reading database ... 17307 files and directories currently installed.)
Preparing to unpack .../pbuilder-satisfydepends-dummy.deb ...
Unpacking pbuilder-satisfydepends-dummy (0.invalid.0) ...
dpkg: dependency problems prevent configuration of pbuilder-satisfydepends-dummy:
 pbuilder-satisfydepends-dummy depends on cdbs; however:
  Package cdbs is not installed.
 pbuilder-satisfydepends-dummy depends on libaccountsservice-dev (>= 0.6.39); however:
  Package libaccountsservice-dev is not installed.
```

Masuk ke base.tgz ( dengan opsi --save-after-login dan --save-after-exec), lalu pasang paket terkait. Saat logout, perubahan akan tersimpan. Ulangi buildnya.
