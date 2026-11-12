---
title: Kali Linux Root Hesabı Aktifleştirme ve Sudo Problemi Çözüm Rehberi
date: 2026-11-05
slug: kali-linux-root-hesabi-aktiflestirme-ve-sudo-problemi-cozumu
description: Kali Linux üzerinde her komutta sudo yazma zorunluluğunu ortadan kaldırmak için root hesabını aktif etme ve şifre belirleme rehberi.
cover: /img/kali-linux-root-hesabi-aktiflestirme-ve-sudo-problemi-cozumu/Ekran.png
categories:
  - Siber Güvenlik
tags:
  - kali-linux
  - root
  - sudo
  - sudo
  - sudo
draft: false
toc: false
---

# Kali Linux Root Hesabı Aktifleştirme ve Sudo Problemi Çözüm Rehberi

Linux tabanlı işletim sistemlerinde **Root**, sistem üzerindeki her şeye sınırsız erişim hakkına sahip olan en yetkili kullanıcıdır. Kali Linux 2020.1 sürümünden itibaren güvenlik politikaları gereği root kullanıcısı varsayılan olarak şifresiz veya kurulumda ayarlanmamış gelmektedir. Bu durum, günlük kullanımda `ifconfig` gibi basit komutları çalıştırmak için bile sürekli `sudo` komutu kullanmanızı gerektirir. Bu yazımızda bu durumdan kurtulmak için root hesabını nasıl aktif edeceğinizi anlatacağız.

---

## Root Hesabı ve Sudo Zorunluluğu

Kali Linux'u standart bir kullanıcıyla kurduğunuzda, en temel sistem komutlarında bile yönetici yetkisi (`sudo`) ve kullanıcı şifrenizi girmeniz gerekir. Bir süre sonra bu durum pratik çalışmayı yavaşlatabilir. Doğrudan Root kullanıcısı ile oturum açarak tüm komutları yetki sınırlaması olmadan çalıştırmak mümkündür.

---

## Root Hesabını Aktif Etme Adımları

![](/img/kali-linux-root-hesabi-aktiflestirme-ve-sudo-problemi-cozumu/image.png)

Root hesabına şifre tanımlamak ve doğrudan root ile oturum açmak için şu adımları izleyin:

1. **Şifre Belirleme Komutu:** Terminali açın ve şu komutu girin:
   ```bash
   sudo passwd root
   ```
2. **Kullanıcı Şifresi:** `sudo` yetkisi kullandığınız için sistem sizden mevcut kullanıcı şifrenizi isteyecektir (güvenlik nedeniyle şifre karakterleri ekranda görünmez).
3. **Root Şifresi Belirleme:** Şifre doğrulandıktan sonra yeni root hesabınız için güçlü bir parola belirleyin ve onaylayın.
4. **Root ile Oturum Açma:** İşlem tamamlandıktan sonra oturumu kapatıp kullanıcı değiştir bölümünden **root** kullanıcı adıyla ve belirlediğiniz şifreyle giriş yapabilirsiniz.

Artık komut çalıştırmak için `sudo` yazmanıza gerek kalmadan sistemde tam yetkiye sahip olabilirsiniz.
