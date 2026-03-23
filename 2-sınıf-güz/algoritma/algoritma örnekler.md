# 🐍 ALGORİTMA SINAVI - ÖRNEK SORULAR VE ÇÖZÜMLER

> Tüm değişken ve fonksiyon isimleri Türkçe olarak hazırlanmıştır.
> Her örneğin hem normal hem de fonksiyonlu hali verilmiştir.

---

## 📌 1. TEMEL HESAPLAMALAR

### Örnek 1.1: İki Sayının Toplamı

**Normal Hali:**
```python
sayi1 = int(input("Birinci sayı: "))
sayi2 = int(input("İkinci sayı: "))

toplam = sayi1 + sayi2
print(f"Toplam: {toplam}")
```

**Fonksiyonlu Hali:**
```python
def toplama_yap(sayi1, sayi2):
    """İki sayıyı toplar ve sonucu döndürür"""
    return sayi1 + sayi2

# Ana program
birinci = int(input("Birinci sayı: "))
ikinci = int(input("İkinci sayı: "))
sonuc = toplama_yap(birinci, ikinci)
print(f"Toplam: {sonuc}")
```

---

### Örnek 1.2: Dört İşlem Hesaplayıcı

**Normal Hali:**
```python
sayi1 = float(input("Birinci sayı: "))
sayi2 = float(input("İkinci sayı: "))

toplam = sayi1 + sayi2
fark = sayi1 - sayi2
carpim = sayi1 * sayi2

if sayi2 != 0:
    bolum = sayi1 / sayi2
else:
    bolum = "Tanımsız"

print(f"Toplam: {toplam}")
print(f"Fark: {fark}")
print(f"Çarpım: {carpim}")
print(f"Bölüm: {bolum}")
```

**Fonksiyonlu Hali:**
```python
def dort_islem(sayi1, sayi2):
    """Dört işlem sonuçlarını döndürür"""
    toplam = sayi1 + sayi2
    fark = sayi1 - sayi2
    carpim = sayi1 * sayi2
    
    if sayi2 != 0:
        bolum = sayi1 / sayi2
    else:
        bolum = "Tanımsız"
    
    return toplam, fark, carpim, bolum

# Ana program
a = float(input("Birinci sayı: "))
b = float(input("İkinci sayı: "))

toplam, fark, carpim, bolum = dort_islem(a, b)
print(f"Toplam: {toplam}")
print(f"Fark: {fark}")
print(f"Çarpım: {carpim}")
print(f"Bölüm: {bolum}")
```

---

### Örnek 1.3: Üçgenin Alanını Hesaplama

**Normal Hali:**
```python
taban = float(input("Taban uzunluğu: "))
yukseklik = float(input("Yükseklik: "))

alan = (taban * yukseklik) / 2
print(f"Üçgenin alanı: {alan}")
```

**Fonksiyonlu Hali:**
```python
def ucgen_alani_hesapla(taban, yukseklik):
    """Üçgenin alanını hesaplar"""
    alan = (taban * yukseklik) / 2
    return alan

# Ana program
t = float(input("Taban uzunluğu: "))
y = float(input("Yükseklik: "))
sonuc = ucgen_alani_hesapla(t, y)
print(f"Üçgenin alanı: {sonuc}")
```

---

### Örnek 1.4: Dairenin Çevresi ve Alanı

**Normal Hali:**
```python
yaricap = float(input("Yarıçap: "))
pi = 3.14

cevre = 2 * pi * yaricap
alan = pi * yaricap * yaricap

print(f"Çevre: {cevre}")
print(f"Alan: {alan}")
```

**Fonksiyonlu Hali:**
```python
def daire_hesapla(yaricap):
    """Dairenin çevre ve alanını hesaplar"""
    pi = 3.14
    cevre = 2 * pi * yaricap
    alan = pi * yaricap * yaricap
    return cevre, alan

# Ana program
r = float(input("Yarıçap: "))
cevre, alan = daire_hesapla(r)
print(f"Çevre: {cevre}")
print(f"Alan: {alan}")
```

---

## 📌 2. KOŞUL YAPILARI (IF-ELIF-ELSE)

### Örnek 2.1: Pozitif/Negatif/Sıfır Kontrolü

**Normal Hali:**
```python
sayi = int(input("Bir sayı girin: "))

if sayi > 0:
    print("Pozitif sayı")
elif sayi < 0:
    print("Negatif sayı")
else:
    print("Sıfır")
```

**Fonksiyonlu Hali:**
```python
def sayi_turunu_bul(sayi):
    """Sayının pozitif, negatif veya sıfır olduğunu belirler"""
    if sayi > 0:
        return "Pozitif sayı"
    elif sayi < 0:
        return "Negatif sayı"
    else:
        return "Sıfır"

# Ana program
girilen = int(input("Bir sayı girin: "))
sonuc = sayi_turunu_bul(girilen)
print(sonuc)
```

---

### Örnek 2.2: Çift/Tek Sayı Kontrolü

**Normal Hali:**
```python
sayi = int(input("Bir sayı girin: "))

if sayi % 2 == 0:
    print(f"{sayi} çift sayıdır")
else:
    print(f"{sayi} tek sayıdır")
```

**Fonksiyonlu Hali:**
```python
def cift_mi(sayi):
    """Sayının çift olup olmadığını kontrol eder"""
    if sayi % 2 == 0:
        return True
    else:
        return False

# Ana program
girilen = int(input("Bir sayı girin: "))

if cift_mi(girilen):
    print(f"{girilen} çift sayıdır")
else:
    print(f"{girilen} tek sayıdır")
```

---

### Örnek 2.3: Not Değerlendirme (Harf Notu)

**Normal Hali:**
```python
puan = int(input("Puanınızı girin (0-100): "))

if puan >= 90:
    harf = "AA"
elif puan >= 85:
    harf = "BA"
elif puan >= 80:
    harf = "BB"
elif puan >= 75:
    harf = "CB"
elif puan >= 70:
    harf = "CC"
elif puan >= 65:
    harf = "DC"
elif puan >= 60:
    harf = "DD"
elif puan >= 50:
    harf = "FD"
else:
    harf = "FF"

print(f"Harf notunuz: {harf}")
```

**Fonksiyonlu Hali:**
```python
def harf_notu_bul(puan):
    """Puana göre harf notunu döndürür"""
    if puan >= 90:
        return "AA"
    elif puan >= 85:
        return "BA"
    elif puan >= 80:
        return "BB"
    elif puan >= 75:
        return "CB"
    elif puan >= 70:
        return "CC"
    elif puan >= 65:
        return "DC"
    elif puan >= 60:
        return "DD"
    elif puan >= 50:
        return "FD"
    else:
        return "FF"

# Ana program
puan = int(input("Puanınızı girin: "))
harf = harf_notu_bul(puan)
print(f"Harf notunuz: {harf}")
```

---

### Örnek 2.4: En Büyük Sayıyı Bulma (3 Sayı)

**Normal Hali:**
```python
sayi1 = int(input("Birinci sayı: "))
sayi2 = int(input("İkinci sayı: "))
sayi3 = int(input("Üçüncü sayı: "))

if sayi1 >= sayi2 and sayi1 >= sayi3:
    en_buyuk = sayi1
elif sayi2 >= sayi1 and sayi2 >= sayi3:
    en_buyuk = sayi2
else:
    en_buyuk = sayi3

print(f"En büyük sayı: {en_buyuk}")
```

**Fonksiyonlu Hali:**
```python
def en_buyugu_bul(sayi1, sayi2, sayi3):
    """Üç sayıdan en büyüğünü bulur"""
    if sayi1 >= sayi2 and sayi1 >= sayi3:
        return sayi1
    elif sayi2 >= sayi1 and sayi2 >= sayi3:
        return sayi2
    else:
        return sayi3

# Ana program
a = int(input("Birinci sayı: "))
b = int(input("İkinci sayı: "))
c = int(input("Üçüncü sayı: "))

sonuc = en_buyugu_bul(a, b, c)
print(f"En büyük sayı: {sonuc}")
```

---

### Örnek 2.5: Yaş Kontrolü (Ehliyet)

**Normal Hali:**
```python
yas = int(input("Yaşınızı girin: "))

if yas < 0:
    print("Geçersiz yaş!")
elif yas < 18:
    print("Ehliyet alamazsınız")
elif yas <= 65:
    print("Ehliyet alabilirsiniz")
else:
    print("Sağlık raporu gerekli")
```

**Fonksiyonlu Hali:**
```python
def ehliyet_durumu(yas):
    """Yaşa göre ehliyet durumunu kontrol eder"""
    if yas < 0:
        return "Geçersiz yaş!"
    elif yas < 18:
        return "Ehliyet alamazsınız"
    elif yas <= 65:
        return "Ehliyet alabilirsiniz"
    else:
        return "Sağlık raporu gerekli"

# Ana program
kullanici_yasi = int(input("Yaşınızı girin: "))
durum = ehliyet_durumu(kullanici_yasi)
print(durum)
```

---

### Örnek 2.6: Artık Yıl Kontrolü

**Normal Hali:**
```python
yil = int(input("Yıl girin: "))

if (yil % 4 == 0 and yil % 100 != 0) or (yil % 400 == 0):
    print(f"{yil} artık yıldır")
else:
    print(f"{yil} artık yıl değildir")
```

**Fonksiyonlu Hali:**
```python
def artik_yil_mi(yil):
    """Yılın artık yıl olup olmadığını kontrol eder"""
    if (yil % 4 == 0 and yil % 100 != 0) or (yil % 400 == 0):
        return True
    else:
        return False

# Ana program
girilen_yil = int(input("Yıl girin: "))

if artik_yil_mi(girilen_yil):
    print(f"{girilen_yil} artık yıldır")
else:
    print(f"{girilen_yil} artık yıl değildir")
```

---

## 📌 3. MATCH-CASE (SWITCH-CASE)

### Örnek 3.1: Basit Hesap Makinesi

**Normal Hali:**
```python
print("=== HESAP MAKİNESİ ===")
print("1. Toplama")
print("2. Çıkarma")
print("3. Çarpma")
print("4. Bölme")

secim = input("Seçiminiz (1-4): ")
sayi1 = float(input("Birinci sayı: "))
sayi2 = float(input("İkinci sayı: "))

match secim:
    case "1":
        sonuc = sayi1 + sayi2
        print(f"Sonuç: {sonuc}")
    case "2":
        sonuc = sayi1 - sayi2
        print(f"Sonuç: {sonuc}")
    case "3":
        sonuc = sayi1 * sayi2
        print(f"Sonuç: {sonuc}")
    case "4":
        if sayi2 != 0:
            sonuc = sayi1 / sayi2
            print(f"Sonuç: {sonuc}")
        else:
            print("Sıfıra bölünemez!")
    case _:
        print("Geçersiz seçim!")
```

**Fonksiyonlu Hali:**
```python
def toplama(a, b):
    return a + b

def cikarma(a, b):
    return a - b

def carpma(a, b):
    return a * b

def bolme(a, b):
    if b != 0:
        return a / b
    else:
        return "Sıfıra bölünemez!"

def hesap_makinesi(secim, sayi1, sayi2):
    """Seçime göre işlem yapar"""
    match secim:
        case "1":
            return toplama(sayi1, sayi2)
        case "2":
            return cikarma(sayi1, sayi2)
        case "3":
            return carpma(sayi1, sayi2)
        case "4":
            return bolme(sayi1, sayi2)
        case _:
            return "Geçersiz seçim!"

# Ana program
print("1.Toplama 2.Çıkarma 3.Çarpma 4.Bölme")
kullanici_secimi = input("Seçiminiz: ")
a = float(input("Birinci sayı: "))
b = float(input("İkinci sayı: "))

sonuc = hesap_makinesi(kullanici_secimi, a, b)
print(f"Sonuç: {sonuc}")
```

---

### Örnek 3.2: Alışveriş Sistemi (ÖNEMLİ!)

**Normal Hali:**
```python
sepet = []
toplam_tutar = 0

while True:
    print("\n=== ALIŞVERİŞ SİSTEMİ ===")
    print("1. Elma (5 TL)")
    print("2. Ekmek (10 TL)")
    print("3. Süt (25 TL)")
    print("4. Peynir (50 TL)")
    print("5. Sepeti Gör")
    print("6. Ödeme Yap")
    
    secim = input("Seçiminiz: ")
    
    match secim:
        case "1":
            sepet.append("Elma")
            toplam_tutar += 5
            print("✓ Elma eklendi!")
        case "2":
            sepet.append("Ekmek")
            toplam_tutar += 10
            print("✓ Ekmek eklendi!")
        case "3":
            sepet.append("Süt")
            toplam_tutar += 25
            print("✓ Süt eklendi!")
        case "4":
            sepet.append("Peynir")
            toplam_tutar += 50
            print("✓ Peynir eklendi!")
        case "5":
            print(f"Sepet: {sepet}")
            print(f"Toplam: {toplam_tutar} TL")
        case "6":
            print("\n=== FİŞ ===")
            for urun in sepet:
                print(f"- {urun}")
            print(f"TOPLAM: {toplam_tutar} TL")
            break
        case _:
            print("Geçersiz seçim!")
```

**Fonksiyonlu Hali:**
```python
def urun_ekle(sepet, urun_adi, fiyat, toplam):
    """Sepete ürün ekler"""
    sepet.append(urun_adi)
    toplam += fiyat
    print(f"✓ {urun_adi} eklendi!")
    return toplam

def sepeti_goster(sepet, toplam):
    """Sepeti gösterir"""
    print(f"Sepet: {sepet}")
    print(f"Toplam: {toplam} TL")

def fis_yazdir(sepet, toplam):
    """Fişi yazdırır"""
    print("\n=== FİŞ ===")
    for urun in sepet:
        print(f"- {urun}")
    print(f"TOPLAM: {toplam} TL")

def alisveris_yap():
    """Ana alışveriş fonksiyonu"""
    sepet = []
    toplam_tutar = 0
    
    while True:
        print("\n1.Elma(5TL) 2.Ekmek(10TL) 3.Süt(25TL) 4.Peynir(50TL) 5.Sepet 6.Ödeme")
        secim = input("Seçim: ")
        
        match secim:
            case "1":
                toplam_tutar = urun_ekle(sepet, "Elma", 5, toplam_tutar)
            case "2":
                toplam_tutar = urun_ekle(sepet, "Ekmek", 10, toplam_tutar)
            case "3":
                toplam_tutar = urun_ekle(sepet, "Süt", 25, toplam_tutar)
            case "4":
                toplam_tutar = urun_ekle(sepet, "Peynir", 50, toplam_tutar)
            case "5":
                sepeti_goster(sepet, toplam_tutar)
            case "6":
                fis_yazdir(sepet, toplam_tutar)
                break
            case _:
                print("Geçersiz!")

# Programı başlat
alisveris_yap()
```

