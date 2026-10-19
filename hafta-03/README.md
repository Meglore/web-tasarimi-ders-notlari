🌐 Hafta 03: Web Çalışma Mimarisi & HTTP Durum Kodları

!Modül !Konu !Odak

Bu oturumda, modern web uygulamalarının temel çalışma mimarisi ele alınmıştır. Tarayıcı ile sunucu arasındaki iletişim süreci, bir web sayfasına erişim sırasında gerçekleşen ağ adımları ve HTTP protokolünün yanıt mekanizması incelenmiştir.

Ders kapsamında ayrıca HTTP durum kodlarının sınıflandırılması, istemci ve sunucu kaynaklı hataların ayırt edilmesi ve bu kodların gerçek dünya web uygulamalarındaki kullanım senaryoları değerlendirilmiştir.

📌 Oturum Özeti

Web uygulamalarının yalnızca kullanıcı arayüzünden ibaret olmadığı; DNS, ağ bağlantıları, HTTP istekleri, sunucu taraflı işlemler ve tarayıcıda görüntüleme gibi birbirine bağlı bileşenlerden oluştuğu açıklanmıştır.

Oturumun temel kazanımları:

İstemci (Client) ve sunucu (Server) mimarisini kavramak.
Bir URL üzerinden web kaynağına erişim sürecini açıklamak.
HTTP Request ve Response kavramlarını ayırt etmek.
HTTP durum kodlarını kategorilerine göre sınıflandırmak.
Yaygın HTTP hata kodlarını analiz ederek olası sorunları yorumlamak.
🔍 1. Web İstek Yaşam Döngüsü (Request Lifecycle)

Tarayıcı adres çubuğuna bir URL yazılıp Enter tuşuna basıldığında, web sayfasının görüntülenmesine kadar birden fazla işlem gerçekleşir.

┌──────────────────────────┐
│ 1. URL ve DNS Çözümleme │
│ Domain → IP Adresi │
└────────────┬─────────────┘
▼
┌──────────────────────────┐
│ 2. Bağlantı Kurulması │
│ TCP + TLS (HTTPS) │
└────────────┬─────────────┘
▼
┌──────────────────────────┐
│ 3. HTTP Request │
│ GET / POST / Diğerleri │
└────────────┬─────────────┘
▼
┌──────────────────────────┐
│ 4. Sunucu İşlemleri │
│ Uygulama / Veri / Mantık │
└────────────┬─────────────┘
▼
┌──────────────────────────┐
│ 5. HTTP Response │
│ Status + Headers + Body │
└────────────┬─────────────┘
▼
┌──────────────────────────┐
│ 6. Tarayıcıda Görüntüleme│
│ HTML / CSS / JavaScript │
└──────────────────────────┘

Sürecin Temel Bileşenleri
DNS Lookup: Alan adı, ilgili IP adresine çözümlenir.
Connection Establishment: İstemci ile sunucu arasında bağlantı kurulur. HTTPS bağlantılarında TLS ile güvenli iletişim sağlanır.
HTTP Request: Tarayıcı, sunucuya bir kaynak veya işlem için istek gönderir.
Server Processing: Sunucu isteği değerlendirir; gerekli uygulama kodlarını çalıştırabilir ve veri tabanı işlemleri gerçekleştirebilir.
HTTP Response: Sunucu, durum kodu ve yanıt başlıklarıyla birlikte uygun yanıtı döndürür.
Rendering: Tarayıcı, gelen kaynakları işleyerek kullanıcı arayüzünü oluşturur.
[!NOTE]
Bu akış kavramsal bir modeldir. Önbellek kullanımı, mevcut bağlantıların yeniden kullanılması, HTTP/3 ve tarayıcının kaynak yükleme stratejileri gibi etkenler gerçek iletişim sırasını değiştirebilir.
📡 2. HTTP Request & Response Mimarisi

HTTP, istemci ile sunucu arasında kaynakların alınması ve işlemlerin gerçekleştirilmesi için kullanılan bir uygulama katmanı protokolüdür.

Request — İstek

İstemcinin sunucuya ilettiği mesajdır.

GET /products HTTP/1.1
Host: example.com
Accept: application/json

Method: Yapılacak işlemin türünü belirtir.
Path: Erişilmek istenen kaynak yolunu belirtir.
Headers: İstek hakkında ek bilgiler taşır.
Body: Gerektiğinde gönderilen verileri içerir.
Response — Yanıt

Sunucunun istemciye döndürdüğü mesajdır.

HTTP/1.1 200 OK
Content-Type: application/json

{"message": "Request successful"}

Status Code: İsteğin sonucunu sınıflandırır.
Headers: İçerik türü, önbellekleme ve diğer yanıt bilgilerini taşır.
Body: Varsa HTML, JSON, dosya veya başka bir içerik barındırır.
🚦 3. HTTP Durum Kodu Sınıfları

HTTP durum kodları, sunucunun isteğe nasıl karşılık verdiğini üç basamaklı sayılarla ifade eder.

