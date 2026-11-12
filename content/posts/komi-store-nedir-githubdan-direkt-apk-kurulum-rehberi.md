---
title: Komi Store Nedir? GitHub'dan Direkt APK Kurulumu ve Açık Kaynak Uygulama Mağazası
date: 2026-11-03
slug: komi-store-nedir-githubdan-direkt-apk-kurulum-rehberi
description: Komi Store nedir? GitHub, Codeberg ve Forgejo üzerindeki açık kaynak uygulamaları tek tıkla Android'e kurun. Shizuku, root desteği ve F-Droid alternatifi rehber.
cover: /img/komi-store-nedir-githubdan-direkt-apk-kurulum-rehberi/Komi1.png
categories:
  - Mobil Dünya
tags:
  - komi-store
  - android
  - apk
  - acik-kaynak
  - github
  - f-droid
  - uygulama-magazasi
  - shizuku
  - yan-yukleme
draft: false
toc: false
---

# Komi Store Nedir? GitHub'dan Direkt APK Kurulumu ve Açık Kaynak Uygulama Mağazası

![](/img/komi-store-nedir-githubdan-direkt-apk-kurulum-rehberi/Komi1.png)

**Komi Store**, GitHub, Codeberg, Forgejo ve Gitea üzerindeki açık kaynak uygulamaları doğrudan Android cihazınıza tek tıkla kurmanızı sağlayan ücretsiz ve açık kaynaklı bir uygulama mağazasıdır. Google Play Store'a ya da F-Droid'e beklemeye gerek yok — resmi GitHub sürüm sayfasından anında kurulum yapılır, web kazıma yoktur.

Eğer siz de özgür yazılım dünyasını keşfetmek istiyor, güvenilir kaynaklardan APK indirip kurmaktan yorulduysanız bu rehber tam size göre. Komi Store'un ne olduğunu, nasıl çalıştığını ve neden F-Droid ya da Obtainium'a güçlü bir alternatif olduğunu adım adım ele alacağız.

---

## Komi Store Nedir ve Ne Zaman Ortaya Çıktı?

Komi Store, daha önce **GitHub Store** adıyla bilinen bir projedir. Temel amacı şu: GitHub başta olmak üzere Codeberg, Forgejo ve Gitea gibi kod barındırma platformlarındaki uygulama sürümlerini tarayarak Android kullanıcılarının bu uygulamaları mağaza kuyruklarına girmeden, doğrudan orijinal dağıtım dosyalarından kurmasını sağlamak.

Geleneksel yöntemlerde bir geliştirici GitHub'a APK yükler, siz sayfayı açar, doğru mimariyi (arm64 mü, evrensel mü?) bulur, indirip kendiniz kurarsınız. Komi Store bu süreci tamamen otomatik hale getirir.

> **Önemli:** Komi Store, web kazıma (scraping) yapmaz. Uygulamaların resmi GitHub Releases API'sini kullanır — bu da güvenlik açısından kritik bir ayrımdır.

---

## Komi Store'un Çözdüğü Problem: Neden Google Play Yetmez?

Açık kaynak dünyasında yüzlerce güçlü uygulama bulunur ama bunların büyük çoğunluğu Google Play Store'da hiç yer almaz. Bunun birkaç nedeni var:

- Geliştirici Google Play politikalarına uymak istemez.
- Uygulama sürekli güncelleniyor ve Play Store inceleme süreci çok yavaş.
- Bazı uygulamalar gizlilik odaklıdır ve Google ekosistemine girmek istemez.

