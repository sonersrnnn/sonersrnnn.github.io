---
title: Tor Browser Nedir, Nasıl Kullanılır? Anonim İnternet Rehberi
slug: tor-browser-nedir-nasil-kullanilir-anonim-internet-rehberi
description: Tor Browser nedir nasıl kullanılır merak ediyorsanız, sansürsüz ve anonim internet gezintisi için kurulum, köprü ve güvenlik ayarları rehberi burada.
date: 2026-11-01
draft: false
toc: false
cover: /img/tor-browser-nedir-nasil-kullanilir-anonim-internet-rehberi/Tor1.jpg
categories:
  - Mobil Dunya
tags:
  - tor-browser
  - anonimlik
  - gizlilik
  - siber-guvenlik
  - guvenlik
  - dark-web
---
# Tor Browser Nedir, Nasıl Kullanılır? Anonim İnternet Rehberi

![](/img/tor-browser-nedir-nasil-kullanilir-anonim-internet-rehberi/Tor1.jpg)

**Tor Browser nedir nasıl kullanılır** sorusu, dijital gözetimin, internet sansürünün ve kullanıcı takibinin zirveye ulaştığı günümüz dünyasında gerçek gizlilik arayanların en çok araştırdığı konudur. İnternet servis sağlayıcılarının gezindiğiniz her sayfayı kaydettiği, reklam ağlarının parmak izinizi çıkararak profil oluşturduğu modern web ortamında standart tarayıcılar yetersiz kalır. İşte bu noktada Tor Browser, verilerinizi üç katmanlı şifreleme ve küresel gönüllü röle ağı üzerinden yönlendirerek hem IP adresinizi gizler hem de sansürsüz, tamamen anonim bir internet deneyimi sunar.

- - -

## Tor Browser Nedir ve Nasıl Çalışır?

**Tor Browser**, The Onion Routing (Tor) felsefesine dayanan, internet trafiğini şifreleyerek anonim iletişim sağlayan ücretsiz ve açık kaynaklı bir web tarayıcısıdır. Birleşik Devletler Deniz Araştırma Laboratuvarı tarafından temelleri atılan ve bugün bağımsız The Tor Project tarafından geliştirilen bu sistem, dünya genelinde 2.5 milyondan fazla günlük kullanıcıya hizmet vermektedir. Hatta sızdırılan NSA belgelerinde Tor için *"anonim internetin tahtından indirilemeyen, düşük gecikmeli kralı"* olarak bahsedilmiştir.

Tarayıcının temel çalışma adımları şöyledir:

1. **Giriş Rölesi (Guard Node):** Cihazınız ilk olarak bu düğüme bağlanır. Gerçek IP adresinizi görür fakat hangi web sitesini ziyaret edeceğinizi asla bilemez.
2. **Orta Röle (Middle Node):** Veri paketlerini giriş rölesinden alıp çıkış rölesine iletir. Hem trafiğin asıl kaynağına hem de hedef siteye karşı tamamen kördür.
3. **Çıkış Rölesi (Exit Node):** Son şifreleme katmanını açarak isteği hedef web sitesine iletir. Hedef web sitesi sizin değil, yalnızca bu çıkış düğümünün IP adresini görür.