---

### Örnek 3.3: Gün Adı Bulma

**Normal Hali:**
```python
gun_numarasi = int(input("Gün numarası (1-7): "))

match gun_numarasi:
    case 1:
        print("Pazartesi")
    case 2:
        print("Salı")
    case 3:
        print("Çarşamba")
    case 4:
        print("Perşembe")
    case 5:
        print("Cuma")
    case 6:
        print("Cumartesi")
    case 7:
        print("Pazar")
    case _:
        print("Geçersiz gün!")
```

**Fonksiyonlu Hali:**
```python
def gun_adi_bul(numara):
    """Numaraya göre gün adını döndürür"""
    match numara:
        case 1:
            return "Pazartesi"
        case 2:
            return "Salı"
        case 3:
            return "Çarşamba"
        case 4:
            return "Perşembe"
        case 5:
            return "Cuma"
        case 6:
            return "Cumartesi"
        case 7:
            return "Pazar"
        case _:
            return "Geçersiz gün!"

# Ana program
numara = int(input("Gün numarası: "))
gun = gun_adi_bul(numara)
print(gun)
```

---

## 📌 4. WHILE DÖNGÜSÜ

### Örnek 4.1: 1'den N'e Kadar Sayıları Yazdırma

**Normal Hali:**
```python
n = int(input("N değeri: "))
sayac = 1

while sayac <= n:
    print(sayac)
    sayac += 1
```

**Fonksiyonlu Hali:**
```python
def sayilari_yazdir(n):
    """1'den n'e kadar sayıları yazdırır"""
    sayac = 1
    while sayac <= n:
        print(sayac)
        sayac += 1

# Ana program
deger = int(input("N değeri: "))
sayilari_yazdir(deger)
```

---

### Örnek 4.2: 1'den N'e Kadar Toplam

**Normal Hali:**
```python
n = int(input("N değeri: "))
sayac = 1
toplam = 0

while sayac <= n:
    toplam += sayac
    sayac += 1

print(f"1'den {n}'e kadar toplam: {toplam}")
```

**Fonksiyonlu Hali:**
```python
def toplam_hesapla(n):
    """1'den n'e kadar sayıların toplamını hesaplar"""
    sayac = 1
    toplam = 0
    
    while sayac <= n:
        toplam += sayac
        sayac += 1
    
    return toplam

# Ana program
deger = int(input("N değeri: "))
sonuc = toplam_hesapla(deger)
print(f"Toplam: {sonuc}")
```

---

### Örnek 4.3: Faktöriyel Hesaplama

**Normal Hali:**
```python
n = int(input("Sayı girin: "))
faktoriyel = 1
sayac = 1

while sayac <= n:
    faktoriyel *= sayac  # faktoriyel = faktoriyel * sayac
    sayac += 1

print(f"{n}! = {faktoriyel}")
```

**Fonksiyonlu Hali:**
```python
def faktoriyel_hesapla(n):
    """n! değerini hesaplar"""
    sonuc = 1
    sayac = 1
    
    while sayac <= n:
        sonuc *= sayac
        sayac += 1
    
    return sonuc

# Ana program
sayi = int(input("Sayı girin: "))
sonuc = faktoriyel_hesapla(sayi)
print(f"{sayi}! = {sonuc}")
```

---

### Örnek 4.4: Sayı Tahmin Oyunu

**Normal Hali:**
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

**Fonksiyonlu Hali:**
```python
import random

def ipucu_ver(tahmin, gizli):
    """Tahmine göre ipucu verir"""
    if tahmin < gizli:
        return "Daha büyük!"
    elif tahmin > gizli:
        return "Daha küçük!"
    else:
        return "dogru"

def oyunu_oyna():
    """Tahmin oyununu başlatır"""
    gizli_sayi = random.randint(1, 100)
    deneme = 0
    
    print("1-100 arası sayı tuttum!")
    
    while True:
        tahmin = int(input("Tahmin: "))
        deneme += 1
        
        sonuc = ipucu_ver(tahmin, gizli_sayi)
        
        if sonuc == "dogru":
            print(f"Tebrikler! {deneme} denemede buldunuz!")
            break
        else:
            print(sonuc)

# Oyunu başlat
oyunu_oyna()
```

---

### Örnek 4.5: Şifre Kontrolü (3 Deneme Hakkı)

**Normal Hali:**
```python
dogru_sifre = "python123"
kalan_hak = 3

while kalan_hak > 0:
    girilen = input("Şifre: ")
    
    if girilen == dogru_sifre:
        print("Giriş başarılı!")
        break
    else:
        kalan_hak -= 1
        print(f"Yanlış! {kalan_hak} hak kaldı.")

if kalan_hak == 0:
    print("Hesap kilitlendi!")
```

**Fonksiyonlu Hali:**
```python
def sifre_kontrol(girilen, dogru):
    """Şifrenin doğru olup olmadığını kontrol eder"""
    return girilen == dogru

def giris_yap():
    """Giriş işlemini yönetir"""
    dogru_sifre = "python123"
    kalan_hak = 3
    
    while kalan_hak > 0:
        girilen = input("Şifre: ")
        
        if sifre_kontrol(girilen, dogru_sifre):
            print("Giriş başarılı!")
            return True
        else:
            kalan_hak -= 1
            print(f"Yanlış! {kalan_hak} hak kaldı.")
    
    print("Hesap kilitlendi!")
    return False

# Programı başlat
giris_yap()
```

---

### Örnek 4.6: Basamak Sayısı Bulma

**Normal Hali:**
```python
sayi = int(input("Sayı girin: "))
basamak_sayisi = 0
gecici = sayi

while gecici > 0:
    gecici = gecici // 10
    basamak_sayisi += 1

print(f"{sayi} sayısı {basamak_sayisi} basamaklıdır")
```

**Fonksiyonlu Hali:**
```python
def basamak_say(sayi):
    """Sayının kaç basamaklı olduğunu bulur"""
    sayac = 0
    
    if sayi == 0:
        return 1
    
    while sayi > 0:
        sayi = sayi // 10
        sayac += 1
    
    return sayac

# Ana program
girilen = int(input("Sayı girin: "))
sonuc = basamak_say(girilen)
print(f"{sonuc} basamaklıdır")
```

---

### Örnek 4.7: Rakamlar Toplamı

**Normal Hali:**
```python
sayi = int(input("Sayı girin: "))
toplam = 0
gecici = sayi

while gecici > 0:
    son_rakam = gecici % 10
    toplam += son_rakam
    gecici = gecici // 10

print(f"{sayi} sayısının rakamları toplamı: {toplam}")
```

**Fonksiyonlu Hali:**
```python
def rakam_toplami_bul(sayi):
    """Sayının rakamlarının toplamını bulur"""
    toplam = 0
    
    while sayi > 0:
        son_rakam = sayi % 10
        toplam += son_rakam
        sayi = sayi // 10
    
    return toplam

# Ana program
girilen = int(input("Sayı girin: "))
sonuc = rakam_toplami_bul(girilen)
print(f"Rakamlar toplamı: {sonuc}")
```

---

## 📌 5. FOR DÖNGÜSÜ

### Örnek 5.1: Liste Elemanlarını Yazdırma

**Normal Hali:**
```python
meyveler = ["elma", "armut", "muz", "çilek"]

for meyve in meyveler:
    print(meyve)
```

**Fonksiyonlu Hali:**
```python
def listeyi_yazdir(liste):
    """Liste elemanlarını yazdırır"""
    for eleman in liste:
        print(eleman)

# Ana program
meyveler = ["elma", "armut", "muz", "çilek"]
listeyi_yazdir(meyveler)
```

---

### Örnek 5.2: Çarpım Tablosu

**Normal Hali:**
```python
sayi = int(input("Hangi sayının çarpım tablosu: "))

for i in range(1, 11):
    sonuc = sayi * i
    print(f"{sayi} x {i} = {sonuc}")
```

**Fonksiyonlu Hali:**
```python
def carpim_tablosu(sayi):
    """Bir sayının çarpım tablosunu yazdırır"""
    for i in range(1, 11):
        sonuc = sayi * i
        print(f"{sayi} x {i} = {sonuc}")

# Ana program
n = int(input("Sayı: "))
carpim_tablosu(n)
```

---

### Örnek 5.3: Liste Toplamı ve Ortalaması

**Normal Hali:**
```python
notlar = [70, 85, 90, 65, 80]
toplam = 0

for nott in notlar:
    toplam += nott

ortalama = toplam / len(notlar)
print(f"Toplam: {toplam}")
print(f"Ortalama: {ortalama}")
```

**Fonksiyonlu Hali:**
```python
def toplam_bul(liste):
    """Listenin toplamını bulur"""
    toplam = 0
    for eleman in liste:
        toplam += eleman
    return toplam

def ortalama_bul(liste):
    """Listenin ortalamasını bulur"""
    toplam = toplam_bul(liste)
    return toplam / len(liste)

# Ana program
notlar = [70, 85, 90, 65, 80]
print(f"Toplam: {toplam_bul(notlar)}")
print(f"Ortalama: {ortalama_bul(notlar)}")
```

---

### Örnek 5.4: En Büyük ve En Küçük Sayı

**Normal Hali:**
```python
sayilar = [23, 45, 12, 67, 34, 89, 5]

en_buyuk = sayilar[0]
en_kucuk = sayilar[0]

for sayi in sayilar:
    if sayi > en_buyuk:
        en_buyuk = sayi
    if sayi < en_kucuk:
        en_kucuk = sayi

print(f"En büyük: {en_buyuk}")
print(f"En küçük: {en_kucuk}")
```

**Fonksiyonlu Hali:**
```python
def en_buyuk_bul(liste):
    """Listedeki en büyük sayıyı bulur"""
    en_buyuk = liste[0]
    for sayi in liste:
        if sayi > en_buyuk:
            en_buyuk = sayi
    return en_buyuk

def en_kucuk_bul(liste):
    """Listedeki en küçük sayıyı bulur"""
    en_kucuk = liste[0]
    for sayi in liste:
        if sayi < en_kucuk:
            en_kucuk = sayi
    return en_kucuk

# Ana program
sayilar = [23, 45, 12, 67, 34, 89, 5]
print(f"En büyük: {en_buyuk_bul(sayilar)}")
print(f"En küçük: {en_kucuk_bul(sayilar)}")
```

---

### Örnek 5.5: Çift Sayıları Bulma

**Normal Hali:**
```python
sayilar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
cift_sayilar = []

for sayi in sayilar:
    if sayi % 2 == 0:
        cift_sayilar.append(sayi)

print(f"Çift sayılar: {cift_sayilar}")
```

**Fonksiyonlu Hali:**
```python
def cift_sayilari_bul(liste):
    """Listedeki çift sayıları bulur"""
    ciftler = []
    for sayi in liste:
        if sayi % 2 == 0:
            ciftler.append(sayi)
    return ciftler

# Ana program
sayilar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
sonuc = cift_sayilari_bul(sayilar)
print(f"Çift sayılar: {sonuc}")
```

---

### Örnek 5.6: String'deki Sesli Harfleri Sayma

**Normal Hali:**
```python
cumle = input("Bir cümle girin: ")
sesli_harfler = "aeıioöuüAEIİOÖUÜ"
sayac = 0

for harf in cumle:
    if harf in sesli_harfler:
        sayac += 1

print(f"Sesli harf sayısı: {sayac}")
```

**Fonksiyonlu Hali:**
```python
def sesli_harf_say(metin):
    """Metindeki sesli harfleri sayar"""
    sesli_harfler = "aeıioöuüAEIİOÖUÜ"
    sayac = 0
    
    for harf in metin:
        if harf in sesli_harfler:
            sayac += 1
    
    return sayac

# Ana program
cumle = input("Cümle girin: ")
sonuc = sesli_harf_say(cumle)
print(f"Sesli harf sayısı: {sonuc}")
```

---

## 📌 6. İÇ İÇE DÖNGÜLER

### Örnek 6.1: Dikdörtgen Çizme

**Normal Hali:**
```python
satir = 4
sutun = 6

for i in range(satir):
    for j in range(sutun):
        print("*", end="")
    print()
```

**Fonksiyonlu Hali:**
```python
def dikdortgen_ciz(satir, sutun):
    """Yıldızlarla dikdörtgen çizer"""
    for i in range(satir):
        for j in range(sutun):
            print("*", end="")
        print()

# Ana program
dikdortgen_ciz(4, 6)
```

---

### Örnek 6.2: Üçgen Çizme

**Normal Hali:**
```python
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

**Fonksiyonlu Hali:**
```python
def ucgen_ciz(yukseklik):
    """Yıldızlarla üçgen çizer"""
    for i in range(1, yukseklik + 1):
        for j in range(i):
            print("*", end="")
        print()

# Ana program
ucgen_ciz(5)
```

---

### Örnek 6.3: Ters Üçgen

**Normal Hali:**
```python
satir_sayisi = 5

for i in range(satir_sayisi, 0, -1):
    for j in range(i):
        print("*", end="")
    print()

# Çıktı:
# *****
# ****
# ***
# **
# *
```

**Fonksiyonlu Hali:**
```python
def ters_ucgen_ciz(yukseklik):
    """Ters üçgen çizer"""
    for i in range(yukseklik, 0, -1):
        for j in range(i):
            print("*", end="")
        print()

# Ana program
ters_ucgen_ciz(5)
```

---

### Örnek 6.4: Çarpım Tablosu (1-10 Arası)

**Normal Hali:**
```python
for i in range(1, 11):
    for j in range(1, 11):
        sonuc = i * j
        print(f"{sonuc:4}", end="")
    print()
```

**Fonksiyonlu Hali:**
```python
def carpim_tablosu_olustur(baslangic, bitis):
    """Çarpım tablosu oluşturur"""
    for i in range(baslangic, bitis + 1):
        for j in range(baslangic, bitis + 1):
            sonuc = i * j
            print(f"{sonuc:4}", end="")
        print()

