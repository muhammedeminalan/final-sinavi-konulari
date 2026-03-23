# ÇIKTI 1 — MARKDOWN SUNUM
Bu sunum yalnızca `veritabani/veri_tabanı.pdf` içeriğinden üretilmiştir.
---
## Bölüm 1 — Kısaltmalar Sözlüğü
Ünite metninde geçen temel kısaltmalar DBMS, DDL, DML, SQL, ER, ODBC, JDBC, DBA ve DB'dir. Slaytlarda bu kısaltmaların çoğu başlık düzeyinde doğrudan verilmiştir ve konular arası bağlantıyı kurmak için ana omurgayı oluşturur.

DBMS (Veritabanı Yönetim Sistemi) verinin saklanması ve yönetimi için ortam sağlar; DDL şema tanımlar; DML veriye erişir/değiştirir; SQL yaygın nonprocedural sorgu dilidir; ER kavramsal tasarım modelidir; ODBC/JDBC uygulama programı arayüzüdür; DBA yetkili yöneticidir; DB ise verinin tutulduğu veritabanını ifade eder.

Bu kısaltmalar rol olarak farklıdır: DB veri kümesinin kendisi, DBMS onu yöneten yazılım ortamı, DDL/DML ise DBMS içinde kullanılan dil sınıflarıdır. ODBC/JDBC dil değil bağlantı köprüsüdür. ER tasarım aşamasında, SQL ise sorgulama aşamasında ağırlık kazanır.

Örnek akış: Bir kurum önce ER ile tasarım yapar, DDL ile tabloları kurar, DML/SQL ile kayıt ekler-günceller, uygulama ODBC/JDBC ile bağlanır, DBA yetkilendirme ve performans takibini yapar.

Sınavda en çok karıştırılan nokta DB ile DBMS ayrımı ve DDL-DML ayrımıdır. Kısaltma sorularında yalnızca açılım değil, hangi aşamada kullanıldığını da yazmak tam puan getirir.

---
## Bölüm 2 — Veritabanı Nedir
Slaytta veritabanı düzenli bilgiler topluluğu, bilgisayar ortamında saklanan düzenli veriler ve programlarca işlenebilen sistematik veri yığını olarak tanımlanır.

Veritabanı; sistematik erişim, yönetilebilirlik, güncellenebilirlik, taşınabilirlik ve veriler arası tanımlı ilişkiler özellikleriyle çalışır. Bu özellikler birlikte olduğunda veri yalnızca depolanmaz, yönetilir ve sorgulanabilir hale gelir.

Basit dosya yığınından farkı, veriler arası ilişkinin tanımlı olması ve erişimin sistematik şekilde yürütülmesidir. Dosya yaklaşımında kayıt tutmak mümkündür; ancak yönetilebilirlik ve tutarlılık seviyesi düşer.

Örneğin bir okul veritabanında öğrenci, ders ve not verileri tek tek dosyalarda da tutulabilir; fakat veritabanında bu kayıtlar ilişkili tutulduğu için güncelleme ve raporlama daha güvenli yapılır.

Sınavda 'veritabanının özellikleri nelerdir' sorusunda sadece tanım değil, neden gerekli olduklarını yazmak gerekir: sistematik erişim hatayı azaltır, yönetilebilirlik bakım kolaylaştırır, güncellenebilirlik değişime uyum sağlar.

---
## Bölüm 3 — DBMS Nedir
DBMS, birbiriyle ilişkili veriler topluluğunu yöneten, veriye erişim için program seti sunan sistemdir. Slaytta MySQL, MSSQL Server ve Oracle örnekleri verilir.

DBMS; verilerin verimli depolanmasını, erişimini ve yönetimini aynı ortamda birleştirir. Kullanıcıya kullanım kolaylığı ve verimli çalışma ortamı sağlar; ayrıca belirli bir kuruluş hakkında bilgiyi düzenli tutar.

DBMS doğrudan verinin kendisi değildir; veriyi yöneten katmandır. Dosya sistemine göre farkı, bütünlük, eşzamanlılık ve güvenlik problemlerine yerleşik çözümler sunmasıdır.

Bankacılık uygulamasında hesap, işlem ve müşteri bilgileri DBMS üzerinde yönetildiğinde hem işlem hızı hem de veri doğruluğu korunur. Aynı sistemde çok kullanıcı aynı anda çalışabilir.

Sınavda DBMS tanım sorularında iki ana ifade beklenir: 'verilere erişmek için program seti' ve 'kolay/verimli depolama ve yönetim'. Ürün örneği yazmak (MySQL vb.) genelde puan artırır.

---
## Bölüm 4 — DBMS Kullanım Alanları
Slaytlarda kullanım alanları bankacılık, havayolları, üniversiteler, satış, imalat ve insan kaynakları olarak sıralanır. Her alanda ortak ihtiyaç, düzenli ve güvenli veri yönetimidir.

Bankacılıkta tüm işlemler; havayollarında rezervasyon ve planlama; üniversitelerde kayıt ve notlar; satışta müşteri-ürün-satın alma; imalatta üretim- envanter-sipariş-tedarik zinciri; İK'da çalışan-maaş-vergi bilgileri DBMS ile yönetilir.

Alanlar farklı görünse de veri akış mantığı aynıdır: kayıt alma, güncelleme, sorgulama ve raporlama. Fark, iş kurallarının türündedir; örneğin bankacılıkta atomiklik kritik, İK'da yetkilendirme daha belirgindir.

Havayolu rezervasyonunda koltuk planlama, satış ve iptal işlemleri eşzamanlı yürütülür. DBMS olmasa aynı koltuğun iki farklı kişiye satılması gibi tutarsızlıklar oluşabilir.

Sınavda alan bazlı sorular genellikle 'hangi veri tutulur' biçiminde gelir. Cevapta alan adı + veri örneği yazmak gerekir: örn. satış -> müşteri, ürün, satın alma kayıtları.

---
## Bölüm 5 — Dosya Sistemlerinin Sorunları: Veri Tekrarı ve Tutarsızlığı
Dosya tabanlı yaklaşımda aynı bilgi farklı dosyalarda kopyalandığında veri tekrarı oluşur. Bir güncelleme tek yerde yapılıp diğer yerde atlanırsa tutarsızlık oluşur.

Sorunun kaynağı çoklu dosya biçimi ve merkezi yönetim eksikliğidir. Aynı müşteri bilgisi farklı dosyalarda tutulduğunda birinin güncel, diğerinin eski kalması kaçınılmazdır.

Bu problem, veri izolasyonundan farklı olarak doğrudan aynı verinin birden fazla kopyasına odaklanır. İzolasyonda dosyalar arası birlikte kullanım zorluğu vardır; tekrarda ise aynı veri farklı değer alır.

Müşterinin adresi satış dosyasında güncellenip muhasebe dosyasında güncellenmezse fatura yanlış adrese gider. İşletme açısından bu durum operasyonel ve mali hata üretir.

Sınavda 'DBMS bu sorunu nasıl çözer?' sorusunda beklenen vurgu merkezileşmedir: tek veritabanı yapısıyla tekrar azalır, güncelleme tek noktadan yapılır, tutarlılık korunur.

---
## Bölüm 6 — Dosya Sistemlerinin Sorunları: Erişim Zorluğu ve Veri İzolasyonu
Slaytta veriye erişimde zorluk ve veri izolasyonu birlikte verilir. Her yeni görev için yeni program yazma ihtiyacı dosya sisteminin en önemli darboğazlarından biridir.

Dosya biçimleri farklı olduğunda bir raporu hazırlamak için verileri farklı kaynaklardan elle birleştirmek gerekir. Bu da geliştirme süresini uzatır ve hata olasılığını artırır.

Veri tekrarı probleminde odak kopyalanan kayıtlar iken burada odak erişim maliyetidir. Veri mevcut olsa bile bütünleşik erişim yolu yoksa bilgi üretimi zorlaşır.

Belirli bir departmanın çalışan raporu için ayrı dosyalardan çekim yapmak yerine DBMS üzerinde tek sorgu ile rapor alınması erişim zorluğunu ortadan kaldırır.

Sınavda bu başlık çoğunlukla 'neden her yeni görev için yeni program gerekir?' şeklinde gelir. Cevap: standart sorgu katmanı yoktur, dosya formatları heterojendir, birlikte çalışma düşüktür.

---
## Bölüm 7 — Dosya Sistemlerinin Sorunları: Bütünlük Sorunları
Bütünlük kısıtlamalarının (ör. hesap bakiyesi > 0) program kodunun içine gömülmesi, kural yönetimini zorlaştırır. Slayt bu durumu doğrudan bütünlük sorunu olarak tanımlar.

Kural uygulama koduna dağılınca yeni kısıtlama eklemek veya mevcut kuralı değiştirmek için birçok modülün ayrı ayrı güncellenmesi gerekir. Bu da bakım maliyeti üretir.

Atomiklikten farkı şudur: bütünlük sorunu kuralların doğruluğu ile ilgilidir; atomiklik ise işlemin tamamının ya hep ya hiç uygulanmasıyla ilgilidir.

Bir sistemde bakiye eksiye düşemez kuralı sadece bazı ekranlarda uygulanırsa farklı işlem kanallarında farklı sonuç oluşur ve bütünlük bozulur.

Sınavda beklenen cevap DBMS'in merkezi kısıtlama yönetimi sunduğudur. Kısıtlar şema ve bütünlük tanımları üzerinden tek noktadan uygulanır.

---
## Bölüm 8 — Dosya Sistemlerinin Sorunları: Atomiklik
Atomiklik, bir güncelleme dizisinin ya tamamen yapılması ya da hiç yapılmaması ilkesidir. Slaytta para transferi örneğiyle açıklanır.

Transfer işleminde bir hesaptan düşüm yapılıp diğer hesaba ekleme yapılmadan sistem durursa veritabanı tutarsız olur. Atomiklik bu kısmi güncellemeyi engellemek için gereklidir.

Eşzamanlılık sorunu aynı anda birden fazla işlemin çakışmasıdır; atomiklikte tek bir işlemin yarım kalması ön plandadır. İki kavram farklı risk türlerini ifade eder.

A hesabından 100 TL çıkıp B hesabına eklenmezse toplam para azalır. Bu senaryo atomiklik ihlalinin klasik gerçek hayat sonucudur.

Sınavda para transferi senaryosunda doğru ifade 'işlem tamamlanmalı veya hiç olmamalıdır'. Bu cümleyi yazmak doğrudan atomiklik tanım puanı getirir.

---
## Bölüm 9 — Dosya Sistemlerinin Sorunları: Eşzamanlılık ve Güvenlik
Birden çok kullanıcı tarafından eşzamanlı erişim performans için gereklidir; ancak kontrolsüz erişim tutarsızlığa yol açar. Güvenlik de ayrı bir temel sorundur.

Slayttaki örnekte iki kişi aynı bakiyeyi okuyup eşzamanlı güncellerse biri diğerini ezebilir. DBMS eşzamanlılık kontrolüyle bu etkileşimi düzenler.

Eşzamanlılık veri bütünlüğünü işlem sırasından etkiler; güvenlik ise veriye kimin hangi yetkiyle erişeceğini düzenler. Birincisi zamanlama, ikincisi yetki problemidir.

Online bankacılıkta aynı hesabın mobil ve web üzerinden aynı anda güncellenmesi mümkündür. Yetkisiz erişim engeli yoksa hem gizlilik hem doğruluk zarar görür.

Sınav sorularında 'kontrolsüz eşzamanlı erişim neden sorun?' ifadesine mutlaka 'tutarsızlık' cevabı verilir. Güvenlik için de yetkilendirme/erişim kontrolü vurgulanır.

---
## Bölüm 10 — DBMS Bileşenleri
DBMS bileşenleri slaytta kullanıcılar, yazılımlar, donanım (hardware) ve veri (data) olarak özetlenir. Bileşenlerin birlikte çalışması sistemin bütününü oluşturur.

Kullanıcılar veriyi talep eder, yazılım katmanı işleyişi yönetir, donanım depolamayı sağlar, veri ise numeric, non-numeric ve logical biçimlerde veritabanında tutulur.

Bileşenler rol bakımından ayrılır: donanım fiziksel taşıyıcıdır, yazılım yönetici katmandır, kullanıcı talep üretir, veri ise işlenen içeriktir. Birinin eksikliği sistemin çalışmasını aksatır.

Disk üzerinde tutulan müşteri verisi (data), DBMS yazılımı üzerinden sorgulanır; son kullanıcı uygulamayla erişir; DBA yetki ve performans ayarını yönetir.

Sınavda numeric/non-numeric/logical ayrımı sık sorulur. Cevapta sayısal veri, metinsel veri ve mantıksal/iş kuralı anlamındaki veri ayrımını birlikte yazmak gerekir.

---
## Bölüm 11 — DBMS Veri Yapı Taşları ve Avantajları
Veri yapı taşları kolon/alan, satır/tuple/kayıt ve tablo kavramlarıdır. Slayt ayrıca veri bağımsızlığı, verimli erişim, bütünlük-güvenlik, yönetim, eşzamanlı erişim ve uygulama süresi kısalması avantajlarını listeler.

Kolonlar öznitelikleri, satırlar tekil kayıtları, tablolar ise ilişkisel veri kümesini temsil eder. DBMS bu yapıları standardize ederek sorgu ve güncelleme işlemlerini düzenler.

Kolon-satır-tablo ayrımı yapısaldır; avantajlar ise bu yapının yönetim sonucu doğurduğu çıktılardır. Örneğin eşzamanlı erişim bir yapı değil, DBMS'in yönetim kabiliyetidir.

Müşteri tablosunda her satır bir müşteriyi, her kolon müşteri özelliğini taşır. Bu düzen sayesinde aynı veriye çok kullanıcı kontrollü biçimde erişebilir.

Sınavda 'tuple nedir' ve 'DBMS avantajları' birlikte gelebilir. Yapısal tanım ile yönetimsel faydayı aynı cevapta ayrıştırarak vermek gerekir.

---
## Bölüm 12 — DBMS Ne Zaman Kullanılmaz
Slayt, DBMS kullanımının genel maliyetini vurgular: başlangıçta donanım-yazılım-eğitim yatırımı, veri tanımlama/işleme maliyeti ve güvenlik-eşzamanlılık-kurtarma ek yükü.

Bu maliyetler küçük ve değişmeyecek sistemlerde gereksiz olabilir. Veriye çok kullanıcılı erişim yoksa dosya tabanlı düzen daha cazip hale gelebilir.

DBMS'in güçlü olduğu yer karmaşık, değişen ve çok kullanıcılı ortamlardır. Basit/tek kullanıcı/az değişen senaryolarda maliyet-fayda dengesi dosya sistemine kayabilir.

Nadiren güncellenen ve tek kişinin kullandığı küçük bir kayıt listesi için DBMS kurulum maliyeti, sağlayacağı ek faydadan daha yüksek olabilir.

Sınav sorusu genelde 'DBMS her zaman kullanılmalı mı?' şeklinde gelir. Doğru yaklaşım koşullu cevaptır: gereksinim küçükse dosya yaklaşımı tercih edilebilir.

---
## Bölüm 13 — 3 Seviyeli Mimari Genel Bakış
3 seviyeli mimari External, Conceptual ve Internal seviyelerinden oluşur. Amaç, kullanıcı görünümü, mantıksal yapı ve fiziksel depolamayı ayırarak karmaşıklığı yönetmektir.

