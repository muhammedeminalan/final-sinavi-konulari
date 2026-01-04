# 🐍 ALGORİTMA VE PYTHON FİNAL ÖZETİ

---

## 📚 BÖLÜM 1: TEMEL KAVRAMLAR

### 🔹 Algoritma Nedir?
Bir problemi çözmek için izlenen **adım adım** talimatlar dizisidir.

**Örnek:** Çay Demleme Algoritması
1. Su kaynat
2. Çaydanlığa çay koy
3. Kaynar suyu ekle
4. 5 dakika bekle
5. Bardağa dök

---

## ⚡ BÖLÜM 2: DERLEYİCİ VE YORUMLAYICI (ÖNEMLİ!)

### 🔸 Derleyici (Compiler) Nedir?
- Kaynak kodu **tamamını** makine diline çevirir
- Çeviri işlemi **bir kerede** yapılır
- Çalıştırmadan önce tüm hatalar bulunur
- **Hızlı çalışır** (çünkü önceden derlenmiş)

**Örnekler:** C, C++, Java, Go

```
Kaynak Kod → [DERLEYİCİ] → Makine Kodu (.exe) → Çalıştır
```

### 🔸 Yorumlayıcı (Interpreter) Nedir?
- Kaynak kodu **satır satır** okur ve çalıştırır
- Her çalıştırmada yeniden yorumlar
- Hata bulunduğu satırda program durur
- **Daha yavaş** ama geliştirmesi kolay

**Örnekler:** Python, JavaScript, Ruby, PHP

```
Kaynak Kod → [YORUMLAYICI] → Satır satır çalıştır
```

### 📊 Karşılaştırma Tablosu

| Özellik | Derleyici | Yorumlayıcı |
|---------|-----------|-------------|
| Çeviri | Tamamını bir kerede | Satır satır |
| Hız | Hızlı | Yavaş |
| Hata tespiti | Derleme sırasında | Çalışma sırasında |
| Örnek | C, C++ | Python, JS |

---

## 🔢 BÖLÜM 3: PYTHON VERİ TİPLERİ

```python
# Sayılar
tam_sayi = 10          # int (tam sayı)
ondalik = 3.14         # float (ondalıklı)

# Metin
isim = "Ali"           # str (string/metin)

# Mantıksal
dogru_mu = True        # bool (True/False)

# Listeler
sayilar = [1, 2, 3]    # list (liste)
```

---

## 🎯 BÖLÜM 4: OPERATÖRLER

### Aritmetik Operatörler
```python
toplam = 10 + 5    # 15 (toplama)
fark = 10 - 5      # 5 (çıkarma)
carpim = 10 * 5    # 50 (çarpma)
bolum = 10 / 3     # 3.33 (bölme)
tam_bolum = 10 // 3  # 3 (tam bölme)
kalan = 10 % 3     # 1 (mod - kalan)
us = 2 ** 3        # 8 (üs alma)
```

### Karşılaştırma Operatörleri
```python
10 == 10   # True (eşit mi?)
10 != 5    # True (eşit değil mi?)
10 > 5     # True (büyük mü?)
10 < 5     # False (küçük mü?)
10 >= 10   # True (büyük eşit mi?)
10 <= 5    # False (küçük eşit mi?)
```

### Mantıksal Operatörler
```python
True and True    # True (ve)
True or False    # True (veya)
not True         # False (değil)
```

---

## ⚡ BÖLÜM 5: KISA DEVRE DEĞERLENDİRME (ÖNEMLİ!)

Python'da `and` ve `or` operatörleri **kısa devre** mantığı ile çalışır.

### 🔸 AND Kısa Devre
```python
# AND: İlk False gördüğünde durur, gerisine bakmaz

sonuc = False and print("Bu yazılmaz")
# False buldu, sağ tarafa bakmadı!

yas = 15
ehliyet_var = True
# İlk şart False olduğu için ikinciye bakılmaz
if yas >= 18 and ehliyet_var:
    print("Araba kullanabilir")
```

**Kural:** `False and (herhangi bir şey)` → Sonuç direkt **False**

### 🔸 OR Kısa Devre
```python
# OR: İlk True gördüğünde durur, gerisine bakmaz

sonuc = True or print("Bu yazılmaz")
# True buldu, sağ tarafa bakmadı!

vip_mi = True
bilet_var = False
# İlk şart True olduğu için ikinciye bakılmaz
if vip_mi or bilet_var:
    print("Giriş yapabilir")
```

