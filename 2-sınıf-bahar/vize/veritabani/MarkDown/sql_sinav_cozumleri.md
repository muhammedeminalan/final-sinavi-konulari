# SQL Sınav Soruları — Tam Çözüm

---

# 📄 DOSYA 1: Film & Oyuncu Soruları

---

## Soru 1 — Tabloları Oluşturma

**Soru:** Film ve Oyuncu isimli tabloları oluşturmak için gerekli SQL kodlarını yazınız. Tablolar arasındaki ilişkileri de oluşturunuz. İlişki türünü belirtiniz.

**Ne isteniyor:** Şemadaki 6 tabloyu (ulke, sehir, kategori, film, oyuncu, film_oyuncu) CREATE TABLE ile oluştur, foreign key ilişkilerini kur.

**İlişki Türleri:**
- ulke → sehir: 1-N (Bir ülkede birden fazla şehir olabilir)
- sehir → oyuncu: 1-N (Bir şehirde birden fazla oyuncu olabilir)
- kategori → film: 1-N (Bir kategoride birden fazla film olabilir)
- film ↔ oyuncu: N-N (Bir filmde birçok oyuncu, bir oyuncu birçok filmde oynayabilir → ara tablo: film_oyuncu)

**Cevap SQL Kodu:**

```sql
-- Önce bağımsız tablolar (FK almayan) oluşturulur

CREATE TABLE ulke (
    ulke_id INT PRIMARY KEY,
    ulke_ad VARCHAR(50)
);

CREATE TABLE kategori (
    kategori_id INT PRIMARY KEY,
    kategori_ad VARCHAR(50)
);

-- Sonra FK alan tablolar

CREATE TABLE sehir (
    sehir_id INT PRIMARY KEY,
    sehir_ad VARCHAR(50),
    ulke_id INT,
    FOREIGN KEY (ulke_id) REFERENCES ulke(ulke_id)
);

CREATE TABLE oyuncu (
    id INT PRIMARY KEY,
    ad VARCHAR(50),
    soyad VARCHAR(50),
    dogumtarihi DATE,
    sehir_id INT,
    FOREIGN KEY (sehir_id) REFERENCES sehir(sehir_id)
);

CREATE TABLE film (
    id INT PRIMARY KEY,
    ad VARCHAR(100),
    aciklama VARCHAR(200),
    sure INT,
    yil INT,
    kategori_id INT,
    FOREIGN KEY (kategori_id) REFERENCES kategori(kategori_id)
);

-- N-N ilişki için ara tablo
CREATE TABLE film_oyuncu (
    film_id INT,
    oyuncu_id INT,
    PRIMARY KEY (film_id, oyuncu_id),
    FOREIGN KEY (film_id) REFERENCES film(id),
    FOREIGN KEY (oyuncu_id) REFERENCES oyuncu(id)
);
```

**Örnek Verilerin Eklenmesi:**

```sql
INSERT INTO ulke VALUES (1, 'Türkiye');
INSERT INTO ulke VALUES (2, 'ABD');

INSERT INTO kategori VALUES (1, 'Korku');
INSERT INTO kategori VALUES (2, 'Komedi');

INSERT INTO sehir VALUES (1, 'İstanbul', 1);
INSERT INTO sehir VALUES (2, 'New York', 2);

INSERT INTO oyuncu VALUES (1, 'Ali', 'Veli', '2000-01-01', 1);
INSERT INTO oyuncu VALUES (2, 'Ahmet', 'Yaşar', '1980-01-01', 2);
INSERT INTO oyuncu VALUES (3, 'Mehmet', 'Ucan', '1985-05-01', 1);
INSERT INTO oyuncu VALUES (4, 'Mehmet', 'Yaşar', '1989-02-01', 2);

INSERT INTO film VALUES (1, 'Avrupa Yakası', 'Komedi Filmi', 120, 2008, 2);
INSERT INTO film VALUES (2, 'Testere', 'Korku Filmi', 120, 2006, 1);
INSERT INTO film VALUES (3, 'Batman', 'Korku Filmi', 150, 2008, 1);
INSERT INTO film VALUES (4, 'Recep İvedik', 'Komedi Filmi', 150, 2006, 2);

INSERT INTO film_oyuncu VALUES (1, 1);
INSERT INTO film_oyuncu VALUES (1, 2);
INSERT INTO film_oyuncu VALUES (2, 4);
INSERT INTO film_oyuncu VALUES (2, 2);
INSERT INTO film_oyuncu VALUES (2, 1);
INSERT INTO film_oyuncu VALUES (3, 4);
INSERT INTO film_oyuncu VALUES (4, 2);
```