External seviye kullanıcıya görünen kısmı; conceptual seviye tüm verinin mantıksal bütününü; internal seviye fiziksel depolama ayrıntılarını taşır. Katman ayrımı değişiklik etkisini sınırlar.

Tek katmanda tüm ayrıntının birlikte olması bakım zorluğu doğurur. 3 seviyeli yaklaşımda her seviye farklı sorumlulukla tanımlandığı için veri bağımsızlığı güçlenir.

Kullanıcı maaş bilgisini görmeden personel kaydını inceleyebilir (external görünüm), aynı anda sistem mantıksal ilişkileri ve fiziksel depolamayı kendi içinde yönetir.

Sınavda neden ayrıştırıldığı sorulursa 'güvenlik, soyutlama, bakım kolaylığı ve veri bağımsızlığı' anahtar cevaplarıdır.

---
## Bölüm 14 — External Seviye (Dış Seviye)
Dış seviye, veritabanının her kullanıcıyla ilgili olan kısmını tanımlar. Kullanıcı veriyi görür ama şema ve depolama ayrıntılarını bilmek zorunda değildir.

Kullanıcı sadece görünüm düzeyine dönen veriyle ilgilenir. Bu sayede farklı kullanıcılar aynı veritabanını kendi gereksinimlerine göre farklı görünümde kullanabilir.

Conceptual seviyeden farkı kapsamdır: conceptual tüm veritabanı gerçekliğini taşır, external yalnızca kullanıcıya gerekli parçayı taşır. Internal seviyeden farkı ise fiziksel ayrıntı içermemesidir.

İK personeli çalışan kayıtlarını görürken finans kullanıcısı maaş odaklı görünüm alabilir. İki kullanıcı da aynı DB üzerinde farklı görünümle çalışır.

Sınavda 'kullanıcı neyi bilmez?' sorusu gelebilir. Doğru cevap: tablo fiziksel düzeni, depolama ayrıntısı ve iç şema teknikleri external seviyede gizlenir.

---
## Bölüm 15 — Conceptual Seviye (Kavramsal Seviye)
Kavramsal seviye veritabanında hangi verilerin depolandığını ve veriler arası ilişkileri tanımlar. Tüm varlıklar, özellikler, kısıtlamalar, güvenlik ve bütünlük bilgileri bu düzeydedir.

Bu seviye kurumun veriyi nasıl anlamlandırdığının merkezidir. Uygulamalardan bağımsız mantıksal model burada kurulur ve sistemin iş kuralları burada korunur.

External seviyeye göre daha genel ve merkezi bir çerçeve sunar; internal seviyeye göre ise fiziksel ayrıntı taşımaz. Yani 'ne var ve nasıl ilişkili' sorusunun yanıtıdır.

Öğrenci, ders, not varlıklarının birbiriyle ilişkisi, notların hangi kısıtlarla saklanacağı gibi kurallar kavramsal düzeyde tanımlanır.

Sınavda kavramsal seviye için varlık-özellik-ilişki-kısıtlama dörtlüsünü birlikte yazmak yüksek olasılıkla tam puan getirir.

---
## Bölüm 16 — Internal Seviye (İç Seviye)
İç seviye fiziksel seviye olarak da geçer ve verinin depolama cihazlarında gerçekte nasıl saklandığını açıklar. Alan tahsisi, sıkıştırma ve şifreleme teknikleri bu seviyededir.

DBMS bu seviyede dosya düzeni, erişim yolu ve fiziksel yerleşimi belirler. Kullanıcılar bu ayrıntıyı görmeden veriye erişebilir.

External/Conceptual düzeyler mantıksal görünüm sağlar; internal düzey fiziksel uygulamadır. Bu nedenle mimarinin en düşük seviyesidir.

Sabit diskten SSD'ye geçiş veya dizin düzeni değişikliği iç seviyede gerçekleşir; uygulama ve kullanıcı görünümü etkilenmeden devam eder.

Sınavda 'neden en düşük seviye?' sorusuna 'fiziksel depolama ayrıntılarını taşıdığı için' cevabı verilir. Sıkıştırma-şifreleme örneği eklemek puanı güçlendirir.

---
## Bölüm 17 — Soyutlama Düzeyleri
Soyutlama düzeyleri fiziksel, mantıksal ve görünüm seviyeleridir. Amaç kullanıcıyı gereksiz ayrıntıdan korumak ve veriyle çalışmayı kolaylaştırmaktır.

Fiziksel düzey kayıtların nasıl saklandığını; mantıksal düzey veriler arası ilişkiyi; görünüm düzeyi ise uygulamaya gösterilen seçilmiş veriyi yönetir. Görünüm düzeyi güvenlik için bazı bilgileri gizleyebilir.

Fiziksel düzey depolamaya odaklıdır, mantıksal düzey anlam ve ilişkiye odaklıdır, görünüm düzeyi kullanıcı ihtiyacına odaklıdır. Katmanlar birlikte veri bağımsızlığını güçlendirir.

Maaş alanı mantıksal modelde var olabilir; fakat görünüm düzeyinde normal kullanıcıdan gizlenir. Böylece hem veri korunur hem işlev sürer.

Sınavda tabloyla karşılaştırma beklenir; 'kim kullanır, ne içerir, hangi ayrıntıyı gizler' ekseninde yanıt yazılmalıdır.

| Düzey | Ne Yapar | Kim Kullanır | İçerik |
| --- | --- | --- | --- |
| Fiziksel Düzey | Kaydın depoda nasıl saklandığını tanımlar. | Sistem/DBMS iç mekanizması, yönetim tarafı | Dosya düzeni, depolama ayrıntısı, fiziksel yerleşim |
| Mantıksal Düzey | Veritabanında hangi verinin ve hangi ilişkilerin tutulduğunu tanımlar. | Tasarımcılar, DBA, geliştiriciler | Varlıklar, ilişkiler, kısıtlar, mantıksal şema |
| Görünüm Düzeyi | Kullanıcıya gerekli veriyi gösterir, gereksiz ayrıntıyı gizler. | Son kullanıcılar ve uygulama kullanıcıları | Yetkiye göre filtrelenmiş veri görünümü; örn. maaşın gizlenmesi |

---
## Bölüm 18 — 1 Katmanlı Mimari
1-tier mimaride veritabanı doğrudan kullanıcı tarafından kullanılabilir. Yapılan değişiklikler doğrudan veritabanına yansır.

Bu yapı son kullanıcıya dost bir soyutlama sağlamaz; daha çok programcıların hızlı yanıt için yerel uygulama geliştirdiği senaryolarda kullanılır.

2-tier ve 3-tier yapılarda istemci-sunucu ayrımı varken 1-tier yaklaşımda ara katman yoktur. Bu durum hız avantajı sağlayabilir ama yönetim ve güvenlik açısından sınırlıdır.

Geliştiricinin test amaçlı doğrudan veritabanına bağlanıp düzenleme yaptığı yerel ortam 1-tier yaklaşımına örnektir.

Sınavda 'neden son kullanıcı için uygun değil?' sorusuna doğrudan erişim nedeniyle araçsallaştırma, güvenlik ve kullanım kolaylığı eksikliği cevabı verilir.

---
## Bölüm 19 — 2 Katmanlı Mimari
2-tier mimari temel istemci-sunucu modelidir. İstemci uygulaması sunucu tarafındaki veritabanı ile doğrudan iletişim kurar.

Kullanıcı arayüzü ve uygulama programı istemci tarafında, sorgu işleme ve işlem yönetimi sunucu tarafında çalışır. Bağlantı için ODBC ve JDBC gibi API arayüzleri kullanılır.

1-tier'a göre rol ayrımı daha nettir; 3-tier'a göre ise arada ek uygulama katmanı yoktur. Bu nedenle doğrudan ve hızlı iletişim avantajı sunar.

Masaüstü istemci uygulamasının ODBC/JDBC üzerinden DB sunucusuna bağlanıp sorgu çalıştırması tipik 2-tier akışıdır.

Sınavda ODBC/JDBC'nin rolü sorulursa 'istemci ile DBMS arasındaki bağlantı/program arayüzü' ifadesi kullanılmalıdır.

---
## Bölüm 20 — 3 Katmanlı Mimari
3-tier mimaride istemci ve sunucu arasında ek bir uygulama katmanı bulunur. İstemci doğrudan veritabanı ile konuşmaz.

İstemci uygulama sunucusuyla etkileşir; uygulama sunucusu da veritabanıyla iletişim kurar. Son kullanıcı, veritabanının uygulama katmanı ötesindeki varlığını bilmeden sistemi kullanır.

2-tier'da istemci DB'ye doğrudan bağlanırken 3-tier'da middle katman arabulucudur. Bu yapı özellikle büyük web uygulamalarında ölçeklenebilirlik ve yönetim için tercih edilir.

Web arayüzünden gelen isteklerin önce uygulama sunucusunda işlenip sonra veritabanına iletilmesi 3-tier mimarinin tipik örneğidir.

Sınavda 'neden büyük web uygulamalarında 3-tier?' sorusunda arabulucu katmanın yönetim, güvenlik ve iş mantığı ayrıştırması sağladığı belirtilir.

| Karşılaştırma | 2-Tier | 3-Tier |
| --- | --- | --- |
| Bağlantı Yapısı | İstemci doğrudan DB sunucusuna bağlanır. | İstemci, uygulama katmanı üzerinden DB'ye ulaşır. |
| Ara Katman | Yok | Var (Application/Middle) |
| İletişim | Doğrudan ve hızlı | Dolaylı ama yönetilebilir/ölçeklenebilir |
| Kullanım Senaryosu | Daha basit istemci-sunucu uygulamaları | Büyük web uygulamaları |
| Güvenlik ve Ayrışma | Daha sınırlı | Katman ayrımı nedeniyle daha güçlü yönetim |

---
## Bölüm 21 — 3 Katmanlı Mimari Katman Detayları
Data katmanı sorgu işleme diliyle birlikte verinin tutulduğu katmandır. Middle katman kullanıcıya soyut görünüm sunar ve kullanıcı ile DB arasında arabulucu olur.

Presentation katmanında son kullanıcı çalışır ve bu katmanın ötesindeki DB ayrıntılarını bilmez. Böylece görevler katmanlara dağıtılır ve sistem yönetimi kolaylaşır.

Data katmanı kalıcılık ve sorgu yürütme odaklıdır; middle katman iş akışı ve yönlendirme odaklıdır; presentation katmanı etkileşim ve gösterim odaklıdır.

Kullanıcı formu doldurur (presentation), kurallar middle katmanda uygulanır, sonuç data katmanında saklanır ve geri döner.

Katman sorularında karışıklığı önlemek için 'kimle konuşur?' yaklaşımı kullanılabilir: kullanıcı->presentation, presentation->middle, middle->data.

---
## Bölüm 22 — Veri Bağımsızlığı Nedir
Veri bağımsızlığı, sistem değişirken kullanıcı ve uygulamaların mümkün olduğunca etkilenmemesini hedefler. Slaytta meta data (veri hakkında veri) kavramıyla birlikte verilir.

DBMS büyüdükçe gereksinimler değişir; tüm veriler birbirine sıkı bağımlıysa sistem karmaşıklaşır. Veri bağımsızlığı bu bağımlılığı azaltarak evrimi yönetilebilir kılar.

Veri bağımsızlığı, yalnızca depolama tekniği değişimi değildir; mantıksal ve fiziksel düzeyde iki ayrı kapsama ayrılır. Bu ayrım sınavın temel ayırt noktasıdır.

Meta verilerle verinin yapısı ve kuralları tanımlanır. Yapıdaki kontrollü değişiklikler uygulamayı kırmadan yürütülebilirse veri bağımsızlığı sağlanmış olur.

Sınavda meta data tanımı genelde sorulur: 'verilerle ilgili veriler'. Ayrıca iki tür veri bağımsızlığı (mantıksal/fiziksel) birlikte yazılmalıdır.

---
## Bölüm 23 — Mantıksal Veri Bağımsızlığı
Mantıksal veri bağımsızlığı, diskteki gerçek verileri etkilemeden mantıksal yapıda değişim yapabilme mekanizmasıdır. Slaytta tablo/ilişki ve kısıt değişiklikleri üzerinden anlatılır.

Yeni öznitelik, varlık veya ilişki ekleme/değiştirme/silme; kayıtları birleştirme ya da bölme işlemleri mevcut uygulamaları yeniden yazmadan yapılabilmelidir.

Fiziksel bağımsızlık depolama detayını değiştirir; mantıksal bağımsızlık şema/mantık düzenini değiştirir. Bu nedenle uygulama etkisi açısından mantıksal bağımsızlık daha zor kabul edilir.

Bir tabloda yeni alan eklendiğinde rapor ekranlarının tamamını baştan yazmadan sistemin çalışması mantıksal veri bağımsızlığına örnektir.

Sınavda örnek sorulursa en güvenli cevap: 'mevcut uygulamaları yeniden yazmadan yeni öznitelik/varlık/ilişki ekleme'.

---
## Bölüm 24 — Fiziksel Veri Bağımsızlığı
Fiziksel veri bağımsızlığı, şema veya mantıksal verileri etkilemeden fiziksel depolamayı değiştirebilme gücüdür. Slaytta SSD örneği açıkça verilir.

Depolama cihazı, dosya düzenleme tekniği, erişim yöntemi, dizin ve veritabanı konumu (C sürücüsünden D sürücüsüne) gibi değişiklikler bu kapsamdadır.

Mantıksal bağımsızlıktan farkı değişen katmandır: burada fiziksel altyapı değişir, mantıksal model sabit kalır. Kullanıcı ve uygulama bunu doğrudan hissetmez.

Sabit diskin SSD ile değiştirilmesi performansı etkiler; ancak tablo yapısı ve uygulama işleyişi aynı kalırsa fiziksel veri bağımsızlığı sağlanmıştır.

Sınavda fiziksel bağımsızlık örnekleri liste şeklinde sorulabilir. Cevapta depolama cihazı, erişim yöntemi, dizin ve konum değişimi mutlaka yazılmalıdır.

| Özellik | Mantıksal Veri Bağımsızlığı | Fiziksel Veri Bağımsızlığı |
| --- | --- | --- |
| Değişen Katman | Mantıksal şema/ilişki düzeni | Depolama düzeni ve fiziksel altyapı |
| Uygulamaya Etki | Uygulama yeniden yazılmadan değişim hedeflenir | Mantıksal şemayı etkilemeden değişim hedeflenir |
| Örnek | Yeni öznitelik ekleme, varlık/ilişki değiştirme | HDD->SSD, dosya düzeni/dizin/erişim yöntemi değişikliği |
| Amaç | İş kuralı ve model evrimi | Performans/altyapı evrimi |
| Slayttaki Vurgu | Ekleme-değiştirme-silme, kayıt birleştirme/bölme | C'den D'ye taşıma, depolama cihazı değiştirme |

---
## Bölüm 25 — Örnekler ve Şemalar
Slaytta schema-instance ayrımı programlama dillerindeki tür-değişken benzetmesiyle anlatılır. Şema mantıksal yapı, instance belirli andaki gerçek içeriktir.

Fiziksel şema fiziksel düzey tasarımı; mantıksal şema mantıksal düzey tasarımı ifade eder. Uygulamalar mantıksal şemaya bağlıdır ve iyi tanımlı arayüzler değişim etkisini azaltır.