Geleneksel internet şifrelemesi sunan [VPN Nedir? Kali Linux Üzerinde Vpnbook ile OpenVPN Kurulumu](https://sonersrnnn.github.io/vpn-nedir-ve-kali-linux-openvpn-kurulumu/) rehberimizdeki VPN mantığından farklı olarak Tor, tek bir şirkete veya VPN sağlayıcısına güvenmek zorunda kalmadığınız merkeziyetsiz bir mimari sunar.

- - -

## Tor Browser ile Neler Yapılabilir? Tor Ne Yapar, Ne Yapmaz?

Tor Browser güçlü bir anonimlik kalkanı olsa da kullanıcıların en büyük yanılgısı uygulamanın her şeyi sihirli bir şekilde gizlediğini düşünmesidir:

| Özellik / Senaryo                              | Tor Browser Korur mu? | Açıklama                                                                     |
| ---------------------------------------------- | --------------------- | ---------------------------------------------------------------------------- |
| **Gerçek IP Adresini Gizleme**                 | ✅ Evet                | Web siteleri yalnızca çıkış rölesinin IP adresini görür.                     |
| **İSS'den Gezilen Siteleri Gizleme**           | ✅ Evet                | İnternet sağlayıcınız hangi sitelere girdiğinizi göremez.                    |
| **.onion (Gizli Servis) Sitelerine Giriş**     | ✅ Evet                | Dark web ve güvenli bağımsız yayınlara doğrudan erişir.                      |
| **Giriş Yapılan Hesapları Anonim Kılma**       | ❌ Hayır               | Google, Facebook vb. şahsi hesaplara girerseniz kimliğiniz açığa çıkar.      |
| **İndirilen Dosyalardaki İzleri Temizleme**    | ❌ Hayır               | İndirilen PDF veya Word dosyaları üstveriler (EXIF/metadata) barındırabilir. |
| **Formlara Yazılan Kişisel Bilgileri Saklama** | ❌ Hayır               | Kendi elinizle yazdığınız ad, telefon veya kredi kartı bilgisi gizlenemez.   |

- - -

![](/img/tor-browser-nedir-nasil-kullanilir-anonim-internet-rehberi/Tor2.jpg)

## Adım Adım Tor Browser Kurulumu Nasıl Yapılır?

Tor Browser'ı güvenli biçimde kullanmanın ilk kuralı, yazılımı **yalnızca resmi kaynaklardan** indirmektir. Üçüncü taraf indirme siteleri veya değiştirilmiş paketler casus yazılım riski taşır.

### 1. Windows Kurulumu

1. torproject.org/download adresine gidin ve Windows için `.exe` dosyasını indirin.
2. Kurulum sihirbazını tamamlayın ve tarayıcıyı başlatın.
3. Açılan karşılama ekranında doğrudan **Connect (Bağlan)** butonuna tıklayın.

### 2. Linux Kurulumu

Linux dağıtımlarının resmi depolarındaki paketler çoğu zaman güncelliğini yitirmiştir. Bu nedenle resmi siteden indirme yapmak şarttır:

```bash
# Arşivi çıkarın
tar -xf tor-browser-linux-*.tar.xz
cd tor-browser

# Uygulama menüsüne kaydetmek ve başlatmak için
./start-tor-browser.desktop --register-app
```

*İpucu:* Dosya bütünlüğünü doğrulamak için resmi web sitesindeki `.asc` imza dosyasını GPG aracıyla doğrulamak en üst düzey güvenlik sağlar.

### 3. Android ve iOS (Mobil) Cihazlar

* **Android:** Tor Browser'ı Google Play Store, projenin resmi sitesi veya The Guardian Project'in F-Droid deposundan kurabilirsiniz. (Orbot uygulaması cihaz trafiğini Tor'dan geçirir ancak tarayıcı bazlı parmak izi koruması sağlamaz).
* **iOS (iPhone/iPad):** iOS ekosisteminde resmi bir Tor Browser bulunmaz; The Tor Project tarafından resmen tavsiye edilen açık kaynaklı **Onion Browser** tercih edilmelidir.

- - -

## Türkiye'de Tor Browser Bağlantı Sorunu ve Köprü (Bridge) Ayarları

Türkiye'deki internet servis sağlayıcıları zaman zaman Tor giriş rölelerini engeller. İnternet sansürlerini ve ağ filtrelerini aşmak için [ByeByeDPI Nedir? Android'de Rootsuz Hotspot Sınırı ve DPI Aşma](https://sonersrnnn.github.io/byebyedpi-nedir-rootsuz-hotspot-siniri-nasil-asilir/) rehberimizde incelediğimiz gibi derin paket denetimi (DPI) mekanizmaları devreye girer. Tor Browser'da bu engelleri aşmanın yolu **Köprüleri (Bridges)** etkinleştirmektir.

### Köprüleri Etkinleştirme Adımları:

1. Tarayıcıda sağ üstteki menüden veya bağlantı ekranından **Connection Settings (Bağlantı Ayarları)** bölümüne girin.
2. **Use a bridge (Köprü kullan)** seçeneğini işaretleyin.
3. Dahili köprü seçeneklerinden birini belirleyin:

   * **Snowflake:** WebRTC tabanlı geçici köprüler kurar; sansürlü ağlarda bağlanmanın en pratik ve hızlı yoludur.
   * **obfs4:** Trafiği şifreleyerek sıradan bir internet gürültüsüne dönüştürür; İSS'lerin Tor protokolünü tanımasını engeller. Dilerseniz `bridges.torproject.org` adresinden özel köprü satırları alıp yapıştırabilirsiniz.
   * **meek-azure:** Ağır sansür koşullarında Microsoft Azure bulut altyapısı arkasına gizlenir; diğerlerine göre yavaş olsa da engellenmesi son derece zordur.

- - -

## Hayati Güvenlik Kuralları: Anonimliğinizi Korumak İçin Yapılması Gerekenler

Tor Browser'ı kurup açmak tek başına tam koruma sağlamaz. Yanlış bir alışkanlık kimliğinizi anında ele verebilir. İşte uymanız gereken katı kurallar:

1. **Pencere Boyutunu Değiştirmeyin:** Tarayıcıyı tam ekran yapmayın veya pencereyi elinizle genişletmeyin. Ekran çözünürlüğü ve pencere boyutu benzersiz bir "tarayıcı parmak izi" oluşturarak sizi takip edilebilir kılar.
2. **Eklenti Yüklemeyin:** Reklam engelleyici veya çeviri eklentisi dahil hiçbir harici eklenti kurmayın. Her ekstra eklenti sizi milyonlarca standart Tor kullanıcısından ayıran bir iz bırakır.
3. **Güvenlik Seviyesini Ayarlayın:** Kalkan simgesinden güvenlik seviyesini yönetin:

   * *Standard:* Varsayılan günlük mod.
   * *Safer:* Riskli sitelerde JavaScript kısıtlanır, medya oynatıcılar tıklamayla çalışır.
   * *Safest:* JavaScript tamamen kapatılır; en güvenli moddur ancak bazı modern sitelerin tasarımı bozulabilir.
4. **Torrent ve P2P Kullanmayın:** Torrent istemcileri proxy tünellerini bypass ederek gerçek IP adresinizi açık kaynaklara sızdırır.
5. **İndirilen Belgeleri Çevrimdışı Açın:** Tor üzerinden indirdiğiniz PDF veya Word belgelerini tarayıcı açıkken çalıştırmayın. Bu dosyalar arka planda harici bir sunucuya istek göndererek gerçek IP adresinizi sızdırabilir.
6. **Yeni Kimlik (New Identity) Özelliğini Kullanın:** İşiniz bittiğinde menüden *New Identity* seçeneğini tıklayın; tüm çerezler temizlenir ve yeni bir Tor devresi oluşturulur.
7. **Güvenli Parola Yönetimi:** Anonim platformlardaki üyeliklerinizde standart şifrelerinizi asla kullanmayın; [KeePassDX: Android Güvenli Şifre Yöneticisi Rehberi](https://sonersrnnn.github.io/keeppassdx-android-guvenli-sifre-yoneticisi/) gibi yerel ve şifreli veri tabanlarında rastgele oluşturulmuş güçlü parolalar saklayın.

- - -

![](/img/tor-browser-nedir-nasil-kullanilir-anonim-internet-rehberi/Tor3.jpg)

## .onion Siteleri (Gizli Servisler) Nedir?

Tor ağının en belirgin özelliklerinden biri `.onion` alan adı uzantısına sahip web siteleridir. Bu siteler standart arama motorları tarafından dizine eklenmez ve klasik tarayıcılarla açılamaz.

* **Uçtan Uca Gizlilik:** `.onion` sitelerinde yalnızca istemcinin değil, web sitesini barındıran sunucunun fiziksel konumu ve IP adresi de gizlidir.
* **Resmi Onion Siteleri:** Güvenlik ve sansürsüz haber alma amacıyla DuckDuckGo, BBC, ProtonMail ve The New York Times gibi dev platformların doğrulanmış resmi `.onion` adresleri mevcuttur.
* **Adres Doğrulaması:** Onion adresleri karmaşık karakterlerden oluştuğu için kimlik avı (phishing) sitelerine karşı adresleri daima doğrulanmış resmi kaynaklardan almalısınız.

Daha da ileri düzeyde bir yalıtım ve iz bırakmama ihtiyacı duyuyorsanız, tüm işletim sistemini RAM üzerinden çalıştıran ve tüm trafiği zorunlu olarak Tor'dan geçiren **Tails OS** veya **Whonix** sanal ortamlarını değerlendirebilirsiniz.

- - -

## Sıkça Sorulan Sorular (SSS)

### Tor Browser kullanmak yasal mıdır?

Evet, Tor Browser kullanmak Türkiye dahil dünyanın büyük bir bölümünde tamamen yasaldır. Gazeteciler, araştırmacılar, siber güvenlik uzmanları ve gizliliğine önem veren milyonlarca vatandaş Tor ağından meşru şekilde faydalanır. Ancak bu tarayıcı üzerinden yasa dışı faaliyetlerde bulunmak suç teşkil eder ve cezai sorumluluk doğurur.

### Tor Browser ile VPN aynı şey midir?

Hayır, ikisi farklı amaçlara hizmet eder. VPN tüm cihaz trafiğini tek bir ticari sunucu tüneline yönlendirirken, Tor Browser trafiği merkeziyetsiz 3 ayrı bağımsız röleden geçirerek çok katmanlı anonimlik sunar. Tor gizlilik ve gözetimi engellemede daha üstündür fakat VPN'e kıyasla daha yavaş çalışır.

### Tor Browser neden yavaş çalışıyor?

Verileriniz dünya çapında rastgele seçilen üç ayrı gönüllü röle üzerinden katman katman şifrelenip iletildiği için standart tarayıcılara kıyasla bir gecikme yaşanması doğaldır. Bu hız kaybı, üstün anonimlik ve gizlilik seviyesinin doğal bir sonucudur.

### Tor açıkken Google veya banka hesaplarıma girebilir miyim?

Teknik olarak girebilirsiniz ancak bu durum anonimliğinizi tamamen yok eder. Kişisel hesabınıza giriş yaptığınız anda oturum bilgilerinizle gerçek kimliğiniz eşleşir ve Tor ağının sağladığı gizlilik kalkanı anlamsız hale gelir.

- - -