# Ana program
carpim_tablosu_olustur(1, 10)
```

---

### ⭐ Örnek 6.5: Asal Sayıları Bulma (ÖNEMLİ!)

**Normal Hali:**
```python
print("2-100 arası asal sayılar:")

for sayi in range(2, 101):
    asal_mi = True
    
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            asal_mi = False
            break
    
    if asal_mi:
        print(sayi, end=" ")
```

**Fonksiyonlu Hali:**
```python
def asal_mi_kontrol(sayi):
    """Bir sayının asal olup olmadığını kontrol eder"""
    if sayi < 2:
        return False
    
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            return False
    
    return True

def asal_sayilari_bul(baslangic, bitis):
    """Aralıktaki asal sayıları bulur"""
    asallar = []
    
    for sayi in range(baslangic, bitis + 1):
        if asal_mi_kontrol(sayi):
            asallar.append(sayi)
    
    return asallar

# Ana program
sonuc = asal_sayilari_bul(2, 100)
print("Asal sayılar:", sonuc)
print(f"Toplam {len(sonuc)} adet asal sayı var")
```

---

### Örnek 6.6: Mükemmel Sayı Bulma

**Normal Hali:**
```python
# Mükemmel sayı: Kendisi hariç bölenlerinin toplamı kendisine eşit
# Örnek: 6 = 1 + 2 + 3

print("1-1000 arası mükemmel sayılar:")

for sayi in range(1, 1001):
    bolenler_toplami = 0
    
    for bolen in range(1, sayi):
        if sayi % bolen == 0:
            bolenler_toplami += bolen
    
    if bolenler_toplami == sayi:
        print(sayi, end=" ")
```

**Fonksiyonlu Hali:**
```python
def mukemmel_mi(sayi):
    """Sayının mükemmel sayı olup olmadığını kontrol eder"""
    bolenler_toplami = 0
    
    for bolen in range(1, sayi):
        if sayi % bolen == 0:
            bolenler_toplami += bolen
    
    return bolenler_toplami == sayi

def mukemmel_sayilari_bul(baslangic, bitis):
    """Aralıktaki mükemmel sayıları bulur"""
    mukemmeller = []
    
    for sayi in range(baslangic, bitis + 1):
        if mukemmel_mi(sayi):
            mukemmeller.append(sayi)
    
    return mukemmeller

# Ana program
sonuc = mukemmel_sayilari_bul(1, 1000)
print("Mükemmel sayılar:", sonuc)
```

---

## 📌 7. LİSTELER

### Örnek 7.1: Liste Oluşturma ve Elemanları Yazdırma

**Normal Hali:**
```python
ogrenciler = ["Ali", "Veli", "Ayşe", "Fatma", "Mehmet"]

print("Öğrenci listesi:")
for i in range(len(ogrenciler)):
    print(f"{i+1}. {ogrenciler[i]}")
```

**Fonksiyonlu Hali:**
```python
def numarali_liste_yazdir(liste, baslik):
    """Listeyi numaralı olarak yazdırır"""
    print(baslik)
    for i in range(len(liste)):
        print(f"{i+1}. {liste[i]}")

# Ana program
ogrenciler = ["Ali", "Veli", "Ayşe", "Fatma"]
numarali_liste_yazdir(ogrenciler, "Öğrenci Listesi:")
```

---

### Örnek 7.2: Listeye Eleman Ekleme/Silme

**Normal Hali:**
```python
liste = [1, 2, 3]

# Sona ekleme
liste.append(4)
print(f"Append sonrası: {liste}")

# Belirli indekse ekleme
liste.insert(0, 0)
print(f"Insert sonrası: {liste}")

# Değere göre silme
liste.remove(2)
print(f"Remove sonrası: {liste}")

# İndekse göre silme
silinen = liste.pop(0)
print(f"Pop sonrası: {liste}, silinen: {silinen}")
```

**Fonksiyonlu Hali:**
```python
def sona_ekle(liste, eleman):
    """Listenin sonuna eleman ekler"""
    liste.append(eleman)
    return liste

def basa_ekle(liste, eleman):
    """Listenin başına eleman ekler"""
    liste.insert(0, eleman)
    return liste

def eleman_sil(liste, eleman):
    """Listeden elemanı siler"""
    if eleman in liste:
        liste.remove(eleman)
    return liste

# Ana program
sayilar = [1, 2, 3]
sayilar = sona_ekle(sayilar, 4)
print(sayilar)  # [1, 2, 3, 4]
```

---

### Örnek 7.3: Listeyi Sıralama

**Normal Hali:**
```python
sayilar = [64, 34, 25, 12, 22, 11, 90]

# Küçükten büyüğe
sayilar.sort()
print(f"Artan sıra: {sayilar}")

# Büyükten küçüğe
sayilar.sort(reverse=True)
print(f"Azalan sıra: {sayilar}")
```

**Fonksiyonlu Hali:**
```python
def artan_sirala(liste):
    """Listeyi küçükten büyüğe sıralar"""
    kopya = liste.copy()
    kopya.sort()
    return kopya

def azalan_sirala(liste):
    """Listeyi büyükten küçüğe sıralar"""
    kopya = liste.copy()
    kopya.sort(reverse=True)
    return kopya

# Ana program
sayilar = [64, 34, 25, 12, 22]
print(f"Artan: {artan_sirala(sayilar)}")
print(f"Azalan: {azalan_sirala(sayilar)}")
```

---

### ⭐ Örnek 7.4: Asal Sayıları Listeye Ekleme

**Normal Hali:**
```python
asal_liste = []

for sayi in range(2, 51):
    asal = True
    
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            asal = False
            break
    
    if asal:
        asal_liste.append(sayi)

print(f"Asal sayılar: {asal_liste}")
print(f"Toplam: {len(asal_liste)} adet")
```

**Fonksiyonlu Hali:**
```python
def asal_mi(sayi):
    """Sayının asal olup olmadığını kontrol eder"""
    if sayi < 2:
        return False
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            return False
    return True

def asal_listesi_olustur(baslangic, bitis):
    """Aralıktaki asal sayıların listesini oluşturur"""
    liste = []
    for sayi in range(baslangic, bitis + 1):
        if asal_mi(sayi):
            liste.append(sayi)
    return liste

# Ana program
asallar = asal_listesi_olustur(2, 50)
print(f"Asallar: {asallar}")
```

---

### ⭐ Örnek 7.5: Adam Asmaca Oyunu (LİSTELERLE)

```python
import random

def kelime_sec(kelimeler):
    """Listeden rastgele kelime seçer"""
    return random.choice(kelimeler)

def gorunum_olustur(kelime):
    """Kelimenin görünümünü oluşturur (alt çizgilerle)"""
    return ["_"] * len(kelime)

def harf_kontrol(harf, kelime, gorunum):
    """Harfin kelimede olup olmadığını kontrol eder"""
    bulundu = False
    for i in range(len(kelime)):
        if kelime[i] == harf:
            gorunum[i] = harf
            bulundu = True
    return bulundu

def oyun_bitti_mi(gorunum):
    """Oyunun bitip bitmediğini kontrol eder"""
    return "_" not in gorunum

def adam_asmaca():
    """Adam asmaca oyununu başlatır"""
    kelimeler = ["python", "algoritma", "bilgisayar", "klavye", "programlama"]
    gizli_kelime = kelime_sec(kelimeler)
    gorunum = gorunum_olustur(gizli_kelime)
    yanlis_harfler = []
    can = 6
    
    print("=== ADAM ASMACA ===")
    
    while can > 0 and not oyun_bitti_mi(gorunum):
        print(f"\nKelime: {' '.join(gorunum)}")
        print(f"Yanlış harfler: {yanlis_harfler}")
        print(f"Kalan can: {can}")
        
        tahmin = input("Harf girin: ").lower()
        
        if len(tahmin) != 1:
            print("Tek harf girin!")
            continue
        
        if tahmin in gorunum or tahmin in yanlis_harfler:
            print("Bu harfi denediniz!")
            continue
        
        if harf_kontrol(tahmin, gizli_kelime, gorunum):
            print("Doğru!")
        else:
            print("Yanlış!")
            yanlis_harfler.append(tahmin)
            can -= 1
    
    if oyun_bitti_mi(gorunum):
        print(f"\n🎉 TEBRİKLER! Kelime: {gizli_kelime}")
    else:
        print(f"\n💀 KAYBETTİNİZ! Kelime: {gizli_kelime}")

# Oyunu başlat
adam_asmaca()
```

---

## 📌 8. KISA DEVRE DEĞERLENDİRME

### Örnek 8.1: AND Kısa Devre

```python
def kontrol_yap(deger):
    """Kontrol fonksiyonu"""
    print("Fonksiyon çalıştı!")
    return deger

# False AND durumu - ikinci kısım çalışmaz
sonuc = False and kontrol_yap(True)
print(f"Sonuç: {sonuc}")
# Çıktı: Sonuç: False (Fonksiyon çalışmadı!)

# True AND durumu - ikinci kısım çalışır
sonuc = True and kontrol_yap(True)
print(f"Sonuç: {sonuc}")
# Çıktı: Fonksiyon çalıştı!
#        Sonuç: True
```

### Örnek 8.2: OR Kısa Devre

```python
def kontrol_yap(deger):
    """Kontrol fonksiyonu"""
    print("Fonksiyon çalıştı!")
    return deger

# True OR durumu - ikinci kısım çalışmaz
sonuc = True or kontrol_yap(False)
print(f"Sonuç: {sonuc}")
# Çıktı: Sonuç: True (Fonksiyon çalışmadı!)

# False OR durumu - ikinci kısım çalışır
sonuc = False or kontrol_yap(True)
print(f"Sonuç: {sonuc}")
# Çıktı: Fonksiyon çalıştı!
#        Sonuç: True
```

### Örnek 8.3: Sıfıra Bölme Koruması

```python
def guvenli_bolme(bolunen, bolen):
    """Sıfıra bölme hatasından korunan bölme"""
    # Kısa devre: bolen 0 ise ikinci kısım çalışmaz
    if bolen != 0 and bolunen / bolen > 5:
        return "Sonuç 5'ten büyük"
    elif bolen == 0:
        return "Sıfıra bölünemez!"
    else:
        return f"Sonuç: {bolunen / bolen}"

print(guvenli_bolme(10, 0))  # Sıfıra bölünemez!
print(guvenli_bolme(30, 5))  # Sonuç 5'ten büyük
```

### Örnek 8.4: Liste Boş Kontrolü

```python
def ilk_elemani_al(liste):
    """Listenin ilk elemanını güvenle alır"""
    # Kısa devre: liste boşsa ikinci kısım çalışmaz
    if len(liste) > 0 and liste[0] > 10:
        return f"İlk eleman 10'dan büyük: {liste[0]}"
    elif len(liste) == 0:
        return "Liste boş!"
    else:
        return f"İlk eleman: {liste[0]}"

print(ilk_elemani_al([]))         # Liste boş!
print(ilk_elemani_al([15, 20]))   # İlk eleman 10'dan büyük: 15
print(ilk_elemani_al([5, 10]))    # İlk eleman: 5
```

---

## 📌 9. LEN() FONKSİYONU ÖRNEKLERİ

### Örnek 9.1: String Uzunluğu

```python
def karakter_say(metin):
    """Metindeki karakter sayısını döndürür"""
    return len(metin)

isim = "Muhammed"
print(f"{isim} ismi {karakter_say(isim)} karakterdir")  # 8
```

### Örnek 9.2: Şifre Uzunluk Kontrolü

```python
def sifre_gecerli_mi(sifre):
    """Şifrenin geçerli uzunlukta olup olmadığını kontrol eder"""
    if len(sifre) < 6:
        return "Şifre en az 6 karakter olmalı!"
    elif len(sifre) > 20:
        return "Şifre en fazla 20 karakter olabilir!"
    else:
        return "Şifre geçerli!"

print(sifre_gecerli_mi("abc"))        # En az 6 karakter
print(sifre_gecerli_mi("python123"))  # Geçerli
```

### Örnek 9.3: Liste Eleman Sayısı

```python
def liste_bilgisi(liste):
    """Liste hakkında bilgi verir"""
    eleman_sayisi = len(liste)
    
    if eleman_sayisi == 0:
        return "Liste boş!"
    else:
        return f"Listede {eleman_sayisi} eleman var"

ogrenciler = ["Ali", "Veli", "Ayşe"]
print(liste_bilgisi(ogrenciler))  # 3 eleman
print(liste_bilgisi([]))          # Liste boş
```

### Örnek 9.4: Ortalama Hesaplama

```python
def ortalama_hesapla(notlar):
    """Not ortalamasını hesaplar"""
    if len(notlar) == 0:
        return "Liste boş!"
    
    toplam = 0
    for nott in notlar:
        toplam += nott
    
    return toplam / len(notlar)

ogrenci_notlari = [70, 85, 90, 65, 80]
print(f"Ortalama: {ortalama_hesapla(ogrenci_notlari)}")  # 78.0
```

---

## 📌 10. RECURSİVE (ÖZYİNELEMELİ) FONKSİYONLAR

### Örnek 10.1: Geri Sayım

```python
def geri_say(sayi):
    """Recursive geri sayım"""
    # Durma koşulu
    if sayi <= 0:
        print("Bitti!")
        return
    
    print(sayi)
    geri_say(sayi - 1)  # Kendini çağır

# Kullanım
geri_say(5)
# Çıktı: 5 4 3 2 1 Bitti!
```

### Örnek 10.2: Faktöriyel (Recursive)

```python
def faktoriyel(sayi):
    """Faktöriyel hesaplar (özyinelemeli)"""
    # Durma koşulu
    if sayi == 0 or sayi == 1:
        return 1
    
    # Recursive çağrı
    return sayi * faktoriyel(sayi - 1)

# 5! = 5 * 4 * 3 * 2 * 1 = 120
print(f"5! = {faktoriyel(5)}")  # 120
```

### Örnek 10.3: Fibonacci (Recursive)

```python
def fibonacci(n):
    """n. Fibonacci sayısını döndürür"""
    # Durma koşulları
    if n == 0:
        return 0
    if n == 1:
        return 1
    
    # Recursive çağrı
    return fibonacci(n - 1) + fibonacci(n - 2)

# İlk 10 Fibonacci sayısı
print("Fibonacci serisi:")
for i in range(10):
    print(fibonacci(i), end=" ")