Şema değişken tipi gibidir ve nispeten daha kalıcıdır; instance değişkenin değeri gibi zamana göre değişir. Karışıklık çoğunlukla bu kalıcılık farkından çıkar.

Müşteri-hesap ilişkisini tanımlayan yapı şemadır; bugün saat 10:00'daki müşteri kayıtlarının tamamı instance'tır.

Sınavda schema-instance farkı sorularında 'yapı vs anlık içerik' ifadesi anahtar cümledir. Fiziksel/mantıksal şema ayrımını da eklemek gerekir.

---
## Bölüm 26 — Veritabanı Kullanıcı Türleri 1
Yerel kullanıcı, DBMS varlığını bilmeden mevcut uygulamalarla etkileşen kullanıcıdır. Örnekler: ATM, online kütüphane, bilet rezervasyon.

Uygulama programcısı ise DML sorgularını C, C++, Java, Pascal gibi dillerde yazar ve sorgular nesne koda dönüştürülerek veritabanı ile iletişim kurar.

Yerel kullanıcı hazır ekranı kullanır; uygulama programcısı altyapıyı kodlar. Biri işlev tüketicisi, diğeri veritabanı etkileşimini üreten geliştiricidir.

ATM'de para çekme yapan kişi yerel kullanıcıdır. ATM yazılımında DML sorgularını yazan geliştirici uygulama programcısıdır.

Sınavda kullanıcı türü sorularında örnekle cevap vermek önemlidir. 'Yerel kullanıcı DB'yi bilmeden uygulamayı kullanır' cümlesi kritik ifadedir.

---
## Bölüm 27 — Veritabanı Kullanıcı Türleri 2
Gelişmiş kullanıcı SQL ile doğrudan veri seçme/ekleme/silme/güncelleme yapar. Uzman kullanıcı özel veritabanı uygulama programları geliştiren sofistike kullanıcıdır. Online kullanıcı DB ile doğrudan çevrimiçi iletişim kurabilir.

Gelişmiş kullanıcı uygulama katmanına ihtiyaç duymadan sorgu diliyle çalışır. Uzman kullanıcı ihtiyaç bazlı karmaşık programlar üretir. Online kullanıcı ise servis üzerinden gerçek zamanlı etkileşir.

Gelişmiş kullanıcı sorgu düzeyinde, uzman kullanıcı geliştirme düzeyinde, online kullanıcı kullanım düzeyinde öne çıkar. Bu ayrım sınavda karşılaştırma olarak sorulur.

SQL tasarımcısı gelişmiş kullanıcı; özel karar destek aracı geliştiren kişi uzman kullanıcı; web panelden anlık işlem yapan müşteri online kullanıcıdır.

Sınavda tablo karşılaştırması beklenirse temel ayrım 'SQL yazma', 'özel program geliştirme', 'çevrimiçi kullanım' başlıklarıyla verilmelidir.

| Kullanıcı Türü | Temel Özellik | Veritabanı ile Etkileşim Şekli |
| --- | --- | --- |
| Gelişmiş Kullanıcı | SQL sorguları yazar, doğrudan çalışır. | SELECT/INSERT/UPDATE/DELETE gibi sorguları doğrudan işletir. |
| Uzman Kullanıcı | Karmaşık ve özel uygulamalar geliştirir. | İhtiyaca özel veritabanı programları üretir. |
| Online Kullanıcı | Çevrimiçi doğrudan etkileşim kurar. | Uygulama/servis üzerinden anlık işlem yapar. |

---
## Bölüm 28 — Veritabanı Yöneticisi (DBA)
DBA, veritabanı sistemini uygulayan kişi veya gruptur. DBMS'in izin verdiği tüm ayrıcalıklara sahiptir ve yetkileri kullanıcıya verebilir/kaldırabilir.

Görevleri şema tanımı, depolama yapısı ve erişim yöntemi tanımı, şema/fiziksel organizasyon değişikliği, yetkilendirme, bütünlük kısıtları, kullanıcı iletişimi, performans izleme ve değişen gereksinimlere yanıtı içerir.

Normal kullanıcı işlem yapar; DBA sistemin tamamını koordine eder. Bu nedenle DBA rolü operasyonel değil yönetsel ve stratejik kapsam taşır.

Kuruluşta yeni bir rapor ihtiyacı doğduğunda DBA hem şema değişimini planlar hem performans etkisini izler hem gerekli erişim izinlerini dağıtır.

Sınavda DBA soruları çoğunlukla görev listesi ister. Listeyi maddeli ve eksiksiz yazmak gerekir; özellikle yetkilendirme ile performans takibini atlamamak önemlidir.

---
## Bölüm 29 — İşlem Yönetimi
İşlem (transaction), veritabanı uygulamasında tek bir mantıksal işlevi gerçekleştiren işlemler koleksiyonudur.

İşlem yönetimi bileşeni güç kesintisi, işletim sistemi çökmesi ve işlem hataları gibi durumlarda veritabanının tutarlı kalmasını sağlar. Eşzamanlılık kontrol yöneticisi işlemler arası etkileşimi denetler.

Atomiklik işlem bütünlüğünü, eşzamanlılık kontrolü ise birden fazla işlemin birlikte güvenli yürütülmesini hedefler. İkisi birlikte tutarlılık katmanını oluşturur.

Para transferinde iki adımın tek işlem gibi ele alınması gerekir. Arıza durumunda yarım kalan güncelleme geri alınarak tutarlılık korunur.

Sınavda işlem yönetimi sorularında 'sistem arızalarına rağmen tutarlılık' ifadesini yazmak kritiktir. Eşzamanlılık kontrol yöneticisini ayrıca tanımlamak puan getirir.

---
## Bölüm 30 — Depolama Yönetimi
Depolama yöneticisi, alt düzey depolanan veri ile uygulama programları/sorgular arasında arayüz sağlayan program modülüdür.

Dosya yöneticisi ile etkileşir; verinin verimli depolanması, alınması ve güncellenmesinden sorumludur. Böylece üst katmanların fiziksel ayrıntıya bağımlılığı azalır.

İşlem yöneticisi tutarlılık ve işlem akışına odaklanırken depolama yöneticisi veri yerleşimi ve erişim verimliliğine odaklanır.

Bir sorgu sonucu hızlı dönüyorsa bunun arkasında depolama yöneticisinin doğru dosya/dizin etkileşimi ve erişim yöntemi seçimi vardır.

Sınavda arayüz rolü sık sorulur: depolama yöneticisi alt düzey veri ile sorgu/uygulama arasında köprü kurar.

---
## Bölüm 31 — Veri Modelleri
Veri modeli, data, data ilişkileri, veri anlambilim ve veri kısıtlamalarını açıklamak için araç koleksiyonudur.

Slaytta ER modeli ve ilişkisel model temel modeller olarak; object-oriented ve semi-structured modeller diğer seçenekler olarak; network ve hierarchical modeller daha eski modeller olarak verilir.

ER kavramsal tasarımda güçlüdür, ilişkisel model depolama/işlemede yaygındır. Diğer modeller özel ihtiyaçlara veya tarihsel yaklaşımlara karşılık gelir.

Bir sistemin önce ER ile tasarlanıp ardından ilişkisel tablolara dönüştürülmesi model geçişinin tipik uygulamasıdır.

Sınavda model listesi sorularında amaç ezberden çok modelin hangi seviyede kullanıldığını ayırt etmektir: ER kavramsal, ilişkisel uygulama odaklıdır.

| Veri Modeli | PDF'deki Konumu | Ne İçin Kullanıldığı |
| --- | --- | --- |
| ER Modeli | Temel model | Kavramsal tasarım, varlık-ilişki gösterimi |
| İlişkisel Model | Temel model | Tablolarda veri depolama ve işleme |
| Object-Oriented Model | Diğer modeller | Nesne merkezli veri temsil gereksinimleri |
| Semi-Structured Model | Diğer modeller | Esnek/yarı yapılı veri temsilleri |
| Network Model | Daha eski model | Tarihsel/klasik bağlantı temelli yapı |
| Hierarchical Model | Daha eski model | Hiyerarşik ağaç benzeri veri yapısı |

---
## Bölüm 32 — ER Modeli Genel
ER modeli veritabanının kavramsal görünümünü tanımlar ve gerçek dünyadaki varlıklar ile ilişkiler etrafında çalışır.

Görünüm düzeyinde veritabanı tasarımı için iyi seçenek olarak verilir. ER diyagramları ilişkisel şema ile eşleştirilebilir; yani ER'den ilişkisel şema üretmek mümkündür.

ER modeli doğrudan sorgu dili değildir; tasarım aracıdır. İlişkisel model ise tablo tabanlı depolama ve işleme modelidir.

Okul sistemi için öğrenci-öğretmen-ders varlıkları ve aralarındaki ilişkiler önce ER üzerinde kurulup sonra tabloya dönüştürülür.

Sınavda ER'nin amacı sorulduğunda 'kavramsal tasarım, varlık-ilişki odaklı yaklaşım ve ilişkisel şemaya dönüştürülebilirlik' birlikte yazılmalıdır.

---
## Bölüm 33 — Entity ve Entity Set
Entity, canlı veya cansız, kolayca tanımlanabilen gerçek dünya nesnesidir. Entity Set, benzer türde varlıkların koleksiyonudur.

Varlıklar nitelikleriyle temsil edilir ve kimlik kazanır. Öğrenci, öğretmen, sınıf, ders gibi varlıklar bir sistemde farklı entity set'ler oluşturur.

Entity tekil örneği, Entity Set ise bu örneklerin sınıfını ifade eder. Bu ayrım şema tasarımında temel düzeyde önemlidir.

'Ayşe Yılmaz' tek bir entity, 'Öğrenci Kümesi' tüm öğrencilerin entity set'idir.

Sınavda en çok karışan nokta budur. Cevapta 'tekil nesne vs benzer nesneler kümesi' cümlesi mutlaka yer almalıdır.

---
## Bölüm 34 — Öznitelik Türleri 1
Basit öznitelik atomik, daha fazla bölünemeyen değerdir. Bileşik öznitelik birden fazla basit öznitelikten oluşur.

Slaytta basit örnek olarak 10 basamaklı telefon numarası; bileşik örnek olarak ad-soyad birleşimi verilir. Tasarımda ayrıştırma düzeyi veri kullanım amacına göre belirlenir.

Basit öznitelik tek parçalıdır; bileşik öznitelik alt bileşenlere ayrılabilir. Bu fark sorgulama ve normalizasyon aşamalarında etkili olur.

Telefon numarasını tek alan tutmak basit öznitelik yaklaşımıdır; tam adı ad ve soyad alanlarına ayırmak bileşik yaklaşımıdır.

Sınavda ayırt etme sorularında ana ipucu şudur: değer anlamlı alt parçalara ayrılabiliyorsa bileşik, ayrılamıyorsa basit kabul edilir.

| Tür | Tanım | Slayttaki Örnek/İpucu | Sınav Ayırt Noktası |
| --- | --- | --- | --- |
| Basit Öznitelik | Atomik, daha fazla bölünemez | 10 basamaklı telefon numarası | Alt bileşene ayrılamıyorsa basit |
| Bileşik Öznitelik | Birden fazla basit öznitelikten oluşur | Tam adın ad+soyad bileşenleri | Anlamlı alt parçalar varsa bileşik |

---
## Bölüm 35 — Öznitelik Türleri 2
Türetilmiş öznitelik fiziksel veritabanında doğrudan tutulmaz; değeri diğer özniteliklerden türetilir. Tek değerli öznitelik tek değer, çok değerli öznitelik birden fazla değer taşır.

Tasarımsal amaç, gereksiz tekrar depolamayı azaltmak ve veri modelini anlamlı kılmaktır. Çok değerli özniteliklerde bir varlık için birden çok kayıt mantığı doğabilir.

Türetilmiş öznitelik depolama açısından farklıdır; tek/çok değerli ayrımı kardinalite açısından farklıdır. Bu iki ayrım farklı eksenlerde düşünülmelidir.

Yaş bilgisinin doğum tarihinden hesaplanması türetilmiş yapı örneğidir. Bir kişinin birden çok telefonu çok değerli öznitelik mantığına karşılık gelir.

Sınavda üçlü karşılaştırma sorusunda depolama var/yok (türetilmiş), değer sayısı tek/çok (tek-çok değerli) şeklinde sistematik cevap verilmelidir.

| Tür | Tanım | Depolama/Değer Yapısı | Örnek Çerçevesi |
| --- | --- | --- | --- |
| Türetilmiş Öznitelik | Diğer özniteliklerden hesaplanır | Fiziksel DB'de doğrudan tutulmayabilir | Doğum tarihinden yaş türetme yaklaşımı |
| Tek Değerli Öznitelik | Tek değer taşır | Her varlık için tek değer | Bir kişiye bir kimlik numarası |
| Çok Değerli Öznitelik | Birden çok değer taşır | Aynı varlık için çoklu değer | Bir kişiye birden çok telefon |

---
## Bölüm 36 — ER Diyagramı Sembolleri 1
ER diyagramında dikdörtgen varlık kümesi setini, elips nitelikleri, altı çizili elips anahtar niteliği, baklava ilişkiyi temsil eder.

Semboller diyagramın söz dizimidir. Doğru sembol seçimi modelin doğru okunması için zorunludur ve şema dönüşüm adımlarını doğrudan etkiler.

Varlık sembolü nesne sınıfını, ilişki sembolü varlıklar arası bağı, nitelik sembolü özellikleri taşır. Anahtar niteliğin altı çizili gösterilmesi onu ayırt eder.

Öğrenci dikdörtgeni, ÖğrenciNo altı çizili elipsi, KayıtOlur baklavası birlikte kullanıldığında model netleşir.

Sınavda sembol-eşleştirme soruları çok yaygındır. Görsel verildiğinde önce varlıkları (dikdörtgen), sonra anahtarları (altı çizili elips) tespit etmek doğru stratejidir.

---
## Bölüm 37 — ER Diyagramı Sembolleri 2
Çift elips çok değerli nitelik, çift dikdörtgen zayıf varlık kümesi, kesik elips türetilmiş nitelik, çift baklava zayıf ilişkiyi ifade eder. Ayrıca bire-bir, çoktan-bire, çoka-çok ilişki türleri; nicelik limitleri ve rol göstergeleri kullanılır.

Bu semboller ilişki gücünü, bağımlılığı ve kardinaliteyi görsel hale getirir. Rol göstergesi aynı varlığın ilişkide farklı anlamda yer almasını açıklamada kullanılır.

Basit semboller temel yapıyı verirken çift/kesik semboller özel durumları gösterir. Zayıf varlık ve zayıf ilişki sembolleri birlikte okunmalıdır.

Bağımsız anahtarı olmayan bir alt varlık çift dikdörtgenle çizilir ve onu tanımlayan ana varlıkla çift baklava ilişkisi kurulur.

Sınavda kardinalite ve sembol soruları birlikte gelebilir. Bire-bir, çoktan-bire, çoka-çok ayrımını nicelik limitleri ile okumak gerekir.

---
## Bölüm 38 — ER'den İlişkisel Şemaya: Varlık Haritalama
Varlık haritalama, her varlığı ilişkisel modelde tabloya dönüştürme sürecidir. Slaytta algoritma adımları net biçimde verilir.

Adım 1: her varlık için tablo oluşturulur. Adım 2: varlığın öznitelikleri veri türleriyle tablo alanına çevrilir. Adım 3: birincil anahtar belirtilir.

