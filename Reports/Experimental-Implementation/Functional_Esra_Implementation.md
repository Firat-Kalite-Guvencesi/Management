# Deneysel Uygulama Günlüğü

**Araştırmacı:** Esra Nur Gümüş  
**Tarih:** 27 Kasım 2025  
**Görev:** OWASP Juice Shop Fonksiyonel Test Uygulaması

---

## 1. Yönetici Özeti

### Paragraf 1: Sonuç

Benim özel hedefim, literatür taramasında ve test planında belirtildiği gibi, OWASP Juice Shop web uygulamasının temel fonksiyonel özelliklerinin (login akışı, arama fonksiyonu, menü yönlendirmeleri, sayfa yükleme, form davranışları) doğru çalıştığını kanıtlamaktı. Bu hedefe Python Playwright ve Pytest kullanarak 34 fonksiyonel test case yazarak başarıyla ulaştım. Tüm testler başarıyla çalıştı (%100 başarı oranı) ve uygulamanın temel kullanıcı akışlarının beklendiği gibi çalıştığını doğruladım. Bu fonksiyonel testler, login akışının (boş alan kontrolü, hatalı giriş, başarılı giriş), arama çubuğunun input alıp sonuçları tetiklemesi, menü/buton yönlendirmelerinin (Score Board, Products sayfaları) doğru route'lara gitmesi, sayfaların yüklenme ve temel UI elementlerinin görünürlüğü, form davranışları ve hata mesajlarının doğruluğu gibi ana kullanıcı akışlarını kapsamaktadır.

### Paragraf 2: Deneyim

Docker Compose ile OWASP Juice Shop'un kurulumu oldukça verimliydi ve uygulamanın localhost:3000 üzerinde çalışmasını sağladı. Ancak Python Playwright ile browser-based fonksiyonel testler yazmak, başlangıçta beklenenden daha karmaşıktı. Karşılaştığım en büyük "sorun" DOM selector'larının stabilitesi ve Angular uygulamasının dinamik yapısıydı: OWASP Juice Shop'un Angular tabanlı yapısı nedeniyle bazı elementler dinamik olarak yükleniyordu ve selector'ların gerçekçi ve stabil olması gerekiyordu. Ayrıca, test izolasyonu sağlamak (her testin birbirini etkilememesi) ve yönlendirme sonrası URL ve element doğrulamalarının doğru yapılması önemli zaman gerektirdi. Bu süreç, kodlama dışı önemli bir zaman gerektirdi ancak sonuçta sağlam ve gerçekçi testler oluşturuldu.

---

## 2. Kurulum ve Yapılandırma

**Kullanılan Araç(lar):** Docker Compose v2.0+, Python v3.13.3, Python Playwright kütüphanesi, Pytest framework

**Kurulum için Tahmini Süre:** 60 dakika (Ortam) + 120 dakika (Test Kodları)

### Kurulum ve Yapılandırma Günlüğü

Docker Compose kullanılarak yapılan ortam kurulumu (`docker-compose.yml` dosyasında ayrıntılı olarak açıklandığı gibi) oldukça verimliydi ve OWASP Juice Shop uygulamasının localhost:3000 üzerinde çalışmasını sağladı. İlk 60 dakika, Docker Desktop kurulumu, WSL 2 yapılandırması (Ubuntu kurulumu), container'ın çalıştığını ve belirlenen portunda (3000) erişilebilir olduğunu doğrulamaya ayrıldı. Sürtünme, test kodları yazma aşamasında başladı çünkü Playwright ile browser automation yapmak, DOM selector'larının stabil olmasını, test izolasyonunun sağlanmasını ve Angular uygulamasının dinamik yapısına uygun testlerin yazılmasını gerektiriyordu. Toplam 120 dakika, 34 fonksiyonel test case'in yazılması, selector'ların optimize edilmesi ve test akışlarının birbirini etkilememesi için harcandı.

---

## 3. Uygulama Günlüğü: "Yolculuk"

**Hedef Fonksiyonellik:** OWASP Juice Shop'un temel kullanıcı akışlarının fonksiyonel testleri (Login, Arama, Navigation, UI, Form davranışları).

### İşlem Günlüğü

