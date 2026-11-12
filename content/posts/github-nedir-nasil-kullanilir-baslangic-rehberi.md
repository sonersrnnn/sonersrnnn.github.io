---
title: GitHub Nedir? Nasıl Kullanılır? Başlangıç Rehberi
slug: github-nedir-nasil-kullanilir-baslangic-rehberi
description: GitHub nedir, nasıl kullanılır? Git ve GitHub farkı, temel komutlar, repository açma ve kod paylaşımı için adım adım başlangıç rehberi.
date: 2026-11-01
draft: false
toc: false
cover: /img/github-nedir-nasil-kullanilir-baslangic-rehberi/github1.jpeg
categories:
  - Linux
tags:
  - github
  - git
  - versiyon-kontrol
  - yazılım
  - açık-kaynak
  - kod-yönetimi
---
# GitHub Nedir? Git ile Kod Yönetiminde Başlangıç Rehberi

**GitHub nedir nasıl kullanılır** diye merak edenler için doğru yerdesiniz. GitHub, yazılımcıların kodlarını güvenle depoladığı, değişiklikleri adım adım takip ettiği ve diğer geliştiricilerle ortak projeler yürüttüğü dünyanın en büyük **bulut tabanlı kod barındırma platformudur**. Bu rehberde GitHub'ı sıfırdan öğrenecek; temel kavramları, temel komutları ve gerçek kullanım senaryolarını adım adım keşfedeceksiniz.

- - -

## GitHub Nedir? Kısaca Tanıyalım

GitHub, **Git** adlı versiyon kontrol sistemi üzerine inşa edilmiş bir web platformudur. Microsoft'a ait olan bu platform, dünya genelinde 100 milyonu aşkın geliştiriciyi ve milyonlarca açık kaynak projeyi bünyesinde barındırmaktadır.

Bunu şöyle düşünün: Nasıl Google Drive belgelerinizi bulutta saklıyor ve paylaşmanızı sağlıyorsa, GitHub de **kodlarınızı bulutta saklar, değişiklik geçmişinizi kaydeder ve ekibinizle birlikte çalışmanızı kolaylaştırır**. Ancak GitHub bunun çok ötesinde özellikler sunar.

- - -

## Git Nedir? GitHub ile Farkı Ne?


GitHub'ı anlamak için önce **Git**'i bilmek gerekir. Bu iki kavram çoğu zaman birbirine karıştırılır.

### Git Nedir?

Git, **Linus Torvalds** tarafından geliştirilen, tamamen ücretsiz ve açık kaynaklı bir **Versiyon Kontrol Sistemi (VCS)**'dir. Bilgisayarınızda yerel olarak çalışır. Kodunuzdaki her değişikliği takip eder, kaydeder ve gerektiğinde eski sürüme dönmenizi sağlar.

Bunu oyunlardaki **Save Point (kayıt noktası)** sistemine benzetebiliriz. Her `commit` komutu, projenizin o anki durumunu kaydeden bir kontrol noktasıdır. İstediğiniz zaman o noktaya geri dönebilirsiniz.

### GitHub Nedir?

GitHub ise Git depolarını **çevrimiçi olarak barındıran** bir platformdur. Git'i yerel kullanabilirsiniz; ama GitHub ile kodlarınızı buluta taşırsınız, ekibinizle paylaşırsınız ve dünya genelindeki geliştiricilerle işbirliği yaparsınız.

| Özellik     | Git               | GitHub                      |
| ----------- | ----------------- | --------------------------- |
| Konum       | Yerel bilgisayar  | Bulut (çevrimiçi)           |
| Amaç        | Versiyon kontrolü | Depo barındırma + işbirliği |
| Ücret       | Ücretsiz          | Ücretsiz (temel plan)       |
| İnternet    | Gerekmez          | Gerekir                     |
| Geliştirici | Linus Torvalds    | GitHub Inc. / Microsoft     |

- - -

## GitHub Neden Kullanılır? 7 Güçlü Sebep

GitHub kullanmanın yalnızca "kod saklamak" olmadığını görmek, platforma bakış açınızı tamamen değiştirecek.

### 1. Versiyon Kontrolü — Hata Yapma Korkusu Ortadan Kalkar

Kodunuzun her değişikliğini kayıt altına alır. Bir hata yapıp her şeyi bozduğunuzda saniyeler içinde **çalışan eski sürüme geri dönebilirsiniz**. Yanlışlıkla sildiğiniz kod? Sorun değil, geçmişte duruyor.

### 2. Takım Çalışması — Aynı Dosyada Çakışmasız Geliştirme

