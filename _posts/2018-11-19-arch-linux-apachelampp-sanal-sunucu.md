---
layout:  post
title: Arch Linux Apache(lampp) Sanal Sunucu Kurulumu
description: Arch Linux Apache(lampp) Sanal Sunucu Kurulumu
tags:
-  ipucu
comments:  true
edit_url:  true
---

Merhaba, bloga uzun süre aradan sonra yazılar ateşlemişken, proje oluştururken sıkça kullandığım bir yöntemin **Türkçe Dökümantasyonu** olsun istedim. Bu yöntemin adı **Virtual Host** olarak bilinmektedir. Her projeye bir domainmiş gibi isim atayarak kodlama ve proje isimlerinin akılda kalması hususunda bana yardımcı oluyor. (Kodlama olarak şu şekilde projeye define bir url atarsınız css js vb gibi dosyaları entegre ederken rahatlık sağlar gibi gibi)



1.  [Arch Linux Xampp Lampp Kurulumu](https://yuceltoluyag.github.io/arch-linux-lampp-kurulumuphp7xmariadbmy/) yapılmalıdır

**baba test** adında domain oluşturdum.

```sh
sudo mkdir /srv/http/baba.test
```

Bu domainin içerisine test olarak bir dosya atın örnek olarak :

```sh
sudo nano /srv/http/baba.test/index.html
```

içerisine şu kodları yapıştırın

```html
<html>
<head>
<title>baba.test</title>
</head>
<body> <h1>Youtube Kanalıma Abone Olmayı unutmayın : Virtual Host işlemi başarılı</h1>
</body>
</html>
```

F3 ardından F2 basarak çıkıyoruz.

```sh
sudo nano /etc/httpd/conf/httpd.conf
```

dosyasının en altına şu kodu yapıştırıyoruz.

```
# Virtual hostsInclude conf/extra/httpd-vhosts.conf
```

F3 enter F2 yaptıktan sonra bu dosyayı oluşturuyoruz.

```sh
sudo nano /etc/httpd/conf/extra/httpd-vhosts.conf
```

bu dosyanın en altına yapıştırıyoruz.

```
    ServerAdmin webmaster@baba.test
    DocumentRoot "/srv/http/baba.test"
    ServerName baba.test    ServerAlias www.baba.test
    ErrorLog "/var/log/httpd/baba.test-error_log"
    CustomLog "/var/log/httpd/baba.test-access_log" common
```
standart kullanım bu şekilde ancak ben sadece documentroot ve servername kısmını kullanıyorum. İsterseniz kullanmak istemediklerinizin başına # işareti koyarsınız. Yada silebilirsiniz : )

```sh
apachectl configtest
```

komutunu çalıştırıp işlemleri test edebilirisniz. Ancak son bir işlem kaldı host dosyamıza bu urlmizi tanımlayacağız.

```sh
sudo nano /etc/hosts
```
bu dosyanın en altına

```sh
127.0.0.1 baba.test
```
yazıp kaydediyorum, apache sunucumu yeniden başlatıyorum.

```sh
sudo systemctl restart httpd
```
![its work](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/baba.test.png)