**Kurulum ve Doğrulama (60 dk):** 
- Docker Desktop kurulumu ve yapılandırması
- WSL 2 kurulumu (Ubuntu)
- Python 3.13.3 kurulumu ve PATH yapılandırması
- Tüm Python bağımlılıklarının yüklenmesi (Playwright, Pytest, vb.)
- Playwright browser'larının yüklenmesi
- OWASP Juice Shop container'ının çalıştığının doğrulanması (`docker compose ps`)
- Uygulamanın localhost:3000 üzerinden erişilebilir olduğunun doğrulanması (`test_connection.py`)

**Test Kodları Yazma (120 dk):**
- Test klasör yapısının oluşturulması (`tests/` klasörü)
- Pytest fixtures'ların yazılması (`conftest.py` - browser, context, page)
- Konfigürasyon dosyasının oluşturulması (`config.py` - selector'lar, URL'ler)
- Yardımcı fonksiyonların yazılması (`helpers.py` - login, logout fonksiyonları)
- 5 test dosyasının yazılması:
  - `test_login.py` (5 test case)
  - `test_search.py` (5 test case)
  - `test_navigation.py` (6 test case)
  - `test_ui.py` (10 test case)
  - `test_forms.py` (8 test case)

**Takılı Kaldığım Nokta: Selector Stabilitesi ve Test İzolasyonu (40 dk):**

Asıl zorluk, DOM selector'larının stabil ve gerçekçi olmasını sağlamaktı. Angular uygulamasında bazı elementler dinamik olarak yükleniyordu ve selector'ların uygulamanın varsayılan yapısına uygun çalışması gerekiyordu. Özellikle:
- Arama component'i (`#searchQuery`) bir Angular component'ti ve içindeki gerçek input'u bulmak gerekiyordu
- Body elementinin bazen "hidden" olması nedeniyle farklı doğrulama yöntemleri kullanmak gerekti
- Test izolasyonu için her testin yeni bir browser context kullanması gerekiyordu
- Form validasyon testlerinde disabled buton kontrolü yapmak gerekiyordu

**Test Düzeltmeleri ve Optimizasyon (30 dk):**

İlk test çalıştırmasında bazı testler başarısız oldu. Bu testleri düzeltmek için:
- Body visibility sorunlarını çözdüm (body yerine URL ve sayfa başlığı kontrolü)
- Search input selector'larını düzelttim (Angular component içindeki input'u bulma)
- Form validasyon testlerini güncelledim (disabled buton kontrolü)
- Navigation testlerindeki URL kontrol mantığını iyileştirdim

**İspatın Sonlandırılması (20 dk):**

Tüm testler başarıyla çalıştırıldı ve %100 başarı oranı elde edildi (34/34 test başarılı). Test raporu HTML formatında oluşturuldu (`reports/report.html`) ve tüm fonksiyonelliklerin doğru çalıştığı kanıtlandı.

**En Büyük "Sorun" / "Zorluk":**

En sinir bozucu kısım, Angular uygulamasının dinamik yapısı nedeniyle selector'ların stabil olmamasıydı. Özellikle:
- Arama component'i bir Angular component'ti ve içindeki gerçek input'u bulmak için component'e tıklayıp dialog'u açmak gerekiyordu
- Body elementinin bazen "hidden" olması nedeniyle farklı doğrulama yöntemleri kullanmak gerekti
- Test izolasyonu sağlamak için her testin yeni bir browser context kullanması gerekiyordu

Ancak bu zorluklar, gerçekçi ve stabil testler yazılmasına yol açtı ve uygulamanın gerçek kullanım senaryolarını daha iyi yansıttı.

---

## 4. Son Eserler

**Kod Deposu/Özet Bağlantısı:** 
- GitHub Repository: https://github.com/EsraGumus7/yazilim-kalite-hata-kanit
- Test Dosyaları: `tests/` klasörü (5 test dosyası, 34 test case)
- Dokümantasyon: `belgeler/` ve `senaryolar/` klasörleri
- Test Planı: `test_planı.md` (Test durumu tablosu ile)

**Test Sonuçları:**
- Toplam Test Sayısı: 34
- Başarılı Testler: 34
- Başarısız Testler: 0
- Başarı Oranı: %100
- Test Süresi: ~2.5 dakika

## 5. LLM-QA ile Yansıma ve İlgililik

### Manuel Sürecin Analizi