---

## Soru 2.1

**Soru:** Filmler tablosundaki tüm veriyi getiren sorguyu yazınız.

**Ne isteniyor:** Film tablosundaki bütün satır ve sütunları getir.

```sql
SELECT * FROM film;
```

> `*` tüm sütunları getirir.

---

## Soru 2.2

**Soru:** Oyuncu tablosundaki kayıt sayısını getiren sorguyu yazınız.

**Ne isteniyor:** Toplam kaç oyuncu var, sayısını bul.

```sql
SELECT COUNT(*) FROM oyuncu;
```

> `COUNT(*)` satır sayısını döndürür. Sonuç: 4

---

## Soru 2.3

**Soru:** Oyuncu adını ve soyadını yan yana getiren sorguyu yazınız.

**Ne isteniyor:** ad ve soyad sütunlarını birleştirip tek sütunda göster.

```sql
SELECT CONCAT(ad, ' ', soyad) AS adsoyad FROM oyuncu;
```

> `CONCAT` fonksiyonu stringleri birleştirir. Araya boşluk koyduk.

---

## Soru 2.4

**Soru:** Hangi kategoride kaç film olduğunu gösteren sorguyu yazınız.

**Ne isteniyor:** Kategoriye göre grupla, her grupta kaç film var say.

```sql
SELECT kategori_id, COUNT(*) AS film_sayisi
FROM film
GROUP BY kategori_id;
```

> `GROUP BY` ile grupluyoruz, `COUNT(*)` ile her gruptaki sayıyı buluyoruz.

---

## Soru 2.5

**Soru:** Sehir tablosuna ülkesi "Türkiye" olan bir şehir ekleyen sorguyu yazınız.

**Ne isteniyor:** Türkiye'nin ulke_id'si 1, yeni bir şehir ekle.

```sql
INSERT INTO sehir VALUES (3, 'Ankara', 1);
```

> ulke_id = 1 Türkiye'ye karşılık geliyor.

---

## Soru 2.6

**Soru:** Tüm oyuncuları silen sorguyu yazınız.

**Ne isteniyor:** Oyuncu tablosundaki tüm satırları sil (tablo kalsın).

```sql
DELETE FROM oyuncu;
```

> `DELETE FROM` veriyi siler, tablo yapısı durur.

---

## Soru 2.7

**Soru:** Yıllara göre film süreleri toplamını bulan sorguyu yazınız.

**Ne isteniyor:** Yıla göre grupla, her yılın toplam film süresini bul.

```sql
SELECT yil, SUM(sure) AS toplam_sure
FROM film
GROUP BY yil;
```

> 2006 yılı: 120+150=270, 2008 yılı: 120+150=270

---

## Soru 2.8

**Soru:** Oyuncu tablosunu içindeki veriyle birlikte silen sorguyu yazınız.

**Ne isteniyor:** Tabloyu tamamen yok et (yapı + veri).

```sql
DROP TABLE oyuncu;
```

> `DROP TABLE` tabloyu komple siler. `DELETE` sadece veriyi siler, `DROP` her şeyi siler.

---

## Soru 2.9

**Soru:** Hiçbir filmde oynamamış oyuncuları bulan sorguyu yazınız.