**Kural:** `True or (herhangi bir şey)` → Sonuç direkt **True**

### 💡 Pratik Örnek
```python
# Sıfıra bölme hatasından korunma
sayi = 0
bolen = 0

# Kısa devre sayesinde bölme işlemi yapılmaz!
if bolen != 0 and sayi / bolen > 5:
    print("Büyük")
else:
    print("Bölme yapılamaz")
# bolen 0 olduğu için ilk şart False, ikinci şarta bakılmadı
```

---

## 🔀 BÖLÜM 6: IF YAPISI (KOŞUL İFADELERİ)

### 🔸 Basit if
```python
yas = 20

if yas >= 18:
    print("Reşitsiniz")
```

### 🔸 if-else
```python
not_ortalamasi = 45

if not_ortalamasi >= 50:
    print("Geçtiniz!")
else:
    print("Kaldınız!")
```

### 🔸 if-elif-else
```python
puan = 75

if puan >= 90:
    harf = "AA"
elif puan >= 80:
    harf = "BA"
elif puan >= 70:
    harf = "BB"
elif puan >= 60:
    harf = "CB"
elif puan >= 50:
    harf = "CC"
else:
    harf = "FF"

print(f"Harf notunuz: {harf}")
```

### 🔸 İç İçe if
```python
kullanici_adi = "admin"
sifre = "1234"

if kullanici_adi == "admin":
    if sifre == "1234":
        print("Giriş başarılı!")
    else:
        print("Şifre yanlış!")
else:
    print("Kullanıcı bulunamadı!")
```

---

## 🔄 BÖLÜM 7: MATCH-CASE (SWITCH-CASE) - ALIŞVERİŞ ÖRNEĞİ (ÖNEMLİ!)

Python 3.10+ ile gelen `match-case` yapısı (diğer dillerdeki switch-case):

### 🛒 Alışveriş Sistemi Örneği
```python
# Basit Alışveriş Menüsü
print("=== ALIŞVERİŞ SİSTEMİ ===")
print("1. Ürün Ekle")
print("2. Sepeti Görüntüle")
print("3. Ödeme Yap")
print("4. Çıkış")

secim = input("Seçiminiz: ")

match secim:
    case "1":
        print("Ürün ekleme sayfası açılıyor...")
    case "2":
        print("Sepetiniz görüntüleniyor...")
    case "3":
        print("Ödeme sayfasına yönlendiriliyorsunuz...")
    case "4":
        print("Güle güle!")
    case _:  # default (hiçbiri değilse)
        print("Geçersiz seçim!")
```

### 🛍️ Detaylı Alışveriş Sepeti Örneği
```python
# Alışveriş Sepeti Uygulaması
sepet = []
toplam_fiyat = 0

while True:
    print("\n=== MARKET ===")
    print("1. Elma (5 TL)")
    print("2. Ekmek (10 TL)")
    print("3. Süt (25 TL)")
    print("4. Peynir (50 TL)")
    print("5. Sepeti Gör")
    print("6. Ödeme ve Çıkış")
    
    secim = input("Seçiminiz: ")
    
    match secim:
        case "1":
            sepet.append("Elma")
            toplam_fiyat += 5
            print("✓ Elma sepete eklendi!")
        case "2":
            sepet.append("Ekmek")
            toplam_fiyat += 10
            print("✓ Ekmek sepete eklendi!")
        case "3":
            sepet.append("Süt")
            toplam_fiyat += 25
            print("✓ Süt sepete eklendi!")
        case "4":
            sepet.append("Peynir")
            toplam_fiyat += 50
            print("✓ Peynir sepete eklendi!")
        case "5":
            print(f"Sepetiniz: {sepet}")
            print(f"Toplam: {toplam_fiyat} TL")
        case "6":
            print("\n=== FİŞ ===")
            for urun in sepet:
                print(f"- {urun}")
            print(f"TOPLAM: {toplam_fiyat} TL")
            print("Teşekkürler!")
            break
        case _:
            print("❌ Geçersiz seçim!")
```

---

## 🔁 BÖLÜM 8: WHILE DÖNGÜSÜ (ÖNEMLİ!)