Kod Aralığı Sınıf Anlamı
1xx Informational İstek alındı; iletişim süreci devam ediyor.
2xx Success İstek başarıyla işlendi.
3xx Redirection İstek için yönlendirme veya ek işlem gerekiyor.
4xx Client Error İstek veya istemcinin erişim koşullarıyla ilgili bir sorun var.
5xx Server Error Sunucu, isteği yerine getirirken bir hatayla karşılaştı.
🧭 4. Sık Kullanılan HTTP Durum Kodları
✅ Başarılı Yanıtlar — 2xx
Kod Durum Açıklama
200 OK İstek başarıyla işlendi.
201 Created İstek sonucunda yeni bir kaynak oluşturuldu.
204 No Content İstek başarılıdır; yanıt gövdesi içermez.
🔀 Yönlendirme ve Önbellek — 3xx
Kod Durum Açıklama
301 Moved Permanently Kaynağın kalıcı olarak başka bir URL'e taşındığını belirtir.
302 Found Kaynağın geçici olarak başka bir URL üzerinden erişilebilir olduğunu belirtir.
304 Not Modified İstemcinin önbelleğindeki kaynağı yeniden kullanabileceğini belirtir.
⚠️ İstemci Hataları — 4xx
Kod Durum Açıklama
400 Bad Request İstek, geçersiz sözdizimi veya hatalı veriler içeriyor.
401 Unauthorized Kaynağa erişmek için geçerli kimlik doğrulaması gerekiyor.
403 Forbidden Sunucu isteği anladı ancak erişime izin vermiyor.
404 Not Found İstenen kaynak bulunamadı.
405 Method Not Allowed Kullanılan HTTP metodu bu kaynak için desteklenmiyor.
429 Too Many Requests İstek sınırı aşıldı; hız sınırlaması uygulanıyor.
🔥 Sunucu Hataları — 5xx
Kod Durum Açıklama
500 Internal Server Error Sunucuda beklenmeyen bir hata oluştu.
502 Bad Gateway Ağ geçidi veya proxy, üst sunucudan geçerli bir yanıt alamadı.
503 Service Unavailable Sunucu geçici olarak hizmet veremiyor.
504 Gateway Timeout Ağ geçidi veya proxy, üst sunucudan zamanında yanıt alamadı.
🧪 5. Gerçek Dünya Senaryoları

HTTP durum kodları, web uygulamalarında hata ayıklama ve sistem davranışını yorumlama açısından önemli bir araçtır.

Senaryo Olası Kod Teknik Yorum
Ürün listesi başarıyla yüklendi. 200 İstek başarılı sonuçlandı.
Yeni kullanıcı kaydı oluşturuldu. 201 Yeni kaynak oluşturuldu.
Kullanıcı oturum açmadan korumalı bir kaynağa erişti. 401 Kimlik doğrulaması gerekiyor.
Kullanıcının erişim izni olmayan bir sayfa açıldı. 403 Erişim reddedildi.
Geçersiz bir API adresine istek gönderildi. 404 Kaynak bulunamadı.
API'ye çok kısa sürede fazla istek gönderildi. 429 Hız sınırlaması devreye girdi.
Sunucu tarafında beklenmeyen bir istisna oluştu. 500 Sunucu hatası meydana geldi.
Bağımlı bir servis zamanında yanıt vermedi. 504 Ağ geçidi zaman aşımına uğradı.
[!IMPORTANT]
HTTP durum kodları tek başına sorunun kesin nedenini her zaman göstermez. Özellikle 401, 403, 500 ve 503 gibi kodların doğru yorumlanması için uygulama günlükleri, sunucu yapılandırması ve ilgili servislerin durumu birlikte incelenmelidir.
🛠️ 6. Teknik Değerlendirme ve Hata Ayıklama

Bir web uygulamasında hata oluştuğunda geliştirici, sorunu sistematik olarak incelemelidir.

Browser DevTools → Network: İstek URL'ini, HTTP metodunu, durum kodunu, başlıkları ve yanıt gövdesini kontrol et.
Request Validation: Gönderilen parametrelerin, içerik türünün ve veri formatının doğruluğunu incele.
Authentication & Authorization: Kimlik doğrulama ile erişim izinlerini birbirinden ayır.
Server Logs: Sunucu tarafındaki hata kayıtlarını ve istisnaları analiz et.
API Testing: Gerekli durumlarda isteği bir API test aracıyla yeniden oluştur.

Bu yaklaşım, yalnızca hatanın görünen sonucunu değil, hataya neden olan katmanı da belirlemeye yardımcı olur.

🎯 Oturum Sonuçları

Bu hafta sonunda öğrencilerin:

Web uygulamalarındaki istemci-sunucu iletişim modelini açıklayabilmesi,
DNS, bağlantı kurulumu, HTTP isteği, yanıt ve tarayıcıda görüntüleme aşamalarını tanımlayabilmesi,
HTTP durum kodlarını 1xx–5xx sınıflarına ayırabilmesi,
Yaygın başarı, yönlendirme ve hata kodlarını gerçek senaryolarla ilişkilendirebilmesi,
Tarayıcı geliştirici araçlarını kullanarak temel HTTP sorunlarını inceleyebilmesi

hedeflenmiştir.

➡️ Sonraki Oturuma Hazırlık

Bir sonraki hafta, web uygulamalarının istemci tarafındaki temel yapı taşlarına geçilerek HTML doküman yapısı, temel etiketler ve semantik işaretleme kavramları ele alınabilir.
