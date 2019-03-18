# Website Dokumentasi RistEx URO ITB

## Prasyarat
### Ruby & Ruby-dev
```
sudo apt install ruby ruby-dev
```
### Bundler gems & Jekyll
```
sudo gem install jekyll bundler
```

## Jalankan secara Lokal
1. Clone repository
	```
	git clone https://github.com/ristex/ristex.github.io.git
	```
2. Buka `_config.yml` dan hapus **#** di awal baris `theme: just-the-docs`
3. Install tema just-the-docs
	```
	sudo gem install just-the-docs
	```
4. Build dan jalankan secara lokal
	```
	bundle exec jekyll serve
	```

## Push note
Buka `_config.yml` dan Tambahkan **#** di awal baris `theme: just-the-docs`

Hal ini dilakukan agar github tidak mengirimkan pesan warning, karena theme just-the-docs sebenarnya tidak disupport di github pages
