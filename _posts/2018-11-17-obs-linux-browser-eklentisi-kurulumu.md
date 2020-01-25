---
layout:  post
title: OBS Linux Browser Eklentisi Kurulumu + Discord Chat Eklenmesi
description: OBS Linux Browser Eklentisi Kurulumu + Discord Chat Eklenmesi
tags:
-  ipucu
comments:  true
edit_url:  true
---

Merhaba, Open Broadcaster Software Video kaydetme ve canlı yayınyapma konusunda en iyi uygulamalardan bir tanesidir. Linux tarafında uygulamaya nasıl eklenti eklenip aktif edileceği hususunda Türkçe kaynak bulunmadığı için, bu rehberi hazırlamaya karar verdim. OBS nasıl kullanılır anlatmayacağım çünkü bu konuda yeterince Türkçe kaynak var..

OBS plugin ekleyip test olarak Discord StreamKit entegre edeceğiz.

-   [obs-linuxbrowse](https://github.com/bazukas/obs-linuxbrowser/releases)r
-   [discordstreamkit](https://discordapp.com/streamkit)

Bu işlemleri ellede yapabilirsiniz. Ben terminal üzerinden yapmayı tercih ediyorum.

```sh
wget https://github.com/bazukas/obs-linuxbrowser/releases/download/0.6.1/linuxbrowser0.6.1-obs23.0.2-64bit.tgz
mkdir -p $HOME/.config/obs-studio/plugins
tar xfvz linuxbrowser0.6.1-obs23.0.2-64bit.tgz -C $HOME/.config/obs-studio/plugins/
```

![obs linux browser](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/linux_browser.png)

Burada yaptığım işlem dosyayı indirdim. Ev dizinim altındaki .config dosyam içerisinde ki obs-studio içerisine plugins klasörü oluşturdum. Farklı bir eklenti ekleyeceksem bu dosyanın içerisine atmam yeterlidir.

OBS açıyoruz Kaynaklar + tuşuna basıp Linux Browser i Seçiyoruz

![linux_browser_kaynaklar](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/linux_browser_kaynaklar.png)

Stream Kits linki üzerinde sayfanın en altında bulunan obs->connect discorda basıyorum
![linux_browser_discord](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/linux_browser_discord.png)

Install For OBS butonuna tıklıyoruz

![linux_browser_obs](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/linux_browser_obs.png)

Gelen Ekranda Serverimi Seçip Ses - Yazı seçeneklerinde hangisini isterseniz eklersiniz
![linux_browser_obs_custom.png](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/linux_browser_obs_custom.png)

Açtığımız Linux Browser Url Kısmına Linkimizi Yapıştırıyoruz. İsterseniz yükseklik genişlik hatta css bilginizle dahada güzelleştirebilirsiniz
![linux_browser_settings](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/linux_browser_settings.png)


![linux_browser_final](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/linux_browser_final.png)

Bu arada discord sunucumuza katılmak isterseniz [Discord Sunucuma Katıl](https://discordapp.com/invite/da3Su8s)
