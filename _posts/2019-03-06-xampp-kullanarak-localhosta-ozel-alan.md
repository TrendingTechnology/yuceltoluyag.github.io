---
layout:  post
title: XAMPP Kullanarak localhost'a Özel Alan Adı Oluşturma
description: XAMPP Kullanarak localhost'a Özel Alan Adı Oluşturma
tags:
-  ipucu
comments:  true
edit_url:  true
---

Linux Tarafında Kullanmak isteyenleri böyle alalım. => [Dıkla](https://yuceltoluyag.github.io/arch-linux-apachelampp-sanal-sunucu/)

Aşağıdaki dosya dizinine gidin not defteri veya herhangi bir editörle açın

1.  C:\Windows\System32\Drivers\etc\hosts
2.  Açılan dosyanın en altına 127.0.0.1 siteadresi.uzantı şeklinde ekleme yapın Örneğin
    127.0.0.1 eticaret.test
    ![Host Dosyası Edit](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/hosts.png)

3.  XAMPP dizini gidin editorunuzle açın
C:\xampp\apache\conf\extra\httpd-vhosts.conf

  ServerAdmin webmaster@dummy-host.example.com
    DocumentRoot "C:/xampp/htdocs/<font color='red'>eticaret/</font>"
    <font color='orange'>ServerName eticaret.test</font>
    <font color='yellow'>ServerAlias www.eticaret.test</font>
    ErrorLog "logs/eticaret.test-error.log"
    CustomLog "logs/eticaret.test-access.log

Kırmızıyla işaretlenen yere klasör adınızı yazmalısınız. Sarı ile işaretlenen yere yukarıda yazdığımız domain ismini yazacaksınız.Xampp yeniden başlatın