`while` döngüsü, koşul `True` olduğu sürece çalışır.

### 🔸 Temel Kullanım
```python
# 1'den 5'e kadar sayma
sayac = 1

while sayac <= 5:
    print(sayac)
    sayac += 1  # sayac = sayac + 1

# Çıktı: 1 2 3 4 5
```

### 🔸 Kullanıcıdan Şifre Alma
```python
dogru_sifre = "python123"
deneme = 3

while deneme > 0:
    girilen = input("Şifre: ")
    
    if girilen == dogru_sifre:
        print("Giriş başarılı!")
        break  # Döngüden çık
    else:
        deneme -= 1
        print(f"Yanlış! {deneme} hak kaldı.")

if deneme == 0:
    print("Hesap kilitlendi!")
```

### 🔸 Toplam Hesaplama
```python
# Kullanıcı 0 girene kadar sayıları topla
toplam = 0

while True:
    sayi = int(input("Sayı girin (çıkış: 0): "))
    
    if sayi == 0:
        break
    
    toplam += sayi

print(f"Toplam: {toplam}")
```

### 🔸 Sayı Tahmin Oyunu
```python
import random

gizli_sayi = random.randint(1, 100)
tahmin_sayisi = 0

print("1-100 arası bir sayı tuttum!")

while True:
    tahmin = int(input("Tahmininiz: "))
    tahmin_sayisi += 1
    
    if tahmin < gizli_sayi:
        print("Daha büyük!")
    elif tahmin > gizli_sayi:
        print("Daha küçük!")
    else:
        print(f"Tebrikler! {tahmin_sayisi} denemede buldunuz!")
        break
```

---

## 🔁 BÖLÜM 9: FOR DÖNGÜSÜ (ÖNEMLİ!)

`for` döngüsü, bir dizi/liste üzerinde gezinmek için kullanılır.

### 🔸 Temel Kullanım
```python
# Liste üzerinde gezinme
meyveler = ["elma", "armut", "muz"]

for meyve in meyveler:
    print(meyve)

# Çıktı:
# elma
# armut
# muz
```

### 🔸 range() ile Kullanım
```python
# 0'dan 4'e kadar (5 dahil değil)
for i in range(5):
    print(i)  # 0, 1, 2, 3, 4

# 1'den 5'e kadar
for i in range(1, 6):
    print(i)  # 1, 2, 3, 4, 5

# 0'dan 10'a 2'şer artarak
for i in range(0, 11, 2):
    print(i)  # 0, 2, 4, 6, 8, 10
```

### 🔸 Çarpım Tablosu
```python
sayi = 5

for i in range(1, 11):
    sonuc = sayi * i
    print(f"{sayi} x {i} = {sonuc}")
```

### 🔸 Toplam ve Ortalama
```python
notlar = [70, 85, 90, 65, 80]
toplam = 0

for nott in notlar:
    toplam += nott

ortalama = toplam / len(notlar)
print(f"Ortalama: {ortalama}")
```

### 🔸 String Üzerinde Gezinme
```python
kelime = "PYTHON"

for harf in kelime:
    print(harf)

# Çıktı: P Y T H O N (alt alta)
```

---

## 🔄 BÖLÜM 10: İÇ İÇE DÖNGÜLER (ÖNEMLİ!)

Bir döngünün içinde başka bir döngü kullanma.

### 🔸 Temel Örnek - Dikdörtgen Çizme
```python
# 4 satır, 5 sütun yıldız
satir_sayisi = 4
sutun_sayisi = 5

for satir in range(satir_sayisi):
    for sutun in range(sutun_sayisi):
        print("*", end="")
    print()  # Satır sonu

# Çıktı:
# *****
# *****
# *****
# *****
```

### 🔸 Çarpım Tablosu (1-10)
```python
for i in range(1, 11):
    for j in range(1, 11):
        sonuc = i * j
        print(f"{sonuc:4}", end="")  # 4 karakter genişlik
    print()
```

