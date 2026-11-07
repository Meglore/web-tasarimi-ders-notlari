<div align="center">
  <p><strong>Hazırlayan: Mustafa Kemal Yazlık</strong></p>
  <h1>🌐 Hafta 06</h1>
  <h3>Tablolar · Multimedya · Form Mimarisi · Semantik HTML5</h3>
  <p>
    <img src="https://img.shields.io/badge/HTML5-Advanced-E34F26?style=flat-square&amp;logo=html5&amp;logoColor=white" alt="HTML5" />
    <img src="https://img.shields.io/badge/HTTP-GET_%26_POST-2563EB?style=flat-square" alt="HTTP GET ve POST" />
    <img src="https://img.shields.io/badge/Standart-Semantik_HTML5-059669?style=flat-square" alt="Semantik HTML5" />
  </p>
  <p><strong>HTML5 bileşenlerini yalnızca kullanmayı değil, doğru yapılandırmayı ve tarayıcı üzerinden incelemeyi öğrenin.</strong></p>
</div>

---

## 📖 Genel Bakış

Bu haftada; **HTML tabloları**, **yerel ses/video oynatımı**, **formların HTTP ile veri göndermesi** ve **semantik sayfa yapısı** ele alınmıştır. Konular uygulama dosyalarıyla desteklenmiş, özellikle `rowspan` / `colspan` kullanımı ve DevTools üzerinden form verisi incelemesi üzerinde durulmuştur.

> [!NOTE]
> **HTML yapıyı, CSS görünümü yönetir.** Renk, boşluk, hizalama ve kenarlık gibi sunum kararları CSS ile verilmelidir. Doğru HTML etiketleri ise anlamlı belge yapısı, erişilebilirlik ve SEO açısından önem taşır.

### 🧭 İçindekiler