Aynı kod dosyası üzerinde birden fazla geliştirici **birbirinin işini bozmadan** aynı anda çalışabilir. Branch (dal) sistemi sayesinde herkes kendi geliştirme yolunda ilerler, hazır olduğunda ana projeye dahil eder.

### 3. Code Review (Kod İncelemesi) — Kalite Kontrol

**Pull Request** özelliği, yazdığınız kodların ekip arkadaşlarınız tarafından incelenmesini sağlar. Hatalar canlıya çıkmadan önce tespit edilir, iyileştirme önerileri yapılır. Bu özellik profesyonel yazılım ekiplerinin vazgeçilmezi.

### 4. Kariyer ve Portföy — Özgeçmişten Güçlü

GitHub profiliniz, iş başvurularında **en etkili dijital portföyünüzdür**. İşverenler adayların GitHub profilini inceleyerek hangi projelerde çalıştığını, nasıl kod yazdığını ve topluluğa ne kadar katkıda bulunduğunu görebilir.

### 5. Açık Kaynak Katkısı — Dünyayı Etkileyin

GitHub'da milyonlarca açık kaynak proje yer alır. Kullandığınız bir araçta hata buldunuz mu? **Pull Request göndererek düzeltebilirsiniz**. Bu hem dünyaya katkı yapmaktır hem de özgeçmişinize değer katmaktır.

### 6. GitHub Pages — Ücretsiz Web Sitesi

Statik web sitelerinizi veya proje dokümanlarınızı **tamamen ücretsiz** olarak GitHub üzerinden yayınlayabilirsiniz. GitHub Pages ile kişisel portföy sitesi, proje tanıtım sayfası veya blog kurabilirsiniz.

### 7. GitHub Actions — Otomatik CI/CD

Kodunuzu her güncellediğinizde **otomatik olarak test edilmesini ve canlıya alınmasını** sağlayabilirsiniz. Bu CI/CD (Sürekli Entegrasyon / Sürekli Dağıtım) sürecidir ve profesyonel yazılım geliştirmenin temelidir.

- - -

## GitHub Temel Terimleri Sözlüğü

GitHub'ı kullanmaya başlamadan önce bu kavramları öğrenmek çok işinize yarayacak.

### Repository (Depo / Repo)

Projenizin dosyalarının ve tüm geçmiş sürüm kayıtlarının saklandığı alan. Her proje için ayrı bir repository oluşturursunuz. Public (herkese açık) veya Private (gizli) olabilir.

### Commit

Projede yaptığınız değişiklikleri kalıcı olarak kaydeden işlem. Her commit'e açıklayıcı bir mesaj eklenir: `git commit -m "Giriş sayfası eklendi"`. Bu mesajlar ileride neyin ne zaman değiştirildiğini anlamanızı sağlar.

### Branch (Dal)

Ana kodunuza zarar vermeden yeni bir özellik denemek veya hata düzeltmek için projenizin kopyasını alıp üzerinde çalıştığınız yan yol. Varsayılan dal genellikle `main` veya `master` olarak adlandırılır.

### Pull Request (Çekme Talebi)

Yan dalda yaptığınız değişiklikleri ana projeye dahil etmesi için gönderdiğiniz onay isteği. Ekip arkadaşlarınız bu talebi inceleyip onaylayabilir veya değişiklik önerebilir.

### Clone (Klonlama)

İnternetteki bir depoyu bilgisayarınıza indirme işlemi: `git clone <url>`. İndirdiğiniz depo üzerinde yerel olarak çalışabilirsiniz.

### Push / Pull

* **Push:** Bilgisayarınızdaki yerel değişiklikleri GitHub'a gönderme
* **Pull:** GitHub'daki güncel değişiklikleri bilgisayarınıza çekme

### Fork

Başkasının projesini kendi hesabınıza kopyalama. Açık kaynak projelere katkı sağlamanın birincil yöntemidir.

- - -

## GitHub Nasıl Kullanılır? Adım Adım Başlangıç

### Adım 1: Hesap Oluşturun

