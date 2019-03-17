---
layout: default
title: Instalasi dan Konfigurasi PostgreSQL
nav_order: 1
parent: Eksplorasi PostgreSQL
grand_parent: Eksplorasi Database
---

# Instalasi dan Konfigurasi PostgreSQL
{: .no_toc }

## Daftar Isi
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Tutorial ini telah dicoba di Ubuntu 18.04

## Instalasi dari Kode Sumber
1. Download kode sumber postgreSQL di [sini](https://www.postgresql.org/ftp/source/v11.2/).
    Versi terakhir ketika tulisan ini dibuat: v11.2

2. Ekstrak sesuai dengan jenis kompresi dan archieve-nya
    ```
    tar xvzf file.tar.gz
    ```
    atau  
    ```
    tar xvjf file.tar.bz2
    ```

3. Konfigurasi kode sumber
    Sebelum menkonfigurasi, pastikan di sistem anda telah terinstall gcc, readline-devel dan zlib-devel
    ```
    sudo apt install gcc zlib1g-dev libreadline6-dev
    ```
    Lakukan konfigurasi:
    ```
    ./configure
    ```
    Mengeksekusi skrip configure bertujuan untuk mengkonfigurasi software agar sesuai dengan sistem (OS) yang anda gunakan.

4. Build & Compile software
    ```
    make
    ```
    Perintah ini akan menjalankan beberapa build-command yang diperlukan untuk membangun software

5. Instalasi software
    ```
    sudo make install
    ```
    Perintah ini akan "menginstall" (mengcopy program yang telah dibuild ke lokasi yang seharusnya). Lokasi default hasil instalasi berada di `/usr/local/pgsql`

## Prosedur Post-Installation
1. Menambahkan user baru (postgres)
Dalam menjalankan server PostgreSQL dibutuhkan suatu user khusus (biasa diberi nama postgres).  
Tambahkan user baru:
    ```
    sudo adduser postgres
    ```

    Ikuti arahan prompt hingga selesai.

2. Buat folder untuk tempat menyimpan file-file database
Biasanya di /usr/local/pgsql/data
    ```
    sudo mkdir /usr/local/pgsql/data
    ```

3. Berikan akses kepemilikan folder tersebut kepada user postgres
    ```
    sudo chown postgres /usr/local/pgsql/data
    ```

4. Masuk sebagai user postgres
    ```
    su - postgres
    ```

5. Mengatur Environment Variables   
    Edit file `~/.bashrc` tambahkan :
    ```
    export PATH="$PATH:/usr/local/pgsql/bin"
    ```
    di akhir file kemudian save.
    Jalankan perintah 
    ```
    source ~/.bashrc
    ```
    Lalu periksa apakah PATH telah berubah dengan 
    ```
    echo $PATH
    ```

## Inisialisasi Database Cluster dan Jalankan PostgreSQL Server
Anda hanya dapat menginisialisasi database dan menjalankan postgreSQL jika sedang masuk sebagai user postgres.
1. Membuat cluster PostgreSQL
    ```
    initdb -D /usr/local/pgsql/data
    ```
    Perintah ini akan membuat cluster database.

2. Jalankan server PostgreSQL
    ```
    pg_ctl start -D /usr/local/pgsql/data
    ```

3. Masuk ke psql cmd-line program
    ```
    psql
    ```

4. Keluar dari psql
    ```
    exit;
    ```

5. Hentikan server PostgreSQL
    ```
    pg_ctl stop -D /usr/local/pgsql/data
    ```

---
Referensi:
- <https://hackprogramming.com/2-ways-to-permanently-set-path-variable-in-ubuntu/>
- <https://www.wikihow.com/Install-PostgreSQL-Using-the-Source-Code>
- <https://www.tecmint.com/install-postgresql-from-source-code-in-linux/>
- <https://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file>