# Çıktı: 0 1 1 2 3 5 8 13 21 34
```

### Örnek 10.4: Toplam (Recursive)

```python
def toplam_recursive(sayi):
    """1'den n'e kadar toplamı recursive hesaplar"""
    # Durma koşulu
    if sayi == 1:
        return 1
    
    return sayi + toplam_recursive(sayi - 1)

print(f"1+2+3+4+5 = {toplam_recursive(5)}")  # 15
```

### Örnek 10.5: Üs Alma (Recursive)

```python
def us_al(taban, us):
    """Üs hesaplar (özyinelemeli)"""
    # Durma koşulu
    if us == 0:
        return 1
    
    return taban * us_al(taban, us - 1)

print(f"2^5 = {us_al(2, 5)}")  # 32
print(f"3^4 = {us_al(3, 4)}")  # 81
```

### Örnek 10.6: Rakamlar Toplamı (Recursive)

```python
def rakam_toplami(sayi):
    """Sayının rakamlarının toplamını recursive bulur"""
    # Durma koşulu (tek basamak)
    if sayi < 10:
        return sayi
    
    son_rakam = sayi % 10
    kalan = sayi // 10
    return son_rakam + rakam_toplami(kalan)

print(f"123 -> {rakam_toplami(123)}")  # 6 (1+2+3)
print(f"9876 -> {rakam_toplami(9876)}")  # 30
```

### Örnek 10.7: String Ters Çevirme (Recursive)

```python
def ters_cevir(metin):
    """Metni recursive olarak ters çevirir"""
    # Durma koşulu
    if len(metin) <= 1:
        return metin
    
    return metin[-1] + ters_cevir(metin[:-1])

print(ters_cevir("python"))  # nohtyp
print(ters_cevir("merhaba"))  # abahrem
```

### Örnek 10.8: Palindrom Kontrolü (Recursive)

```python
def palindrom_mu(kelime):
    """Kelimenin palindrom olup olmadığını recursive kontrol eder"""
    # Durma koşulu
    if len(kelime) <= 1:
        return True
    
    # İlk ve son harf eşit mi?
    if kelime[0] != kelime[-1]:
        return False
    
    # Ortadaki kısmı kontrol et
    return palindrom_mu(kelime[1:-1])// filepath: /Users/wonzy/Finla Sınavı Konuları/algoritma/algoritma örnekler.md
# 🐍 ALGORİTMA SINAVI - ÖRNEK SORULAR VE ÇÖZÜMLER

> Tüm değişken ve fonksiyon isimleri Türkçe olarak hazırlanmıştır.
> Her örneğin hem normal hem de fonksiyonlu hali verilmiştir.

---

## 📌 1. TEMEL HESAPLAMALAR

### Örnek 1.1: İki Sayının Toplamı

**Normal Hali:**
```python
sayi1 = int(input("Birinci sayı: "))
sayi2 = int(input("İkinci sayı: "))

toplam = sayi1 + sayi2
print(f"Toplam: {toplam}")
```

**Fonksiyonlu Hali:**
```python
def toplama_yap(sayi1, sayi2):
    """İki sayıyı toplar ve sonucu döndürür"""
    return sayi1 + sayi2

# Ana program
birinci = int(input("Birinci sayı: "))
ikinci = int(input("İkinci sayı: "))
sonuc = toplama_yap(birinci, ikinci)
print(f"Toplam: {sonuc}")
```

---

### Örnek 1.2: Dört İşlem Hesaplayıcı

**Normal Hali:**
```python
sayi1 = float(input("Birinci sayı: "))
sayi2 = float(input("İkinci sayı: "))

toplam = sayi1 + sayi2
fark = sayi1 - sayi2
carpim = sayi1 * sayi2

if sayi2 != 0:
    bolum = sayi1 / sayi2
else:
    bolum = "Tanımsız"

print(f"Toplam: {toplam}")
print(f"Fark: {fark}")
print(f"Çarpım: {carpim}")
print(f"Bölüm: {bolum}")
```

**Fonksiyonlu Hali:**
```python
def dort_islem(sayi1, sayi2):
    """Dört işlem sonuçlarını döndürür"""
    toplam = sayi1 + sayi2
    fark = sayi1 - sayi2
    carpim = sayi1 * sayi2
    
    if sayi2 != 0:
        bolum = sayi1 / sayi2
    else:
        bolum = "Tanımsız"
    
    return toplam, fark, carpim, bolum

# Ana program
a = float(input("Birinci sayı: "))
b = float(input("İkinci sayı: "))

toplam, fark, carpim, bolum = dort_islem(a, b)
print(f"Toplam: {toplam}")
print(f"Fark: {fark}")
print(f"Çarpım: {carpim}")
print(f"Bölüm: {bolum}")
```

---

### Örnek 1.3: Üçgenin Alanını Hesaplama

**Normal Hali:**
```python
taban = float(input("Taban uzunluğu: "))
yukseklik = float(input("Yükseklik: "))

alan = (taban * yukseklik) / 2
print(f"Üçgenin alanı: {alan}")
```

**Fonksiyonlu Hali:**
```python
def ucgen_alani_hesapla(taban, yukseklik):
    """Üçgenin alanını hesaplar"""
    alan = (taban * yukseklik) / 2
    return alan

# Ana program
t = float(input("Taban uzunluğu: "))
y = float(input("Yükseklik: "))
sonuc = ucgen_alani_hesapla(t, y)
print(f"Üçgenin alanı: {sonuc}")
```

---

### Örnek 1.4: Dairenin Çevresi ve Alanı

**Normal Hali:**
```python
yaricap = float(input("Yarıçap: "))
pi = 3.14

cevre = 2 * pi * yaricap
alan = pi * yaricap * yaricap

print(f"Çevre: {cevre}")
print(f"Alan: {alan}")
```

**Fonksiyonlu Hali:**
```python
def daire_hesapla(yaricap):
    """Dairenin çevre ve alanını hesaplar"""
    pi = 3.14
    cevre = 2 * pi * yaricap
    alan = pi * yaricap * yaricap
    return cevre, alan

# Ana program
r = float(input("Yarıçap: "))
cevre, alan = daire_hesapla(r)
print(f"Çevre: {cevre}")
print(f"Alan: {alan}")
```

---

## 📌 2. KOŞUL YAPILARI (IF-ELIF-ELSE)

### Örnek 2.1: Pozitif/Negatif/Sıfır Kontrolü

**Normal Hali:**
```python
sayi = int(input("Bir sayı girin: "))

if sayi > 0:
    print("Pozitif sayı")
elif sayi < 0:
    print("Negatif sayı")
else:
    print("Sıfır")
```

**Fonksiyonlu Hali:**
```python
def sayi_turunu_bul(sayi):
    """Sayının pozitif, negatif veya sıfır olduğunu belirler"""
    if sayi > 0:
        return "Pozitif sayı"
    elif sayi < 0:
        return "Negatif sayı"
    else:
        return "Sıfır"

# Ana program
girilen = int(input("Bir sayı girin: "))
sonuc = sayi_turunu_bul(girilen)
print(sonuc)
```

---

### Örnek 2.2: Çift/Tek Sayı Kontrolü

**Normal Hali:**
```python
sayi = int(input("Bir sayı girin: "))

if sayi % 2 == 0:
    print(f"{sayi} çift sayıdır")
else:
    print(f"{sayi} tek sayıdır")
```

**Fonksiyonlu Hali:**
```python
def cift_mi(sayi):
    """Sayının çift olup olmadığını kontrol eder"""
    if sayi % 2 == 0:
        return True
    else:
        return False

# Ana program
girilen = int(input("Bir sayı girin: "))

if cift_mi(girilen):
    print(f"{girilen} çift sayıdır")
else:
    print(f"{girilen} tek sayıdır")
```

---

### Örnek 2.3: Not Değerlendirme (Harf Notu)

**Normal Hali:**
```python
puan = int(input("Puanınızı girin (0-100): "))

if puan >= 90:
    harf = "AA"
elif puan >= 85:
    harf = "BA"
elif puan >= 80:
    harf = "BB"
elif puan >= 75:
    harf = "CB"
elif puan >= 70:
    harf = "CC"
elif puan >= 65:
    harf = "DC"
elif puan >= 60:
    harf = "DD"
elif puan >= 50:
    harf = "FD"
else:
    harf = "FF"

print(f"Harf notunuz: {harf}")
```

**Fonksiyonlu Hali:**
```python
def harf_notu_bul(puan):
    """Puana göre harf notunu döndürür"""
    if puan >= 90:
        return "AA"
    elif puan >= 85:
        return "BA"
    elif puan >= 80:
        return "BB"
    elif puan >= 75:
        return "CB"
    elif puan >= 70:
        return "CC"
    elif puan >= 65:
        return "DC"
    elif puan >= 60:
        return "DD"
    elif puan >= 50:
        return "FD"
    else:
        return "FF"

# Ana program
puan = int(input("Puanınızı girin: "))
harf = harf_notu_bul(puan)
print(f"Harf notunuz: {harf}")
```

---

### Örnek 2.4: En Büyük Sayıyı Bulma (3 Sayı)

**Normal Hali:**
```python
sayi1 = int(input("Birinci sayı: "))
sayi2 = int(input("İkinci sayı: "))
sayi3 = int(input("Üçüncü sayı: "))

if sayi1 >= sayi2 and sayi1 >= sayi3:
    en_buyuk = sayi1
elif sayi2 >= sayi1 and sayi2 >= sayi3:
    en_buyuk = sayi2
else:
    en_buyuk = sayi3

print(f"En büyük sayı: {en_buyuk}")
```

**Fonksiyonlu Hali:**
```python
def en_buyugu_bul(sayi1, sayi2, sayi3):
    """Üç sayıdan en büyüğünü bulur"""
    if sayi1 >= sayi2 and sayi1 >= sayi3:
        return sayi1
    elif sayi2 >= sayi1 and sayi2 >= sayi3:
        return sayi2
    else:
        return sayi3

# Ana program
a = int(input("Birinci sayı: "))
b = int(input("İkinci sayı: "))
c = int(input("Üçüncü sayı: "))

sonuc = en_buyugu_bul(a, b, c)
print(f"En büyük sayı: {sonuc}")
```

---

### Örnek 2.5: Yaş Kontrolü (Ehliyet)

**Normal Hali:**
```python
yas = int(input("Yaşınızı girin: "))

if yas < 0:
    print("Geçersiz yaş!")
elif yas < 18:
    print("Ehliyet alamazsınız")
elif yas <= 65:
    print("Ehliyet alabilirsiniz")
else:
    print("Sağlık raporu gerekli")
```

**Fonksiyonlu Hali:**
```python
def ehliyet_durumu(yas):
    """Yaşa göre ehliyet durumunu kontrol eder"""
    if yas < 0:
        return "Geçersiz yaş!"
    elif yas < 18:
        return "Ehliyet alamazsınız"
    elif yas <= 65:
        return "Ehliyet alabilirsiniz"
    else:
        return "Sağlık raporu gerekli"

# Ana program
kullanici_yasi = int(input("Yaşınızı girin: "))
durum = ehliyet_durumu(kullanici_yasi)
print(durum)
```

---

### Örnek 2.6: Artık Yıl Kontrolü

**Normal Hali:**
```python
yil = int(input("Yıl girin: "))

if (yil % 4 == 0 and yil % 100 != 0) or (yil % 400 == 0):
    print(f"{yil} artık yıldır")
else:
    print(f"{yil} artık yıl değildir")
```

**Fonksiyonlu Hali:**
```python
def artik_yil_mi(yil):
    """Yılın artık yıl olup olmadığını kontrol eder"""
    if (yil % 4 == 0 and yil % 100 != 0) or (yil % 400 == 0):
        return True
    else:
        return False

# Ana program
girilen_yil = int(input("Yıl girin: "))

if artik_yil_mi(girilen_yil):
    print(f"{girilen_yil} artık yıldır")
else:
    print(f"{girilen_yil} artık yıl değildir")
```

---

## 📌 3. MATCH-CASE (SWITCH-CASE)

### Örnek 3.1: Basit Hesap Makinesi

**Normal Hali:**
```python
print("=== HESAP MAKİNESİ ===")
print("1. Toplama")
print("2. Çıkarma")
print("3. Çarpma")
print("4. Bölme")

secim = input("Seçiminiz (1-4): ")
sayi1 = float(input("Birinci sayı: "))
sayi2 = float(input("İkinci sayı: "))

match secim:
    case "1":
        sonuc = sayi1 + sayi2
        print(f"Sonuç: {sonuc}")
    case "2":
        sonuc = sayi1 - sayi2
        print(f"Sonuç: {sonuc}")
    case "3":
        sonuc = sayi1 * sayi2
        print(f"Sonuç: {sonuc}")
    case "4":
        if sayi2 != 0:
            sonuc = sayi1 / sayi2
            print(f"Sonuç: {sonuc}")
        else:
            print("Sıfıra bölünemez!")
    case _:
        print("Geçersiz seçim!")
```

**Fonksiyonlu Hali:**
```python
def toplama(a, b):
    return a + b

def cikarma(a, b):
    return a - b

def carpma(a, b):
    return a * b

def bolme(a, b):
    if b != 0:
        return a / b
    else:
        return "Sıfıra bölünemez!"

def hesap_makinesi(secim, sayi1, sayi2):
    """Seçime göre işlem yapar"""
    match secim:
        case "1":
            return toplama(sayi1, sayi2)
        case "2":
            return cikarma(sayi1, sayi2)
        case "3":
            return carpma(sayi1, sayi2)
        case "4":
            return bolme(sayi1, sayi2)
        case _:
            return "Geçersiz seçim!"

# Ana program
print("1.Toplama 2.Çıkarma 3.Çarpma 4.Bölme")
kullanici_secimi = input("Seçiminiz: ")
a = float(input("Birinci sayı: "))
b = float(input("İkinci sayı: "))

sonuc = hesap_makinesi(kullanici_secimi, a, b)
print(f"Sonuç: {sonuc}")
```

---

### Örnek 3.2: Alışveriş Sistemi (ÖNEMLİ!)

