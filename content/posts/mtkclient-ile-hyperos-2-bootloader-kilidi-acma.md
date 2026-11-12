---
title: MTKClient ile HyperOS 2 Bootloader Kilidi Açma ve RPMB Çözümü
date: 2026-11-02
slug: mtkclient-ile-hyperos-2-bootloader-kilidi-acma
description: MediaTek işlemcili cihazlarda MTKClient ve RPMB magic silme yöntemiyle HyperOS 2 bootloader kilidi açma ve Arch Linux kurulum rehberi.
cover: /img/mtkclient-ile-hyperos-2-bootloader-kilidi-acma/mtkclient.jpg
categories:
  - Linux
tags:
  - mtkclient
  - hyperos-2
  - bootloader
  - rpmb
  - mediatek
  - arch-linux
  - android
draft: false
toc: false
---

# MTKClient ile HyperOS 2 Bootloader Kilidi Açma ve RPMB Çözümü

MediaTek işlemcili telefonlarda yeni nesil HyperOS 2 sürümleriyle birlikte gelen RPMB kilitleri ve seccfg engellerini aşarak bootloader kilidini açmak, geleneksel resmi yöntemlerin yetersiz kaldığı durumlarda kritik bir çözümdür. Bu kapsamlı rehberde, MTKClient aracını kullanarak Arch Linux ortamında BROM modunda güvenli bootloader kilidi açma işlemlerini, RPMB yedeği almayı ve magic string silme adımlarını tüm detaylarıyla inceleyeceğiz.

## MediaTek Cihazlarda Bootloader Kilidi ve Riskler

MediaTek tabanlı akıllı telefonlarda bootloader açma işlemi mümkündür ancak dikkat edilmesi gereken ciddi riskler barındırır. İşlem sonucunda cihazdaki tüm veriler fabrika ayarlarına döner (factory reset gibi silinir), cihazda brick (açılmama) riski oluşur ve cihaz garanti dışı kalır. Bu nedenle öncelikle üreticinin resmi yöntemi (örneğin Xiaomi için Mi Unlock) mevcutsa öncelikle o denenmelidir. HyperOS ve yeni MIUI sürümlerinde ek güvenlik katmanları (RPMB vb.) kullanıcıların karşısına çıkmaktadır.

### Önemli Ön Hazırlıklar
* Tüm verilerinizi yedekleyin, işlem sırasında cihaz tamamen sıfırlanacaktır.
* İşlem kararlılığı için USB 2.0 portu tercih edin (USB 3.0 bazen el sıkışma hatalarına yol açabilir).
* Yalnızca şarj kablosu değil, yüksek kaliteli ve veri aktarımını destekleyen bir data kablosu kullanın.
* Cihazı tamamen kapatıp BROM moduna alma adımlarına dikkat edin.

## Arch Linux Üzerinde MTKClient Kurulumu

İşlemlerin kararlılığı açısından Windows yerine Linux tabanlı sistemler (özellikle Arch Linux) struct.error gibi Python hatalarının önüne geçmek için idealdir. Terminal üzerinden gerekli paketleri kurarak başlayalım:

```bash
sudo pacman -Syu
sudo pacman -S python python-pip git libusb fuse2 base-devel
```

Sistem genelini kirletmemek için sanal çevre (`venv`) oluşturup etkinleştirin:

```bash
python -m venv ~/.venv-mtk
source ~/.venv-mtk/bin/activate
```

Ardından MTKClient deposunu klonlayıp gerekli Python bağımlılıklarını kurun:

```bash
cd ~
git clone https://github.com/bkerler/mtkclient --recursive
cd mtkclient
pip install -r requirements.txt
pip install .
```

udev kurallarını yükleyerek kullanıcı grubunuzu yetkilendirin:

```bash
sudo usermod -aG plugdev,dialout $USER
sudo cp ./Setup/Linux/51-edl.rules /etc/udev/rules.d/
sudo cp ./Setup/Linux/52-mtk.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules
sudo udevadm trigger
```

Değişikliklerin aktif olması için oturumu kapatıp yeniden açın veya bilgisayarı yeniden başlatın.