Bu süreç ilişki haritalamadan farklıdır; burada odak varlığın kendi tablosudur. İlişki haritalamada varlıklar arası bağın tablosu ve yabancı anahtarlar öne çıkar.

Öğrenci varlığı için OgrNo, OgrAd, OgrSoyad alanlarıyla tablo kurulup OgrNo birincil anahtar seçilir.

Sınavda adım sıralaması sorulabilir. En kritik sıra: tablo oluştur -> öznitelikleri ekle -> PK belirle.

---
## Bölüm 39 — ER'den İlişkisel Şemaya: İlişki Haritalama
İlişki haritalama, varlıklar arasındaki ilişkinin tabloya dönüştürülmesidir. Slayt bu dönüşümde PK ve FK adımlarını özellikle vurgular.

Adım 1: ilişki için tablo oluşturulur. Adım 2: katılımcı varlıkların birincil anahtarları uygun veri türleriyle tablo alanlarına eklenir. Adım 3: ilişkinin kendi öznitelikleri eklenir. Adım 4: katılımcı PK'ların birleşiminden bir PK belirtilir. Adım 5: yabancı anahtar kısıtlamaları tanımlanır.

Varlık haritalamada tek varlık tablosu kurulurken burada en az iki varlığın bağını temsil eden tablo kurulur. FK zorunluluğu bu bölümün ayırıcı unsurudur.

Depozitor ilişkisinde müşteri-id ve hesap-no alanları hem PK bileşeni hem de ilgili tablolara FK olarak tanımlanabilir.

Sınavda FK adımı unutulursa cevap eksik kalır. İlişki tablosunun PK'si çoğu durumda katılımcı anahtarların birleşimidir.

---
## Bölüm 40 — ER'den İlişkisel Şemaya: Zayıf Varlık Haritalama
Zayıf varlık kümesi, kendi başına birincil anahtara sahip olmayan varlık kümesidir. Haritalamada bu eksiklik tanımlayıcı anahtarla giderilir.

Adım 1: zayıf varlık için tablo oluşturulur. Adım 2: tüm özellikler alan olarak eklenir. Adım 3: varlığı tanımlayan birincil anahtar (genellikle bağlı olduğu güçlü varlığın anahtarıyla birlikte) eklenir. Adım 4: yabancı anahtar kısıtlamaları belirtilir.

Normal varlık doğrudan kendi PK'siyle tanımlanabilir; zayıf varlıkta bağımlı anahtar yapısı gerekir. Bu yüzden güçlü varlıkla ilişki kritik hale gelir.

Bağımlı kayıtların ana varlık olmadan tek başına tanımlanamaması zayıf varlık senaryosudur; tabloya bu bağımlılık FK ile işlenir.

Sınavda zayıf varlık sorularında anahtar eksikliği mutlaka yazılmalıdır. Çözüm adımı olarak 'tanımlayıcı anahtar ekleme + FK tanımı' beklenir.

---
## Bölüm 41 — ER'den İlişkisel Şemaya: Hiyerarşik Varlık Haritalama
ER özelleşme/genelleme hiyerarşik varlık kümeleri biçiminde gelir. Üst düzey ve alt düzey varlıklar için ayrı tablo stratejisi uygulanır.

Adım 1: tüm üst düzey varlıklar için tablolar oluşturulur. Adım 2: alt düzey varlıklar için tablolar oluşturulur. Adım 3: üst düzey PK alt düzey tablolara eklenir. Adım 4: alt düzey öznitelikler eklenir. Adım 5: PK/FK kısıtları belirtilir.

Düz varlık haritalamadan farkı kalıtım benzeri yapı taşımasıdır. IS-A ilişkisi üst-alt düzey bağlantısını kuran temel kavramdır.

Çalışan üst varlığından Mühendis alt varlığı türetildiğinde, Mühendis tablosu Çalışan PK'sini taşıyacak şekilde modellenir.

Sınavda adımları sıralı yazmak önemlidir. Özellikle üst düzey PK'nin alt düzeye eklenmesi noktası çoğunlukla sorulur.

---
## Bölüm 42 — İlişkisel Model Kavramları
İlişkisel model, veri depolama ve işleme için yaygın kullanılan birincil modeldir. Basit yapı sunarken gerekli yetenekleri sağlar.

Veri tablolar halinde tutulur; satırlar tuple, sütunlar özniteliktir. Domain olası sütun değerleri kümesidir. Schema tablo tanımını, instance anlık içeriği ifade eder.

Informal terimler günlük kullanım dilidir (tablo, satır vb.); formal terimler modelin kuramsal dilidir (relation, tuple, domain vb.). İkisi aynı yapının farklı anlatımıdır.

Customer tablosu relation; bir müşteriye ait satır tuple; customer-city sütununun alabileceği şehir değerleri domain yaklaşımıdır.

Sınavda informal-formal eşleştirme çok sorulur. Tablo=Relation, Satır=Tuple, Alan değer kümesi=Domain, Tablo tanımı=Relation Schema eşleştirmesi kritik listedir.

---
## Bölüm 43 — İlişki Özellikleri, Derece ve Nicelik
İlişkinin altı temel özelliği slaytta listelenir: farklı ilişki adı, her hücrede tek değer, her öznitelik adı farklı, yinelenen tuple yok, öznitelik sırası önemsiz, tuple sırası önemsiz.

Derece bir ilişkideki öznitelik sayısıdır. Nicelik (kardinalite/önem) ise ilişkideki tuple sayısıdır. Bu iki ölçü tabloyu farklı açıdan tanımlar.

Derece sütun sayısını, nicelik satır sayısını ifade eder. Karışıklık genelde 'kaç alan' ile 'kaç kayıt' ayrımının yapılmamasından doğar.

5 sütunlu 100 satırlı tabloda derece 5, nicelik 100'dür. Bu örnek sınavda hızlı hesap için güvenilir şablondur.

İlişki özellikleri ezber sorusu olarak gelebilir. En çok unutulan madde 'öznitelik sırası ile tuple sırasının önemsizliği'dir.

---
## Bölüm 44 — İlişkisel Bütünlük Kısıtlamaları
Geçerli ilişkiyi korumak için ilişkisel bütünlük kısıtları gerekir. Slaytta üç ana grup verilir: anahtar, etki alanı ve bilgi tutarlılığı kısıtlamaları.

Anahtar kısıtı: iki tuple anahtar öznitelikte aynı değeri alamaz, anahtar NULL olamaz. Etki alanı kısıtı: öznitelik değerleri gerçek dünya sınırına uyar. Bilgi tutarlılığı kısıtı: yabancı anahtarlar üzerinden ilişkiler arası tutarlılığı korur.

Anahtar kısıtı benzersizliği; etki alanı değer geçerliliğini; bilgi tutarlılığı referans bütünlüğünü hedefler. Üçü birlikte model doğruluğunu oluşturur.

Yaş alanının negatif olamaması etki alanı; müşteri-id'nin benzersiz olması anahtar; hesap kaydının var olmayan müşteriye bağlanmaması bilgi tutarlılığı örneğidir.

Sınavda bu başlık çoğunlukla karşılaştırmalı gelir. Her kısıt türüne bir örnek yazmak cevap kalitesini yükseltir.

---
## Bölüm 45 — Anahtar Türleri Karşılaştırması
Slaytta birincil anahtar, aday anahtar, süper anahtar, yabancı anahtar, bileşik anahtar, benzersiz anahtar (unique) türleri verilir. Unique için NULL değeri alır notu özellikle geçer.

Primary key bir varlığın örneğini tekil tanımlar. Candidate key tekil tanımlayabilecek alternatif güçlü anahtarlardır. Super key aday anahtarın üst kümesidir. Foreign key başka tablonun PK'sine işaret eder. Composite key çoklu öznitelik birleşimiyle anahtar kurar. Unique key benzersizlik için kullanılır ve slaytta NULL alabilir ifadesi vardır.

En kritik farklar: PK seçilen adaydır; candidate alternatif güçlü adaydır; super key daha geniş kümedir; foreign referans verir; composite yapı türüdür; unique benzersizlik sağlar ancak slayt notuna göre NULL alabilir.

Müşteri-id PK olabilir; e-posta candidate/unique adayı olabilir; (ders-kod, ogr-no) birleşimi composite anahtar olabilir; hesap tablosundaki müşteri-id foreign key olabilir.

Sınavda PK-Unique ve Candidate-Super ayrımı en çok karıştırılır. Cevapta hiyerarşi ve NULL farkı mutlaka belirtilmelidir.

| Anahtar Türü | Tanım | NULL Durumu (PDF bağlamı) | Tekrar Durumu | Diğerlerinden Farkı |
| --- | --- | --- | --- | --- |
| Primary Key | Bir varlığın tek örneğini benzersiz tanımlar | Anahtar kısıtına göre NULL olamaz | Tekrarlanamaz | Candidate key'lerden seçilen temel anahtardır |
| Candidate Key | Tuple'ı benzersiz tanımlayabilen aday anahtar | Anahtar mantığı gereği NULL olmamalı | Tekrarlanamaz | Primary seçilmemiş güçlü adaydır |
| Super Key | Tuple'ı benzersiz tanımlayabilen öznitelik kümesi | Alt anahtar mantığına bağlı | Tekrarlanamaz | Candidate key'in üst kümesidir |
| Foreign Key | Başka tablonun PK'sine işaret eder | Referans kurallarına bağlı | Tekrar edebilir | Referans bütünlüğü kurar |
| Composite Key | Birden çok özniteliğin birleşik anahtarı | Bileşen kurallara bağlı | Bileşim tekrar etmez | Yapısal olarak çoklu alanla anahtar olur |
| Unique Key | Benzersizlik için kullanılan anahtar | Slaytta 'NULL değeri alır' ifadesi var | Tekrar etmez | PK'den farklı olarak slaytta NULL notu verilmiştir |

---
## Bölüm 46 — Anahtar Türleri Hiyerarşisi
Slayta göre super key, candidate key'in üst kümesidir; primary key ise candidate key'lerden seçilen bir anahtardır.

Önce bir tuple'ı tekil belirleyen super key kümesi düşünülür. Minimal olanlar candidate key olur. Candidate key'lerden biri primary key olarak seçilir.

Bu nedenle kapsama ilişkisi Super Key ⊇ Candidate Key ve Candidate Key -> seçilen Primary Key biçimindedir. Yabancı anahtar bu hiyerarşiye dahil olmak yerine referans bütünlüğü için dış ilişki kurar.

Öğrenci tablosunda {OgrNo, OgrAd} super key olabilir; minimal {OgrNo} candidate olur; seçilen primary key de {OgrNo} olur.

Sınavda küme ilişkisi çizdirmek yaygındır. Super-candidate-primary ilişkisini açıkça yazmak ve unique/foreign ile karıştırmamak gerekir.

---
## Bölüm 47 — DDL Nedir ve Komutları
DDL (Veri Tanımlama Dili), veritabanı yapısını/şemasını tanımlar. Slayttaki CREATE TABLE örneği account-number ve balance alanlarıyla verilir.

DDL derleyici, veri sözlüğünde depolanan tabloları oluşturur; veri sözlüğü meta verileri tutar. Slaytta CREATE, ALTER, DROP, TRUNCATE komutları DDL kapsamında listelenir.

DDL veri tanımına odaklıdır; DML veri manipülasyonuna odaklıdır. DDL komutları şema düzeyinde çalışırken DML kayıt düzeyinde çalışır.

create table account (account-number char(10), balance integer) ifadesi şema kurulumuna örnektir. ALTER mevcut yapıyı değiştirir, DROP yapıyı kaldırır, TRUNCATE slaytta DDL komutu olarak listelenmiştir.

Sınavda komutların ne zaman kullanıldığı sorulur. Cevabı şema yaşam döngüsü olarak vermek gerekir: CREATE kur, ALTER değiştir, DROP kaldır, TRUNCATE temizle (slayt bağlamı).

| Komut | Amaç | Şema/Veri Etkisi | Slayttaki Konum |
| --- | --- | --- | --- |
| CREATE | Yeni veritabanı nesnesi/tablo oluşturma | Şema oluşturur | DDL komutları arasında listelenir; CREATE TABLE örneği verilir |
| ALTER | Mevcut yapıda değişiklik | Şema günceller | DDL komutları arasında listelenir |
| DROP | Nesneyi kaldırma | Şemadan kaldırır | DDL komutları arasında listelenir |
| TRUNCATE | Slaytta DDL komutu olarak listelenir | Temizleme/boşaltma amaçlı kullanılır (detay verilmemiş) | DDL komutları arasında listelenir |

---
## Bölüm 48 — DML Nedir ve Komutları
DML (Veri İşleme Dili), uygun veri modeliyle düzenlenen veriye erişme ve veriyi değiştirme dilidir. Sorgu dili olarak da anılır.

Slaytta DML altında INSERT, UPDATE, DELETE komutları verilir. Ayrıca dil iki sınıfa ayrılır: prosedürel (hangi veri + nasıl alınacak) ve nonprocedural (hangi veri).

DML kayıtlarla çalışır; DDL yapı ile çalışır. SQL en yaygın nonprocedural sorgu dili olarak DML bağlamında vurgulanır.

INSERT yeni kayıt ekler, UPDATE mevcut kaydı değiştirir, DELETE kaydı siler. SQL ile bu işlemler tablo verisi üzerinde uygulanır.

Sınavda DDL-DML farkı temel sorudur. Cevapta 'şema vs veri' ayrımı ve prosedürel/nonprocedural tanımı birlikte yazılmalıdır.

| Karşılaştırma | DDL | DML |
| --- | --- | --- |
| Temel Amaç | Veritabanı yapısını/şemasını tanımlamak | Veriye erişmek ve veriyi değiştirmek |
| Tipik Komutlar | CREATE, ALTER, DROP, TRUNCATE | INSERT, UPDATE, DELETE |
| Çalışma Düzeyi | Şema ve metadata | Kayıt/ilişki içeriği |
| PDF Vurgusu | Veri sözlüğü ve meta veri bağlantısı | Sorgu dili, prosedürel vs nonprocedural ayrımı |

---
## Bölüm 49 — SQL
SQL, slayta göre yaygın kullanılan nonprocedural dildir. Örneklerde SELECT-FROM-WHERE yapısı müşteri ve hesap tabloları üzerinden gösterilir.

İlk örnekte müşteri-id'ye göre müşteri adı seçilir. İkinci örnekte depositor ve account tabloları koşullu birleştirilerek hesap bakiyeleri bulunur.

SQL, ilişkisel cebirdeki işlemlerin pratik sorgu dilindeki karşılığıdır. ODBC/JDBC ise SQL'in uygulama programından veritabanına gönderilmesini sağlayan arayüzdür; dilin kendisi değildir.

select account.balance from depositor, account where depositor.customer-id='192-83-7465' and depositor.account-number=account.account-number sorgusu iki tabloyu ilişkilendirir.

Sınavda SELECT-FROM-WHERE bloğunda koşul ifadesini doğru kurmak kritik puandır. Ayrıca ODBC/JDBC'nin bağlantı arayüzü olduğu vurgulanmalıdır.

---
## Bölüm 50 — İlişkisel Cebir Nedir
İlişkisel cebir işlemlerin tasarımında kullanılır ve SQL'in kavramsal temelini oluşturur. DB'deki gerçek ilişkiyi değiştirmeden ilişkiler üzerinde operatör uygular.