**Normal Hali:**
```python
sepet = []
toplam_tutar = 0

while True:
    print("\n=== ALIŞVERİŞ SİSTEMİ ===")
    print("1. Elma (5 TL)")
    print("2. Ekmek (10 TL)")
    print("3. Süt (25 TL)")
    print("4. Peynir (50 TL)")
    print("5. Sepeti Gör")
    print("6. Ödeme Yap")
    
    secim = input("Seçiminiz: ")
    
    match secim:
        case "1":
            sepet.append("Elma")
            toplam_tutar += 5
            print("✓ Elma eklendi!")
        case "2":
            sepet.append("Ekmek")
            toplam_tutar += 10
            print("✓ Ekmek eklendi!")
        case "3":
            sepet.append("Süt")
            toplam_tutar += 25
            print("✓ Süt eklendi!")
        case "4":
            sepet.append("Peynir")
            toplam_tutar += 50
            print("✓ Peynir eklendi!")
        case "5":
            print(f"Sepet: {sepet}")
            print(f"Toplam: {toplam_tutar} TL")
        case "6":
            print("\n=== FİŞ ===")
            for urun in sepet:
                print(f"- {urun}")
            print(f"TOPLAM: {toplam_tutar} TL")
            break
        case _:
            print("Geçersiz seçim!")
```

**Fonksiyonlu Hali:**
```python
def urun_ekle(sepet, urun_adi, fiyat, toplam):
    """Sepete ürün ekler"""
    sepet.append(urun_adi)
    toplam += fiyat
    print(f"✓ {urun_adi} eklendi!")
    return toplam

def sepeti_goster(sepet, toplam):
    """Sepeti gösterir"""
    print(f"Sepet: {sepet}")
    print(f"Toplam: {toplam} TL")

def fis_yazdir(sepet, toplam):
    """Fişi yazdırır"""
    print("\n=== FİŞ ===")
    for urun in sepet:
        print(f"- {urun}")
    print(f"TOPLAM: {toplam} TL")

def alisveris_yap():
    """Ana alışveriş fonksiyonu"""
    sepet = []
    toplam_tutar = 0
    
    while True:
        print("\n1.Elma(5TL) 2.Ekmek(10TL) 3.Süt(25TL) 4.Peynir(50TL) 5.Sepet 6.Ödeme")
        secim = input("Seçim: ")
        
        match secim:
            case "1":
                toplam_tutar = urun_ekle(sepet, "Elma", 5, toplam_tutar)
            case "2":
                toplam_tutar = urun_ekle(sepet, "Ekmek", 10, toplam_tutar)
            case "3":
                toplam_tutar = urun_ekle(sepet, "Süt", 25, toplam_tutar)
            case "4":
                toplam_tutar = urun_ekle(sepet, "Peynir", 50, toplam_tutar)
            case "5":
                sepeti_goster(sepet, toplam_tutar)
            case "6":
                fis_yazdir(sepet, toplam_tutar)
                break
            case _:
                print("Geçersiz!")

# Programı başlat
alisveris_yap()
```

---

### Örnek 3.3: Gün Adı Bulma

**Normal Hali:**
```python
gun_numarasi = int(input("Gün numarası (1-7): "))

match gun_numarasi:
    case 1:
        print("Pazartesi")
    case 2:
        print("Salı")
    case 3:
        print("Çarşamba")
    case 4:
        print("Perşembe")
    case 5:
        print("Cuma")
    case 6:
        print("Cumartesi")
    case 7:
        print("Pazar")
    case _:
        print("Geçersiz gün!")
```

**Fonksiyonlu Hali:**
```python
def gun_adi_bul(numara):
    """Numaraya göre gün adını döndürür"""
    match numara:
        case 1:
            return "Pazartesi"
        case 2:
            return "Salı"
        case 3:
            return "Çarşamba"
        case 4:
            return "Perşembe"
        case 5:
            return "Cuma"
        case 6:
            return "Cumartesi"
        case 7:
            return "Pazar"
        case _:
            return "Geçersiz gün!"

# Ana program
numara = int(input("Gün numarası: "))
gun = gun_adi_bul(numara)
print(gun)
```

---

## 📌 4. WHILE DÖNGÜSÜ

### Örnek 4.1: 1'den N'e Kadar Sayıları Yazdırma

**Normal Hali:**
```python
n = int(input("N değeri: "))
sayac = 1

while sayac <= n:
    print(sayac)
    sayac += 1
```

**Fonksiyonlu Hali:**
```python
def sayilari_yazdir(n):
    """1'den n'e kadar sayıları yazdırır"""
    sayac = 1
    while sayac <= n:
        print(sayac)
        sayac += 1

# Ana program
deger = int(input("N değeri: "))
sayilari_yazdir(deger)
```

---

### Örnek 4.2: 1'den N'e Kadar Toplam

**Normal Hali:**
```python
n = int(input("N değeri: "))
sayac = 1
toplam = 0

while sayac <= n:
    toplam += sayac
    sayac += 1

print(f"1'den {n}'e kadar toplam: {toplam}")
```

**Fonksiyonlu Hali:**
```python
def toplam_hesapla(n):
    """1'den n'e kadar sayıların toplamını hesaplar"""
    sayac = 1
    toplam = 0
    
    while sayac <= n:
        toplam += sayac
        sayac += 1
    
    return toplam

# Ana program
deger = int(input("N değeri: "))
sonuc = toplam_hesapla(deger)
print(f"Toplam: {sonuc}")
```

---

### Örnek 4.3: Faktöriyel Hesaplama

**Normal Hali:**
```python
n = int(input("Sayı girin: "))
faktoriyel = 1
sayac = 1

while sayac <= n:
    faktoriyel *= sayac  # faktoriyel = faktoriyel * sayac
    sayac += 1

print(f"{n}! = {faktoriyel}")
```

**Fonksiyonlu Hali:**
```python
def faktoriyel_hesapla(n):
    """n! değerini hesaplar"""
    sonuc = 1
    sayac = 1
    
    while sayac <= n:
        sonuc *= sayac
        sayac += 1
    
    return sonuc

# Ana program
sayi = int(input("Sayı girin: "))
sonuc = faktoriyel_hesapla(sayi)
print(f"{sayi}! = {sonuc}")
```

---

### Örnek 4.4: Sayı Tahmin Oyunu

**Normal Hali:**
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

**Fonksiyonlu Hali:**
```python
import random

def ipucu_ver(tahmin, gizli):
    """Tahmine göre ipucu verir"""
    if tahmin < gizli:
        return "Daha büyük!"
    elif tahmin > gizli:
        return "Daha küçük!"
    else:
        return "dogru"

def oyunu_oyna():
    """Tahmin oyununu başlatır"""
    gizli_sayi = random.randint(1, 100)
    deneme = 0
    
    print("1-100 arası sayı tuttum!")
    
    while True:
        tahmin = int(input("Tahmin: "))
        deneme += 1
        
        sonuc = ipucu_ver(tahmin, gizli_sayi)
        
        if sonuc == "dogru":
            print(f"Tebrikler! {deneme} denemede buldunuz!")
            break
        else:
            print(sonuc)

# Oyunu başlat
oyunu_oyna()
```

---

### Örnek 4.5: Şifre Kontrolü (3 Deneme Hakkı)

**Normal Hali:**
```python
dogru_sifre = "python123"
kalan_hak = 3

while kalan_hak > 0:
    girilen = input("Şifre: ")
    
    if girilen == dogru_sifre:
        print("Giriş başarılı!")
        break
    else:
        kalan_hak -= 1
        print(f"Yanlış! {kalan_hak} hak kaldı.")

if kalan_hak == 0:
    print("Hesap kilitlendi!")
```

**Fonksiyonlu Hali:**
```python
def sifre_kontrol(girilen, dogru):
    """Şifrenin doğru olup olmadığını kontrol eder"""
    return girilen == dogru

def giris_yap():
    """Giriş işlemini yönetir"""
    dogru_sifre = "python123"
    kalan_hak = 3
    
    while kalan_hak > 0:
        girilen = input("Şifre: ")
        
        if sifre_kontrol(girilen, dogru_sifre):
            print("Giriş başarılı!")
            return True
        else:
            kalan_hak -= 1
            print(f"Yanlış! {kalan_hak} hak kaldı.")
    
    print("Hesap kilitlendi!")
    return False

# Programı başlat
giris_yap()
```

---

### Örnek 4.6: Basamak Sayısı Bulma

**Normal Hali:**
```python
sayi = int(input("Sayı girin: "))
basamak_sayisi = 0
gecici = sayi

while gecici > 0:
    gecici = gecici // 10
    basamak_sayisi += 1

print(f"{sayi} sayısı {basamak_sayisi} basamaklıdır")
```

**Fonksiyonlu Hali:**
```python
def basamak_say(sayi):
    """Sayının kaç basamaklı olduğunu bulur"""
    sayac = 0
    
    if sayi == 0:
        return 1
    
    while sayi > 0:
        sayi = sayi // 10
        sayac += 1
    
    return sayac

# Ana program
girilen = int(input("Sayı girin: "))
sonuc = basamak_say(girilen)
print(f"{sonuc} basamaklıdır")
```

---

### Örnek 4.7: Rakamlar Toplamı

**Normal Hali:**
```python
sayi = int(input("Sayı girin: "))
toplam = 0
gecici = sayi

while gecici > 0:
    son_rakam = gecici % 10
    toplam += son_rakam
    gecici = gecici // 10

print(f"{sayi} sayısının rakamları toplamı: {toplam}")
```

**Fonksiyonlu Hali:**
```python
def rakam_toplami_bul(sayi):
    """Sayının rakamlarının toplamını bulur"""
    toplam = 0
    
    while sayi > 0:
        son_rakam = sayi % 10
        toplam += son_rakam
        sayi = sayi // 10
    
    return toplam

# Ana program
girilen = int(input("Sayı girin: "))
sonuc = rakam_toplami_bul(girilen)
print(f"Rakamlar toplamı: {sonuc}")
```

---

## 📌 5. FOR DÖNGÜSÜ

### Örnek 5.1: Liste Elemanlarını Yazdırma

**Normal Hali:**
```python
meyveler = ["elma", "armut", "muz", "çilek"]

for meyve in meyveler:
    print(meyve)
```

**Fonksiyonlu Hali:**
```python
def listeyi_yazdir(liste):
    """Liste elemanlarını yazdırır"""
    for eleman in liste:
        print(eleman)

# Ana program
meyveler = ["elma", "armut", "muz", "çilek"]
listeyi_yazdir(meyveler)
```

---

### Örnek 5.2: Çarpım Tablosu

**Normal Hali:**
```python
sayi = int(input("Hangi sayının çarpım tablosu: "))

for i in range(1, 11):
    sonuc = sayi * i
    print(f"{sayi} x {i} = {sonuc}")
```

**Fonksiyonlu Hali:**
```python
def carpim_tablosu(sayi):
    """Bir sayının çarpım tablosunu yazdırır"""
    for i in range(1, 11):
        sonuc = sayi * i
        print(f"{sayi} x {i} = {sonuc}")

# Ana program
n = int(input("Sayı: "))
carpim_tablosu(n)
```

---

### Örnek 5.3: Liste Toplamı ve Ortalaması

**Normal Hali:**
```python
notlar = [70, 85, 90, 65, 80]
toplam = 0

for nott in notlar:
    toplam += nott

ortalama = toplam / len(notlar)
print(f"Toplam: {toplam}")
print(f"Ortalama: {ortalama}")
```

**Fonksiyonlu Hali:**
```python
def toplam_bul(liste):
    """Listenin toplamını bulur"""
    toplam = 0
    for eleman in liste:
        toplam += eleman
    return toplam

def ortalama_bul(liste):
    """Listenin ortalamasını bulur"""
    toplam = toplam_bul(liste)
    return toplam / len(liste)

# Ana program
notlar = [70, 85, 90, 65, 80]
print(f"Toplam: {toplam_bul(notlar)}")
print(f"Ortalama: {ortalama_bul(notlar)}")
```

---

### Örnek 5.4: En Büyük ve En Küçük Sayı

**Normal Hali:**
```python
sayilar = [23, 45, 12, 67, 34, 89, 5]

en_buyuk = sayilar[0]
en_kucuk = sayilar[0]

for sayi in sayilar:
    if sayi > en_buyuk:
        en_buyuk = sayi
    if sayi < en_kucuk:
        en_kucuk = sayi

print(f"En büyük: {en_buyuk}")
print(f"En küçük: {en_kucuk}")
```

**Fonksiyonlu Hali:**
```python
def en_buyuk_bul(liste):
    """Listedeki en büyük sayıyı bulur"""
    en_buyuk = liste[0]
    for sayi in liste:
        if sayi > en_buyuk:
            en_buyuk = sayi
    return en_buyuk

def en_kucuk_bul(liste):
    """Listedeki en küçük sayıyı bulur"""
    en_kucuk = liste[0]
    for sayi in liste:
        if sayi < en_kucuk:
            en_kucuk = sayi
    return en_kucuk

# Ana program
sayilar = [23, 45, 12, 67, 34, 89, 5]
print(f"En büyük: {en_buyuk_bul(sayilar)}")
print(f"En küçük: {en_kucuk_bul(sayilar)}")
```

---

### Örnek 5.5: Çift Sayıları Bulma

**Normal Hali:**
```python
sayilar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
cift_sayilar = []

for sayi in sayilar:
    if sayi % 2 == 0:
        cift_sayilar.append(sayi)

print(f"Çift sayılar: {cift_sayilar}")
```

**Fonksiyonlu Hali:**
```python
def cift_sayilari_bul(liste):
    """Listedeki çift sayıları bulur"""
    ciftler = []
    for sayi in liste:
        if sayi % 2 == 0:
            ciftler.append(sayi)
    return ciftler

# Ana program
sayilar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
sonuc = cift_sayilari_bul(sayilar)
print(f"Çift sayılar: {sonuc}")
```

---

### Örnek 5.6: String'deki Sesli Harfleri Sayma

**Normal Hali:**
```python
cumle = input("Bir cümle girin: ")
sesli_harfler = "aeıioöuüAEIİOÖUÜ"
sayac = 0

for harf in cumle:
    if harf in sesli_harfler:
        sayac += 1

print(f"Sesli harf sayısı: {sayac}")
```

**Fonksiyonlu Hali:**
```python
def sesli_harf_say(metin):
    """Metindeki sesli harfleri sayar"""
    sesli_harfler = "aeıioöuüAEIİOÖUÜ"
    sayac = 0
    
    for harf in metin:
        if harf in sesli_harfler:
            sayac += 1
    
    return sayac

# Ana program
cumle = input("Cümle girin: ")
sonuc = sesli_harf_say(cumle)
print(f"Sesli harf sayısı: {sonuc}")
```

---

## 📌 6. İÇ İÇE DÖNGÜLER

