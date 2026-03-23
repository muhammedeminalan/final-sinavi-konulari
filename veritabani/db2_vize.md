# Veritabanı Sistemleri — Bölümlü Özet

---

## 1) Tüm Kısaltmalar ve Açılımları

| Kısaltma | Açılım | Kısa Açıklama |
| --- | --- | --- |
| **DB** | Database | Verilerin düzenli ve ilişkili şekilde saklandığı veritabanı yapısıdır. |
| **DBMS** | Database Management System | Veritabanını yönetmek, sorgulamak, güncellemek ve güvenli erişim sağlamak için kullanılan sistemdir. |
| **DDL** | Data Definition Language | Veritabanı şemasını/yapısını tanımlamak için kullanılan komutlar bütünüdür. |
| **DML** | Data Manipulation Language | Veriye erişmek ve veriyi değiştirmek için kullanılan komutlar bütünüdür. |
| **SQL** | Structured Query Language | Yaygın kullanılan sorgu dilidir; veriyi tanımlama ve işleme işlemlerinde kullanılır. |
| **ER** | Entity-Relationship | Varlık-ilişki modeli; veritabanı tasarımının kavramsal aşamasında kullanılır. |
| **ODBC** | Open Database Connectivity | Uygulamaların veritabanına bağlanması için kullanılan arayüz standartlarından biridir. |
| **JDBC** | Java Database Connectivity | Java tabanlı uygulamaların veritabanına bağlanmasında kullanılan arayüzdür. |
| **DBA** | Database Administrator | Veritabanı yöneticisi; yetkilendirme, performans, bütünlük ve bakım sorumluluğunu taşır. |

---

## 2) DBMS Nedir ve Kullanım Alanları

DBMS, birbiriyle ilişkili verileri düzenli biçimde saklayan ve bu veriler üzerinde erişim, güncelleme, güvenlik ve yönetim işlemlerini sağlayan sistem yazılımıdır. Verilerin kolay ve verimli şekilde işlenmesi için standart bir ortam sunar.

DBMS kullanımı özellikle çok kullanıcılı, sürekli güncellenen ve tutarlılık gerektiren sistemlerde kritik hale gelir. Dosya temelli dağınık yapılara göre daha güçlü bir kontrol mekanizması sağlar.

**Yaygın kullanım alanları:**
- **Bankacılık:** hesaplar, transferler, işlem kayıtları
- **Havayolları:** rezervasyon ve planlama sistemleri
- **Üniversiteler:** öğrenci kayıtları, dersler, not bilgileri
- **Satış:** müşteri, ürün, satın alma verileri
- **İmalat:** üretim, envanter, sipariş, tedarik zinciri
- **İnsan Kaynakları:** çalışan, maaş, vergi ve özlük kayıtları

---

## 3) Dosya Sistemlerinin Sorunları ve DBMS Çözümleri

| Dosya Sistemi Sorunu | Ne Problem Oluşturur? | DBMS Çözümü |
| --- | --- | --- |
| Veri tekrarı ve tutarsızlık | Aynı verinin farklı dosyalarda farklı değer alması | Merkezi veri yönetimi ve tek kaynaktan güncelleme |
| Erişim zorluğu | Her yeni rapor/iş için yeni program yazma ihtiyacı | Standart sorgulama dili ve ortak erişim katmanı |
| Veri izolasyonu | Farklı dosya formatlarından birleşik veri üretilememesi | İlişkisel yapı ile bütünleşik sorgulama |
| Bütünlük sorunları | Kısıtların dağınık kodlarda tutulması | Kısıtları merkezi tanımlama ve denetleme |
| Atomiklik sorunu | Kısmi güncelleme ile tutarsız durum | İşlem yönetimi (ya hep ya hiç) |
| Eşzamanlılık sorunu | Aynı anda güncellemede çakışma | Eşzamanlılık kontrolü |
| Güvenlik sorunu | Yetkisiz erişim riski | Yetkilendirme ve erişim kontrolü |

---

## 4) 3 Seviyeli Mimari (External, Conceptual, Internal) Katmanları ve Özellikleri

