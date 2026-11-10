<div align="center">
  <p><strong>Hazırlayan: Mustafa Kemal Yazlık</strong></p>
  <h1>🎨 Hafta 07</h1>
  <h3>CSS’e Giriş · Seçiciler · Görsel Biçimlendirme</h3>
  <p>
    <img src="https://img.shields.io/badge/CSS-Temeller-663399?style=flat-square&amp;logo=css&amp;logoColor=white" alt="CSS Temelleri" />
    <img src="https://img.shields.io/badge/HTML5-Uygulama-E34F26?style=flat-square&amp;logo=html5&amp;logoColor=white" alt="HTML5 Uygulamaları" />
    <img src="https://img.shields.io/badge/DevTools-Stil_İnceleme-2563EB?style=flat-square" alt="DevTools ile stil inceleme" />
  </p>
  <p><strong>Bir HTML öğesinin görünümünü hangi CSS kuralının belirlediğini tarayıcıda adım adım incele.</strong></p>
</div>

---

[← Haftalık ilerleme matrisi](../README.md) · [Önceki hafta · HTML5](../hafta-06/README.md)

## 📖 Genel Bakış

Bu hafta CSS’in HTML öğelerinin görünümünü nasıl değiştirdiği ele alındı. Harici, dahili ve satır içi stil ekleme yöntemleri karşılaştırıldı. Etiket, ID ve sınıf seçicileriyle öğelerin nasıl seçildiği ve birden fazla kural aynı özelliği belirlediğinde hangisinin uygulandığı örneklerle gösterildi. Renk ve kalıtım, arka plan görselleri, kenarlıklar ve metin biçimlendirme üzerinde çalışıldı. Sabit boyutlu kutularda taşan içeriğin nasıl yönetildiği ve `padding` ile `margin` arasındaki fark incelendi.

### 🧭 İçindekiler