### ⭐ ASAL SAYI BULMA ÖRNEĞİ (ÇOK ÖNEMLİ!)
```python
# 2'den 50'ye kadar asal sayıları bul

print("2-50 arası asal sayılar:")

for sayi in range(2, 51):
    asal_mi = True  # Başta asal kabul et
    
    # 2'den sayının kareköküne kadar kontrol
    for bolen in range(2, sayi):
        if sayi % bolen == 0:  # Tam bölünüyorsa
            asal_mi = False   # Asal değil
            break             # Döngüden çık
    
    if asal_mi:
        print(sayi, end=" ")

# Çıktı: 2 3 5 7 11 13 17 19 23 29 31 37 41 43 47
```

### 🔸 Asal Sayı Kontrolü (Fonksiyonlu)
```python
def asal_mi(sayi):
    """Bir sayının asal olup olmadığını kontrol eder"""
    if sayi < 2:
        return False
    
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            return False  # Bölen bulundu, asal değil
    
    return True  # Hiç bölen bulunamadı, asal

# Test
test_sayisi = 17
if asal_mi(test_sayisi):
    print(f"{test_sayisi} asal sayıdır")
else:
    print(f"{test_sayisi} asal sayı değildir")
```

### 🔸 Üçgen Çizme
```python
# Yıldızlarla üçgen
satir_sayisi = 5

for i in range(1, satir_sayisi + 1):
    for j in range(i):
        print("*", end="")
    print()

# Çıktı:
# *
# **
# ***
# ****
# *****
```

---

## 📏 BÖLÜM 11: LEN() FONKSİYONU (ÖNEMLİ!)

`len()` fonksiyonu bir nesnenin **uzunluğunu** (eleman sayısını) döndürür.

### 🔸 String ile Kullanım
```python
isim = "Muhammed"
uzunluk = len(isim)
print(f"İsim {uzunluk} karakterdir")  # 8

# Boşluklar da sayılır
cumle = "Merhaba Dünya"
print(len(cumle))  # 13
```

### 🔸 Liste ile Kullanım
```python
ogrenciler = ["Ali", "Veli", "Ayşe", "Fatma"]
ogrenci_sayisi = len(ogrenciler)
print(f"Toplam {ogrenci_sayisi} öğrenci var")  # 4

# Boş liste kontrolü
sepet = []
if len(sepet) == 0:
    print("Sepet boş!")
```

### 🔸 Döngülerle Kullanım
```python
notlar = [70, 85, 90, 65, 80]

# Klasik for döngüsü ile indeksle erişim
for i in range(len(notlar)):
    print(f"{i+1}. not: {notlar[i]}")

# Ortalama hesaplama
toplam = sum(notlar)
ortalama = toplam / len(notlar)
print(f"Ortalama: {ortalama}")
```

### 🔸 Şifre Uzunluk Kontrolü
```python
sifre = input("Şifre belirleyin: ")

if len(sifre) < 6:
    print("Şifre en az 6 karakter olmalı!")
elif len(sifre) > 20:
    print("Şifre en fazla 20 karakter olabilir!")
else:
    print("Şifre kabul edildi!")
```

---

## 📋 BÖLÜM 12: LİSTELER (ÖNEMLİ!)

Listeler, birden fazla veriyi bir arada tutmak için kullanılır.

### 🔸 Liste Oluşturma
```python
# Boş liste
bos_liste = []

# Sayı listesi
sayilar = [1, 2, 3, 4, 5]

# String listesi
isimler = ["Ali", "Veli", "Ayşe"]

# Karışık liste
karisik = [1, "Ali", 3.14, True]
```

### 🔸 Liste Elemanlarına Erişim
```python
meyveler = ["elma", "armut", "muz", "çilek"]

print(meyveler[0])   # elma (ilk eleman)
print(meyveler[1])   # armut
print(meyveler[-1])  # çilek (son eleman)
print(meyveler[-2])  # muz (sondan ikinci)
```

### 🔸 Liste Dilimleme (Slicing)
```python
sayilar = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(sayilar[2:5])   # [2, 3, 4]
print(sayilar[:4])    # [0, 1, 2, 3]
print(sayilar[6:])    # [6, 7, 8, 9]
print(sayilar[::2])   # [0, 2, 4, 6, 8] (2'şer atlayarak)
```

