---
title: Akses Repository Github tanpa Login
date: "2021-10-01"
description: Login yang berulang ketika kita push / pull repository ke github cukup sangat mengganggu. Ada banyak jalan pintas untuk membuatnya Passwordless (tanpa login), salah satunya dengan Token. 
---

### Pengantar

Login yang berulang ketika kita push / pull repository ke github cukup sangat mengganggu. Ada banyak jalan pintas untuk membuatnya **Passwordless** (tanpa login), salah satunya dengan Token.

## Membuat token
1. Login github, di sudut kanan atas klik **photo profile** lalu klik **Settings**
2. Di sidebar kiri, klik **Developer Settings** lalu klik **Personal access tokens**
3. Isi form mulai dari input **Note**, **Expiration**, dan **Select scopes**. Kemudian tekan tombol **generate token**
4. Copy **token** dan paste di Text Editor kesayangan lalu simpan

## Sisipkan token

Ketika **clone** repository dari Github, sisipkan token, menjadi seperti:
```bash
git clone https://c904a061a164cb45a9abf5dbc6c8b8f4c16d6xxx@github.com/user/test.git
```

Atau jika terlanjur **clone** edit **git config** di directory local

```bash
nano .git/config
```

```
[core]
repositoryformatversion = 0
filemode = true
bare = false
logallrefupdates = true
[remote "origin"]
url = https://github.com/user/test.git
fetch = +refs/heads/*:refs/remotes/origin/*
```

Ubah menjadi

```
[core]
repositoryformatversion = 0
filemode = true
bare = false
logallrefupdates = true
[remote "origin"]
url = https://c904a061a164cb45a9abf5dbc6c8b8f4c16d6xxx@github.com/user/test.git
fetch = +refs/heads/*:refs/remotes/origin/*
```

Tekan **ctrl + x** dan **Enter** untuk menyimpan **config**, Selesai.