Prosedürel bir ara dil olarak tanımlanır. Sorgular operatörlerle adım adım kurulur; sonuçlar da ilişki olduğu için işlemler zincirlenebilir.

Nonprocedural SQL 'ne istendiğini' vurgularken ilişkisel cebir 'nasıl üretileceğini' operatörlerle açıklar. Bu yüzden optimizer ile ilişkisi güçlüdür.

Sorgu iyileştirici, cebirsel ifade alternatiflerinden en verimli olanı değerlendirir. Bu avantaj slaytta ayrıca belirtilir.

Sınavda ilişkisel cebir için 'tekli/ikili operatör', 'ara sonuçların ilişki olması' ve 'SQL'in kavramsal temeli' ifadeleri beklenir.

---
## Bölüm 51 — Select Operatörü (σ)
Select (σ), bir ilişkiden satır alt kümesi seçer. Gösterimi slaytta σ p(r) olarak verilir.

Burada σ seçme işlemini, r ilişki adını, p önerme mantığı/koşulu temsil eder. Örnek olarak σsubject='database'(Books) ve koşul birleşimli biçimi verilmiştir.

Select satır seçer; Project sütun seçer. SQL karşılığı genellikle WHERE koşuludur.

σA=C(r) gösterimi, A özniteliğinin C koşulunu sağladığı r satırlarını filtreler. Koşul arttıkça çıkan satır sayısı azalır.

Sınavda sembol anlamı sorulabilir. 'σ = filtreleme/koşul seçimi' ve 'SQL WHERE karşılığı' birlikte yazılmalıdır.

---
## Bölüm 52 — Project Operatörü (π)
Project (π), belirli koşulu karşılayan/istenen sütunları yansıtır. Gösterim π A1, A2, ... , An(r) biçimindedir.

A1..An seçilecek öznitelik adlarıdır. İlişki küme kabul edildiğinden yinelenen satırlar otomatik kaldırılır.

Select satırları süzerken Project sütunları seçer. SQL'de SELECT listesi Project'e karşılık gelir.

π konu, yazar(Kitaplar) ifadesi Kitaplar ilişkisinden yalnız konu ve yazar sütunlarını döndürür; tekrar eden demetler elenir.

Sınavda en çok unutulan nokta yinelenen satırların otomatik kaldırılmasıdır. Bu özellik mutlaka belirtilmelidir.

---
## Bölüm 53 — Union Operatörü (∪)
Union, iki ilişki arasında birleşim işlemi yapar: r ∪ s = { t | t ∈ r or t ∈ s }.

Geçerli birleşim için r ve s aynı sayıda özniteliğe sahip olmalı ve öznitelik alanları uyumlu olmalıdır. Yinelenen demetler otomatik kaldırılır.

Union ortak yapılı iki sonucu birleştirir; set difference birinden diğerini çıkarır. Union sonuç kümesi kapsamı genişletir.

π author(Books) ∪ π author(Articles) ifadesi kitap veya makale ya da her ikisini yazan yazar adlarını üretir.

Sınavda union koşulları sık gelir. Öznitelik sayısı ve domain uyumu yazılmadan cevap eksik kalır.

---
## Bölüm 54 — Set Difference Operatörü (−)
Set difference, bir ilişkide olup diğerinde olmayan tuple'ları döndürür. Gösterim r - s biçimindedir.

İşlem soldaki kümeyi temel alır ve sağdakilerle ortak olanları eler. Sonuç, sadece solda kalan tuple'lardır.

Union iki kümeyi toplarken set difference ayırır. Bu nedenle sonuç kümesi genellikle daha dardır.

π author(Books) − π author(Articles) ifadesi kitap yazmış ama makale yazmamış yazarları verir.

Sınavda yön önemlidir: r-s ile s-r farklı sonuç üretir. Bu ayrımı belirtmek puan kazandırır.

---
## Bölüm 55 — Cartesian Product Operatörü (×)
Kartezyen çarpımı (×), iki ilişkinin bilgisini tek yerde birleştirir. Gösterim r × s olup tüm kombinasyonları üretir.

Formal tanım r × s = {qt | q ∈ r ve t ∈ s} biçimindedir. Sonuç çoğu zaman büyük olduğu için select koşuluyla birlikte filtrelenir.

Join benzeri sonuçlara temel oluşturur ama tek başına koşulsuz kombinasyon üretir. Select ile beraber kullanıldığında anlamlı eşleşmeler çıkar.

σauthor='abc'(Books × Articles) ifadesi önce kartesyen çarpım üretir, sonra koşulla ilgili satırları seçer.

Sınavda 'neden select ile birlikte?' sorusuna kartesyen çarpımın tüm kombinasyonları ürettiği ve filtreleme gerektirdiği cevabı verilir.

---
## Bölüm 56 — Rename Operatörü (ρ) ve Operatörlerin Birlikte Kullanımı
Rename (ρ), adlandırması olmayan cebirsel sonuç ilişkisine isim vermek için kullanılır. Gösterim ρ x(E) biçimindedir.

E ifadesinin sonucu x adıyla kaydedilir. Operatörler zincirlenerek önce çarpım, sonra seçim, sonra projeksiyon gibi adımlar oluşturulabilir.

Rename veri içeriğini değiştirmez; sadece ifade okunabilirliğini ve sonraki adımlarda referansı kolaylaştırır. Select/Project/Union gibi operatörler ise sonuç kümesini değiştirir.

Operatör birlikte kullanımında σA=C(r × s) biçiminde filtre uygulanıp sonuç ρ t(...) ile adlandırılabilir. Slaytta operatörlerin birlikte kullanımı ayrıca örnek başlığıyla verilmiştir.

Sınavda rename çoğu zaman küçük detay sanılıp atlanır. Oysa cebir ifadelerinde ara sonucun yeniden kullanımı için kritik adımdır.

---
## Bölüm 57 — Genel Özet ve Sınavda Dikkat Edilecekler
Ünite 1; DBMS ihtiyacını dosya sistemi sorunlarından hareketle kurar, mimari seviyelerle soyutlamayı açıklar, veri bağımsızlığıyla değişim yönetimini temellendirir, ER ve ilişkisel modelle tasarım/uygulama bağını kurar.

Dil ve işlem tarafında DDL-DML-SQL-ilişkisel cebir zinciri; kullanıcı/yönetim tarafında kullanıcı türleri-DBA-işlem/depolama yönetimi zinciri sunulur. Bu yapı sınav sorularının çoğunu karşılayan ana iskelettir.

Karışan çiftler genellikle aynı başlığın farklı katmanlarıdır: DDL-DML, mantıksal-fiziksel bağımsızlık, primary-unique, 2-tier-3-tier, external-conceptual, entity-entity set, schema-instance.

Örnek bütünleşik akış: ER ile tasarla -> ilişkisel şemaya dönüştür -> DDL ile oluştur -> DML/SQL ile işle -> eşzamanlılık ve bütünlük kısıtlarıyla tutarlılığı koru.

Sınav stratejisi olarak her kavramı 'tanım + ne işe yarar + neyle karışır + bir örnek' formatında yazmak yüksek doğruluk sağlar.

| Karışan Kavram Çifti | Net Ayrım | Sınav İpucu |
| --- | --- | --- |
| DDL vs DML | DDL yapı, DML veri işlem dili | Komut türünden ayır: CREATE mi INSERT mi? |
| Mantıksal vs Fiziksel Bağımsızlık | Mantıksal model değişimi vs depolama değişimi | 'HDD->SSD' görürsen fiziksel düşün |
| Primary Key vs Unique Key | PK temel seçilen anahtar; unique benzersizlik sağlar, slaytta NULL alabilir notu var | NULL ifadesini özellikle yaz |
| 2-Tier vs 3-Tier | Doğrudan istemci-DB vs arada middle katman | 'Büyük web uygulaması' -> 3-tier |
| External vs Conceptual | Kullanıcı görünümü vs tüm mantıksal yapı | 'Kullanıcı neyi görür?' sorusuna external |
| Entity vs Entity Set | Tek varlık vs benzer varlık kümesi | Tekil/çoğul mantığıyla ayır |
| Schema vs Instance | Yapı tanımı vs anlık içerik | Tür-değişken değeri benzetmesini kullan |

---
# ÇIKTI 2 — PODCAST / AUDIO SCRIPT
Aşağıdaki diyalog, yalnızca PDF içeriğindeki başlık ve tanımlara dayanır.
---
## Bölüm 1: Veritabanı ve DBMS
- **Öğretici:** Veritabanı düzenli bilgiler topluluğu olarak tanımlanıyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** DBMS ise bu veriye erişim için program seti sağlıyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Dosya sistemi yaklaşımında sorunlar birikince DBMS ihtiyacı doğuyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** DBMS kolay ve verimli bir ortam sunuyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** MySQL, MSSQL Server, Oracle örnekleri doğrudan slaytta var.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Kısacası DB veri; DBMS veriyi yöneten sistem.

---
## Bölüm 2: Dosya Sistem Sorunları ve Çözümler
- **Öğretici:** Veri tekrarı ve tutarsızlık ilk kırılma noktası.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Erişim zorluğu nedeniyle her yeni görev için yeni program yazmak gerekiyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Veri izolasyonu, çok dosya ve çok formatla birleşince raporlama zorlaşıyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Bütünlük kurallarının kod içine gömülmesi bakım maliyeti üretiyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Atomiklik ihlalinde para transferi gibi işlemler yarım kalabiliyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Kontrolsüz eşzamanlılık ve güvenlik sorunları DBMS ile yönetiliyor.

---
## Bölüm 3: DBMS Bileşenleri ve Yapı Taşları
- **Öğretici:** Bileşenler: kullanıcı, yazılım, donanım, veri.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Veri numeric, non-numeric ve logical biçimde tutulabiliyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Yapı taşları kolon, satır/tuple ve tablo.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Avantajlar veri bağımsızlığı, verimli erişim, bütünlük ve güvenlik.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Eşzamanlı erişim ve uygulama süresinin kısalması da vurgulanıyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Bunlar dosya sistemine göre önemli iyileştirmeler.

---
## Bölüm 4: 3 Seviyeli Mimari
- **Öğretici:** External seviye kullanıcıya görünen parçayı tanımlar.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Conceptual seviye tüm veri, ilişki ve kısıtları taşır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Internal seviye fiziksel depolama detayını yönetir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kullanıcı dış seviyede tablo ayrıntısını bilmek zorunda değildir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Internal seviyede alan tahsisi, sıkıştırma ve şifreleme yer alır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Bu ayrım güvenlik ve bakım açısından kritik.

---
## Bölüm 5: 1-tier, 2-tier, 3-tier
- **Öğretici:** 1-tier doğrudan veritabanı erişimi sağlar.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** 2-tier istemci-sunucu yapıdır; ODBC/JDBC kullanılır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** 3-tier'da arada middle katman vardır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** 2-tier daha doğrudan ve hızlı iletişim sunar.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** 3-tier büyük web uygulamalarında tercih edilir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Katman sayısı arttıkça ayrışma ve yönetim artar.

---
## Bölüm 6: Mantıksal ve Fiziksel Veri Bağımsızlığı
- **Öğretici:** Mantıksal bağımsızlıkta şema düzeyi değişim uygulamayı kırmamalı.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Fiziksel bağımsızlıkta depolama değişimi mantığı etkilememeli.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Slaytta HDD'den SSD'ye geçiş doğrudan örnekleniyor.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Mantıksal değişim örnekleri: öznitelik/varlık/ilişki ekleme-değiştirme-silme.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Fiziksel değişim örnekleri: dosya düzeni, erişim yöntemi, dizin, konum.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Sınavda en çok karışan fark çiftlerinden biri bu.

---
## Bölüm 7: Kullanıcı Türleri ve DBA
- **Öğretici:** Yerel kullanıcı uygulamayı kullanır, DBMS ayrıntısını bilmez.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Uygulama programcısı DML sorgularını C/C++/Java gibi dillerde yazar.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Gelişmiş kullanıcı SQL ile doğrudan çalışır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Uzman kullanıcı özel veritabanı programları geliştirir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Online kullanıcı doğrudan çevrimiçi etkileşim kurar.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: DBA ise yetkilendirme, şema, performans ve koordinasyon sorumluluğunu taşır.

---
## Bölüm 8: İşlem ve Depolama Yönetimi
- **Öğretici:** İşlem tek mantıksal işlevi gerçekleştiren işlem koleksiyonudur.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** İşlem yönetimi arıza durumlarında tutarlılığı korur.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Eşzamanlılık kontrol yöneticisi işlemler arası etkileşimi düzenler.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Depolama yöneticisi alt düzey veri ile sorgu/uygulama arasında arayüzdür.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Dosya yöneticisiyle etkileşir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Verimli depolama-alma-güncelleme bu katmanın görevidir.

---
## Bölüm 9: Veri Modelleri
- **Öğretici:** Veri modeli veri, ilişki, anlambilim ve kısıtları açıklayan araç koleksiyonudur.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** ER ve ilişkisel model ana eksen olarak verilir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Object-oriented ve semi-structured modeller diğer seçeneklerdir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Network ve hierarchical modeller eski modeller olarak geçer.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Model seçimi tasarım yaklaşımını belirler.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: ER'den ilişkisel şemaya dönüşüm bu bağın örneğidir.

---
## Bölüm 10: ER Modeli ve Öznitelikler
- **Öğretici:** ER modeli kavramsal görünümü tanımlar.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Entity canlı/cansız gerçek dünya nesnesidir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Entity set benzer varlıkların koleksiyonudur.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Öznitelik türleri: basit, bileşik, türetilmiş, tek değerli, çok değerli.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Domain kavramı özniteliğin alabileceği değer aralığını belirtir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: ER diyagram sembolleri sınavda ezber değil anlamla öğrenilmelidir.

---
## Bölüm 11: ER Sembolleri ve İlişkiler
- **Öğretici:** Dikdörtgen varlık, elips nitelik, altı çizili elips anahtar nitelik.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Baklava ilişkiyi gösterir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Çift elips çok değerli nitelik, çift dikdörtgen zayıf varlık kümesi.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kesik elips türetilmiş nitelik, çift baklava zayıf ilişki.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Bire-bir, çoktan-bire, çoka-çok ilişki türleri birlikte düşünülmeli.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Nicelik limitleri ve rol göstergeleri ilişki okumasını netleştirir.

---
## Bölüm 12: ER'den İlişkisel Şemaya Haritalama
- **Öğretici:** Varlık haritalamada her varlık için tablo kurulur.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Öznitelikler veri türleriyle alanlara dönüşür.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Birincil anahtar tanımlanır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** İlişki haritalamada katılımcı PK'lar tabloya eklenir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Yabancı anahtar kısıtları belirtilir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Zayıf ve hiyerarşik varlıklar için özel adımlar uygulanır.

---
## Bölüm 13: İlişkisel Model Kavramları
- **Öğretici:** Tablo relation, satır tuple, sütun öznitelik karşılığıdır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Domain olası sütun değer kümesidir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Schema tablo tanımı, instance anlık içeriktir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** İlişki derecesi sütun sayısıdır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** İlişki niceliği tuple sayısıdır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: İlişkinin altı temel özelliği sıralı olarak bilinmelidir.

