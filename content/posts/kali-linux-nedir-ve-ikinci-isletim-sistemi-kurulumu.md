---
title: Kali Linux Nedir? İkinci İşletim Sistemi (Dual Boot) Olarak Kurulum Rehberi
date: 2026-11-03
slug: kali-linux-nedir-ve-ikinci-isletim-sistemi-kurulumu
description: Kali Linux işletim sisteminin tanımı ve Windows yanına ikinci işletim sistemi (Dual Boot) olarak adım adım kurulum rehberi.
cover: /img/kali-linux-nedir-ve-ikinci-isletim-sistemi-kurulumu/kali-linux.jpg
categories:
  - Siber Güvenlik
tags:
  - kali-linux
  - dual-boot
  - isletim-sistemi
  - kurulum
  - siber-guvenlik
draft: false
toc: false
---

# Kali Linux Nedir? İkinci İşletim Sistemi (Dual Boot) Olarak Kurulum Rehberi

Siber güvenlik uzmanları, penetrasyon testerlar ve yazılım geliştiriciler tarafından aktif olarak kullanılan **Kali Linux**, Debian tabanlı güçlü bir güvenlik kontrol işletim sistemidir. 2013 yılında BackTrack'in yerini alan bu dağıtım, sızma testleri ve tersine mühendislik için yüzlerce araç barındırır. Bu yazımızda Kali Linux'un ne işe yaradığını inceleyecek ve bilgisayarınıza ikinci işletim sistemi (Dual Boot) olarak nasıl kuracağınızı öğreneceğiz.

---

## Kali Linux Ne İşe Yarar? Başlıca Özellikleri

Kali Linux, profesyonel güvenlik denetimleri için tasarlanmış açık kaynaklı bir platformdur. Öne çıkan özellikleri şunlardır:
- **600+ Test Aracı:** Güvenlik testleri ve ağ analizleri için hazır araçlar.
- **Tamamen Ücretsiz:** Offensive Security tarafından geliştirilen sistem hep ücretsiz kalacaktır.
- **Açık Kaynak ve Özelleştirilebilirlik:** Kaynak kodları açık olup kullanıcı isteklerine göre şekillendirilebilir.
- **Çoklu Dil Desteği:** Türkçe dahil olmak üzere çoklu dil desteği sunar.
- **Kablosuz Donanım Uyumluluğu:** Wi-Fi ve kablosuz adaptörler için en geniş Linux desteğine sahiptir.

---

## Kali Linux İkinci İşletim Sistemi (Dual Boot) Olarak Nasıl Kurulur?

Kali Linux'u tam performansla kullanmak ve ana işletim sisteminizin (Windows) yanına kurmak için şu adımları takip edebilirsiniz:

1. **ISO İndirme ve Flash Yazdırma:** Resmi siteden Kali ISO dosyasını indirin ve bir USB bellek üzerine yazdırın.
2. **Disk Alanı Ayırma:** Windows disk yönetimi (`Arama -> Disk Yönetimi`) üzerinden Kali Linux için en az **50 GB** boş alan ayırın (birimi küçült).
3. **Boot Menüsü:** Hazırladığınız USB belleği bilgisayara takın ve bilgisayar açılırken Boot tuşuna (F12, F2 veya Del - marka modele göre değişir) basarak önyükleme önceliğini USB sürücüye verin.
4. **Kurulum Adımları:** Kurulum ekranında dil, saat ve klavye ayarlarınızı yapın. Kullanıcı adı ve parolanızı belirledikten sonra disk bölümleme aşamasında ayrılan boş alanı yapılandırarak kurulumu tamamlayın.