### 🔸 Liste Metodları
```python
liste = [3, 1, 4, 1, 5]

# Eleman ekleme
liste.append(9)       # Sona ekler: [3, 1, 4, 1, 5, 9]
liste.insert(0, 2)    # İndekse ekler: [2, 3, 1, 4, 1, 5, 9]

# Eleman silme
liste.remove(1)       # İlk 1'i siler
liste.pop()           # Son elemanı siler ve döndürür
liste.pop(0)          # 0. indeksi siler

# Diğer metodlar
liste.sort()          # Sıralar
liste.reverse()       # Ters çevirir
liste.count(1)        # 1'in kaç kez geçtiği
liste.index(4)        # 4'ün indeksi
```

### ⭐ ASAL SAYILARI LİSTEYE EKLEME ÖRNEĞİ
```python
# 1-100 arası asal sayıları listeye ekle
asal_sayilar = []

for sayi in range(2, 101):
    asal_mi = True
    
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            asal_mi = False
            break
    
    if asal_mi:
        asal_sayilar.append(sayi)

print("Asal sayılar:", asal_sayilar)
print(f"Toplam {len(asal_sayilar)} asal sayı var")
```

### 🎮 ADAM ASMACA OYUNU (LİSTELERLE)
```python
import random

# Kelime listesi
kelimeler = ["python", "algoritma", "bilgisayar", "programlama", "klavye"]

# Rastgele kelime seç
gizli_kelime = random.choice(kelimeler)
kelime_uzunlugu = len(gizli_kelime)

# Tahmin edilen harfler (başta hepsi _ )
gorunen = ["_"] * kelime_uzunlugu

# Yanlış tahminler
yanlis_harfler = []
can = 6

print("=== ADAM ASMACA ===")
print(" ".join(gorunen))

while can > 0 and "_" in gorunen:
    tahmin = input("\nBir harf girin: ").lower()
    
    # Harf daha önce denendi mi?
    if tahmin in gorunen or tahmin in yanlis_harfler:
        print("Bu harfi zaten denediniz!")
        continue
    
    # Harf kelimede var mı?
    if tahmin in gizli_kelime:
        print("Doğru!")
        # Harfin tüm konumlarını bul
        for i in range(kelime_uzunlugu):
            if gizli_kelime[i] == tahmin:
                gorunen[i] = tahmin
    else:
        print("Yanlış!")
        yanlis_harfler.append(tahmin)
        can -= 1
    
    # Durumu göster
    print(" ".join(gorunen))
    print(f"Yanlış harfler: {yanlis_harfler}")
    print(f"Kalan can: {can}")

# Oyun sonu
if "_" not in gorunen:
    print(f"\n🎉 TEBRİKLER! Kelime: {gizli_kelime}")
else:
    print(f"\n💀 KAYBETTINIZ! Kelime: {gizli_kelime}")
```

---

## 🔧 BÖLÜM 13: FONKSİYONLAR (ÖNEMLİ!)

Fonksiyonlar, belirli bir görevi yapan ve tekrar kullanılabilir kod bloklarıdır.

### 🔸 Basit Fonksiyon
```python
def selamla():
    """Ekrana selam yazar"""
    print("Merhaba!")

# Fonksiyonu çağır
selamla()  # Çıktı: Merhaba!
```

### 🔸 Parametreli Fonksiyon
```python
def selamla_kisi(isim):
    """Kişiye özel selam verir"""
    print(f"Merhaba {isim}!")

selamla_kisi("Ali")    # Merhaba Ali!
selamla_kisi("Ayşe")   # Merhaba Ayşe!
```

### 🔸 Birden Fazla Parametre
```python
def toplama_yap(sayi1, sayi2):
    """İki sayıyı toplar"""
    sonuc = sayi1 + sayi2
    print(f"{sayi1} + {sayi2} = {sonuc}")

toplama_yap(5, 3)   # 5 + 3 = 8
toplama_yap(10, 20) # 10 + 20 = 30
```

### 🔸 Return (Değer Döndürme)
```python
def kare_al(sayi):
    """Sayının karesini döndürür"""
    return sayi * sayi

sonuc = kare_al(5)
print(sonuc)  # 25

# Direkt kullanım
print(kare_al(7))  # 49
```

### 🔸 Varsayılan Parametre
```python
def selamla(isim="Misafir"):
    """Varsayılan isimle selamlar"""
    print(f"Hoş geldin {isim}!")

selamla()         # Hoş geldin Misafir!
selamla("Ali")    # Hoş geldin Ali!
```

