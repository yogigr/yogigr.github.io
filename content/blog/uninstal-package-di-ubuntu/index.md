---
title: Uninstal atau Hapus Package di Ubuntu
date: "2018-08-27"
description: "Adakalanya kita ingin menghapus package/paket yang tidak begitu penting di sistem operasi kita karena beberapa alasan."
---

Adakalanya kita ingin menghapus package/paket yang tidak begitu penting di sistem operasi **Ubuntu** kita karena beberapa alasan. Langsung saja kita buka **terminal** dan jalankan perintah:

```bash
apt --installed list | more
```

perintah diatas akan memberi kita informasi paket apa saja yang sudah terinstal. Setelah kita menemukan nama paketnya, jalankan lagi perintah:

```bash
sudo apt-get remove --purge [nama_paket]
```

```bash
sudo apt-get autoremove
```

```bash
sudo apt-get clean
```

selesai.