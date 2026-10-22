**Kaynak notu:** Proje mevcut Positron/Aris bot altyapısı üzerinde geliştirilmiştir. Kaynak dosyalardaki özgün atıflar korunur. Paket metadatasında yazar `Positron`, lisans `ISC` olarak belirtilmiştir.

**Bot ile alakalı herhangi bir sorun-telif olursa eğer discord - semikinc. hesabından ulaşabilirsiniz.**

**Bot şuan da aktif olarak gelişim aşamasındadır. Bittikten sonra ücretsiz bir şekilde tam işlevsel paylaşılacaktır.**

**Botlar tamamen https://github.com/ravgar/Discord.js-v14-Setup-Bot bu repoya aittir. Sadece alınıp üzerinde güncelleme ve değişim yapılmıştır.**


<div align="center">

# SEMIK · Discord Bot Sistemi

**Sunucu yönetimi, Guard koruması, web paneli ve coin ekonomisi tek projede.**

![Discord.js](https://img.shields.io/badge/Discord.js-v14-5865F2?style=for-the-badge)
![Node.js](https://img.shields.io/badge/Node.js-22.12%2B-339933?style=for-the-badge)
![MongoDB](https://img.shields.io/badge/MongoDB-Replica_Set-47A248?style=for-the-badge)
![PM2](https://img.shields.io/badge/PM2-Multi_Bot-2B037A?style=for-the-badge)

[Kapsam](#kapsam) · [Komutlar](#komutlar) · [Guard](#guard) · [Web Paneli](#web-paneli) · [Kurulum](#kurulum)

</div>

---

## Kapsam

SEMIK; kayıt, moderasyon, yetkili takibi, sunucu güvenliği ve üye etkileşimini dört bot üzerinden yöneten bir Discord projesidir. Discord içindeki butonlu paneller, tarayıcıdan erişilen yönetim ekranı ve dinamik canvas görselleri aynı veri altyapısıyla çalışır.

| Sistem | Neler sunar? |
| --- | --- |
| 🛡️ **Guard & yedekleme** | Kategori bazlı koruma, kullanıcı/rol izinleri, günlük işlem limitleri, olay kayıtları ve desteklenen işlemlerde geri yükleme |
| 🌐 **Web yönetim paneli** | Sunucu ayarları, rol/kanal seçimleri, yetkili basamakları, üye paneli ayarları ve salt okunur ceza kayıtları |
| 👥 **Kayıt & moderasyon** | Üye kaydı, isim geçmişi, ban, timeout, ceza ve sicil işlemleri |
| 📊 **İstatistik & yetkili** | Mesaj, ses, yayın ve kamera istatistikleri; sıralamalar, görev ve yetki takibi |
| 🪙 **Coin & yatırım** | Banka kartı, altın, günlük ödül, mağaza, transfer ve 80 varlıklı simülasyon piyasası |
| 🎛️ **Üye panelleri** | Kullanıcı kısayolları, rol seçimi, streamer yönetimi, özel oda ve sorun çözme panelleri |
| 🎨 **Canvas görselleri** | Hesaba özel banka kartları, piyasa grafikleri, sıralamalar ve level bildirimleri |

### Bot mimarisi

| Bot | Görevi | PM2 adı |
| --- | --- | --- |
| **Executive** | Kayıt, moderasyon, istatistik, yetkili sistemi ve ekonomi | `semik_Mod1` |
| **ExecutivePlus** | Sunucu ayarları, web paneli, üye panelleri ve kayıt/log olayları | `semik_Mod2` |
| **Guard** | Koruma kararları, güvenli izinleri, limitler ve ihlal işlemleri | `semik_Guard` |
| **Database** | Yedek oluşturma, geri yükleme ve Guard onarım kuyruğu | `semik_Database` |

Botlar `ecosystem.config.js` ile yönetilir. Web paneli ExecutivePlus içinde çalışır; ayrı bir bot süreci gerektirmez.

## Komutlar

Örneklerde önek `.` olarak gösterilmiştir; kurulumunuzdaki önek `System.js → Bot.Prefixs` üzerinden belirlenir. Aşağıdaki tablo kullanım amacına göre gruplandırılmış komut örneklerini içerir. Yetkiler komuta göre değişir; yönetim komutları herkese açık değildir.

| Kategori | Örnek komutlar | Kullanım amacı |
| --- | --- | --- |
| **Kayıt** | `.kayıt`, `.kayıtsız`, `.isim`, `.isimler`, `.teyitler` | Kayıt işlemleri, isim düzenleme/geçmişi ve kayıt sayıları |
| **Moderasyon** | `.ban`, `.unban`, `.timeout`, `.untimeout`, `.ceza`, `.cezakaldir`, `.sicil` | Ceza uygulama, kaldırma ve geçmiş inceleme |
| **Ses yönetimi** | `.move`, `.allmove`, `.allmute`, `.device`, `.nerede` | Üyeleri taşıma, toplu ses işlemleri ve ses bilgisi |
| **Genel kullanım** | `.help`, `.avatar`, `.say`, `.afk`, `.booster`, `.clear`, `.git`, `.çek` | Yardım, profil, sunucu bilgisi ve günlük kullanım |
| **İstatistik** | `.stat`, `.topstat`, `.leaderboard`, `.sesleader`, `.mesajleader` | Aktivite verileri ve kalıcı sıralama yayınları |
| **Yetkili / Upstaff** | `.auth`, `.rank`, `.veriler`, `.taglı`, `.oryantasyon`, `.mazeret`, `.senkronize` | Yetkili atama, puan basamakları, görevler ve mazeret takibi |
| **Kurucu araçları** | `.komutizin`, `.adminlist`, `.ysay`, `.meeting`, `.emoji`, `.eskirol`, `.sürelirol` | Komut yetkileri, yönetici kontrolü, toplantı ve rol işlemleri |
| **Sunucu kurulumu** | `.sunucu`, `.kur`, `.ba`, `.logmen` | Bot ve sunucu ayarları, kurulum araçları |
| **Discord panelleri** | `.userpanel`, `.rolpanel`, `.streamerpanel`, `.streamerrolpanel`, `.ozelodapanel`, `.soruncozmepanel` | Kalıcı buton/seçim menüsü yayınları |
| **Ekonomi** | `.coin`, `.yatırım`, `.coinleader`, `.yatırımleader` | Cüzdan, yatırım ve ekonomi sıralamaları |
| **Guard** | `.guard`, `.güvenli`, `.guardolay`, `.guardcezaac` | Koruma, izin, olay ve Guard cezası yönetimi |
| **Yedekleme** | `.yedek`, `.yedekonar` | Yedek alma, geri yükleme ve kontrol bekleyen onarımı yeniden kuyruğa alma |
| **Sistem** | `.panel`, `.pm2`, `.eval` | Web paneline giriş ve ayrıcalıklı bakım araçları |

Slash komutları arasında `/avatar`, `/banner`, `/nerede`, `/say` ve `/rol` bulunur. Prefix komutlarının tümü slash komutu değildir.

<details>
<summary><strong>Sık kullanılan komut alternatifleri</strong></summary>

| Ana komut | Alternatifler |
| --- | --- |
| `.help` | `.yardım`, `.y` |
| `.coin` | `.bakiye`, `.cüzdan` |
| `.yatırım` | `.yatirim`, `.borsa` |
| `.panel` | `.webpanel` |
| `.guard` | `.shield` |
| `.güvenli` | `.guvenli`, `.whitelist`, `.gw` |
| `.guardolay` | `.guardlog` |
| `.yedek` | `.backup` |

</details>

## Guard

`.guard`, sunucunun koruma ve limit yönetim panelini açar. Sistem Discord olaylarını ve denetim kayıtlarını değerlendirir; yetkisiz veya limit dışı işlemlerde ceza ve desteklenen geri yükleme akışını işletir. Koruma kapsamları ayrı ayrı açılıp kapatılabilir.

### Koruma kapsamları

| Kapsam | İzlenen işlem alanı |
| --- | --- |
| **Sunucu** | Sunucu ayarlarındaki değişiklikler |
| **Rol** | Rol yönetimi ve üye rol değişiklikleri |
| **Kanal** | Kanal oluşturma, silme ve düzenleme işlemleri |
| **Üye / sağ tık** | Desteklenen üye yönetimi işlemleri |
| **Emoji / sticker** | Sunucu ifadelerinin yönetimi |
| **Bot** | Sunucuya bot ekleme işlemleri |
| **Webhook** | Webhook yönetimi |
| **Chat** | Sohbet koruması ve ilgili muafiyetler |

### `.guard` panelinde neler yapılır?

- Ana koruma ve kategori korumaları açılır/kapatılır.
- Günlük işlem limiti ile Streamer/Public kanal limiti ayarlanır.
- Ceza rolü ve log kanalı yapılandırılır.
- Ek korumalarda korunan roller ve oturum korumasında alınacak roller seçilir.
- Web oturumu ve çevrim dışı rol koruması ayrı ayrı yönetilir.

Günlük sayaçlar **Europe/Istanbul saat diliminde 00.00** sınırını kullanır. Yeni Guard ayarında ana koruma kapalıdır; varsayılan günlük limit 10, Streamer/Public limiti 5'tir.

### Güvenli kullanıcı ve roller

`.güvenli @üye` veya `.güvenli @rol` ile hedefin izin paneli açılır.

| İzin türü | Davranış |
| --- | --- |
| **Dokunulmaz Yönetim** | Limitsiz erişim ve Guard cezası muafiyeti |
| **Full Yönetim** | Günlük limitli yönetim izinleri |
| **Kategori izinleri** | Rol, kanal, üye, sunucu, bot, webhook veya emoji/sticker alanında ayrı yetkilendirme |
| **Ek muafiyetler** | Chat, Streamer, Web ve çevrim dışı koruması için bağımsız izinler |

Guard yönetimi sunucu sahibi, yapılandırılmış sahip ve `Bot.Roots` kapsamıyla sınırlandırılır. Bir kullanıcıya işlem izni vermek, onu otomatik olarak panel yöneticisi yapmaz. Etkileşimli Guard oturumları 5 dakika geçerlidir.

### İhlal, olay ve geri yükleme

İhlalde cezalı rolü verilir; botun yönetebildiği diğer roller kaldırılır. `.guardolay` son engellenen işlemleri ve onarım sonuçlarını gösterir. `.guardcezaac @üye` ceza kaydındaki geri verilebilir rolleri geri yüklemeyi dener.

Guard'ı açmadan önce **Database botu bağlı**, **ilk eksiksiz yedek hazır** ve **uygun ceza rolü seçilmiş** olmalıdır. Ceza rolü botun altında, normal ve yönetim yetkileri taşımayan bir rol olmalıdır.

> **Oturum koruması:** Yalnızca web oturumu görülen yetkilinin seçili rolleri 60 saniye sonra alınabilir. Discord çevrim dışı ve görünmez durumlarını ayırt etmediği için bu iki durum birlikte değerlendirilir; bilinmeyen presence verisi tek başına ceza nedeni değildir.

## Yedekleme

`.yedek` panelinden yedek oluşturabilir, hazır yedekleri inceleyebilir ve geri yükleme başlatabilirsiniz. Database botu, Guard tarafından oluşturulan onarım işlerini de işler.

- Mevcut öğelere kaydedilmiş ayarlar uygulanır; desteklenen eksik öğeler yeniden oluşturulur.
- Fazladan kanal ve roller topluca silinmez.
- Silinen mesajlar ve eski Discord nesne ID'leri geri getirilemez.
- Rol hiyerarşisi ve Discord izinleri geri yüklenebilecek işlemleri sınırlar.
- `.yedekonar OLAY_ID`, kontrol bekleyen Guard onarımını yeniden kuyruğa alır.

## Web Paneli

ExecutivePlus ile çalışan web paneli, botların kullandığı ayarları tarayıcı üzerinden düzenlemeyi sağlar. Varsayılan adres: **http://127.0.0.1:3000**.

### Panelin işlevleri

| Ekran / kategori | Yapılabilen işlemler |
| --- | --- |
| **Ana sayfa** | Sunucu özeti, üye/rol/kanal bilgileri, Discord ve MongoDB bağlantısı, gecikme ve çalışma süresi |
| **Genel ayarlar** | Sunucu tagları, semboller, özel URL bilgisi ve kurucu listesi |
| **Kayıt ayarları** | Kayıt yetkilileri, kayıt/kayıtsız rolleri, karşılama görseli ve kanalları, taglı alım |
| **Moderasyon** | Yetkili ve özel roller, sohbet ve komut kanalları |
| **Ceza ayarları** | Ceza yetkilileri, ceza rolleri ve Underworld seçeneği |
| **Kanal & kategoriler** | Bot ses kanalı, özel oda alanları, Public ve Streamer kategorileri |
| **Yetkili & puan** | Otomatik yükseltim, puan/süre eşikleri, yetki basamakları ve haftalık lider ayarları |
| **Üye panelleri** | Rol seçimi, streamer, özel oda ve sorun çözme sisteminin rol/kanal ayarları |
| **Guard bölümü** | Yasaklı tag ayarı ve aktif Guard yönetim panellerine yönlendirme |
| **Ceza kayıtları** | Üye ID ve aktiflik filtresiyle sayfalı, salt okunur ceza geçmişi |
| **Değişiklik günlüğü** | Web panelinden yapılan ayar değişikliklerinin kayıtları |

Rol ve kanal seçenekleri bağlı Discord sunucusundan alınır. Değişiklikler kategori bazında MongoDB'ye kaydedilir; botlar sonraki ayar sorgularında yeni değerleri okur. Aynı kategoride eşzamanlı değişiklik varsa panel eski verinin üzerine yazmak yerine yenileme ister.

**Aktif Guard korumaları, günlük limitler ve güvenli izinleri Discord'daki `.guard` / `.güvenli` panellerinden yönetilir.** Web panelindeki eski Guard alanları bu sistemin yerine kullanılmaz. Panel ceza uygulamaz veya kaldırmaz; bot süreçlerini yeniden başlatmaz. Eski `ecoProduct` alanı yeni coin mağazasını yönetmez; Upstaff puanları da yeni coin cüzdanından ayrıdır.

### Giriş

1. ExecutivePlus botunu çalıştırın ve panel adresini açın.
2. Discord sunucusunda `.panel` yazın.
3. Botun özel mesajla gönderdiği tek kullanımlık kodu girin.

Kod **5 dakika**, oturum **8 saat** geçerlidir. Giriş için kullanıcı `System.js → Bot.Roots` listesinde ve ilgili sunucuda olmalıdır. Kurucu veya Guard güvenli listesinde olmak tek başına panel erişimi vermez. Bot yeniden başladığında oturumlar ve kullanılmamış kodlar geçersiz olur.

İsteğe bağlı Discord OAuth2 girişi de desteklenir. Ayrıntılar: [Web paneli kurulum rehberi](Bots/ExecutivePlus/Panel/KURULUM.md).

## Üye Panelleri

| Panel | Özellikler |
| --- | --- |
| **Kullanıcı paneli** | Ceza puanı, isim geçmişi, hesap/katılım tarihi, davet, haftalık istatistik, rol bilgisi, uygun booster üyeler için isim güncelleme |
| **Rol paneli** | Yapılandırılmış rol gruplarından seçim |
| **Streamer rol paneli** | Streamer rolü işlemleri |
| **Streamer kontrolü** | Yayın izni verme/alma/isteme, susturma, sesten atma, izin listesi ve sahiplik devri |
| **Özel oda** | Oda oluşturma, ad/limit/kilit ayarları, kullanıcı ve yönetici erişimi, yasaklama ve oda kaldırma |
| **Sorun çözme** | İlgili sorun çözme paneli ve yapılandırılmış rol/kanal akışı |

Yeni üye ve Guard panellerinde Discord **Components V2** bileşenleri kullanılır. Kullanıcı paneli kişisel bilgileri özel yanıtlarla sunar; rol temizleme işlemi yapılandırılmış seçim rollerini hedefler.

## Coin ve Yatırım Ekonomisi

`.coin` ile banka kartı açılır. Buradan mağaza, satın alınan görünümler, altın dönüşümü, yatırım portföyü, transfer geçmişi ve günlük ödüle erişilir.

<div align="center">
  <img src="docs/images/coin-bank.png" alt="Coin banka kartı tasarım önizlemesi" width="760">
</div>

*Görseller tasarım önizlemesidir; örnek bakiye ve isimler içerir.*

| Ödül | Miktar |
| --- | --- |
| **Ses leveli** | Her kazanılan level için **30.000 coin + 1 altın** |
| **Mesaj leveli** | Her kazanılan level için **25.000 coin + 1 altın** |
| **Günlük ödül** | 24 saatte bir **3.000–6.000 coin** |

Cüzdanlar sunucu/üye bazındadır. Transferin iki tarafı aynı transaction içinde güncellenir. Tekrarlanan işlem kimlikleri yeniden para hareketi oluşturmaz. Level ödülleri geçilen seviye sayısına göre verilir; eski seviyeler ilk kurulumda topluca ödüllendirilmez.

### Otomatik piyasa

**8 kategori × 10 varlık = 80 yatırım seçeneği:** Teknoloji, Otomotiv, VIP, Değerli Maden, Kripto, Borsa, Uzay ve Lüks.

- Dış API veya fiyat aboneliği gerektirmeyen sunucu içi simülasyon.
- Türkiye saatiyle her gün 00.00'da yükseliş, düşüş veya yatay piyasa yönü.
- 5 dakikalık fiyat hareketleri, kategoriye göre risk ve sektör haberleri.
- Kesirli alım-satım, maliyet, portföy değeri ve gerçekleşmemiş kâr/zarar takibi.
- Alışta +%0,5, satışta −%0,5 makas; 30 saniye işlem aralığı.
- Hesap başına günlük 100 işlem ve işlem başına 1.000.000 coin sınırı.
- Yeniden başlatmalarda korunan fiyat geçmişi, ilk 20 zengin ve ilk 6 yatırımcı sıralaması.

<div align="center">
  <img src="docs/images/investment-market.png" alt="On varlıklı yatırım kategorisi tasarım önizlemesi" width="760">
</div>

> Fiyatlar oyun tarafından üretilir. Gerçek isim ve semboller kullanılsa da gerçek borsa fiyatı veya gerçek varlık mülkiyeti sunulmaz. Coin ve altın sunucu içi sanal değerlerdir.

Level formülleri, limitler, fiyat geçmişi ve veri geçişi ayrıntıları: [Ekonomi rehberi](docs/ECONOMY.md).

## Kurulum

### Gereksinimler

- **Node.js 22.12 veya üzeri** — mevcut ses bağımlılığının gereksinimi.
- **MongoDB replica set veya Atlas** — coin transaction işlemleri için gerekli.
- Discord bot uygulamaları, gerekli sunucu izinleri ve kullanılan özelliklere uygun Gateway Intent ayarları.
- Bağımlılıkları kurabilen bir npm ortamı; canvas paketlerinin platform gereksinimleri.

### 1. Bağımlılıkları kurun

```sh
npm install
```

### 2. Yapılandırmayı tamamlayın

| Dosya | İçerik |
| --- | --- |
| `Global/Settings/System.js` | Bot tokenları, sunucu, önek, Roots ve MongoDB bağlantısı |
| `Global/Settings/Shield.js` | Guard/Database yapılandırma köprüsü |
| `Global/Settings/Panel.js` | Web paneli açma/kapatma, port, bind adresi ve public URL |
| `Global/Settings/DeveloperPanels.js` | Üye panellerinin ayar tanımları |
| `ecosystem.config.js` | Bot süreçleri ve PM2 çalışma ayarları |

Token ve özel anahtarlarınızı herkese açık repoya eklemeyin. README örnekleri gizli bilgi içermez. `Roots` listesine yalnızca yönetim erişimi vermek istediğiniz kullanıcıları ekleyin.

Replica set bağlantı örneği:

```text
mongodb://127.0.0.1:27017/semik_bots?replicaSet=semik-rs
```

Replica set adı ve veritabanı adı kendi kurulumunuzla eşleşmelidir. Tek düğümlü replica set transaction desteği sağlar; yedek sunucu sağlamaz.

```sh
npm run check:mongodb
```

İsteğe bağlı ortam ayarları:

| Değişken | İşlev |
| --- | --- |
| `COIN_LEVEL_CHANNEL_ID` | Level bildirimlerinin gönderileceği kanal |
| `PANEL_DISCORD_CLIENT_SECRET` | Discord OAuth2 girişi için uygulama secret'ı |
| `PANEL_PUBLIC_URL` | Panelin dışarıdan erişilen origin adresi |

Simülasyon piyasası için API anahtarı gerekmez.

### 3. Botları başlatın

```sh
npm start
```

Alternatif PM2 yönetimi:

```sh
npx pm2 start ecosystem.config.js
npx pm2 status
npx pm2 logs semik_Mod2 --lines 50
```

Bu iki başlatma yönteminden kurulumunuza uygun olanını kullanın. Executive istatistik yazıcısı tek instance çalışmalıdır; mevcut PM2 yapılandırması buna göre ayarlanmıştır.

### 4. İlk kurulum sırası

1. Botların bağlandığını ve rol sıralamalarının uygun olduğunu kontrol edin.
2. `.sunucu` veya web panelinden temel rol/kanal ayarlarını tamamlayın.
3. Database botuyla `.yedek` panelinden ilk eksiksiz yedeği alın.
4. `.guard` ile ceza rolünü, log kanalını ve koruma limitlerini ayarlayıp korumayı açın.
5. İstediğiniz kanallarda üye panellerini yayınlayın.
6. `.coin`, `.yatırım`, `.coinleader #kanal` ve `.yatırımleader #kanal` ile ekonomiyi açın.

Kalıcı görsel yayınlarda botun **ViewChannel, SendMessages, ReadMessageHistory, EmbedLinks ve AttachFiles** izinleri bulunmalıdır. Guard ve yedekleme için ilgili yönetim izinleri ve uygun rol hiyerarşisi ayrıca gerekir.

## Proje Yapısı

```text
Bots/
├── Executive/          # Kayıt, moderasyon, istatistik ve ekonomi komutları
├── ExecutivePlus/      # Sunucu ayarları ve Discord panelleri
│   └── Panel/          # Web sunucusu, arayüz ve panel testleri
├── Guard/              # Koruma komutları, olaylar ve Guard servisi
└── Database/           # Yedekleme ve onarım akışları
Global/
├── Economy/            # Cüzdan, simülasyon, işlem ve canvas katmanı
├── Shield/             # Ortak Guard/Database altyapısı
├── DeveloperPanels/    # Rol, streamer, özel oda ve destek panelleri
├── Structures/         # Bot yapısı, kullanıcı paneli ve sıralamalar
└── Settings/           # Yapılandırma ve veri modelleri
tests/                  # Birim ve entegrasyon testleri
scripts/                # Önizleme, bağlantı kontrolü ve bakım araçları
docs/                   # Ayrıntılı rehberler ve README görselleri
```

## Test ve Önizleme

| Komut | Kapsam |
| --- | --- |
| `npm run test:economy` | Cüzdan, ödül, simülasyon, işlem limiti ve fiyat kontrolleri |
| `npm run test:panel` | Web paneli giriş, yetki, ayar ve doğrulama testleri |
| `npm run test:panel:mongo` | Ayrı geçici veritabanıyla gerçek MongoDB panel testleri |
| `npm run check:mongodb` | Yapılandırılmış bağlantıda transaction commit/rollback kontrolü |
| `npm run preview:economy` | `artifacts/economy/` altında örnek canvaslar |
| `npm run panel:preview` | 3001 portunda örnek verili web paneli; gerçek sunucuyu yönetmez |

Ek testler `tests/` ve `tests/shield/` altındadır. Birim testleri canlı Discord izinlerini, rol hiyerarşisini ve sunucuya özel ayarların doğrulanmasını kapsamaz.

## Teknik Notlar

- Ceza şemasının bazı kayıtları guild alanı içermez; bu kurulumun veritabanını bağımsız sunucular arasında ortak kullanmayın.
- Guard ve Database birlikte çalışır; desteklenen geri yüklemeler Discord API ve izin sınırlarına tabidir.
- Web panelindeki Upstaff puanları ile coin ekonomisi ayrı sistemlerdir.
- Varsayılan web paneli yerel erişime açıktır. Dış erişim kurulumu ve OAuth2 ayrıntıları [panel rehberinde](Bots/ExecutivePlus/Panel/KURULUM.md) açıklanır.

---

**Teknoloji:** Discord.js v14 · Node.js · MongoDB/Mongoose · Express · Canvas · PM2