### 🔸 Çoklu Değer Döndürme
```python
def hesapla(sayi1, sayi2):
    """Toplam ve çarpımı döndürür"""
    toplam = sayi1 + sayi2
    carpim = sayi1 * sayi2
    return toplam, carpim

t, c = hesapla(4, 5)
print(f"Toplam: {t}, Çarpım: {c}")
# Toplam: 20, Çarpım: 20
```

### 🔸 Farklı Fonksiyon Örnekleri

#### Çift/Tek Kontrolü
```python
def cift_mi(sayi):
    """Sayının çift olup olmadığını kontrol eder"""
    if sayi % 2 == 0:
        return True
    else:
        return False

# Kullanım
print(cift_mi(4))   # True
print(cift_mi(7))   # False
```

#### Faktöriyel Hesaplama
```python
def faktoriyel(sayi):
    """Sayının faktöriyelini hesaplar"""
    sonuc = 1
    for i in range(1, sayi + 1):
        sonuc *= i  # sonuc = sonuc * i
    return sonuc

print(faktoriyel(5))  # 120 (5*4*3*2*1)
```

#### Asal Sayı Kontrolü (Fonksiyon)
```python
def asal_mi(sayi):
    """Sayının asal olup olmadığını kontrol eder"""
    if sayi < 2:
        return False
    
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            return False
    
    return True

# Test
for s in range(1, 20):
    if asal_mi(s):
        print(s, end=" ")
# Çıktı: 2 3 5 7 11 13 17 19
```

#### Liste Ortalaması
```python
def ortalama_bul(sayilar):
    """Liste ortalamasını hesaplar"""
    if len(sayilar) == 0:
        return 0
    
    toplam = sum(sayilar)
    ortalama = toplam / len(sayilar)
    return ortalama

notlar = [70, 85, 90, 65, 80]
print(f"Ortalama: {ortalama_bul(notlar)}")  # 78.0
```

#### En Büyük Sayıyı Bulma
```python
def en_buyuk_bul(liste):
    """Listedeki en büyük sayıyı bulur"""
    en_buyuk = liste[0]  # İlk elemanı en büyük kabul et
    
    for sayi in liste:
        if sayi > en_buyuk:
            en_buyuk = sayi
    
    return en_buyuk

sayilar = [3, 7, 2, 9, 5]
print(f"En büyük: {en_buyuk_bul(sayilar)}")  # 9
```

---

## 🔄 BÖLÜM 14: RECURSIVE (ÖZYINELEMELI) FONKSİYONLAR (ÖNEMLİ!)

Kendini çağıran fonksiyonlara **recursive (özyinelemeli)** fonksiyon denir.

### 🔸 Temel Mantık
```python
def geri_say(sayi):
    """Sayıdan geriye doğru sayar"""
    if sayi <= 0:  # Durma koşulu (BASE CASE)
        print("Bitti!")
        return
    
    print(sayi)
    geri_say(sayi - 1)  # Kendini çağır

geri_say(5)
# Çıktı: 5 4 3 2 1 Bitti!
```

### ⭐ Faktöriyel (Recursive)
```python
def faktoriyel(sayi):
    """
    Faktöriyel hesaplar (özyinelemeli)
    5! = 5 * 4 * 3 * 2 * 1 = 120
    """
    # Durma koşulu
    if sayi == 0 or sayi == 1:
        return 1
    
    # Kendini çağır
    return sayi * faktoriyel(sayi - 1)

# Nasıl çalışır:
# faktoriyel(5)
# = 5 * faktoriyel(4)
# = 5 * 4 * faktoriyel(3)
# = 5 * 4 * 3 * faktoriyel(2)
# = 5 * 4 * 3 * 2 * faktoriyel(1)
# = 5 * 4 * 3 * 2 * 1
# = 120

print(faktoriyel(5))  # 120
```

### ⭐ Fibonacci Serisi (Recursive)
```python
def fibonacci(n):
    """
    n. Fibonacci sayısını döndürür
    Seri: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...
    Her sayı önceki iki sayının toplamı
    """
    # Durma koşulları
    if n == 0:
        return 0
    if n == 1:
        return 1
    
    # Önceki iki sayının toplamı
    return fibonacci(n - 1) + fibonacci(n - 2)

# İlk 10 fibonacci sayısı
print("Fibonacci serisi:")
for i in range(10):
    print(fibonacci(i), end=" ")
# Çıktı: 0 1 1 2 3 5 8 13 21 34
```