[github.com](https://github.com/) adresine gidin ve ücretsiz hesap açın. Kullanıcı adı seçerken dikkatli olun; bu isim GitHub URL'inizde görünecek ve kariyerinize yansıyacak.

### Adım 2: Git Programını Kurun

GitHub'ı kullanmak için bilgisayarınıza **Git yazılımını** kurmanız gerekir. [git-scm.com](https://git-scm.com/) adresinden işletim sisteminize uygun sürümü indirin ve kurun.

Kurulumdan sonra kimliğinizi tanıtın:

```bash
git config --global user.name "Adınız Soyadınız"
git config --global user.email "email@example.com"
```

### Adım 3: Yeni Bir Repository Açın

GitHub profilinizde sağ üstteki **"+"** ikonuna tıklayın → **"New repository"** seçin → Projenize bir isim verin → **"Create repository"** butonuna basın.

### Adım 4: Yerel Projenizi GitHub'a Bağlayın

Terminal veya komut satırını açın ve proje klasörünüze gidin:

```bash
# Mevcut bir klasörü Git deposuna dönüştür
git init

# Tüm dosyaları hazırlık alanına ekle
git add .

# İlk commit'i oluştur
git commit -m "İlk commit - proje başlatıldı"

# GitHub deposunu uzak kaynak olarak ekle
git remote add origin https://github.com/kullaniciadiniz/proje-adi.git

# Dosyaları GitHub'a gönder
git push -u origin main
```

### Adım 5: Takım Çalışması — Branch ve Pull Request

```bash
# Yeni dal oluştur ve geç
git checkout -b yeni-ozellik

# Değişiklikleri yap, ekle ve commit et
git add .
git commit -m "Yeni özellik eklendi"

# Dalı GitHub'a gönder
git push origin yeni-ozellik
```

Ardından GitHub arayüzünden **"Compare & pull request"** butonuna tıklayarak ekip arkadaşlarınızdan inceleme isteyin.

- - -

## GitHub Pages ile Ücretsiz Web Sitesi Yayınlayın

GitHub'ın en kullanışlı ama en az bilinen özelliklerinden biri **GitHub Pages**'tir. HTML, CSS ve JavaScript ile oluşturduğunuz statik web sitelerini tamamen ücretsiz olarak yayınlayabilirsiniz.

Aktivasyon için:

1. Repository'nize girin → **Settings** → **Pages**
2. Source olarak **main** dalını seçin
3. Birkaç dakika sonra siteniz `kullaniciadiniz.github.io/proje-adi` adresinde yayında!

Kişisel portföy sitesi oluşturmak için de mükemmel bir yöntemdir. GitHub, açık kaynak felsefesinin tam merkezinde yer alır: Kaynak kodlar şeffaftır, herkes tarafından görüntülenebilir, değiştirilebilir ve dağıtılabilir. Bu yaklaşım; Ubuntu, Debian, Fedora gibi Linux dağıtımlarının temelini oluşturan [açık kaynak ekosistemin](https://sonersrnnn.github.io/linux-nedir-ve-populer-linux-dagitimlari/) doğal bir parçasıdır.

- - -

## GitHub ve IDE Entegrasyonu — Visual Studio ile Güçlü İkili

GitHub, yalnızca terminalde kullanılan bir araç değildir. **IDE (Entegre Geliştirme Ortamı)** olan Visual Studio ile doğrudan entegre çalışır. IDE, kod yazma, derleme, hata ayıklama ve test etme araçlarını tek arayüzde birleştiren bir yazılım ortamıdır. Visual Studio'nun **IntelliSense** özelliği, kod yazarken otomatik tamamlama ve hata öneri sistemi sunar — bu deneyim GitHub ile birleşince çok daha güçlü hale gelir.

Özellikle dikkat çekici olan: Visual Studio, **GitHub Copilot** yapay zeka entegrasyonuna sahiptir. Copilot, GitHub üzerindeki milyarlarca satır açık kaynak koddan öğrenerek size kod önerisi sunar. Yani GitHub'daki açık kaynak ekosistemi doğrudan yazdığınız kodun kalitesini etkiler.

> **Pratik İpucu:** C# ve .NET ile geliştirme yapıyorsanız Visual Studio + GitHub kombinasyonu endüstri standardıdır. C#, Microsoft tarafından geliştirilmiş, nesne yönelimli ve tip güvenli bir dildir; web, masaüstü, mobil ve oyun geliştirmede yaygın kullanılır.

- - -

## GitHub Actions ile Otomasyona Giriş

**GitHub Actions**, kodunuzu her GitHub'a gönderdiğinizde otomatik olarak çalışan iş akışları oluşturmanızı sağlar. Bu CI/CD (Continuous Integration / Continuous Deployment) sürecidir.

Örnek kullanım senaryoları:

* Kod her güncellendiğinde otomatik testleri çalıştır
* Test başarılıysa kodu otomatik olarak canlıya al
* Her pull request açıldığında kod kalite kontrolü yap

```yaml
# .github/workflows/test.yml
name: Test
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Testleri çalıştır
        run: npm test
```

Bu tür otomasyon araçları, profesyonel geliştirme ortamlarında çok yaygındır. Benzer şekilde, [Visual Studio Nedir?](https://sonersrnnn.github.io/visual-studio-nedir-ve-gelistirme-ortami-rehberi/) yazımızda anlattığımız IDE'lerle GitHub entegrasyonu son derece güçlüdür.

- - -

## GitHub ile Açık Kaynak Projelere Katkı Sağlama

GitHub'ın en heyecan verici boyutu: **dünyaya katkı yapmak**. Favori uygulamanızda bir hata buldunuz mu? GitHub üzerinden düzeltebilirsiniz.

### Fork + Pull Request Döngüsü:

1. Katkı sağlamak istediğiniz projeyi **Fork** edin (kendi hesabınıza kopyalayın)
2. Fork'u bilgisayarınıza **Clone** edin
3. Yeni bir **Branch** oluşturun
4. Değişikliklerinizi yapın ve **Commit** edin
5. **Push** ile kendi fork'unuza gönderin
6. Orijinal projeye **Pull Request** açın
7. Proje sahipleri inceleyip merge edebilir

Bu döngü, açık kaynak dünyasının işleyiş biçimidir. Git ve GitHub konusunda ilerlemenizi C# gibi bir programlama dili öğrenimiyle pekiştirebilirsiniz; [C# Nedir?](https://sonersrnnn.github.io/c-sharp-programlama-diliyle-neler-yapilabilir/) yazımıza göz atabilirsiniz.

- - -

## Sık Kullanılan Git Komutları Hızlı Referans

```bash
# Durum kontrolü
git status

# Değişiklikleri göster
git diff

# Commit geçmişini gör
git log --oneline

# Uzak depodaki güncel değişiklikleri çek
git pull origin main

# Dal listesi
git branch -a

# Belirli bir commit'e git (geçici)
git checkout <commit-hash>

# Son commit'i geri al (değişiklikler korunur)
git reset HEAD~1

# Tüm yerel değişiklikleri sil (dikkatli kullanın!)
git checkout .
```

- - -

## Sıkça Sorulan Sorular (SSS)

**GitHub ücretsiz mi?**
Evet, GitHub temel planı tamamen ücretsizdir. Ücretsiz hesapla hem public (herkese açık) hem de private (gizli) sınırsız repository oluşturabilirsiniz. Gelişmiş kurumsal özellikler için ücretli planlar mevcuttur.

**Git olmadan GitHub kullanılabilir mi?**
GitHub web arayüzü üzerinden bazı işlemler yapılabilir; ancak tam verimle kullanmak için bilgisayarınıza Git kurulumu gereklidir. GitHub Desktop uygulaması ile komut satırı yerine görsel arayüz kullanabilirsiniz.

**GitHub ile GitLab arasındaki fark nedir?**
Her ikisi de Git tabanlı depo barındırma platformlarıdır. GitHub Microsoft'a ait olup daha büyük topluluğa sahiptir. GitLab ise özellikle CI/CD ve DevOps odaklı özellikleriyle öne çıkar ve kendi sunucunuza kurulabilir (self-hosted).

**Commit mesajları neden önemli?**
Commit mesajları, ileride kim hangi değişikliği neden yaptı diye bakıldığında bağlam sağlar. Kötü mesaj: `güncelleme`. İyi mesaj: `Kullanıcı giriş formu doğrulama hatası düzeltildi`. Profesyonel projelerde okunabilir commit mesajları zorunluluktur.

**GitHub'da bir projeye katkı sağlamak zor mu?**
Temel seviyede değil. Fork → Clone → Branch → Commit → Push → Pull Request döngüsünü kavradıktan sonra herhangi bir açık kaynak projeye katkı sağlayabilirsiniz. Küçük düzeltmelerle (yazım hatası, dokümantasyon) başlamak en iyi yoldur.

- - -

## Sonuç

GitHub, modern yazılım geliştirmenin merkezinde yer alan vazgeçilmez bir platformdur. **Git ile versiyon kontrolü**, **Pull Request ile kod incelemesi**, **GitHub Pages ile ücretsiz barındırma** ve **GitHub Actions ile otomasyon** gibi güçlü özellikler bir arada sunan bu platform; hem yeni başlayanlar için öğrenme ortamı hem de profesyoneller için üretim aracıdır.

Kod yazmayı yeni öğreniyor olun ya da deneyimli bir geliştirici olun — GitHub profilinizi oluşturmak ve aktif tutmak kariyerinize değer katan en önemli adımlardan biridir.

- - -