---
## Bölüm 14: Anahtar Türleri
- **Öğretici:** Primary key tekil tanımlayıcıdır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Candidate key birincil olabilecek güçlü adaydır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Super key candidate key'in üst kümesidir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Foreign key başka tablonun PK'sine işaret eder.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Composite key çoklu öznitelik birleşimidir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Unique key için slaytta NULL alır notu özellikle geçer.

---
## Bölüm 15: Bütünlük Kısıtları
- **Öğretici:** Anahtar kısıtı benzersizlik ve NULL olmama şartı taşır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Etki alanı kısıtı gerçek dünya değer sınırlarını uygular.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Bilgi tutarlılığı kısıtı yabancı anahtar bağlantısıyla çalışır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Bu üçlü birlikte veri doğruluğunu korur.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Sınavda her birine örnek vermek önemlidir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Anahtar kısıtlarına varlık kısıtları da denir ifadesi slaytta vardır.

---
## Bölüm 16: DDL ve DML
- **Öğretici:** DDL şema tanımlar; DML veriyi işler.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** DDL: CREATE, ALTER, DROP, TRUNCATE.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** DML: INSERT, UPDATE, DELETE.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** DDL veri sözlüğü ve metadata ile ilişkilidir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** DML prosedürel/nonprocedural ayrımıyla açıklanır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Sınavda bu fark en kritik karşılaştırmadır.

---
## Bölüm 17: SQL ve Arayüzler
- **Öğretici:** SQL nonprocedural sorgu dili olarak verilir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** SELECT-FROM-WHERE örnekleri müşteri ve hesap tabloları üzerinden anlatılır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** İki tablo örneğinde koşullu eşleştirme yapılır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Gömülü SQL dil uzantılarıyla kullanılabilir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** ODBC/JDBC uygulama programı arayüzleri olarak geçer.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Yani SQL dil, ODBC/JDBC bağlantı köprüsüdür.

---
## Bölüm 18: İlişkisel Cebir Operatörleri
- **Öğretici:** İlişkisel cebir SQL'in kavramsal temelidir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Select satır alt kümesi; Project sütun yansıtmasıdır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Union için öznitelik sayısı ve domain uyumu gerekir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Set difference solda olup sağda olmayan tuple'ları verir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Cartesian product tüm kombinasyonları üretir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Rename ara sonuçları adlandırarak operatör zincirini okunur kılar.

---
## Bölüm 19: Kapanış Özeti
- **Öğretici:** DBMS dosya sisteminin tekrar, bütünlük, atomiklik ve eşzamanlılık sorunlarına çözüm sunar.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Mimari katmanlar soyutlama ve güvenlik sağlar.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Veri bağımsızlığı sistemin değişime dayanıklılığını artırır.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** ER ve ilişkisel model tasarım ve uygulama köprüsünü kurar.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** DDL-DML-SQL-ilişkisel cebir zinciri sınavın teknik çekirdeğidir.
- **Öğrenen:** Bunu sınavda nasıl ayırt edeceğimizi bir cümleyle söyler misin?
- **Öğretici:** Kısa kural: Karşılaştırmalı kavramları çiftler halinde çalışmak başarıyı yükseltir.

---
# ÇIKTI 3 — TEST SORULARI
Sorular yalnızca PDF'deki konulardan derlenmiştir. Her sorunun altında cevap ve açıklama verilmiştir.
---
## Çoktan Seçmeli Sorular
### Soru 1
DBMS aşağıdakilerden hangisini ifade eder?
- A) Birbiriyle ilişkili verileri yöneten sistem
- B) Sadece fiziksel disk donanımı
- C) Yalnızca rapor ekranı
- D) Sadece ağ protokolü
**Doğru Cevap:** A
**Açıklama:** PDF'de DBMS, veriye erişim için program seti sunan ve veritabanını yöneten sistem olarak tanımlanır. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 2
Aşağıdakilerden hangisi dosya sisteminin sakıncalarından biri değildir?
- A) Veri tekrarı
- B) Veri izolasyonu
- C) Kontrollü eşzamanlılık
- D) Bütünlük sorunu
**Doğru Cevap:** C
**Açıklama:** Kontrollü eşzamanlılık dosya sisteminin sorunu değil, DBMS'in çözüm tarafında ele aldığı bir yetenektir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 3
Atomiklik için doğru ifade hangisidir?
- A) İşlem kısmen tamamlanabilir
- B) İşlem ya tamamen olur ya hiç olmaz
- C) İşlem sadece tek kullanıcıyla çalışır
- D) İşlem sadece read-only'dir
**Doğru Cevap:** B
**Açıklama:** Slaytta para transferi örneğiyle işlem bütünlüğünün 'tamamı veya hiçbiri' olduğu vurgulanır. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 4
External seviye için en doğru ifade hangisidir?
- A) Fiziksel depolamayı tanımlar
- B) Kullanıcıya ilgili veri görünümünü sunar
- C) Sadece DBA tarafından görülebilir
- D) Sadece güvenlik kayıtlarını tutar
**Doğru Cevap:** B
**Açıklama:** External level kullanıcının ilgili kısmı görmesini sağlar; şema ayrıntılarını bilmek gerekmez. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 5
Internal seviye aşağıdakilerden hangisini içerir?
- A) Kullanıcı görünüm filtreleri
- B) Fiziksel depolama ve alan tahsisi
- C) Sadece SQL komut listesi
- D) Yalnızca iş raporu şablonları
**Doğru Cevap:** B
**Açıklama:** Internal level fiziksel depolama, alan tahsisi, sıkıştırma ve şifreleme tekniklerini içerir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 6
2-tier mimaride istemci ile sunucu iletişiminde hangileri örnek API'dir?
- A) ODBC ve JDBC
- B) DDL ve DML
- C) ER ve SQL
- D) PK ve FK
**Doğru Cevap:** A
**Açıklama:** Slaytta 2-tier iletişimi için ODBC/JDBC açıkça verilmiştir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 7
3-tier mimarinin tipik kullanım alanı nedir?
- A) Basit tek kullanıcılı dosya listesi
- B) Büyük web uygulamaları
- C) Sadece lokal test scripti
- D) Sadece yedekleme aracı
**Doğru Cevap:** B
**Açıklama:** PDF'de 3-tier mimarinin büyük web uygulamalarında kullanıldığı belirtilir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 8
Mantıksal veri bağımsızlığı örneği hangisidir?
- A) HDD yerine SSD kullanma
- B) Yeni öznitelik ekleme
- C) Disk bölümü büyütme
- D) Veri merkezini taşıma
**Doğru Cevap:** B
**Açıklama:** Yeni öznitelik/varlık/ilişki ekleme mantıksal bağımsızlık kapsamına girer. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 9
Fiziksel veri bağımsızlığı örneği hangisidir?
- A) Tabloya yeni sütun eklemek
- B) İlişki türünü değiştirmek
- C) Dosya düzenleme tekniğini değiştirmek
- D) Yeni varlık eklemek
**Doğru Cevap:** C
**Açıklama:** Dosya düzeni, erişim yöntemi, depolama cihazı değişimi fiziksel bağımsızlık örnekleridir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 10
Schema ve instance için doğru eşleşme hangisidir?
- A) Schema anlık veri, instance kalıcı tanım
- B) Schema mantıksal yapı, instance anlık içerik
- C) İkisi tamamen aynıdır
- D) Schema sadece fiziksel disk adıdır
**Doğru Cevap:** B
**Açıklama:** Slaytta tür-değişken benzetmesiyle schema yapı, instance değer/gerçek içerik olarak verilir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 11
ER modelinde entity set neyi ifade eder?
- A) Tek bir varlığı
- B) Benzer varlıkların koleksiyonunu
- C) Yalnızca anahtar alanı
- D) Yalnızca ilişki çizgisini
**Doğru Cevap:** B
**Açıklama:** Entity set benzer türde varlıkların koleksiyonudur. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 12
Aşağıdakilerden hangisi basit özniteliktir?
- A) Ad+Soyad
- B) Telefon numarası (atomik kabul edilen)
- C) Doğum tarihi üzerinden türetilen yaş
- D) Birden fazla telefon listesi
**Doğru Cevap:** B
**Açıklama:** Slaytta basit öznitelik için atomik değer örneği olarak telefon numarası kullanılır. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 13
Çift elips ER diyagramında neyi gösterir?
- A) Anahtar nitelik
- B) Çok değerli nitelik
- C) Zayıf ilişki
- D) Varlık kümesi
**Doğru Cevap:** B
**Açıklama:** ER sembollerinde çift elips çok değerli niteliği temsil eder. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 14
İlişki haritalamada hangi adım zorunludur?
- A) Katılımcı PK'ların tabloya eklenmesi
- B) Sadece tablo adını yazmak
- C) Yalnızca view oluşturmak
- D) Tüm FK'ları kaldırmak
**Doğru Cevap:** A
**Açıklama:** İlişki haritalamada katılımcı varlıkların PK'ları alan olarak eklenir ve FK kısıtları tanımlanır. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 15
İlişki derecesi neyi ifade eder?
- A) Tuple sayısını
- B) Öznitelik sayısını
- C) Tablo sayısını
- D) Veritabanı kullanıcı sayısını
**Doğru Cevap:** B
**Açıklama:** İlişki derecesi bir ilişkideki öznitelik (sütun) sayısıdır. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 16
Anahtar kısıtlaması için doğru ifade hangisidir?
- A) Anahtar öznitelik NULL olabilir
- B) İki tuple anahtar değeri aynı olabilir
- C) Anahtar değeri tekrarlanamaz ve NULL olamaz
- D) Yalnızca FK için geçerlidir
**Doğru Cevap:** C
**Açıklama:** Anahtar kısıtlarında benzersizlik ve NULL olmama şartı slaytta açıkça verilir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 17
Super key ile candidate key ilişkisi hangisidir?
- A) Candidate key super key'in üst kümesidir
- B) Super key candidate key'in üst kümesidir
- C) İkisi ilişkisizdir
- D) Super key yalnızca FK'dır
**Doğru Cevap:** B
**Açıklama:** Slayta göre super key, candidate key'in üst kümesidir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 18
DDL kapsamında yer alan komut seti hangisidir?
- A) INSERT-UPDATE-DELETE
- B) CREATE-ALTER-DROP-TRUNCATE
- C) SELECT-FROM-WHERE
- D) UNION-PROJECT-SELECT
**Doğru Cevap:** B
**Açıklama:** DDL komutları slaytta CREATE, ALTER, DROP, TRUNCATE olarak listelenmiştir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 19
DML komutları içinde hangisi yer alır?
- A) CREATE
- B) DROP
- C) UPDATE
- D) ALTER
**Doğru Cevap:** C
**Açıklama:** DML altında INSERT, UPDATE, DELETE komutları verilir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 20
Project (π) operatörünün temel işlevi nedir?
- A) Satır filtrelemek
- B) Sütun yansıtmak
- C) İki ilişkiyi fark almak
- D) İlişki adını değiştirmek
**Doğru Cevap:** B
**Açıklama:** Project operatörü belirli öznitelikleri seçer ve yinelenen satırları otomatik kaldırır. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 21
Union işleminin geçerli olma koşulu hangisidir?
- A) Her iki ilişkide tuple sayısı eşit olmalı
- B) Aynı öznitelik sayısı ve uyumlu domain
- C) PK isimleri aynı olmalı
- D) Her iki tabloda da FK bulunmalı
**Doğru Cevap:** B
**Açıklama:** Union için öznitelik sayısı eşitliği ve domain uyumluluğu şartı PDF'de açıkça belirtilir. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

### Soru 22
Rename (ρ) operatörü ne sağlar?
- A) Fiziksel depolamayı değiştirir
- B) Sonuç ilişkisine isim verir
- C) Anahtar kısıtı ekler
- D) Tabloyu siler
**Doğru Cevap:** B
**Açıklama:** Rename, adlandırılmamış sonuç ilişkisinin yeniden adlandırılmasını sağlar. Bu ayrım sınavda benzer kavramlarla kıyaslanarak sorulabilir; cevapta tanım + neden birlikte verilmelidir.

---
## Doğru / Yanlış Soruları
### Soru 1
DBMS yalnızca veri depolar, erişim program seti sunmaz.
**Cevap:** Yanlış
**Açıklama:** DBMS tanımında veriye erişim için program seti sunduğu açıkça belirtilir. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

### Soru 2
Dosya sisteminde veri izolasyonu, farklı dosya ve formatlardan kaynaklanabilir.
**Cevap:** Doğru
**Açıklama:** Slaytta veri izolasyonu birden çok dosya ve format bağlamında açıklanır. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

### Soru 3
External seviyede kullanıcı veritabanı şema ayrıntılarını bilmek zorundadır.
**Cevap:** Yanlış
**Açıklama:** External seviyenin amacı ayrıntıyı gizlemek ve kullanıcıya ilgili görünümü vermektir. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

### Soru 4
Internal seviye mimarinin en düşük seviyesidir.
**Cevap:** Doğru
**Açıklama:** İç seviye fiziksel depolama seviyesidir ve en düşük seviye olarak verilir. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

### Soru 5
2-tier mimaride istemci sunucuya dolaylı bağlanır, doğrudan bağlanamaz.
**Cevap:** Yanlış
**Açıklama:** 2-tier modelde istemci sunucu veritabanına doğrudan iletişim kurar. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

### Soru 6
3-tier mimaride middle katman kullanıcı ile DB arasında arabulucudur.
**Cevap:** Doğru
**Açıklama:** Application(Middle) katmanının arabulucu rolü açıkça belirtilir. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

### Soru 7
Mantıksal veri bağımsızlığında HDD yerine SSD geçişi örnek olarak verilir.
**Cevap:** Yanlış
**Açıklama:** Bu örnek fiziksel veri bağımsızlığı kapsamındadır. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

### Soru 8
Schema, veritabanının mantıksal yapısını ifade eder.
**Cevap:** Doğru
**Açıklama:** Slaytta schema doğrudan mantıksal yapı olarak tanımlanır. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

### Soru 9
Entity set, tek bir varlığı ifade eder.
**Cevap:** Yanlış
**Açıklama:** Entity set benzer varlıkların koleksiyonudur. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

### Soru 10
Project operatörü yinelenen satırları küme mantığı nedeniyle kaldırabilir.
**Cevap:** Doğru
**Açıklama:** PDF'de project için yinelenen satırların otomatik kaldırıldığı belirtilir. Benzer soru tiplerinde kavramın hangi katmanda/başlıkta geçtiğini belirtmek yanlışı azaltır.

---
## Boşluk Doldurma Soruları
### Soru 1
Veri tanımlama dili kısaltması ______ şeklindedir.
**Cevap:** DDL
**Açıklama:** DDL, şema tanımlamak için kullanılır ve veri sözlüğü/meta data ile ilişkilidir. Bu tip sorularda kısaltma açılımı ile kullanım bağlamını birlikte hatırlamak gerekir.

### Soru 2
Veri işleme dili kısaltması ______ şeklindedir.
**Cevap:** DML
**Açıklama:** DML veri üzerinde INSERT, UPDATE, DELETE gibi işlemleri kapsar. Bu tip sorularda kısaltma açılımı ile kullanım bağlamını birlikte hatırlamak gerekir.

### Soru 3
DBMS ile istemci bağlantısı için örnek API'ler ______ ve ______ olarak verilir.
**Cevap:** ODBC, JDBC
**Açıklama:** 2-tier mimari slaytında bu iki arayüz doğrudan belirtilmiştir. Bu tip sorularda kısaltma açılımı ile kullanım bağlamını birlikte hatırlamak gerekir.

