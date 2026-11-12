---
title: VeraCrypt Nedir? Dosya ve Disk Şifreleme Rehberi
date: 2026-11-01
slug: veracrypt-nedir-dosya-disk-sifreleme-rehberi
description: VeraCrypt nedir, nasıl kullanılır? Ücretsiz ve açık kaynaklı dosya şifreleme programıyla verilerinizi AES ile koruyun. Adım adım kurulum ve kasa oluşturma rehberi.
cover: /img/veracrypt-nedir-dosya-disk-sifreleme-rehberi/Vera1.png
categories:
  - 🐧 Linux
tags:
  - veracrypt
  - dosya-sifreleme
  - disk-sifreleme
  - gizlilik
  - acik-kaynak
  - aes
  - truecrypt
draft: false
toc: false
---

# VeraCrypt Nedir? Ücretsiz Dosya ve Disk Şifreleme Programı Rehberi
![VeraCrypt](/img/veracrypt-nedir-dosya-disk-sifreleme-rehberi/Vera1.png "veracrypt nedir nasıl kullanılır")

**Dosya şifreleme programı** arayanların önüne en sık çıkan isim **VeraCrypt**'tir; ve bu tesadüf değildir. VeraCrypt, Windows, macOS ve Linux üzerinde çalışan, tamamen ücretsiz ve açık kaynaklı bir disk şifreleme yazılımıdır. Dosyalarınızı, USB belleğinizi veya tüm sabit diskinizi askeri düzeyde AES şifrelemeyle korur; şifrenizi bilmeyen hiç kimse — istihbarat teşkilatları dahil — verilerinize ulaşamaz. Bu rehberde VeraCrypt'in ne olduğunu, nasıl çalıştığını ve adım adım nasıl kullanacağınızı eksiksiz anlatacağız.

---

## VeraCrypt Nedir?

**VeraCrypt**, 2013 yılında geliştirimi durdurulan TrueCrypt projesinin mirasını devralan, güvenlik açıkları kapatılmış ve aktif olarak geliştirilen açık kaynaklı bir şifreleme yazılımıdır. Fransa merkezli IDRIX şirketi tarafından sürdürülmekte olup kaynak kodu herkes tarafından incelenebilir.

VeraCrypt'in çalışma prensibi **anında şifreleme (on-the-fly encryption / OTFE)** üzerine kuruludur: Veriler diske yazılmadan hemen önce RAM'de otomatik olarak şifrelenir; okunurken yine RAM'de çözülür. Siz sadece normal bir sürücüde çalışıyormuşsunuz gibi dosyalarınızı kullanırsınız. VeraCrypt arka planda tüm şifreleme işlemini görünmez biçimde gerçekleştirir.

### VeraCrypt ile TrueCrypt Arasındaki Fark
TrueCrypt, 2014'te gizemli biçimde geliştirimini durdurdu ve güvenlik denetimleri bazı kritik açıklar ortaya çıkardı. VeraCrypt bu açıkları kapattı, daha güçlü anahtar türetme algoritmaları (PBKDF2-SHA-512) kullandı ve aktif geliştirmeye devam etti. Bugün güvenlik uzmanları TrueCrypt yerine VeraCrypt'i önermektedir.

---

## VeraCrypt'in Temel Özellikleri

### 🔐 Anında Şifreleme (On-the-Fly)
Şifreli kasanız açıkken dosyalar okunurken RAM'de otomatik çözülür, yazılırken otomatik şifrelenir. Disk üzerinde hiçbir zaman şifresiz veri bulunmaz. Bilgisayarı kapattığınızda veya kasayı dismount ettiğinizde veriler tekrar erişilemez hale gelir.

### 🧱 Güçlü Şifreleme Algoritmaları