### Örnek 6.1: Dikdörtgen Çizme

**Normal Hali:**
```python
satir = 4
sutun = 6

for i in range(satir):
    for j in range(sutun):
        print("*", end="")
    print()
```

**Fonksiyonlu Hali:**
```python
def dikdortgen_ciz(satir, sutun):
    """Yıldızlarla dikdörtgen çizer"""
    for i in range(satir):
        for j in range(sutun):
            print("*", end="")
        print()

# Ana program
dikdortgen_ciz(4, 6)
```

---

### Örnek 6.2: Üçgen Çizme

**Normal Hali:**
```python
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

**Fonksiyonlu Hali:**
```python
def ucgen_ciz(yukseklik):
    """Yıldızlarla üçgen çizer"""
    for i in range(1, yukseklik + 1):
        for j in range(i):
            print("*", end="")
        print()

# Ana program
ucgen_ciz(5)
```

---

### Örnek 6.3: Ters Üçgen

**Normal Hali:**
```python
satir_sayisi = 5

for i in range(satir_sayisi, 0, -1):
    for j in range(i):
        print("*", end="")
    print()

# Çıktı:
# *****
# ****
# ***
# **
# *
```

**Fonksiyonlu Hali:**
```python
def ters_ucgen_ciz(yukseklik):
    """Ters üçgen çizer"""
    for i in range(yukseklik, 0, -1):
        for j in range(i):
            print("*", end="")
        print()

# Ana program
ters_ucgen_ciz(5)
```

---

### Örnek 6.4: Çarpım Tablosu (1-10 Arası)

**Normal Hali:**
```python
for i in range(1, 11):
    for j in range(1, 11):
        sonuc = i * j
        print(f"{sonuc:4}", end="")
    print()
```

**Fonksiyonlu Hali:**
```python
def carpim_tablosu_olustur(baslangic, bitis):
    """Çarpım tablosu oluşturur"""
    for i in range(baslangic, bitis + 1):
        for j in range(baslangic, bitis + 1):
            sonuc = i * j
            print(f"{sonuc:4}", end="")
        print()

# Ana program
carpim_tablosu_olustur(1, 10)
```

---

### ⭐ Örnek 6.5: Asal Sayıları Bulma (ÖNEMLİ!)

**Normal Hali:**
```python
print("2-100 arası asal sayılar:")

for sayi in range(2, 101):
    asal_mi = True
    
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            asal_mi = False
            break
    
    if asal_mi:
        print(sayi, end=" ")
```

**Fonksiyonlu Hali:**
```python
def asal_mi_kontrol(sayi):
    """Bir sayının asal olup olmadığını kontrol eder"""
    if sayi < 2:
        return False
    
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            return False
    
    return True

def asal_sayilari_bul(baslangic, bitis):
    """Aralıktaki asal sayıları bulur"""
    asallar = []
    
    for sayi in range(baslangic, bitis + 1):
        if asal_mi_kontrol(sayi):
            asallar.append(sayi)
    
    return asallar

# Ana program
sonuc = asal_sayilari_bul(2, 100)
print("Asal sayılar:", sonuc)
print(f"Toplam {len(sonuc)} adet asal sayı var")
```

---

### Örnek 6.6: Mükemmel Sayı Bulma

**Normal Hali:**
```python
# Mükemmel sayı: Kendisi hariç bölenlerinin toplamı kendisine eşit
# Örnek: 6 = 1 + 2 + 3

print("1-1000 arası mükemmel sayılar:")

for sayi in range(1, 1001):
    bolenler_toplami = 0
    
    for bolen in range(1, sayi):
        if sayi % bolen == 0:
            bolenler_toplami += bolen
    
    if bolenler_toplami == sayi:
        print(sayi, end=" ")
```

**Fonksiyonlu Hali:**
```python
def mukemmel_mi(sayi):
    """Sayının mükemmel sayı olup olmadığını kontrol eder"""
    bolenler_toplami = 0
    
    for bolen in range(1, sayi):
        if sayi % bolen == 0:
            bolenler_toplami += bolen
    
    return bolenler_toplami == sayi

def mukemmel_sayilari_bul(baslangic, bitis):
    """Aralıktaki mükemmel sayıları bulur"""
    mukemmeller = []
    
    for sayi in range(baslangic, bitis + 1):
        if mukemmel_mi(sayi):
            mukemmeller.append(sayi)
    
    return mukemmeller

# Ana program
sonuc = mukemmel_sayilari_bul(1, 1000)
print("Mükemmel sayılar:", sonuc)
```

---

## 📌 7. LİSTELER

### Örnek 7.1: Liste Oluşturma ve Elemanları Yazdırma

**Normal Hali:**
```python
ogrenciler = ["Ali", "Veli", "Ayşe", "Fatma", "Mehmet"]

print("Öğrenci listesi:")
for i in range(len(ogrenciler)):
    print(f"{i+1}. {ogrenciler[i]}")
```

**Fonksiyonlu Hali:**
```python
def numarali_liste_yazdir(liste, baslik):
    """Listeyi numaralı olarak yazdırır"""
    print(baslik)
    for i in range(len(liste)):
        print(f"{i+1}. {liste[i]}")

# Ana program
ogrenciler = ["Ali", "Veli", "Ayşe", "Fatma"]
numarali_liste_yazdir(ogrenciler, "Öğrenci Listesi:")
```

---

### Örnek 7.2: Listeye Eleman Ekleme/Silme

**Normal Hali:**
```python
liste = [1, 2, 3]

# Sona ekleme
liste.append(4)
print(f"Append sonrası: {liste}")

# Belirli indekse ekleme
liste.insert(0, 0)
print(f"Insert sonrası: {liste}")

# Değere göre silme
liste.remove(2)
print(f"Remove sonrası: {liste}")

# İndekse göre silme
silinen = liste.pop(0)
print(f"Pop sonrası: {liste}, silinen: {silinen}")
```

**Fonksiyonlu Hali:**
```python
def sona_ekle(liste, eleman):
    """Listenin sonuna eleman ekler"""
    liste.append(eleman)
    return liste

def basa_ekle(liste, eleman):
    """Listenin başına eleman ekler"""
    liste.insert(0, eleman)
    return liste

def eleman_sil(liste, eleman):
    """Listeden elemanı siler"""
    if eleman in liste:
        liste.remove(eleman)
    return liste

# Ana program
sayilar = [1, 2, 3]
sayilar = sona_ekle(sayilar, 4)
print(sayilar)  # [1, 2, 3, 4]
```

---

### Örnek 7.3: Listeyi Sıralama

**Normal Hali:**
```python
sayilar = [64, 34, 25, 12, 22, 11, 90]

# Küçükten büyüğe
sayilar.sort()
print(f"Artan sıra: {sayilar}")

# Büyükten küçüğe
sayilar.sort(reverse=True)
print(f"Azalan sıra: {sayilar}")
```

**Fonksiyonlu Hali:**
```python
def artan_sirala(liste):
    """Listeyi küçükten büyüğe sıralar"""
    kopya = liste.copy()
    kopya.sort()
    return kopya

def azalan_sirala(liste):
    """Listeyi büyükten küçüğe sıralar"""
    kopya = liste.copy()
    kopya.sort(reverse=True)
    return kopya

# Ana program
sayilar = [64, 34, 25, 12, 22]
print(f"Artan: {artan_sirala(sayilar)}")
print(f"Azalan: {azalan_sirala(sayilar)}")
```

---

### ⭐ Örnek 7.4: Asal Sayıları Listeye Ekleme

**Normal Hali:**
```python
asal_liste = []

for sayi in range(2, 51):
    asal = True
    
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            asal = False
            break
    
    if asal:
        asal_liste.append(sayi)

print(f"Asal sayılar: {asal_liste}")
print(f"Toplam: {len(asal_liste)} adet")
```

**Fonksiyonlu Hali:**
```python
def asal_mi(sayi):
    """Sayının asal olup olmadığını kontrol eder"""
    if sayi < 2:
        return False
    for bolen in range(2, sayi):
        if sayi % bolen == 0:
            return False
    return True

def asal_listesi_olustur(baslangic, bitis):
    """Aralıktaki asal sayıların listesini oluşturur"""
    liste = []
    for sayi in range(baslangic, bitis + 1):
        if asal_mi(sayi):
            liste.append(sayi)
    return liste

# Ana program
asallar = asal_listesi_olustur(2, 50)
print(f"Asallar: {asallar}")
```

---

### ⭐ Örnek 7.5: Adam Asmaca Oyunu (LİSTELERLE)

```python
import random

def kelime_sec(kelimeler):
    """Listeden rastgele kelime seçer"""
    return random.choice(kelimeler)

def gorunum_olustur(kelime):
    """Kelimenin görünümünü oluşturur (alt çizgilerle)"""
    return ["_"] * len(kelime)

def harf_kontrol(harf, kelime, gorunum):
    """Harfin kelimede olup olmadığını kontrol eder"""
    bulundu = False
    for i in range(len(kelime)):
        if kelime[i] == harf:
            gorunum[i] = harf
            bulundu = True
    return bulundu

def oyun_bitti_mi(gorunum):
    """Oyunun bitip bitmediğini kontrol eder"""
    return "_" not in gorunum

def adam_asmaca():
    """Adam asmaca oyununu başlatır"""
    kelimeler = ["python", "algoritma", "bilgisayar", "klavye", "programlama"]
    gizli_kelime = kelime_sec(kelimeler)
    gorunum = gorunum_olustur(gizli_kelime)
    yanlis_harfler = []
    can = 6
    
    print("=== ADAM ASMACA ===")
    
    while can > 0 and not oyun_bitti_mi(gorunum):
        print(f"\nKelime: {' '.join(gorunum)}")
        print(f"Yanlış harfler: {yanlis_harfler}")
        print(f"Kalan can: {can}")
        
        tahmin = input("Harf girin: ").lower()
        
        if len(tahmin) != 1:
            print("Tek harf girin!")
            continue
        
        if tahmin in gorunum or tahmin in yanlis_harfler:
            print("Bu harfi denediniz!")
            continue
        
        if harf_kontrol(tahmin, gizli_kelime, gorunum):
            print("Doğru!")
        else:
            print("Yanlış!")
            yanlis_harfler.append(tahmin)
            can -= 1
    
    if oyun_bitti_mi(gorunum):
        print(f"\n🎉 TEBRİKLER! Kelime: {gizli_kelime}")
    else:
        print(f"\n💀 KAYBETTİNİZ! Kelime: {gizli_kelime}")

# Oyunu başlat
adam_asmaca()
```

---

## 📌 8. KISA DEVRE DEĞERLENDİRME

### Örnek 8.1: AND Kısa Devre

```python
def kontrol_yap(deger):
    """Kontrol fonksiyonu"""
    print("Fonksiyon çalıştı!")
    return deger

# False AND durumu - ikinci kısım çalışmaz
sonuc = False and kontrol_yap(True)
print(f"Sonuç: {sonuc}")
# Çıktı: Sonuç: False (Fonksiyon çalışmadı!)

# True AND durumu - ikinci kısım çalışır
sonuc = True and kontrol_yap(True)
print(f"Sonuç: {sonuc}")
# Çıktı: Fonksiyon çalıştı!
#        Sonuç: True
```

### Örnek 8.2: OR Kısa Devre

```python
def kontrol_yap(deger):
    """Kontrol fonksiyonu"""
    print("Fonksiyon çalıştı!")
    return deger

# True OR durumu - ikinci kısım çalışmaz
sonuc = True or kontrol_yap(False)
print(f"Sonuç: {sonuc}")
# Çıktı: Sonuç: True (Fonksiyon çalışmadı!)

# False OR durumu - ikinci kısım çalışır
sonuc = False or kontrol_yap(True)
print(f"Sonuç: {sonuc}")
# Çıktı: Fonksiyon çalıştı!
#        Sonuç: True
```

### Örnek 8.3: Sıfıra Bölme Koruması

```python
def guvenli_bolme(bolunen, bolen):
    """Sıfıra bölme hatasından korunan bölme"""
    # Kısa devre: bolen 0 ise ikinci kısım çalışmaz
    if bolen != 0 and bolunen / bolen > 5:
        return "Sonuç 5'ten büyük"
    elif bolen == 0:
        return "Sıfıra bölünemez!"
    else:
        return f"Sonuç: {bolunen / bolen}"

print(guvenli_bolme(10, 0))  # Sıfıra bölünemez!
print(guvenli_bolme(30, 5))  # Sonuç 5'ten büyük
```

### Örnek 8.4: Liste Boş Kontrolü

```python
def ilk_elemani_al(liste):
    """Listenin ilk elemanını güvenle alır"""
    # Kısa devre: liste boşsa ikinci kısım çalışmaz
    if len(liste) > 0 and liste[0] > 10:
        return f"İlk eleman 10'dan büyük: {liste[0]}"
    elif len(liste) == 0:
        return "Liste boş!"
    else:
        return f"İlk eleman: {liste[0]}"

print(ilk_elemani_al([]))         # Liste boş!
print(ilk_elemani_al([15, 20]))   # İlk eleman 10'dan büyük: 15
print(ilk_elemani_al([5, 10]))    # İlk eleman: 5
```

---

## 📌 9. LEN() FONKSİYONU ÖRNEKLERİ

### Örnek 9.1: String Uzunluğu

```python
def karakter_say(metin):
    """Metindeki karakter sayısını döndürür"""
    return len(metin)

isim = "Muhammed"
print(f"{isim} ismi {karakter_say(isim)} karakterdir")  # 8
```

### Örnek 9.2: Şifre Uzunluk Kontrolü

```python
def sifre_gecerli_mi(sifre):
    """Şifrenin geçerli uzunlukta olup olmadığını kontrol eder"""
    if len(sifre) < 6:
        return "Şifre en az 6 karakter olmalı!"
    elif len(sifre) > 20:
        return "Şifre en fazla 20 karakter olabilir!"
    else:
        return "Şifre geçerli!"

print(sifre_gecerli_mi("abc"))        # En az 6 karakter
print(sifre_gecerli_mi("python123"))  # Geçerli
```

### Örnek 9.3: Liste Eleman Sayısı

```python
def liste_bilgisi(liste):
    """Liste hakkında bilgi verir"""
    eleman_sayisi = len(liste)
    
    if eleman_sayisi == 0:
        return "Liste boş!"
    else:
        return f"Listede {eleman_sayisi} eleman var"

