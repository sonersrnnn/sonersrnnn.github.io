---
title: Kali Linux Sanal Makineye Nasıl Kurulur? VirtualBox Adım Adım Kurulum Rehberi
date: 2026-11-02
slug: kali-linux-sanal-makineye-nasil-kurulur-virtualbox-rehberi
description: Kali Linux siber güvenlik işletim sistemini Oracle VM VirtualBox kullanarak sanal makineye adım adım nasıl kuracağınızı öğrenin.
cover: /img/kali-linux-sanal-makineye-nasil-kurulur-virtualbox-rehberi/kali-linux.jpg
categories:
  - Siber Güvenlik
tags:
  - kali-linux
  - virtualbox
  - sanal-makine
  - kurulum
  - siber-guvenlik
draft: false
toc: false
---

# Kali Linux Sanal Makineye Nasıl Kurulur? VirtualBox Adım Adım Kurulum Rehberi

Siber güvenlik dünyasında sızma testleri (penetration testing) ve güvenlik denetimleri denildiğinde akla ilk gelen işletim sistemi **Kali Linux**'tur. 2013 yılında BackTrack'in yerini alan, Debian tabanlı bu güçlü dağıtım; 600'den fazla sızma testi aracı, ücretsiz ve açık kaynak yapısı ile siber güvenlik uzmanlarının vazgeçilmezidir. Bu rehberimizde, Kali Linux'u ana sisteminize zarar vermeden test edebilmeniz için **VirtualBox** ile sanal makineye nasıl kuracağınızı inceleyeceğiz.

---

## Kali Linux Nedir ve Ne İşe Yarar?

Kali Linux; profesyonel penetrasyon testleri, güvenlik araştırmaları ve tersine mühendislik için gerekli tüm yazılımlarla donatılmış özel bir Linux dağıtımıdır. Başlıca özellikleri şunlardır:
- **600+ Test Aracı:** Ağ analizi, parola kırma ve güvenlik denetimleri için zengin araç koleksiyonu.
- **Tamamen Ücretsiz ve Açık Kaynak:** Offensive Security tarafından geliştirilen sistem tamamen ücretsizdir ve kaynak kodları açıktır.
- **Kişiselleştirilebilirlik ve Donanım Desteği:** Çoklu dil (Türkçe dahil) ve geniş kablosuz ağ aygıtı desteği sunar.

---

## VirtualBox ile Adım Adım Kali Linux Kurulumu

Kali Linux'u sanal makinede çalıştırmak için öncelikle bir sanallaştırma yazılımına ve ISO dosyasına ihtiyacımız var.

### 1. Hazırlık Aşaması
- Resmi web sitesinden **Kali Linux ISO** dosyasını indirin.
- **Oracle VM VirtualBox** programını indirip bilgisayarınıza kurun.

### 2. Sanal Makine Oluşturma
1. VirtualBox'ı çalıştırın ve **"Yeni"** butonuna tıklayın.
2. Sanal makine adını belirleyin, işletim sistemi olarak Linux ve Debian sürümünü seçin.
3. RAM (bellek) boyutunu sistem kaynaklarınıza göre ayarlayın.
4. Sanal sabit disk boyutunu belirleyin (örneğin 20 GB veya üzeri) ve sihirbazı tamamlayın.

### 3. ISO Dosyasını Bağlama ve Kurulum
1. Oluşturduğunuz sanal makineyi başlatın ve ISO dosyasını seçmenizi isteyen ekrandan indirdiğiniz Kali ISO'sunu gösterin.
2. Açılış menüsünden **Graphical install** seçeneğini seçerek Enter tuşuna basın.
3. Kurulum dilini (Türkçe) ve klavye düzeninizi seçin.
4. Sistem için bir kullanıcı adı ve parola belirleyin (bu bilgiler oturum açarken ve root yetkisi alırken kullanılacaktır).
5. Bölümleme ekranında **"Yardımcı ile – diskin tamamını kullan"** ve ardından **"Tüm dosyalar tek bölümde"** seçeneklerini tercih edin.
6. Değişikliklerin diske kaydedilmesini onaylayın ve temel sistem dosyalarının kurulmasını bekleyin.
7. Önerilen varsayılan masaüstü paketlerini seçerek kurulumu sonlandırın ve GRUB önyükleyicisini ana sürücüye (`/dev/sda`) kurun.

Kurulum tamamlandıktan sonra Kali Linux sanal makineniz kullanıma hazır olacaktır!
