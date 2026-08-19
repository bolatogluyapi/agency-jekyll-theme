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
| `location` | Meta şeridindeki "Konum". |
| `date` | **Sıralamayı bu belirler.** Yeni tarih en üste çıkar. `YYYY-AA-GG`. |
| `category` | **Hangi hizmet sayfasında görüneceğini belirler.** Aşağıya bak. |
| `client` | İsteğe bağlı. Yazmazsan meta şeridinde hiç görünmez. |
| `description` | Arama sonucundaki açıklama. 140-160 karakter ideal. |
| `alt` | Görsel açıklaması. Görsel aramada işe yarar, boş bırakma. |
| `image` | **Link paylaşıldığında çıkan önizleme görseli.** Proje sayfalarında o işin fotoğrafı, diğer tüm sayfalarda logo kullanılır. Değeri `caption.thumbnail` ile aynı olmalı. |

`order` diye bir alan yok, sıralama tamamen `date` ile.

## 4. Kategori listesi — TAM OLARAK böyle yazılmalı

`category` alanına aşağıdaki sekiz değerden **birini** yaz. Harfi harfine
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

Çelik kapı işi eklersen yeni bir kategori gerekir; o zaman
`_hizmetler/celik-kapi.md` içindeki `categories: []` satırını
`categories: ["Çelik Kapı"]` yapıp projeye de aynı değeri yaz.

Bu liste `_hizmetler/*.md` dosyalarındaki `categories` alanlarından gelir.
Şüphedeysen ilgili hizmet dosyasını açıp oraya bak — asıl kaynak orası.

## 5. Kontrol et

```bash
bundle _2.7.2_ exec jekyll build
```

Uyarı çıkmamalı. Sonra `bundle _2.7.2_ exec jekyll serve` ile:

- `/islerim/` — yeni proje en üstte mi (tarih en yeniyse)
- `/hizmetler/<ilgili-sayfa>/` — proje sayısı bir artmış mı

İkincisi artmadıysa `category` yazımı tutmuyordur.

## 6. Yayınla

```bash
git add -A
git commit -m "Yeni proje: erbaa cumhuriyet cam balkon"
git push
```

Push sonrası GitHub Actions siteyi otomatik yayına alır.

---

## Yeni bir hizmet eklemek

`_hizmetler/` klasörüne `.md` dosyası aç:

```yaml
---
title: "Erbaa ... Sistemleri"     # arama sonucu basligi, ~40 karakter
heading: "... Sistemleri"          # sayfadaki h1 ve kart basligi
subtitle: "Tek cumlelik ozet"      # kartin altindaki aciklama
description: "140-160 karakter."
icon: fas fa-tools                 # fontawesome.com/icons
order: 10                          # kartlarin sirasi
categories:
  - "İlgili Kategori"
---

Hizmet metni buraya.
```

Ana sayfadaki hizmet kartları ve `/hizmetler/` sayfası bu klasörden
otomatik beslenir, ayrıca bir yere eklemen gerekmez.

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
order: 8                 # link sirasindaki yeri
ilce: "Zile"             # projelerdeki ilce degeriyle ayni
title: "Zile PVC Pencere ve Cam Balkon"    # arama sonucu basligi, ~40 karakter
heading: "Zile"                            # sayfadaki h1
subtitle: "Zile'de tamamladığımız işler."  # h1 altindaki tek satir
description: "140-160 karakter, arama sonucu aciklamasi."
---

Buraya o ilçeye özgü metin yaz. En az 100 kelime olsun.
```

### 3. ÖNEMLİ: metin gerçekten farklı olmalı

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

### 4. Başka bir şey yapmana gerek yok

`/islerim/` sayfasının altındaki bölge listesi `layout: bolge` olan tüm
sayfalardan otomatik üretilir. Sıralama `order` alanına göre. Sitemap'e de
kendiliğinden girer.

### 5. Kontrol

```bash
bundle _2.7.2_ exec jekyll build
```

Sonra `/zile/` sayfasını aç: proje sayısı doğru mu, `/islerim/` altındaki bölge
listesinde görünüyor mu. Proje çıkmıyorsa `ilce` yazımı tutmuyordur.

Yayınladıktan sonra Google Search Console'da **URL Denetimi → Dizine eklenmesini
iste** demeyi unutma; yeni sayfanın taranması aksi halde haftalar sürer.
