---
layout:  post
title: composer yavaş indirme sorunu çözümü
description: composer yavaş indirme sorunu çözümü
tags:
-  ipucu
comments:  true
edit_url:  true
---
![Composer Slow Download Fixed Solution](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/composer.jpeg)<div  class="showyourterms"><div  class="type"  data-action="command"  data-delay="400"><br />composer diagnose</div><div  class="line yellow"  data-delay="400">Checking platform settings: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking git settings: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking http connectivity to packagist: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking https connectivity to packagist: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking github.com rate limit: 1 </div><div  class="line yellow"  data-delay="400"><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking disk free space: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking pubkeys: <br /><div  class="red">FAIL</div></div><div  class="line yellow"  data-delay="400"><div  class="red">Missing pubkey for tags verification </div></div><div  class="line yellow"  data-delay="400"><div  class="red">Missing pubkey for dev verification </div></div><div  class="line yellow"  data-delay="400">Run composer self-update --update-keys to set them up </div><div  class="line yellow"  data-delay="400">Checking composer version: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Composer version: 1.9.1 </div><div  class="line yellow"  data-delay="400">PHP version: 7.4.0 </div><div  class="line yellow"  data-delay="400">PHP binary path: /usr/bin/php </div></div>

Yukarıda ki gibi hata alıyorsanız [Composer PUBLIC KEY](https://composer.github.io/pubkeys.html) adresine gidip güncel keyleri almanız gerekmektedir. Bu keyleri iki yöntemle oluşturabilirsiniz.
* Terminal yöntemi ile
<div  class="showyourterms"><div  class="type"  data-action="command"  data-delay="400">composer self-update --update-keys</div></div>
komutunu çalıştırdak sonra pubkeys linkinde ki keyleri sırasıyla yapıştırın. (Yapıştırırken, elinizi korkak alıştırmayın tümü seçip yapıştırabilirsiniz :)

Diğer yöntem ise Composer ayarlarınızın bulunduğu klasöre giderek (**/home/kullaniciadiniz/.config/composer/)** bu dizine iki tane dosya oluşturuyoruz.
1.  keys.dev.pub
2.  keys.tags.pub

Bu dosyaların içerisine sırasıyla pubkeys linkinde ki keyleri yapıştırıyoruz. Terminaliniz açıksa kapatın ve yeniden açın
<div  class="showyourterms"><div  class="type"  data-action="command"  data-delay="400">composer diagnose</div><div  class="line yellow"  data-delay="400">Checking platform settings: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking git settings: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking http connectivity to packagist: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking https connectivity to packagist: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking github.com rate limit: 1 </div><div  class="line yellow"  data-delay="400"><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking disk free space: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking pubkeys: </div><div  class="line yellow"  data-delay="400"><div  class="green">Tags Public Key Fingerprint: 57815BA2 7E54DC31 7ECC7CC5 573090D0 87719BA6 8F3BB723 4E5D42D0 84A14642 </div></div><div  class="line yellow"  data-delay="400"><div  class="green">Dev Public Key Fingerprint: 4AC45767 E5EC2265 2F0C1167 CBBB8A2B 0C708369 153E328C AD90147D AFE50952 </div></div><div  class="line yellow"  data-delay="400"><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Checking composer version: <br /><div  class="green">OK</div></div><div  class="line yellow"  data-delay="400">Composer version: 1.9.1 </div><div  class="line yellow"  data-delay="400">PHP version: 7.4.0 </div><div  class="line yellow"  data-delay="400">PHP binary path: /usr/bin/php </div></div>

Şunu belirtmeliyim ki yapılan işlemlere composer tarafında bazen **anlık tepki** alamıyorsunuz. Yani bu configin tanınması bir kaç dakika alabiliyor. O yüzden yaptım hala aynı diye düşünmeyin.. Ortalama **5 dakika** geçtikten sonra halen devam ediyorsa alternatif olarak şu yöntemleride deneyebilirsiniz.

**Alternatif 1**
vvv komutunu kullanabilirsiniz örneğin
<div  class="showyourterms"><div  class="type"  data-action="command"  data-delay="400">composer -vvv require phpunit/phpunit</div></div>

**Alternatif 2**
Bildiğiniz üzere paketler genel olarak packagist üzerinden yüklenir. Packagist composer ayar dosyamıza ekleyebiliriz.
<div  class="showyourterms"><div  class="type"  data-action="command"  data-delay="400">composer config --global repo.packagist composer https://packagist.org</div></div>

**Alternatif 3**
Aslında bunu en başta mı versem diye düşündüm. Özellikle sunucu tarafında composer kullanıyorsanız IPV6 üzerinde timeout hatası alıyorsanız şu komutu çalıştırmalısınız
<div  class="showyourterms"><div  class="type"  data-action="command"  data-delay="400">sudo sh -c "echo 'precedence ::ffff:0:0/96 100' &gt;&gt; /etc/gai.conf"</div></div>

Detaylı bilgi için [https://getcomposer.org/doc/articles/troubleshooting.md#operation-timed-out-ipv6-issues-](https://getcomposer.org/doc/articles/troubleshooting.md#operation-timed-out-ipv6-issues-)

**Alternatif 4**

Yapılacak herşeyi yaptınız, son çare olarak parelel composer reposunu deneyebilirsiniz.Detaylı bilgi ve kurulum için [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) göz atabilirsiniz.


**Tekrar belirtiyorum** yapılan işlemlerden sonra ortalama **BEŞ(5)** dakika bekleyin. İşleme tekrar başlamadan önce composer clear-cache ve composer dump-autoload komutlarını kullandıktan sonra başlayın.
