# 🌐 Hafta 02: HTTP Durum Kodları (HTTP Status Codes)

Bu derste istemci (client) ile sunucu (server) arasındaki haberleşmede dönen HTTP yanıt kodları, mantıksal grupları ve en sık kullanılan kodlar incelendi.

## 📌 Kod Blokları ve Anlamları

* **1xx (Bilgi / Informational):** İstek alındı, süreç devam ediyor.
* **2xx (Başarı / Success):** İstek başarıyla alındı, anlaşıldı ve kabul edildi.
* **3xx (Yönlendirme / Redirection):** İsteğin tamamlanması için ek işlem gerekiyor.
* **4xx (İstemci Hatası / Client Error):** İstekte hata var veya yetkisiz erişim denendi.
* **5xx (Sunucu Hatası / Server Error):** Sunucu geçerli bir isteği yerine getiremedi.

---

## 🚀 En Sık Kullanılan Durum Kodları

| Kod | İsim | Açıklama |
| :---: | :--- | :--- |
| **200** | OK | İstek başarılı oldu ve yanıt gövdesi döndü. |
| **201** | Created | İstek başarılı oldu ve sunucuda yeni bir kaynak oluşturuldu (POST genelde). |
| **204** | No Content | İstek başarılı ancak döndürülecek bir içerik yok. |
| **301** | Moved Permanently | Kaynak kalıcı olarak yeni bir URL'e taşındı (SEO yönlendirmeleri). |
| **302** | Found | Kaynak geçici olarak başka bir URL'e yönlendirildi. |
| **304** | Not Modified | Kaynak değişmedi, tarayıcı önbellekteki (cache) kopyayı kullanabilir. |
| **400** | Bad Request | Sunucu isteği sözdizimi veya parametre hatası nedeniyle anlayamadı. |
| **401** | Unauthorized | Kimlik doğrulaması gerekiyor (Token/Login eksik veya geçersiz). |
| **403** | Forbidden | Kimlik doğrulandı ancak bu kaynağa erişim izni yok. |
| **404** | Not Found | İstenen kaynak veya endpoint sunucuda bulunamadı. |
| **405** | Method Not Allowed | İlgili URL belirtilen HTTP metodunu (GET, POST, PUT vb.) desteklemiyor. |
| **429** | Too Many Requests | Kullanıcı belirli bir süre içinde çok fazla istek gönderdi (Rate limit). |
| **500** | Internal Server Error | Sunucu tarafında beklenmeyen genel bir hata/çökme oluştu. |
| **502** | Bad Gateway | Ağ geçidi veya proxy olarak çalışan sunucu, üst sunucudan geçersiz yanıt aldı. |
| **503** | Service Unavailable | Sunucu aşırı yük altında veya bakımda, geçici olarak hizmet veremiyor. |
| **504** | Gateway Timeout | Ağ geçidi/proxy sunucu, üst sunucudan zamanında yanıt alamadı. |
