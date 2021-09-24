---
title: Instalasi Laravel di Ubuntu Server
date: "2018-08-28"
description: Laravel adalah framework php gratis / open source yang populer dan banyak digunakan oleh banyak developer dalam membangun aplikasi web.
---

### Pengantar

Laravel adalah framework php gratis / open source yang populer dan banyak digunakan oleh banyak developer dalam membangun aplikasi web. **Laravel** dapat berjalan di sistem operasi Windows, macOs, maupun Linux selama sistem operasi tersebut sudah terinstal **PHP**.

### Persiapan

Sebelum instalasi **Laravel**, kita siapkan terlebih dahulu Server **Ubuntu 18.04 Server** yang sudah terinstal **LAMP**. Jika belum, silahkan instal dulu **LAMP** nya di [Cara Instalasi LAMP (Linux, Apache, Mysql, PHP) di Ubuntu 18.04](http://localhost:8000/instalasi-lamp-di-ubuntu-18-04/)

## Instalasi Composer

```bash
sudo apt install composer
```

Test jika instalasi berhasil dengan perintah: 

```bash
composer
```

## Instalasi Laravel

```bash
cd /var/www/html
```

```bash
composer create-project --prefer-dist laravel/laravel laravel
```

```bash
cd laravel && mv .env.example .env
```

```bash
php artisan key:generate
```

## Konfigurasi Apache Web Server

```bash
sudo nano /etc/apache2/sites-available/laravel.conf
```

```conf
# laravel.conf

<VirtualHost *:80>
  ServerName [nama_domain]

  ServerAdmin webmaster@localhost
  DocumentRoot /var/www/html/laravel/public
  <Directory /var/www/html/laravel/public >
      Options Indexes FollowSymLinks MultiViews
      AllowOverride All
      Require all granted
  </Directory>
  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

```bash
sudo a2ensite laravel.conf
```

```bash
sudo a2enmod rewrite
```

```bash
sudo a2enmod php7.0
```

```bash
sudo service apache2 restart
```

## Konfigurasi file hosts

```bash
sudo nano /etc/hosts
```

```
# /etc/hosts

127.0.1.1   [nama_domain]
```

**ctrl + x**, lalu tekan **y** untuk menyimpan.

Izinkan Apache web server mengakses folder **laravel** dan sub folder **storage** dengan jalankan perintah:

```bash
sudo chgrp -R www-data /var/www/html/laravel
```

```bash
sudo chmod -R 775 /var/www/html/laravel/storage
```

Sampai langkah ini proses instalasi **Laravel** di **Ubuntu Server** selesai. Silahkan buka browser untuk testing.

```
http://nama_domain
```