### Soru 4
Kavramsal seviyede ______, ______ ve ______ bilgileri tutulur.
**Cevap:** varlıklar, ilişkiler, kısıtlamalar
**Açıklama:** Conceptual level verinin mantıksal bütününü taşır. Bu tip sorularda kısaltma açılımı ile kullanım bağlamını birlikte hatırlamak gerekir.

### Soru 5
Bir ilişkideki öznitelik sayısına ilişki ______ denir.
**Cevap:** derecesi
**Açıklama:** Derece sütun sayısını ifade eder; nicelik ise tuple sayısıdır. Bu tip sorularda kısaltma açılımı ile kullanım bağlamını birlikte hatırlamak gerekir.

### Soru 6
Bir ilişkide olup diğerinde olmayan tuple'ları döndüren operatör ______ operatörüdür.
**Cevap:** Set Difference (−)
**Açıklama:** r-s gösterimiyle belirtilir ve fark kümesini üretir. Bu tip sorularda kısaltma açılımı ile kullanım bağlamını birlikte hatırlamak gerekir.

### Soru 7
İlişkisel cebirde sonuç ilişkisinin adını değiştiren operatör ______ operatörüdür.
**Cevap:** Rename (ρ)
**Açıklama:** ρ x(E) gösterimiyle ifade edilir. Bu tip sorularda kısaltma açılımı ile kullanım bağlamını birlikte hatırlamak gerekir.

### Soru 8
DBA'nın açılımı ______ olup yetkilendirme dahil sistem koordinasyonundan sorumludur.
**Cevap:** Database Administrator
**Açıklama:** Slaytta DBA tüm ayrıcalıklara sahip yönetici rolüyle tanımlanır. Bu tip sorularda kısaltma açılımı ile kullanım bağlamını birlikte hatırlamak gerekir.

---
## Kısa Cevaplı Sorular
### Soru 1
DDL ile DML arasındaki temel farkı PDF bağlamında açıklayınız.
**Örnek Cevap:** DDL veritabanı yapısını (şema) tanımlar; DML veriye erişir ve veriyi değiştirir. DDL'de CREATE/ALTER/DROP/TRUNCATE, DML'de INSERT/UPDATE/DELETE komutları verilir. Sınavda bu farkı 'yapı vs içerik' ekseninde belirtmek gerekir.
**Açıklama:** Kısa cevap sorularında sadece tanım değil, karşılaştırma ve örnek boyutunu eklemek değerlendirme kalitesini yükseltir.

### Soru 2
Mantıksal ve fiziksel veri bağımsızlığını örnekle karşılaştırınız.
**Örnek Cevap:** Mantıksal bağımsızlıkta tablo/öznitelik/ilişki gibi şema düzeyi değişiklikler uygulamayı kırmamalıdır. Fiziksel bağımsızlıkta HDD->SSD, dosya düzeni, dizin ve erişim yöntemi değişse bile mantıksal şema etkilenmez. Karşılaştırma yapılırken değişen katman açıkça yazılmalıdır.
**Açıklama:** Kısa cevap sorularında sadece tanım değil, karşılaştırma ve örnek boyutunu eklemek değerlendirme kalitesini yükseltir.

### Soru 3
Primary key, candidate key ve super key hiyerarşisini açıklayınız.
**Örnek Cevap:** Super key tuple'ı benzersiz tanımlayan öznitelik kümesidir ve candidate key'in üst kümesidir. Candidate key minimal güçlü aday anahtarlardır. Primary key, candidate key'lerden seçilen temel anahtardır.
**Açıklama:** Kısa cevap sorularında sadece tanım değil, karşılaştırma ve örnek boyutunu eklemek değerlendirme kalitesini yükseltir.

### Soru 4
External ve Conceptual seviye arasındaki farkı yazınız.
**Örnek Cevap:** External seviye kullanıcıya ilgili görünümü sunar ve şema ayrıntılarını gizler. Conceptual seviye tüm verinin mantıksal yapısını, varlıkları, ilişkileri, kısıtları, güvenlik ve bütünlük bilgisini taşır. Biri kullanıcı görünümü, diğeri sistemin mantıksal çekirdeğidir.
**Açıklama:** Kısa cevap sorularında sadece tanım değil, karşılaştırma ve örnek boyutunu eklemek değerlendirme kalitesini yükseltir.

### Soru 5
Select ve Project operatörlerinin farkını örnekle açıklayınız.
**Örnek Cevap:** Select (σ) satır alt kümesi seçer; Project (π) sütun alt kümesi yansıtır. Örneğin σA=C(r) satırları filtrelerken πA,B(r) sütunları seçer. Project'te küme mantığı nedeniyle yinelenen satırlar kaldırılabilir.
**Açıklama:** Kısa cevap sorularında sadece tanım değil, karşılaştırma ve örnek boyutunu eklemek değerlendirme kalitesini yükseltir.

