---
layout:  post
title: PHPStorm içerisinde cmder kullanmak
description: PHPStorm içerisinde cmder kullanmak
tags:
-  ipucu
comments:  true
edit_url:  true
---

Phpstorm içerisinde terminali kullanabilmek için **ortam değişken**lerine yolu belirtmemiz gereklidir. Windows ortamında ortam değişkeni eklemek için :
-   Bilgisayarıma sağ tıklayıp  **özellikler** ardından  **gelişmiş sistem ayarları** na tıklayınız.
    **Başlangıç ve Kurtarma**  nın hemen altında  **ortam değişkenleri**ni göreceksiniz. Ortam değişkenlerine tıklayıp yeni 'ye tıklayın
    ![ortam_degiskenleri_windows10](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/ortam_degiskenleri1.png)

	-   değişken adı kısmına : CMDER_ROOT
	-   yol kısmına : C:\cmder

![ortam_degiskenleri_windows10](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/ortam_degiskenleri3.png)

Ben Cmder'in full sürümünü indirip c dizinine çıkarmıştım. Siz nereye kurduysanız o dizini gösterirsiniz.

![ortam_degiskenleri_windows10](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/ortam_degiskenleri2.png)

Daha sonra phpstorm içerisinden ayarlara girin. **Tools** altında ki **Terminal** menüsüne tıklayın. **Shell Path** kısmına
```sh
"cmd" /k ""%CMDER_ROOT%\vendor\init.bat""
```
kodunu yapıştırın.

![phpstorm_cmder_full](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/phpstorm_terminal.png)

Ayarları uyguladıktan sonra phpstormu yeniden başlatın. Phpstorm yeniden açıldıktan sonra terminal sekmesine tıklayın.

![phpstorm_cmder_full](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/phpstorm_terminal2.png)

Cmder terminali windows kullanan arkadaşlara tavsiye ederim. [https://cmder.net/](https://cmder.net/) adresinden full sürümünü indirip istediğiniz dizine çıkartabilirsiniz.