| Katman | Odak | Özellik |
| --- | --- | --- |
| **External (Dış / View)** | Kullanıcı görünümü | Kullanıcı sadece kendine gerekli veriyi görür, şema/fiziksel ayrıntıyı bilmez. |
| **Conceptual (Kavramsal / Logical)** | Tüm mantıksal yapı | Varlıklar, ilişkiler, kısıtlar, bütünlük ve güvenlik kuralları burada tanımlanır. |
| **Internal (İç / Physical)** | Fiziksel depolama | Verinin diskte nasıl tutulduğu, alan tahsisi, erişim düzeni, sıkıştırma/şifreleme gibi konular bulunur. |

Bu ayrımın temel amacı, kullanıcı görünümü ile fiziksel depolamayı birbirinden izole ederek sistemi daha yönetilebilir hale getirmektir.

---

## 5) 1-tier, 2-tier, 3-tier Mimari Karşılaştırması

| Özellik | 1-tier | 2-tier | 3-tier |
| --- | --- | --- | --- |
| Bağlantı yapısı | Kullanıcı/veri doğrudan aynı katmanda | İstemci doğrudan DB sunucusuna bağlanır | İstemci, uygulama katmanı üzerinden DB'ye erişir |
| Ara katman | Yok | Yok | Var (Application/Middle) |
| Kullanım tipi | Yerel/geliştirici odaklı senaryolar | Temel istemci-sunucu uygulamaları | Büyük ölçekli web/kurumsal uygulamalar |
| Avantaj | Basit ve hızlı doğrudan erişim | Doğrudan ve hızlı iletişim | Güvenlik, ölçeklenebilirlik, bakım kolaylığı |
| Dezavantaj | Son kullanıcı için sınırlı uygunluk | İş mantığı istemciye dağılabilir | Kurulum/katman yönetimi daha karmaşık |

---

## 6) Mantıksal ve Fiziksel Veri Bağımsızlığı Karşılaştırması

| Kriter | Mantıksal Veri Bağımsızlığı | Fiziksel Veri Bağımsızlığı |
| --- | --- | --- |
| Değişen kısım | Mantıksal şema (öznitelik/varlık/ilişki) | Fiziksel depolama altyapısı |
| Amaç | Uygulamaları kırmadan modeli geliştirmek | Mantıksal yapıyı etkilemeden altyapıyı değiştirmek |
| Örnek | Yeni sütun ekleme, ilişki yapısı güncelleme | HDD -> SSD, dizin/erişim yöntemi değişimi |
| Etki | Uygulama katmanına etkisi daha yüksek olabilir | Uygulamaya etkisi minimum olmalıdır |

---

## 7) Kullanıcı Türleri ve DBA Görevleri

### Kullanıcı Türleri

| Tür | Açıklama |
| --- | --- |
| **Yerel Kullanıcı** | Hazır uygulama üzerinden işlem yapar; DBMS detayını bilmesi gerekmez (ATM, rezervasyon vb.). |
| **Uygulama Programcısı** | DML sorgularını C/C++/Java gibi dillerde uygulamaya gömer. |
| **Gelişmiş Kullanıcı** | SQL ile veritabanına doğrudan sorgu gönderir. |
| **Uzman Kullanıcı** | Özel/karmaşık veritabanı uygulamaları geliştirir. |
| **Online Kullanıcı** | Çevrimiçi sistemler üzerinden doğrudan işlem yapar. |

### DBA Görevleri

- Şema tanımı yapmak
- Depolama yapısı ve erişim yöntemlerini belirlemek
- Şema/fiziksel organizasyon değişikliklerini yönetmek
- Kullanıcılara yetki vermek veya kaldırmak
- Bütünlük kısıtlarını belirlemek
- Kullanıcılarla teknik iletişimi yürütmek
- Performansı izlemek ve ihtiyaç değişimlerine yanıt vermek

---

## 8) ER Diyagramı Sembolleri ve Anlamları

| Sembol | Anlam |
| --- | --- |
| Dikdörtgen | Varlık kümesi (Entity Set) |
| Elips | Öznitelik (Attribute) |
| Altı çizili elips | Anahtar öznitelik |
| Baklava | İlişki (Relationship) |
| Çift elips | Çok değerli öznitelik |
| Kesik elips | Türetilmiş öznitelik |
| Çift dikdörtgen | Zayıf varlık kümesi |
| Çift baklava | Zayıf ilişki |