**Ne isteniyor:** film_oyuncu tablosunda hiç kaydı olmayan oyuncuları bul.

```sql
SELECT * FROM oyuncu
WHERE id NOT IN (SELECT oyuncu_id FROM film_oyuncu);
```

> Alt sorgu film_oyuncu'daki tüm oyuncu id'lerini getirir. `NOT IN` ile bunların dışındakileri buluruz. Sonuç: Mehmet Ucan (id=3)

---

## Soru 2.10

**Soru:** Şehir ve ülke isimlerini yan yana getiren sorguyu yazınız.

**Ne isteniyor:** sehir ve ulke tablolarını JOIN ile birleştir.

```sql
SELECT s.sehir_ad, u.ulke_ad
FROM sehir s
INNER JOIN ulke u ON s.ulke_id = u.ulke_id;
```

> İki tabloyu ortak alan (ulke_id) üzerinden birleştiriyoruz.

---

## Soru 2.11

**Soru:** Tüm filmlerin süresini 100 yapan sorguyu yazınız.

**Ne isteniyor:** film tablosundaki tüm satırlarda sure sütununu 100 yap.

```sql
UPDATE film SET sure = 100;
```

> WHERE koşulu yok = tüm satırları günceller.

---

## Soru 2.12

**Soru:** Batman filminde oynayan oyuncuların ülkesini bulan sorguyu yazınız.

**Ne isteniyor:** film → film_oyuncu → oyuncu → sehir → ulke zincirini takip et.

```sql
SELECT DISTINCT u.ulke_ad
FROM film f
INNER JOIN film_oyuncu fo ON f.id = fo.film_id
INNER JOIN oyuncu o ON fo.oyuncu_id = o.id
INNER JOIN sehir s ON o.sehir_id = s.sehir_id
INNER JOIN ulke u ON s.ulke_id = u.ulke_id
WHERE f.ad = 'Batman';
```

> 4 tabloyu zincirleme JOIN ile bağlıyoruz. Batman'de oyuncu id=4 (Mehmet Yaşar, New York → ABD). `DISTINCT` tekrar eden ülkeleri elemeye yarar.

---
---

# 📄 DOSYA 2: Ürünler & Kategori Soruları

---

## Soru 1 — Tabloları Oluşturma

**Soru:** Urunler ve Kategori isimli tabloları oluşturmak için gerekli SQL kodlarını yazınız. İlişkileri de oluşturunuz.

**İlişki Türü:** kategori → urunler: 1-N (Bir kategoride birden fazla ürün olabilir)

**Cevap SQL Kodu:**

```sql
CREATE TABLE kategori (
    kat_id INT PRIMARY KEY,
    ad VARCHAR(50)
);

CREATE TABLE urunler (
    id INT PRIMARY KEY,
    urun VARCHAR(50),
    miktar INT,
    birim VARCHAR(20),
    gelis_tarih DATE,
    kat_id INT,
    FOREIGN KEY (kat_id) REFERENCES kategori(kat_id)
);
```

**Örnek Verilerin Eklenmesi:**

```sql
INSERT INTO kategori VALUES (1, 'Meyve');
INSERT INTO kategori VALUES (2, 'Sebze');
INSERT INTO kategori VALUES (3, 'Bakliyat');
INSERT INTO kategori VALUES (4, 'Şarküteri');

INSERT INTO urunler VALUES (1, 'Elma', 1000, 'Kg', '2017-01-01', 1);
INSERT INTO urunler VALUES (2, 'Domates', 5000, 'Kg', '2017-01-01', 2);
INSERT INTO urunler VALUES (3, 'Kıvırcık', 1000, 'adet', '2017-02-01', 2);
INSERT INTO urunler VALUES (4, 'Nohut', 500, 'Kg', '2017-02-01', 3);
INSERT INTO urunler VALUES (5, 'Makarna', 1000, 'Kg', '2017-03-01', NULL);
INSERT INTO urunler VALUES (6, 'Limon', 5000, 'adet', '2017-03-01', 2);
```

