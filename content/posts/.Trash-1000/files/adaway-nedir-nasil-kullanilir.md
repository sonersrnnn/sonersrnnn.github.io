---
title: AdAway Nedir? Nasıl Kullanılır? (Android Reklam Engelleme)
slug: adaway-nedir-nasil-kullanilir
date: 2026-11-14
lastmod: 2026-11-16
draft: false
description: AdAway nedir, nasıl çalışır? Android'de rootlu hosts ve rootsuz yerel VPN yöntemleriyle reklam engelleme, F-Droid kurulumu ve detaylı ayar rehberi.
tags:
  - android
  - reklam-engelleme
  - acik-kaynak
  - gizlilik
categories:
  - Android
  - Güvenlik
toc: true
---

Akıllı telefonlarımızda internette gezinirken, bir uygulamayı açtığımızda veya oyun oynarken karşımıza çıkan agresif reklamlar sadece can sıkıcı olmakla kalmıyor; veri kotamızı tüketiyor, cihazımızı yavaşlatıyor ve gizliliğimizi tehlikeye atıyor. Üstelik Google Play Store'daki pek çok reklam engelleyici vaadi taşıyan uygulama, arka planda kullanıcı verilerini toplayarak reklam şirketlerine satıyor.

Eğer Android cihazınızda kontrolü tamamen elinize almak, hem tarayıcıda hem de yüklü uygulamalarda reklamları pilinizi tüketmeden durdurmak istiyorsanız aradığınız çözüm açık kaynak dünyasında yer alıyor. Bu rehberde **AdAway nedir**, cihazınızda root yetkisi olsun ya da olmasın nasıl çalışır ve adım adım nasıl kurulur sorularını tüm teknik ayrıntılarıyla ele alıyoruz.

---

## AdAway Nedir?

> **AdAway**, Android işletim sistemi için geliştirilmiş ücretsiz ve açık kaynak kodlu (FOSS) bir reklam engelleme yazılımıdır. Root yetkisi olan cihazlarda sistemin ana bilgisayar (`hosts`) dosyasını güncelleyerek, rootsuz cihazlarda ise yerel bir VPN tüneli kurarak reklam ve takipçi sunucularına giden istekleri sistem genelinde bloke eder.

Pek çok tarayıcı eklentisi yalnızca yüklü olduğu internet tarayıcısındaki reklamları durdurabilirken, AdAway işletim sistemi seviyesinde çalışır. Bu sayede yalnızca web sitelerindeki değil, Android cihazınızdaki üçüncü taraf uygulamaların ve ücretsiz oyunların içerisine yerleştirilmiş reklam ağlarını da engeller.

<!-- GORSEL: AdAway ana ekran arayüzü ve engellenen kaynak sayısı özeti. Dosya: /images/adaway-ana-ekran.webp | Alt Metin: AdAway Android ana ekranında engellenen reklam kaynakları ve durum paneli -->

---

## AdAway Nasıl Çalışır? (İşin Mantığı)

AdAway'i diğer reklam engelleyicilerden ayıran en temel özellik, cihazınızın durumuna göre iki farklı çalışma mekanizması sunmasıdır:

### 1. Rootlu Yöntem: Hosts Dosyası ve Yerel Yönlendirme

Android, temelinde Linux çekirdeği barındıran bir işletim sistemidir. Linux sistemlerinde internetteki alan adlarının IP adreslerine dönüştürülmesinde ilk başvurulan yer `/system/etc/hosts` dosyasıdır.

AdAway root yetkisine sahip bir cihaza kurulduğunda şu adımları izler:

1. Güvenilir engelleme listelerinden binlerce bilinen reklam, takipçi ve zararlı yazılım alan adını indirir.
2. Bu alan adlarını cihazın yerel `hosts` dosyasına yazar ve her birini yerel geri döngü IP adresi olan `127.0.0.1` (veya `0.0.0.0`) adresine yönlendirir.
3. Bir uygulama veya web sitesi reklam sunucusuna istek gönderdiğinde, sistem DNS sunucusuna sormadan önce `hosts` dosyasına bakar.
4. İstek doğrudan cihazın kendi içine (`127.0.0.1`) yönlendirildiği için hiçbir reklam indirilmez ve bağlantı anında düşer.