*Görsel: MTKClient ile MediaTek cihaz bağlantı şeması ve BROM modu.*

## Telefonu BROM Moduna Alma Adımları

HyperOS 2 ve güncel sürümlerde cihazı BROM moduna almak en kritik aşamadır. Doğru sıra şu şekildedir:

1. Telefonu tamamen kapatın (Power tuşuna 15 saniye basılı tutun, logo kaybolduktan sonra 5 saniye bekleyin).
2. Terminalde komutu hazırlayın: `python mtk.py printgpt`
3. Ses Açma (Volume Up) ve Ses Kısma (Volume Down) tuşlarına aynı anda basılı tutun.
4. Tuşları basılı tutmaya devam ederken USB kabloyu bilgisayara takın.
5. Cihaz algılandığında tuşları serbest bırakın.

## HyperOS 2 için RPMB Magic Silme ve Unlock İşlemi

HyperOS 2’de standart `seccfg unlock` komutu tek başına yeterli olmaz; Xiaomi RPMB alanına ek kilit koyar. Bu yüzden sırasıyla şu adımlar izlenmelidir:

### Adım 1: RPMB Yedeği Alma
Asla atlanmaması gereken bu adımda cihazın şifreli bellek alanı yedeklenir:
```bash
python mtk.py da rpmb r rpmb_backup.bin
```

### Adım 2: Magic String Tespiti ve Sektör Hesabı
```bash
grep -boa "Jz8PNRUF" rpmb_backup.bin
```
Çıkan bayt değerini 256'ya bölerek silinecek sektörü hesaplayın (Örn: 14680064 / 256 = 57344).

### Adım 3: RPMB Magic Silme ve Bootloader Kilidi
```bash
python mtk.py da rpmb e --sector 57344 --sectors 4
```
Bu işlemden sonra telefonu yeniden BROM moduna alarak seccfg kilidini kaldırın:
```bash
python mtk.py da seccfg unlock
python mtk.py e metadata,userdata,md_udc
python mtk.py reset
```

Cihaz açıldığında sarı renkli "The bootloader is unlocked" uyarısını göreceksiniz. Kali Linux veya benzeri araçlarla doğrulama yapmak için Fastboot moduna geçip `fastboot getvar unlocked` komutunu çalıştırabilirsiniz.

## Sıkça Sorulan Sorular (SSS)

### HyperOS 2'de normal seccfg unlock neden yetersiz kalıyor?
Xiaomi ve diğer üreticiler, HyperOS 2 ile birlikte RPMB (Replay Protected Memory Block) adı verilen donanımsal korumalı bellek alanına ek kilitler yerleştirmiştir. Sadece seccfg baytlarını değiştirmek kilit durumunu kalıcı olarak değiştiremediğinden, RPMB magic string verisinin de temizlenmesi şarttır.

### İşlem sırasında veri kaybı yaşanır mı?
Evet, bootloader kilidini açma işlemi tıpkı fabrika ayarlarına sıfırlama (factory reset) gibidir. Cihazdaki tüm fotoğraflar, uygulamalar ve kişisel veriler silinir. Bu nedenle işlem öncesinde mutlaka harici bir yedek alınmalıdır.

### Neden Windows yerine Linux tercih edilmelidir?
RPMB yedeği ve manipülasyon işlemlerinde Windows üzerinde `struct.error` gibi Python kütüphane çakışmaları ve sürücü sorunları sıkça görülmektedir. Arch Linux ve benzeri dağıtımlar, libusb entegrasyonu ve kararlı Python ortamı sayesinde süreci çok daha hatasız tamamlamanızı sağlar.

### Brick riskine karşı ne yapılmalıdır?
İşlem sırasında orijinal data kablosu kullanmak, USB 2.0 port tercih etmek ve RPMB yedeğini (`rpmb_backup.bin`) güvenli bir yerde saklamak hayati önem taşır. Olası bir brick durumunda SP Flash Tool ve scatter dosyaları ile kurtarma yapılması gerekebilir.

---
