# Bolatoğlu Yapı — İçerik Ekleme Rehberi

Bu dosya üç işi anlatır: **proje**, **hizmet** ve **bölge** eklemek.

> **Önce dosyanın sonundaki [İÇERİK STANDARTLARI](#icerik-standartlari) bölümünü oku.**
> Kelime sayısı, kopya içerik kuralı, iç link zorunluluğu ve karakter
> sınırları orada. Bunlara uymadan eklenen sayfa sonradan düzeltilmek
> zorunda kalıyor.

Hızlı geçiş:

* [Proje eklemek](#1-dosyayı-oluştur) — aşağıda, 1. bölümden itibaren
* [Hizmet eklemek](#yeni-bir-hizmet-eklemek)
* [Bölge eklemek](#yeni-bölge-ilçe-sayfası-eklemek)
* [Rehber yazısı eklemek](#yeni-rehber-yazısı-eklemek)
* [İçerik standartları](#icerik-standartlari)

---

# Yeni İş (Proje) Ekleme Rehberi

Bu dosya siteye dahil edilmez, sadece senin için not.

## 1. Dosyayı oluştur

`_portfolio/` klasörüne yeni bir `.md` dosyası aç. Dosya adı aynı zamanda
adres olur, o yüzden Türkçe karaktersiz ve tireli yaz:

    _portfolio/erbaa-cumhuriyet-cam-balkon.md
    →  bolatogluyapi.com/islerim/erbaa-cumhuriyet-cam-balkon/

İyi bir dosya adı ne yapıldığını ve nerede yapıldığını içerir.

## 2. Şablonu kopyala

```yaml
---
caption: #ana sayfa ve /islerim/ grid'inde gorunen bilgiler
  title: Katlanır Cam Balkon
  subtitle: Erbaa / Cumhuriyet
  thumbnail: /assets/img/portfolio/ornek.jpg

#proje sayfasinda gorunen bilgiler
title: Erbaa Cumhuriyet Mah. Katlanır Cam Balkon
subtitle: Erbaa / Cumhuriyet
location: "Tokat / Erbaa - Cumhuriyet Mah."
ilce: "Erbaa"
date: 2026-08-15
category: "Cam Balkon Sistemleri"
image: /assets/img/portfolio/ornek.jpg
alt: Erbaa Cumhuriyet Mahallesi katlanır cam balkon uygulaması
description: "Yaklasik 140-160 karakter. Arama sonucunda bu metin gorunur."
---

## Proje Hakkında

İki paragraf: müşteri ne istiyordu, neden bu çözümü seçtik.

### Teknik Detaylar

* **Başlık:** Açıklama.
* **Başlık:** Açıklama.

### Sonuç

Bir paragraf: ortaya ne çıktı.
```

## 3. Alanların anlamı

| Alan | Ne işe yarar |
|---|---|
| `caption.title` | Kart başlığı. Kısa tut, 2-4 kelime. |
| `caption.subtitle` | Kartta başlığın altı. Genelde ilçe/mahalle. |
| `caption.thumbnail` | Karttaki küçük görsel. |
| `title` | Proje sayfasının `h1`'i ve arama sonucu başlığı. |
| `subtitle` | Proje sayfasında başlığın altındaki tek satır. |
| `location` | Meta şeridindeki "Konum". |
| `ilce` | **Hangi bölge sayfasında görüneceğini belirler.** Yazmazsan proje hiçbir bölge sayfasında çıkmaz. Bölge dosyasındaki `ilce` değeriyle harfi harfine aynı olmalı. Şu an tanımlı olanlar: Erbaa, Tokat, Turhal, Niksar, Amasya, Taşova, Suluova, Ünye, Akkuş, Kadıköy. Listede olmayan bir ilçe yazacaksan önce o bölge sayfasını aç (aşağıdaki bölüm). |
| `date` | **Sıralamayı bu belirler.** Yeni tarih en üste çıkar. `YYYY-AA-GG`. |
| `category` | **Hangi hizmet sayfasında görüneceğini belirler.** Aşağıya bak. |
| `client` | İsteğe bağlı. Yazmazsan meta şeridinde hiç görünmez. |
| `description` | Arama sonucundaki açıklama. 140-160 karakter ideal. |
| `alt` | Görsel açıklaması. Görsel aramada işe yarar, boş bırakma. |
| `image` | **Link paylaşıldığında çıkan önizleme görseli.** Proje sayfalarında o işin fotoğrafı, diğer tüm sayfalarda logo kullanılır. Değeri `caption.thumbnail` ile aynı olmalı. |

`order` diye bir alan yok, sıralama tamamen `date` ile.

## 4. Kategori listesi — TAM OLARAK böyle yazılmalı

`category` alanına aşağıdaki on değerden **birini** yaz. Harfi harfine
aynı olmalı; büyük/küçük harf veya Türkçe karakter farkı olursa proje
hiçbir hizmet sayfasında görünmez (kendi sayfası ve /islerim/ yine çalışır).

| `category` değeri | Görüneceği hizmet sayfası |
|---|---|
| `"PVC Kapı Pencere"` | /hizmetler/pvc-kapi-pencere/ |
| `"Cam Balkon Sistemleri"` | /hizmetler/cam-balkon/ |
| `"Korkuluk Sistemleri"` | /hizmetler/korkuluk-kupeste/ |
| `"Banyo Sistemleri"` | /hizmetler/dusakabin-banyo/ |
| `"Sineklik Sistemleri"` | /hizmetler/sineklik/ |
| `"Alüminyum Doğrama"` | /hizmetler/aluminyum-dograma/ |
| `"PVC Sistemleri"` | /hizmetler/teras-kapatma-kis-bahcesi/ (teras, kış bahçesi) |
| `"Tamir ve Bakım"` | /hizmetler/tadilat-bakim/ |
| `"Çelik Kapı"` | /hizmetler/celik-kapi/ |
| `"Panjur Sistemleri"` | /hizmetler/panjur-kepenk/ |

Bu liste `_hizmetler/*.md` dosyalarındaki `categories` alanlarından gelir.
Şüphedeysen ilgili hizmet dosyasını açıp oraya bak — asıl kaynak orası.
Yeni bir kategori kullanmak istiyorsan önce ilgili hizmet dosyasının
`categories` listesine eklemen gerekir, yoksa eşleşme olmaz.

## 5. Kontrol et

```bash
bundle _2.7.2_ exec jekyll build
```

`Error` veya `Conflict` satırı çıkmamalı. **Sass deprecation uyarıları
normaldir** — temadan geliyor, işin bozulduğu anlamına gelmez.

Sonra `bundle _2.7.2_ exec jekyll serve` ile üçünü de kontrol et:

- `/islerim/` — yeni proje en üstte mi (tarih en yeniyse)
- `/hizmetler/<ilgili-sayfa>/` — proje sayısı bir artmış mı
- `/<ilce>/` — bölge sayfasındaki sayı bir artmış mı
- `/hizmetler/` — hiçbir hizmet kartı boş kalmış mı (tıklayınca hiç proje
  göstermeyen bir hizmet varsa `categories` alanı ya boştur ya da yazımı
  projedeki `category` ile tutmuyordur)

İkincisi artmadıysa `category`, üçüncüsü artmadıysa `ilce` yazımı tutmuyordur.
Build hata vermez, sessizce eşleşmez.

## 6. Yayınla

```bash
git add -A
git commit -m "Yeni proje: erbaa cumhuriyet cam balkon"
git push
```

Push sonrası GitHub Actions siteyi otomatik yayına alır ve Cloudflare
önbelleğini temizler. Elle bir şey yapmana gerek yok; birkaç dakika içinde
canlıda görünür.

**Yeni bir sayfa eklediysen** (proje, bölge veya hizmet), son bir adım var:
Google Search Console'da `URL Denetimi` kutusuna yeni adresi yazıp
**"Dizine eklenmesini iste"** de. Bu olmadan da Google eninde sonunda bulur
ama haftalar sürebilir.

---

## Yeni bir hizmet eklemek

`_hizmetler/` klasörüne `.md` dosyası aç:

```yaml
---
title: "Erbaa ... Sistemleri"     # arama sonucu basligi, ~40 karakter
heading: "... Sistemleri"          # sayfadaki h1 ve kart basligi
subtitle: "Tek cumlelik ozet"      # kartin altindaki aciklama
description: "140-160 karakter."
icon: tools                        # asagidaki listeden bir ad
order: 11                          # kartlarin sirasi (her hizmette farkli olmali)
categories:
  - "İlgili Kategori"
---

Hizmet metni buraya.
```

### Alanların anlamı

| Alan | Ne işe yarar |
|---|---|
| `title` | Arama sonucu başlığı. Sonuna `| Bolatoğlu Yapı` otomatik eklenir, o yüzden ~40 karakterde tut. |
| `heading` | Sayfadaki `h1` ve ana sayfadaki kart başlığı. Kısa. |
| `subtitle` | Kartın altındaki tek satırlık özet. |
| `description` | Arama sonucundaki açıklama. 140-160 karakter. |
| `icon` | Karttaki ikon. Aşağıdaki listeden bir ad. |
| `order` | Kartların sırası. **Her hizmette farklı olmalı.** Şu an 1-10 dolu, yenisi için 11'den devam et. |
| `categories` | **Bu sayfada hangi projelerin listeleneceğini belirler.** Projelerdeki `category` değeriyle harfi harfine aynı olmalı. |

Ana sayfadaki hizmet kartları, `/hizmetler/` sayfası, bütün bölge
sayfalarındaki hizmet listesi ve yapısal veri bu klasörden otomatik beslenir.
Ayrıca bir yere eklemen gerekmez.

### Kullanılabilir ikon adları

Font Awesome'ı siteden kaldırdık (18 ikon için 162 KB yazı tipi indiriliyordu).
İkonlar artık `_includes/ikon.html` içinde gömülü SVG olarak duruyor. `icon:`
alanına **yalnızca** şunlardan birini yazabilirsin:

    bars          bath          border-all    clock         columns
    door-closed   envelope      home          layer-group   map-marker-alt
    phone         plus          shield-alt    tools         window-maximize

Şu an kullanımda olanlar: `window-maximize` (PVC), `layer-group` (cam balkon),
`shield-alt` (korkuluk), `bath` (duşakabin), `border-all` (sineklik),
`columns` (alüminyum), `home` (teras), `tools` (tadilat), `door-closed`
(çelik kapı), `bars` (panjur). Aynı ikonu iki hizmette kullanmak teknik olarak
sorun değil ama kartlar birbirine benzer görünür.

`fas fa-tools` gibi eski yazım da çalışır, sondaki adı alır. Ama listede
olmayan bir ad yazarsan (örneğin `fa-fire-extinguisher`) sayfa bozulmaz,
**sade bir daire** çıkar.

### `categories` alanını boş bırakma

```yaml
categories:
  - "Panjur Sistemleri"
```

Bu alan hizmet sayfasının hangi projeleri listeleyeceğini belirler. **Boş
bırakırsan (`categories: []`) o hizmet sayfası hiçbir zaman proje göstermez** —
sonradan o kategoriyle proje eklesen bile. Bir süre `celik-kapi.md` bu haldeydi.

Yeni bir hizmet açarken kategori adını şimdiden yaz; henüz o işten projen
olmasa bile. Proje eklediğin gün kendiliğinden eşleşir.

Yeni ikon gerekiyorsa: fontawesome.com/icons adresinden SVG'yi indir,
`_includes/ikon.html` dosyasına örnektekiler gibi bir `when` satırı ekle.

---

## Yeni bölge (ilçe) sayfası eklemek

Bölge sayfaları `/erbaa/`, `/turhal/` gibi adreslerde yayınlanır ve o ilçede
yaptığın işleri otomatik listeler. "niksar cam balkon", "turhal pencere tamiri"
gibi aramalar için var.

### 1. Projelere ilçe bilgisi ver

Her proje dosyasında `ilce` alanı olmalı:

```yaml
location: "Tokat / Zile - Cumhuriyet Mah."
ilce: "Zile"
```

`ilce` değeri bölge sayfasındaki değerle **harfi harfine aynı** olmalı.

### 2. Kök dizine bölge dosyasını aç

Örnek: `zile.md`

```yaml
---
layout: bolge
permalink: /zile/
order: 10                # link sirasindaki yeri (her bolgede farkli olmali)
ilce: "Zile"             # projelerdeki ilce degeriyle ayni
il: "Tokat"              # bagli oldugu il - asagida acikliyorum
title: "Zile PVC Pencere ve Cam Balkon"    # arama sonucu basligi, ~40 karakter
heading: "Zile"                            # sayfadaki h1
subtitle: "Zile'de tamamladığımız işler."  # h1 altindaki tek satir
description: "140-160 karakter, arama sonucu aciklamasi."
---

Buraya o ilçeye özgü metin yaz. En az 100 kelime olsun.
```

### 3. `il` alanı neden gerekiyor

Bu alan sayfada hiçbir yerde görünmez. Google'a gönderdiğimiz yapısal veride
"bu ilçe hangi ilde" bilgisini taşır:

```json
{ "name": "Turhal", "containedInPlace": { "name": "Tokat" } }
```

Neden önemli: Türkiye'de aynı isimde birden fazla yer var ve bizim hizmet
alanımız tek ile sığmıyor. Taşova ve Suluova Amasya'da, Ünye Ordu'da. İl
bilgisi olmadan Google bunları doğru eşleştiremez, yerel aramada yanlış
bölgeye bağlayabilir.

**Yazmayı unutursan** bölge sayfası yine çalışır, sadece o ilçe için il
bilgisi gönderilmez. Bilerek böyle yaptık: yanlış bir il yazmaktansa hiç
yazmamak daha iyi.

### 4. ÖNEMLİ: metin gerçekten farklı olmalı

Aynı metni ilçe adını değiştirerek çoğaltma. Google buna "kapı sayfası" diyor ve
cezalandırıyor — tek bir kopyala-yapıştır sayfa bütün bölge sayfalarının değerini
düşürebilir.

Her sayfada o ilçeye **özgü** bir şey anlat. Örnekler:

- mesafe ve keşif düzeni (Tokat merkez sayfasında var)
- o ilçede öne çıkan iş tipi (Turhal'da fitil değişimi, Taşova'da korkuluk)
- coğrafi/iklim özelliği (Niksar'da yayla evleri ve ısı yalıtımı)
- yapı stoku (Suluova'da yeni inşaat)

Anlatacak özgün bir şey yoksa o ilçe için sayfa açma; projeler zaten
`/islerim/` içinde ve kendi sayfalarında görünüyor.

### 5. Hizmet vermediğin bir yerse

Bir bölge sayfası açtın ama orada düzenli hizmet vermiyorsan (örneğin tek
seferlik bir iş yaptıysan), front matter'a şunu ekle:

```yaml
hizmet_bolgesi: false
```

Sayfa yine yayınlanır ve listede görünür, ama Google'a gönderdiğimiz yapısal
veride "hizmet bölgem" olarak geçmez. Örnek: `kadikoy.md`.

### 6. Başka bir şey yapmana gerek yok

Yeni bölge sayfası açtığında **üç yer birden** kendiliğinden güncellenir:

* `/islerim/` sayfasının altındaki bölge bağlantı listesi (sıra `order` ile)
* Sitemap
* **Yapısal veridekiareaServed listesi** — Google'a "buralarda hizmet
  veriyorum" diyen alan. Eskiden `_data/business.yml` içinde elle tutuluyordu,
  artık bölge sayfalarından üretiliyor.

**`order` değeri her bölgede farklı olmalı.** İki bölgeye aynı sayıyı
verirsen sıralama Jekyll'ın dosya okuma sırasına kalır, yani öngörülemez olur.
Şu an kullanımdakiler: 1 Erbaa, 2 Tokat, 3 Turhal, 4 Niksar, 5 Amasya,
6 Taşova, 7 Suluova, 8 Ünye, 9 Akkuş, 10 Kadıköy.

### 7. Kontrol

```bash
bundle _2.7.2_ exec jekyll build
```

Sonra `/zile/` sayfasını aç: proje sayısı doğru mu, `/islerim/` altındaki bölge
listesinde görünüyor mu. Proje çıkmıyorsa `ilce` yazımı tutmuyordur.

Yayınladıktan sonra Google Search Console'da **URL Denetimi → Dizine eklenmesini
iste** demeyi unutma; yeni sayfanın taranması aksi halde haftalar sürer.

---

## Yeni rehber yazısı eklemek

Rehber yazıları `/rehber/` altında yayınlanır ve soru formatlı aramaları
hedefler ("pvc pencere neden rüzgar alır", "cam balkon ısıcam mı").

`_rehber/` klasörüne bir `.md` dosyası aç:

```yaml
---
layout: rehber
order: 7                 # /rehber/ listesindeki sirasi, benzersiz olmali
title: "Çelik Kapı Seçim Rehberi"     # ~40 karakter
heading: "Çelik Kapı Seçim Rehberi"   # sayfadaki h1
subtitle: "Merkezi kilit, sac kalınlığı ve dolgu."   # kart altindaki satir
ozet: "Yazinin basinda vurgulu kutuda cikan giris. 1-2 cumle."
description: "140-160 karakter, arama sonucu aciklamasi."
---

Yazi metni. En az 400 kelime.
```

`/rehber/` liste sayfası ve menü otomatik güncelleniyor, dokunman gerekmiyor.

### Rehber yazısı hizmet sayfasından farklı olmalı

En kritik kural bu. Hizmet sayfası **ne yaptığımızı** anlatır (ticari niyet),
rehber yazısı **nasıl karar verileceğini** anlatır (bilgi niyeti). İkisi aynı
şeyi anlatırsa birbirinin kopyası olurlar.

Mevcut altı yazıda ölçülen örtüşme oranları %11-20 arasında; üst sınır %35.
Yeni yazı eklerken ilgili hizmet sayfasını açıp yan yana oku.

### Her yazıda en az bir iç link

Metnin içinden ilgili hizmet sayfasına link ver. Sayfanın altındaki "Diğer
Rehberler" listesi otomatik, o ayrı.

---

<a id="icerik-standartlari"></a>

# İÇERİK STANDARTLARI — her ekleme öncesi oku

Bu bölüm, sitedeki tüm sayfalara uygulanmış kuralları özetler. Yeni bir
proje, hizmet veya bölge eklerken bunlara uy; sonradan toplu düzeltme yapmak
zorunda kalmayız.

## 1. Kelime sayısı

Sitedeki mevcut durum. **Aralık sütunu her yeni sayfayla değişir**, asıl
bağlayıcı olan son sütundaki alt sınırdır:

| Sayfa tipi | Aralık | Ortalama | Yeni eklerken hedef |
|---|---|---|---|
| Proje | 253-532 | 327 | **en az 280** |
| Bölge | 368-477 | 404 | **en az 350** |
| Hizmet | 416-607 | 496 | **en az 420** |
| Rehber yazısı | 428-493 | 469 | **en az 400** |

Bu sayılar gövde metnini kapsar; başlık, proje grid'i ve hizmet listesi dahil
değildir.

**Alt sınırın altına düşme.** Yeni eklediğin sayfa 150 kelimeyse, o sayfa
"ince içerik" sayılır ve sadece kendisi değil, aynı kategorideki diğer
sayfaların değerini de aşağı çeker.

**Üst sınır için dolgu yazma.** Söyleyecek şey bittiğinde dur. Dolgu metin,
kısa metinden daha zararlıdır — Google bunu "arama motoru için yazılmış
içerik" olarak okur.

## 2. Kopya içerik — en kritik kural

Aynı kategoride onlarca proje sayfası var (PVC, cam balkon ve korkuluk en
kalabalık gruplar). **Aynı kategorideki
sayfalara aynı teknik metni koyarsan hepsi birbirinin kopyası olur.** Google
buna "kapı sayfası" (doorway page) diyor ve tek bir kopya sayfa, aynı gruptaki
bütün sayfaların değerini düşürebilir.

Kural: **her sayfa, o sayfaya özgü tek bir konuyu anlatır ve o konu başka
sayfada tekrar edilmez.**

Mevcut sayfalarda uygulanmış hali — hepsi cam balkon projesi, hiçbiri aynı
şeyi anlatmıyor:

| Proje | Anlattığı konu |
|---|---|
| Tepeşehir | Füme camın işlevi, hangi cephede yanlış tercih |
| Erbaa Füme | Katlanır sistemde kanatların park yeri |
| Erbaa Merkez Füme | Rulman ve ray bakımı |
| Niksar Bağlar | Balkon düz değilse ölçü nasıl alınır |
| Ünye Gölevi | Deniz havasında bakım |
| Karayaka | Koyu profilin ısınması, folyo kalitesi |
| Gazi Osman Paşa | L köşe birleşim profili |
| Amasya Bronz | Bronz profil + şeffaf cam |
| Tokat Isıcamlı | Isıcam ile tek cam farkı |
| Füme + Korkuluk | İki sistemin birlikte tasarlanması |

Yeni bir cam balkon projesi eklerken bu on konudan hiçbirini tekrar etme;
onbirinci bir konu bul (cam temizliği, kanat kilidi, katlanır ile sürme
karşılaştırması, kış kullanımında havalandırma...).

**Ölçüt:** iki sayfanın kelime örtüşmesi %35'i geçmemeli. Şu an sitedeki en
yüksek değer %22.

## 3. İç link — her sayfada zorunlu

Her proje sayfasının gövdesinde **iki link** bulunur:

```markdown
Benzer işlerimiz ve seçenekler için [cam balkon sayfamıza](/hizmetler/cam-balkon/),
bu bölgede yaptığımız diğer işler için [Erbaa sayfamıza](/erbaa/) bakabilirsiniz.
```

Birincisi projenin kategorisine karşılık gelen hizmet sayfası, ikincisi
projenin `ilce` değerine karşılık gelen bölge sayfası. Doğru adresler için
aşağıdaki tabloya bak.

Bölge ve hizmet sayfalarında da metnin **içinden** en az bir bağlamsal link
olmalı. Sayfanın altındaki otomatik listeler ayrı; konu içinde geçen link daha
değerli.

| İlçe | Bölge sayfası | | Kategori | Hizmet sayfası |
|---|---|---|---|---|
| Erbaa | `/erbaa/` | | PVC Kapı Pencere | `/hizmetler/pvc-kapi-pencere/` |
| Tokat | `/tokat/` | | Cam Balkon Sistemleri | `/hizmetler/cam-balkon/` |
| Turhal | `/turhal/` | | Korkuluk Sistemleri | `/hizmetler/korkuluk-kupeste/` |
| Niksar | `/niksar/` | | Banyo Sistemleri | `/hizmetler/dusakabin-banyo/` |
| Amasya | `/amasya/` | | Sineklik Sistemleri | `/hizmetler/sineklik/` |
| Taşova | `/tasova/` | | Alüminyum Doğrama | `/hizmetler/aluminyum-dograma/` |
| Suluova | `/suluova/` | | PVC Sistemleri | `/hizmetler/teras-kapatma-kis-bahcesi/` |
| Ünye | `/unye/` |
| Akkuş | `/akkus/` | | Tamir ve Bakım | `/hizmetler/tadilat-bakim/` |
| Kadıköy | `/kadikoy/` | | Çelik Kapı | `/hizmetler/celik-kapi/` |
| Akkuş | `/akkus/` | | Panjur Sistemleri | `/hizmetler/panjur-kepenk/` |

## 4. Başlık ve açıklama uzunlukları

**`title` — 40-45 karakter.** Sonuna `| Bolatoğlu Yapı` (17 karakter) otomatik
ekleniyor, toplam 60'ı geçmesin. Google 60 karakterden sonrasını keser.

**`description` — 140-160 karakter.** 120'nin altı arama sonucunda yer boşa
harcar, 165'in üstü kesilir. Mevcut sayfalarda aralık 101-169; yeni
eklediklerinde 140-160'ta kal.

**İkisi de her sayfada benzersiz olmalı.** Şu an sitede tek bir tekrar eden
başlık veya açıklama yok, bu durumu koru. İki sayfaya aynı açıklamayı yazmak,
Google'a "bu iki sayfa aynı" demektir.

## 5. Başlık yapısı

* Her sayfada **tek bir `h1`** olur. Bunu layout otomatik üretir, gövdeye
  `# Başlık` yazma.
* Gövdede `##` ile başla, alt kırılım için `###` kullan.
* `##` olmadan `###` kullanma.
* Proje sayfalarında mevcut yapı: `## Proje Hakkında` → `### Teknik Detaylar`
  → `### [sana özgü konu]` → `### Sonuç`

## 6. Ne uydurulur, ne uydurulmaz

**Uydurma:** müşteri adı, iş süresi, fiyat, yapılmamış iş, proje sayısı,
"X yılda Y iş yaptık" gibi sayılar, sahip olmadığın belge veya yetki
("yetkili bayi" gibi). Bunlar bir müşteri sorduğunda seni zor durumda bırakır.

**Serbest:** sektör bilgisi ve teknik anlatım. Malzeme özellikleri, montaj
yöntemleri, bakım önerileri, "neye dikkat edilmeli" tarzı içerik. Bunlar hem
doğru hem müşterinin işine yarıyor ve kelime sayısını rahatça dolduruyor.

**Dikkatli ol:** işleyişe dair cümleler ("keşif ücretsiz", "kenar düzeltmesi
montaja dahil", "kışın yaylaya montaj yapmıyoruz"). Bunlar doğruysa yaz, ama
müşteri okuyup ona göre gelir.

## 7. Ekleme sonrası kontrol listesi

```bash
bundle _2.7.2_ exec jekyll build
```

`Error` veya `Conflict` çıkmamalı (Sass uyarıları normal). Sonra sırayla:

- [ ] Sayfa kendi adresinde açılıyor mu
- [ ] `/islerim/` listesinde görünüyor mu (proje ekledinse)
- [ ] İlgili hizmet sayfasında sayı bir arttı mı → artmadıysa `category` yazımı
- [ ] İlgili bölge sayfasında sayı bir arttı mı → artmadıysa `ilce` yazımı
- [ ] `/hizmetler/` sayfasında hiçbir kart boş kalmış mı
- [ ] Gövdede iki iç link var mı
- [ ] Kelime sayısı alt sınırın üstünde mi
- [ ] Aynı kategorideki başka bir sayfayla aynı konuyu anlatmıyor mu
- [ ] Başlık 45, açıklama 160 karakteri geçmiyor mu

Yayınladıktan sonra Google Search Console → **URL Denetimi** → yeni adresi
yaz → **Dizine eklenmesini iste**.