| Bölüm                                                        | Bu bölümde neler var?                                 |
| ------------------------------------------------------------ | ----------------------------------------------------- |
| [01 · Tablo mimarisi](#01--tablo-mimarisi)                   | `table`, `thead`, `tbody`, `rowspan`, `colspan`       |
| [02 · HTML5 multimedya](#02--html5-multimedya)               | `video`, `audio`, `source`, `poster`                  |
| [03 · Form ve HTTP](#03--form-mimarisi-ve-http-analizi)      | `GET`, `POST`, `name`, `id`, form doğrulama, DevTools |
| [04 · Semantik HTML5](#04--blok-satır-içi-ve-semantik-html5) | Blok/satır içi davranışı, semantik etiketler          |
| [📁 Uygulama dosyaları](#-uygulama-dosyaları)                | Beş örnek HTML dosyasına hızlı erişim                 |

---

## 01 · Tablo Mimarisi

HTML tabloları, **satır** ve **sütun** ilişkisi bulunan verileri göstermek için kullanılır. Sayfa yerleşimi oluşturmak için tablo kullanmak yerine CSS tercih edilir.

| Etiket / nitelik | Görevi                                                                                             |
| ---------------- | -------------------------------------------------------------------------------------------------- |
| `<table>`        | Tabloyu tanımlar.                                                                                  |
| `<thead>`        | Başlık satırlarını gruplar.                                                                        |
| `<tbody>`        | Veri satırlarını gruplar.                                                                          |
| `<tr>`           | Yeni bir satır oluşturur.                                                                          |
| `<th>`           | Başlık hücresi oluşturur.                                                                          |
| `<td>`           | Veri hücresi oluşturur.                                                                            |
| `rowspan="N"`    | Hücreyi **dikey** olarak toplam `N` satıra yayar; mevcut satırın altındaki `N-1` satırı da kapsar. |
| `colspan="N"`    | Hücreyi **yatay** olarak toplam `N` sütuna yayar; yanındaki `N-1` sütunu kapsar.                   |

### 👀 Birleştirilmiş hücre örneği

Özgün örnekteki **Ad, Soyad, Öğrenci No, Program, Yaş, Vize ve Final** alanlarının tamamı korunmuştur. **YBS** hücresi `rowspan="3"` ile üç öğrencinin program alanını birleştirir. **Vize** ve **Final** ayrı sütunlardır; ilk öğrencinin tek **90** notu, `colspan="2"` sayesinde iki not sütununun **ortasında** görünür. Final için ayrıca tire konulmaz.

<table>
  <thead>
    <tr>
      <th scope="col">Ad</th>
      <th scope="col">Soyad</th>
      <th scope="col">Öğrenci No</th>
      <th scope="col">Program</th>
      <th scope="col">Yaş</th>
      <th scope="col">Vize</th>
      <th scope="col">Final</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Mustafa Kemal</td>
      <td>Yazlık</td>
      <td>240307059</td>
      <td rowspan="3" align="center">YBS</td>
      <td>20</td>
      <td colspan="2" align="center">90</td>
    </tr>
    <tr>
      <td>Samet</td>
      <td>Acar</td>
      <td>240307013</td>
      <td>21</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <td>Emirhan</td>
      <td>Derebaşı</td>
      <td>240307015</td>
      <td>21</td>
      <td>90</td>
      <td>92</td>
    </tr>
    <tr>
      <td>Berat</td>
      <td>Koşararslan</td>
      <td>240307024</td>
      <td>Bilgisayar M.</td>
      <td>22</td>
      <td>80</td>
      <td>70</td>
    </tr>
  </tbody>
</table>

> [!IMPORTANT]
> `rowspan="3"` kullandığınızda, sonraki iki satıra **Program sütunu için yeniden `<td>` yazmayın**. Birleşik hücre bu satırları zaten kaplar; ekstra hücre, tablonun hizasını bozar.

<details>
<summary><strong>⌨️ Tablonun birebir HTML kodunu göster</strong></summary>

```html
<table>
  <thead>
    <tr>
      <th scope="col">Ad</th>
      <th scope="col">Soyad</th>
      <th scope="col">Öğrenci No</th>
      <th scope="col">Program</th>
      <th scope="col">Yaş</th>
      <th scope="col">Vize</th>
      <th scope="col">Final</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Mustafa Kemal</td>
      <td>Yazlık</td>
      <td>240307059</td>
      <td rowspan="3" align="center">YBS</td>
      <td>20</td>
      <td colspan="2" align="center">90</td>
    </tr>
    <tr>
      <td>Samet</td>
      <td>Acar</td>
      <td>240307013</td>
      <td>21</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <td>Emirhan</td>
      <td>Derebaşı</td>
      <td>240307015</td>
      <td>21</td>
      <td>90</td>
      <td>92</td>
    </tr>
    <tr>
      <td>Berat</td>
      <td>Koşararslan</td>
      <td>240307024</td>
      <td>Bilgisayar M.</td>
      <td>22</td>
      <td>80</td>
      <td>70</td>
    </tr>
  </tbody>
</table>
```

</details>

**Modern yaklaşım:** Eski `border`, `cellpadding`, `cellspacing` ve `align` gibi sunum amaçlı HTML nitelikleri yerine CSS'te `border`, `border-collapse`, `padding` ve gerektiğinde `margin: auto` kullanılır.

**İlgili uygulama:** [`01-tables.html`](./01-tables.html)

---

## 02 · HTML5 Multimedya

HTML5 ile Flash gibi üçüncü taraf eklentilere ihtiyaç duymadan video (`<video>`) ve ses (`<audio>`) oynatılabilir. Video için `.mp4` / `.webm`, ses için `.mp3` / `.ogg` gibi alternatif kaynaklar tanımlanabilir.

| Nitelik / etiket | Ne yapar?                                                                                                             |
| ---------------- | --------------------------------------------------------------------------------------------------------------------- |
| `controls`       | Oynatma ve ses gibi yerel arayüz kontrollerini gösterir. Kullanılması önerilir; zorunlu değildir.                     |
| `autoplay`       | Otomatik oynatmayı talep eder. Tarayıcı politikaları nedeniyle engellenebilir.                                        |
| `muted`          | Sesi kapatır; `autoplay` ile birlikte kullanılması otomatik oynatma olasılığını artırır.                              |
| `loop`           | Medyayı bittiğinde tekrar oynatır.                                                                                    |
| `poster`         | Videonun başlamasından önce gösterilecek `.jpg` veya `.png` gibi kapak görselini belirtir; `<video>` için geçerlidir. |
| `<source>`       | Tarayıcı uyumluluğu için alternatif medya dosyalarını ve türlerini **öncelik sırasıyla** tanımlar.                    |

<details>
<summary><strong>🎬 Video ve ses örneklerini göster</strong></summary>

**Video**

```html
<video controls poster="kapak.jpg" width="640">
  <source src="video.webm" type="video/webm" />
  <source src="video.mp4" type="video/mp4" />
  Tarayıcınız video oynatmayı desteklemiyor.
</video>
```

**Ses**

```html
<audio controls>
  <source src="ses.ogg" type="audio/ogg" />
  <source src="ses.mp3" type="audio/mpeg" />
  Tarayıcınız ses oynatmayı desteklemiyor.
</audio>
```

Tarayıcı, desteklediği ilk uygun kaynağı kullanır. Uyumluluk; dosya uzantısının yanında **kullanılan codec'e** de bağlıdır. `controls` belirtilmezse standart oynatma kontrolleri görünmeyebilir. Özellikle **sesli otomatik oynatma** genellikle engellenir; `muted` bu kısıtın aşılmasına yardımcı olabilir ancak kesin garanti değildir.

</details>

**İlgili uygulamalar:** [`02-video.html`](./02-video.html) · [`03-audio.html`](./03-audio.html)

---

## 03 · Form Mimarisi ve HTTP Analizi

Formlar, kullanıcı girdilerini toplar ve bu verilerin bir sunucuya gönderilmesini sağlar. Formun davranışı `action`, `method` ve kontrol elemanlarının `name` nitelikleriyle şekillenir.

### A · GET ve POST karşılaştırması

| Özellik                     | `GET`                                                      | `POST`                                             |
| --------------------------- | ---------------------------------------------------------- | -------------------------------------------------- |
| Veri nerede taşınır?        | URL sorgu parametrelerinde (`?kullanici_adi=ahmet&yas=20`) | HTTP istek gövdesinde (`request body`)             |
| URL'de görünür mü?          | Evet                                                       | Normalde hayır                                     |
| Tipik kullanım              | Arama ve filtreleme gibi veri okuma işlemleri              | Kayıt, form gönderimi ve veri değiştirme işlemleri |
| Hassas bilgi için uygun mu? | Hayır; URL'ler geçmişe ve kayıtlara girebilir              | Yalnızca **HTTPS** ve uygun sunucu güvenliğiyle    |

> [!WARNING]
> **POST tek başına güvenlik sağlamaz.** Verilerin ağ üzerinde korunması için HTTPS gerekir. Dosya yükleme yapılan klasik HTML formlarında genellikle `method="post"` ve `enctype="multipart/form-data"` birlikte kullanılır. GET için evrensel, sabit bir URL karakter sınırı yoktur; tarayıcı ve sunucu sınırları değişebilir.

### B · `id` ve `name` farkı

| Nitelik | Kullanım                                                                                        |
| ------- | ----------------------------------------------------------------------------------------------- |
| `id`    | Bir öğeyi sayfada tanımlamak; CSS, JavaScript ve `<label for="...">` ilişkisi kurmak.           |
| `name`  | Form gönderiminde alanın anahtarını belirtmek; örneğin PHP tarafında `$_POST['kullanici_adi']`. |

```html
<form action="/kayit" method="post">
  <label for="kullanici_adi">Kullanıcı adı</label>
  <input type="text" id="kullanici_adi" name="kullanici_adi" required />
  <button type="submit">Gönder</button>
</form>
```

Bu örnekte `id`, etiketi giriş alanına bağlar; `name` ise gönderilen verinin anahtarı olur. `$_POST` örneği, isteğin PHP tarafından işlenmesi durumunda geçerlidir.

### C · Yerleşik form doğrulama

| Özellik                  | Açıklama                                                                                             |
| ------------------------ | ---------------------------------------------------------------------------------------------------- |
| `required`               | Alanın boş bırakılmasını engeller.                                                                   |
| `type="email"`           | Temel e-posta biçimini tarayıcıda denetler.                                                          |
| `min` / `max`            | Sayısal ve tarih alanlarına alt/üst sınır koyar.                                                     |
| `type="color"`           | Renk seçici gösterir; tipik olarak `#RRGGBB` değeri üretir.                                          |
| `type="file"` + `accept` | Örneğin `accept=".jpg,.pdf"` ile seçilebilen türleri filtreler; sunucu doğrulamasının yerine geçmez. |
| `type="radio"`           | Aynı `name` ile gruplanan seçeneklerden tek seçim sağlar.                                            |
| `type="checkbox"`        | Bağımsız veya çoklu seçimler sağlar.                                                                 |

### D · DevTools ile gönderilen veriyi inceleme

1. Sayfayı açın ve **F12 → Network (Ağ)** sekmesine geçin.
2. Formu doldurun ve **Gönder** düğmesine basın.
3. Oluşan isteği seçerek **Headers (Üst Bilgiler)** bölümünde istek yöntemi ve adresi kontrol edin.
4. **Payload** bölümünde gönderilen alanları inceleyin. `application/x-www-form-urlencoded` biçiminde alanlar `name=value` çiftleri olarak kodlanır.
5. **Response** ve **Status** bilgilerini kontrol edin. Örneğin `200 OK` başarılı bir yanıtı, `302 Found` ise yönlendirmeyi ifade edebilir; gerçek sonuç sunucunun uygulama mantığına bağlıdır.

**İlgili uygulama:** [`04-forms.html`](./04-forms.html)

---

## 04 · Blok, Satır İçi ve Semantik HTML5

### A · Blok ve satır içi davranış

| Davranış               | Tipik örnekler                                                                                                          | Varsayılan görünüm                                                                    |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| **Blok (block)**       | `<div>`, `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`, `<form>`, `<p>`, `<h1>`–`<h6>` | Genellikle yeni satırdan başlar ve normal akışta kullanılabilir yatay alanı doldurur. |
| **Satır içi (inline)** | `<span>`, `<a>`, `<b>`, `<strong>`, `<i>`, `<em>`, `<u>`, `<mark>`, `<label>`                                           | Metin akışı içinde yer alır; gerektiğinde satır sonunda bölünebilir.                  |

> [!TIP]
> Bunlar **varsayılan CSS görüntüleme davranışlarıdır**; tüm HTML elemanlarını eksiksiz olarak iki sınıfa ayıran bir kural değildir. Örneğin `<input>` genellikle `inline-block`, `<table>` ise `table` görüntüleme davranışına sahiptir. `display` özelliğiyle görünüm değiştirilebilir. Bloklar otomatik olarak her koşulda “%100 genişlikte” olmak zorunda değildir.

### B · Semantik sayfa yapısı

Semantik etiketler içerik bölümlerinin **ne anlama geldiğini** belirtir. Böylece sayfa yapısı geliştirici, arama motoru ve yardımcı teknolojiler için daha anlaşılır olur.

```text
<body>
├── <header>       Üst bilgi
│   └── <nav>      Gezinme bağlantıları
├── <main>         Sayfanın birincil içeriği
│   ├── <section>  Konu odaklı bölüm
│   └── <article>  Bağımsız içerik
├── <aside>        Tamamlayıcı / yan içerik
└── <footer>       Alt bilgi
</body>
```

| Etiket      | Kullanım amacı                                                                   |
| ----------- | -------------------------------------------------------------------------------- |
| `<header>`  | Sayfa veya bölümün giriş ve üst bilgi alanı.                                     |
| `<nav>`     | Gezinme bağlantılarının bulunduğu alan.                                          |
| `<main>`    | Belgenin birincil, özgün içeriği. Sayfada genellikle tek görünür `main` bulunur. |
| `<section>` | Genellikle başlığı olan, tematik içerik bölümü.                                  |
| `<article>` | Tek başına anlam taşıyan yazı, duyuru veya içerik kartı.                         |
| `<aside>`   | Ana içerikle dolaylı ilişkili ek bilgiler.                                       |
| `<footer>`  | Sayfa veya bölümün alt bilgisi.                                                  |

**İlgili uygulama:** [`05-seo-tags.html`](./05-seo-tags.html)

---

## 📁 Uygulama Dosyaları

| Dosya                                    | İçerik                                                   |
| ---------------------------------------- | -------------------------------------------------------- |
| [`01-tables.html`](./01-tables.html)     | Tablolar, başlık/gövde grupları ve hücre birleştirme     |
| [`02-video.html`](./02-video.html)       | Video denetimleri, kapak görseli ve alternatif kaynaklar |
| [`03-audio.html`](./03-audio.html)       | Ses oynatıcı ve ses dosyası formatları                   |
| [`04-forms.html`](./04-forms.html)       | Form kontrolleri, doğrulama ve gönderim                  |
| [`05-seo-tags.html`](./05-seo-tags.html) | Blok/satır içi davranış ve semantik sayfa iskeleti       |

<details>
<summary><strong>📌 Gelecek hafta: Hafta 07 · CSS'e Giriş</strong></summary>

Bir sonraki modülde HTML'in yapısal iskeleti, **CSS (Cascading Style Sheets)** ile biçimlendirilecek.

- **CSS ekleme yöntemleri:** Dahili (`<style>`), satır içi (`style="..."`) ve harici (`.css`).
- **Temel seçiciler:** Etiket, `.class` ve `#id`.
- **Kutu modeli (Box Model):** `content`, `padding`, `border`, `margin`.

</details>

---

<div align="center">
  <p><strong>Hafta 06 · HTML5 Uygulamaları</strong></p>
  <sub>Hazırlayan: Mustafa Kemal Yazlık</sub>
</div>
