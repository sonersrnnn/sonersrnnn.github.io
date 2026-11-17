---
title: "Arch Linux Terminal Komutları: Kapsamlı ve Pratik Rehber"
date: 2026-11-14
slug: arch-linux-terminal-komutlari
description: Arch Linux terminal komutları rehberiyle pacman, AUR, systemd ve sistem yönetimi komutlarını öğrenin. Pratik kodlarla sisteminizi hemen hızlandırın.
cover: /img/arch-linux-terminal-komutlari/terminal.png
categories:
  - Linux
tags:
  - arch-linux
  - terminal
  - pacman
  - systemd
  - aur
  - linux-komutlari
draft: false
toc: false
---

# Arch Linux Terminal Komutları: Kapsamlı ve Pratik Rehber
---
![Pacman paket kaldırma ve Rns parametresi çıktısı](/img/arch-linux-terminal-komutlari/terminal.png "arch-linux-terminal-komutlari-pacman-paket-yonetimi")

---
**Arch Linux terminal komutları**, sisteminize tam hakimiyet kurmanızı sağlayan en temel ve vazgeçilmez araç takımıdır. Kullanıcıyı grafiksel kısıtlamalara mahkûm etmeyen ve doğrudan denetim yetkisi veren Arch Linux, komut satırı mimarisiyle öne çıkar. Birçok kullanıcı karmaşık komut dizilimleri ve sistem yönetimi karşısında çekinse de, temel kalıpları kavramak bu güçlü işletim sistemini zahmetsizce yönetmenizi sağlar. Bu kapsamlı rehberde; günlük işlerinizde ihtiyaç duyacağınız paket yönetiminden servis kontrollerine, sistem izlemeden dosya işlemlerine kadar en hayati **Arch Linux terminal komutları** derlemesini pratik örnekler ve tablolar eşliğinde bulacaksınız.

---
![Arch Linux terminal penceresinde pacman güncellemesi ve fastfetch çıktısı](/img/arch-linux-terminal-komutlari/ArchLinuxTerminal.png "arch-linux-terminal-komutlari-sistem-guncellemesi")

---

## Arch Linux Terminal Komutları Neden Bu Kadar Önemli?

