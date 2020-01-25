---
layout:  post
title: Vagrant VirtualBox 6.1 ile uyumlu hale getirmek
description: Vagrant VirtualBox 6.1 ile uyumlu hale getirmek
tags:
-  ipucu
comments:  true
edit_url:  true
---
![Vagrant VirtualBox Windows Linux Güncelleme](https://raw.githubusercontent.com/yuceltoluyag/yuceltoluyag.github.io/master/uploads/ol_vbox_vagrant-min.png)11 Aralık 2019 tarihinde Virtualbox'un yeni sürümü yayınlandı. Bu yayınlama ile birlikte vagrant ile virtualbox arasında bir uyumsuzluk sorunu oldu. Vagrant'ı çalıştırdığınızda karşınıza şu ileti gelmekteydi :

<div  class="showyourterms"><br /><div  class="type"  data-action="command"  data-delay="400"><br />The provider 'virtualbox' that was requested to back the machine<br />'homestead' is reporting that it isn't usable on this system. The<br />reason is shown below:<br /><br />Vagrant has detected that you have a version of VirtualBox installed<br />that is not supported by this version of Vagrant. Please install one of<br />the supported versions listed below to use Vagrant:<br /><br />4.0, 4.1, 4.2, 4.3, 5.0, 5.1, 5.2, 6.0<br /><br />A Vagrant update may also be available that adds support for the version<br />you specified. Please check www.vagrantup.com/downloads.html to download<br />the latest version.</div><br /></div>

6.0 dan sonrası için henüz gerekli işlemler yapılmamıştı. Bende bu uyarıyı güncellemeden sonra aldım. Güncellemeden sonra O**racle** gerekli makaleyi **yayınlamıştı**,bu sayede beni bir dertten kurtardılar.

1.  /opt/vagrant/embedded/gems/2.2.6/gems/vagrant-2.2.6/plugins/providers/virtualbox/driver/meta.rb dosyasına açalım ve şu satırı ekleyelim

<div  class="showyourterms"><div  class="type"  data-action="command"  data-delay="400">@logger.debug("Finding driver for VirtualBox version: #{@@version}")<br />driver_map = {<br />"4.0" =&gt; Version_4_0,<br />"4.1" =&gt; Version_4_1,<br />"4.2" =&gt; Version_4_2,<br />"4.3" =&gt; Version_4_3,<br />"5.0" =&gt; Version_5_0,<br />"5.1" =&gt; Version_5_1,<br />"5.2" =&gt; Version_5_2,<br />"6.0" =&gt; Version_6_0,<br /><div  class="green">"6.1" =&gt; Version_6_1,</div>}</div></div>

yeşil renkle belirtiğim satırıcı ekleyin. Eğer windows kullanıyorsanız bu dosya **C:\HashiCorp\Vagrant\embedded\gems\2.2.6\gems\vagrant-2.2.6\plugins\providers\virtualbox\driver** içerisindedir.(Kaydetme sorunları yaşamamak için kullandığınız not defteri yada editoru yönetici olarak açın.)
-   Yine aynı dizinin içerisinde **version_6_1.rb** adlı dosya oluşturmalıyız. Cem Yılmaz'ın dediği gibi burada oluşturulmuşu var = > Bu dosyaya  [buradan ulaşabilirsiniz](http://www.coter.net/upload/version_6_1.rb) +  [Alternatif](http://www.mediafire.com/file/wzq4l2xe6ul2dnw/version_6_1.rb/file)
-   Bu işlemden sonra bir üst dizinde ki
- **plugin.rb** dosyasını açıyoruz. Ve şu satırı ekliyoruz :
<div  class="showyourterms"><div  class="type"  data-action="command"  data-delay="400"># Drop some autoloads in here to optimize the performance of loading<br /><br /># our drivers only when they are needed.<br /><br />module Driver<br />autoload :Meta, File.expand_path("../driver/meta", __FILE__)<br />autoload :Version_4_0, File.expand_path("../driver/version_4_0", __FILE__)<br />autoload :Version_4_1, File.expand_path("../driver/version_4_1", __FILE__)<br />autoload :Version_4_2, File.expand_path("../driver/version_4_2", __FILE__)<br />autoload :Version_4_3, File.expand_path("../driver/version_4_3", __FILE__)<br />autoload :Version_5_0, File.expand_path("../driver/version_5_0", __FILE__)<br />autoload :Version_5_1, File.expand_path("../driver/version_5_1", __FILE__)<br />autoload :Version_5_2, File.expand_path("../driver/version_5_2", __FILE__)<br />autoload :Version_6_0, File.expand_path("../driver/version_6_0", __FILE__)<br /><div  class="green">autoload :Version_6_1, File.expand_path("../driver/version_6_1", __FILE__)</div>end</div></div>

Bu işlemlerden sonra vagrant ınızı çalışması gerekli :) Eğer hata alırsanız yorumlamaktan çekinmeyin 👍💗
