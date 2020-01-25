---
layout:  post
title:  Linux Üzerinde Apache2 MySQL PhpMyAdmin Kurulumu debian ve türevleri
description: Linux Üzerinde Apache2 MySQL PhpMyAdmin Kurulumu debian ve türevleri
tags:
-  ipucu
comments:  true
edit_url:  true
---
Merhaba, windows ve linuxta uyumlu çalışan xampp kullanmaktaydım.Her nedense xamppın yerine apache kurmak ilgimi çekti :) Kurulumu son derece basit ve sürekli açık :) Bende yeni tecrübe ettiğim bu işlemi,sizlerle paylaşmak istedim 🙌



Her koddan sonra entere basmayı unutmayın 👀

```sh
sudo apt-get updatesudo apt-get install apache2
```

bu komuttan sonra localhost yada ip adresinizi tarayıcınıza yazın apachenin çalıştığını göreceksiniz.

```sh
sudo apt-get install mysql-server mysql-client
```

Önünüze şifre sorma ekranı gelecek oraya iki defa şifrenizi yazın.

![configure_lampp](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/configure_lampp.jpeg)

```sh
sudo systemctl status mysql
```

bu kodun çıktısı şu şekilde olacak

```sh
mysql.service - MySQL Community Server
Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: en
Active: active (running) since Cts 2017-06-17 23:30:16 +03; 38min ago
Main PID: 18866 (mysqld)
CGroup: /system.slice/mysql.service
└─18866 /usr/sbin/mysqld
Haz 17 23:30:15 friday13-MS-7817 systemd[1]: Starting MySQL Community Server...
Haz 17 23:30:16 friday13-MS-7817 systemd[1]: Started MySQL Community Server.
```

MariaDB yüklemek isteyenler yorum bıraksın yardımcı olurum, ben yüklemek istemediğim için kurmadım.

```sh
mysql_secure_installation
```

bu komutu yazdıktan sonra şifre ekranına yukarıda yazdığınız şifrenin aynısını yazın.Gelen seçenek için entere basın Remove anonoymus userkısmı için Y yazın entere basın. Disallow Root kısmı için Y basın Reload privegille kısmı için Y basın ALL DONE ! dediyse tamamdır :)

```sh
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt search php7
sudo apt install php7.0-mysql php7.0-curl php7.0-json php7.0-cgi php7.0 libapache2-mod-php7.0
```

Kurulum bittikten sonra php -v yazarak versiyonu görebilirsiniz.

```sh
sudo systemctl restart apache2
```

apache mizi yeniden başlatıyoruz..

```sh
sudo apt-get install phpmyadmin
```

karşımıza gelen ekrana apache2 yi seçip sonraki işlemde yukarıda yazdığımız şifrenin aynısını iki kere yazıp gelen seçeneğe evet diyoruz.

```sh
sudo systemctl restart apache2
```

apache mizi yeniden başlatıyoruz..localhost/phpmyadmin yazıyoruz. root ve oluşturduğumuz şifreyi yazarak işlemi tamamlamış oluyoruz :)Eğer ki phpmyadmin kısmında 404 hatası veriyor ise

```sh
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
sudo a2enconf phpmyadmin.conf
sudo service apache2 reload
```

tekrar localhost/phpmyadmin giriyoruz olmuş :D

bu kısımda The mbstring extension is missing. Please check your PHP configuration. Hatası ile karşılaştıysanız.

```sh
sudo apt-get install libapache2-mod-php7.0
sudo apt-get install php7.0-mbstring
sudo service apache2 restart
```

kurulumda hata alır iseniz yorum bırakın çözelim, iyi çalışmalar.