### ⭐ Sayıların Toplamı (Recursive)
```python
def toplam_hesapla(sayi):
    """
    1'den n'e kadar sayıların toplamı
    Örnek: toplam(5) = 5 + 4 + 3 + 2 + 1 = 15
    """
    # Durma koşulu
    if sayi == 1:
        return 1
    
    # Kendini çağır
    return sayi + toplam_hesapla(sayi - 1)

print(toplam_hesapla(5))   # 15
print(toplam_hesapla(10))  # 55
```

### ⭐ Üs Alma (Recursive)
```python
def us_al(taban, us):
    """
    taban^us hesaplar
    Örnek: us_al(2, 3) = 2^3 = 8
    """
    # Durma koşulu
    if us == 0:
        return 1
    
    # Kendini çağır
    return taban * us_al(taban, us - 1)

print(us_al(2, 3))   # 8
print(us_al(5, 2))   # 25
print(us_al(3, 4))   # 81
```

### ⭐ Rakamlar Toplamı (Recursive)
```python
def rakam_toplami(sayi):
    """
    Bir sayının rakamlarının toplamı
    Örnek: 123 -> 1 + 2 + 3 = 6
    """
    # Durma koşulu (tek haneli sayı)
    if sayi < 10:
        return sayi
    
    # Son rakam + kalan rakamların toplamı
    son_rakam = sayi % 10
    kalan = sayi // 10
    return son_rakam + rakam_toplami(kalan)

print(rakam_toplami(123))   # 6
print(rakam_toplami(9876))  # 30
```

### ⭐ Liste Toplamı (Recursive)
```python
def liste_toplami(liste):
    """
    Liste elemanlarının toplamı (özyinelemeli)
    """
    # Durma koşulu (boş liste)
    if len(liste) == 0:
        return 0
    
    # İlk eleman + kalan elemanların toplamı
    return liste[0] + liste_toplami(liste[1:])

sayilar = [1, 2, 3, 4, 5]
print(liste_toplami(sayilar))  # 15
```

### ⭐ Palindrom Kontrolü (Recursive)
```python
def palindrom_mu(kelime):
    """
    Kelimenin palindrom olup olmadığını kontrol eder
    Palindrom: Tersten okunuşu aynı (aba, kazak, ana)
    """
    # Durma koşulu (0 veya 1 karakter)
    if len(kelime) <= 1:
        return True
    
    # İlk ve son harf eşit mi?
    if kelime[0] != kelime[-1]:
        return False
    
    # Ortadaki kısmı kontrol et
    return palindrom_mu(kelime[1:-1])

print(palindrom_mu("ana"))     # True
print(palindrom_mu("kazak"))   # True
print(palindrom_mu("python"))  # False
```

---

## 📝 ÖZET TABLO

| Konu | Açıklama |
|------|----------|
| Derleyici | Tüm kodu bir kerede makine diline çevirir |
| Yorumlayıcı | Kodu satır satır yorumlayarak çalıştırır |
| if-elif-else | Koşula göre farklı kod çalıştırır |
| match-case | Çoklu seçim yapısı (switch-case) |
| while | Koşul doğru olduğu sürece tekrarlar |
| for | Liste/dizi üzerinde gezinir |
| Kısa Devre | and/or operatörlerinde erken sonuç |
| len() | Uzunluk/eleman sayısı döndürür |
| Liste | Birden fazla veriyi tutar |
| Fonksiyon | Tekrar kullanılabilir kod bloğu |
| Recursive | Kendini çağıran fonksiyon |

---

## 🎯 SINAV İÇİN ÖNEMLİ İPUÇLARI

1. **Kısa devre**: `False and X` → False (X'e bakılmaz)
2. **Kısa devre**: `True or X` → True (X'e bakılmaz)
3. **Asal sayı**: Sadece 1 ve kendine bölünen sayı
4. **Recursive**: Mutlaka durma koşulu (base case) olmalı
5. **len()**: String, liste, tuple için uzunluk döndürür
6. **match-case**: Python 3.10+ gerektirir, `_` default case'dir

---

**💪 Başarılar!**