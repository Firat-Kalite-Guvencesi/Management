Deneysel Uygulama Günlüğü
Araştırmacı: Esra Nur Gümüş
Tarih: 27 Kasım 2025
Görev: OWASP Juice Shop Fonksiyonel Test Uygulaması

1. Yönetici Özeti
Paragraf 1: Sonuç
Benim özel hedefim, literatür taramasında ve test planında belirtildiği gibi, OWASP Juice Shop web dağıtımının temel fonksiyonel kütüphaneleri (login verileri, arama fonksiyonu, menü yönlendirmeleri, sayfa yükleme, form çıkışı) doğru çalıştığını kanıtlamaktı. Bu hedefe Python Playwright ve Pytest kullanarak 34 fonksiyonel test senaryosuna ulaştım. Tüm testler başarıyla çalıştı (%100 başarı oranı) ve temel kullanıcı kullanımlarının beklendiği gibi çalışılması doğrulandı. Bu fonksiyonel testler, giriş sonuçları (boş alan kontrolü, hatalı giriş, başarılı giriş), arama sonuçlarının giriş sonuçları tetiklemesi, menü/buton yönlendirmelerinin (Puan Tablosu, Ürünler sayfaları) doğru rota'lara gitmesi, sayfaların yüklenmesi ve temel UI öğelerinin görünmesi, form çıkışı ve hatalarının gibi ana işlemleri.

Paragraf 2: Deneyim
Docker Compose ile OWASP Juice Shop'un kurulumu oldukça verimliydi ve uygulanması localhost:3000 üzerinde çalıştırılmasını sağladı. Ancak Python Playwright ile tarayıcı tabanlı fonksiyonel testler yazmak, başlangıçta beklenenden daha karmaşıktı. Karşılaştığı en büyük "sorun" DOM ​​seçicinin stabilitesi ve Angular'ın dayanıklı dinamik yapısıydı: OWASP Juice Shop'un Angular tabanlı yapısı nedeniyle bazı elementlerin dinamik olarak yüklenmesi gerekiyordu ve selector'ların pratik ve stabil olması gerekiyordu. Ayrıca, testin birbirini etkilememesini sağlamak ve yönlendirmek için URL ve öğe izolasyonunun doğru yapılması önemli zaman gerektirdi. Bu sürecin, önemli olmayan bir zaman gerektirdi ancak sonuçta sağlam ve prosedür çalışmaları yer aldı.

2. Kurulum ve Yapılandırma
Kullanılan Araç(lar): Docker Compose v2.0+, Python v3.13.3, Python Playwright kütüphanesi, Pytest framework

Kurulum için Tahmini Süresi: 60 dakika (Ortam) + 120 dakika (Test Kodları)

Kurulum ve Yapılandırma Günlüğü
Docker Compose kullanılarak yapılan ortam kurulumu ( docker-compose.ymlayrıntılı olarak ayrıntılı olarak açıklandığı gibi) oldukça verimliydi ve OWASP Juice Shop'un çalıştırılabilir localhost:3000 üzerinde çalıştırılması sağlandı. İlk 60 dakika, Docker Desktop kurulumu, WSL 2 kurulumu (Ubuntu kurulumu), Container'ın çalıştırıldığı ve kaydedilen portunda (3000) erişilebilir olduğundan sürekli olarak ayrılır. Sürtünme, test kodları yazma aşamasında başladı çünkü Playwright ile tarayıcı otomasyonu yapmak, DOM selector'larının stabil hale getirilmesi, test yalıtımının korunmasını ve Angular yapısal dinamik yapının uygun testlerin yazılmasının sağlanmasıdu. 120 dakika, 34 fonksiyonel test senaryosunun yazılması, toplam seçicilerin optimize edilmesi ve test akışlarının değişiminin etkilenmemesi için harcandı.

3. Uygulama Günlüğü: "Yolculuk"
Hedef Fonksiyonellik: OWASP Juice Shop'un temel kullanıcı işlemlerinin işlevsel olarak test edildiği (Giriş, Arama, Gezinme, UI, Form devam ediyor).

İşlem Günlüğü
Kurulum ve Doğrulama (60 dk):