---

## Soru 2 — SQL Nedir?

**Soru:** SQL nedir? Ne işe yarar? SQL çeşitleri nelerdir?

**Cevap:**

**SQL (Structured Query Language):** Veritabanlarıyla iletişim kurmak için kullanılan standart bir dildir. Veri ekleme, silme, güncelleme, sorgulama ve veritabanı yapısını yönetme işlemlerini yapar.

**SQL Çeşitleri (Alt Dilleri):**

| Tür | Açıklama | Örnek Komutlar |
|-----|----------|----------------|
| **DDL** (Data Definition Language) | Tablo yapısını tanımlar | CREATE, ALTER, DROP, TRUNCATE |
| **DML** (Data Manipulation Language) | Veriyi yönetir | SELECT, INSERT, UPDATE, DELETE |
| **DCL** (Data Control Language) | Yetkilendirme yapar | GRANT, REVOKE |
| **TCL** (Transaction Control Language) | İşlem kontrolü | COMMIT, ROLLBACK |

---

## Soru 3.1

**Soru:** Urunler tablosundaki tüm veriyi getiren sorguyu yazınız.

```sql
SELECT * FROM urunler;
```

---

## Soru 3.2

**Soru:** Urunler tablosundaki kayıt sayısını getiren sorguyu yazınız.

```sql
SELECT COUNT(*) FROM urunler;
```

> Sonuç: 6

---

## Soru 3.3

**Soru:** Urunler tablosuna satici isimli varchar(30) veritipinde bir sütun ekleyen sorguyu yazınız.

**Ne isteniyor:** Mevcut tabloya yeni bir sütun ekle. Bu DDL (ALTER) işlemidir.

```sql
ALTER TABLE urunler ADD satici VARCHAR(30);
```

> `ALTER TABLE ... ADD` ile mevcut tabloya yeni sütun eklenir.

---

## Soru 3.4

**Soru:** Urunlerin adını, miktarını ve birimini getiren sorguyu yazınız.

```sql
SELECT urun, miktar, birim FROM urunler;
```

---

## Soru 3.5

**Soru:** Urun adını ve kategori adını yan yana getiren sorguyu yazınız.

**Ne isteniyor:** urunler ve kategori tablolarını JOIN ile birleştir.

```sql
SELECT u.urun, k.ad AS kategori_ad
FROM urunler u
INNER JOIN kategori k ON u.kat_id = k.kat_id;
```

> NOT: Makarna'nın kat_id'si NULL olduğu için INNER JOIN'de gelmez. Eğer Makarna da gelsin isteniyorsa LEFT JOIN kullanılır.

---

## Soru 3.6

**Soru:** Hangi kategoride kaç ürün olduğunu gösteren sorguyu yazınız.

```sql
SELECT kat_id, COUNT(*) AS urun_sayisi
FROM urunler
WHERE kat_id IS NOT NULL
GROUP BY kat_id;
```

> NULL kategorili ürünleri dahil etmemek için `WHERE kat_id IS NOT NULL` ekledik.

---

## Soru 3.7

**Soru:** Ürün adı, miktarı ve birimini tek bir sütunda getiren sorguyu yazınız.

**Ne isteniyor:** Üç sütunu birleştirip tek sütun yap.

```sql
SELECT CONCAT(urun, ' - ', miktar, ' ', birim) AS bilgi
FROM urunler;
```

> Örnek çıktı: "Elma - 1000 Kg"

---

## Soru 3.8

**Soru:** Urun tablosuna bir satır veri ekleyen sorguyu yazınız.

```sql
INSERT INTO urunler VALUES (7, 'Portakal', 2000, 'Kg', '2017-04-01', 1);
```

---

## Soru 3.9

**Soru:** Miktarı 500'den fazla olan ürünleri silen sorguyu yazınız.

