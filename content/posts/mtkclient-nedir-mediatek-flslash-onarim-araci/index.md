---
title: MTKClient Nedir? MediaTek Cihazlar İçin Flaş, Onarım ve Kilit Açma Rehberi
slug: mtkclient-nedir-mediatek-flslash-onarim-araci
description: MediaTek işlemcili Android cihazlarda yazılım yükleme, bootloader
  kilidi açma ve brick olmuş telefonları kurtarma imkanı sunan güçlü araç
  MTKClient rehberi.
date: 2026-10-19
draft: false
toc: false
cover: mtkclient-nedir-mediatek-flslash-onarim-araci/mtk.png
categories:
  - 🐧 Linux
tags:
  - mtkclient
  - mediatek
  - android
  - root
  - rom
  - unbrick
  - acik-kaynak
---

# MTKClient Nedir? MediaTek Cihazlar İçin Flaş, Onarım ve Kilit Açma Rehberi

Android akıllı telefon ve tablet dünyasında özelleştirme, ROM atma ve yazılım kurtarma işlemleri her zaman heyecan verici ancak bir o kadar da riskli olmuştur. Özellikle **MediaTek (MTK)** işlemcili cihazlarda yanlış bir işlem yapmak, cihazın hiç açılmamasına (bricked / tuğla olmasın) yol açabilir. İşte tam bu noktada, geliştirici *bkerler* tarafından hayata geçirilen **MTKClient**, düşük seviyeli (low-level) erişim sağlayarak bu zorlukların üstesinden gelen en güçlü açık kaynaklı araç olarak karşımıza çıkıyor.

Peki **MTKClient nedir**, hangi özellikleri sunar, Linux ve Windows üzerinde nasıl kurulur? Bu kapsamlı rehberde MediaTek cihaz yönetiminin kapılarını aralıyoruz.

---

## MTKClient Nedir ve Ne İşe Yarar?

**MTKClient**, MediaTek işlemcilerle donatılmış akıllı telefon ve tabletlerde BROM (Read-Only Memory) modunu kullanarak doğrudan donanımsal düzeyde iletişim kuran açık kaynaklı bir flaş, yedekleme ve onarım aracıdır.

Piyasadaki pek çok ticari veya kapalı kaynaklı aracın aksine MTKClient tamamen özgürdür ve özel Download Agent (DA) dosyalarına ihtiyaç duymaz. Araç sayesinde yapabileceğiniz başlıca işlemler şunlardır:

* **Firmware Yükleme (Flaşlama):** Cihazınıza resmi (stock) veya özel (custom) yazılımları güvenle yükleyebilirsiniz.
* **Bölüm Yönetimi (Partition Backup/Dump):** Cihazınızın flash hafızasındaki tüm bölümleri yedekleyebilir veya olası bir çökmeye karşı geri yükleyebilirsiniz.
* **Bootloader Kilidi Açma:** Desteklenen MTK modellerinde önyükleyici (bootloader) kilidini kaldırabilirsiniz.
* **Brick Olmuş Cihazları Kurtarma:** Yazılımsal olarak kilitlenmiş, açılmayan veya logo ekranında kalan cihazları BROM veya V6 önyükleyici modları aracılığıyla hayata döndürebilirsiniz.

---

## MTKClient'ın Öne Çıkan Temel Özellikleri

### 1. Çapraz Platform Desteği
Windows, Linux ve macOS işletim sistemlerinde çalışabilen MTKClient, USB sürücü desteği ve kararlılığı nedeniyle özellikle **Linux (Ubuntu önerilir)** ortamında kusursuz bir performans sunar.

### 2. Güvenli Önyükleme (Secure Boot) Bypass
Güvenli önyükleme mekanizmasına sahip modern MediaTek yonga setlerinde bile özel anahtarlara ihtiyaç duymadan düşük seviyeli erişim sağlayarak kilitleri aşmanıza olanak tanır.

### 3. V6 Protokol ve Yeni Nesil Yonga Setleri Desteği
MT6781, MT6789, MT6855, MT6886, MT6895, MT6983 ve MT8985 gibi V6 protokolünü kullanan yeni nesil yonga setlerinde önyükleyici yamalama ve `--loader` parametresiyle gelişmiş kurtarma operasyonları gerçekleştirilebilir.

---

## MTKClient Nasıl Kurulur? (Linux / Ubuntu Rehberi)

MTKClient'ı kurmak ve çalıştırmak için sisteminizde Python (3.10 veya üzeri) ve Git kurulu olmalıdır. Ubuntu tabanlı bir sistemde adım adım kurulum süreci şu şekildedir:

### Adım 1: Bağımlılıkların Yüklenmesi
```shell
sudo apt install git build-essential curl libssl-dev python3-pip -y
```

### Adım 2: MTKClient Deposunu Klonlama
```shell
git clone https://github.com/bkerler/mtkclient --recursive
cd mtkclient
```

### Adım 3: Udev Kurallarının Ayarlanması
Cihazınızın bilgisayar tarafından doğru tanınması için udev kurallarını kopyalayın:
```shell
sudo cp Setup/Linux/*.rules /etc/udev/rules.d/
sudo udevadm control -R && sudo udevadm trigger
sudo usermod -aG dialout $USER && sudo usermod -aG plugdev $USER
```
*(Not: Bu adımlardan sonra bilgisayarınızı yeniden başlatmanız gerekebilir.)*

### Adım 4: Gereksinimlerin Yüklenmesi (Pip veya UV ile)
```shell
pip3 install -r requirements.txt
```
Veya modern `uv` paket yöneticisini tercih ediyorsanız:
```shell
uv sync --frozen
```

---

## MTKClient ile Cihaz Bağlantısı (BROM Modu)

Aracı çalıştırmak ve telefonunuzla iletişim kurmak için şu adımları izlemelisiniz:
1. Telefonunuzu tamamen kapatın.
2. Cihazın modeline bağlı olarak **Ses Açma + Güç** veya **Ses Kısma + Güç** tuşlarına basılı tutun.
3. USB kablosunu bilgisayara bağlayın.
4. MTKClient cihazı algıladığında tuşları bırakabilirsiniz.
*(Not: V6 protokolü kullanan yeni cihazlarda donanım tuşlarına basmadan doğrudan kablo bağlantısı kurarak veya `adb reboot edl` komutuyla önyükleyici moduna geçiş yapabilirsiniz.)*

---

## Neden MTKClient Kullanmalısınız?

MediaTek işlemcili bir Android cihaza sahipseniz ve geliştirici dünyasının sınırlarını zorlamak istiyorsanız, MTKClient çantanızda bulunması gereken en kritik araçtır. Üretici kilitlerini açmak, tam yedek almak (dump) veya yazılımsal hatalar nedeniyle kullanılamaz hale gelen telefonunuzu kurtarmak için tamamen açık kaynaklı, güvenilir ve güçlü bir çözümdür.

---
## Bağlantılar

[**MtkClient Github**](https://github.com/bkerler/mtkclient)

---