| Algoritma | Özellik |
|---|---|
| **AES** | Dünya standardı, donanım hızlandırma (AES-NI) desteği |
| **Serpent** | Daha muhafazakâr, AES'e alternatif |
| **Twofish** | Blowfish'in halefi, kanıtlanmış güvenlik |
| **AES-Twofish** | Cascade: iki algoritma zincirleme |
| **AES-Twofish-Serpent** | En güçlü cascade, biraz daha yavaş |

Çoğu kullanıcı için **AES + SHA-512** kombinasyonu hem güvenli hem de hızlıdır.

### 🎭 Gizli Kasa (Hidden Volume / Plausible Deniability)
VeraCrypt'in en ilgi çekici özelliğidir. Dış kasanın içine ikinci, gizli bir kasa yerleştirebilirsiniz. Birisi sizi parolanızı vermeye zorlarsa dış kasanın parolasını verirsiniz; içinde masum dosyalar görünür. Gizli kasanın varlığını kanıtlamak teknik olarak imkânsızdır çünkü şifreli alanın tamamı rastgele veriden ayırt edilemez.

### 🔑 Keyfile (Dosya Anahtarı)
Parolaya ek olarak belirli bir dosyayı (fotoğraf, müzik, herhangi bir dosya) "anahtar" olarak tanımlayabilirsiniz. Hem parolayı hem de o dosyayı bilen biri kasayı açabilir. Dosya kaybolursa kasa sonsuza kadar açılamaz.

### 🔢 PIM (Personal Iterations Multiplier)
Anahtar türetme işleminin kaç tur tekrar edeceğini belirleyen ek parametre. Yüksek PIM, brute-force saldırılarını dramatik biçimde zorlaştırır; ancak bağlama süresi uzar.
![VeraCrypt](/img/veracrypt-nedir-dosya-disk-sifreleme-rehberi/Vera2.jpg)

---

## VeraCrypt Kullanım Senaryoları: Hangi Yöntemi Seçmelisiniz?

VeraCrypt üç farklı şifreleme yöntemi sunar:

### 1. Dosya Kapsayıcısı (Container) — En Yaygın Yöntem
Sabit diskinizde tek bir büyük dosya oluşturursunuz. Bu dosya, içinde binlerce dosya taşıyabilen şifreli bir "kasa"dır. Kasayı VeraCrypt ile bağlayınca bilgisayarınızda yeni bir sürücü harfi belirir (ör. `E:\`); dosyalarınızı buraya normal sürücüymüş gibi kopyalarsınız. İşiniz bitince "Dismount" dersiniz, kasa kapanır.

**Avantajı:** Taşınabilir (USB'ye atılabilir), boyutu önceden belirlenir.  
**Dezavantajı:** Boyutu sonradan büyütemezsiniz — cömert seçin.

### 2. Bölüm veya USB Şifreleme
Harici sabit disk, USB bellek veya disk bölümünün tamamını şifreler. USB belleğinizi tamamen şifrelemek için idealdir; belleği bağladığınızda VeraCrypt parola sorar.

**Avantajı:** Tüm bölüm şifreli, ek kasa dosyası gerekmez.  
**Dezavantajı:** Bölümdeki tüm veriler silinir, VeraCrypt yüklü bilgisayar gerekir.

### 3. Sistem Şifreleme (Windows)
Windows kurulu diskin tamamını şifreler. Bilgisayar açılışında VeraCrypt parola sorar; doğru parola girilmezse Windows hiç başlamaz. Dizüstü bilgisayar çalınsa bile içindeki hiçbir veriye erişilemez.

**Avantajı:** En kapsamlı koruma, tüm sistem şifreli.  
**Dezavantajı:** En riskli yöntem, yanlış yapılırsa Windows açılmaz; kurtarma diski zorunlu.

---

## VeraCrypt Nasıl Kurulur?

### Windows
1. [https://veracrypt.io/en/Downloads.html](https://veracrypt.io/en/Downloads.html) adresine gidin
2. **Windows Installer (.exe)** dosyasını indirin — başka sitelerden indirmeyin
3. Çalıştırın → **Install** seçin (USB'de taşınabilir kullanım için **Extract** seçeneği de var)
4. İndirme sayfasındaki SHA-256 hash'i kontrol edin (güvenlik doğrulaması)

### Linux (Ubuntu/Debian)
```bash
# .deb paketini resmi siteden indirin
sudo apt install ./veracrypt-*.deb
```

Fedora/openSUSE için `.rpm` paketi, diğer dağıtımlar için `.tar.bz2` mevcuttur.

### macOS
Resmi siteden `.dmg` dosyasını indirip kurabilirsiniz.

### Android
VeraCrypt'in resmi Android uygulaması **yoktur**. Play Store'daki "VeraCrypt" isimli uygulamalara güvenmeyin. VeraCrypt kasalarını açabilen üçüncü taraf uygulama olarak **EDS (Encrypted Data Stash)** kullanılabilir; ancak hassas veriler için dikkatli olun.

---

## VeraCrypt ile Şifreli Kasa Nasıl Oluşturulur? (Adım Adım)

Bu en yaygın yöntem olan **dosya kapsayıcısı** oluşturmayı anlatmaktadır.

### Adım 1: Volume Oluşturma Sihirbazını Açın
VeraCrypt'i açın → **Create Volume** butonuna tıklayın.

### Adım 2: Kasa Türünü Seçin
- ✅ **Create an encrypted file container** seçin → Next

### Adım 3: Volume Tipini Belirleyin
- **Standard VeraCrypt volume:** Normal şifreli kasa
- **Hidden VeraCrypt volume:** Gizli kasa (gelişmiş kullanım)

Başlangıç için **Standard** seçin → Next

### Adım 4: Dosya Konumunu Belirleyin
**Select File** → Kasanın kaydedileceği konumu ve dosya adını seçin.  
Örnek: `C:\Users\Kullanici\Belgeler\kasa.hc`

> Dosyaya herhangi bir ad ve uzantı verebilirsiniz. `.hc` uzantısı yaygın kullanılır ama zorunlu değil.

### Adım 5: Şifreleme Algoritmasını Seçin
- **Encryption Algorithm:** AES (çoğu kullanıcı için yeterli)
- **Hash Algorithm:** SHA-512

Maksimum güvenlik isteyenler AES-Twofish veya AES-Twofish-Serpent seçebilir; ancak performans biraz düşer → Next

### Adım 6: Kasa Boyutunu Belirleyin
Kasanın boyutunu MB veya GB olarak girin. **Sonradan büyütemezsiniz**, bu yüzden ihtiyacınızdan biraz fazla ayırın.

Örnek: Belgeler ve fotoğraflar için → 10 GB

### Adım 7: Güçlü Parola Oluşturun
En az **20 karakter** içeren bir parola belirleyin. Birkaç rastgele kelimeden oluşan bir parola cümlesi (passphrase) hem hatırlanabilir hem de güçlüdür.

> ⚠️ Bu parolayı unutursanız verilerinizi **hiçbir şekilde** kurtaramazsınız. [KeePassDX](https://sonersrnnn.github.io/keeppassdx-android-guvenli-sifre-yoneticisi/) gibi bir şifre yöneticisinde saklayın.

### Adım 8: Dosya Sistemini Seçin
- **exFAT:** Windows, macOS ve Linux arasında taşınabilir — önerilir
- **NTFS:** Sadece Windows; 4 GB üzeri dosyalar için FAT32 yerine kullanın
- **ext4:** Sadece Linux

### Adım 9: Rastgele Veri Üretimi (Entropi)
Ekranda farenizi en az 30 saniye rastgele hareket ettirin. Bu, şifreleme anahtarının gücünü artırır. Progress bar dolunca → **Format** butonuna basın.

Kasa oluşturma işlemi boyuta göre birkaç saniye ile birkaç dakika arasında sürer.

---

## Şifreli Kasayı Bağlama ve Kullanma

```
1. VeraCrypt'i açın
2. Listeden bir sürücü harfi seçin (ör. E:)
3. "Select File" → kasa dosyanızı seçin
4. "Mount" butonuna basın
5. Parolanızı girin → OK
```

Kasanız artık Dosya Gezgini'nde yeni bir sürücü olarak görünür. Normal bir sürücü gibi dosya kopyalayabilir, silebilir, düzenleyebilirsiniz.

### Dismount (Kasayı Kapatma)
İşiniz bitince VeraCrypt'te kasayı seçin → **Dismount**. Artık kasaya erişim mümkün değildir.

> Dismount etmeden bilgisayarı kapatmayın veya USB'yi çıkarmayın — veri bozulması riski vardır.

---

## Gizli Kasa (Hidden Volume) Nasıl Çalışır?

Hidden Volume, VeraCrypt'in en güçlü gizlilik özelliğidir. Tek bir kasa dosyasının içinde iki bağımsız kasa bulunur:

- **Dış Kasa (Outer Volume):** Birincil parola ile açılır, masum dosyalar içerir
- **İç/Gizli Kasa (Hidden Volume):** Gizli parola ile açılır, gerçek hassas veriler burada

Birisi sizi parolanızı vermeye zorlarsa dış kasanın parolasını verirsiniz. Gizli kasanın varlığı teknik olarak kanıtlanamaz; çünkü şifreli alanın tamamı rastgele veriden oluşur.

**Dikkat:** Hidden Volume kullanırken her mount işleminde "Protect hidden volume" seçeneğini işaretleyin; aksi takdirde dış kasaya yazdığınız veriler gizli kasayı ezebilir.

---

## Önemli Güvenlik İpuçları

### ✅ Volume Header Yedeği Alın
```
VeraCrypt → Tools → Backup Volume Header
```
Kasa başlığı bozulursa (disk hatası, bit çürümesi) kasayı açamazsınız. Yedeği güvenli bir yerde saklayın.

### ✅ Bulut Senkronizasyonunda Dikkat
OneDrive, Google Drive veya Dropbox kullanıyorsanız kasayı **kapalıyken** senkronize edin. Kasa açıkken senkronize edilirse her küçük değişiklikte tüm kasa dosyası (örneğin 10 GB) yeniden yüklenir.

### ✅ Geçici Dosyalar
Microsoft Office, PDF okuyucular ve bazı uygulamalar açtığınız dosyaların geçici kopyalarını sistem geçici klasörüne yazar. Bu kopyalar kasa dışındadır. Hassas belgelerle çalışırken buna dikkat edin.

### ✅ RAM'de Şifre
Kasa bağlıyken şifreleme anahtarı RAM'de bulunur. Fiziksel erişimi olan biri RAM dump yaparak anahtara ulaşabilir (Cold Boot Attack). Kritik senaryolarda bilgisayarı kapatın — sadece uyku moduna almayın.

### ✅ İndirme Güvenliği
VeraCrypt'i **yalnızca** `veracrypt.io` adresinden indirin. İndirme sayfasındaki SHA-256 hash değerini dosyayla karşılaştırarak doğrulayın.

---

## VeraCrypt'i Hangi Araçlarla Birlikte Kullanmalısınız?

VeraCrypt tek başına güçlü bir araçtır; ancak doğru ekiple kullanıldığında dijital gizliliğiniz çok daha kapsamlı hale gelir:

- **[KeePassDX](https://sonersrnnn.github.io/keeppassdx-android-guvenli-sifre-yoneticisi/):** VeraCrypt parolalarınızı güvenle saklamak için açık kaynaklı şifre yöneticisi. Güçlü ve uzun parolalar kullanmak artık sorun değil.
- **[AdGuard Nedir? Güvenli Reklam Engelleme ve Tarayıcı Koruma Rehberi](https://sonersrnnn.github.io/adguard-nedir-guvenli-reklam-engelleme-rehberi/):** Şifreli dosyalarınızın yanı sıra internet trafiğinizi de koruyun.
- **[VPN Nedir? Kali Linux Üzerinde Vpnbook ile OpenVPN Kurulumu](https://sonersrnnn.github.io/vpn-nedir-ve-kali-linux-openvpn-kurulumu/):** VeraCrypt depolama güvenliğini, VPN ağ güvenliğini sağlar. İkisi birlikte kapsamlı bir gizlilik katmanı oluşturur.

---

## VeraCrypt vs BitLocker: Hangisini Seçmelisiniz?

| Özellik | VeraCrypt | BitLocker |
|---|---|---|
| Lisans | Ücretsiz, açık kaynak | Windows Pro/Enterprise ile birlikte |
| Platform | Windows, macOS, Linux | Yalnızca Windows |
| Kaynak Kod İnceleme | ✅ Herkese açık | ❌ Kapalı kaynak |
| Hidden Volume | ✅ Var | ❌ Yok |
| Bağımsız Güvenlik Denetimi | ✅ Yapıldı | ❌ Yok |
| Kullanım Kolaylığı | Orta | Kolay |
| Hükümet Arka Kapı Riski | Çok düşük | Tartışmalı |

Güvenliğe ve gizliliğe önem veriyorsanız VeraCrypt her zaman daha güvenilir bir seçimdir. BitLocker yalnızca kolaylık ve kurumsal entegrasyon gerektiğinde tercih edilebilir.

---
## Sıkça Sorulan Sorular (SSS)

**VeraCrypt ücretsiz mi?**
Evet, tamamen ücretsiz ve açık kaynaklıdır. Herhangi bir abonelik veya lisans ücreti yoktur. Kaynak kodu GitHub üzerinde herkese açıktır ve bağımsız güvenlik denetimleri yapılmıştır.

**VeraCrypt kasasını unuttum, verilerimi kurtarabilir miyim?**
Hayır. VeraCrypt'in güçlü şifreleme tasarımı gereği, parolanızı unutursanız verilerinizi kurtarmanın hiçbir yolu yoktur. Bu nedenle parolayı bir şifre yöneticisinde saklamak kritik önem taşır.

**VeraCrypt bulut depolama ile kullanılabilir mi?**
Evet, ancak dikkatli olunmalıdır. Kasa dosyanızı (ör. `kasa.hc`) OneDrive veya Google Drive klasörüne koyabilirsiniz; ancak kasayı her zaman **kapalıyken** senkronize edin. Açıkken senkronize etmek hem veri bozulmasına hem de büyük dosya yükleme sorununa yol açar.

**Şifreli USB bellek yapmak mümkün mü?**
Evet. VeraCrypt ile USB belleğin tamamını veya bir kısmını şifreleyebilirsiniz. Taşınabilir VeraCrypt kurulumunu da USB'ye koyarak VeraCrypt yüklü olmayan bilgisayarlarda bile kasanızı açabilirsiniz.

**VeraCrypt NSA tarafından kırılabilir mi?**
VeraCrypt'in kullandığı AES-256 şifrelemesi, mevcut bilgi ve teknoloji ile kırılabilir değildir. Zayıf nokta algoritmada değil, kullanıcı davranışındadır: zayıf parola, güvensiz ortamda bağlı kasa, RAM dump saldırıları gibi insan kaynaklı riskler asıl tehdit oluşturur.

---
## Sonuç

**VeraCrypt**, dijital güvenliğini ciddiye alan herkes için temel bir araçtır. Ücretsiz, açık kaynaklı, bağımsız denetimden geçmiş ve tüm büyük platformlarda çalışan bu yazılım; dosyalarınızı, USB belleğinizi ve tüm diskinizi askeri düzeyde koruma altına alır. Hidden Volume özelliğiyle zorlama senaryolarına bile hazırlıklı olmanızı sağlar. Kurulumu on dakika, öğrenmesi bir saat; ama kazandırdığı güvenlik ömür boyu sürer.

---