Docker Masaüstü kurulumu ve ayarları
WSL 2 kurulumu (Ubuntu)
Python 3.13.3 kurulumu ve PATH kurulumu
Tüm Python programlamalarının yazılımı (Playwright, Pytest, vb.)
Oyun yazarı tarayıcılarının yazmaları
OWASP Juice Shop Container'ının çalıştırılmasının doğrulanması ( docker compose ps)
Uygulamanın localhost:3000 üzerinden erişilebilir biçimde doğrulanması ( test_connection.py)
Test Kodları Yazma (120 dk):

Test bilgisayarındaki ( tests/programların)
Pytest fikstürlerinin yazılması ( conftest.py- tarayıcı, bağlam, sayfa)
Yapılandırma oranlarının değerleri ( config.py- selector'lar, URL'ler)
Yardımcı kapasitesinin yazılması ( helpers.py- giriş yapma, çıkış yapma)
5 test payının yazılması:
test_login.py(5 test vakası)
test_search.py(5 test vakası)
test_navigation.py(6 test vakası)
test_ui.py(10 test vakası)
test_forms.py(8 test vakası)
Takılı Kaldığım Nokta: Selector Stabilitesi ve Test İzolasyonu (40 dk):

Asıl zorluklar, DOM seçicilerin stabil hale getirilmesi ve gerçekleştirilmesinin sağlanması. Açısal değişikliklerin bazı elementler dinamik olarak yükleniyordu ve selector'ların piyasaya sürülme kapasitesi uygun çalışması gerekiyordu. Özellikle:

Arama bileşeni'i ( #searchQuery) bir Angular bileşeni'ti ve İçindeki gerçek girdi'u mevcuttu
Vücut elementinin bazen "gizli" olması nedeniyle farklı yöntem yöntemleri kullanılması gerekti
Testin izolasyonu için yeni bir tarayıcı içeriğinin kullanılması gerekiyordu
Form doğrulama testlerinde devre dışı buton kontrolü yapmak gerekiyordu
Test başvuruları ve Optimizasyon (30 dk):

İlk test çalıştırmasında bazı testler başarısız oldu. Bu testleri düzeltmek için:

Gövde görünürlük sorunları çözülmüyor (gövdenin yerine URL ve sayfa ana başlık kontrolü)
Arama giriş seçici'lerini düzelttim (Açısal bileşen içindeki giriş'u bulma)
Form doğrulama testlerini güncelledim (devre dışı buton kontrolü)
Gezinme testlerindeki URL kontrolünü insan iyileştirmedim
İspatın Sonlandırılması (20 dk):

Tüm testler başarıyla uygulandı ve %100 başarı oranı elde edildi (34/34 test başarılı). Test raporunun HTML formatı oluşturuldu ( reports/report.html) ve tüm fonksiyonelliklerin büyüklüğü doğrulandı.

En Büyük "Sorun" / "Zorluk":

En sinir bozucu kısım, Açısal kırılmanın dinamik yapısı nedeniyle seçicilerin stabil olmamasıydı. Özellikle:

Arama bileşeni'i bir Angular bileşeni'ti ve içindeki gerçek giriş'u bulmak için bileşeni'e açmak diyalog'u açmak gerekiyordu
Vücut elementinin bazen "gizli" olması nedeniyle farklı yöntem yöntemleri kullanılması gerekti
Testin izolasyonunu sağlamak için yeni bir tarayıcı içeriğinin kullanılması gerekiyordu
Ancak bu zorluklar, kalıcı ve stabil testlerin yazılmasına yol açtı ve uygulanması gerçek kullanım senaryolarını daha iyi yansıttı.

4. Son Eserler
Kod Deposu/Özet Bağlantısı:

GitHub Deposu: https://github.com/EsraGumus7/yazilim-kalite-hata-kanit
Test Dosyaları: tests/parçalar (5 test dosyası, 34 test senaryosu)
Dokumantasyon: belgeler/ve senaryolar/klasörleri
Test Planı: test_planı.md(Test durumu tablosu ile)
Test Sonuçları:

Toplam Test Sayısı: 34
Başarılı Testler: 34
Başarısız Testler: 0
Başarı Oranı: %100
Test Süresi: ~2,5 dakika

5. LLM-QA ile Yansıma ve İlgililik
Manuel Sürecin Analizi
Manuel fonksiyonel test yazma süreci, "altın veri" kaydı için değerli olsa da, ciddi hasar parçalanmasından muzdariptir. Bu süreç, test yazıcısının üç yerden manuel olarak bilgi toplamasını gerektirir:

Test planı ve değişiklikleri (Hedef işlevsellikleri: giriş, arama, gezinme, kullanıcı arayüzü, form)
Uygulama yapısı ve seçiciler (OWASP Juice Shop'un Angular yapısı, DOM elementleri)
Test aracının belgeleri (Playwright API, Pytest fikstürleri, iddia metodları)
Alan bilgisi (fonksiyonel test çözümleri), araç söz dizimi (Playwright/Pytest) ve uygulama yapısı (Angular, selector'lar) arasındaki bu geçiş, süreci aşırı derecede yavaş ve hataya açık hale gelir. Özellikle selector'ların stabil olması, test izolasyonunun sürdürülmesi ve Açısal aralıkların dinamik özellikleri uygun testlerin yazılması için önemli zaman harcandı.

LLM-QA Nasıl Yardımcı Olabilirdi
Aracımız burada değişebilecektir. LLM-QA sistemini şunu belirtebilirim:

" test_planı.mdve docker-compose.ymlödemelerin analiz et. OWASP Juice Shop (localhost:3000) giriş verilerinin (boş alan, hatalı giriş, başarılı giriş), arama sonuçların giriş sonuçları tetiklemesi, menü/buton yönlendirmelerinin (Score Board, Products) doğru rota'lara gitmesi, sayfaların doldurulması ve temel UI elemanlarının göründüğü, form çıkışı ve hata mesajlarının çalıştığı gibi ana bilgisayarlarını test eden Python Playwright testleri oluşturmak. Açısal yapının dinamik yapıya uygun olması gerekir."

LLM anlık olarak yapabiliyordu:

Test planını analiz edebilir: 34 test senaryosunun sonuçlarını anlayabilir
Uygulamayı anlayabilir: OWASP Juice Shop'un Angular, selector'larını ve Route'larını analiz edebilir
Doğru test işlemlerini gerçekleştirir: Playwright API'sini kullanarak stabil, izolasyonlu ve izolasyonlu testler yazabilir
Selector değişimiu yapabilir: Angular Component'leri, dinamik elementler için doğru seçici stratejilerini uygulayabilir
Test izolasyonu sağlayabilir: Testi için yeni tarayıcı bağlamı otomatik olarak yapılandırılabilir
Bu arada, selector'ların stabil olması, test izolasyonunun yalıtımı ve Açısal dayanıklı dinamik yapılar uygun testlerin yazılması için harcadığım 120 dakikadan önemli tasarruf sağlayabilirdi. Ayrıca test kodlarının daha iyi birleştirilmesi ve bakımının kolaylaştırılması sağlanıyordu.

LLM-QA'nın Özel Değeri
Bu projede LLM-QA'nın özel değerleri şu şekilde olacaktı:

Çoklu Bağlam Entegrasyonu: Test planı, uygulama yapısı ve test aracı belgeleri tek birleştirilebilir birleştirilebilirdi
Selector Optimizasyonu: Açısal dinamik yapıya uygun selector stratejilerini otomatik olarak önerebilirdi
Test İzolasyonu: Test için yeni tarayıcı bağlamı otomatik olarak yapılandırılabilirdi
Hata Önleme: Yaygın hatalar (gövde görünürlüğü, seçici stabilitesi, test izolasyonu) önceden tespit edilip çözülebilirdi
Dokumantasyon Entegrasyonu: Test senaryolarını, test kodlarını ve test planını otomatik olarak doldurabilirdi
Bu, manuel olarak harcanan 120 dakikalık önemli miktarlarda ve daha kaliteli, bakımı kolay test kodlarını sağlayabilmektedir.

Sonuç
Bu uygulama, OWASP Juice Shop üzerinde 34 fonksiyonel test senaryosu ile ulaşılan kanıt temel kullanımlarının doğru çalışmasını başarıyla gerçekleştirdi. %100 başarı oranı ile tüm testler yapıldı ve oynatılması, oturum açma, arama, gezinme, kullanıcı arayüzü ve form oluşması gibi ana işlevselliklerinin beklendiği gibi doğrulanması sağlandı. LLM-QA sisteminin bu sürecin kullanılması, test yazma süresinin önemli ölçüde artması ve daha kaliteli, bakımı kolay test kodlarının çalışmasını sağlar.
