---
title: Kali Linux Paket Bulunamadı Hatası ve Kesin Sources.list Çözümü
date: 2026-11-02
slug: kali-linux-paket-bulunamadi-hatasi-ve-sources-list-cozumu
description: Kali Linux üzerinde paket yükleme ve güncelleme yaparken yaşanan 'paket bulunamadı' hatasının sources.list dosyası ile kesin çözüm rehberi.
cover: /img/kali-linux-paket-bulunamadi-hatasi-ve-sources-list-cozumu/image.png
categories:
  - Siber Guvenlik
tags:
  - kali-linux
  - apt
  - sources-list
  - paket-bulunamadi
  - hata-cozumu
draft: false
toc: false
---

# Kali Linux Paket Bulunamadı Hatası ve Kesin Sources.list Çözümü

Kali Linux kullanıcılarının kurulum sonrasında en sık karşılaştığı sorunlardan biri, paket yüklemek veya sistemi güncellemek istediğinde alınan **"paket bulunamadı"** hatasıdır. Çeşitli forumlarda farklı öneriler yer alsa da sorunun temel kaynağı yazılım depo adreslerinin (sources.list) pasif gelmesidir. Bu yazımızda bu hatanın nedenini ve kalıcı çözümünü inceleyeceğiz.

---

## Hatanın Nedeni Nedir?

Kali Linux ilk kurulduğunda, paket yöneticisinin (APT) yazılım indireceği resmi depolar (`sources.list`) güvenlik veya varsayılan yapılandırma gereği pasif (`#` işaretiyle devre dışı bırakılmış) olarak gelir. Depolar pasif olduğunda sistem yeni paketleri sorgulayamaz ve güncelleme yapamaz.

---

## Paket Bulunamadı Hatası Kesin Çözüm Adımları

Bu sorunu çözmek ve depoları aktif hale getirmek için terminal üzerinde şu adımları izleyin:

### 1. Sources.list Dosyasını Açma
Terminali açın ve metin düzenleyici ile konfigürasyon dosyasını açın:
```bash
sudo mousepad /etc/apt/sources.list
```

### 2. Depoları Aktifleştirme
Dosya içerisinde şu satırları göreceksiniz:
```text
#deb http://http.kali.org/kali kali-rolling main contrib non-free
#deb-src http://http.kali.org/kali kali-rolling main contrib non-free
```
Bu satırların başında bulunan **`#`** işaretlerini silerek satırları aktif hale getirin:
```text
deb http://http.kali.org/kali kali-rolling main contrib non-free
deb-src http://http.kali.org/kali kali-rolling main contrib non-free
```
Değişiklikleri yaptıktan sonra dosyayı **kaydedip** kapatın.

![](/img/kali-linux-paket-bulunamadi-hatasi-ve-sources-list-cozumu/image1.png)
### 3. Sistemi Güncelleme
Depolar aktif hale geldikten sonra paket listesini ve sistem uygulamalarını güncelleyin:
```bash
sudo apt-get update
sudo apt-get upgrade
```

Bu işlemlerin ardından paket bulunamadı hatası ortadan kalkacak ve sisteminiz sorunsuz güncellenecektir.
