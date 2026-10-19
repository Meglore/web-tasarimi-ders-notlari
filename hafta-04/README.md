# 📦 Hafta 04: HTML Temelleri, Etiket Mantığı ve Doküman Yapısı

![Modül](https://img.shields.io/badge/Modül-Web_Biçimlendirme-E34F26?style=flat-square&logo=html5&logoColor=white)
![Protokol](https://img.shields.io/badge/İnceleme-DevTools_Network-232F3E?style=flat-square)
![Standart](https://img.shields.io/badge/Standart-HTML5_Semantic-blue?style=flat-square)

Bu modülde işaretleme dillerinin (XML/HTML) temel çalışma prensibi, tarayıcı geliştirici araçları üzerinden istemci-sunucu trafiğinin izlenmesi, standart HTML5 iskeleti ve temel sayfa içi içerik etiketleri ele alınmıştır.

> [!NOTE]
> Web sayfaları tarayıcı tarafından doğrudan derlenmez; DOM (Document Object Model) ağacına göre yukarıdan aşağıya doğru parse edilir. Etiketlerin doğru kapatılması ve hiyerarşik paketleme, arayüzün kararlı render edilmesi için kritiktir.

---

## 📑 Ders Konu Başlıkları

### 1. İşaretleme Dilleri ve XML Mantığı

- **Hiyerarşik Ağaç Yapısı:** Verilerin alt etiketler (`tag`) aracılığıyla anlamlandırılması.
- **Veri Paketleme:** Çoklu veri modellerinde (Örn: Öğrenci tablosu) alanların birbirine karışmaması için kapsayıcı (`<OgrenciDetay>`) etiket kullanımı.

---

### 2. HTML Sayfa İskeleti ve Yorumlama

- **Doküman Tanımı:** `<!DOCTYPE html>` ile HTML5 standartlarına geçiş.
- **Bölümleme Mantığı:**
  - `<head>`: Sayfa başlığı (`<title>`), mobil uyumluluk (`viewport`) ve karakter seti (`UTF-8`).
  - `<body>`: Kullanıcıya yansıtılan tüm görsel ve metinsel arayüz bileşenleri.
- **Dosya Dönüşümü:** Düz metin (`.txt`) uzantısının `.html` yapılarak tarayıcı motoruna yorumlatılması.

---

### 3. Tarayıcı Geliştirici Araçları (DevTools — `F12`)

| Sekme        | İnceleme Alanı & Odak                                                                               |
| :----------- | :-------------------------------------------------------------------------------------------------- |
| **Elements** | Canlı DOM ağacı, etiket kutu modeli (genişlik/yükseklik piksel tahsisleri).                         |
| **Console**  | JavaScript çalışma zamanı hataları, referans uyarıları ve satır takibi.                             |
| **Sources**  | Sunucudan indirilen kaynak dosyaların (HTML, harici CSS/JS) ham hali.                               |
| **Network**  | `GET`/`POST` istekleri, kaynak yükleme süreleri ve HTTP durum kodları (`200`, `302`, `401`, `403`). |

---

### 4. Metin ve Tipografi Mimarisi

- **Başlıklar (`<h1>` – `<h6>`):** Sayfa hiyerarşisini belirler, varsayılan olarak satırı blok kaplar.
- **Paragraflar & Satır Atlama:** Metin blokları için `<p>`, satır içi atlama için tekil `<br />` etiketi.
- **Görsel vs Semantik Vurgulama:**
  - `<b>` _(yalnızca kalın)_ ⟷ `<strong>` _(anlamsal önem ve vurgu)_
  - `<i>` _(yalnızca italik)_ ⟷ `<em>` _(vurgulanmış eğik ifade)_
  - `<u>` _(altı çizili)_ ve `<mark>` _(fosforlu arkaplan vurgusu)_

---

### 5. Köprüler (Links) ve Bağıl Yol Yönetimi

- **Hedef Yönetimi (`target`):**
  - `_self`: Mevcut sekmede gezinme (varsayılan).
  - `_blank`: Dış bağlantıları izole yeni sekmede açma.
- **Dizin Hiyerarşisi (Relative Paths):**
  - Aynı dizin: `dosya.html`
  - Alt klasöre iniş: `klasor/dosya.html`
  - Üst klasöre çıkış: `../dosya.html`

---

### 6. Medya ve Listeleme Yapıları

- **Görseller (`<img>`):** `src`, boyut sınırlamaları (`width`/`height`) ve SEO/erişilebilirlik için zorunlu `alt` alternatifi.
- **Sırasız Listeler (`<ul>`):** Madde imli listeler (Modern navigasyon barlarının temeli).
- **Sıralı Listeler (`<ol>`):** Sayısal/alfabetik aşamalı adımlar.
- **Liste Elemanı (`<li>`):** Tüm liste türlerinin ortak satır taşıyıcısı.

---

## 📂 Dosya Dizini ve Uygulamalar

Aşağıdaki tabloda bu hafta yazılan ve birbiriyle bağıl yollarla (`relative path`) ilişkili olan çalışma dosyaları yer almaktadır:

|  Tip   | Dosya Adı                                                      | Açıklama                                                      |
| :----: | :------------------------------------------------------------- | :------------------------------------------------------------ |
| `XML`  | [`01-xml-yapisi.xml`](./01-xml-yapisi.xml)                     | Hiyerarşik veri etiketleme ve paket blok örneği               |
| `HTML` | [`02-temel-iskelet.html`](./02-temel-iskelet.html)             | Standart HTML5 iskeleti, meta veriler ve sekme başlığı        |
| `HTML` | [`03-metin-bicimlendirme.html`](./03-metin-bicimlendirme.html) | Başlık blokları, paragraf yapısı ve metin vurguları           |
| `HTML` | [`04-baglantilar.html`](./04-baglantilar.html)                 | Dahili/harici linkler, sekme hedefleri ve yol testleri        |
| `HTML` | [`05-gorseller.html`](./05-gorseller.html)                     | Görsel çağırma, boyutlandırma ve fallback (`alt`) mekanizması |
| `HTML` | [`06-listeler.html`](./06-listeler.html)                       | `<ul>` ve `<ol>` listeleri, `<li>` veri gruplama              |
| `TEST` | [`sayfalar/alt-sayfa.html`](./sayfalar/alt-sayfa.html)         | Üst klasöre geri çıkış (`../`) bağıl yol denemesi             |

---

<details>
<summary>📌 <strong>Gelecek Hafta Öncesi Notlar (Hafta 05)</strong></summary>

- `<center>` ve benzeri eski HTML hizalama etiketleri kullanılmayacaktır; mizanpaj çözümleri **CSS** modülünde ele alınacaktır.
- Bir sonraki derste `<table>` veri tabloları, `<video>` multimedya etiketleri ve temel CSS seçicilerine giriş yapılacaktır.
</details>
