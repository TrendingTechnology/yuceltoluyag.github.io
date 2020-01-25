---
layout:  post
title: Linux Codeigniter son sürüm Nasıl Yüklenir
description: Linux Codeigniter son sürüm Nasıl Yüklenir
tags:
-  ipucu
comments:  true
edit_url:  true
---

Gökhan Kandemir’in [codeigniter kitabı](http://kablosuzkedi.com/index.php/2017/10/24/codeigniter-3-kitabi-cikti/) aldıktan,çalışma yapabilmek için codeigniteri kurmam gerekliydi. Kurulum gayet basit,localde çalışabilmek için farklı bir ayara gerek kalmıyor ancak sunucu tarafında bir kaç ayar daha yapmanız gereklidir.Dileyen olursa o ayarlarıda paylaşırım.


1.  [Apache Kurmalısınız](https://yuceltoluyag.github.io/linux-uzerinde-apache2-mysql-phpmyadmin_14/) [Arch linux için  Tıklayın](https://yuceltoluyag.github.io/arch-linux-lampp-kurulumuphp7xmariadbmy/)
2.  [Codeigniter](https://codeigniter.com/download) sayfasından indirme bağlantımızı kopyalıyoruz. Şu an ki versiyon 3.1.9

```sh
wget https://github.com/bcit-ci/CodeIgniter/archive/3.1.9.zip
unzip 3.1.6.zip
mv CodeIgniter-3.1.6 codeigniter
sudo chown -R sistemkullaniciadiniz:sistemkullanıcıadınız /var/www/html/
cp -R codeigniter /var/www/html/codeigniter
service apache2 restart
```
[http://localhost/codeigniter](http://localhost/codeigniter)  adresinden CI ‘ ya ulaşabilirsiniz.

3. [Video Link](https://www.youtube.com/channel/UCJyK4D5BcoPXjV5T8N8-liA?view_as=subscriber)