| Bölüm | Bu bölümde neler var? |
| --- | --- |
| [01 · Harici CSS](#01--harici-css-ve-etiket-seçicisi) | `<link>`, göreli yol, etiket seçicisi |
| [02 · Dahili ve satır içi CSS](#02--dahili-ve-satır-içi-css) | `<style>`, `style` ve aynı özelliğin çakışması |
| [03 · Boş kutu ve yükseklik](#03--boş-bir-kutu-ve-yükseklik) | Arka planın görünmesi için kutunun ölçüsü |
| [04 · ID ve Class](#04--id-ve-class-ile-öğeleri-seçmek) | Etiket, ID, sınıf ve seçici özgüllüğü |
| [05 · Bildirim önceliği](#05--bildirim-önceliği-ve-important) | Normal bildirimler ve `!important` |
| [06 · Renk ve kalıtım](#06--renkler-arka-plan-ve-kalıtım) | Renk adı, HEX, RGB ve `body` üzerinden kalıtım |
| [07 · Arka plan görseli](#07--arka-plan-görseli-tekrar-ve-boyutlandırma) | `url()`, tekrar, boyut ve konum |
| [08 · Kenarlıklar](#08--kenarlıklar-ve-kısa-yazım) | Kalınlık, stil, renk, tek kenar ve köşe yarıçapı |
| [09 · Metin biçimlendirme](#09--metin-hizalama-çizgiler-ve-yazı-tipi) | Hizalama, metin çizgileri, yazı tipi ve ilk satır girintisi |
| [10 · Metin taşması](#10--sabit-yükseklik-ve-taşma) | `overflow`, sabit yükseklik ve kaydırma |
| [11 · Yazı stili ve satır yüksekliği](#11--yazı-stili-ve-satır-yüksekliği) | `font-style` ve `line-height` |
| [12 · Kutu boşlukları](#12--kutu-boşlukları-ve-kutu-modeli) | `padding`, `border`, `margin` ve `margin-left` |
| [📁 Uygulama dosyaları](#-uygulama-dosyaları) | Tarayıcıda açılabilen örnekler |
| [🧪 Ek uygulama](#-ek-uygulama) | Derste gösterilen örnekleri tamamlayan yorumlu CSS denemeleri |

---

## 01 · Harici CSS ve Etiket Seçicisi

Geçen haftanın HTML örnekleri açıldıktan sonra yeni bir HTML dosyası ve ayrı bir CSS dosyası oluşturuldu. HTML içerikteki öğeleri tanımlar. CSS ise renk, boyut ve boşluk gibi görünüm özelliklerini belirler.

CSS dosyasını HTML ile aynı klasöre koymak, tarayıcının stilleri uygulaması için tek başına yeterli değildir. HTML belgesinin `<head>` bölümüne şu bağlantı eklenir.

```html
<link rel="stylesheet" href="./01-harici-css.css" />
```

| Parça | Görevi |
| --- | --- |
| `rel="stylesheet"` | Bağlantının bir stil dosyası olduğunu bildirir. |
| `href="./01-harici-css.css"` | Stil dosyasının HTML dosyasına göre konumunu gösterir. |
| `p` | Sayfadaki bütün paragraf öğelerini seçer. |
| `background-color: aqua;` | Eşleşen öğelere bir arka plan rengi uygular. |

```css
p {
  background-color: aqua;
  color: orangered;
}
```

Seçici, kuralların uygulanacağı öğeleri belirler. Süslü ayraçlar içindeki her bildirimde özellik ve değer iki noktayla ayrılır. Birden çok bildirim yazıldığında noktalı virgül bir bildirimi sonrakinden ayırır.

> [!TIP]
> [Uygulamayı](./01-harici-css.html) tarayıcıda aç. İki paragrafın da arka planı renklidir. Başlık ve yatay çizgi aynı kuraldan etkilenmez. `<link>` satırını geçici olarak kaldırıp sayfayı yenileyerek bağlantının etkisini görebilirsin.

---

## 02 · Dahili ve Satır İçi CSS

Harici stil bağlantısı devre dışı bırakıldıktan sonra aynı paragraf kuralı bu kez HTML dosyasının `<head>` bölümündeki `<style>` bloğuna yazıldı. Mavi yazı ve sarı arka plan yine bütün paragraflara uygulandı. Ardından bir paragrafın kendi `style` niteliğiyle tek bir öğenin görünümü değiştirildi.

| Yöntem | Nerede yazılır? | Etki alanı |
| --- | --- | --- |
| Harici (external) | Ayrı `.css` dosyasında. HTML, dosyayı `<link>` ile yükler. | Dosyayı yükleyen sayfalardaki eşleşen öğeler |
| Dahili (internal) | HTML belgesindeki `<style>` bloğunda | O belgedeki eşleşen öğeler |
| Satır içi (inline) | Öğenin açılış etiketindeki `style` niteliğinde | Yalnızca o öğe |

```html
<!-- head bölümünde -->
<style>
  p {
    color: blue;
    background-color: yellow;
  }
</style>

<!-- body bölümünde -->
<p>Yazı mavi, arka plan sarı.</p>
<p style="color: red">Yazı kırmızı, arka plan yine sarı.</p>
```

> [!IMPORTANT]
> Örnekte iki stil aynı paragrafın `color` özelliğini belirler. Satır içindeki normal renk bildirimi, dahili seçicinin normal bildirimine üstün gelir. `background-color` için satır içi bildirim yazılmadığı için sarı arka plan uygulanmaya devam eder.

🔗 [Dahili ve satır içi stilleri karşılaştır](./02-dahili-ve-satir-ici-css.html)

---

## 03 · Boş Bir Kutu ve Yükseklik

Derste boş bir `<div>` öğesine `background-color: darkslategray;` verildi. Öğenin içeriği ve yüksekliği bulunmadığı için renk ekranda görünmedi. `height: 30px;` eklendiğinde arka planı boyayacak bir alan oluştu.

```css
div {
  background-color: darkslategray;
  height: 30px;
}
```

[Uygulamada](./03-bos-div.html) iki boş kutu art arda gösterilir. Ortak kural iki kutuya da aynı arka planı verir. Yalnız ikinci kutuya yükseklik verildiği için renk o kutuda görünür.

Bu örneğin ardından stil dosyalarının tema değiştirmek için de kullanılabileceği anlatıldı. Sayfanın HTML içeriği aynı kalırken yüklenecek CSS dosyası değiştirilerek renk ve görünüm değiştirilebilir.

---

## 04 · ID ve Class ile Öğeleri Seçmek

Etiket seçicisi bütün paragrafları kapsar. Derste ikinci paragrafa `id="haber"` verilerek tek bir öğe seçildi. CSS tarafında ID seçicisinin başında `#` kullanıldı. Bir HTML belgesinde aynı ID yalnızca bir öğeye verilmelidir.

```html
<p>Genel paragraf</p>
<p id="haber">Haber metni</p>
```

```css
#haber {
  color: white;
  background-color: forestgreen;
}

p {
  color: navy;
}
```

İki seçici de haber paragrafına uyar. İkisi de `color` özelliğine değer verdiğinde `#haber` daha özgül olduğu için beyaz yazı uygulanır. Bu örnekte `p` kuralının dosyada daha aşağıda bulunması sonucu değiştirmez. Derste art arda iki `p` kuralı yazıldığında ise ikisi eşit özgüllükteydi. Sonraki kural yalnız `background-color` değerini değiştirdi. İlk kuraldaki yazı rengi geçerli kaldı.

Ardından bir görünümü birden çok öğede kullanmak için sınıf tanımlandı. HTML’de `class="arka-plan"`, CSS’te ise `.arka-plan` yazılır. Aynı sınıf hem bir paragrafa hem bir `<div>` öğesine verilebilir. Uygulamada haber paragrafı hem `#haber` hem `.arka-plan` ile eşleşir. Çakışan arka plan rengini daha özgül olan ID kuralı belirler. Sınıfın `font-weight` bildirimi ise başka bir bildirimle çakışmadığı için uygulanır.

| Seçici | Eşleştiği öğeler |
| --- | --- |
| `p` | Tüm paragraf öğeleri |
| `#haber` | `id="haber"` olan öğe |
| `.arka-plan` | `class` listesinde `arka-plan` bulunan bütün öğeler |

🔗 [Etiket, ID ve sınıf seçicilerini karşılaştır](./04-id-ve-class.html)

---

## 05 · Bildirim Önceliği ve !important

Örnekte `!important` ile bir arka plan bildiriminin önceliği değiştirildi. İşaretli sınıf bildirimi, ID seçicisinin normal bildirimine üstün geldi. Ardından aynı fark satır içi yazı rengiyle denendi.

```css
.oncelikli {
  color: blue !important;
}
```

```html
<p class="oncelikli" style="color: darkgoldenrod">Bu yazı mavi görünür.</p>
```

Normal satır içi bildirim, aynı yazarın normal stil kurallarına üstün gelir. Bu örnekte CSS kuralındaki `color` bildirimi `!important` olduğu için normal satır içi renk yerine mavi uygulanır. İşaret yalnızca yazıldığı bildirimin önceliğini değiştirir.

Derste bir sonraki adımda ID kuralına da `!important` eklendi. İki bildirim aynı yazar stilinde ve aynı önem düzeyinde olduğunda daha özgül seçici kazanır. Bu yüzden uygulamadaki haber paragrafı beyaz görünür.

> [!TIP]
> [İlk iki paragrafı karşılaştır](./05-important.html). Ardından `!important` ifadesini kaldırıp sayfayı yenile. İki paragrafın rengini de satır içi bildirim belirler.

---

## 06 · Renkler, Arka Plan ve Kalıtım

CSS’te renkler adlarıyla, HEX kodlarıyla veya RGB değerleriyle belirtilebilir. Editördeki renk paleti bu değerleri seçmeyi kolaylaştırır. `background-color` bir alanın arka planını, `color` yazının rengini değiştirir.

| Renk biçimi | Örnek | Nasıl okunur? |
| --- | --- | --- |
| Renk adı | `aqua` | CSS’in tanıdığı hazır renk adı |
| HEX | `#00ffff` | Kırmızı, yeşil ve mavi kanalları için onaltılık değerler |
| RGB | `rgb(0, 255, 255)` | Aynı üç kanalın sayısal değerleri |

Tablodaki üç gösterim aynı rengi verir. Derste HSL ve alfa kanallı RGBA gösterimleri de anıldı. Alfa kanalı rengin opaklığını belirler. Editörde renk kutusuna tıklandığında açılan paletten bir ton seçilebilir. Düzenleyici seçilen rengi HEX veya RGB gibi bir biçimde koda yazar.

```css
body {
  background-color: #17365d;
  color: yellow;
}

.ornek {
  background-color: rgb(224, 242, 254);
  color: #17365d;
}
```

`body` için verilen arka plan sayfa genelinde görünür. `color` ise kalıtılabilir. Alt öğe kendi rengini belirlemiyorsa üst öğenin rengini devralır. Derste bazı paragrafların sarıya dönmemesi, o paragraflarda önceden tanımlanmış renk bildirimleri olmasından kaynaklanıyordu.

| Seçici | Hangi öğeye doğrudan kural uygular? |
| --- | --- |
| `body` | Sayfanın gövde öğesine |
| `body p` | Gövdenin içindeki paragraf öğelerine |
| `body, p` | Hem gövdeye hem paragraf öğelerine |

🔗 [Sayfa ve paragraf renklerini karşılaştır](./06-renkler-ve-kalitim.html)

---

## 07 · Arka Plan Görseli, Tekrar ve Boyutlandırma

Bir `<div>` kutusunun arka planına `background-image: url("…");` ile görsel eklenir. Bu uygulama tam bir HTTPS adresi kullanır. Göreli yol yazıldığında, yol harici CSS’te stil dosyasının konumuna, dahili CSS’te ise HTML belgesinin konumuna göre çözülür.

```css
.ornek {
  min-height: 200px;
  background-color: #e2e8f0;
  background-image: url("https://i.hizliresim.com/rwludxz7.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
```

| Özellik | Örnek | Etkisi |
| --- | --- | --- |
| `background-repeat` | `repeat`, `repeat-x`, `repeat-y`, `no-repeat` | Görselin iki eksende, yalnız yatayda, yalnız dikeyde veya hiç tekrar etmemesini belirler. |
| `background-size` | `auto`, `110px auto`, `cover` | Görseli kendi ölçülerinde bırakır, genişliğe göre ölçekler veya alanı kaplatır. |
| `background-position` | `center` | Görseli kutunun merkezine hizalar. |

`cover`, görselin en-boy oranını koruyarak kutuyu doldurur. Görsel ile kutunun oranları farklıysa görselin bir bölümü kırpılabilir. Derste görsel ilk boyutunda gösterildiğinde kutuda fotoğrafın yalnızca bir bölümü görünüyordu. Boyutlandırma kuralı değiştirilince görüntü daha belirgin hâle geldi. Arka plan görseli boş bir kutuya kendi başına yükseklik kazandırmaz.

> [!TIP]
> Görsel görünmüyorsa DevTools’ta önce öğenin ölçüsünü ve uygulanan `background-image` değerini, ardından görsel isteğinin yüklenip yüklenmediğini kontrol et. Bir görsel adresinin çalışması, adresin `.jpg` ile bitmesine bağlı değildir.

🔗 [Tekrarlanan, ortalanan ve alanı kaplayan görselleri karşılaştır](./07-arka-plan-gorseli.html)

---

## 08 · Kenarlıklar ve Kısa Yazım

Arka plan örneğindeki kutunun başlangıç ve bitiş noktalarını görmek için `border` kullanıldı. Önce kenarlığın stili, rengi ve kalınlığı ayrı özelliklerle denendi.

| Özellik | Örnek | Görevi |
| --- | --- | --- |
| `border-style` | `solid`, `dotted`, `dashed`, `double`, `none` | Kenarlığın düz, noktalı, kesik, çift çizgili veya görünmez olmasını belirler. |
| `border-width` | `10px` | Çizginin kalınlığını belirler. |
| `border-color` | `brown` | Çizginin rengini belirler. |
| `border-left` | `10px solid brown` | Kısa yazımı yalnızca sol kenara uygular. |

```css
.kutu {
  border-width: 10px;
  border-style: solid;
  border-color: brown;
}

/* Yukarıdaki üç bildirimin kısa yazımı */
.kutu {
  border: 10px solid brown;
}
```

> [!NOTE]
> Renk ve kalınlık verilse bile çizgi stili `none` olarak kalırsa görünür bir kenarlık oluşmaz. Yalnız belirli bir kenarı çizmek için `border-top`, `border-right`, `border-bottom` veya `border-left` kullanılabilir.

Derste kutunun içerik alanına `width: 200px;` ve `height: 200px;` verildi. Ardından `border-radius: 30px;` ile dört köşe aynı ölçüde yuvarlatıldı. Değer 5 piksele düşürüldüğünde köşelerdeki eğim azaldı.

🔗 [Çizgi türlerini, tek kenarı ve yuvarlatılmış köşeleri karşılaştır](./08-kenarliklar.html)

---

## 09 · Metin Hizalama, Çizgiler ve Yazı Tipi

Bir paragraf önce sayfanın tamamına göre hizalandı. Ardından bir `<div>` içine taşındı. `text-align: center;` bu kez metni paragrafın kutusu içinde ortaladı. Kutunun konumu aynı kaldı.

| Özellik | Örnek | Etkisi |
| --- | --- | --- |
| `text-align` | `left`, `center`, `right`, `justify` | Metni sola, ortaya, sağa veya iki yana hizalar. |
| `text-decoration` | `underline`, `overline`, `line-through` | Metnin altına, üstüne veya ortasına çizgi ekler. |
| `font-weight` | `normal`, `bold`, `700` | Yazının ağırlığını belirler. Kullanılan yazı tipi farklı ağırlıkları aynı görünüme eşleyebilir. |
| `font-family` | `Arial, sans-serif` | Yazı tipi listesini belirler. Arial yoksa tarayıcı sans-serif bir yazı tipi seçer. |
| `text-indent` | `30px` | Paragrafın ilk satırını içeri alır. |

```css
.kutu p {
  text-align: left;
  font-family: Arial, sans-serif;
  font-weight: 700;
  text-indent: 30px;
}
```

🔗 [Bir kutu içinde hizalamayı ve metin çizgilerini karşılaştır](./09-metin-bicimlendirme.html)

---

## 10 · Sabit Yükseklik ve Taşma

Girinti örneğinde paragraf uzadığında kutu sabit yüksekliğe sahip olduğu için metin kutunun dışına taştı. Yükseklik kaldırıldığında kutu içeriğine göre büyüdü. Yüksekliğin sabit kalması gerekiyorsa `overflow` ile taşan içeriğin davranışı belirlenebilir.

| Değer | Davranış |
| --- | --- |
| `visible` | Varsayılan davranışta taşan metin kutu dışında görünür. |
| `auto` | Gerektiğinde kaydırma yapılabilmesini sağlar. |
| `scroll` | Taşma miktarından bağımsız olarak bir kaydırma alanı oluşturur. |
| `hidden` | Kutuyu aşan kısmı kırpar ve kullanıcıya kaydırma çubuğu göstermez. |

```css
.kutu {
  height: 4rem;
  overflow: auto;
}
```

🔗 [Kaydırılan ve gizlenen metni karşılaştır](./10-metin-tasmasi.html)

---

## 11 · Yazı Stili ve Satır Yüksekliği

Taşma örneğinden sonra metin `font-style: italic;` ile eğik gösterildi. Ardından birden çok satıra yayılan paragrafın `line-height` değeri artırıldı.

```css
.ornek {
  font-style: italic;
  line-height: 30px;
}
```

`font-style` yazının biçimini, `line-height` her satır için ayrılan yüksekliği belirler. Aynı yazı boyutunda satır yüksekliğini 20 pikselden 30 piksele çıkarmak, satırların birbirinden daha uzak görünmesini sağlar.

🔗 [İtalik biçimi ve satır yüksekliği farkını incele](./11-yazi-stili-ve-satir-yuksekligi.html)

---

## 12 · Kutu Boşlukları ve Kutu Modeli

Son uygulamada aynı kutuya önce `padding: 30px;`, ardından dış boşluk için `margin: 50px;` verildi. Son adımda dış boşluk yalnız sol kenara uygulandı.

| Katman | Konumu |
| --- | --- |
| İçerik | Yazı veya diğer öğelerin bulunduğu alan |
| `padding` | İçerik ile kenarlık arasındaki iç boşluk |
| `border` | İç boşluğu ve içeriği çevreleyen kenarlık |
| `margin` | Kenarlığın dışındaki boşluk |

```css
.kutu {
  padding: 30px;
  border: 2px solid #1d4ed8;
  margin-left: 50px;
}
```

> [!TIP]
> [Örneği](./12-padding-ve-margin.html) aç ve mavi kutuyu DevTools’ta seç. Kutu modeli görünümünde dört kenardaki 30 px iç boşluğu ve yalnız soldaki 50 px dış boşluğu ayrı ayrı görebilirsin.

---

## 📁 Uygulama Dosyaları

HTML dosyalarını depo klasöründen doğrudan tarayıcıda açabilirsin. Arka plan uygulaması, [çevrimiçi araba görselini](https://i.hizliresim.com/rwludxz7.jpg) kullanır.

| Dosya | İçerik |
| --- | --- |
| [`01-harici-css.html`](./01-harici-css.html) | Ayrı stil dosyasını bağlama |
| [`02-dahili-ve-satir-ici-css.html`](./02-dahili-ve-satir-ici-css.html) | Dahili ve satır içi stilleri karşılaştırma |
| [`03-bos-div.html`](./03-bos-div.html) | Boş bir öğeye yükseklik verme |
| [`04-id-ve-class.html`](./04-id-ve-class.html) | Özgüllük ve eşit kurallarda yazım sırası |
| [`05-important.html`](./05-important.html) | Satır içi stil ile `!important` karşılaştırması |
| [`06-renkler-ve-kalitim.html`](./06-renkler-ve-kalitim.html) | Sayfa rengi ve öğeye özel renk |
| [`07-arka-plan-gorseli.html`](./07-arka-plan-gorseli.html) | Görseli tekrarlama ve alanı kaplatma |
| [`08-kenarliklar.html`](./08-kenarliklar.html) | Kenarlık çizgileri ve yuvarlatılmış kutu |
| [`09-metin-bicimlendirme.html`](./09-metin-bicimlendirme.html) | Metin özelliklerini karşılaştırma |
| [`10-metin-tasmasi.html`](./10-metin-tasmasi.html) | Taşan metni kaydırma ve gizleme |
| [`11-yazi-stili-ve-satir-yuksekligi.html`](./11-yazi-stili-ve-satir-yuksekligi.html) | İtalik yazı ve farklı satır yükseklikleri |
| [`12-padding-ve-margin.html`](./12-padding-ve-margin.html) | İç ve dış boşluğu aynı kutuda karşılaştırma |
| [`01-harici-css.css`](./01-harici-css.css) | İlk uygulamanın yüklediği harici stil dosyası |

---

## 🧪 Ek Uygulama

> [!NOTE]
> Bu bölümdeki ek konular derste işlenmedi. 7. haftada öğrenilen CSS konularını pekiştirmek ve sonraki uygulamalarda işine yarayacak ayrıntıları görmek için hazırlandı.

[**Tamamlayıcı CSS Laboratuvarı**](./ek-uygulamalar/01-css-tamamlayici.html) bağımsız bir çalışma dosyasıdır. Birleşik seçicileri, `box-sizing` hesabını, esnek genişliği ve klavye odağını içerir. [Ek uygulamalar rehberinde](./ek-uygulamalar/README.md) her deneyde neyi gözlemleyeceğini bulabilirsin.

---

<div align="center">
  <p><strong>Hafta 07 · CSS Uygulamaları</strong></p>
  <sub>Hazırlayan: Mustafa Kemal Yazlık</sub>
</div>