[F-Droid](https://sonersrnnn.github.io/adaway-nedir-android-icin-acik-kaynakli-reklam-engelleyici/) bu boşluğu kısmen dolduruyor; ancak F-Droid'in kendi imzalama altyapısı var ve uygulamalar genellikle güncel sürümlerden birkaç hafta geride kalıyor. Komi Store ise **kaynak doğrudan geliştirici** olduğu için sürüm gecikmesi sıfıra yakın.

---

## Komi Store Nasıl Çalışır?

### Temel Akış

1. Komi Store'u açarsınız.
2. Keşif sekmesinde veya arama ile bir uygulama bulursunuz.
3. Uygulamanın GitHub/Codeberg/Forgejo sayfasına bağlanır.
4. Platform, cihazınızın mimarisini (arm64, x86, evrensel) otomatik algılar.
5. Doğru APK dosyası tek tıkla indirilir ve kurulur.

Komi Store, bu kurulumu gerçekleştirirken seçtiğiniz **kurulum arka ucunu** kullanır. Standart Android yükleyicisinden root tabanlı sessiz kuruluma kadar birden fazla seçenek sunar.

### Platform Algılama Özelliği

Komi Store'un en güçlü özelliklerinden biri **Platform Algılama**dır. Cihazınızın işletim sistemine göre uyumlu binary dosyasını otomatik filtreler:

| Platform | Desteklenen Format |
|---|---|
| Android | `.apk` |
| Windows | `.exe`, `.msi` |
| macOS | `.dmg`, `.pkg` |
| Linux | `.deb`, `.AppImage`, `.tar.gz` |

Bu sayede tek bir depo listesinden farklı platformlara uygun kurulum yapılabilir.

---

## Komi Store'un Öne Çıkan Özellikleri

### 1. Çoklu Depo Desteği

Komi Store yalnızca GitHub ile sınırlı değildir. Desteklenen platformlar:

- **GitHub** — En büyük açık kaynak deposu
- **Codeberg** — Almanya merkezli, gizlilik odaklı Gitea tabanlı platform
- **Forgejo** — Gitea'nın topluluk çatalı
- **Gitea** — Kendi sunucunuzda barındırabileceğiniz hafif platform
- **Özel Barındırılan Örnekler** — Kendi Gitea/Forgejo sunucunuzu ekleyebilirsiniz

Bu çoklu depo yapısı, [açık kaynak ve özgür yazılım](https://sonersrnnn.github.io/linux-nedir-ve-populer-linux-dagitimlari/) ekosisteminin tamamına tek noktadan erişim anlamına gelir.

### 2. Akıllı Keşif Sistemi

Hangi uygulamayı arayacağınızı bilmiyorsanız Komi Store'un keşif sekmeleri devreye girer:

- **Trend Olan:** O anki en hızlı yükselen projeler
- **Sıcak Yayınlar:** Son çıkan güncellemeler
- **En Popüler:** Toplam star sayısına göre sıralı
- **Konu Kategorileri:** Gizlilik, Medya, Verimlilik, Ağ Oluşturma, Geliştirici Araçları

### 3. Yükleme Takibi ve Güncelleme Bildirimleri

Komi Store üzerinden kurduğunuz uygulamalar takip listesine eklenir. Yeni bir sürüm çıktığında bildirim alırsınız. Üstelik **yan yüklemeli** ya da F-Droid'den kurduğunuz uygulamaları da reposuna bağlayarak güncellemelerini takip ettirebilirsiniz.

### 4. Çoklu Kurulum Arka Uçları

Bu özellik, teknik kullanıcılar için son derece değerlidir:

| Yöntem | Gereksinim | Avantaj |
|---|---|---|
| Standart Android Yükleyici | Yok | Evrensel destek |
| **Shizuku** | Android 11+ | Sessiz kurulum, root gerektirmez |
| **Dhizuku** | Cihaz Yöneticisi | İşletme odaklı sessiz kurulum |
| **Magisk / KernelSU / APatch** | Root | Tam sistem entegrasyonu |

[Magisk](https://diyom.blogspot.com/2026/10/revanced-youtube-nedir-ozellikleri-ve-kullanim-rehberi-indir.html) gibi root çözümleriyle kullanıldığında Komi Store, uygulamaları hiçbir onay penceresi çıkmadan sessizce kurabilir.

### 5. APK Varyant Sabitleme

Bazı projeler tek bir GitHub Release'de onlarca farklı dosya sunar: arm64, x86, evrensel, Play Store sürümü... Komi Store **bir kez seçtiğiniz varyantı hatırlar** ve sonraki güncellemelerde hep aynı dosyayı indirir. Monorepo projelerinde güncelleme kaosunu ortadan kaldırır.

### 6. Sürüm Yönetimi Araçları

- **Sürüm Atla:** Belirli bir sürümü geçmek istiyorsanız.
- **Güncellemeyi Yoksay:** Kararlı sürümde kalmak istiyorsanız.
- **Gelişmiş Varlık Regex:** Hangi dosyanın indirileceğini regex ile özelleştirin.

### 7. README Uygulama İçi Çevirisi

Uygulamanın README dosyasını Komi Store içinde okuyabilirsiniz. Desteklenen çeviri servisleri:

- Google Translate
- DeepL
- LibreTranslate (açık kaynak, öz barındırılabilir)
- Microsoft Translator
- Youdao

### 8. Güvenlik: AES-256-GCM Şifreleme

Hesap bilgileriniz ve tercihleriniz **AES-256-GCM** algoritmasıyla şifrelenir. Android'in donanım destekli **KSafe (Keystore)** altyapısı kullanılır — bu, şifreleme anahtarının cihazın güvenli donanım bölgesinde saklandığı anlamına gelir.

GitHub OAuth için üç farklı yöntem desteklenir:
- Web OAuth (PKCE)
- Cihaz Akışı
- Kişisel Erişim Jetonu (PAT)


|                                                                           |                                                                           |                                                                           |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| ![](/img/komi-store-nedir-githubdan-direkt-apk-kurulum-rehberi/komi2.jpg) | ![](/img/komi-store-nedir-githubdan-direkt-apk-kurulum-rehberi/komi3.jpg) | ![](/img/komi-store-nedir-githubdan-direkt-apk-kurulum-rehberi/komi4.jpg) |





---

## Komi Store vs F-Droid vs Obtainium: Hangisi Daha İyi?

| Özellik | Komi Store | F-Droid | Obtainium |
|---|---|---|---|
| Kaynak | GitHub/Codeberg/Forgejo/Gitea | F-Droid deposu | GitHub/GitLab/vb. |
| Güncelleme Hızı | Anında (resmi release) | Gecikmeli (imzalama süreci) | Anında |
| Keşif | ✅ Zengin | Sınırlı | ❌ Yok |
| Sessiz Kurulum | ✅ Shizuku/root | ❌ | ❌ |
| Platform Algılama | ✅ Otomatik | ❌ | Kısmi |
| Varyant Sabitleme | ✅ | ❌ | ✅ |
| Masaüstü Desteği | ✅ Win/Mac/Linux | ❌ | ❌ |
| Arayüz | Material 3 | Standart | Minimalist |
| Türkçe Dil | ✅ | ✅ | ❌ |

---

## Komi Store Nasıl Kurulur?

Komi Store'u kurmak için resmi GitHub sayfasına gitmeniz yeterlidir:

👉 **İndirme Sayfası:** [github.com/komi-store/komi-store/releases](https://github.com/komi-store/komi-store/releases)

### Adım Adım Kurulum

1. Yukarıdaki bağlantıyı açın.
2. En son sürümdeki `komi-store-*.apk` dosyasını indirin (arm64 önerilir).
3. Android'de "Bilinmeyen Kaynaklardan Yükleme"ye izin verin.
4. APK'yı açıp kurulumu tamamlayın.
5. İsteğe bağlı: Shizuku veya Magisk ile sessiz kurulum modunu etkinleştirin.

> **Not:** Komi Store'u bir kez manuel kurduğunuzda, sonraki güncellemelerini **kendisi otomatik olarak** takip edip size haber verir.

---

## Komi Store Hangi Uygulamaları Destekler?

Komi Store'un kataloğu esasen **GitHub ve benzeri platformlardaki tüm açık kaynak projeler**dir. Kategoriler şunlardır:

- **Gizlilik:** VPN uygulamaları, şifre yöneticileri, ad-blocker'lar
- **Medya:** Müzik çalarlar, video oynatıcılar, podcast uygulamaları
- **Verimlilik:** Not uygulamaları, takvim, görev yöneticileri
- **Ağ:** Proxy araçları, DNS yöneticileri
- **Geliştirici Araçları:** Terminal emülatörleri, SSH istemcileri
- **Oyunlar:** Açık kaynak emülatörler ve strateji oyunları

Hatta [APK Extractor](https://sonersrnnn.github.io/apk-extractor-ile-yuklu-uygulamalardan-apk-nasil-alinir/) gibi araçları bile Komi Store üzerinden güncel tutabilirsiniz.

---

## Masaüstü Desteği: Sadece Android Değil

Komi Store yalnızca Android'e özel değildir. **Windows, macOS ve Linux** üzerinde de çalışır:

- İki bölmeli tablet/masaüstü arayüzü
- Akışkan içerik genişliği
- Kalıcı pencere durumu
- Windows 11 ve macOS'ta yerel karanlık başlık çubuğu

Bu sayede hem telefonunuz hem de bilgisayarınızdaki açık kaynak uygulamaları tek bir araçla yönetebilirsiniz.

---

## Komi Store Güvenli mi?

Evet — ancak birkaç noktaya dikkat etmeniz gerekir:

1. **Kaynak güvenilirliği:** Komi Store, uygulamaları doğrudan GitHub/Codeberg'den alır. Uygulamanın kendisi güvenilir olduğu sürece sorun yoktur. Tanımadığınız geliştiricilerin uygulamalarını kurmadan önce GitHub sayfasını inceleyin.

2. **Komi Store'un kendi kodu:** Tamamen açık kaynak ve GitHub'da incelenebilir durumdadır.

3. **Kimlik bilgisi güvenliği:** AES-256-GCM + donanım Keystore kullanımı, günümüzün en güçlü mobil şifreleme standartlarından biridir.

4. **GitHub API Limitleri:** Giriş yapmadan API limitine takılabilirsiniz. GitHub hesabıyla giriş yaparak bu limiti 60'tan 5000 istek/saate çıkarabilirsiniz.

---

## Sonuç: Komi Store Kimler İçin?

Komi Store şu kullanıcılar için mükemmel bir araçtır:

- Google Play Store'dan bağımsız olmak isteyenler
- F-Droid'deki güncel sürüm gecikmesinden rahatsız olanlar
- GitHub'da keşfettiği uygulamaları kolayca yüklemek isteyenler
- Shizuku veya root kullananlar ve sessiz kurulum isteyenler
- Açık kaynak ekosistemini aktif olarak takip eden meraklılar

---

## Sıkça Sorulan Sorular (SSS)

**Komi Store ücretsiz mi?**
Evet, tamamen ücretsizdir. Komi Store açık kaynaklıdır ve GitHub üzerinden dağıtılmaktadır. Herhangi bir ücret veya abonelik yoktur.

**Komi Store root gerektiriyor mu?**
Hayır. Standart Android yükleyicisi veya Shizuku ile root olmadan da kullanılabilir. Root yalnızca sessiz arka plan kurulumu için opsiyonel bir seçenektir.

**F-Droid ile Komi Store arasındaki fark nedir?**
F-Droid, kendi imzaladığı uygulamaları barındırır ve güncelleme sürecinde gecikme yaşanabilir. Komi Store ise doğrudan GitHub gibi platformlardaki resmi sürümlerden çalışır; güncelleme anında gelir ve çok daha büyük bir uygulama kataloğu sunar.

**Komi Store hangi Android sürümlerini destekler?**
Standart kurulum modunda Android 5.0 ve üzeri çalışır. Shizuku ile sessiz kurulum için Android 11 ve üzeri gerekmektedir.

**Komi Store'a kendi Gitea sunucumu ekleyebilir miyim?**
Evet. Ayarlardan kendi barındırdığınız Gitea veya Forgejo sunucu adresini ekleyebilir ve özel depolara ana bilgisayar bazlı Kişisel Erişim Jetonu (PAT) tanımlayabilirsiniz.

---
