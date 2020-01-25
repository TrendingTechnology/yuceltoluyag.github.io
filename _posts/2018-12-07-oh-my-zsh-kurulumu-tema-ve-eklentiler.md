---
layout:  post
title: Oh My ZSH Kurulumu (tema ve eklentiler dahil)
description: Oh My ZSH Kurulumu (tema ve eklentiler dahil)
tags:
-  ipucu
comments:  true
edit_url:  true
---
Merhaba, uzun süredir fish shell kullanıyordum. Oh my zsh deneyimlemek istedim. Kurulumda ve kullanımda bir kaç hata(bug) gibi şeylerle karşılaştım. Maalesef yeterince açıklayıcı Türkçe kaynak bulamadım. Resmi ve reposundan arakladığım bilgiler ile tertemiz bir kurulum gerçekleştirdim.

```sh
sudo apt-get install zsh #debian
sudo pacman -S zsh #arch based
```
Şimdi resmi sitesinde ki ister **curl** ister **wget** li kısmını indirebiliriz. Ben **curl** kullandım.

```sh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"chsh -s /usr/bin/zsh
```
 Bu işlem default shellimizi değiştirecek. Yani varsayılan olarak zsh çalışacak-> Sonraki adımda Şifrenizi yazınız, ve **bilgisayarı yeniden** başlatınız.
Bu adımda ne yapsanızda shelliniz değişmiyor ise izlemeniz gereken iki yol var.

-> Öncelikle daha önce **fish** vb terminal eklentilerini kurduysanız genelde bu sorun bundan kaynaklanıyor. Ben **fish** yerine farklı bir plugin kullanmak istediğimden ötürü bu hata ile karşılaşıyordum.

chsh — s /usr/bla/blashell shelinizi değiştirmeye çalıştığınızda saçma  bu hatayı verecektir,Terminal için kabuğu değiştirmemelisiniz

1.  sudo subl /etc/passwd (subl yerine nano gedit vs de kullanabilirsiniz )
2.  /bin/zsh veya değiştirmek istediğiniz pluginin kısa adı ne ise onu yazıyorsunuz. resimde gördüğünüz 1 ve 40 satırdaki kodları zsh olarak değiştiriniz. Sizde farklı yerde olabilir. ![oh-my-zsh](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/oh_my_zsh.png)

<font color="orange"> manuel olarak işlemi gerçekleştirdik. Pek sağlıklı bir yöntem değildir lakin fazla bilgi göz çıkarmaz 😅  </font>

Yada ev dizininde .bashrc dosyasını açın en alt satıra (yada .bash_profile)

```sh
if [[ $- == *i* ]]; then export SHELL=zsh exec zsh -l afi
```
yazarak kaydedin terminalizi yeniden başlatın.

## Oh My ZSH tema kurulumu

```
subl ~/.zshrc  # subl yerine nano gedit vs kullanabilirsiniz.
```

10 satırdaki ZSH_THEME=”robbyrussell” tırnak işareti yerine [ZSH temaları](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)bu adresteki beğendiğimiz temanın kısa adını yazıyoruz. Örneğin ZSH_THEME=”agnoster”

### Oh My ZSH eklenti kurulumu

```sh
subl ~/.zshrc  # subl yerine nano gedit vs kullanabilirsiniz.
```

54 satırdaki plugins=(git) varsayılan olarak gelir. [ZSH eklentileri](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins) buradan beğendiğiniz eklentinin ismini boşluk bırakarak dosyaya yazmanız yeterli örneğin
```sh
 plugins=(git extract)
```
burada dosya çıkartma eklentisini aktif etmiş oldum. Kaydedip çıktıktan sonra
```sh
 source ~/.zshrc
```
 komutunu terminalde çalıştırın tamamdır. Yada terminali kapatıp açabilirsiniz.

Aklınıza takılan soru ve sorunlar için yorum bırakmanız yeterlidir. Sağlıcakla 🤗