ogrenciler = ["Ali", "Veli", "Ayşe"]
print(liste_bilgisi(ogrenciler))  # 3 eleman
print(liste_bilgisi([]))          # Liste boş
```

### Örnek 9.4: Ortalama Hesaplama

```python
def ortalama_hesapla(notlar):
    """Not ortalamasını hesaplar"""
    if len(notlar) == 0:
        return "Liste boş!"
    
    toplam = 0
    for nott in notlar:
        toplam += nott
    
    return toplam / len(notlar)

ogrenci_notlari = [70, 85, 90, 65, 80]
print(f"Ortalama: {ortalama_hesapla(ogrenci_notlari)}")  # 78.0
```

---

## 📌 10. RECURSİVE (ÖZYİNELEMELİ) FONKSİYONLAR

### Örnek 10.1: Geri Sayım

```python
def geri_say(sayi):
    """Recursive geri sayım"""
    # Durma koşulu
    if sayi <= 0:
        print("Bitti!")
        return
    
    print(sayi)
    geri_say(sayi - 1)  # Kendini çağır

# Kullanım
geri_say(5)
# Çıktı: 5 4 3 2 1 Bitti!
```

### Örnek 10.2: Faktöriyel (Recursive)

```python
def faktoriyel(sayi):
    """Faktöriyel hesaplar (özyinelemeli)"""
    # Durma koşulu
    if sayi == 0 or sayi == 1:
        return 1
    
    # Recursive çağrı
    return sayi * faktoriyel(sayi - 1)

# 5! = 5 * 4 * 3 * 2 * 1 = 120
print(f"5! = {faktoriyel(5)}")  # 120
```

### Örnek 10.3: Fibonacci (Recursive)

```python
def fibonacci(n):
    """n. Fibonacci sayısını döndürür"""
    # Durma koşulları
    if n == 0:
        return 0
    if n == 1:
        return 1
    
    # Recursive çağrı
    return fibonacci(n - 1) + fibonacci(n - 2)

# İlk 10 Fibonacci sayısı
print("Fibonacci serisi:")
for i in range(10):
    print(fibonacci(i), end=" ")
# Çıktı: 0 1 1 2 3 5 8 13 21 34
```

### Örnek 10.4: Toplam (Recursive)

```python
def toplam_recursive(sayi):
    """1'den n'e kadar toplamı recursive hesaplar"""
    # Durma koşulu
    if sayi == 1:
        return 1
    
    return sayi + toplam_recursive(sayi - 1)

print(f"1+2+3+4+5 = {toplam_recursive(5)}")  # 15
```

### Örnek 10.5: Üs Alma (Recursive)

```python
def us_al(taban, us):
    """Üs hesaplar (özyinelemeli)"""
    # Durma koşulu
    if us == 0:
        return 1
    
    return taban * us_al(taban, us - 1)

print(f"2^5 = {us_al(2, 5)}")  # 32
print(f"3^4 = {us_al(3, 4)}")  # 81
```

### Örnek 10.6: Rakamlar Toplamı (Recursive)

```python
def rakam_toplami(sayi):
    """Sayının rakamlarının toplamını recursive bulur"""
    # Durma koşulu (tek basamak)
    if sayi < 10:
        return sayi
    
    son_rakam = sayi % 10
    kalan = sayi // 10
    return son_rakam + rakam_toplami(kalan)

print(f"123 -> {rakam_toplami(123)}")  # 6 (1+2+3)
print(f"9876 -> {rakam_toplami(9876)}")  # 30
```

### Örnek 10.7: String Ters Çevirme (Recursive)

```python
def ters_cevir(metin):
    """Metni recursive olarak ters çevirir"""
    # Durma koşulu
    if len(metin) <= 1:
        return metin
    
    return metin[-1] + ters_cevir(metin[:-1])

print(ters_cevir("python"))  # nohtyp
print(ters_cevir("merhaba"))  # abahrem
```
// ...existing code...

### Örnek 10.8: Palindrom Kontrolü (Recursive)
```python
# Palindrom: Tersten okunuşu aynı olan kelime (ana, aba, kazak)

# --- FONKSİYONSUZ ---
kelime = "kazak"
ters_kelime = kelime[::-1]

if kelime == ters_kelime:
    print(f"{kelime} palindromdur")
else:
    print(f"{kelime} palindrom değildir")


# --- FONKSİYONLU (Recursive) ---
def palindrom_mu(kelime):
    # Durma koşulu: 0 veya 1 harf kaldıysa palindromdur
    if len(kelime) <= 1:
        return True
    
    # İlk ve son harf farklıysa palindrom değil
    if kelime[0] != kelime[-1]:
        return False
    
    # Ortadaki kısmı kontrol et
    return palindrom_mu(kelime[1:-1])

# Test
test_kelimeler = ["ana", "kazak", "python", "aba", "radar"]
for k in test_kelimeler:
    if palindrom_mu(k):
        print(f"✓ {k} palindromdur")
    else:
        print(f"✗ {k} palindrom değildir")
```

---

### Örnek 10.9: Dizi Tersine Çevirme (Recursive)
```python
# --- FONKSİYONSUZ ---
liste = [1, 2, 3, 4, 5]
ters_liste = liste[::-1]
print(f"Ters: {ters_liste}")


# --- FONKSİYONLU (Recursive) ---
def listeyi_ters_cevir(liste):
    # Durma koşulu: boş veya tek elemanlı liste
    if len(liste) <= 1:
        return liste
    
    # Son eleman + kalan listenin tersi
    return [liste[-1]] + listeyi_ters_cevir(liste[:-1])

# Test
sayilar = [1, 2, 3, 4, 5]
sonuc = listeyi_ters_cevir(sayilar)
print(f"Orijinal: {sayilar}")
print(f"Ters: {sonuc}")
```

---

### Örnek 10.10: En Büyük Ortak Bölen - EBOB (Recursive)
```python
# EBOB: İki sayıyı bölen en büyük sayı

# --- FONKSİYONSUZ ---
sayi1 = 48
sayi2 = 18
a, b = sayi1, sayi2

while b != 0:
    kalan = a % b
    a = b
    b = kalan

print(f"EBOB({sayi1}, {sayi2}) = {a}")


# --- FONKSİYONLU (Recursive - Öklid Algoritması) ---
def ebob_bul(a, b):
    # Durma koşulu: b sıfır olduğunda a sonuçtur
    if b == 0:
        return a
    
    # Recursive çağrı
    return ebob_bul(b, a % b)

# Test
print(f"EBOB(48, 18) = {ebob_bul(48, 18)}")   # 6
print(f"EBOB(100, 25) = {ebob_bul(100, 25)}") # 25
print(f"EBOB(17, 5) = {ebob_bul(17, 5)}")     # 1
```

---

### Örnek 10.11: En Küçük Ortak Kat - EKOK (Recursive)
```python
# EKOK: İki sayının ortak katı olan en küçük sayı
# Formül: EKOK(a,b) = (a * b) / EBOB(a,b)

# --- FONKSİYONLU ---
def ebob_bul(a, b):
    if b == 0:
        return a
    return ebob_bul(b, a % b)

def ekok_bul(a, b):
    return (a * b) // ebob_bul(a, b)

# Test
print(f"EKOK(4, 6) = {ekok_bul(4, 6)}")     # 12
print(f"EKOK(3, 5) = {ekok_bul(3, 5)}")     # 15
print(f"EKOK(12, 18) = {ekok_bul(12, 18)}") # 36
```

---

### Örnek 10.12: İkili (Binary) Arama (Recursive)
```python
# Sıralı bir listede eleman arama

# --- FONKSİYONLU (Recursive) ---
def ikili_arama(liste, aranan, bas, son):
    # Durma koşulu: bulunamadı
    if bas > son:
        return -1
    
    # Ortayı bul
    orta = (bas + son) // 2
    
    if liste[orta] == aranan:
        return orta  # Bulundu, indeksi döndür
    elif liste[orta] > aranan:
        return ikili_arama(liste, aranan, bas, orta - 1)  # Sol tarafa bak
    else:
        return ikili_arama(liste, aranan, orta + 1, son)  # Sağ tarafa bak

# Test
sayilar = [2, 5, 8, 12, 16, 23, 38, 45, 56, 72, 91]
aranan_sayi = 23

sonuc = ikili_arama(sayilar, aranan_sayi, 0, len(sayilar) - 1)

if sonuc != -1:
    print(f"{aranan_sayi} sayısı {sonuc}. indekste bulundu")
else:
    print(f"{aranan_sayi} listede yok")
```

---

## 📌 BÖLÜM 11: LİSTE İŞLEMLERİ ÖRNEKLERİ

### Örnek 11.1: Listedeki Çift Sayıları Bulma
```python
# --- FONKSİYONSUZ ---
sayilar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
cift_sayilar = []

for sayi in sayilar:
    if sayi % 2 == 0:
        cift_sayilar.append(sayi)

print(f"Çift sayılar: {cift_sayilar}")


# --- FONKSİYONLU ---
def cift_sayilari_bul(liste):
    ciftler = []
    for sayi in liste:
        if sayi % 2 == 0:
            ciftler.append(sayi)
    return ciftler

# Test
tum_sayilar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
bulunan = cift_sayilari_bul(tum_sayilar)
print(f"Çift sayılar: {bulunan}")
```

---

### Örnek 11.2: Listedeki Tekrar Eden Elemanları Bulma
```python
# --- FONKSİYONSUZ ---
liste = [1, 2, 2, 3, 4, 4, 4, 5, 6, 6]
tekrar_edenler = []

for eleman in liste:
    if liste.count(eleman) > 1 and eleman not in tekrar_edenler:
        tekrar_edenler.append(eleman)

print(f"Tekrar edenler: {tekrar_edenler}")


# --- FONKSİYONLU ---
def tekrar_edenleri_bul(liste):
    tekrarlar = []
    for eleman in liste:
        sayi = liste.count(eleman)
        if sayi > 1 and eleman not in tekrarlar:
            tekrarlar.append(eleman)
    return tekrarlar

# Test
sayilar = [1, 2, 2, 3, 4, 4, 4, 5, 6, 6]
sonuc = tekrar_edenleri_bul(sayilar)
print(f"Tekrar eden elemanlar: {sonuc}")
```

---

### Örnek 11.3: İki Listeyi Birleştirip Sıralama
```python
# --- FONKSİYONSUZ ---
liste1 = [3, 1, 4]
liste2 = [2, 7, 5]

birlesik = liste1 + liste2
birlesik.sort()
print(f"Sıralı birleşik: {birlesik}")


# --- FONKSİYONLU ---
def birlestir_ve_sirala(liste1, liste2):
    birlesik = liste1 + liste2
    birlesik.sort()
    return birlesik

# Test
a = [3, 1, 4]
b = [2, 7, 5]
sonuc = birlestir_ve_sirala(a, b)
print(f"Sonuç: {sonuc}")
```

---

### Örnek 11.4: Listeden Belirli Değeri Silme
```python
# --- FONKSİYONSUZ ---
liste = [1, 2, 3, 2, 4, 2, 5]
silinecek = 2
yeni_liste = []

for eleman in liste:
    if eleman != silinecek:
        yeni_liste.append(eleman)

print(f"Yeni liste: {yeni_liste}")


# --- FONKSİYONLU ---
def degeri_sil(liste, deger):
    sonuc = []
    for eleman in liste:
        if eleman != deger:
            sonuc.append(eleman)
    return sonuc

# Test
sayilar = [1, 2, 3, 2, 4, 2, 5]
temiz = degeri_sil(sayilar, 2)
print(f"2 silindi: {temiz}")
```

---

### Örnek 11.5: Listedeki Pozitif ve Negatif Sayıları Ayırma
```python
# --- FONKSİYONSUZ ---
sayilar = [-3, 5, -1, 8, -2, 9, 0, -7]
pozitifler = []
negatifler = []

for sayi in sayilar:
    if sayi > 0:
        pozitifler.append(sayi)
    elif sayi < 0:
        negatifler.append(sayi)

print(f"Pozitifler: {pozitifler}")
print(f"Negatifler: {negatifler}")


# --- FONKSİYONLU ---
def pozitif_negatif_ayir(liste):
    pozitifler = []
    negatifler = []
    
    for sayi in liste:
        if sayi > 0:
            pozitifler.append(sayi)
        elif sayi < 0:
            negatifler.append(sayi)
    
    return pozitifler, negatifler

# Test
tum = [-3, 5, -1, 8, -2, 9, 0, -7]
poz, neg = pozitif_negatif_ayir(tum)
print(f"Pozitifler: {poz}")
print(f"Negatifler: {neg}")
```

---

## 📌 BÖLÜM 12: STRING İŞLEMLERİ ÖRNEKLERİ

### Örnek 12.1: Kelime Sayısı Bulma
```python
# --- FONKSİYONSUZ ---
cumle = "Python programlama dili çok güzel"
kelimeler = cumle.split()
kelime_sayisi = len(kelimeler)
print(f"Kelime sayısı: {kelime_sayisi}")


# --- FONKSİYONLU ---
def kelime_say(cumle):
    kelimeler = cumle.split()
    return len(kelimeler)

# Test
metin = "Python programlama dili çok güzel"
sayi = kelime_say(metin)
print(f"Kelime sayısı: {sayi}")
```

---

### Örnek 12.2: Sesli Harf Sayısı
```python
# --- FONKSİYONSUZ ---
kelime = "Algoritma"
sesli_harfler = "aeıioöuüAEIİOÖUÜ"
sayac = 0

for harf in kelime:
    if harf in sesli_harfler:
        sayac += 1

print(f"Sesli harf sayısı: {sayac}")


# --- FONKSİYONLU ---
def sesli_harf_say(kelime):
    sesli_harfler = "aeıioöuüAEIİOÖUÜ"
    sayac = 0
    
    for harf in kelime:
        if harf in sesli_harfler:
            sayac += 1
    
    return sayac

# Test
print(sesli_harf_say("Algoritma"))  # 4
print(sesli_harf_say("Python"))     # 1
```

---

### Örnek 12.3: Cümleyi Tersine Çevirme (Kelime Sırasını)
```python
# --- FONKSİYONSUZ ---
cumle = "Python öğrenmek çok eğlenceli"
kelimeler = cumle.split()
ters_kelimeler = kelimeler[::-1]
ters_cumle = " ".join(ters_kelimeler)
print(f"Ters: {ters_cumle}")