Arch Linux, "Keep It Simple, Stupid" (KISS) prensibini benimseyen minimalist bir dağıtımdır. Diğer popüler [Linux dağıtımları]({{{< ref "linux-nedir-ve-populer-linux-dagitimlari" >}}) gibi arka planda otomatik çalışan onlarca grafik sihirbazı yerine, işletim sisteminin tüm kontrol mekanizmasını kullanıcıya bırakır. Bu kontrolün ana anahtarı ise doğrudan terminaldir.

Modern bir [Linux işletim sistemi]({{{< ref "linux-nedir-ve-populer-linux-dagitimlari" >}}) ortamında terminal yalnızca acil durum kurtarma aracı değil; yazılım yükleme, kernel parametrelerini düzenleme, depolama alanlarını bağlama ve servisleri denetleme merkezidir. Mobil ortamlarda aşina olduğumuz gelişmiş [Termux terminal]({{{< ref "termux-nedir-ne-ise-yarar-android-linux-rehberi" >}}) kültüründe olduğu gibi, Arch üzerinde de CLI (komut satırı arayüzü) hızlı, kararlı ve kaynak tasarruflu bir iş akışı sunar.

---

## Arch Linux Paket Yönetimi: Pacman ve AUR Komutları

Arch Linux ekosisteminin kalbinde C ile yazılmış son derece hızlı **Pacman** paket yöneticisi yer alır. Resmi depolardaki ikili (binary) paketlerin yanı sıra, topluluk tarafından geliştirilen Arch User Repository (AUR) üzerinden kaynak kodları derleyerek sisteme entegre edebilirsiniz.

Aşağıdaki tabloda günlük hayatta en sık başvurulan paket yönetimi komutları listelenmiştir:


| Komut                        | Açıklama                                                                                |
| :--------------------------- | :-------------------------------------------------------------------------------------- |
| `sudo pacman -Syu`           | Paket veritabanlarını eşitler ve tüm sistemi tamamen günceller.                         |
| `sudo pacman -S paket_adi`   | Resmi depolardan belirtilen paketi kurar.                                               |
| `sudo pacman -Rns paket_adi` | Paketi, artık kullanılmayan bağımlılıklarını ve ayar dosyalarını temizleyerek kaldırır. |
| `pacman -Ss arama_terimi`    | Resmi depolarda anahtar kelimeye göre paket arar.                                       |
| `pacman -Qi paket_adi`       | Sistemde kurulu olan bir paketin sürüm ve bağımlılık ayrıntılarını verir.               |
| `pacman -Qo /dosya/yolu`     | Belirtilen dosyanın sistemdeki hangi pakete ait olduğunu gösterir.                      |
| `pacman -Qdt`                | Sistemde yetim (artık ihtiyaç duyulmayan) kalmış bağımlılık paketlerini listeler.       |
| `paccache -r`                | Eski paket indirme önbelleğini temizleyerek disk alanı açar (pacman-contrib gerekir).   |
| `checkupdates`               | Sistemi henüz güncellemeden hangi paketlerin yeni sürümünün olduğunu listeler.          |
| `yay -S paket_adi`           | AUR yardımcısı (AUR helper) ile topluluk depolarından paket kurar.                      |
| `makepkg -si`                | `PKGBUILD` dosyasını derler, bağımlılıkları tamamlar ve paketi pacman ile kurar.        |

---

![/img/arch-linux-terminal-komutlari/kaldir.png "arch-linux-terminal-komutlari-pacman-paket-yonetimi"](/img/arch-linux-terminal-komutlari/kaldir.png "arch-linux-terminal-komutlari-pacman-paket-yonetimi")

---

## Sistem Bilgisi ve Donanım İzleme Terminal Komutları

Bir sorunu teşhis etmeden ya da yeni bir donanım yapılandırmadan önce sisteminizin o anki durumunu bilmek gerekir. Arch Linux terminal komutları sayesinde CPU frekansından PCI veri yollarına kadar her bileşeni anlık olarak izleyebilirsiniz:



| Komut              | Açıklama                                                                                 |
| :----------------- | :--------------------------------------------------------------------------------------- |
| `uname -a`         | Çekirdek sürümünü (kernel) ve mimari bilgisini listeler.                                 |
| `hostnamectl`      | Bilgisayar adı, kurulu çekirdek ve dağıtım kimliğini gösterir.                           |
| `uptime`           | Bilgisayarın ne kadar süredir açık olduğunu ve yük ortalamasını (load average) belirtir. |
| `lscpu`            | İşlemcinin mimarisini, çekirdek ve iş parçacığı sayısını, önbellek boyutunu döker.       |
| `free -h`:         | Kullanılan ve boşta kalan RAM ile Swap belleği anlaşılır (MB/GB) birimlerle gösterir.    |
| `lsblk`            | Takılı diskleri, depolama bölümlerini ve bağlama noktalarını ağaç yapısıyla sunar.       |
| `lspci` ve `lsusb` | Anakart üzerindeki PCI (ekran kartı, ses kartı vb.) ve USB aygıtlarını listeler.         |
|  `df -h`           | Bağlı disk bölümlerinin doluluk oranlarını ve kalan boş alanı gösterir.                  |
| `du -sh *`         | Bulunulan dizindeki her klasörün toplam disk tüketimini hesaplar.                        |
| `fastfetch`        | Dağıtım logosuyla birlikte şık ve özet bir sistem donanım kartı basar.                   |
| `dmesg \| tail`    | Çekirdek tarafından üretilen en son sistem ve donanım olay günlüklerini ekrana yazdırır. |

## Dosya Yönetimi ve Dizin Değiştirme Komutları

Linux dosya hiyerarşisinde güvenle gezinmek, dizin değiştirmek ve dosyaları manipüle etmek için temel çekirdek komutları eksiksiz bilinmelidir. Günlük iş akışında en çok kullanılan dosya ve dizin komutları aşağıdaki tabloda özetlenmiştir:

| Komut | Ne İşe Yarar? (Açıklama) |
| :--- | :--- |
| `ls -la` | Gizli dosyalar (`.` ile başlayanlar) dahil tüm dosya ve dizinleri izinleriyle listeler. |
| `cd /yol` | Belirtilen hedef dizine geçiş yapar (dizin değiştirir). |
| `pwd` | Şu an bulunulan aktif çalışma dizininin tam yolunu ekrana yazdırır. |
| `mkdir -p a/b/c` | Var olmayan üst klasörlerle birlikte iç içe dizin yapısını tek seferde oluşturur. |
| `touch dosya` | Yeni ve boş bir dosya oluşturur ya da mevcut dosyanın erişim tarihini günceller. |
| `cp -r kaynak hedef` | Dosya veya klasörleri tüm alt dizinleriyle birlikte kopyalar. |
| `mv eski yeni` | Dosya veya dizinleri başka konuma taşır ya da yeniden adlandırır. |
| `rm -rf dizin` | Belirtilen dizini ve altındaki tüm dosyaları kalıcı ve zorla siler. |
| `ln -s hedef kisayol` | Hedef dosya veya klasör için sembolik bağlantı (soft link) oluşturur. |
| `cat dosya` | Dosyanın tüm içeriğini doğrudan terminal ekranına yazdırır. |
| `less dosya` | Uzun metin dosyalarını sayfa sayfa, yukarı/aşağı kaydırarak okutur. |
| `tail -f dosya` | Günlük (log) dosyalarının son satırlarını canlı olarak ekrandan izler. |
| `find / -name "*.conf"` | Belirtilen dizinden başlayarak dosya adına göre derinlemesine arama yapar. |
| `plocate kelime` | Önceden indekslenmiş veritabanını kullanarak saniyeler içinde hızlı dosya arar. |
| `tree` | Bulunulan dizinin hiyerarşik yapısını dallı budaklı bir ağaç görünümünde listeler. |
| `nano dosya` / `vim dosya` | Dosyaları doğrudan terminal üzerinden düzenlemek için metin editörünü açar. |

---

## Kullanıcı İzinleri ve Süreç Denetimi

Arch Linux kurulumundan hemen sonra güvenlik gerekçesiyle kök hesap (`root`) yerine standart bir kullanıcı açılır ve yönetimsel görevler için yetkilendirme tanımlanır. Yetki yapılandırmalarında yaşanan aksaklıklarda [Kali Linux sudo rehberi]({{{< ref "kali-linux-root-hesabi-aktiflestirme-ve-sudo-problemi-cozumu" >}})nde olduğu gibi grup kontrolleri büyük önem taşır. Kullanıcı izinleri ve takılan süreçleri yönetmek için kullanılan temel komutlar şunlardır:

| Komut | Açıklama / Ne İşe Yarar? |
| :--- | :--- |
| `chmod 755 dosya` | Dosyanın okuma, yazma ve çalıştırma izinlerini sayısal modda yeniden tanımlar. |
| `sudo chown kullanici:grup dosya` | Dosya veya dizinin mülkiyetini belirtilen kullanıcı ve gruba devreder. |
| `whoami` / `id` | Aktif oturum açmış kullanıcı adını ve dahil olduğu grup kimliklerini (GID/UID) gösterir. |
| `sudo useradd -m -G wheel ad` | Ev dizinine sahip olan ve yönetici grubuna (`wheel`) dahil yeni bir kullanıcı açar. |
| `sudo passwd ad` | Belirtilen kullanıcı hesabı için yeni bir giriş parolası belirler. |
| `sudo usermod -aG grup ad` | Mevcut bir kullanıcıyı ikincil bir kullanıcı grubuna ekler. |
| `sudo userdel -r ad` | Kullanıcı hesabını ve bağlı ev dizinini sistemden kalıcı olarak siler. |
| `sudo visudo` | `sudoers` dosyasını sözdizimi denetimi yaparak güvenli bir şekilde düzenler. |
| `ps aux` | Sistemde arka planda ve ön planda çalışan tüm süreçleri anlık listeler. |
| `htop` / `top` | Süreçleri, CPU ve bellek tüketimlerini terminalde renkli ve canlı olarak izler. |
| `kill PID` | Belirtilen süreç kimlik numarasına (PID) sonlandırma sinyali gönderir. |
| `pkill surec_adi` | Kilitlenen veya yanıt vermeyen programları doğrudan işlem adıyla kapatır. |
| `nohup komut &` | Terminal penceresi kapansa dahi komutun arka planda çalışmasını sürdürür. |
| `lsof -i :80` | Belirtilen portu (ör. 80 HTTP) o anda hangi sürecin dinlediğini tespit eder. |

---

## Systemd ve Servis Yönetimi Komutları

Modern Linux mimarisinde servisleri ayağa kaldırmak, arka plan işlemlerini denetlemek ve sistem çökmelerini incelemek için `systemd` ve `journalctl` ikilisi kullanılır. Günlük sistem yönetiminde ihtiyaç duyulan başlıca komutlar şunlardır:

| Komut | Açıklama / Ne İşe Yarar? |
| :--- | :--- |
| `systemctl status servis_adi` | Belirtilen servisin o anki çalışma durumunu ve son günlük kayıtlarını gösterir. |
| `sudo systemctl enable --now servis_adi` | Servisi hemen başlatır ve sistem açılışında otomatik başlamasını sağlar. |
| `sudo systemctl disable --now servis_adi` | Servisi anında durdurur ve açılışta otomatik başlamasını devre dışı bırakır. |
| `sudo systemctl restart servis_adi` | Yapılandırma değişikliklerinden sonra servisi yeniden başlatır. |
| `systemctl --failed` | Başlatılamayan, çöken veya arızalı duruma düşen tüm servisleri listeler. |
| `journalctl -b` | Mevcut açılıştan (boot) itibaren toplanan tüm sistem günlüklerini gösterir. |
| `journalctl -u servis_adi -f` | Belirli bir servise ait günlük akışını canlı ve anlık olarak takip eder. |
| `journalctl -p 3 -xb` | Mevcut açılıştaki kritik hata düzeyine (level 3 err) sahip olayları ayıklar. |

Özellikle sistem önyüklemesinde aksama yaşandığında `journalctl -p 3 -xb` komutu arızalı sürücüyü veya donanım/servis hatasını doğrudan gün yüzüne çıkarır.

---

## Ağ Yapılandırması ve Disk İşlemleri

İnternet bağlantısını kurmak, portları denetlemek, veri transferi yapmak ve disk bölümlerini bağlamak için kullanılan temel komutlar şunlardır:

| Komut | Açıklama / Ne İşe Yarar? |
| :--- | :--- |
| `ip a` | Sistemdeki tüm aktif ağ arayüzlerini ve atanmış IP adreslerini listeler. |
| `ping -c 4 archlinux.org` | DNS çözümlemesini ve internet erişim kalitesini 4 paket göndererek test eder. |
| `nmcli device wifi list` | Çevrede bulunan tüm Wi-Fi ağlarını ve sinyal güçlerini listeler. |
| `nmcli device wifi connect "AG_ADI" password "PAROLA"` | Terminalden belirtilen kablosuz ağa güvenli şekilde bağlanır. |
| `ss -tulpn` | Sistemde dinlenen açık portları ve bu portları kullanan servis süreçlerini listeler. |
| `curl -O url` / `wget url` | Uzak sunucudan belirtilen dosya bağlantısını doğrudan bilgisayara indirir. |
| `ssh kullanici@sunucu` | Uzaktaki bir Linux sunucusuna terminal üzerinden şifreli uzaktan erişim sağlar. |
| `tar -xzf arsiv.tar.gz` | Sıkıştırılmış `.tar.gz` arşiv dosyalarını bulunulan dizine açar. |
| `sudo mount /dev/sdb1 /mnt` | Belirtilen disk bölümünü sistemdeki bir dizine erişim için bağlar. |
| `sudo mkinitcpio -P` | Çekirdek güncellemeleri sonrası tüm kurulu kernel kalıpları için initramfs üretir. |
| `sudo grub-mkconfig -o /boot/grub/grub.cfg` | GRUB önyükleyici yapılandırma dosyasını yeniden tarayıp günceller. |

---

## Sıkça Sorulan Sorular (SSS)

### Arch Linux terminal komutları öğrenmek zor mu?
Arch Linux terminal komutları temel mantık kavrandığında son derece kolaydır. Pacman komutlarının tutarlı parametre yapısı (`-S` yükle, `-R` sil, `-Q` sorgula) ve systemd standartları sayesinde günlük kullanım birkaç gün içinde tamamen refleks haline gelir.

### Pacman önbelleği nasıl güvenli bir şekilde temizlenir?
Pacman indirilen paketleri `/var/cache/pacman/pkg/` dizininde depolar. Bu dizini güvenle temizlemek için `pacman-contrib` paketiyle gelen `paccache -r` komutu çalıştırılmalıdır. Bu komut geriye dönük kurtarma için en son sürümleri tutarak eski paket kalıntılarını siler.

### Arch Linux'ta AUR paketleri pacman ile doğrudan kurulabilir mi?
Hayır, Pacman doğrudan AUR depolarını tarayamaz veya derleyemez. AUR paketleri `makepkg -si` komutuyla kaynak kod üzerinden manuel olarak ya da `yay` ve `paru` gibi topluluk tarafından geliştirilen AUR yardımcıları kullanılarak otomatik biçimde sisteme yüklenir.

### Arch Linux sistem güncellemeleri ne sıklıkla yapılmalıdır?
Arch Linux sürekli güncellenen (rolling-release) bir yapıya sahip olduğundan, haftada en az bir veya iki kez `sudo pacman -Syu` komutunu çalıştırmanız önerilir. Güncelleme öncesinde kritik paket değişiklikleri için Arch Linux resmi duyurularına göz atmak kararlılık açısından faydalıdır.

## İlgili Yazılar

- [Linux dağıtımları ve Arch Linux konumu]({{{< ref "linux-nedir-ve-populer-linux-dagitimlari" >}})
- [Debian tabanlı Kali Linux ve paket yönetimi]({{{< ref "kali-linux-nedir-ve-ikinci-isletim-sistemi-kurulumu" >}})
- [Android'de Linux terminal (Termux)]({{{< ref "termux-nedir-ne-ise-yarar-android-linux-rehberi" >}})
- [VirtualBox'ta Arch Linux test ortamı]({{{< ref "sanal-makine-nedir-nasil-kurulur-virtualbox-rehberi" >}})