**En Büyük Avantajı:** Sistem dosyasını bir kez güncelledikten sonra AdAway'in arka planda açık kalmasına gerek yoktur. Arka planda servis çalışmadığı için **pil tüketimi sıfırdır** ve cihazınızda RAM harcanmaz.

### 2. Rootsuz Yöntem: Yerel VPN (Loopback) Mimarisi

Telefonunuzda root erişimi yoksa sistem dizinindeki `hosts` dosyasını doğrudan değiştiremezsiniz. AdAway, rootsuz cihazlar için Google'ın resmi [Android VpnService API](https://developer.android.com/reference/android/net/VpnService) arayüzünü kullanır:

- Cihaz içinde sanal ve yerel bir VPN tüneli kurulur.
- Çıkan tüm ağ ve DNS istekleri bu tünelden geçer.
- İstek yapılan alan adı AdAway'in engelleme listesindeyse paket filtrelenir ve engellenir; temiz istekler normal internet bağlantınıza iletilir.
- **Gizlilik Notu:** Bu yöntem geleneksel VPN hizmetleri gibi trafiğinizi uzak bir sunucuya göndermez. Tüm çözümleme ve filtreleme tamamen telefonunuzun işlemcisinde yerel olarak gerçekleşir.

---

## Rootlu ve Rootsuz Yöntem Karşılaştırması

Hangi yöntemi seçeceğinize karar verirken aşağıdaki karşılaştırma tablosu size yol gösterecektir:

| Kriter | Rootlu Mod (Hosts) | Rootsuz Mod (Yerel VPN) |
|---|---|---|
| **Gereksinim** | Magisk / Kök erişimi (Root) | Herhangi bir standart Android cihaz |
| **Pil Tüketimi** | Sıfır (Arka planda servis çalışmaz) | Çok düşük (Yerel filtreleme servisi) |
| **RAM Kullanımı** | Yok | Düşük (~30-50 MB) |
| **Harici VPN Uyumluluğu** | Başka bir VPN ile sorunsuz çalışır | Aynı anda başka bir VPN açılamaz |
| **Kapsam** | Sistem genelinde tüm uygulamalar | Sistem genelinde tüm uygulamalar |
| **Uygulama Hariç Tutma** | Desteklemez (Tüm sistem etkilenir) | Destekler (Bölünmüş tünelleme) |

---

## AdAway Güvenli mi?

Reklam engelleyici seçerken güvenlik en kritik faktördür. Chrome eklenti mağazalarında ve uygulama marketlerinde yer alan pek çok sahte reklam engelleyicinin kullanıcıların gezinme verilerini topladığı veya cihazlara kötü amaçlı yazılım enjekte ettiği bilinmektedir.

AdAway bu açıdan en güvenilir araçlardan biridir:

- **Tamamen Açık Kaynak Kodludur (GPLv3+):** Kaynak kodları [AdAway resmi GitHub deposu](https://github.com/AdAway/AdAway) üzerinde herkesin incelemesine açıktır. Gizli bir veri toplama, reklam şirketlerine telemetri satma veya casus yazılım barındırma ihtimali bağımsız geliştiriciler tarafından sürekli denetlenir.
- **İsteğe Bağlı Telemetri:** Uygulama varsayılan olarak geliştiricilere hiçbir veri göndermez. Çökme raporları yalnızca kullanıcının açık onayıyla iletilebilir.
- **İzin Şeffaflığı:** Yalnızca ağ bağlantısını yönetmek, filtre listelerini indirmek ve yerel VPN servisini yürütmek için gereken temel izinleri talep eder.

---

## AdAway Nasıl Kurulur? (Adım Adım)

Google, gelir modeli reklam yayıncılığına dayandığı için sistem genelinde reklam engelleyen uygulamaları Google Play Store'da barındırmaz. Bu nedenle AdAway'i yalnızca resmi ve güvenilir kaynaklardan yüklemelisiniz.

> **Uyarısı:** AdAway APK dosyasını asla rastgele indirme sitelerinden veya forum linklerinden indirmeyin. Kurulumu yalnızca resmi [F-Droid AdAway sayfası](https://f-droid.org/packages/org.adaway/) deposundan veya geliştiricinin resmi [GitHub Sürümler (Releases)](https://github.com/AdAway/AdAway/releases) sayfasından yapın.

### Rootsuz Cihazlar İçin Kurulum:

1. [F-Droid resmi sitesinden](https://f-droid.org/) F-Droid istemcisini veya doğrudan AdAway APK dosyasını indirin.
2. İndirdiğiniz APK'yı yükleyin (Gerekirse tarayıcınıza "Bilinmeyen kaynaklardan uygulama yükleme" izni verin).
3. AdAway'i açın ve karşılama ekranında **"VPN Tabanlı Reklam Engelleme"** seçeneğini seçin.
4. Android sisteminin göstereceği **"Bağlantı İsteği (VPN profili oluşturma)"** uyarısını onaylayın.
5. Filtre listelerinin indirilmesini bekleyin ve ana ekrandaki korumayı aktif hale getirin.

### Rootlu Cihazlar İçin Kurulum:

1. Cihazınızda Magisk yüklü olduğundan emin olun.
2. Modern Android sürümlerinde (Android 9+) sistem bölümü salt okunur (read-only) olduğundan, önce **Magisk uygulamasını açın > Ayarlar > Systemless Hosts modülünü etkinleştirin**.
3. AdAway uygulamasını kurup açın ve **"Kök Erişimi Tabanlı (Root)"** seçeneğini seçin.
4. Çıkan Magisk / Superuser isteminde AdAway'e root yetkisi verin.
5. "Filtreleri İndir ve Uygula" butonuna dokunun. İşlem tamamlandığında cihazınızı bir kez yeniden başlatın.

<!-- GORSEL: AdAway kurulum aşamaları ve root / VPN seçim ekranı. Dosya: /images/adaway-kurulum-adimlari.webp | Alt Metin: AdAway Android uygulamasında kök erişimi ve yerel VPN kurulum adımları -->

---

## AdAway'in Sınırları: Neleri Engelleyemez?

AdAway mükemmel bir ağ filtreleyicidir ancak teknik çalışma mimarisinden ötürü her reklamı engelleyemez. Hayal kırıklığı yaşamamak için bu sınırları bilmek gerekir:

1. **YouTube Video İçi Reklamlar:** AdAway alan adı (DNS) seviyesinde filtreleme yapar. YouTube video içi reklamları ise videoların kendisiyle aynı sunuculardan (CDN) ve aynı alan adından gönderir. AdAway bu alan adını engellerse videonun kendisi de açılmaz. Bu nedenle YouTube reklamları için ReVanced veya Firefox üzerinde uBlock Origin gibi kozmetik filtreleme yapabilen çözümler kullanılmalıdır. Reklamsız müzik akışı içinse [ViMusic]({{< ref "vimusic-nedir-nasil-kullanilir" >}}) gibi bağımsız açık kaynaklı istemciler tercih edilebilir.
2. **Kozmetik Filtreleme (Boş Reklam Alanları):** Tarayıcı eklentileri (örneğin AdGuard veya uBlock Origin), reklam kaldırıldığında web sayfasındaki boş çerçeveleri CSS kurallarıyla gizler. AdAway ağ isteğini kestiği için web sitelerinde reklamın yerine gri/boş bir kutu kalabilir.
3. **Aynı Anda İkinci Bir VPN Kullanımı (Rootsuz Mod):** Android işletim sistemi aynı anda yalnızca tek bir VPN profili çalıştırabilir. Rootsuz AdAway açıkken gizlilik veya konum değiştirme amacıyla harici bir VPN açarsanız AdAway devre dışı kalır.

---

## Sık Karşılaşılan Sorunlar ve Çözümleri

### "Bankacılık veya Alışveriş Uygulaması Açılmıyor"
Bazı bankacılık ve e-ticaret uygulamaları sahtekarlık önleme amacıyla üçüncü taraf analiz servislerine bağlanır. Bu servisler AdAway listelerinde engellendiğinde uygulama hata verebilir:
- **Rootsuz Modda:** AdAway ayarlarından *Bölünmüş Tünelleme (Split Tunneling)* bölümüne gidin ve sorun çıkaran uygulamayı VPN filtresinden hariç tutun.
- **Rootlu Modda:** AdAway menüsünden *İzin Verilenler (Allowlist)* listesine girerek engellenen ilgili alan adını beyaz listeye ekleyin.

### "Hosts Dosyası Yazılamadı Hatası"
Rootlu kurulumda bu hatayı alıyorsanız, cihazınızın sistem bölümü yazma korumalıdır. Çözüm için Magisk ayarlarından *Systemless Hosts* eklentisinin aktif olduğundan emin olun ve cihazı yeniden başlatın.

---

## Sıkça Sorulan Sorular

### AdAway nedir ve ne işe yarar?
AdAway, Android cihazlarda reklam ve takipçileri sistem genelinde engelleyen açık kaynaklı bir güvenlik aracıdır. Rootlu cihazlarda sistem `hosts` dosyasını, rootsuz cihazlarda ise yerel bir VPN profilini kullanarak reklam sunucularına giden bağlantıları engeller.

### AdAway rootsuz telefonlarda çalışır mı?
Evet. AdAway modern sürüümlerinde kök erişimi (root) olmayan cihazlar için yerel VPN tabanlı filtreleme sunar. Bu modda cihaz dışına veri çıkmadan tüm filtreleme yerel döngüde gerçekleştirilir.

### AdAway telefonun pilini hızlı bitirir mi?
Rootlu modda sistem hosts dosyasını kullandığı için arka planda hiçbir servis çalıştırmaz; pil tüketimi sıfırdır. Rootsuz VPN modunda ise hafif bir arka plan servisi çalışır ancak veriler uzak sunuculara iletilmediği için pil tüketimi fark edilmeyecek kadar azdır.

### AdAway YouTube reklamlarını engeller mi?
Hayır. AdAway alan adı düzeyinde engelleme yaptığı ve YouTube reklamları doğrudan video akışıyla aynı sunuculardan servis edildiği için video içi reklamları engelleyemez. YouTube için açık kaynaklı alternatif istemciler veya içerik engelleyici destekli tarayıcılar tercih edilmelidir.

### AdAway kullanırken başka bir VPN açabilir miyim?
Eğer AdAway'i rootlu modda kullanıyorsanız evet; hosts dosyası sistemi etkilediği için istediğiniz harici VPN servisini aynı anda kullanabilirsiniz. Ancak rootsuz (yerel VPN) modunu kullanıyorsanız Android aynı anda tek bir VPN bağlantısına izin verdiği için ikinci bir VPN açılamaz.

---

## Sonuç ve Sonraki Adım

Android dünyasında reklam engelleme söz konusu olduğunda AdAway; açık kaynak kodlu yapısı, telemetri barındırmayan gizlilik politikası ve sıfır pil tüketimi sunan rootlu hosts desteğiyle öne çıkan en güçlü araçlardan biridir. Reklam ağlarının ve izleyicilerin cihazınızı yavaşlatmasını engellemek için telefonunuzun durumuna uygun kurulum modunu seçerek hemen kullanmaya başlayabilirsiniz.

Bir sonraki adımda, tarayıcınızda boş reklam alanlarını gizlemek ve kozmetik filtreleme sağlamak için açık kaynaklı tarayıcı eklentilerini inceleyebilir veya ağ genelinde koruma için DNS tabanlı filtreleme çözümlerimize göz atabilirsiniz.
