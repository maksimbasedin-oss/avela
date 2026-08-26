# Demo Modest — Shopify demo kataloğu

Bu klasör **Demo Modest** adlı DEMO tesettür kataloğunu içerir. Kayıtlar tema testine hizmet eder. Gerçek marka, gerçek stok, gerçek satış, gerçek yorum veya gerçek görsel URL’si yoktur.

## Dosyalar

- `shopify-products.csv` — Shopify ürün içe aktarma (UTF-8)
- `demo-products.json` — zengin ürün verisi
- `demo-collections.json` — koleksiyon SEO ve ürün eşlemesi
- `demo-blog.json` — 5 DEMO yazı
- `README.md` — bu dosya

Vendor: **Demo Modest**. Daha sonra Admin’den toplu değiştirilebilir.

## 1. Ürünleri içe aktarma

1. Shopify Admin → **Products → Import**.
2. `shopify-products.csv` dosyasını seçin.
3. Para birimi mağazada **TRY** değilse fiyatlar yine sayı olarak gelir; para birimini Settings → Markets / Payments üzerinden ayrı ayarlayın.
4. Görsel sütunları boş bırakıldı. Sahte URL yoktur. İçe aktarım sonrası ürün düzenleyiciden görsel ekleyin.
5. Metafield sütunları (`product.metafields.custom.*`) tanımlı değilse Shopify gevşek metafield oluşturabilir. Tercihen önce **Settings → Custom data → Products** altında `custom` ad alanında şu anahtarları tanımlayın: `material`, `fit`, `length`, `model_height`, `model_size`, `fabric`, `care`, `season`, `style`, `occasion`.
6. Mevcut Avela temasında `fit`, `length`, `fabric`, `model_size`, `care` zaten kullanılıyor. `stretch` ve `size_chart` bu CSV’de yoktur; gerekirse sonra ekleyin.

## 2. CSV kullanımı

- Kodlama: **UTF-8**. Excel’de Türkçe bozulursa Numbers, Google Sheets veya `iconv` ile açın; kaydederken UTF-8 seçin.
- Klasik sütun adları kullanıldı: `Handle`, `Title`, `Body (HTML)`, `Variant Price` vb. Shopify hâlâ bunları kabul eder.
- Her varyant ayrı satırdır. Aynı `Handle` aynı üründür.
- `Image Src` boştur. `Image Alt Text` yalnızca ilk satırda planlanan ana görsel metnidir.
- `Variant Inventory Policy` = `deny` → adet 0 olan varyant **Tükendi** görünür.
- Karşılaştırma fiyatı yalnızca indirim rozetli 5 üründedir.

## 3. Koleksiyonları oluşturma

`demo-collections.json` içindeki handle’larla Admin’de koleksiyon açın veya otomatik koleksiyon kullanın.

Önerilen otomatik kurallar (tag):

| Koleksiyon | Kural |
|---|---|
| Yeni Sezon | tag `yeni-sezon` |
| Çok Satanlar | tag `cok-satan` |
| İndirim | tag `indirim` |
| Tesettür Elbise | product type `Tesettür Elbise` |
| Tesettür Tunik | product type `Tesettür Tunik` |
| Tesettür Takım | product type `Tesettür Takım` |
| Tesettür Pantolon | product type `Tesettür Pantolon` |
| Tesettür Ferace | product type `Tesettür Ferace` |
| Tesettür Kap | product type `Tesettür Kap` |
| Tesettür Pardesü | product type `Tesettür Pardesü` |
| Tesettür Abiye | product type `Tesettür Abiye` |
| Dış Giyim | tag `dis-giyim` |
| Şal & Eşarp | product type `Şal` OR `Eşarp` |
| Jile & Yelek | product type `Tesettür Jile` OR `Tesettür Yelek` |

JSON’daki `description`, `seo_title` ve `seo_description` alanlarını koleksiyon SEO formuna kopyalayın. Tema, koleksiyon açıklamasını intro olarak gösterir.

Mevcut mağazada `yeni-sezon`, `tesettur-elbise`, `tesettur-takim`, `tesettur-tunik`, `tesettur-pantolon`, `dis-giyim`, `sal-esarp`, `cok-satanlar` handle’ları varsa üzerine yazmayın; kuralı güncelleyin. `tesettur-ferace`, `tesettur-kap`, `tesettur-pardesu`, `tesettur-abiye`, `jile-yelek`, `indirim` yeni açılmalıdır.

## 4. Demo blog

Admin → **Online Store → Blog posts**.

1. Blog: `stil-rehberi` (yoksa oluşturun).
2. `demo-blog.json` içindeki 5 yazıyı başlık, handle, özet ve gövde ile ekleyin.
3. SEO title / description alanlarını yazı SEO’suna yapıştırın.
4. Görsel eklemeyin veya kendi DEMO görselinizi yükleyin. URL uydurmayın.

## 5. Demo veriyi temizleme

- Products’ta vendor **Demo Modest** ile filtreleyin ve silin.
- DEMO koleksiyonları (özellikle `indirim`, `tesettur-ferace`, `jile-yelek` vb.) silin veya otomatik kuralı kapatın.
- Blog yazılarını `stil-rehberi` altından silin.
- CSV ile gelen metafield tanımlarını kullanmayacaksanız Custom data’dan kaldırın.

Mağazada daha önce oluşturulan 7 Avela ürünü bu CSV’de yoktur. Temizlik yalnızca Demo Modest kaydını hedefler.

## 6. Gerçek ürüne geçerken

Değiştirin:

- Vendor ve marka adı
- Fiyat ve para birimi
- Stok adetleri ve konum
- Görseller ve alt metin
- Ürün / SEO metinleri (DEMO ibaresini çıkarın)
- Compare-at (yalnızca gerçek indirimde)
- Çok satan / yeni etiketleri (gerçek merch kararına göre)
- Metafield ölçü ve kumaş bilgileri
- Koleksiyon açıklamaları

Kaldırın:

- Açıklamadaki “DEMO üründür” cümlesi
- Sahte satış veya yorum iddiası (zaten yok)
- Test amaçlı tükendi varyantları

Eklemeyin:

- Uydurma görsel URL
- Uydurma yorum / puan
- Arama hacmi cümlesi

## Rozet testi

Tema etiketlerden okur:

- `yeni-sezon` → Yeni (8 ürün)
- `cok-satan` → Çok satan (7 ürün)
- compare-at dolu + `indirim` → İndirim (5 ürün)
- `sinirli-stok` + düşük adet → stok az UI (3 ürün)
- 7 üründe rozet yok

## Doğrulama özeti

- 30 benzersiz ürün
- Benzersiz handle ve varyant SKU
- Renk + beden varyantları
- Bazı beden/renk tükendi
- UTF-8
- Görsel URL yok