---
# ÇIKTI 4 — BİLGİ KARTLARI (FLASHCARD)
Kartlar PDF'deki kavramları sınav tekrarına uygun, kısa ama açıklamalı arka yüzlerle derler.
---
## Kart 1
**ÖN YÜZ:** DBMS
**ARKA YÜZ:** Veritabanı Yönetim Sistemi'dir. Birbiriyle ilişkili verileri depolar, yönetir ve veriye erişim için program seti sunar. Slaytta MySQL, MSSQL Server, Oracle örnekleriyle verilir.
---
## Kart 2
**ÖN YÜZ:** DDL
**ARKA YÜZ:** Veri Tanımlama Dili'dir. Veritabanı yapısını/şemasını tanımlamak için kullanılır. CREATE, ALTER, DROP, TRUNCATE komutları bu başlıkta listelenir.
---
## Kart 3
**ÖN YÜZ:** DML
**ARKA YÜZ:** Veri İşleme Dili'dir. Veriye erişme ve veriyi değiştirme işlemlerini kapsar. INSERT, UPDATE, DELETE komutları DML altında verilir.
---
## Kart 4
**ÖN YÜZ:** SQL
**ARKA YÜZ:** Yaygın kullanılan nonprocedural sorgu dilidir. SELECT-FROM-WHERE yapısıyla veri talebi belirtilir, nasıl alınacağı sistem tarafından planlanır.
---
## Kart 5
**ÖN YÜZ:** ER
**ARKA YÜZ:** Entity-Relationship modelidir. Veritabanının kavramsal görünümünü varlıklar ve ilişkiler üzerinden tasarlamak için kullanılır.
---
## Kart 6
**ÖN YÜZ:** ODBC
**ARKA YÜZ:** Uygulama programlarının veritabanına sorgu göndermesi için kullanılan arayüz örneklerinden biridir. 2-tier mimaride istemci-sunucu bağlantısında geçer.
---
## Kart 7
**ÖN YÜZ:** JDBC
**ARKA YÜZ:** ODBC gibi uygulama-veritabanı bağlantısını sağlayan arayüz örneğidir. Slaytta ODBC ile birlikte anılır.
---
## Kart 8
**ÖN YÜZ:** DBA
**ARKA YÜZ:** Database Administrator'dır. Şema tanımı, yetkilendirme, performans izleme, bütünlük kısıtları gibi sistemin kritik yönetim görevlerini üstlenir.
---
## Kart 9
**ÖN YÜZ:** DB
**ARKA YÜZ:** Veritabanının kendisini ifade eder. DBMS ise bu veriyi yöneten yazılımsal sistemdir; ikisi aynı kavram değildir.
---
## Kart 10
**ÖN YÜZ:** Veri Tekrarı ve Tutarsızlığı
**ARKA YÜZ:** Dosya sistemlerinde aynı bilginin farklı dosyalarda tutulmasıyla oluşur. Güncelleme her kopyaya yansımadığında tutarsızlık üretilir; DBMS merkezi yönetimle bu riski azaltır.
---
## Kart 11
**ÖN YÜZ:** Atomiklik
**ARKA YÜZ:** Bir işlemin ya tamamen tamamlanması ya da hiç uygulanmamasıdır. Para transferi örneğinde yarım güncelleme tutarsızlık yaratacağı için atomiklik kritiktir.
---
## Kart 12
**ÖN YÜZ:** External Seviye
**ARKA YÜZ:** Kullanıcıya ilgili veri görünümünü sunar. Kullanıcının şema ve fiziksel depolama ayrıntılarını bilmesi gerekmez.
---
## Kart 13
**ÖN YÜZ:** Conceptual Seviye
**ARKA YÜZ:** Veritabanında depolanan tüm veriyi, ilişkileri, kısıtları ve bütünlük-güvenlik bilgisini mantıksal düzeyde tanımlar.
---
## Kart 14
**ÖN YÜZ:** Internal Seviye
**ARKA YÜZ:** Fiziksel depolama düzeyidir. Alan tahsisi, sıkıştırma ve şifreleme gibi konular bu seviyede ele alınır.
---
## Kart 15
**ÖN YÜZ:** Mantıksal Veri Bağımsızlığı
**ARKA YÜZ:** Şema düzeyindeki değişikliklerin uygulamaları yeniden yazmadan yapılabilmesidir. Yeni öznitelik/varlık/ilişki ekleme bunun örneğidir.
---
## Kart 16
**ÖN YÜZ:** Fiziksel Veri Bağımsızlığı
**ARKA YÜZ:** Depolama tekniği değişikliklerinin mantıksal şemayı etkilememesidir. HDD->SSD geçişi slaytta doğrudan örneklenir.
---
## Kart 17
**ÖN YÜZ:** Schema
**ARKA YÜZ:** Veritabanının mantıksal yapısını tanımlar. Programlamadaki tür (type) kavramına benzetilir.
---
## Kart 18
**ÖN YÜZ:** Instance
**ARKA YÜZ:** Veritabanının belirli bir andaki gerçek içeriğidir. Programlamadaki değişkenin değeri benzetmesiyle açıklanır.
---
## Kart 19
**ÖN YÜZ:** Entity
**ARKA YÜZ:** Kolay tanımlanabilen gerçek dünya nesnesidir; canlı veya cansız olabilir. Öğrenci, öğretmen, ders gibi örnekler verilir.
---
## Kart 20
**ÖN YÜZ:** Entity Set
**ARKA YÜZ:** Benzer türde varlıkların koleksiyonudur. Örneğin Öğrenci kümesi bir okulun tüm öğrencilerini içerebilir.
---
## Kart 21
**ÖN YÜZ:** Basit Öznitelik
**ARKA YÜZ:** Atomik ve bölünemeyen özniteliktir. Slaytta telefon numarası örneğiyle açıklanır.
---
## Kart 22
**ÖN YÜZ:** Bileşik Öznitelik
**ARKA YÜZ:** Birden fazla basit öznitelikten oluşan yapıdır. Ad+soyad bileşimi klasik örnektir.
---
## Kart 23
**ÖN YÜZ:** Türetilmiş Öznitelik
**ARKA YÜZ:** Fiziksel DB'de tutulmayan, başka özniteliklerden hesaplanan alandır. Depolama tekrarını azaltma yaklaşımıyla ilişkilidir.
---
## Kart 24
**ÖN YÜZ:** Tek Değerli Öznitelik
**ARKA YÜZ:** Her varlık için tek değer alır. Kardinalite tekli yapıdadır.
---
## Kart 25
**ÖN YÜZ:** Çok Değerli Öznitelik
**ARKA YÜZ:** Bir varlık için birden fazla değer alabilir. ER diyagramında çift elipsle gösterilir.
---
## Kart 26
**ÖN YÜZ:** Varlık Haritalama
**ARKA YÜZ:** Her varlık için tablo oluşturma, öznitelikleri alanlara dönüştürme ve birincil anahtar belirleme sürecidir.
---
## Kart 27
**ÖN YÜZ:** İlişki Haritalama
**ARKA YÜZ:** İlişki için ayrı tablo kurulur, katılımcı PK'lar eklenir, gerekirse ilişkinin öznitelikleri eklenir, PK/FK kısıtları tanımlanır.
---
## Kart 28
**ÖN YÜZ:** Zayıf Varlık Haritalama
**ARKA YÜZ:** Kendi PK'si olmayan varlık için tablo oluşturulup tanımlayıcı anahtar ve FK kısıtları eklenir.
---
## Kart 29
**ÖN YÜZ:** Hiyerarşik Haritalama
**ARKA YÜZ:** Üst ve alt düzey varlıklar için ayrı tablolar açılır; üst düzey PK alt düzeye taşınır ve PK/FK ilişkisi kurulur.
---
## Kart 30
**ÖN YÜZ:** İlişki Derecesi
**ARKA YÜZ:** Bir ilişkideki öznitelik sayısıdır (sütun sayısı). Nicelikten farklıdır.
---
## Kart 31
**ÖN YÜZ:** İlişki Niceliği
**ARKA YÜZ:** Bir ilişkideki tuple sayısıdır (satır sayısı). Derece ile karıştırılmamalıdır.
---
## Kart 32
**ÖN YÜZ:** Anahtar Kısıtlaması
**ARKA YÜZ:** Aynı anahtar değeri iki tuple'da tekrar edemez ve anahtar NULL olamaz. Varlık kısıtı olarak da anılır.
---
## Kart 33
**ÖN YÜZ:** Etki Alanı Kısıtlaması
**ARKA YÜZ:** Özniteliklerin alabileceği değer aralığını gerçek dünya kurallarına göre sınırlar. Örn. yaş negatif olamaz.
---
## Kart 34
**ÖN YÜZ:** Bilgi Tutarlılığı Kısıtı
**ARKA YÜZ:** Yabancı anahtar üzerinden ilişkiler arası tutarlılığı korur. Referans bütünlüğünün temelidir.
---
## Kart 35
**ÖN YÜZ:** Primary Key
**ARKA YÜZ:** Bir varlık örneğini benzersiz tanımlayan seçilmiş temel anahtardır. Candidate key'ler arasından seçilir.
---
## Kart 36
**ÖN YÜZ:** Candidate Key
**ARKA YÜZ:** Tuple'ı benzersiz tanımlayabilen aday anahtar(lar)dır. Primary seçilmese bile güçlü anahtar niteliği taşır.
---
## Kart 37
**ÖN YÜZ:** Super Key
**ARKA YÜZ:** Tuple'ı benzersiz tanımlayabilen öznitelik kümesidir. Candidate key'in üst kümesi olarak geçer.
---
## Kart 38
**ÖN YÜZ:** Foreign Key
**ARKA YÜZ:** Başka tablonun primary key'ine işaret eden sütun(lar)dır. Bilgi tutarlılığı kısıtında merkez rol oynar.
---
## Kart 39
**ÖN YÜZ:** Composite Key
**ARKA YÜZ:** Birden fazla özniteliğin birleşimiyle oluşan anahtardır. Tek alanla benzersizlik sağlanamadığında kullanılır.
---
## Kart 40
**ÖN YÜZ:** Unique Key
**ARKA YÜZ:** Benzersizlik sağlayan anahtardır; slayt notunda NULL değeri alabileceği belirtilir. PK ile bu noktada ayrılır.
---
## Kart 41
**ÖN YÜZ:** Select (σ)
**ARKA YÜZ:** Satır alt kümesi seçer. Gösterimi σ p(r) ve SQL'deki WHERE mantığıyla eşleştirilir.
---
## Kart 42
**ÖN YÜZ:** Project (π)
**ARKA YÜZ:** Sütun yansıtması yapar. Gösterimi π A1, A2, ... (r) ve yinelenen satırları küme mantığıyla kaldırabilir.
---
## Kart 43
**ÖN YÜZ:** Union (∪)
**ARKA YÜZ:** İki ilişkideki uygun tuple'ları birleştirir. Geçerlilik için öznitelik sayısı eşitliği ve domain uyumu gerekir.
---
## Kart 44
**ÖN YÜZ:** Set Difference (−)
**ARKA YÜZ:** r-s ifadesi, r'de olup s'de olmayan tuple'ları döndürür.
---
## Kart 45
**ÖN YÜZ:** Cartesian Product (×)
**ARKA YÜZ:** İki ilişkinin tüm kombinasyonlarını üretir. Pratikte seçme koşuluyla birlikte kullanılır.
---
## Kart 46
**ÖN YÜZ:** Rename (ρ)
**ARKA YÜZ:** İlişkisel cebirde adlandırılmamış sonucu yeniden isimlendirmeyi sağlar: ρ x(E).
---
## Kart 47
**ÖN YÜZ:** DDL vs DML
**ARKA YÜZ:** DDL şemayı tanımlar; DML veriyi işler. Sınavda bu ayrımın komut örnekleriyle birlikte yazılması beklenir.
---
## Kart 48
**ÖN YÜZ:** External vs Conceptual
**ARKA YÜZ:** External kullanıcı görünümüdür; conceptual tüm mantıksal modeldir. Kullanıcı neyi görür sorusunda ayrım netleşir.
---
## Kart 49
**ÖN YÜZ:** 2-tier vs 3-tier
**ARKA YÜZ:** 2-tier doğrudan istemci-DB iletişimidir; 3-tier'da arada middle katman vardır ve büyük web uygulamalarında tercih edilir.
---
## Kart 50
**ÖN YÜZ:** Schema vs Instance
**ARKA YÜZ:** Schema yapı tanımıdır; instance anlık içeriktir. Tür-değer benzetmesiyle hatırlanır.
---
# ÇIKTI 5 — İNFOGRAFİK AÇIKLAMASI
Aşağıdaki metin, tek sayfalık bir infografik yerleşimini metinsel olarak tarif eder. Tüm içerik PDF'deki Ünite 1 başlıklarından türetilmiştir.
---
## 1) Renk ve Kategori Sistemi
- **Mavi Alan:** Temel tanımlar (DB, DBMS, kısaltmalar)
- **Turuncu Alan:** Sorunlar ve çözümler (dosya sistemi vs DBMS)
- **Yeşil Alan:** Mimari ve veri bağımsızlığı
- **Kırmızı Alan:** Tasarım ve modelleme (ER, ilişkisel model, anahtarlar)
- **Gri Alan:** Diller ve işlemler (DDL, DML, SQL, ilişkisel cebir)
Her alanın altında kısa açıklama kutuları ve oklarla ilişki yönü gösterilir.
---
## 2) Tüm Kısaltmalar ve Açılımları
| Kısaltma | Açılım | İnfografikte Konumu | Kısa Not |
| --- | --- | --- | --- |
| DB | Database | Sol üst | Verinin kendisi |
| DBMS | Database Management System | Sol üst-merkez | Veriyi yöneten sistem |
| DDL | Data Definition Language | Alt orta | Şema tanımı |
| DML | Data Manipulation Language | Alt orta | Veri işlemleri |
| SQL | Structured Query Language | Alt orta | Yaygın nonprocedural sorgu dili |
| ER | Entity-Relationship | Sağ orta | Kavramsal tasarım modeli |
| ODBC | Open Database Connectivity (slaytta kısaltma olarak geçer) | Mimari alanı | Uygulama arayüzü |
| JDBC | Java Database Connectivity (slaytta kısaltma olarak geçer) | Mimari alanı | Uygulama arayüzü |
| DBA | Database Administrator | Üst sağ | Yönetim ve yetkilendirme rolü |
---
## 3) DBMS ve Kullanım Alanları
Bankacılık, havayolu, üniversite, satış, imalat ve insan kaynakları için altı sütunlu mini kartlar kullanılır. Her kartta 'tutulan veri' satırı vardır: örn. bankacılıkta işlemler, üniversitede kayıt/not, satışta müşteri-ürün-satın alma. Kutuların altında tek bir ortak mesaj kutusu yer alır: **'Veritabanları hayatın her alanına dokunur.'**
---
## 4) Dosya Sistemi Sorunları -> DBMS Çözümleri
| Sorun | Etki | DBMS Çözümü |
| --- | --- | --- |
| Veri tekrarı/tutarsızlık | Aynı verinin farklı dosyalarda farklılaşması | Merkezileştirilmiş veri yönetimi |
| Erişim zorluğu | Her yeni iş için yeni program gereksinimi | Standart sorgu ve yönetim katmanı |
| Veri izolasyonu | Çok dosya/çok format nedeniyle birleşik görünüm eksikliği | İlişkisel yapı ve bütünleşik erişim |
| Bütünlük sorunu | Kısıtların kod içinde dağılması | Merkezi kısıt/kural yönetimi |
| Atomiklik sorunu | Kısmi güncelleme ile tutarsızlık | İşlem yönetimi (ya hep ya hiç) |
| Eşzamanlılık/güvenlik | Çakışma ve yetkisiz erişim riski | Eşzamanlılık kontrolü + yetkilendirme |
Bu bölümde her satırdan sağa doğru ok çizilerek 'sorun -> çözüm' akışı görselleştirilir.
---
## 5) 3 Seviyeli Mimari ve Soyutlama
| Seviye | Ne Bilir? | Ne Bilmez? | Güvenlik/İşlev Notu |
| --- | --- | --- | --- |
| External | Kullanıcıya gereken görünüm verisi | Fiziksel depolama ayrıntısı, tam şema detayları | Yetkiye göre görünüm üretir |
| Conceptual | Tüm varlık-ilişki-kısıt-güvenlik yapısı | Fiziksel bit düzeyi depolama | Kurumsal mantıksal model çekirdeği |
| Internal | Fiziksel depolama, alan tahsisi, sıkıştırma/şifreleme | Kullanıcı görünüm ayrıntıları | En düşük seviye depolama kontrolü |
External -> Conceptual -> Internal yönünde aşağı akış oku; ters yönde veri dönüş oku gösterilir.
---
## 6) 1-tier / 2-tier / 3-tier Karşılaştırması
| Karşılaştırma | 2-Tier | 3-Tier |
| --- | --- | --- |
| Bağlantı Yapısı | İstemci doğrudan DB sunucusuna bağlanır. | İstemci, uygulama katmanı üzerinden DB'ye ulaşır. |
| Ara Katman | Yok | Var (Application/Middle) |
| İletişim | Doğrudan ve hızlı | Dolaylı ama yönetilebilir/ölçeklenebilir |
| Kullanım Senaryosu | Daha basit istemci-sunucu uygulamaları | Büyük web uygulamaları |
| Güvenlik ve Ayrışma | Daha sınırlı | Katman ayrımı nedeniyle daha güçlü yönetim |
Ek not kutusu: 1-tier doğrudan erişim nedeniyle son kullanıcı için sınırlı kullanım kolaylığı sunar; daha çok programcının yerel geliştirme/sınama senaryosunda görülür.
---
## 7) Mantıksal vs Fiziksel Veri Bağımsızlığı
| Özellik | Mantıksal Veri Bağımsızlığı | Fiziksel Veri Bağımsızlığı |
| --- | --- | --- |
| Değişen Katman | Mantıksal şema/ilişki düzeni | Depolama düzeni ve fiziksel altyapı |
| Uygulamaya Etki | Uygulama yeniden yazılmadan değişim hedeflenir | Mantıksal şemayı etkilemeden değişim hedeflenir |
| Örnek | Yeni öznitelik ekleme, varlık/ilişki değiştirme | HDD->SSD, dosya düzeni/dizin/erişim yöntemi değişikliği |
| Amaç | İş kuralı ve model evrimi | Performans/altyapı evrimi |
| Slayttaki Vurgu | Ekleme-değiştirme-silme, kayıt birleştirme/bölme | C'den D'ye taşıma, depolama cihazı değiştirme |
İnfografikte çift kutu tasarımı önerilir: solda mantıksal değişim örnekleri, sağda fiziksel değişim örnekleri. İki kutunun ortasında 'uygulama etkisini azalt' hedef rozeti yer alır.
---
## 8) Kullanıcı Türleri ve DBA
| Rol | Kısa Tanım | Örnek |
| --- | --- | --- |
| Yerel Kullanıcı | Uygulamayı kullanır, DBMS ayrıntısını bilmeyebilir | ATM, bilet, kütüphane sistemi |
| Uygulama Programcısı | DML sorgularını uygulama dili içinde yazar | C/C++/Java ile rapor geliştirme |
| Gelişmiş Kullanıcı | SQL ile doğrudan DB etkileşimi | Doğrudan sorgu yazan geliştirici |
| Uzman Kullanıcı | Özel/kapsamlı DB uygulaması geliştirir | İhtiyaca özel sistem modülü |
| Online Kullanıcı | Çevrimiçi doğrudan etkileşim kurar | Web/mobil panel işlemleri |
| DBA | Şema, yetki, performans, bütünlük yönetimi | Kurumsal DB yöneticisi |
---
## 9) ER Sembolleri ve Öznitelik Türleri
| Sembol/Kavram | Anlam |
| --- | --- |
| Dikdörtgen | Varlık kümesi |
| Elips | Nitelik |
| Altı çizili elips | Anahtar nitelik |
| Baklava | İlişki |
| Çift elips | Çok değerli nitelik |
| Çift dikdörtgen | Zayıf varlık kümesi |
| Kesik elips | Türetilmiş nitelik |
| Çift baklava | Zayıf ilişki |
Öznitelik türleri için yan kutu: basit, bileşik, türetilmiş, tek değerli, çok değerli. Her biri için bir satırlık sınav ayırt notu eklenir.
---
## 10) Anahtar Türleri
| Anahtar Türü | Tanım | NULL Durumu (PDF bağlamı) | Tekrar Durumu | Diğerlerinden Farkı |
| --- | --- | --- | --- | --- |
| Primary Key | Bir varlığın tek örneğini benzersiz tanımlar | Anahtar kısıtına göre NULL olamaz | Tekrarlanamaz | Candidate key'lerden seçilen temel anahtardır |
| Candidate Key | Tuple'ı benzersiz tanımlayabilen aday anahtar | Anahtar mantığı gereği NULL olmamalı | Tekrarlanamaz | Primary seçilmemiş güçlü adaydır |
| Super Key | Tuple'ı benzersiz tanımlayabilen öznitelik kümesi | Alt anahtar mantığına bağlı | Tekrarlanamaz | Candidate key'in üst kümesidir |
| Foreign Key | Başka tablonun PK'sine işaret eder | Referans kurallarına bağlı | Tekrar edebilir | Referans bütünlüğü kurar |
| Composite Key | Birden çok özniteliğin birleşik anahtarı | Bileşen kurallara bağlı | Bileşim tekrar etmez | Yapısal olarak çoklu alanla anahtar olur |
| Unique Key | Benzersizlik için kullanılan anahtar | Slaytta 'NULL değeri alır' ifadesi var | Tekrar etmez | PK'den farklı olarak slaytta NULL notu verilmiştir |
Anahtar hiyerarşisi oku: `Super Key ⊇ Candidate Key -> Primary Key seçimi`. Ayrı bir yan notta `Foreign Key`'in referans bütünlüğü rolü belirtilir.
---
## 11) DDL vs DML
| Karşılaştırma | DDL | DML |
| --- | --- | --- |
| Temel Amaç | Veritabanı yapısını/şemasını tanımlamak | Veriye erişmek ve veriyi değiştirmek |
| Tipik Komutlar | CREATE, ALTER, DROP, TRUNCATE | INSERT, UPDATE, DELETE |
| Çalışma Düzeyi | Şema ve metadata | Kayıt/ilişki içeriği |
| PDF Vurgusu | Veri sözlüğü ve meta veri bağlantısı | Sorgu dili, prosedürel vs nonprocedural ayrımı |
Alt şerit: SQL nonprocedural dil olarak vurgulanır; ODBC/JDBC bağlantı arayüzleri olarak ikonlarla gösterilir.
---
## 12) İlişkisel Cebir Operatörleri
| Operatör | Gösterim | Temel İşlev |
| --- | --- | --- |
| Select | σ p(r) | Satır filtreleme |
| Project | π A1, A2, ... (r) | Sütun yansıtma |
| Union | r ∪ s | Uyumlu iki ilişkinin birleşimi |
| Set Difference | r - s | Birinde olup diğerinde olmayanlar |
| Cartesian Product | r × s | Tüm kombinasyonlar |
| Rename | ρ x(E) | Sonuç ilişkiyi adlandırma |
Not kutusu: Operatör zinciri örneği `σA=C(r × s)` ardından `ρ t(...)` ile adlandırma yapılabilir.
---
## 13) İlişkisel Model Kavramları
| Informal | Formal |
| --- | --- |
| Tablo | Relation |
| Kolon başlık/alan | Attribute |
| Olası sütun değerleri | Domain |
| Satır | Tuple |
| Tablo tanımı | Relation Schema |
Ek not: İlişki özelliklerinin 6 maddesi ayrı bir kontrol listesi olarak yerleştirilir.
---
## 14) ER -> İlişkisel Şema Haritalama
| Haritalama Türü | Adımların Özeti |
| --- | --- |
| Varlık Haritalama | Her varlık için tablo, öznitelikleri alanlara dönüştürme, PK belirleme |
| İlişki Haritalama | İlişki tablosu, katılımcı PK'ları ekleme, ilişki öznitelikleri, birleşik PK, FK kısıtları |
| Zayıf Varlık Haritalama | Zayıf varlık tablosu, özellikler, tanımlayıcı anahtar, FK kısıtları |
| Hiyerarşik Haritalama | Üst/alt tablo kurulumu, üst PK'nin alt seviyeye eklenmesi, PK/FK tanımları |
Ok akışı önerisi: `ER Diyagramı -> Haritalama Adımları -> İlişkisel Şema`.
---
## 15) Sınavda Kritik Karşılaştırmalar
| Karışan Kavram Çifti | Net Ayrım | Sınav İpucu |
| --- | --- | --- |
| DDL vs DML | DDL yapı, DML veri işlem dili | Komut türünden ayır: CREATE mi INSERT mi? |
| Mantıksal vs Fiziksel Bağımsızlık | Mantıksal model değişimi vs depolama değişimi | 'HDD->SSD' görürsen fiziksel düşün |
| Primary Key vs Unique Key | PK temel seçilen anahtar; unique benzersizlik sağlar, slaytta NULL alabilir notu var | NULL ifadesini özellikle yaz |
| 2-Tier vs 3-Tier | Doğrudan istemci-DB vs arada middle katman | 'Büyük web uygulaması' -> 3-tier |
| External vs Conceptual | Kullanıcı görünümü vs tüm mantıksal yapı | 'Kullanıcı neyi görür?' sorusuna external |
| Entity vs Entity Set | Tek varlık vs benzer varlık kümesi | Tekil/çoğul mantığıyla ayır |
| Schema vs Instance | Yapı tanımı vs anlık içerik | Tür-değişken değeri benzetmesini kullan |
Bu blok infografiğin en altına 'hızlı tekrar' paneli olarak yerleştirilir.
---
