---
title: Airgeddon Nedir? Kali Linux ile Wi-Fi Güvenlik ve Evil Twin Testleri
slug: airgeddon-ile-kali-linux-wifi-kirma-ve-evil-twin-saldirisi
date: 2026-11-06
lastmod: 2026-11-17
draft: false
description: Airgeddon nedir, nasıl kullanılır? Kali Linux üzerinde Evil Twin (Şeytani İkiz) saldırısı ve Wi-Fi kablosuz ağ güvenliği testleri rehberi.
tags:
  - kablosuz-ag-guvenligi
  - kali-linux
  - evil-twin
  - guvenlik
categories:
  - Linux
toc: true
cover: /img/airgeddon-ile-kali-linux-wifi-kirma-ve-evil-twin-saldirisi/image.png
---

# Airgeddon Nedir? Kali Linux ile Wi-Fi Güvenlik ve Evil Twin Testleri
![](/img/airgeddon-ile-kali-linux-wifi-kirma-ve-evil-twin-saldirisi/image.png)

Günümüzde kablosuz ağ (Wi-Fi) teknolojilerinin hayatımızın merkezinde yer alması, kablosuz ağ güvenliğini en kritik konulardan biri haline getirmiştir. İnternet maliyetleri veya bağlantı ihtiyaçları nedeniyle kullanıcılar sık sık "Wi-Fi şifresi nasıl kırılır?" sorusunu araştırmaktadır. Bu yazımızda, sızma testlerinde sıklıkla kullanılan **Airgeddon** aracı ve **Evil Twin Attack (Şeytani İkiz Saldırısı)** kavramını inceleyeceğiz.

> **Yasal Uyarı:** Bu yazıda anlatılan teknikler yalnızca eğitim, farkındalık ve kendi ağ güvenliğinizi test etme amaçlıdır. İzinsiz başkalarının ağlarına müdahale etmek yasal suç teşkil eder.

---

## Evil Twin Attack (Şeytani İkiz Saldırısı) Nedir?

Kablosuz cihazlar, çevrelerindeki Wi-Fi ağlarını isimlerine (SSID) göre tanır ve otomatik olarak bağlanmaya çalışır. Aynı ada ve şifreleme türüne sahip birden fazla ağ olduğunda cihazlar genellikle bunlardan birini ayırt edemez. 

**Şeytani İkiz Saldırısı**, hedef ağ ile birebir aynı ada sahip sahte bir erişim noktası oluşturulması esasına dayanır. Doğrudan şifreyi bilmediğimiz durumlarda, gerçek ağdaki kullanıcıları geçici olarak düşürüp sahte ağımıza bağlanmaya zorlayarak bir sosyal mühendislik ekranı (Captive Portal) üzerinden şifreyi girmelerini sağlamak bu saldırının temel mantığıdır.

---

## Airgeddon Nedir ve Nasıl Kurulur?

> **Airgeddon**, Kali Linux üzerinde kablosuz ağ denetimleri ve sızma testleri gerçekleştirmek için tasarlanmış kapsamlı bir bash betik aracıdır.

Kali Linux terminalini açarak Airgeddon'ı kolayca kurabilirsiniz:

```bash
sudo apt-get update
sudo apt-get install airgeddon
```

![](/img/airgeddon-ile-kali-linux-wifi-kirma-ve-evil-twin-saldirisi/image1.png)
Kurulum tamamlandıktan sonra aracı root yetkileriyle başlatmak için:

```bash
sudo airgeddon
```

![](/img/airgeddon-ile-kali-linux-wifi-kirma-ve-evil-twin-saldirisi/image2.png)

komutunu çalıştırmanız yeterlidir. İlk açılışta eksik bağımlılıkları indirmek için program onay isteyecektir; gerekli onayları vererek devam edebilirsiniz.

---

## Donanım Gereksinimi: Monitör Modu ve Paket Enjeksiyonu

Airgeddon ile kablosuz ağ testi yaparken bilgisayarınızın dahili Wi-Fi kartı genellikle yetersiz kalır. Gerçek bir test ortamı için şu iki özelliğe sahip harici bir adaptör şarttır:
- **Monitör Modu (Monitor Mode):** Ağdaki paketleri yönünüze bakmaksızın dinleyebilme.
- **Paket Enjeksiyonu (Packet Injection):** Ağdaki bir cihazı geçici olarak düşürmek (deauth) için havaya paket enjekte edebilme.