# --- FONKSİYONLU ---
def cumleyi_ters_cevir(cumle):
    kelimeler = cumle.split()
    ters = kelimeler[::-1]
    return " ".join(ters)

# Test
metin = "Python öğrenmek çok eğlenceli"
sonuc = cumleyi_ters_cevir(metin)
print(f"Ters: {sonuc}")
# Çıktı: "eğlenceli çok öğrenmek Python"
```

---

### Örnek 12.4: Her Kelimenin İlk Harfini Büyük Yapma
```python
# --- FONKSİYONSUZ ---
cumle = "python programlama dili"
kelimeler = cumle.split()
yeni_kelimeler = []

for kelime in kelimeler:
    yeni = kelime[0].upper() + kelime[1:]
    yeni_kelimeler.append(yeni)

sonuc = " ".join(yeni_kelimeler)
print(sonuc)


# --- FONKSİYONLU ---
def ilk_harfleri_buyut(cumle):
    kelimeler = cumle.split()
    yeni_kelimeler = []
    
    for kelime in kelimeler:
        buyuk = kelime[0].upper() + kelime[1:]
        yeni_kelimeler.append(buyuk)
    
    return " ".join(yeni_kelimeler)

# Test
metin = "python programlama dili"
sonuc = ilk_harfleri_buyut(metin)
print(sonuc)  # "Python Programlama Dili"
```

---

### Örnek 12.5: Şifreleme (Caesar Cipher)
```python
# Harfleri belirli sayıda kaydırarak şifreleme

# --- FONKSİYONLU ---
def sifrele(metin, kayma):
    harfler = "abcdefghijklmnopqrstuvwxyz"
    sifreli = ""
    
    for harf in metin.lower():
        if harf in harfler:
            eski_indeks = harfler.index(harf)
            yeni_indeks = (eski_indeks + kayma) % 26
            sifreli += harfler[yeni_indeks]
        else:
            sifreli += harf  # Harf değilse aynen ekle
    
    return sifreli

def sifre_coz(sifreli_metin, kayma):
    return sifrele(sifreli_metin, -kayma)

# Test
orijinal = "merhaba dunya"
sifreli = sifrele(orijinal, 3)
cozulmus = sifre_coz(sifreli, 3)

print(f"Orijinal: {orijinal}")
print(f"Şifreli: {sifreli}")
print(f"Çözülmüş: {cozulmus}")
```

---

## 📌 BÖLÜM 13: KAPSAMLI PROJELER

### Proje 1: Öğrenci Not Sistemi
```python
def ogrenci_ekle(ogrenciler, isim, notlar):
    """Öğrenci ekler"""
    ogrenciler.append({"isim": isim, "notlar": notlar})
    print(f"✓ {isim} eklendi")

def ortalama_hesapla(notlar):
    """Not ortalamasını hesaplar"""
    if len(notlar) == 0:
        return 0
    return sum(notlar) / len(notlar)

def harf_notu_bul(ortalama):
    """Ortalamaya göre harf notu döndürür"""
    if ortalama >= 90:
        return "AA"
    elif ortalama >= 80:
        return "BA"
    elif ortalama >= 70:
        return "BB"
    elif ortalama >= 60:
        return "CB"
    elif ortalama >= 50:
        return "CC"
    else:
        return "FF"

def gecme_durumu(ortalama):
    """Geçti mi kaldı mı?"""
    if ortalama >= 50:
        return "GEÇTİ"
    return "KALDI"

def ogrencileri_listele(ogrenciler):
    """Tüm öğrencileri listeler"""
    print("\n=== ÖĞRENCİ LİSTESİ ===")
    
    for ogr in ogrenciler:
        isim = ogr["isim"]
        notlar = ogr["notlar"]
        ort = ortalama_hesapla(notlar)
        harf = harf_notu_bul(ort)
        durum = gecme_durumu(ort)
        
        print(f"{isim}: {notlar} -> Ort: {ort:.1f} | {harf} | {durum}")

def sinif_ortalamasi_bul(ogrenciler):
    """Sınıf ortalamasını hesaplar"""
    if len(ogrenciler) == 0:
        return 0
    
    toplam = 0
    for ogr in ogrenciler:
        toplam += ortalama_hesapla(ogr["notlar"])
    
    return toplam / len(ogrenciler)

# === ANA PROGRAM ===
ogrenciler = []

# Öğrenci ekleme
ogrenci_ekle(ogrenciler, "Ali", [70, 80, 90])
ogrenci_ekle(ogrenciler, "Ayşe", [85, 90, 95])
ogrenci_ekle(ogrenciler, "Mehmet", [40, 50, 45])
ogrenci_ekle(ogrenciler, "Fatma", [60, 70, 65])

# Listeleme
ogrencileri_listele(ogrenciler)

# Sınıf ortalaması
sinif_ort = sinif_ortalamasi_bul(ogrenciler)
print(f"\nSınıf Ortalaması: {sinif_ort:.1f}")
```

---

### Proje 2: Basit Hesap Makinesi
```python
def topla(a, b):
    """İki sayıyı toplar"""
    return a + b

def cikar(a, b):
    """İki sayıyı çıkarır"""
    return a - b

def carp(a, b):
    """İki sayıyı çarpar"""
    return a * b

def bol(a, b):
    """İki sayıyı böler"""
    if b == 0:
        return "Hata: Sıfıra bölünemez!"
    return a / b

def us_al(a, b):
    """a üzeri b hesaplar"""
    return a ** b

def mod_al(a, b):
    """Bölümden kalan"""
    if b == 0:
        return "Hata: Sıfıra bölünemez!"
    return a % b

def hesap_makinesi():
    """Ana hesap makinesi fonksiyonu"""
    while True:
        print("\n=== HESAP MAKİNESİ ===")
        print("1. Toplama")
        print("2. Çıkarma")
        print("3. Çarpma")
        print("4. Bölme")
        print("5. Üs Alma")
        print("6. Mod (Kalan)")
        print("7. Çıkış")
        
        secim = input("Seçiminiz: ")
        
        if secim == "7":
            print("Güle güle!")
            break
        
        if secim not in ["1", "2", "3", "4", "5", "6"]:
            print("Geçersiz seçim!")
            continue
        
        sayi1 = float(input("Birinci sayı: "))
        sayi2 = float(input("İkinci sayı: "))
        
        match secim:
            case "1":
                sonuc = topla(sayi1, sayi2)
                islem = "+"
            case "2":
                sonuc = cikar(sayi1, sayi2)
                islem = "-"
            case "3":
                sonuc = carp(sayi1, sayi2)
                islem = "*"
            case "4":
                sonuc = bol(sayi1, sayi2)
                islem = "/"
            case "5":
                sonuc = us_al(sayi1, sayi2)
                islem = "^"
            case "6":
                sonuc = mod_al(sayi1, sayi2)
                islem = "%"
        
        print(f"Sonuç: {sayi1} {islem} {sayi2} = {sonuc}")

# Programı başlat
# hesap_makinesi()
```

---

### Proje 3: To-Do (Yapılacaklar) Listesi
```python
def gorev_ekle(liste, gorev):
    """Yeni görev ekler"""
    liste.append({"gorev": gorev, "tamamlandi": False})
    print(f"✓ '{gorev}' eklendi")

def gorev_tamamla(liste, indeks):
    """Görevi tamamlandı olarak işaretler"""
    if 0 <= indeks < len(liste):
        liste[indeks]["tamamlandi"] = True
        print(f"✓ '{liste[indeks]['gorev']}' tamamlandı")
    else:
        print("Geçersiz görev numarası!")

def gorev_sil(liste, indeks):
    """Görevi siler"""
    if 0 <= indeks < len(liste):
        silinen = liste.pop(indeks)
        print(f"✓ '{silinen['gorev']}' silindi")
    else:
        print("Geçersiz görev numarası!")

def gorevleri_listele(liste):
    """Tüm görevleri listeler"""
    print("\n=== YAPILACAKLAR ===")
    
    if len(liste) == 0:
        print("Liste boş!")
        return
    
    for i, gorev in enumerate(liste):
        durum = "✓" if gorev["tamamlandi"] else "○"
        print(f"{i+1}. [{durum}] {gorev['gorev']}")

def tamamlanmamis_say(liste):
    """Tamamlanmamış görev sayısını döndürür"""
    sayac = 0
    for gorev in liste:
        if not gorev["tamamlandi"]:
            sayac += 1
    return sayac

# === ANA PROGRAM ===
yapilacaklar = []

# Görev ekleme
gorev_ekle(yapilacaklar, "Python çalış")
gorev_ekle(yapilacaklar, "Algoritma ödevini yap")
gorev_ekle(yapilacaklar, "Spor yap")
gorev_ekle(yapilacaklar, "Kitap oku")

# Listeleme
gorevleri_listele(yapilacaklar)

# Bir görevi tamamla
gorev_tamamla(yapilacaklar, 0)  # Python çalış
gorev_tamamla(yapilacaklar, 2)  # Spor yap

# Tekrar listele
gorevleri_listele(yapilacaklar)

# Kalan görev sayısı
kalan = tamamlanmamis_say(yapilacaklar)
print(f"\nKalan görev: {kalan}")
```

---

### Proje 4: Sayı Tahmin Oyunu (Gelişmiş)
```python
import random

def rastgele_sayi_uret(alt, ust):
    """Alt ve üst sınır arasında rastgele sayı üretir"""
    return random.randint(alt, ust)

def ipucu_ver(tahmin, gizli):
    """Tahmini değerlendirir ve ipucu verir"""
    fark = abs(tahmin - gizli)
    
    if tahmin < gizli:
        yon = "BÜYÜK"
    else:
        yon = "KÜÇÜK"
    
    if fark <= 5:
        sicaklik = "🔥 Çok sıcak!"
    elif fark <= 15:
        sicaklik = "☀️ Sıcak"
    elif fark <= 30:
        sicaklik = "🌤️ Ilık"
    else:
        sicaklik = "❄️ Soğuk"
    
    return f"Daha {yon}! {sicaklik}"

def puan_hesapla(tahmin_sayisi, max_tahmin):
    """Tahmin sayısına göre puan hesaplar"""
    if tahmin_sayisi == 1:
        return 100
    elif tahmin_sayisi <= 3:
        return 80
    elif tahmin_sayisi <= 5:
        return 60
    elif tahmin_sayisi <= max_tahmin:
        return 40
    return 0

def oyunu_baslat():
    """Oyun ana fonksiyonu"""
    print("=== SAYI TAHMİN OYUNU ===")
    print("1-100 arası bir sayı tuttum!")
    
    gizli = rastgele_sayi_uret(1, 100)
    max_tahmin = 7
    tahmin_sayisi = 0
    
    while tahmin_sayisi < max_tahmin:
        kalan = max_tahmin - tahmin_sayisi
        print(f"\n(Kalan hak: {kalan})")
        
        try:
            tahmin = int(input("Tahmininiz: "))
        except ValueError:
            print("Lütfen sayı girin!")
            continue
        
        tahmin_sayisi += 1
        
        if tahmin == gizli:
            puan = puan_hesapla(tahmin_sayisi, max_tahmin)
            print(f"\n🎉 TEBRİKLER! {tahmin_sayisi} denemede buldunuz!")
            print(f"🏆 Puanınız: {puan}")
            return
        else:
            mesaj = ipucu_ver(tahmin, gizli)
            print(mesaj)
    
    print(f"\n😔 Kaybettiniz! Sayı: {gizli}")

# Oyunu başlat
# oyunu_baslat()
```

---

## 📌 BÖLÜM 14: EKSTRA KÜÇÜK ÖRNEKLER

### Örnek: Mükemmel Sayı Kontrolü
```python
# Mükemmel sayı: Kendisi hariç bölenlerinin toplamı kendisine eşit
# Örnek: 6 = 1 + 2 + 3

def mukemmel_mi(sayi):
    bolen_toplami = 0
    
    for i in range(1, sayi):
        if sayi % i == 0:
            bolen_toplami += i
    
    return bolen_toplami == sayi

# 1-100 arası mükemmel sayılar
print("Mükemmel sayılar:", end=" ")
for s in range(1, 101):
    if mukemmel_mi(s):
        print(s, end=" ")
# Çıktı: 6 28
```

---

### Örnek: Armstrong Sayısı
```python
# Armstrong: Rakamlarının küplerinin toplamı kendisine eşit
# Örnek: 153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = 153

def armstrong_mi(sayi):
    rakam_sayisi = len(str(sayi))
    toplam = 0
    gecici = sayi
    
    while gecici > 0:
        rakam = gecici % 10
        toplam += rakam ** rakam_sayisi
        gecici //= 10
    
    return toplam == sayi

# 1-1000 arası Armstrong sayıları
print("Armstrong sayıları:", end=" ")
for s in range(1, 1001):
    if armstrong_mi(s):
        print(s, end=" ")
# Çıktı: 1 2 3 4 5 6 7 8 9 153 370 371 407
```

---

### Örnek: Sayının Tersini Bulma
```python
def ters_cevir(sayi):
    ters = 0
    
    while sayi > 0:
        son_rakam = sayi % 10
        ters = ters * 10 + son_rakam
        sayi //= 10
    
    return ters

# Test
print(ters_cevir(12345))  # 54321
print(ters_cevir(1000))   # 1
```

---

### Örnek: İki Sayının Asal Olup Olmadığını Kontrol
```python
# Aralarında asal: EBOB'ları 1 olan iki sayı

def ebob_bul(a, b):
    while b != 0:
        a, b = b, a % b
    return a

def aralarinda_asal_mi(a, b):
    return ebob_bul(a, b) == 1

# Test
print(aralarinda_asal_mi(8, 15))   # True (EBOB = 1)
print(aralarinda_asal_mi(12, 18))  # False (EBOB = 6)
```

---

## 🎯 HIZLI BAKIŞ TABLOSU

| Örnek | Konu | Zorluk |
|-------|------|--------|
| Çift/Tek | if-else | ⭐ |
| Çarpım Tablosu | for döngüsü | ⭐ |
| Asal Sayı | İç içe döngü | ⭐⭐ |
| Faktöriyel | Recursive | ⭐⭐ |
| Fibonacci | Recursive | ⭐⭐ |
| Adam Asmaca | Liste | ⭐⭐⭐ |
| EBOB/EKOK | Recursive | ⭐⭐ |
| İkili Arama | Recursive | ⭐⭐⭐ |
| Caesar Cipher | String | ⭐⭐⭐ |

---

**🍀 Sınavda Başarılar!**