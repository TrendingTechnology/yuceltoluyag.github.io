---
layout:  post
title: PDO Sum Fonksiyonu kullanımı(morris.js içerir)
description: PDO Sum Fonksiyonu kullanımı(morris.js içerir)
tags:
-  ipucu
comments:  true
edit_url:  true
---

Merhaba mysql (phpmyadmin) deki tablodaki satırları toplamak için keşfettiğim basit ve harika fonksiyonun kullanımı göreceğiz. Chart olarak en sevdiğim eklentilerden birisi olan [morris.js](http://morrisjs.github.io/morris.js/) PDO içerisinde kullanımınında görmüş olacağız.
![php_morris_js](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/php_morris.png)

 resimde ki gibi ben burada **hesap_toplam** ve **hesap_odenen** hücrelerinin toplamını alıp **morris.js** deki grafiğe dönüştürmek istiyorum.

```javascript
Morris.Donut({  element: 'morris-donut-chart',  data: [    $kac_tane = $db->query("SELECT sum(hesap_toplam) AS toplagel FROM  hesaplar")->fetch();  $kac_bane = $db->query("SELECT sum(hesap_odenen) AS bulgel FROM hesaplar")->fetch();  $toplam = $kac_tane[0];  $cik    = $kac_bane[0];  echo ' {label: "Toplam Borçlar",   value:'.$toplam.'},';  echo ' {label: "Toplam Ödemeler",   value:'.$cik.'}'; ?>  ]});
```

umarım anlaşılmıştır anlaşılmayan bir nokta olursa sorularınızı yorumlayabilirsiniz :)

![php_morrisjs_graphical](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/php_morris_grafik.png)