```sql
DELETE FROM urunler WHERE miktar > 500;
```

> miktar > 500 olanlar silinir. Nohut (500) silinmez, çünkü 500'den büyük değil.

---

## Soru 3.10

**Soru:** Limonun birimini kg yapan sorguyu yazınız.

```sql
UPDATE urunler SET birim = 'Kg' WHERE urun = 'Limon';
```

---

## Soru 3.11

**Soru:** Ürünleri geliş tarihine göre büyükten küçüğe sıralayarak ilk 3 kaydı getiren sorguyu yazınız.

**Ne isteniyor:** Tarihe göre azalan sırala (en yeni önce), sadece 3 satır getir.

```sql
SELECT * FROM urunler
ORDER BY gelis_tarih DESC
LIMIT 3;
```

> `DESC` = azalan sıra (büyükten küçüğe). `LIMIT 3` = ilk 3 kayıt.
> 
> **NOT:** SQL Server kullanıyorsan LIMIT yerine `SELECT TOP 3` yazılır:
> `SELECT TOP 3 * FROM urunler ORDER BY gelis_tarih DESC;`

---

## Soru 3.12

**Soru:** Tüm ürünleri silen sorguyu yazınız.

```sql
DELETE FROM urunler;
```

> Tablo yapısı kalır, sadece veriler silinir.

---

## Soru 3.13

**Soru:** Kategorisi olmayan ürünlerin adlarının ilk 3 harfini getiren sorguyu yazınız.

**Ne isteniyor:** kat_id NULL olan ürünlerin adının ilk 3 harfini al.

```sql
SELECT LEFT(urun, 3) FROM urunler
WHERE kat_id IS NULL;
```

> `LEFT(urun, 3)` stringin soldan ilk 3 karakterini alır. Sonuç: "Mak" (Makarna)
>
> **Alternatif:** `SUBSTRING(urun, 1, 3)` de aynı işi yapar.

---

## Soru 3.14

**Soru:** Birimi kg olan ürünlerin toplam miktarını bulan sorguyu yazınız.

```sql
SELECT SUM(miktar) AS toplam_miktar
FROM urunler
WHERE birim = 'Kg';
```

> Elma(1000) + Domates(5000) + Nohut(500) + Makarna(1000) = 7500

---

## Soru 3.15

**Soru:** Ürünler tablosunu içindeki veriyle birlikte silen sorguyu yazınız.

```sql
DROP TABLE urunler;
```

> `DROP TABLE` = tablo + veri komple silinir. Geri dönüşü yoktur.

---

# 📌 Hızlı Özet — Sınavda Karıştırılmaması Gerekenler

| Komut | Ne Yapar |
|-------|----------|
| `DELETE FROM tablo` | Tüm veriyi siler, tablo yapısı kalır |
| `DROP TABLE tablo` | Tabloyu komple yok eder (yapı + veri) |
| `TRUNCATE TABLE tablo` | DELETE gibi veriyi siler ama daha hızlı (log tutmaz) |
| `ALTER TABLE ... ADD` | Tabloya yeni sütun ekler |
| `UPDATE ... SET` | Mevcut veriyi günceller |
| `INSERT INTO` | Yeni satır ekler |
| `INNER JOIN` | İki tabloda eşleşen kayıtları getirir |
| `LEFT JOIN` | Sol tablodaki tüm kayıtları getirir, eşleşmeyenler NULL olur |
| `GROUP BY` | Gruplama yapar, genelde COUNT/SUM ile kullanılır |
| `ORDER BY ... DESC` | Azalan sıralama |
| `LIMIT` | Sonuç sayısını sınırlar (SQL Server'da TOP kullanılır) |
| `CONCAT()` | Stringleri birleştirir |
| `LEFT()` | Stringin soldan N karakterini alır |
| `NOT IN (alt sorgu)` | Alt sorgudaki değerlerin dışındakileri getirir |