Manuel fonksiyonel test yazma süreci, "altın veri" üretmek için değerli olsa da, ciddi bağlam parçalanmasından muzdariptir. Bu süreç, test yazıcının üç yerden manuel olarak bilgi toplamasını gerektirir: 
1. Test planı ve gereksinimler (Hedef fonksiyonellikler: login, arama, navigation, UI, form)
2. Uygulama yapısı ve selector'lar (OWASP Juice Shop'un Angular yapısı, DOM elementleri)
3. Test aracının belgeleri (Playwright API, Pytest fixtures, assertion metodları)

Alan bilgisi (fonksiyonel test gereksinimleri), araç sözdizimi (Playwright/Pytest) ve uygulama yapısı (Angular, selector'lar) arasındaki bu geçiş, süreci aşırı derecede yavaş ve hataya açık hale getirir. Özellikle selector'ların stabil olması, test izolasyonunun sağlanması ve Angular uygulamasının dinamik yapısına uygun testlerin yazılması için önemli zaman harcandı.

### LLM-QA Nasıl Yardımcı Olabilirdi

Aracımız burada devrim niteliğinde olabilirdi. LLM-QA sistemine şunu söyleyebilirdim: 

**"`test_planı.md` ve `docker-compose.yml` dosyalarını analiz et. OWASP Juice Shop uygulamasında (localhost:3000) login akışının (boş alan, hatalı giriş, başarılı giriş), arama çubuğunun input alıp sonuçları tetiklemesi, menü/buton yönlendirmelerinin (Score Board, Products sayfaları) doğru route'lara gitmesi, sayfaların yüklenme ve temel UI elementlerinin görünürlüğü, form davranışları ve hata mesajlarının doğruluğu gibi ana kullanıcı akışlarını test eden Python Playwright testleri oluştur. Testler stabil selector'lar kullanmalı, test izolasyonu sağlamalı ve Angular uygulamasının dinamik yapısına uygun olmalı."**

LLM anında şunları yapabilirdi:
1. **Test planını analiz edebilir:** 34 test case'in gereksinimlerini anlayabilir
2. **Uygulama yapısını anlayabilir:** OWASP Juice Shop'un Angular yapısını, selector'larını ve route'larını analiz edebilir
3. **Doğru test kodunu oluşturabilir:** Playwright API'sini kullanarak stabil, gerçekçi ve izole testler yazabilir
4. **Selector optimizasyonu yapabilir:** Angular component'leri, dinamik elementler için doğru selector stratejilerini uygulayabilir
5. **Test izolasyonu sağlayabilir:** Her test için yeni browser context kullanımını otomatik olarak yapılandırabilir

Bu yaklaşım, selector'ların stabil olması, test izolasyonunun sağlanması ve Angular uygulamasının dinamik yapısına uygun testlerin yazılması için harcadığım 120 dakikadan önemli ölçüde tasarruf edebilirdi. Ayrıca, test kodlarının daha tutarlı ve bakımı kolay olmasını sağlayabilirdi.

### LLM-QA'nın Özel Değeri

Bu projede LLM-QA'nın özel değeri şu alanlarda olurdu:

1. **Çoklu Bağlam Entegrasyonu:** Test planı, uygulama yapısı ve test aracı belgelerini tek bir bağlamda birleştirebilirdi
2. **Selector Optimizasyonu:** Angular uygulamasının dinamik yapısına uygun selector stratejilerini otomatik olarak önerebilirdi
3. **Test İzolasyonu:** Her test için yeni browser context kullanımını otomatik olarak yapılandırabilirdi
4. **Hata Önleme:** Yaygın hataları (body visibility, selector stabilitesi, test izolasyonu) önceden tespit edip çözebilirdi
5. **Dokümantasyon Entegrasyonu:** Test senaryolarını, test kodlarını ve test planını otomatik olarak senkronize edebilirdi

Bu, manuel süreçte harcanan 120 dakikayı önemli ölçüde azaltabilir ve daha kaliteli, bakımı kolay test kodları üretilmesini sağlayabilirdi.

---

## Sonuç

Bu deneysel uygulama, OWASP Juice Shop üzerinde 34 fonksiyonel test case yazarak uygulamanın temel kullanıcı akışlarının doğru çalıştığını başarıyla kanıtladı. %100 başarı oranı ile tüm testler geçti ve uygulamanın login, arama, navigation, UI ve form davranışları gibi ana fonksiyonelliklerinin beklendiği gibi çalıştığı doğrulandı. LLM-QA sisteminin bu süreçte kullanılması, test yazma süresini önemli ölçüde azaltabilir ve daha kaliteli, bakımı kolay test kodları üretilmesini sağlayabilir.

