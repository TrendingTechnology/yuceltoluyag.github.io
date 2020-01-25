---
layout:  post
title:  Sweet Alert Sınıfı Kullanımı Detaylı Anlatım Tüm Argümanları ile birlikte
description: Sweet Alert Sınıfı Kullanımı Detaylı Anlatım Tüm Argümanları ile birlikte
tags:
-  ipucu
comments:  true
edit_url:  true
---

Merhaba klasik uyarı pencerelerinden sıkılanlar için, mobil uyumlu sweetalert sınıfından bahsedeceğim.. Sweetalert i PHP içerisinde nasıl kullanırım diye meraklanan var ise [PHP Morris Js](https://yuceltoluyag.github.io/pdo-sum-fonksiyonu-kullanmmorrisjs/) konusunu incelesin, en azından kafanızda birşeyler patlar :D
Öncelikle dosyaları projemize dahil ediyoruz.

```javascript
<script src="dist/sweetalert.min.js"></script>
<link rel="stylesheet" type="text/css" href="dist/sweetalert.css">
```

Uyarı verdirmek istediğimiz yeri seçiyoruz.Butona tıklayınca çıksın istedim.

```html
<button>Tıkla Bana</button>
```

Daha sonra jquery kodlarımızı yazıyoruz.

```javascript
<script type = "text/javascript" >
    $(function() {
        $("button").click(function() {
            sweetAlert({
                title: "Bu Bir Başlıktır",
                text: "Burası <b>Açıklama</b> Kısmıdır adamcoder.net",
                allowEscapeKey: "true", // false değeri alırsa esc kapatmaz
                customClass: ".sınıf", // <button class="sınıf"> gibi :)
                allowOutsideClick: "false", // true yaparsak nereye tıklarsak uyarı kapanır
                showCancelButton: "false", // true yaparsak cancel butonu görünür
                showConfirmButton: "true", // Ok butonunu gösterir false yaparsanız görünmez
                confirmButtonText: "Tamamdır", // ok butonunun yerine istediğnizi yazarsınız
                confirmButtonColor: "#AEDEF4", // Ok butonunu rengini değiştirebilirsiniz
                cancelButtonText: "Geri Git", // Cancel Butonun yerine istediğimizi yazabiliriz.
                closeOnConfirm: "true", // Okeye basıldıysa burayı göster şurayı göster gibi
                closeOnCancel: "true", // cancele basılırsa şurayı göster gibi(if else gibi)
                imageUrl: "https://a2-images.myspacecdn.com/images03/21/026f6a3d1a084b95bcda8e277a7cb743/300x300.jpg", // pencere resmini değiştirir
                imageSize: "100x100", // resmin boyutunu ayarlar
                timer: "10000", // 4 saniyede uyarı penceresini kapatır
                html: "true"
                // diğer ayarları bu şekilde test ederek öğrenebilirsiniz. Bu işler kurcalamadan olmaz : )
            });
        })
    })
    </script>
```

|Argüman| Ne İş Yapar |
|--|--|
| title| Uyarının başlık kısmıdır.|
| text| Uyarının Mesaj Kısmıdır.|
| type| warning, "error", "success" "info" ve dilerseniz input değeride verebilirsiniz. Uyarı mesajlarınızda işinize yarar|
| allowEscapeKey| Bu değer ESC tuşuyla uyarı penceresini kapatabiliyoruz. False değeri vererek bu kuralı uygulamayabilirsiniz|
| customClass| Bu değer uyarınıza bir sınıf atayarak özelleştirmenize yarar.|
| allowOutsideClick| Bu değer uyarı pencerenin dışına tıklanırsa pencereyi kapatmanıza yarar, varsayılan değer olarak false gelir true yaparsanız nereye tıklarsanız tıklayın pencere kapanır.|
| showCancelButton| showCancelButton -> Türkçe'siyle geri butonunu göstereyim mi abi diyor 🤡|
| showConfirmButton| showConfirmButton -> Türkçesiyle Tamam butonunu göstereyim mi abi diyor 🤡|
| confirmButtonText| confirmButtonText -> Tamam butonu yerine istediğinizi yazabilirsiniz "Kabul Ediyorum" vs gibi|
| confirmButtonColor| confirmButtonColor -> Tamam Butonu rengini değiştirebilirsiniz. HEX renk kodları seçmeniz öneriliyor. #DDDFFF gibi|
| cancelButtonText| Geri(iptal) butonu yerine istediğinizi yazabilirsiniz "Kabul Etmiyorumm" vs gibi|
| imageUrl| Bu değer uyarıya varsayılan olarak gelen resimleri kendi isteğimize göre değiştirmemize yarıyor.|
| imageSize| Bu değer uyarıya verdiğimiz resimlerin genişlik ve yüksekliğini ayarlamamıza yarıyor. 100x100 gibi.|
| timer|Bu değer uyarı milisaniye cinsinden uyarıyı otamatik olarak kapatmaya yarıyor 1000 yani 1 saniyede kapatır|
| html| Bu değer uyarı HTML kodları kullanmamıza yarıyor|
| animation| Bu değer uyarı Animasyon açılış ekranını değiştiriyor.|
| inputType| Bu değer İnput lara yazdığımız değerleri girebiliyoruz. Text,Password,Submit vs gibi|
| inputPlaceholder| Bu değer İnput ların içerisine açıklama yazısı girebilmemize yarıyor.|
| inputValue| Bu değer İnput lara değer vermek için kullanılıyor.|
| closeOnConfirm closeOnCancel| Bu değerler Uyarı Penceresinde ikinci bir pencere açmaya yarar|

![sweetalert](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/sweetalert.png)

[Örnek Dosyayı İndirebilirsiniz](http://www.mediafire.com/file/aelw1zkhwcv17b7/sweetalertadamcoder.zip)
