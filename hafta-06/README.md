# 🌐 Hafta 06: Tablolar, Multimedya, Form Mimarisi ve Semantik HTML5

![Modül](https://img.shields.io/badge/Modül-İleri_HTML5_Bileşenleri-E34F26?style=flat-square&logo=html5&logoColor=white)
![Protokol](https://img.shields.io/badge/İnceleme-HTTP_POST_&_Payload-232F3E?style=flat-square)
![Standart](https://img.shields.io/badge/Standart-W3C_Semantic_Web-blue?style=flat-square)

Bu modülde; ilişkisel veri tablolarının oluşturulması ve hücre birleştirme teknikleri (`rowspan`/`colspan`), HTML5 yerel video ve ses yürütücüleri, sunucuyla etkileşimli form kontrolleri (`GET`/`POST`, DevTools Payload analizi) ile blok/satır-içi (inline) ve semantik sayfa mizanpajı ele alınmıştır.

> [!NOTE]
> HTML sayfalarında biçimlendirme ve sunum (renk, kenarlık, konumlandırma) modern web standartlarında **CSS** sorumluluğundadır. Ancak HTML etiketlerinin semantik doğru kullanımı; arama motoru optimizasyonu (SEO), tarayıcı erişilebilirliği ve veri bütünlüğü açısından temel gerekliliktir.

---

## 📑 Ders Konu Başlıkları ve Teknik Analiz

### 1. Tablo Mimarisi ve Hücre Birleştirme (`<table>`)

Tablolar, verileri satır (`<tr>`) ve sütun (`<td>`/`<th>`) ızgarasında yapılandırır:

- **Yapısal Bölümleme:**
  - `<thead>`: Sütun başlıklarını (`<th>`) barındıran üst alan.
  - `<tbody>`: Dinamik veri satırlarını (`<tr>` ve `<td>`) taşıyan gövde alanı.
- **Hücre Birleştirme Dinamikleri:**
  - `rowspan="N"`: Bir hücrenin **dikey** olarak altındaki $N-1$ satırı kapsamasını sağlar. Birleştirilen alt satırlarda ilgili sütun hücresi **kesinlikle yazılmaz**, aksi takdirde satır sağa kayarak tabloyu bozar.
  - `colspan="N"`: Bir hücrenin **yatay** olarak yanındaki $N-1$ sütunu birleştirmesini sağlar.
- **Geleneksel vs. Modern Yaklaşım:** Derste denenen `border`, `cellpadding`, `cellspacing`, `align` gibi HTML nitelikleri HTML5 ile birlikte yerini CSS `border-collapse`, `padding` ve `margin: auto` kurallarına bırakmıştır.

```text
┌──────────────┬──────────────┬──────────────┬──────────────┬──────────────┬──────────────┐
│      Ad      │    Soyad     │  Öğrenci No  │   Program    │     Yaş      │  Vize/Final  │
├──────────────┼──────────────┼──────────────┼──────────────┼──────────────┼──────────────┤
│ M. Kemal     │ Yazlık       │ 240307000    │              │ 20           │      90      │
├──────────────┼──────────────┼──────────────┤     YBS      ├──────────────┼──────┬───────┤
│ Samet        │ Acar         │ 240307000    │ (rowspan="3")│ 23           │  80  │  75   │
├──────────────┼──────────────┼──────────────┤              ├──────────────┼──────┼───────┤
│ Emirhan      │ Derebaşı     │ 240307000    │              │ 21           │  90  │  92   │
├──────────────┼──────────────┼──────────────┼──────────────┼──────────────┼──────┼───────┤
│ Berat        │ Koşararslan  │ 240307000    │ Bilgisayar M.│ 22           │  80  │  70   │
└──────────────┴──────────────┴──────────────┴──────────────┴──────────────┴──────┴───────┘
                                                             (colspan="2") ───┘
```

---

### 2. HTML5 Yerel Multimedya Yönetimi (`<video>` & `<audio>`)

Üçüncü parti eklentilere (Flash vb.) ihtiyaç duymadan yerel medya oynatımı sağlanır:

- **Ortak Denetim Nitelikleri:**
  - `controls`: Oynat/duraklat, ses düzeyi ve tam ekran kontrollerini kullanıcıya sunar (zorunludur, aksi halde arayüz çizilmez).
  - `autoplay`: Sayfa yüklendiğinde otomatik başlatır. Modern tarayıcı güvenlik politikaları gereği sesli içeriklerde engellenir; çalışması için `muted` ile birlikte verilmelidir.
  - `loop`: Medya bittiğinde başa dönerek sonsuz döngüde oynatır.
- **Video Özelinde:** `poster` özelliği ile video yüklenmeden veya başlatılmadan önce gösterilecek kapak görseli (`.jpg`/`.png`) tanımlanır.
- **`<source>` Hiyerarşisi:** Tarayıcı uyumluluğu için farklı formatlar (`.mp4`, `.webm`, `.ogg`, `.mp3`) öncelik sırasına göre listelenir.

---

### 3. Form Mimarisi, Doğrulama ve Ağ (Network) Analizi

Formlar, istemciden kullanıcı verisi toplayıp sunucuya ileten temel etkileşim köprüsüdür.

#### A. HTTP İletim Yöntemleri ve DevTools Payload İncelemesi

- **`GET` Metodu:** Verileri URL parametresi (Query String) olarak taşır (`?kullanici_adi=ahmet&yas=20`). Güvensizdir, karakter sınırı vardır; hassas veriler (şifre vb.) için asla kullanılmaz.
- **`POST` Metodu:** Verileri HTTP istek gövdesinde (`Request Body / Payload`) taşır. URL'de veri görünmez, dosya yükleme ve güvenli veri aktarımı için zorunludur.
- **Geliştirici Araçları (`F12 -> Network`):**
  - Form gönderildiğinde oluşturulan HTTP isteğinin `Headers` ve `Payload` sekmeleri incelenir.
  - Gönderilen verilerin anahtar-değer (`name=value`) ikilileri halinde sunucuya `200 OK` veya `302 Found` (yönlendirme) durum kodlarıyla aktarıldığı doğrulanır.

#### B. Kontrol Elemanları ve Nitelik Ayrımı

- **`id` vs. `name`:**
  - `id`: Yalnızca istemci tarafında (CSS, JavaScript ve `<label for="...">` eşleştirmesi) geçerli tekil tanıtıcıdır.
  - `name`: Form sunucuya POST edildiğinde verinin sunucu tarafındaki değişken adıdır (`$_POST['kullanici_adi']`).
- **Veri Doğrulama ve Kısıtlamalar:**
  - `required`: Boş geçilemez alan kontrolü.
  - `type="email"`: Tarayıcı seviyesinde `@` ve alan adı sentaks denetimi.
  - `min` / `max`: Sayısal (`number`) ve tarih (`date`) girişlerinde alt/üst sınır belirleme.
  - `type="color"`: Yerel renk paleti açarak `#RRGGBB` formatında hex değeri üretir.
  - `type="file"`: `accept=".jpg,.pdf"` niteliği ile yüklenecek dosya türünü sınırlandırır.
  - `type="radio"`: Ortak `name` değeri verilerek grubun içinden tek seçim yapılması garanti edilir.

---

### 4. Blok vs. Satır İçi (Inline) Ayrımı ve Semantik Düzen

Tarayıcının etiketleri ekrana render etme biçimi iki ana kategoride gerçekleşir:

| Davranış Türü             | Temsili Etiketler                                                                                                                  | Kutu Modeli ve Genişlik Özelliği                                                                  |
| :------------------------ | :--------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------ |
| **Blok Seviyeli (Block)** | `<div>`, `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`, `<table>`, `<form>`, `<p>`, `<h1>`-`<h6>` | Bulunduğu satırın **%100 genişliğini** kaplar. Kendisinden sonra gelen elemanı alt satıra zorlar. |
| **Satır İçi (Inline)**    | `<span>`, `<a>`, `<b>`, `<strong>`, `<i>`, `<em>`, `<u>`, `<mark>`, `<label>`, `<input>`                                           | Yalnızca **içeriği kadar** yer kaplar. Yan yana dizilmeye devam eder, alt satıra geçmez.          |

#### Semantik HTML5 Ağacı (W3C Standardı)

Arama motorları ve ekran okuyucular için anlamsız `<div>` karmaşası yerine semantik bölümler kullanılır:

- `<header>`: Sayfa üst bilgisi, kurumsal logo, ana karşılama alanı.
- `<nav>`: Birincil navigasyon ve menü bağlantıları.
- `<main>`: Sayfanın özgün, birincil içerik alanı (sayfa başına 1 adet).
- `<section>`: Tematik olarak ayrılmış mantıksal alt bölümler.
- `<article>`: Tek başına bağımsız dağıtılabilir blog yazısı, duyuru veya haber kartı.
- `<aside>`: Kenar çubuğu, yan menüler, banner veya ek bilgi blokları.
- `<footer>`: Telif hakları, iletişim bilgileri ve ikincil bağlantıların yer aldığı alt bilgi.

---

## 📂 Dosya Dizini ve Bağlantılar

|  Tip   | Dosya Adı                                | Odak & Kazanım                                                                                 |
| :----: | :--------------------------------------- | :--------------------------------------------------------------------------------------------- |
| `HTML` | [`01-tables.html`](./01-tables.html)     | `rowspan`, `colspan`, `thead`, `tbody` ile gelişmiş öğrenci not tablosu                        |
| `HTML` | [`02-video.html`](./02-video.html)       | `<video>` denetimleri, `controls`, `poster`, `source` ve tarayıcı uyumluluğu                   |
| `HTML` | [`03-audio.html`](./03-audio.html)       | `<audio>` etiketi, arka plan oynatımı ve ses formatları                                        |
| `HTML` | [`04-forms.html`](./04-forms.html)       | Kapsamlı form denetimleri (`text`, `color`, `date`, `file`, `radio`, `checkbox`)               |
| `HTML` | [`05-seo-tags.html`](./05-seo-tags.html) | Blok/satır içi davranışı ve modern semantik sayfa iskeleti (`header`, `nav`, `main`, `footer`) |

---

<details>
<summary>📌 <strong>Gelecek Hafta Öncesi Notlar (Hafta 07: CSS Giriş)</strong></summary>

- HTML yapısal iskeleti tamamlanmış olup, biçimlendirme ve mizanpaj kuralları için **CSS (Cascading Style Sheets)** modülüne geçilecektir.
- Dahili (`<style>`), satır içi (`style="..."`) ve harici (`.css`) stil ekleme yöntemleri, temel seçiciler (`class`, `id`, element) ve CSS Kutu Modeli (Box Model: margin, border, padding, content) incelenecektir.
</details>
