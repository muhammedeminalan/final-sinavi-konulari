# YBS 301 Veri Madenciliği – Sınav Çalışma Notu

Nov 3, 2026 · @Emin

## İçindekiler

- [Kapsam ve sınav uyarıları](#mkd9eteer6z.71)
- **Hafta 1**
  - [Neden VM, algoritma, tarihçe, disiplinler](#mkd9eteer6z.1238)
  - [DIKW piramidi](#mkd9eteer6z.4208)
  - [VM kavramı, veri ambarı, OLAP](#mkd9eteer6z.5596)
  - [KDD süreci](#mkd9eteer6z.8020)
  - [Veri ön işleme](#mkd9eteer6z.9446)
  - [Veri madenciliği modelleri](#mkd9eteer6z.13209)
  - [İstatistik vs VM, uygulama alanları](#mkd9eteer6z.16675)
  - [Yanlılıklar ve safsatalar](#mkd9eteer6z.18905)
  - [EDA: 7 veri seti ve 12 soru](#mkd9eteer6z.21531)
- **Hafta 2**
  - [Veri hazırlama ve temel kavramlar](#mkd9eteer6z.24081)
  - [Değişken tipleri](#mkd9eteer6z.25986)
  - [İstasyon 1: Temizleme](#mkd9eteer6z.28514)
  - [İstasyon 2: Birleştirme](#mkd9eteer6z.32330)
  - [İstasyon 3: İndirgeme](#mkd9eteer6z.33728)
  - [İstasyon 4: Dönüştürme ve normalleştirme](#mkd9eteer6z.36587)
- [Python kütüphaneleri](#mkd9eteer6z.59085)
- [Pestil & Köme lab](#mkd9eteer6z.51460)
- [Soru-cevap](#mkd9eteer6z.78646)
- [Son tekrar listesi](#mkd9eteer6z.86815)

## Kapsam ve sınav uyarıları

Bu not yalnızca [YBS-DataMining](https://github.com/kahramankostas/YBS-DataMining) reposundaki iki haftayı kapsar: 1. Hafta (Temel Kavramlar + EDA) ve 2. Hafta (Verinin Hazırlanması). 3–14. haftalar repoda henüz boş.

| Kaynak | İçerik |
| --- | --- |
| hafta1/README.md | 7 veri seti, yükleme kodları, 12 soruluk EDA listesi |
| hafta1/YBS301\_...\_Hafta1.md | Temel kavramlar, KDD, ön işleme, modeller, safsatalar |
| hafta2/README.md | Pestil & Köme vaka özeti, lab görev başlıkları |
| hafta2/YBS301\_...\_Hafta2.md | Değişken tipleri, 4 istasyon, normalleştirme, Python/R kodları |
| hafta2/gumushane\_pestil\_kome\_veriseti/readme.md | Lab görevlerinin ayrıntısı |
| pratik/readme.md | NumPy ve Pandas notebook hedefleri |

**Okunamayanlar:** ders1.pptx, 2.pptx ve .ipynb notebook'ları doğrudan okunmadı. Çalışma notları "kitap + sunum birleştirilerek" hazırlandığı için slayt içeriği büyük ölçüde kapsanıyor; yine de slaytlara bir göz at.

**Hocanın kendi düzelttiği iki kitap hatası (sınavda tuzak olabilir):**

- Z-skor sonucu 0 ile 1 arasında **değildir**. Ortalama 0, standart sapma 1 olur; değerler çoğunlukla −3 ile +3 arasına düşer, negatif ve 1'den büyük değerler çıkar.
- Kitaptaki örnekte 379'un z-skoru 0,770 yazıyor; doğrusu **0,767**.

## 1. Hafta: Neden veri madenciliği, algoritma, tarihçe, disiplinler

Veri madenciliği (VM), toplanması kolay ama anlamlandırılması zor büyük veriden karar destek bilgisi çıkarmak için doğdu. Çözümün kendisi değil, doğru karara destek olan bir **araçtır**.

### Neden ortaya çıktı?

- Bilişim teknolojileri ekonomik koşulları, müşteri beklentilerini ve rakip stratejilerini hızla değiştiriyor.
- Yöneticiler **zamanında elde edilmiş doğru bilgiyle** karar vermek zorunda.
- Veri toplamak ve saklamak kolay; ondan anlamlı bilgi çıkarmak zor.
- Geleneksel analiz yöntemleri veri hacmindeki artış karşısında yetersiz kaldı.

### Algoritma kavramı

Kelime, Harezmli matematikçi **Harezmi (Al-Khwarizmi)** adından gelir. Algoritma, bir problemi çözmek için çözüm yolunun **adım adım** tasarlanmasıdır.

| Problem türü | Tanım | Örnek |
| --- | --- | --- |
| Algoritmik | Adımları net tanımlanabilir | Sıralama, en kısa yol |
| Algoritmik olmayan | Kesin adımlarla tarif edilemez | Yüz tanıma, kediyi ayırt etme, iyi hamleyi sezme |

Makine öğrenimi ve VM, algoritmik olmayan problemlerde devreye girer.

| Tarih | Olay | Neden önemli |
| --- | --- | --- |
| 11 Mayıs 1997 | IBM Deep Blue, Kasparov'u yendi | Kaba kuvvet arama + uzman bilgisi |
| 15 Mart 2016 | Google AlphaGo, Lee Sedol'u 4-1 yendi | Go'da hamle sayısı çok fazla; sistem veriden öğrendi |

### Tarihsel gelişim

| Dönem | Gelişme |
| --- | --- |
| 1950'ler | İlk bilgisayarlar; 1957'de Frank Rosenblatt **perseptronu** geliştirdi (yapay nöronun ilk modeli) |
| 1960'lar | Veritabanı kavramı; 1969'da Minsky ve Papert perseptronun basit mantıksal işlemlerde yetersizliğini gösterdi; hiyerarşik ve ağ veri modelleri |
| 1970'ler | İlişkisel VTYS; kurala dayalı uzman sistemler |
| 1980'ler | VTYS'ler yaygınlaştı; işletmeler müşteri, rakip, ürün verisini saklamaya başladı |
| 1989 | **KDD (IJCAI-89) çalışma grubu** toplantısı; KDD terimi doğdu |
| 1991 | Toplantının sonuç makalesi: temel tanım ve kavramlar |
| 1992 | VM için ilk yazılım |
| 2000'ler | Tüm alanlara yayıldı; CRM ve ERP ile iş dünyasında yaygınlaştı |

İlk zamanlarda "veri taraması", "veri yakalama" denirdi; "veri madenciliği" adı 1990'larda bilgisayar mühendislerince kullanılmaya başlandı.

### Veri madenciliğine etki eden disiplinler

VM tek bir alan değil, birçok disiplinin kesişimidir.

| Disiplin | Kısaca |
| --- | --- |
| İstatistik | Klasik veri analizi; bilgisayar gücüyle eskiden yapılamayanlar mümkün oldu |
| Makine öğrenimi | Bilgisayarın örneklerden çıkarım yaparak öğrenmesi; yapay zekânın temeli |
| Görselleştirme | Veriyi tablo/grafikle sunmak; boyut arttıkça yeni araçlar gerekti |
| Veritabanı sistemleri | VM'nin "olmazsa olmazı" |
| Örüntü tanıma | Tanımlı bir örüntünün (parmak izi, ses, yüz, el yazısı) benzerlerini bulmak |

**Mantığı:** Makine öğrenimi, kediyi ilk kez gören bir çocuk gibidir. Her yeni kediyle "kedi" kavramı netleşir; çocuk ortak özelliklere bakarak sınıflandırmayı öğrenir. Makine de örneklerden ortak özellik çıkarıp yeni veriyi sınıflandırır.

**#10yearchallenge şakası:** 2009'da "istatistik" denen y = βX + ε, 2019'da "makine öğrenimi" diye anılıyor. Mesaj: yöntemlerin kökü istatistiktir.

## DIKW piramidi: Veri → Enformasyon → Bilgi → Bilgelik

R. Ackoff'un (1989) DIKW piramidi, ham veriden karara giden yolu dört katmanda gösterir. Alt üç katman **geçmişi** anlamaya, en üst katman **geleceğe** yönelik karara hizmet eder.

| Katman (alttan üste) | Cevapladığı soru | Tanım | Süreç |
| --- | --- | --- | --- |
| Veri | Hiçbir şey | Tek başına anlam taşımayan ham gözlem, sayı, sembol | Parçaları toplama |
| Malumat / Enformasyon | Ne? | Bağlam içinde ilişkilendirilmiş, düzenlenmiş veri | Parçaları bağlama |
| Bilgi | Nasıl? Neden? | Neden-sonuç ilişkisi kurulmuş, kavrayış sağlayan bilgi | Bütünün oluşması |
| Bilgelik | Neden yapmalı? En iyisi ne? | Birikmiş bilgiyi doğru karar için kullanmak | Bütünleri birleştirme |

### Örnek: Abraham Wald ve bombardıman uçakları (II. Dünya Savaşı)

| Katman | Wald örneğindeki karşılığı |
| --- | --- |
| Veri | Dönen uçaklardaki delik sayıları ve konumları (kanatta 120, gövdede 95, motorda 3) |
| Enformasyon | Deliklerin kanat ve gövdede yoğunlaştığı, motor ve kokpitte neredeyse olmadığı harita |
| Bilgi | İsabetler rastgele dağılır; motor/kokpitten vurulanlar **geri dönemediği** için örneklemde yok. Boş görünen yerler ölümcül noktalardır |
| Bilgelik | Zırh sınırlı (ağırlık yavaşlatır) → zırhı **deliksiz görünen hayati bölgelere** ekle |

**Mantığı:** Sadece "hayatta kalanlara" bakmak seni yanıltır. Bu örnek aynı zamanda **Hayatta Kalma Yanılgısı (Survivorship Bias)**'nın klasik örneğidir; sınavda iki konuyu birden sorabilirler.

## Veri madenciliği kavramı, veri ambarı ve OLAP

VM ile elde edilen bilgi **daha önce bilinmeyen, tahmin bile edilemeyen** bilgidir; VM zaten bilinen bir sonucu doğrulamak için kullanılmaz.

### Tanımlar (kitaptan)

- Büyük veri yığınlarında geleceği tahmin etmeye yardımcı **anlamlı ve yararlı ilişki ve kuralların** bilgisayar yazılımlarıyla aranmasıdır.
- Veriler arasındaki **örüntü (desen) ve ilişkileri** keşfedip doğru tahminler için kullanan bir **süreçtir**.
- İstatistiksel/matematiksel teknikler ve örüntü tanımayla yeni **korelasyon, örüntü ve eğilimlerin** keşfidir.

**Madencilik benzetmesi:** Altın, bor, kömür çıkarılıp işlenmedikçe değersizdir. Veritabanındaki veri de işlenmeyi bekleyen ham maddedir.

**Diğer adları:** bilgi çıkarımı, enformasyon keşfi, enformasyon hasadı, veri arkeolojisi, veri örüntü işleme.

**Sık yapılan hata:** VM ≠ KDD. VM, KDD sürecinin **yalnızca bir adımıdır**.

### Veri ambarı ve ilgili kavramlar

İşlemsel (günlük kayıt tutan) veritabanları VM'de **doğrudan kullanılmaz**; önce hazırlanır.

1. İç ve dış veri kaynakları toplanır.
2. Veri çekilir, temizlenir, dönüştürülür.
3. Veri ambarına yüklenir (alt kümeleri: veri depoları / data mart).
4. Erişim, sorgulama ve analizle OLAP veya VM yapılır.

| Kavram | Açıklama |
| --- | --- |
| İç veri kaynakları | İşletmenin kendi süreçleri (üretim, satın alma, pazarlama kayıtları) |
| Dış veri kaynakları | Sektör verileri, istatistik kurumu raporları, yasal düzenlemeler, döviz kurları |
| Veri ambarı (Data Warehouse) | İç + dış kaynakların birleştirildiği, **konu odaklı**, VM'ye hazır geniş veritabanı; **tüm işletmeyi** ilgilendirir |
| Üst veri (Metadata) | Ambardaki veriler hakkındaki tanımlamalar; ambarın "veri kataloğu" |
| Veri deposu (Data Mart) | Ambarın alt kümesi; **tek bir bölüm veya konuya** yönelik |
| OLAP | Çevrimiçi Analitik İşleme; ambardaki veri üzerinde **çok boyutlu** analiz ve sorgulama |

**Mantığı:** Ambar = tüm şirketin deposu, data mart = bir bölümün rafı, metadata = depo kataloğu.

### Sorgulama düzeyleri: SQL → OLAP → VM (kablo üreticisi örneği)

| Düzey | Örnek soru | Araç |
| --- | --- | --- |
| 1. Basit sorgu | "Geçen ay toplam ne kadar halojensiz tesisat kablosu sattık?" | İşlemsel veritabanı / SQL |
| 2. Çok boyutlu sorgu | "Ağustos'ta İç Anadolu'da ne kadar sattık; geçen ay, geçen yılın Ağustos'u ve tahminle karşılaştırması?" | OLAP (veri küpü: ürün × bölge × zaman × satış) |
| 3. Gizli örüntü | Akla gelmemiş, tahmin edilemeyen ilişkiler | Veri madenciliği |

İlk iki düzey **bilinen veya tahmin edilebilir** sonuçlar verir; VM **bilinmeyeni** arar.

## KDD: Veritabanlarında Bilgi Keşfi süreci

KDD, veriden faydalı bilgi keşfetme sürecinin **tamamıdır**; terim 1989'daki çalışma toplantısında ortaya atıldı. Sürecin en çok zaman alan aşaması **veri ön işlemedir**.

### Han ve Kamber gösterimi

1. Veritabanları / düz dosyalar
2. Veri temizleme ve bütünleştirme
3. Veri seçimi ve dönüştürme
4. Veri madenciliği
5. Örüntüler
6. Değerlendirme ve sunum
7. Bilgi

### Beş aşama (kitap)

| # | Aşama | Konum | Öz |
| --- | --- | --- | --- |
| 1 | Amacın tanımlanması | VM öncesi | Amaç probleme odaklı ve açık olmalı; başarı ölçütü, yanlış tahminin maliyeti, doğru tahminin kazancı tanımlanır |
| 2 | Veriler üzerinde ön işlemler | VM öncesi | Veriyi analize hazırlama; **en çok zaman alan aşama** |
| 3 | Modelin kurulması ve değerlendirilmesi | **VM'nin kendisi** | Birçok model denenir; en iyiye ulaşana kadar 2. ve 3. aşama tekrarlanır; geçerlilik sınanır |
| 4 | Modelin kullanılması ve yorumlanması | VM sonrası | Sonuç başlangıçtaki amaca ulaştı mı? Ulaşmadıysa süreç yenilenir |
| 5 | Modelin izlenmesi | VM sonrası | Koşullar değişir; model sürekli izlenir, gerekirse güncellenir |

**Mantığı:** "Çöp girer, çöp çıkar" (Garbage in, garbage out). Ön işleme özensizse model aşamasından sürekli geri dönersin. KDD'yi bir mutfak gibi düşün: malzemeyi seçmek ve temizlemek (ön işleme) pişirmekten (model) uzun sürer.

**Ezber kalıbı:** Amaç → Ön işlem → Model → Yorum → İzleme. Sınavda "VM, KDD'nin hangi aşamasıdır?" sorusunun cevabı: **3. aşama, modelin kurulması ve değerlendirilmesi**.

## Veri ön işleme (1. Hafta anlatımı)

Ön işleme üç işten oluşur: toplama/birleştirme, temizleme (kayıp veri + gürültü) ve yeniden yapılandırma (normalizasyon, azaltma, dönüştürme).

1. Verilerin toplanması ve birleştirilmesi
2. Verilerin temizlenmesi
   1. Kayıp veriler için işlem
   2. Gürültünün temizlenmesi
3. Verilerin yeniden yapılandırılması
   1. Normalizasyon
   2. Veri azaltma (indirgeme)
   3. Veri dönüştürme

### Toplama ve birleştirme

Amaca uygun veri önce iç kaynaklarda, sonra kamu veritabanları veya veri satan kuruluşlar gibi dış kaynaklarda aranır. **Verinin hangi koşulda ve hangi yöntemle toplandığı önemlidir.**

### Temizlemenin temel kavramları

| Kavram | Tanım | Örnek |
| --- | --- | --- |
| Kayıp veri | Kayıtta eksik değer | Doğum tarihi girilmemiş çalışan |
| Aykırı değer | Doğru olamayacak kadar uç değer | Doğum yılı 1974 yerine 1074 |
| Gürültülü veri | Aykırı veya yanlış girilmiş değerlerin genel adı | — |
| Uyumsuzluk | Kaynaklar arası farklı birim, zaman, kodlama | Bir sistemde cinsiyet E/K, diğerinde 0/1 |

### Kayıp verilerle başa çıkma

| Yaklaşım | Ne zaman uygun | Dikkat |
| --- | --- | --- |
| a. Kaydı silmek | Kayıp oranı çok küçükse | Oran yüksekse sonucu bozar |
| b. Elle doldurmak | Veri küçük, eksiğe ulaşılabilir, zaman var | Aksi hâlde zaman kaybı |
| c. Hepsine aynı sabit ("Y", "E", 9) | Hızlı çözüm | Algoritmayı yanıltabilir; kod başka anlamlı değerle çakışmamalı; bazen gizli örüntü de çıkarabilir |
| d. Ortalama ile doldurmak | Sayısal değişkenlerde | Genel ortalama yerine **sınıf ortalaması** daha uygun |
| e. Diğer değişkenlerle tahmin | Daha doğru doldurma için | Regresyon, zaman serisi, Bayes, karar ağacı, beklenti maksimizasyonu |

**Kira örneği:** 6 numaralı, Alanönü mahallesinde oturan 9 yıllık çalışanın kirası eksik.

- Genel ortalama: (850 + 675 + 780 + 950 + 1250) / 5 = 4505 / 5 = **901**
- Sınıf ortalaması (yalnızca Alanönü'ndeki iki çalışan): **865**
- Hangisinin kullanılacağına karar verici karar verir.

**Mantığı:** Sınıf ortalaması daha isabetlidir, çünkü eksik kişiye benzeyen (aynı gruptaki) kişilerden tahmin yapar. Aynı mahalledeki kira, şehrin ortalamasından daha iyi tahmin verir.

### Gürültüyü temizleme: bölmeleme (binning)

Örnek veri: 24, 18, 7, 27, 31, 24, 11, 37, 28

**Adım 1 — Sırala:** 7, 11, 18, 24, 24, 27, 28, 31, 37

**Adım 2 — Üç eşit bölüme ayır ve düzelt:**

| Bölüm | Orijinal | Ortalama ile | Sınır değerleri ile |
| --- | --- | --- | --- |
| 1 | 7, 11, 18 | 12, 12, 12 | 7, 7, 18 |
| 2 | 24, 24, 27 | 25, 25, 25 | 24, 24, 27 |
| 3 | 28, 31, 37 | 32, 32, 32 | 28, 28, 37 |

- **Ortalama/medyan ile:** Bölümdeki her değer bölüm ortalaması (veya medyanı) olur. Bölüm 1: (7 + 11 + 18) / 3 = 36 / 3 = 12.
- **Sınır değerleri ile:** Her değer, bölümün en küçük ya da en büyük değerinden hangisine yakınsa o olur. 11'in 7'ye uzaklığı 4, 18'e uzaklığı 7 → 7 olur. 31'in 28'e uzaklığı 3, 37'ye 6 → 28 olur.
- **Kitaptaki varyant:** (maks − min) / eleman sayısı bölüme atanır. Bölüm 1: (18 − 7) / 3 = 3,67.
- **Kümeleme:** Veri benzerliğe göre kümelenir; hiçbir kümeye girmeyen nokta aykırıdır ve en yakın kümenin ortalama/sınır değeriyle değiştirilir.
- **Regresyon:** Değişkenler arası ilişki bir fonksiyonla modellenir; biri diğerini tahmin eder (doğrusal / çoklu doğrusal).

**Mantığı:** Bölmeleme "komşularına bak" demektir. Uç bir değer, yakın komşularının ortalamasına çekilerek yumuşatılır. Sınav sorusu çözerken **önce sırala** adımını unutma; en sık yapılan hata budur.

### Yeniden yapılandırma

Bazı algoritmalar yalnızca sayısal, bazıları kategorik, bazıları 0/1 verilerle çalışır; veri algoritmaya uygun hâle getirilir.

| İşlem | Açıklama | Yöntem / Örnek |
| --- | --- | --- |
| Normalizasyon | Değerleri 0–1 gibi ortak aralığa getirmek | Min-maks, sıfır-ortalama (z-skor), ondalıklı |
| Veri azaltma | Temel özelliği kaybetmeden veri miktarını azaltmak | Boyut azaltma, sıkıştırma, PCA, faktör analizi |
| Veri dönüştürme | Algoritmanın kullanabileceği biçime getirmek | 1.500–5.000 TL maaşı "düşük/orta/yüksek" yapmak (kesikleştirme) |

## Veri madenciliği modelleri

Tüm modellerin ortak noktası **öğrenmedir**; modeller tahmin edici (denetimli, etiket var) ve tanımlayıcı (çoğunlukla denetimsiz, etiket yok) olarak ikiye ayrılır.

### Ortak özellik: öğrenme döngüsü

1. Yazılım örnek veriyi inceler, kural çıkarır → **öğrenme**
2. Kuralları kalan veriye uygulayıp kendini sınar → **test**
3. Gerekirse kuralları yeniler → **doğrulama**
4. **Aşırı öğrenme (overfitting)** kontrol edilir: kurallar yalnızca eğitim verisinde işliyor, yeni veride çöküyorsa model **ezber** yapmıştır.

**Mantığı:** Overfitting, sınav sorularını ezberleyip soru biraz değişince çözemeyen öğrencidir.

### Denetimli ve denetimsiz öğrenme

|  | Denetimli (Supervised) | Denetimsiz (Unsupervised) |
| --- | --- | --- |
| Etiket / sınıf bilgisi | **Var** (her kaydın yanında "kadın/erkek" yazar) | **Yok** |
| Amaç | Yeni gözlemin etiketini tahmin etmek | Benzerliğe göre doğal grupları bulmak |
| Veri kullanımı | Eğitim kümesi + test kümesi | Tüm veri |
| Örnek | Sınıflandırma, regresyon | Kümeleme |

### Model sınıflandırması

**Tahmin edici (Predictive):** Regresyon, sınıflandırma, (zaman serisi analizi). Algoritmalar: karar ağaçları, yapay sinir ağları, genetik algoritmalar, k-en yakın komşu, Bayes sınıflandırması, destek vektör makineleri, hatayı geri yayma.

**Tanımlayıcı (Descriptive):** Kümeleme, birliktelik kuralları, sıra örüntü analizi, özetleme, (istisna/aykırı değer analizi, tanımlayıcı istatistik).

### Tahmin edici modeller

**Bilinenden yola çıkıp bilinmeyeni tahmin eder.** Örnek: banka geçmiş kredi verisinden yeni müşterinin krediyi ödeyip ödemeyeceğini, hastane geçmiş vakalardan yeni hastanın teşhisini tahmin eder.

- **Regresyon:** Bağımlı ve bağımsız değişkenler arasındaki ilişkiyi en iyi tanımlayan fonksiyonu bulur; çıktı **sürekli** (sayı).
- **Sınıflandırma:** Veriyi önceden belirlenmiş sınıflara atar; çıktı **kategorik**; denetimlidir.

| Algoritma | Ana fikir | Artı / eksi |
| --- | --- | --- |
| Karar ağaçları | Kök düğümden başlar, her düğümde bir özellik test edilir, yapraklar sınıfı verir | En yaygın; anlaşılması ve kurulması kolay |
| Yapay sinir ağları | Biyolojik sinir sistemini taklit eder | Karmaşık, doğrusal olmayan ilişkileri modeller; **yorumlanması zor** |
| Genetik algoritmalar | Evrimi taklit eder: nüfus, kromozom, uygunluk fonksiyonu | Doğrudan VM modeli değil, **eniyileme** yöntemi |
| Zaman serisi analizi | Zamana bağlı verinin gelecek değerini tahmin eder | En yaygın alan borsa; denetimli |
| k-en yakın komşu (k-NN) | Yeni noktayı en yakın k komşusunun sınıfına atar (Öklid uzaklığı) | k çok büyük → farklı noktalar karışır; k çok küçük → benzerler ayrı sınıfa düşer, gürültüye duyarlılık artar |
| Bayes sınıflandırması | Bayes kuralıyla her sınıfa girme olasılığını hesaplar | Olasılık temelli, hızlı |

### Tanımlayıcı modeller

Verideki örüntü ve ilişkileri tanımlar; kayıtlar arasında bağlantı kurar.

| Model | Ne yapar | Örnek |
| --- | --- | --- |
| Kümeleme | Benzerliğe göre gruplar; hedef değişken yok (**denetimsiz**); kümelerin anlamını alan uzmanı yorumlar | Poliçesini yenilemeyen müşterilerin ortak özellikleri |
| Birliktelik kuralları | Birlikte görülen öğeleri bulur (pazar sepeti analizi) | "Bira alanların %80'i cips de alıyor" → raf düzeni, çapraz satış |
| Sıra örüntü analizi | Birliktelik + **zaman sırası** | "Çekiç alan müşteri ilk üç ayda %15 olasılıkla çivi alır" |
| Özetleme | Alt gruplara ayırıp ortalama, std gibi göstergeler üretir (karakterizasyon / genelleştirme) | Müşteri segment profili |

**Mantığı:** Sınıflar **önceden biliniyorsa** sınıflandırma (denetimli); **bilinmiyorsa** kümeleme (denetimsiz). Birliktelik "ne ile ne birlikte", sıra örüntü "ne, neden sonra" sorusudur.

## Diğer analiz yaklaşımları ve uygulama alanları

Geleneksel istatistik hipotezle başlar ve elle eşitlik kurar; VM hipotezsiz, otomatik keşif yapar ve gizli bilgiyi arar.

### Geleneksel istatistik vs veri madenciliği

| Geleneksel istatistik | Veri madenciliği |
| --- | --- |
| Bir **hipotez** kurarak başlar | Hipoteze ihtiyaç duymaz |
| İstatistikçi eşitlikleri **kendisi** geliştirir | Algoritmalar eşitlikleri **otomatik** geliştirir |
| Çoğunlukla **sayısal** veri | Sayısala ek olarak **metin, ses** vb. |
| Kirli veri analiz sırasında bulunup filtrelenir | **Temizlenmiş** veri üzerinde çalışır |
| Sonuçlar görece kolay yorumlanır | Yorumlamak zor, **uzman** gerekir |

### Kullanım amacına göre araç seçimi

| Araç | Ne zaman |
| --- | --- |
| Veri sorgusu / SQL | Ne aradığını tam biliyorsan |
| OLAP | Çok boyutlu, basit ilişkileri incelemek istiyorsan |
| Veri madenciliği | Açıkça gözlenemeyen örüntü ve ilişkileri keşfetmek istiyorsan |

### Keşfedilen bilgi tipine göre

| Bilgi tipi | Açıklama | Araç |
| --- | --- | --- |
| Sığ bilgi | Veritabanından doğrudan sorgulanabilen | SQL |
| Çok boyutlu bilgi | Veri küpü üzerinden analiz edilebilen | OLAP |
| Gizli bilgi | Kolayca görülemeyen örüntü ve ilişkiler | Veri madenciliği |
| Derin bilgi | Bulunması için ipucu gereken, en zor erişilen | VM'nin araştırma sınırları |

**Mantığı:** Sığ → çok boyutlu → gizli → derin sırası, "ne kadar kazman gerekiyor" sırasıdır.

### Uygulama alanları

Büyük veri üretilen ve karar gereken her alan: pazarlama, finans (bankacılık, sigorta, borsa), perakende, sağlık, telekomünikasyon, endüstri, eğitim, tıp, biyoloji, genetik, kamu, istihbarat ve güvenlik.

| Alan | Örnek uygulamalar |
| --- | --- |
| Pazarlama (en yoğun alan) | Müşteri segmentasyonu, pazar sepeti, kampanya hedefleme, müşteri kaybı (churn) tahmini |
| Finans | Kredi riski, kredi kartı dolandırıcılığı tespiti, borsa tahmini |
| Sağlık | Hastalık teşhisi ve risk tahmini, tedavi etkinliği, ilaç etkileri |
| Endüstri / mühendislik | Arıza tahmini, kalite kontrol, üretim optimizasyonu |
| Eğitim | Başarıyı etkileyen faktörler, okulu bırakma riski |

**Tarihî örnek — John Snow ve kolera (Londra, 1854):** Snow kolera ölümlerini Soho haritasına işaretledi; vakalar **Broad Street'teki su pompası** çevresinde yoğunlaştı. Pompanın kolu çıkarıldı, salgın yavaşladı. Veri görselleştirme ve mekânsal analizin karara dönüştüğü en bilinen erken örnektir.

## Veriyle düşünürken tuzaklar: yanlılıklar ve safsatalar

Ana kural: **korelasyon nedensellik değildir**. İki değişkenin birlikte hareket etmesi birinin diğerine neden olduğunu göstermez; çoğu zaman arkada bir **karıştırıcı (ortak neden) değişken** vardır.

### Sunumdaki sahte korelasyon örnekleri

| Örnek | Gerçek açıklama |
| --- | --- |
| Dondurma satışı ↔ köpekbalığı saldırısı | Ortak neden: **yaz / sıcak hava** |
| Organik gıda satışı ↔ otizm teşhisi (r = 0,997) | İkisi de zamanla artıyor; teşhis kriteri ve farkındalık değişti. Ortak trend ≠ neden |
| Kişi başı çikolata ↔ Nobel sayısı (r = 0,79) | Ülkenin refahı, eğitim ve araştırma yatırımı |
| 2016 Brexit "ayrıl" bölgeleri ↔ 1992 deli dana (BSE) bölgeleri | Harita benzerliği nedensellik değildir (ekolojik düzeyde çıkarım tehlikesi) |
| Çatıdaki leylek yuvası ↔ çocuk sayısı | Büyük evde hem daha çok çocuk hem daha çok yuva yeri var |

### Datasaurus: önce görselleştir

Farklı şekilli veri setleri (dinozor dahil) **aynı ortalama, standart sapma ve korelasyona** sahip olabilir. Yalnız özet istatistiğe bakmak yanıltır; veriyi mutlaka **grafikle** incele. **Anscombe dörtlüsü** de aynı dersi verir.

### 1. Örneklem ve seçim yanlılıkları

| Terim | Kısaca |
| --- | --- |
| Hayatta kalma yanılgısı (Survivorship bias) | Yalnızca başaranlara/hayatta kalanlara bakmak (Wald'ın uçakları) |
| Cımbızlama (Cherry picking) | İşine gelen veriyi seçip diğerlerini yok saymak |
| Gönüllü katılım yanlılığı | Ankete yalnızca güçlü fikri olanlar katılır; örneklem temsilî olmaz |

### 2. İstatistiksel ve metodolojik çarpıtmalar

| Terim | Kısaca |
| --- | --- |
| Teksas keskin nişancısı | Önce ateş edip hedefi kurşunların etrafına çizmek; rastgele kümelenmeye sonradan anlam yüklemek |
| Simpson paradoksu | Alt gruplardaki eğilimin gruplar birleşince **tersine dönmesi** |
| Sahte hassasiyet | Kaba tahmini "%37,284" gibi aşırı kesin göstermek |
| Ortalamanın aldatıcılığı | Ortalamaya göre plan yapmak; "ortalama kişi" çoğu zaman yoktur |
| Göreceli vs mutlak risk | "Riski %50 artırıyor" (1/10.000 → 1,5/10.000) diyerek algıyı abartmak |

### 3. Mantıksal ve çıkarımsal safsatalar

| Terim | Kısaca |
| --- | --- |
| Cum hoc ergo propter hoc | **Birlikte** olduğu için biri diğerinin nedeni sanmak |
| Post hoc ergo propter hoc | **Ondan sonra** olduğu için onun yüzünden sanmak |
| Ekolojik safsata | Grup düzeyindeki bulguyu tek tek bireylere genellemek |
| Kumarbaz safsatası | "5 kez yazı geldi, şimdi tura gelir"; bağımsız olaylar birbirini etkilemez |
| Ortalamaya dönüşü görmezden gelme | Uç sonucun ardından gelen normale dönüşü bir müdahalenin etkisi sanmak |

**Ezber ipucu:** *cum* = "ile" (birlikte) → korelasyon hatası; *post* = "sonra" → zaman sırası hatası. Dondurma–köpekbalığı sorusu gelirse cevap: **cum hoc**, karıştırıcı değişken **sıcak hava**.

## EDA: 7 temel veri seti ve 12 soruluk kontrol listesi

Model kurmadan önce veriyi tanımak gerekir: boyutu, tipleri, eksikleri ve dağılımı. Derste 7 klasik veri seti ve her birine sorulacak 12 soru verildi.

### 7 temel veri seti

| Veri seti | Tür | Boyut | Ne için |
| --- | --- | --- | --- |
| Iris | Klasik tablo / sınıflandırma | 150 örnek, 4 nitelik | Çiçek türü (3 sınıf); en bilinen başlangıç seti |
| Wine | Klasik tablo / sınıflandırma | 178 örnek, 13 nitelik | Kimyasal özelliklerden 3 şarap üreticisi |
| Breast Cancer | İkili sınıflandırma | 569 örnek, 30 nitelik | Tümör iyi (benign) / kötü (malignant) huylu |
| California Housing | Regresyon | 20.640 blok grubu | Medyan konut fiyatı (sürekli hedef) |
| Titanic | Karmaşık ve eksik veri | Yolcu profilleri | Yaş/kabin eksik; kategorik + sayısal karışık |
| MNIST 784 | Görüntü işleme | 70.000 örnek, 28×28 piksel | El yazısı rakam; 784 piksel özelliği |
| 20 Newsgroups | Metin / NLP | Binlerce haber iletisi | Metni vektörleştirme, konu modelleme |

**Mantığı:** Her set bir problem türünü temsil eder. Iris/Wine çok sınıflı sınıflandırma, Breast Cancer ikili sınıflandırma, California regresyon, Titanic eksik veri, MNIST görüntü, 20 Newsgroups metin. "Hangi set regresyondur?" sorusunun cevabı **California Housing**.

### 12 soruluk EDA kontrol listesi

| # | Soru | Pandas karşılığı | İpucu |
| --- | --- | --- | --- |
| 01 | Kaç gözlem var? | df.shape\[0\] veya len(df) | Satır sayısı |
| 02 | Kaç özellik var? | df.shape\[1\] veya len(df.columns) | Sütun sayısı |
| 03 | Özellik isimleri neler? | list(df.columns) | Kolon başlıkları |
| 04 | Hangileri sayısal? | df.select\_dtypes(include='number') | int64, float64 |
| 05 | Kategorik özellik var mı? | df.select\_dtypes(include=\['object', 'category'\]) | Metinsel/sınıfsal |
| 06 | Eksik veri var mı? | df.isnull().sum() | Sütun bazlı NaN sayısı |
| 07 | Hedef değişken nedir? | y (bağımlı değişken) | Tahmin edilecek sütun |
| 08 | Hedef kaç farklı değer alıyor? | y.nunique() / y.unique() | Sınıf çeşitliliği |
| 09 | Sınıflar dengeli mi? | y.value\_counts(normalize=True) | Sınıf oranları (%) |
| 10 | Değer aralıkları benzer mi? | df.describe().T\[\['min', 'max'\]\] | Ölçekleme ihtiyacı |
| 11 | En yüksek korelasyonlu iki özellik? | df.corr().abs() | Değişkenler arası ilişki |
| 12 | Dikkat çeken anormallik var mı? | EDA gözlemi | Aykırı değer, sıfır yoğunluğu |

**Son soru:** "Bu veri setinden hangi sorulara cevap vermeye çalışabiliriz?" Model kurmadan önce iş problemini formüle et: sınıflandırma, regresyon, kümeleme veya anomali tespiti.

**Mantığı:** 10. soru normalleştirmeye, 6. soru eksik veri stratejisine, 9. soru dengesiz sınıf problemine bağlanır. Yani EDA, 2. haftanın ön işleme kararlarının girdisidir.

## 2. Hafta: Veri hazırlama ve temel kavramlar

Veri hazırlama, ham veriyi analize hazır hâle getiren işlemlerin bütünüdür ve analistin zamanının **yaklaşık %80'ini** alır.

- **Amaç:** Ham veriyi değersizleştiren hata ve sorunları ortadan kaldırmak.
- Literatürde aşamaların adı ve sayısı yazara göre değişir; amaç hep aynıdır.
- **Neden bu kadar vakit alır?** Gerçek dünya verisi kusurludur. İnsan hatası, teknolojik kısıt ve sistem arızası veriyi **gürültülü (noisy), eksik (missing) ve tutarsız (inconsistent)** yapar.
- **Veri nereden gelir?** İnsanın oluşturduğu dosyalar, işletme VTYS'leri, standart veritabanları, otomatik kayıt araçları (RFID, barkod, karekod), uydular. Farklı kaynak = farklı yapı ve tip.

**Buzdağı benzetmesi:** Su üstü (görünen) = veri madenciliği ve keşif. Su altı (görünmeyen, %80) = temizleme, birleştirme, indirgeme, dönüştürme.

**Hatırlatma:** Sonucu zaten tahmin edilebilen bir soru için VM'nin maliyetine katlanmak mantıklı değildir.

### Nesne, özellik, ölçme, ölçek

Veri seti bir tablodur: **satırlar nesne**, **sütunlar özellik**, kesiştikleri hücre o nesne için özelliğin aldığı değerdir.

| Kavram | Tanım | Eş anlamlıları |
| --- | --- | --- |
| Nesne | Tablodaki satırlar; gözlemler | Kayıt, gözlem, örnek (instance) |
| Özellik | Tablodaki sütunlar; varlıkları birbirinden ayıran değişkenler | Değişken, nitelik, öznitelik (feature) |
| Ölçme | Birimlerin özelliklerinin derecesini belirleyip sayısal ifade etmek | — |
| Ölçek | Sınıflama, sıralama, derecelendirme veya miktar belirlemenin kural ve kısıtlarını belirleyen ölçme aracı | — |

**Market örneği** (hepsi ölçme, ölçekleri farklı):

- Ürünleri türüne göre sınıflamak → isimsel
- Çalışanları yönetimden en alt kademeye sıralamak → sıra gösteren
- Ürünün ağırlığını ölçmek → oranlı
- Aylık performansı puanlamak → sayısal ölçek

**Mantığı:** Değişken tipini bilmemek ciddi analiz hatası doğurur. Klasik örnek: **posta kodlarının ortalamasını almak**. Posta kodu sayıdır ama isimseldir; ortalaması anlamsızdır.

## Değişken tipleri ve ölçek hiyerarşisi

Altı değişken tipi iki gruba ayrılır: kategorik (isimsel, ikili, sıra gösteren) ve sürekli/sayısal (tamsayılı, aralıklı, oranlı). Sınavın en çok soru çıkabilecek kısmı **aralıklı–oranlı ayrımıdır**.

| Grup | Tip | İşlevi | İzin verilen işlemler | Mutlak sıfır | Örnekler |
| --- | --- | --- | --- | --- | --- |
| Kategorik | İsimsel (Nominal) | Sınıflandırma, etiketleme | Yalnızca =, ≠, sayma | Yok | Cinsiyet, ürün türü, hastalık türü, kan grubu |
| Kategorik | İkili (Binary) | İki olasılıklı durum | Sayma | Yok | Doğru/Yanlış, Pozitif/Negatif, 0/1 |
| Kategorik | Sıra gösteren (Ordinal) | Derecelendirme, sıralama | =, ≠, <, > | Yok | Kıdem, unvan, mezuniyet derecesi, harf notu |
| Sürekli | Tamsayılı (Integer) | Kesir alamayan sayılabilir değerler | +, −, × | Var | Satılan ekmek, koli adedi, çocuk sayısı |
| Sürekli | Aralıklı (Interval) | Eşit aralıklı nicel ölçüm | +, − | **Yok** (göreli sıfır) | Sıcaklık (°C), doğum yılı, rakım |
| Sürekli | Oranlı (Ratio) | En üst düzey nicel ölçüm | Tüm işlemler + **oranlama** | **Var** (mutlak yokluk) | Ağırlık, boy, gelir, tutar, mesafe |

### Her tip için kritik noktalar

- **İsimsel:** Sayıyla kodlanabilir (1, 2, 3…) ama sayılar yalnızca **etikettir**; aritmetik anlamsız.
- **İkili:** İsimselin özel hâli; yalnızca iki sonuç.
- **Sıra gösteren:** Eşitlik + sıralama içerir, isimseli kapsar. Kademeler arası mesafe **eşit değildir**: müdür–şef farkı, şef–memur farkıyla aynı değildir.
- **Aralıklı:** Farklar anlamlıdır ama sıfır **keyfidir**: 0 °C "sıcaklık yok" değildir. Bu yüzden **oran hesaplanamaz**: 20 °C, 10 °C'nin iki katı sıcak değildir.
- **Oranlı:** Sıfır her birimde aynı anlamdadır: 0 kg = 0 g = ağırlık yok. **Oranlama yapılabilir**: 10 kg, 5 kg'ın iki katıdır.

### Ölçek hiyerarşisi

İsimsel (=) ⊂ Sıra gösteren (=, <, >) ⊂ Aralıklı (+, −) ⊂ Oranlı (×, ÷, oran). Her üst düzey alttakilerin tüm özelliklerini taşır.

### Karar mantığı (hızlı test)

1. Sayısal işlem anlamlı mı? Hayır → kategorik.
   1. Sadece iki değer mi? Evet → **ikili**.
   2. Sıralama anlamlı mı? Evet → **sıra gösteren**; hayır → **isimsel**.
2. Evet → sayısal.
   1. Kesirsiz sayım mı (adet)? → **tamsayılı**.
   2. "Sıfır, yokluk anlamına geliyor mu?" Evet → **oranlı**; hayır → **aralıklı**.

**Mantığı:** "İki katı" diyebiliyor musun? 40 kg, 20 kg'ın iki katı → oranlı. 2000 yılı, 1000 yılının "iki katı zaman" değil → aralıklı. Sıcaklık neden tuzak? Kelvin'de mutlak sıfır var: 20 °C = 293 K, 10 °C = 283 K; oran ≈ 1,035, yani sadece %3,5 fark.

**Hızlı örnek seti (kitaptan):** Kan grubu → isimsel · Harf notu (AA, BA, BB) → sıra gösteren · Doğum yılı → aralıklı · Aylık gelir → oranlı · Sigara içiyor mu → ikili · Sınıftaki öğrenci sayısı → tamsayılı.

## 4 aşamalı hat ve İstasyon 1: Veri temizleme

Veri hazırlama 4 istasyonlu bir rafineri hattıdır: **Temizle → Birleştir → İndirge → Dönüştür**. Çoğu uygulamada birden fazlası birlikte kullanılır; sıra veriye göre değişebilir.

| İstasyon | Amaç | Sloganı |
| --- | --- | --- |
| 1. Temizleme | Eksik veri, gürültü, tutarsızlık | Eksikliği gider, aykırıyı tıraşla |
| 2. Birleştirme | Çoklu kaynağı tek veri ambarında toplamak | Şemaları düğümle, tekrarları sil |
| 3. İndirgeme | Daha küçük ama aynı sonucu veren veri | Boyutu daralt, hacmi sıkıştır |
| 4. Dönüştürme | Algoritmaya uygun form | Z-skor / min-maks ile kalıba sok |

**Veri kalitesi** şu sorunların varlığıyla ölçülür: gürültü ve aykırı değerler, eksik, tutarsız ve tekrarlı veriler.

### Temizleme: üç ana başlık

Temizleme, veri kalitesi problemlerinin fark edilip doğrulanmasıdır: **eksik veri, gürültülü veri, tutarsız veri**.

### Eksik veri

**Nedenleri:** Ankette bilgi vermek istememe, yanlış anlama, veri giriş hatası, tutarsız olduğu için silinme.

**Kritik uyarı:** Her boş değer eksik veri değildir. Kadın çalışanların "askerlik durumu" alanının boş olması o nesne için **uygulanamaz** olmasındandır. Doldurmak hatalı bilgi üretir; "uygulanamaz" diye ayrı kategori kullan.

**Strateji karar mantığı:**

1. Veri büyük ve eksik oranı çok düşük mü? → **Nesneyi/özelliği ele** (en basit; enformasyon kaybı riski).
2. Algoritma eksiği kendisi tolere ediyor mu? → **Göz ardı et** (kümelemede yalnızca dolu özelliklerle benzerlik hesabı).
3. Eksik değerin tahmini mi gerekiyor? → **Tahmin ederek doldur** (imputation).

**A) Elemek**

- Satırı silmek: basit ve etkili; ama o satırın diğer özelliklerindeki enformasyon da gider. Birkaç eksik satır varsa uygun.
- Sütunu silmek: özellik analiz için önemli olabilir; dikkatli ol.

**B) Tahmin ederek doldurmak**

| Yöntem | Açıklama | Değerlendirme |
| --- | --- | --- |
| Elle doldurma | Eksiği tek tek bulup girmek | Eksik çok, veri büyükse uygulanamaz |
| Sabit değer | Tüm boşluklara "Bilinmiyor" veya 0 | Basit ama algoritmayı yanıltır; **tercih edilmez** |
| Merkezi eğilim | Özelliğin ortalaması, medyanı veya modu | Hızlı; **varyansı düşürür** |
| Sınıf ortalaması | Önce eksiğin sınıfı bulunur, o sınıfın ortalaması kullanılır | Genel ortalamadan isabetli |
| **En olası değer** | Regresyon, sonuç çıkarma araçları veya karar ağacıyla tahmin | Enformasyondan **en çok yararlanan** ve **en sık kullanılan** yöntem |

**C) Göz ardı etmek:** Birçok algoritma eksiği atlayacak şekilde ayarlanabilir. Özellik sayısı az veya eksik sayısı çok değilse sonuç hemen hemen doğrudur.

**Mantığı:** Sayısal sütunda ortalama/medyan, **kategorik sütunda mod** (en sık değer) kullanılır, çünkü "Ankara" ile "İzmir"in ortalaması alınamaz. Aykırı değer varsa medyan ortalamadan daha güvenlidir.

### Gürültülü veri ve aykırı değerler

**Gürültü:** Beklenen değerlerden sapan aykırı değerler veya hatalar. **Nedenleri:** hatalı toplama gereçleri, veri giriş/iletim problemleri, teknolojik kısıtlar, özellik isimlerindeki tutarsızlık.

| # | Yöntem | Nasıl çalışır |
| --- | --- | --- |
| 1 | Bölmeleme (Binning) | Sırala → eşit bölmelere ayır → bölme ortalaması (veya medyan/sınır) ile düzleştir; komşulara baktığı için **yerel düzleştirme** |
| 2 | Kümeleme (Clustering) | Benzer veriyi kümele; **hiçbir kümeye girmeyen** nokta aykırıdır |
| 3 | İnsan–bilgisayar denetimi | Bilgisayar şüpheliyi işaretler, insan karar verir (el yazısı tanımada faydalı mı çöp mü) |
| 4 | Regresyon | Veriyi bir fonksiyona (doğruya) uydurup pürüzleri giderir |

**Bölmeleme örneği (2. hafta):** 4, 8, 15, 21, 21, 24, 25, 28, 34 → 3 bölme

| Bölme | Değerler | Ortalama | Düzeltilmiş |
| --- | --- | --- | --- |
| 1 | 4, 8, 15 | 27 / 3 = 9 | 9, 9, 9 |
| 2 | 21, 21, 24 | 66 / 3 = 22 | 22, 22, 22 |
| 3 | 25, 28, 34 | 87 / 3 = 29 | 29, 29, 29 |

### Tutarsız veri

- Bazıları **kaynak belgelere** bakılarak elle düzeltilir.
- Bilgi mühendisliği araçları bilinen veri kısıtlarını ihlal eden kayıtları bulur; özellikler arası **işlevsel bağımlılıklar** ("posta kodu → şehir") hataları ortaya çıkarır.
- Örnek: doğum tarihi 2010, yaş 45 → tutarsız kayıt.

## İstasyon 2: Veri birleştirme

Veri birleştirme, çoklu kaynaklardan (veritabanları, veri küpleri, dış dosyalar) gelen verinin uygun bir **veri ambarında** toplanmasıdır. Üç temel sorun ve üç çözüm ezberlenmeli.

| Problem | Açıklama | Çözüm |
| --- | --- | --- |
| Şema uyuşmazlığı | Aynı varlık farklı kaynakta farklı isimde (musteri\_id ↔ cust\_no) | **Meta veri** (veri hakkında veri) ve veri sözlükleriyle eşleştirme |
| Veri fazlalığı (Redundancy) | Aynı özellik birden fazla kaynaktan gelip tekrarlanmış ("yıllık gelir" ile "aylık gelir × 12") | **Korelasyon analizi**: ilişkinin yönü, büyüklüğü, önemi ölçülerek tekrarlar bulunur |
| Veri değer karmaşası | Ölçek, birim, gösterim farkı (kg ↔ libre; E/K ↔ 0/1) | **Birim dönüşümü ve heterojenlik düzeltmesi**: tek standarda indirgeme |

**Lab'deki karşılıkları (Pestil & Köme):**

- **Şema eşleştirme (schema matching):** A dosyasının Türkçe sütunları ile B'nin İngilizce sütunları, B'nin metadata sayfasıyla eşlenir.
- **Varlık eşleştirme (entity resolution):** Aynı müşteri iki kanalda farklı müşteri numarasıyla olabilir. Aynı ad-soyadlı farklı kişilere dikkat.
- **Değer karmaşası:** Para birimi, ağırlık birimi, puan ölçeği, sıcaklık birimi, cinsiyet ve üyelik kodlaması farkları.

**Mantığı:** Şema = "sütun adları uyuşmuyor", fazlalık = "aynı bilgi iki kez var", değer karmaşası = "aynı bilgi farklı birimde". Fazlalığı korelasyonla bulursun, çünkü birinden türetilen sütun diğeriyle neredeyse 1,0 korelasyon verir.

## İstasyon 3: Veri indirgeme

Çok büyük veriyi olduğu gibi analiz etmek pratik değildir; daha küçük bir veri kümesi oluşturulur. **Altın kural:** indirgenmiş veriyle elde edilen sonuç, tam veriyle elde edilecek sonuçtan **çok farklı olmamalıdır**.

| Yöntem | Ne yapar | Örnek / teknik |
| --- | --- | --- |
| Veri küpü birleştirme (OLAP) | Ayrıntılı veriyi üst düzeyde özetler (ön hesaplama) | Günlük/aylık satışları yıllığa çevirmek (roll-up) |
| Boyut indirgeme | Gereksiz/ilgisiz **sütunları** çıkarır | İleriye seçme, geriye eleme, birleşik; wrapper veya filter |
| Veri sıkıştırma | Kodlama/dönüşümle sıkıştırılmış gösterim | Kayıpsız / kayıplı |
| Büyük sayıların indirgenmesi | Veriyi daha küçük gösterimle temsil eder | Parametrik: regresyon, log-doğrusal · Parametrik olmayan: histogram, kümeleme, örnekleme |

### Boyut indirgeme

**Faydaları:** Algoritma verimli çalışır, model anlaşılır olur, görselleştirme kolaylaşır, işlemci süresi ve bellek azalır.

**Sorun:** d özellik varsa olası alt küme sayısı **2ᵈ**. 30 özellik → 2³⁰ ≈ 1 milyardan fazla; 20 özellik → 2²⁰ = 1.048.576. Hepsini denemek imkânsız, bu yüzden **sezgisel (heuristic)** yöntemler kullanılır.

| Sezgisel yöntem | Mantık |
| --- | --- |
| İleriye doğru seçme | Boş kümeyle başla, her adımda en iyi özelliği **ekle** |
| Geriye doğru eleme | Tüm özelliklerle başla, her adımda en kötüsünü **çıkar** |
| Birleşik | Her adımda en iyiyi ekle, en kötüyü çıkar |

En iyi/en kötü özellik; istatistiksel anlamlılık testleri (özellikler bağımsız varsayımıyla) veya karar ağaçlarındaki **enformasyon kazancı (information gain)** ile belirlenir.

|  | Sarmalama (Wrapper) | Süzme (Filter) |
| --- | --- | --- |
| Özellik seçerken | Madencilik algoritmasının **kendisini** kullanır | Algoritmadan **bağımsız** ölçüt |
| Sonuç geçerliliği | Daha yüksek | Daha düşük |
| Hesaplama maliyeti | **Çok yüksek** | Düşük |

**Mantığı:** Wrapper, kıyafeti üstünde deneyerek seçmek (doğru ama yavaş); filter, etiketteki bedene bakarak seçmek (hızlı ama bazen uymaz).

### Veri sıkıştırma

- **Kayıpsız (lossless):** Orijinal veri birebir geri elde edilir (ZIP, gzip, Parquet).
- **Kayıplı (lossy):** Yalnızca yaklaşık hâli elde edilir (JPEG, MP3).

### Büyük sayıların indirgenmesi (numerosity reduction)

- **Parametrik:** Verinin kendisi değil yalnızca **model parametreleri** saklanır.
  - Doğrusal regresyon: y = a + bx → yalnızca a ve b saklanır.
  - Çoklu regresyon: birden fazla özellikle modeller.
  - Log-doğrusal model: kesikli çok boyutlu olasılık dağılımlarını yaklaşık modeller.
- **Parametrik olmayan:**
  - **Histogram** (en yaygın): veriyi aralıklara bölüp dağılımı çıkarır (eşit genişlik veya eşit frekans).
  - **Kümeleme:** veriyi kümeler ve küme temsilcileriyle ifade eder.
  - **Örnekleme:** büyük kümeyi çok daha küçük bir alt kümeyle temsil eder (basit rastgele, tabakalı).

**Mantığı:** Parametrik = "veriyi bir formüle sığdır, formülü sakla". Parametrik olmayan = "formül yok, özet tut". Tabakalı örnekleme, her alt grubu (ör. her ilçeyi) oranında temsil ettiği için basit rastgeleden daha dengeli sonuç verir.

## İstasyon 4: Veri dönüştürme ve normalleştirme

Orijinal özellikler gerekli enformasyonu içerse de algoritmaya uygun formda olmayabilir; dönüştürme bunu düzeltir. Sınavda büyük olasılıkla **min-maks, z-skor ve ondalık ölçekleme hesabı** sorulur.

### Beş dönüştürme işlemi

| İşlem | Açıklama | Örnek |
| --- | --- | --- |
| Düzeltme (Smoothing) | Gürültüyü temizlemek | Bölmeleme, regresyon, kümeleme |
| Bir araya getirme (Aggregation) | Özetleme | Günlük veriyi aylığa çevirmek |
| Genelleme (Generalization) | Düşük düzey veriyi üst kavrama taşımak | Yaş → genç/orta yaşlı/yaşlı · Cadde → şehir → ülke |
| Normalleştirme (Normalization) | Sayısal değerleri küçük aralığa ölçeklemek | Min-maks, z-skor, ondalık |
| Özellik oluşturma (Feature construction) | Mevcut özelliklerden yeni özellik türetmek | Yükseklik × genişlik → alan |

**Karıştırma:** VM'deki "normalleştirme", istatistikteki değişkeni **normal dağılıma** dönüştürme değildir; amaç yalnızca **ölçeklemektir**.

**Neden gerekli?** Yapay sinir ağlarında öğrenmeyi hızlandırır. Mesafeye dayalı algoritmalarda (kümeleme, k-NN) zorunluya yakındır; yoksa aralığı büyük olan özellik (maaş 15.000–80.000) küçüğü (yaş 20–65) ezer.

### Üç yöntemin formülleri

**Min-Maks (Enk-Enb)** → çıktı \[0, 1\]

```latex
X^{*} = \frac{X - X_{enk}}{X_{enb} - X_{enk}}
```

**Z-Skor** → ortalama 0, std 1; değerler çoğunlukla −3 ile +3 arası

```latex
X^{*} = \frac{X - \bar{X}}{s}, \qquad s = \sqrt{\frac{\sum (X - \bar{X})^{2}}{n - 1}}
```

**Ondalık ölçekleme** → çıktı (−1, +1); j, max|X\*| < 1 yapan en küçük tam sayı

```latex
X^{*} = \frac{X}{10^{j}}
```

**Mantığı:**

- **Min-maks:** "Bu değer, en küçükten en büyüğe giden yolun yüzde kaçında?" En küçük 0, en büyük 1 olur.
- **Z-skor:** "Bu değer ortalamadan kaç standart sapma uzakta?" Negatif = ortalamanın altı.
- **Ondalık:** "Virgülü, en büyük sayının basamak sayısı kadar sola kaydır." 472 → 3 basamak → 1000'e böl.

### Çözümlü örnek: X = 251, 148, 166, 244, 472, 356, 379

**Min-maks:** X\_enk = 148, X\_enb = 472 → payda = 472 − 148 = 324

| X | Hesap | X\* |
| --- | --- | --- |
| 251 | 103 / 324 | 0,318 |
| 148 | 0 / 324 | 0 |
| 166 | 18 / 324 | 0,056 |
| 244 | 96 / 324 | 0,296 |
| 472 | 324 / 324 | 1 |
| 356 | 208 / 324 | 0,642 |
| 379 | 231 / 324 | 0,713 |

**Z-skor, adım 1 — ortalama:** 2016 / 7 = **288**

**Adım 2 — standart sapma (örneklem, n − 1):**

| X | X − X̄ | (X − X̄)² |
| --- | --- | --- |
| 251 | −37 | 1.369 |
| 148 | −140 | 19.600 |
| 166 | −122 | 14.884 |
| 244 | −44 | 1.936 |
| 472 | 184 | 33.856 |
| 356 | 68 | 4.624 |
| 379 | 91 | 8.281 |
| Toplam | 0 | 84.550 |

s = √(84.550 / 6) = √14.091,67 ≈ **118,71**

**Adım 3 — dönüştür:**

| X | Hesap | X\* |
| --- | --- | --- |
| 251 | −37 / 118,71 | −0,312 |
| 148 | −140 / 118,71 | −1,179 |
| 166 | −122 / 118,71 | −1,028 |
| 244 | −44 / 118,71 | −0,371 |
| 472 | 184 / 118,71 | 1,550 |
| 356 | 68 / 118,71 | 0,573 |
| 379 | 91 / 118,71 | 0,767 |

Yorum: 148, ortalamanın 1,18 std **altında**; 472, 1,55 std **üstünde**. Kontrol: X − X̄ sütununun toplamı her zaman 0 çıkar; çıkmıyorsa ortalamayı yanlış hesaplamışsındır.

**Ondalık:** En büyük mutlak değer 472 → 3 basamak → j = 3 → hepsi 1000'e bölünür: 0,251 · 0,148 · 0,166 · 0,244 · 0,472 · 0,356 · 0,379. Negatifte de çalışır: −986 ile 917 arası → j = 3 → −0,986 ile 0,917.

### Üç yöntemin karşılaştırması

| X | Min-maks | Z-skor | Ondalık |
| --- | --- | --- | --- |
| 148 | 0 | −1,179 | 0,148 |
| 166 | 0,056 | −1,028 | 0,166 |
| 244 | 0,296 | −0,371 | 0,244 |
| 251 | 0,318 | −0,312 | 0,251 |
| 356 | 0,642 | 0,573 | 0,356 |
| 379 | 0,713 | 0,767 | 0,379 |
| 472 | 1 | 1,550 | 0,472 |

Üçü de **doğrusal dönüşümdür**: sıralamayı ve göreli mesafeleri korur, yalnızca ölçek değişir.

### Hangisi ne zaman?

| Durum | Öneri |
| --- | --- |
| Kesin sınırlı aralık gerekiyorsa (YSA girdisi, görüntü pikseli) | Min-maks |
| Veride aykırı değer var veya min-maks bilinmiyorsa | Z-skor (uygulamada en çok kullanılan) |
| Hızlı, basit, yorumlanabilir ölçek | Ondalık ölçekleme |

**Min-maksın zayıflığı:** Aykırı değere çok duyarlı. 472 yerine hatalı 4720 olsaydı diğer tüm değerler 0'a yığılırdı. Ayrıca yeni gelen veri eski aralığın dışındaysa sonuç \[0, 1\] dışına taşar.

**Tekrar hatırlatma:** Z-skor 0–1 arası **değildir** (kitap hatası); 379 için doğru değer **0,767** (kitapta 0,770).

## Python kütüphaneleri: NumPy, Pandas, scikit-learn

NumPy hesaplar, Pandas tabloyu yönetir, scikit-learn hazır veri seti ve dönüştürücü verir. Her kodun altında **değişkenler** ve **fonksiyonlar** tablosu var.

| Kütüphane | Kısaltma | Ne için |
| --- | --- | --- |
| NumPy | np | Sayı dizisi, hızlı matematik |
| Pandas | pd | Tablo (DataFrame): okuma, temizleme, birleştirme |
| scikit-learn | sklearn | Veri seti yükleme, ölçekleme, eksik doldurma |

**scikit-learn kalıbı:** fit = öğren (min/max, ortalama/std hesapla) · transform = uygula · fit\_transform = ikisi birden.

### 1. NumPy

```python
import numpy as np

X = np.array([251, 148, 166, 244, 472, 356, 379])
buyukler = X[X > 300]
X_minmax = (X - X.min()) / (X.max() - X.min())
X_z = (X - X.mean()) / X.std(ddof=1)
j = len(str(int(np.abs(X).max())))
X_ondalik = X / 10**j

M = np.array([[1, 2, 3], [4, 5, 6]])
sutun_ort = M.mean(axis=0)
satir_ort = M.mean(axis=1)
```

| Değişken | Ne tutar | Sonuç |
| --- | --- | --- |
| X | Ham veri dizisi (ndarray) | \[251 148 … 379\] |
| buyukler | 300'den büyük elemanlar | \[472 356 379\] |
| X\_minmax | Min-maks sonucu | 0 … 1 arası |
| X\_z | Z-skor sonucu (kitaptaki n−1) | −1,179 … 1,550 |
| j | En büyük sayının basamak sayısı | 3 |
| X\_ondalik | Ondalık ölçekleme sonucu | 0,148 … 0,472 |
| M | 2 satır × 3 sütun matris | — |
| sutun\_ort | Her sütunun ortalaması | \[2.5 3.5 4.5\] |
| satir\_ort | Her satırın ortalaması | \[2. 5.\] |

| Fonksiyon / ifade | Ne yapar | Not |
| --- | --- | --- |
| np.array(liste) | Listeyi NumPy dizisine çevirir | Toplu matematik için şart |
| X\[X > 300\] | Boolean maske: koşulu sağlayanları seçer | Döngüsüz filtre |
| X.min() / X.max() | En küçük / en büyük değer | — |
| X.mean() | Ortalama | — |
| X.std(ddof=1) | Standart sapma | ddof=1 → n−1 (örneklem). **Varsayılan ddof=0 → n** |
| np.abs(X) | Mutlak değer | Negatifler için |
| 10\*\*j | 10 üzeri j | Ondalık ölçekleme paydası |
| M.mean(axis=0) | Sütun boyunca hesap | axis=0 = aşağı in |
| M.mean(axis=1) | Satır boyunca hesap | axis=1 = sağa git |

### 2. Pandas: okuma ve seçme

```python
import pandas as pd

df = pd.read_csv("A_dukkan_kasa_satislari.csv", sep=";", decimal=",")
df.head()
df.info()
df.describe()
secim1 = df.loc[0:4, ["urun", "tutar"]]
secim2 = df.iloc[0:5, 0:2]
pahali = df[df["tutar"] > 500]
```

| Değişken | Ne tutar |
| --- | --- |
| df | Tüm tablo (DataFrame); satır = nesne, sütun = özellik |
| df\["tutar"\] | Tek sütun (Series) |
| secim1 | 0–4 etiketli satırlar, urun ve tutar sütunları |
| secim2 | İlk 5 satır, ilk 2 sütun |
| pahali | Tutarı 500'den büyük satırlar |

| Fonksiyon | Ne yapar | Önemli parametre |
| --- | --- | --- |
| pd.read\_csv() | CSV dosyasını tabloya okur | sep=";" ayırıcı, decimal="," Türkçe ondalık |
| pd.read\_excel() | Excel okur | sheet\_name="metadata" belirli sayfa |
| df.head(n) | İlk n satır (varsayılan 5) | — |
| df.info() | Sütun tipleri + dolu değer sayısı | Eksik veriyi de gösterir |
| df.describe() | Sayısal sütunların min, max, ortalama, std, çeyrekleri | .T ile satır-sütun çevrilir |
| df.loc\[satır, sütun\] | **İsimle** seçim | Bitiş dahil |
| df.iloc\[satır, sütun\] | **Sıra numarasıyla** seçim (i = index) | Bitiş hariç |

### 3. EDA kontrol listesi

```python
from sklearn.datasets import load_iris

iris = load_iris(as_frame=True)
df = iris.frame
y = df["target"]

df.shape
df.columns.tolist()
df.select_dtypes(include="number")
df.select_dtypes(include=["object", "category"])
df.isnull().sum()
y.nunique()
y.value_counts(normalize=True)
df.describe().T[["min", "max"]]
df.corr().abs()
```

| Değişken | Ne tutar |
| --- | --- |
| iris | Veri seti paketi (data, target, frame, feature\_names) |
| df | Özellikler + hedef birlikte tablo |
| y | Hedef değişken (tahmin edilecek sütun) |

| Fonksiyon | EDA sorusu | Döndürür |
| --- | --- | --- |
| load\_iris(as\_frame=True) | Veriyi yükler | as\_frame=True → Pandas tablosu |
| df.shape | 1–2: gözlem, özellik sayısı | (150, 5) |
| df.columns.tolist() | 3: özellik isimleri | Liste |
| df.select\_dtypes(include="number") | 4: sayısal sütunlar | Alt tablo |
| df.select\_dtypes(include=\["object","category"\]) | 5: kategorik sütunlar | Alt tablo |
| df.isnull().sum() | 6: sütun başına eksik sayısı | Series |
| y.nunique() | 8: hedefin farklı değer sayısı | 3 |
| y.value\_counts(normalize=True) | 9: sınıf dengesi | Oranlar (normalize=True → yüzde) |
| df.describe().T\[\["min","max"\]\] | 10: aralıklar benzer mi | Min-max tablosu |
| df.corr().abs() | 11: korelasyon | Korelasyon matrisi (mutlak) |

| Yükleme fonksiyonu | Veri seti | Not |
| --- | --- | --- |
| load\_iris / load\_wine / load\_breast\_cancer | Iris, Wine, Breast Cancer | load\_ = paketle gelir |
| fetch\_california\_housing | California Housing | fetch\_ = indirilir |
| fetch\_openml("titanic", version=1) | Titanic | OpenML'den |
| fetch\_openml("mnist\_784", version=1) | MNIST | 70.000 görüntü |
| fetch\_20newsgroups(subset="train", categories=\[…\]) | 20 Newsgroups | Metin; random\_state=42 sabit karıştırma |

### 4. Eksik veri

```python
import numpy as np
import pandas as pd
from sklearn.impute import SimpleImputer

veri = pd.DataFrame({"yas": [25, np.nan, 40, 35, np.nan],
                     "sehir": ["Ankara", "İzmir", np.nan, "Ankara", "Ankara"]})

eksik = veri.isnull().sum()
silinmis = veri.dropna()
veri["yas"] = veri["yas"].fillna(veri["yas"].median())
veri["sehir"] = veri["sehir"].fillna(veri["sehir"].mode()[0])

imp = SimpleImputer(strategy="median")
veri[["yas"]] = imp.fit_transform(veri[["yas"]])

df["kira"] = df.groupby("mahalle")["kira"].transform(lambda s: s.fillna(s.mean()))
```

| Değişken | Ne tutar |
| --- | --- |
| veri | Eksik içeren örnek tablo |
| np.nan | Eksik değer işareti (Not a Number) |
| eksik | Sütun başına eksik sayısı (yas: 2, sehir: 1) |
| silinmis | Eksik satırları atılmış tablo (2 satır kalır) |
| imp | Medyanla dolduran araç |
| s | groupby içinde her grubun kira sütunu |

| Fonksiyon | Ne yapar | Ne zaman |
| --- | --- | --- |
| isnull().sum() | Eksikleri sayar | Önce tespit |
| dropna() | Eksik satırı siler | Eksik az ise |
| fillna(değer) | Eksiği verilen değerle doldurur | — |
| median() | Medyan | Sayısal, aykırı değer varsa |
| mode()\[0\] | Mod (en sık değer); liste döner, ilki alınır | **Kategorik** sütun |
| SimpleImputer(strategy=…) | Hazır doldurucu: "mean", "median", "most\_frequent", "constant" | — |
| groupby("mahalle") | Satırları gruba ayırır | Sınıf ortalaması |
| transform(f) | Her gruba f uygular, orijinal boyutta döner | Gruba göre doldurma |

### 5. Bölmeleme ve histogram

```python
X = pd.Series([4, 8, 15, 21, 21, 24, 25, 28, 34])
bolme = pd.qcut(X, q=3, labels=False)
X_duz = X.groupby(bolme).transform("mean")
araliklar = pd.cut(X, bins=3)
histogram = araliklar.value_counts().sort_index()
```

| Değişken | Ne tutar | Sonuç |
| --- | --- | --- |
| X | Sıralı örnek veri | — |
| bolme | Her elemanın bölme numarası | 0,0,0,1,1,1,2,2,2 |
| X\_duz | Bölme ortalamasıyla düzeltilmiş veri | 9,9,9,22,22,22,29,29,29 |
| araliklar | Eşit genişlikte aralık etiketleri | — |
| histogram | Her aralıkta kaç eleman var | — |

| Fonksiyon | Ne yapar | Akılda kalsın |
| --- | --- | --- |
| pd.qcut(X, q=3) | **Eşit frekans**: her bölmede eşit eleman | q = quantile, kalabalığı eşit böl |
| pd.cut(X, bins=3) | **Eşit genişlik**: aralık uzunlukları eşit | Cetvelle eşit böl |
| labels=False | Etiket yerine 0,1,2 numara verir | — |
| value\_counts() | Her değerden kaç tane | Histogramın sayıları |

### 6. Tutarsızlık ve tekrar

```python
df["urun"] = df["urun"].str.strip().str.lower()
df["cinsiyet"] = df["cinsiyet"].replace({"E": "Erkek", "K": "Kadın", 1: "Erkek", 0: "Kadın"})
df["tutar"] = pd.to_numeric(df["tutar"], errors="coerce")
hatali = df[df["tutar"] != df["adet"] * df["birim_fiyat"]]
tekrar = df.duplicated().sum()
df = df.drop_duplicates()
```

| Değişken | Ne tutar |
| --- | --- |
| hatali | tutar ≠ adet × birim fiyat olan (tutarsız) satırlar |
| tekrar | Tekrarlanan satır sayısı |

| Fonksiyon | Ne yapar |
| --- | --- |
| str.strip() | Baştaki/sondaki boşluğu siler ("pestil " → "pestil") |
| str.lower() | Küçük harfe çevirir ("PESTİL" → "pestil") |
| replace({eski: yeni}) | Kodları tek standarda eşler (E/K, 0/1 → Erkek/Kadın) |
| pd.to\_numeric(errors="coerce") | Metni sayıya çevirir; çevrilemeyeni NaN yapar |
| duplicated() | Her satır için "tekrar mı?" True/False |
| drop\_duplicates() | Tekrarları siler |

### 7. Birleştirme

```python
B = B.rename(columns={"customer_id": "musteri_id", "amount": "tutar"})
tum = pd.concat([A, B], ignore_index=True)
tum = tum.merge(D, on="ilce", how="left")
korelasyon = tum[["tutar", "tutar_eur"]].corr()
```

| Değişken | Ne tutar |
| --- | --- |
| A, B | Dükkan ve e-ticaret satış tabloları |
| D | İlçe referans tablosu (mesafe, rakım) |
| tum | Birleşik satış tablosu |
| korelasyon | İki sütunun korelasyonu; \~1,0 ise biri fazlalıktır |

| Fonksiyon | Ne yapar | Konu karşılığı |
| --- | --- | --- |
| rename(columns={…}) | Sütun adını değiştirir | Şema eşleştirme |
| pd.concat(\[A, B\]) | **Alt alta** ekler (satır) | Aynı yapıdaki kaynakları toplama |
| ignore\_index=True | Satır numaralarını baştan verir | — |
| merge(D, on="ilce", how="left") | **Yan yana** ekler (sütun), SQL JOIN | Referans bilgisi ekleme |
| how="left" | Sol tablonun tüm satırlarını korur | — |
| corr() | Korelasyon matrisi | Veri fazlalığı tespiti |

### 8. İndirgeme

```python
kup = tum.pivot_table(index="ilce", columns="urun", values="tutar", aggfunc="sum")
yillik = tum.groupby(["yil", "ilce"])["tutar"].sum()
ornek = tum.sample(frac=0.10, random_state=42)
tabakali = tum.groupby("ilce").sample(frac=0.10, random_state=42)
tum.to_csv("temiz.csv", index=False)
tum.to_csv("temiz.csv.gz", index=False, compression="gzip")
tum.to_parquet("temiz.parquet")
```

| Değişken | Ne tutar |
| --- | --- |
| kup | İlçe × ürün toplam satış tablosu (veri küpü) |
| yillik | Yıl ve ilçe bazında toplam (roll-up) |
| ornek | %10 basit rastgele örnek |
| tabakali | Her ilçeden ayrı %10 (tabakalı örnek) |

| Fonksiyon | Ne yapar | Parametre |
| --- | --- | --- |
| pivot\_table() | Çapraz özet tablo (OLAP küpü) | index=satır, columns=sütun, values=değer, aggfunc="sum" |
| groupby(\[...\]).sum() | Gruplara göre toplar | Roll-up |
| sample(frac=0.10) | Rastgele %10 seçer | random\_state=42 → her çalıştırmada aynı sonuç |
| groupby("ilce").sample() | Her gruptan ayrı örnek | Tabakalı örnekleme |
| to\_csv(compression="gzip") | Sıkıştırılmış CSV yazar | Kayıpsız |
| to\_parquet() | Sütun bazlı ikili format | Kayıpsız, genelde en küçük |

### 9. Dönüştürme

```python
from sklearn.preprocessing import MinMaxScaler, StandardScaler

df = pd.DataFrame({"X": [251, 148, 166, 244, 472, 356, 379]})
df["minmax"] = MinMaxScaler().fit_transform(df[["X"]])
df["z_kitap"] = (df["X"] - df["X"].mean()) / df["X"].std(ddof=1)
df["z_sklearn"] = StandardScaler().fit_transform(df[["X"]])
j = int(np.ceil(np.log10(df["X"].abs().max() + 1)))
df["ondalik"] = df["X"] / 10**j

df["yas_grubu"] = pd.cut(df["yas"], bins=[0, 30, 50, 120], labels=["genç", "orta", "yaşlı"])
df["tarih"] = pd.to_datetime(df["tarih"], dayfirst=True)
df["ay"] = df["tarih"].dt.month
df["ceyrek"] = df["tarih"].dt.quarter
df["kg_basi_fiyat"] = df["tutar"] / df["agirlik_kg"]
df["gurbetci"] = (df["ulke"] != "Türkiye").astype(int)
```

| Değişken | Ne tutar | 472 için |
| --- | --- | --- |
| minmax | Min-maks sonucu | 1 |
| z\_kitap | Z-skor, n−1 (kitap) | 1,550 |
| z\_sklearn | Z-skor, n (StandardScaler) | 1,674 |
| j | Basamak sayısı | 3 |
| ondalik | Ondalık ölçekleme | 0,472 |
| yas\_grubu | Genelleme: yaş → kategori | — |
| ay, ceyrek | Tarihten türetilen parçalar | — |
| kg\_basi\_fiyat | Özellik oluşturma: tutar / kg | — |
| gurbetci | İkili özellik: yurt dışı = 1 | — |

| Fonksiyon | Ne yapar | Not |
| --- | --- | --- |
| MinMaxScaler() | \[0, 1\] ölçekler | fit min/max'ı öğrenir |
| StandardScaler() | Z-skor | **n'e böler** → kitaptan farklı sonuç |
| df\[\["X"\]\] | Tek sütunu tablo (2 boyut) olarak verir | sklearn hep 2 boyut ister; df\["X"\] 1 boyut |
| np.log10(x) | 10 tabanında logaritma | ceil ile yukarı yuvarlayınca basamak sayısı |
| np.ceil() | Yukarı yuvarlar | 2,67 → 3 |
| pd.cut(bins, labels) | Sayıyı aralığa göre kategoriye çevirir | Genelleme / kesikleştirme |
| pd.to\_datetime(dayfirst=True) | Metni tarihe çevirir | Türkçe gün.ay.yıl |
| .dt.month / .dt.quarter | Ay / çeyrek | Tarih → ay/çeyrek genellemesi |
| astype(int) | True/False → 1/0 | İkili değişken üretir |

**En sık hata:** std'nin bölündüğü sayı. Pandas .std() → n−1 · NumPy np.std() ve StandardScaler → n.

**R (kitap):** clusterSim paketi, data.Normalization(x, type="n4") = min-maks, type="n1" = z-skor.

## Pestil & Köme lab senaryosu

Lab, 2. haftanın tüm teorisini tek bir kurgusal vakada uygulatıyor: üç kirli kaynaktan **tek, temiz, analize hazır veri seti** üretmek. Sınavda "bu durumda hangi işlemi yaparsın?" tipi senaryo sorusu buradan gelebilir.

**Senaryo:** Gümüşhane çarşısındaki kurgusal aile işletmesi pestil, köme, dut pekmezi, kuşburnu marmelatı satıyor. İki kanal: çarşı dükkanı ve e-ticaret pazaryeri. Ürünler 6 ilçeden (Merkez, Torul, Kürtün, Kelkit, Köse, Şiran) geliyor. Müşterilerin önemli kısmı İstanbul, Ankara, Kocaeli, Bursa ve Almanya'daki Gümüşhaneliler. Dönem: Ocak 2024 – Eylül 2025.

**İşletmenin soruları:** Hangi ilçeden, hangi üründen, hangi ayda ne kadar satıyoruz? Gurbetçi müşteriler yerel müşterilerden farklı mı? Kargo mesafesi memnuniyeti etkiliyor mu?

| Dosya | Kaynak | Not |
| --- | --- | --- |
| A\_dukkan\_kasa\_satislari.csv | Dükkan kasa yazılımı | Ayırıcı ;, ondalık , (Türkçe Excel) |
| B\_eticaret\_siparisleri.xlsx | Pazaryeri dışa aktarımı | İngilizce sütunlar; metadata sayfası okunmalı |
| C\_uretici\_kayitlari.csv | Üretici/kooperatif kayıt defteri | Ayırıcı ; |
| D\_ilce\_referans\_tablosu.csv | Dış kaynak | Temiz kabul edilir; düzeltmede referans |

### Görevler ve bağlı olduğu konu

| Görev | Ne isteniyor | Bağlı konu |
| --- | --- | --- |
| 1. Değişken tipleri | Her sütunu 6 tipten birine ata; aralıklı/oranlı ayrımını gerekçelendir (sıcaklık, rakım, tarih ↔ ağırlık, tutar, mesafe); işe yaramayan sütunları belirle | Değişken tipleri |
| 2. Temizleme | İmkânsız değerleri bul, gerçek-ama-sıra-dışıyı hatadan ayır; eksikliğin kaç farklı biçimde kodlandığını bul; her sütuna "göz ardı / tahmin" kararı; farklı yazımları birleştir; çelişkileri D tablosu ve kısıtlarla (yaş aralığı, tutar = adet × birim fiyat) düzelt | İstasyon 1 |
| 3. Birleştirme | A–B şema eşleştirme (metadata), B–C üretici kodu eşleştirme; varlık eşleştirme (aynı ad-soyadlı farklı kişilere dikkat); korelasyonla fazlalık; tekrar satırlar; para, ağırlık, puan, sıcaklık, cinsiyet, üyelik kodlaması farkları | İstasyon 2 |
| 4. İndirgeme | İlçe × ürün × ay küpü, yıl/çeyreğe roll-up; gereksiz özellikleri çıkar; CSV vs gzip vs Parquet boyutu; eşit genişlik ve eşit frekans histogram; %10 basit rastgele ve ilçeye göre tabakalı örnek ortalamalarını karşılaştır | İstasyon 3 |
| 5. Dönüştürme | Tutar, mesafe, rakım için min-maks, z-skor, ondalık; aykırıları temizlemeden önce/sonra min-maks farkı; ilçe → bölge, yaş → yaş grubu, tarih → ay/çeyrek/mevsim; en az 4 yeni özellik (gurbetçi, kg başı fiyat, bayram öncesi sipariş, enflasyondan arındırılmış tutar) | İstasyon 4 |

**Teslim:** Python temizleme kodu, son temiz veri seti ve her adımdaki karar ve sayıları içeren kısa rapor. Hocanın vurgusu: "Sildim" yetmez; **neyi, kaç tane, hangi kurala göre** sildiğini yaz.

**Mantığı (sınav için):**

- "Boş hücre tek biçim değildir": eksik veri boşluk, "NA", "-", "?", 0 veya 999 gibi farklı kodlarla gelebilir. Önce hepsini NaN'a çevir, sonra say.
- "Her aykırı değer hata değildir": Almanya'ya giden 20 kg'lık sipariş sıra dışı ama gerçek olabilir; 500 yaşında müşteri ise imkânsızdır.
- Rakım ve sıcaklık **aralıklı** (sıfırı keyfi), tutar, ağırlık ve mesafe **oranlı** (sıfır = yokluk).

## Soru-cevap

Her sorunun altında cevap ve gerekçe var. 1–2. bölüm repodaki sorular, 3–5. bölüm aynı konulardan ek pratik.

### 1. Hafta (repodan)

**S1. VM ile KDD aynı şey mi?**

- Cevap: Hayır.
- Neden: KDD sürecin tamamı; VM yalnızca 3. adım (model kurma ve değerlendirme).

**S2. VM'de analiz edilen veritabanının adı?**

- Cevap: Veri ambarı.
- Neden: İç + dış kaynak birleştirilip temizlenir. Alt kümesi data mart, tanımları metadata.

**S3. KDD'nin en uzun aşaması?**

- Cevap: Veri ön işleme.
- Neden: Çöp girer, çöp çıkar; özensiz hazırlık sürekli geri dönüş yaratır.

**S4. 5, 8, 15, 21, 22, 30 verisini iki bölüme ayırıp ortalama ile düzeltin.**

- Cevap: 9,33 · 9,33 · 9,33 | 24,33 · 24,33 · 24,33
- Çözüm: Bölüm 1 = (5 + 8 + 15) / 3 = 28 / 3 = 9,33. Bölüm 2 = (21 + 22 + 30) / 3 = 73 / 3 = 24,33.

**S5. Aynı veriyi sınır değerleriyle düzeltin.**

- Cevap: 5, 5, 15 | 21, 21, 30
- Çözüm: 8 → 5'e uzaklık 3, 15'e 7 → 5 olur. 22 → 21'e uzaklık 1, 30'a 8 → 21 olur.

**S6. Ön işlemede yapılan işlemler?**

- Cevap: Toplama/birleştirme · Temizleme (kayıp veri, gürültü) · Yeniden yapılandırma (normalizasyon, azaltma, dönüştürme).

**S7. Kümeleme ile sınıflandırma farkı?**

- Cevap: Sınıflandırmada sınıflar belli (denetimli, tahmin edici). Kümelemede sınıf yok (denetimsiz, tanımlayıcı).

**S8. Overfitting nedir?**

- Cevap: Modelin eğitim verisini ezberlemesi.
- Neden: Kurallar eğitimde çalışır, yeni veride çöker.

**S9. Geleneksel istatistik ile VM'nin farkları?**

- Cevap: İstatistik hipotezle başlar, eşitliği elle kurar, sayısal veri kullanır, kirli veriyi analizde ayıklar, kolay yorumlanır.
- VM hipotezsiz ve otomatiktir, metin/ses de kullanır, temiz veriyle çalışır, uzman yorumu gerekir.

**S10. Wald örneğinde DIKW katmanları?**

- Veri: delik sayısı ve konumu
- Enformasyon: deliklerin yoğunluk haritası
- Bilgi: boş görünen motor/kokpit ölümcül
- Bilgelik: zırhı deliksiz hayati bölgelere ekle

**S11. "Dondurma satışı artınca köpekbalığı saldırısı artıyor, dondurmayı yasaklayalım." Hata ne?**

- Cevap: Cum hoc ergo propter hoc (korelasyonu nedensellik sanmak).
- Neden: Karıştırıcı değişken sıcak hava; ikisini de artırır.

**S12. k-NN'de k çok büyük / çok küçük olursa?**

- Büyük k: farklı noktalar aynı sınıfa toplanır.
- Küçük k: aynı sınıftakiler ayrı sınıflara düşer, gürültüye duyarlılık artar.

### 2. Hafta (repodan)

**S1. İsimsel ile sıra gösteren farkı?**

- Cevap: İkisi de kategorik. Sıra gösterende sıralama anlamlı, ama kademeler arası mesafe eşit değil.

**S2. Kan grubu, harf notu, doğum yılı, aylık gelir, sigara içiyor mu, sınıftaki öğrenci sayısı?**

- Cevap: İsimsel · Sıra gösteren · Aralıklı · Oranlı · İkili · Tamsayılı.
- Neden doğum yılı aralıklı: 0 yılı "zamanın yokluğu" değil.

**S3. "20 °C, 10 °C'nin iki katı sıcak." Neden yanlış?**

- Cevap: Celsius aralıklı; 0 °C yokluk değil, oran alınamaz.
- Kanıt: 293 K / 283 K ≈ 1,035 → yalnızca %3,5 fark.

**S4. Veri hazırlamanın 4 süreci?**

- Cevap: Temizleme → Birleştirme → İndirgeme → Dönüştürme.

**S5. En sık kullanılan ve en güvenilir eksik veri stratejisi?**

- Cevap: Regresyon / karar ağacı ile en olası değeri tahmin etmek.
- Neden: Diğer özelliklerdeki bilgiden en çok yararlanır.

**S6. Kadın çalışanların boş "askerlik durumu" alanını ortalama/mod ile doldurmak doğru mu?**

- Cevap: Hayır.
- Neden: Eksik değil, uygulanamaz. "Uygulanamaz" kategorisi kullanılır.

**S7. Birleştirmede 3 sorun ve çözümü?**

- Şema uyuşmazlığı → meta veri
- Veri fazlalığı → korelasyon analizi
- Değer karmaşası → birim dönüşümü

**S8. Veri indirgeme yöntemleri?**

- Cevap: Veri küpü birleştirme · Boyut indirgeme · Veri sıkıştırma · Büyük sayıların indirgenmesi.

**S9. 20 özellikte kaç alt küme var? Neden sorun?**

- Cevap: 2²⁰ = 1.048.576.
- Neden: Hepsini denemek çok pahalı → ileriye seçme / geriye eleme gibi sezgisel yöntem.

**S10. Wrapper ile filter farkı?**

- Wrapper: algoritmanın kendisini kullanır; isabetli ama pahalı.
- Filter: algoritmadan bağımsız ölçüt; hızlı ama daha az isabetli.

**S11. 10, 21, 14, 29, 37, 45 değerlerini z-skor ile normalleştirin.**

- Cevap: −1,182 · −0,369 · −0,887 · 0,222 · 0,813 · 1,404
- Adım 1: Ortalama = 156 / 6 = 26
- Adım 2: Farklar −16, −5, −12, 3, 11, 19 → kareler 256, 25, 144, 9, 121, 361 → toplam 916
- Adım 3: s = √(916 / 5) = √183,2 ≈ 13,535
- Adım 4: Her farkı 13,535'e böl (−16 / 13,535 = −1,182)

**S12. Aynı veriyi min-maks ve ondalık ölçekleme ile normalleştirin.**

- Min-maks: 0 · 0,314 · 0,114 · 0,543 · 0,771 · 1 (min 10, max 45, payda 35; 21 → 11 / 35 = 0,314)
- Ondalık: 0,10 · 0,21 · 0,14 · 0,29 · 0,37 · 0,45 (en büyük 45 → 2 basamak → 100'e böl)

**S13. k-NN'de yaş (20–65) ve maaş (15.000–80.000) normalleştirilmezse?**

- Cevap: Mesafeyi maaş belirler, yaşın etkisi kaybolur.
- Çözüm: Normalleştirme ikisine eşit ağırlık verir.

**S14. Min-maksın en önemli zayıflığı?**

- Cevap: Aykırı değere duyarlı.
- Örnek: 472 yerine 4720 gelirse diğer tüm değerler 0'a yığılır. Yeni veri eski aralığın dışındaysa sonuç \[0, 1\] dışına taşar.

### 3. Ek pratik: kavram

**S1. Yorumlanması en zor tahmin algoritması?**

- Cevap: Yapay sinir ağları.

**S2. Genetik algoritma bir VM modeli midir?**

- Cevap: Hayır, eniyileme (optimizasyon) yöntemidir.

**S3. Veri ambarı ile data mart farkı?**

- Cevap: Ambar tüm işletmeyi kapsar; data mart tek bir bölüm/konuya yöneliktir.

**S4. "Ağustos'ta İç Anadolu satışı, geçen yılla karşılaştırmalı" sorusu hangi araçla cevaplanır?**

- Cevap: OLAP.
- Neden: Çok boyutlu (ürün × bölge × zaman) ama bilinen bir soru.

**S5. Birliktelik kuralı ile sıra örüntü farkı?**

- Birliktelik: birlikte alınanlar (bira–cips).
- Sıra örüntü: zaman sırası da var (çekiç → 3 ay içinde çivi).

**S6. Alt gruplardaki eğilimin gruplar birleşince tersine dönmesine ne denir?**

- Cevap: Simpson paradoksu.

**S7. "5 kez yazı geldi, şimdi tura gelir" hangi safsata?**

- Cevap: Kumarbaz safsatası.
- Neden: Bağımsız olaylar birbirini etkilemez.

**S8. Kayıpsız ve kayıplı sıkıştırmaya birer örnek?**

- Kayıpsız: ZIP, gzip, Parquet.
- Kayıplı: JPEG, MP3.

**S9. Parametrik veri indirgemeye örnek?**

- Cevap: Doğrusal regresyon (y = a + bx); verinin yerine yalnızca a ve b saklanır.

**S10. Rakım hangi değişken tipidir?**

- Cevap: Aralıklı.
- Neden: 0 m deniz seviyesi, keyfi referans; "yükseklik yok" demek değil.

**S11. Hangi veri seti regresyon içindir?**

- Cevap: California Housing (hedef sürekli: medyan konut fiyatı).

**S12. Sabit değerle (0, "Bilinmiyor") doldurmak neden tercih edilmez?**

- Cevap: Algoritmayı yanıltır; sabit, gerçek bir değerle çakışabilir.

### 4. Ek pratik: hesap

**S1. 12, 3, 22, 9, 30, 20 verisini iki bölüme ayırıp ortalama ve sınır değerleriyle düzeltin.**

- Cevap (ortalama): 8, 8, 8 | 24, 24, 24
- Cevap (sınır): 3, 12, 12 | 20, 20, 30
- Adım 1: Sırala → 3, 9, 12, 20, 22, 30
- Adım 2: Bölüm 1 = 24 / 3 = 8; Bölüm 2 = 72 / 3 = 24
- Adım 3: 9 → 3'e 6, 12'ye 3 uzak → 12. 22 → 20'ye 2, 30'a 8 uzak → 20

**S2. 20, 35, 50, 80 verisini min-maks, z-skor ve ondalık ile normalleştirin.**

| X | 20 | 35 | 50 | 80 |
| --- | --- | --- | --- | --- |
| Min-maks | 0 | 0,25 | 0,5 | 1 |
| Z-skor | −1,025 | −0,439 | 0,146 | 1,317 |
| Ondalık | 0,20 | 0,35 | 0,50 | 0,80 |

- Min-maks: payda 80 − 20 = 60; 35 → 15 / 60 = 0,25
- Z-skor: ortalama 185 / 4 = 46,25; farklar −26,25, −11,25, 3,75, 33,75; kareler toplamı 1.968,75; s = √(1.968,75 / 3) ≈ 25,617; 20 → −26,25 / 25,617 = −1,025
- Ondalık: en büyük 80 → 2 basamak → 100'e böl

**S3. −986 ile 917 arasındaki veri için ondalık ölçeklemede j kaçtır?**

- Cevap: 3.
- Neden: Mutlak en büyük 986 → 3 basamak → sonuç −0,986 ile 0,917 arası.

### 5. Ek pratik: Python

**S1. Eşit frekans bölmeleme fonksiyonu hangisi?**

- Cevap: pd.qcut(). Eşit genişlik için pd.cut().

**S2. StandardScaler ile elle hesaplanan z-skor neden farklı çıkar?**

- Cevap: StandardScaler n'e, kitap (ve Pandas .std()) n−1'e böler.

**S3. Kategorik sütundaki eksik hangi stratejiyle doldurulur?**

- Cevap: Mod → fillna(df\["s"\].mode()\[0\]) veya SimpleImputer(strategy="most\_frequent").

**S4. concat ile merge farkı?**

- concat: alt alta (satır) ekler.
- merge: anahtar üzerinden yan yana (sütun) ekler.

**S5. Sınıf dengesini yüzde olarak gösteren komut?**

- Cevap: y.value\_counts(normalize=True)

**S6. Türkçe Excel CSV'sini doğru okumak için iki parametre?**

- Cevap: sep=";" ve decimal=","

**S7. loc ile iloc farkı?**

- loc: isimle (etiket) seçer.
- iloc: sıra numarasıyla seçer.

**S8. MinMaxScaler'a neden df\[\["X"\]\] verilir, df\["X"\] değil?**

- Cevap: scikit-learn 2 boyutlu tablo ister; \[\["X"\]\] tablo, \["X"\] tek boyutlu Series verir.

## Son tekrar listesi

- VM önceden bilinmeyeni keşfeder; KDD'nin bir adımıdır.
- KDD: Amaç → Ön işlem → Model → Yorum → İzleme. En uzun aşama ön işleme (\~%80).
- Tahmin edici (regresyon, sınıflandırma) ↔ tanımlayıcı (kümeleme, birliktelik, sıra örüntü, özetleme).
- Denetimli = etiket var; denetimsiz = etiket yok.
- Korelasyon ≠ nedensellik; özet istatistikten önce görselleştir (Datasaurus, Anscombe).
- Kategorik: isimsel, ikili, sıra gösteren · Sürekli: tamsayılı, aralıklı, oranlı.
- Aralıklı ≠ oranlı: fark sıfırın "yokluk" olup olmamasıdır.
- Her boş hücre eksik veri değildir: uygulanamaz alanlara dikkat.
- Temizle → Birleştir → İndirge → Dönüştür.
- Min-maks \[0, 1\] · Z-skor ort. 0, std 1 (0–1 değil!) · Ondalık (−1, 1).
- k-NN, kümeleme ve YSA'da normalleştirme şart.
- Kod: Pandas .std() n−1, NumPy ve StandardScaler n; kategorik eksikte mod; load\_ hazır, fetch\_ indirilir.