İlişki tipleri ayrıca **bire-bir**, **bire-çok / çoktan-bire**, **çoka-çok** biçiminde gösterilir.

---

## 9) Öznitelik Türleri Karşılaştırması

| Tür | Tanım | Örnek |
| --- | --- | --- |
| **Basit** | Atomik, daha fazla parçalanamayan öznitelik | Telefon numarası (tek alan) |
| **Bileşik** | Alt parçalara ayrılabilen öznitelik | Ad + Soyad |
| **Türetilmiş** | Değeri diğer alanlardan hesaplanan öznitelik | Doğum tarihinden yaş |
| **Tek değerli** | Her varlık için tek değer alır | T.C./öğrenci numarası |
| **Çok değerli** | Bir varlık için birden fazla değer alır | Birden fazla telefon |

---

## 10) Anahtar Türleri Karşılaştırması (Primary, Candidate, Super, Foreign, Composite, Unique)

| Anahtar Türü | Temel Amaç | Kritik Not |
| --- | --- | --- |
| **Primary Key** | Satırı benzersiz tanımlayan ana anahtar | NULL olamaz, tekrar edemez |
| **Candidate Key** | Primary seçilebilecek alternatif anahtar(lar) | Güçlü adaydır |
| **Super Key** | Satırı benzersiz yapabilen öznitelik kümesi | Candidate key'in üst kümesi olabilir |
| **Foreign Key** | Başka tablonun primary key'ine referans | İlişkiler arası tutarlılık sağlar |
| **Composite Key** | Birden fazla alanla kurulan anahtar | Tek alan yetmediğinde kullanılır |
| **Unique Key** | Alan değerlerini benzersiz tutar | Primary key'den farklı kullanım senaryosu vardır |

---

## 11) DDL Komutları ve DML Komutları Karşılaştırması

| Kategori | Amaç | Komutlar |
| --- | --- | --- |
| **DDL** | Veritabanı yapısını tanımlama/değiştirme | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| **DML** | Veriyi ekleme/güncelleme/silme | `INSERT`, `UPDATE`, `DELETE` |

Özet fark: **DDL şema ile**, **DML veri içeriği ile** çalışır.

---

## 12) İlişkisel Cebir Operatörleri ve Gösterimleri

| Operatör | Gösterim | İşlev |
| --- | --- | --- |
| **Select** | `σ p(r)` | Satır filtreler (koşula uyan tuple'lar) |
| **Project** | `π A1, A2, ... (r)` | Sütun seçer/yansıtır |
| **Union** | `r ∪ s` | Uyumlu iki ilişkiyi birleştirir |
| **Set Difference** | `r - s` | `r` içinde olup `s` içinde olmayanları döndürür |
| **Cartesian Product** | `r × s` | İki ilişkinin tüm kombinasyonlarını üretir |
| **Rename** | `ρ x(E)` | Sonuç ilişkiye yeni ad verir |

İlişkisel cebir, SQL'in kavramsal temelini oluşturan prosedürel sorgulama yaklaşımıdır.

---

## 13) İlişkisel Model Kavramları

| Informal Terim | Formal Terim | Açıklama |
| --- | --- | --- |
| Tablo | Relation | Verinin satır-sütun biçiminde tutulduğu yapı |
| Satır | Tuple | Tablodaki tek kayıt |
| Sütun/Alan | Attribute | Varlığın özelliğini tutan alan |
| Olası değer kümesi | Domain | Bir attribute için geçerli değer aralığı |
| Tablo tanımı | Relation Schema | Tablo adı + sütun yapısı |
| Anlık veri içeriği | Relation Instance | Tablonun belirli andaki gerçek kayıtları |

Ek olarak:
- **İlişki derecesi (degree):** sütun/öznitelik sayısı
- **İlişki niceliği (cardinality/önem):** satır/tuple sayısı
- **Temel ilişki özellikleri:** hücrede tek değer, öznitelik adlarının farklılığı, yinelenen tuple olmaması, satır/sütun sırasının anlamsal olarak kritik olmaması

---
