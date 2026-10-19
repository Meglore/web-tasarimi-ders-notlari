# Hafta 04: HTML Temelleri, Etiket Mantığı ve Doküman Yapısı

Bu hafta işaretleme dillerinin (XML/HTML) temel çalışma mantığı, tarayıcı geliştirici araçları (DevTools), standart HTML5 iskeleti ve temel içerik etiketleri işlenmiştir.

---

## 📑 Ders Konu Başlıkları

1. **İşaretleme Dilleri ve XML Mantığı:**
   - Etiketlerin (tag) hiyerarşik ve ağaç yapısı.
   - Verilerin karışmaması için blok/paket oluşturma mantığı (`<OgrenciDetay>`).
2. **HTML Sayfa İskeleti ve Tarayıcı Yorumlaması:**
   - `<!DOCTYPE html>`, `<html>`, `<head>`, `<body>` bölümleri.
   - Karakter kodlaması (`UTF-8`) ve viewport tanımları.
   - Düz metin dosyasının `.html` uzantısına çevrilerek çalıştırılması.
3. **Tarayıcı Geliştirici Araçları (DevTools - F12):**
   - **Elements:** DOM ağacı ve etiketlerin kapladığı alanlar (genişlik/yükseklik).
   - **Console:** JavaScript ve referans hataları, satır numarası takibi.
   - **Sources:** Yüklenen HTML, harici CSS ve JS dosyaları.
   - **Network:** HTTP istek/yanıt döngüsü (`GET`, `POST`), durum kodları (`200 OK`, `302 Moved`, `401 Unauthorized`, `403 Forbidden`).
4. **Metin ve Tipografi Etiketleri:**
   - Başlık hiyerarşisi (`<h1>` - `<h6>`), satırı blok olarak kaplama davranışı.
   - Paragraf (`<p>`), tekil satır atlama (`<br />`).
   - Biçimlendirme: `<b>` vs `<strong>`, `<i>` vs `<em>`, `<u>`, `<mark>`.
5. **Köprüler ve Dizin Yönetimi:**
   - `<a>` etiketi, `href` ve `target` (`_blank`, `_self`) nitelikleri.
   - Bağıl yollar (Relative Paths): Aynı dizin, alt klasöre iniş (`klasor/dosya.html`), üst klasöre çıkış (`../dosya.html`).
6. **Medya ve Listeler:**
   - Görsel yerleşimi (`<img>`), `src`, `alt`, `width`, `height`.
   - Sırasız liste (`<ul>`), sıralı liste (`<ol>`) ve liste elemanları (`<li>`).

---

## 📂 Dosya Dizini ve Bağlantılar

| Dosya                                                          | Açıklama                                                                 |
| :------------------------------------------------------------- | :----------------------------------------------------------------------- |
| [`01-xml-yapisi.xml`](./01-xml-yapisi.xml)                     | XML veri formatı, etiket eşleme ve veri paketleme örneği.                |
| [`02-temel-iskelet.html`](./02-temel-iskelet.html)             | Standart HTML5 sayfa yapısı ve meta ayarları.                            |
| [`03-metin-bicimlendirme.html`](./03-metin-bicimlendirme.html) | Başlıklar, paragraflar ve metin vurgulama etiketleri.                    |
| [`04-baglantilar.html`](./04-baglantilar.html)                 | İç/dış bağlantılar, sekme yönetimi ve klasör hiyerarşisi.                |
| [`05-gorseller.html`](./05-gorseller.html)                     | Resim ekleme, boyutlandırma ve alt etiketinin SEO/erişilebilirlik önemi. |
| [`06-listeler.html`](./06-listeler.html)                       | Sıralı/sırasız listeler ve web menü altyapısı.                           |
| [`sayfalar/alt-sayfa.html`](./sayfalar/alt-sayfa.html)         | Üst dizine çıkış (`../`) test sayfası.                                   |