---

## Adım Adım Airgeddon ile Evil Twin Saldırısı

1. **Ağ Adaptörü Seçimi:** Program açıldığında sizden bir ağ arayüzü seçmeniz istenecektir. Kablosuz ağ işlemleri için kablosuz adaptörünüzün bulunduğu seçeneği (genellikle 2. seçenek) belirleyin.

   ![Airgeddon Adaptör Seçimi](/img/airgeddon-ile-kali-linux-wifi-kirma-ve-evil-twin-saldirisi/rrrrr.png "airgeddon adaptor secimi")

2. **İzleme Modu (Monitor Mode):** Adaptörünüzü izleme moduna alarak çevredeki ağları taramaya başlayın.

   ![İzleme Modu ve Tarama](/img/airgeddon-ile-kali-linux-wifi-kirma-ve-evil-twin-saldirisi/dddd.png "izleme modu ve tarama")

3. **Saldırı Menüsü:** Menüden uygun saldırı modülünü (örneğin 7. seçenek ve Evil Twin / Captive Portal seçenekleri) seçin.

   ![Saldırı Menüsü](/img/airgeddon-ile-kali-linux-wifi-kirma-ve-evil-twin-saldirisi/999.png "saldiri menusu")

4. **Hedef Ağ Tespiti:** Çevredeki ağlar taranırken hedef ağı belirleyin ve arama işlemini sonlandırarak hedef numarasını girin.
5. **Sahte Erişim Noktası ve Captive Portal:** Airgeddon, seçilen ağın birebir klonunu oluşturur. Kullanıcılar gerçek ağdan koparılarak sahte ağa yönlendirilir ve karşılarına çıkan Türkçe destekli giriş ekranında şifreyi girmeleri istenir. Şifre doğru girildiğinde ekranda açık bir şekilde yakalanır.

---

## Sıkça Sorulan Sorular

### Airgeddon kullanmak yasal mı?
Airgeddon açık kaynaklı bir güvenlik denetim aracıdır. Yasal sınırlar içinde yalnızca kendi ağınızın zafiyetlerini test etmek amacıyla kullanılması tamamen yasaldır; başkalarına ait ağlarda izinsiz kullanım suçtur.

### Her dahili Wi-Fi kartı Airgeddon ile çalışır mı?
Çoğu dizüstü bilgisayarın dahili Wi-Fi kartı monitör modunu veya paket enjeksiyonunu desteklemez. Bu nedenle harici bir USB Wi-Fi adaptörü kullanmanız gerekir.

### Evil Twin saldırılarına karşı nasıl korunulur?
Ağ yöneticileri için için WPA3 Enterprise veya güçlü şifreleme protokolleri kullanmak; son kullanıcılar için ise bilinmeyen açık ağlara bağlanırken Captive Portal ekranlarına ve sertifika uyarılarına karşı dikkatli olmak en iyi korunma yöntemidir.

---

## Sonuç ve Özet

Airgeddon, kablosuz ağ güvenliği testlerinde Evil Twin senaryolarını simüle etmek için güçlü ve pratik bir araçtır. Wi-Fi ağlarının güvenliğini sağlamak için zayıf şifreler yerine WPA3 gibi modern şifreleme standartlarını kullanmak, güçlü ve karmaşık parolalar belirlemek bu tür sosyal mühendislik saldırılarına karşı en etkili savunma yöntemidir.

## İlgili Yazılar

- [Kali Linux kurulum ve sızma testi ortamı]({{{< ref "kali-linux-nedir-ve-ikinci-isletim-sistemi-kurulumu" >}})
- [Linux ve kablosuz ağ araçları temelleri]({{{< ref "linux-nedir-ve-populer-linux-dagitimlari" >}})
- [VirtualBox'ta Kali Linux kurulumu]({{{< ref "kali-linux-sanal-makineye-nasil-kurulur-virtualbox-rehberi" >}})
- [Sanal makine ile güvenli test ortamı]({{{< ref "sanal-makine-nedir-nasil-kurulur-virtualbox-rehberi" >}})
