---
title: Kali Linux Grub Loading Please Wait Error 22 Hatası ve Kesin Çözümü
date: 2026-10-29
slug: kali-linux-grub-loading-error-22-cozumu
description: Kali Linux kaldırıldıktan sonra karşılaşılan Grub loading please wait Error 22 hatasının Windows kurulum USB'si ile adım adım kesin çözüm rehberi.
cover: /img/kali-linux-grub-loading-error-22-cozumu/image.png
categories:
  - Pratik Cozumler
  - Siber Guvenlik
tags:
  - grub
  - error-22
  - dual-boot
  - bootrec
  - mbr
  - windows
  - linux
draft: false
toc: false
---

# Kali Linux Grub Loading Please Wait Error 22 Hatası ve Kesin Çözümü

Bilgisayarınızda **Dual-Boot** (Windows ve Kali Linux yan yana) sistemi kuruluysa ve Linux tarafını doğrudan Windows üzerinden diski biçimlendirerek kaldırdıysanız, muhtemelen yeniden başlattığınızda siyah bir ekranda **"Grub loading please wait Error 22"** hatasıyla karşılaştınız. Bu ekranda sistem kilitlenir ve hiçbir tuş kombinasyonuyla geçiş yapamazsınız. Bu rehberimizde bu hatanın nedenini ve Windows kurulum flash belleği kullanarak nasıl saniyeler içinde çözebileceğinizi anlatıyoruz.

---

## 🛠️ "Grub loading please wait Error 22" Hatası Neden Olur?

Bilgisayarlarda işletim sistemlerinin açılışını yöneten birincil önyükleme yöneticileri bulunur. Linux dağıtımları (Kali Linux dahil) kurulurken **GRUB** (Grand Unified Bootloader) yöneticisini diskin **MBR** (Master Boot Record) veya EFI bölümüne yazar. 

Siz Kali Linux'u düzgün bir şekilde (GRUB rescue veya boot loader temizliği yapmadan) direkt Windows Disk Yönetimi üzerinden silip biçimlendirdiğinizde, MBR hala silinen Linux dosyalarını aramaya devam eder. Bulamadığında ise **Error 22** hatası fırlatarak açılışı durdurur.

---

##  Adım Adım Hata Çözüm Rehberi

Bu sinir bozucu ekrandan kurtulmak ve bilgisayarınızı tekrar normal şekilde açabilmek için elinizde bir **Windows kurulum USB'si** (Windows 7, 8, 10 veya 11 fark etmez) olması yeterlidir.

### 1. Adım: Bilgisayarı Kurulum Medyası ile Başlatın
1. Hazırladığınız Windows kurulum USB belleğini bilgisayarınıza takın.
2. Bilgisayarı yeniden başlatarak Boot Menu (F12, F11, F8 veya Esc tuşlarıyla) üzerinden USB belleği seçin.
3. Windows kurulum ilk ekranı karşınıza geldiğinde korkmayın, kurulum yapmayacağız.

### 2. Adım: Komut İstemi (CMD) Ekranını Açın
1. Kurulum dili seçim ekranında veya hemen sonrasındaki "Şimdi Yükle" penceresinde klavyenizden **`Shift + 10`** tuşlarına basın.
2. Bu işlem sonucunda karşınıza siyah renkli **Komut İstemi (CMD)** penceresi açılacaktır.
![](/img/kali-linux-grub-loading-error-22-cozumu/image1.png)
### 3. Adım: MBR Tablosunu Onarın ve GRUB Kalıntılarını Temizleyin
Açılan siyah komut satırına sırasıyla şu iki kritik komutu yazın ve her birinden sonra Enter tuşuna basın:

```cmd
bootrec /fixmbr
```

```cmd
bootrec /fixboot
```

> **Not:** Bu komutlar, diskin ana önyükleme kaydını (MBR) onararak silinen GRUB kalıntılarını temizler ve doğrudan Windows önyükleyicisine geri döner.

### 4. Adım: Sistemi Yeniden Başlatın
İşlemler başarıyla tamamlandıktan sonra USB belleği bilgisayarınızdan çıkarın ve komut penceresine `exit` yazarak kapatın. Bilgisayarınızı yeniden başlattığınızda hatanın ortadan kalktığını ve doğrudan Windows'un açıldığını göreceksiniz.

---
