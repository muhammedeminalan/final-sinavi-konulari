# 🖥️ İşletim Sistemleri - Final Sınav Özeti (Detaylı)

---

## 📌 1. ANA BELLEK YÖNETİMİ

### 🎯 Temel Problem
> Birden fazla program aynı anda çalışmak istiyor ama RAM tek ve sınırlı. Kim nereye oturacak?

### Adres Kavramları

| Terim | Ne İşe Yarar? | Örnek |
|-------|---------------|-------|
| **Logical Address** | CPU'nun ürettiği adres. Program kendini 0'dan başlıyor sanır | Program: "100. adrese git" |
| **Physical Address** | RAM'deki gerçek konum | Aslında RAM'de 5100. adres |
| **MMU** | Logical → Physical çeviriyi yapan donanım | 100 → 5100 |

**Base-Limit Mantığı:**
```
Fiziksel Adres = Base + Logical Address
Eğer Logical Address > Limit → HATA (başka işlemin alanına girme!)
```

**🔍 Örnek:**
```
Base = 5000, Limit = 1000
Logical Address = 300 → Physical = 5000 + 300 = 5300 ✓
Logical Address = 1200 → 1200 > 1000 → HATA! ✗
```

---

### Bellek Tahsis Stratejileri

#### Contiguous (Bitişik) Tahsis
İşlem RAM'de tek parça halinde oturur.

**Yerleştirme Algoritmaları - Somut Örnek:**

```
Boş bloklar: [100KB] [500KB] [200KB] [300KB] [600KB]
Gelen işlem: 212KB istiyor

First-Fit  → 500KB bloğa koy (ilk uygun)
Best-Fit   → 300KB bloğa koy (en küçük uygun, 88KB israf)
Worst-Fit  → 600KB bloğa koy (en büyük, 388KB kalır)
```

| Algoritma | Avantaj | Dezavantaj |
|-----------|---------|------------|
| First-Fit | Hızlı | Başta küçük parçalar birikir |
| Best-Fit | Az israf | Yavaş, çok küçük parçalar kalır |
| Worst-Fit | Büyük parça kalır | Genelde kötü performans |

#### Parçalanma (Fragmentation)

**External (Dış):** Toplam boş yer yeterli ama dağınık
```
[İşlem A][BOŞ 50KB][İşlem B][BOŞ 80KB][İşlem C][BOŞ 70KB]
Toplam boş: 200KB ama 150KB'lık işlem sığmıyor!
Çözüm: Compaction (sıkıştırma) - işlemleri kaydır, boşlukları birleştir
```

**Internal (İç):** Verilen blok ihtiyaçtan büyük
```
Blok boyutu: 4KB, İşlem ihtiyacı: 3KB
1KB boşa gidiyor → Internal fragmentation
```

---

### Paging (Sayfalama) ⭐⭐

**Mantık:** Hem işlemi hem RAM'i sabit boyutlu parçalara böl. Parçalar ardışık olmak zorunda değil!

| Terim | Açıklama |
|-------|----------|
| **Page** | İşlemin mantıksal parçası (genelde 4KB) |
| **Frame** | RAM'deki fiziksel parça (page ile aynı boyut) |
| **Page Table** | Hangi page hangi frame'de? |

**🔍 Adres Çevirisi Örneği:**

```
Sayfa boyutu: 4KB (4096 byte = 2^12)
Logical Address: 13500

Adım 1: Page Number = 13500 / 4096 = 3 (tam kısım)
Adım 2: Offset = 13500 % 4096 = 1212 (kalan)

Page Table'dan: Page 3 → Frame 7

Physical Address = (7 × 4096) + 1212 = 28672 + 1212 = 29884
```

**Formül:**
```
Page Number = Logical Address / Page Size
Offset = Logical Address % Page Size
Physical Address = (Frame Number × Page Size) + Offset
```

#### TLB (Translation Lookaside Buffer)

**Problem:** Her bellek erişiminde page table'a gitmek = 2 bellek erişimi (yavaş!)

**Çözüm:** TLB = Sık kullanılan çevirilerin önbelleği

```
TLB Hit  → Çeviri TLB'de bulundu (1 erişim yeterli)
TLB Miss → Page table'a git (2 erişim gerekli)
```

**🔍 Effective Access Time (EAT) Hesabı:**

```
Bellek erişim süresi: 100ns
TLB erişim süresi: 10ns
TLB Hit Ratio: %90

TLB Hit:  10 + 100 = 110ns
TLB Miss: 10 + 100 + 100 = 210ns

EAT = 0.90 × 110 + 0.10 × 210 = 99 + 21 = 120ns
```

#### Multi-Level Page Table

**Problem:** 32-bit adres, 4KB sayfa → 2^20 page table entry = 4MB sadece tablo için!

**Çözüm:** Page table'ı da sayfala (2 seviyeli)

```
Logical Address: [10 bit: Outer] [10 bit: Inner] [12 bit: Offset]

1. Outer page table'dan inner table adresini bul
2. Inner table'dan frame numarasını bul
3. Frame + Offset = Physical Address
```

---

### Segmentation (Bölümleme)

Belleği mantıksal parçalara böl: Code, Data, Stack, Heap

```
Segment Table:
| Segment | Base  | Limit |
|---------|-------|-------|
| Code    | 1000  | 400   |
| Data    | 2000  | 500   |
| Stack   | 5000  | 200   |

Adres: <Segment=1, Offset=100>
Physical = 2000 + 100 = 2100
```

**Paging vs Segmentation:**
| Özellik | Paging | Segmentation |
|---------|--------|--------------|
| Parça boyutu | Sabit | Değişken |
| Dış parçalanma | Yok | Var |
| İç parçalanma | Var | Yok |
| Mantıksal bölüm | Yok | Var (code, data...) |

---

## 📌 2. SANAL BELLEK ⭐⭐⭐

### 🎯 Temel Fikir
> RAM yetmiyor mu? Disk'i RAM gibi kullan! İşlemin tamamı bellekte olmak zorunda değil.

### Demand Paging

**Mantık:** Sayfayı lazım olunca yükle, önceden değil.

```
Valid Bit = 1 → Sayfa RAM'de
Valid Bit = 0 → Sayfa diskte (page fault olur)
```

**Page Fault Adımları:**
1. CPU sayfaya erişmek istiyor
2. Page table'da valid=0 → **Page Fault!**
3. OS devreye girer, trap oluşur
4. Sayfa diskte bulunur
5. Boş frame varsa oraya yükle
6. Boş frame yoksa → **Page Replacement** (birini at!)
7. Page table güncelle, valid=1 yap
8. İşlemi kaldığı yerden devam ettir

---

### Page Replacement Algoritmaları ⭐⭐⭐ SINAV KLASİĞİ

**Senaryo:** 3 frame var, sayfa referans dizisi: `7, 0, 1, 2, 0, 3, 0, 4, 2, 3`

#### FIFO (First In First Out)

```
7 → [7, -, -] Page Fault
0 → [7, 0, -] Page Fault
1 → [7, 0, 1] Page Fault
2 → [2, 0, 1] Page Fault (7 en eski, onu at)
0 → [2, 0, 1] Hit! (0 zaten var)
3 → [2, 3, 1] Page Fault (0 en eski, onu at)
0 → [2, 3, 0] Page Fault (1 en eski, onu at)
4 → [4, 3, 0] Page Fault (2 en eski, onu at)
2 → [4, 2, 0] Page Fault (3 en eski, onu at)
3 → [4, 2, 3] Page Fault (0 en eski, onu at)

Toplam: 9 Page Fault
```

**⚠️ Belady Anomalisi:** FIFO'da frame arttığında page fault artabilir!
```
3 frame → 9 fault
4 frame → 10 fault (mantık dışı!)
```

#### Optimal (OPT)

**Mantık:** Gelecekte en uzun süre kullanılmayacak olanı at.

```
7 → [7, -, -] PF
0 → [7, 0, -] PF
1 → [7, 0, 1] PF
2 → [2, 0, 1] PF (7 bir daha hiç kullanılmayacak)
0 → [2, 0, 1] Hit!
3 → [2, 0, 3] PF (1 bir daha kullanılmayacak)
0 → [2, 0, 3] Hit!
4 → [2, 0, 4] PF (3'ten sonra 2 kullanılacak, 3'ü at)
2 → [2, 0, 4] Hit!
3 → [3, 0, 4] PF (2 bir daha kullanılmayacak)

Toplam: 6 Page Fault (en iyi sonuç!)
```

**⚠️ Gerçekte uygulanamaz** - geleceği bilemeyiz, karşılaştırma için kullanılır.

#### LRU (Least Recently Used)

**Mantık:** En uzun süredir kullanılmayanı at (geçmişe bak).

```
7 → [7, -, -] PF
0 → [7, 0, -] PF
1 → [7, 0, 1] PF
2 → [2, 0, 1] PF (7 en eski kullanılan)
0 → [2, 0, 1] Hit! (0 artık en yeni)
3 → [2, 0, 3] PF (1 en eski kullanılan)
0 → [2, 0, 3] Hit!
4 → [4, 0, 3] PF (2 en eski kullanılan)
2 → [4, 0, 2] PF (3 en eski kullanılan)
3 → [4, 3, 2] PF (0 en eski kullanılan)

Toplam: 8 Page Fault
```

**Uygulama Yöntemleri:**
- Counter: Her erişimde zaman damgası
- Stack: Erişilen sayfayı en üste al

#### Clock (Second Chance) Algorithm

**Mantık:** FIFO + referans biti. Atılacak sayfanın biti 1 ise 0 yap, ikinci şans ver.

```
Dairesel kuyruk + reference bit:
- Sayfa erişilirse → bit = 1
- Victim ararken bit=1 ise → bit=0 yap, sonrakine geç
- bit=0 olan ilk sayfayı at
```

```
Örnek: Frame'ler dairesel, pointer → işaret ediyor

[7(1)] → [0(1)] → [1(1)] → pointer başa döner
         ↑
      pointer

2 geldi, 7'nin biti 1, 0 yap geç
0'ın biti 1, 0 yap geç
1'in biti 1, 0 yap geç
7'ye geri döndük, biti artık 0, 7'yi at, 2'yi koy
```

---

### Thrashing (Çırpınma) ⭐⭐

**Nedir?** CPU zamanının büyük kısmı page fault işlemeye gidiyor, iş yapılamıyor.

```
Çok işlem → Herkese az frame → Sürekli page fault
→ CPU boşta (I/O bekliyor) → OS "CPU boş" der
→ Daha fazla işlem yükler → Daha da kötüleşir!
```

**Belirtisi:** CPU kullanımı düşük ama sistem yavaş

**Çözümler:**
1. Multiprogramming derecesini azalt
2. Working Set Model kullan
3. Page Fault Frequency (PFF) kontrolü

### Working Set Model

**Working Set:** Bir işlemin son Δ zaman biriminde kullandığı sayfalar kümesi.

```
Δ = 5, Referans dizisi: ... 1, 2, 3, 4, 1, 2, 5, 1, 2, 3 ...
                                              ↑ şu an

Working Set = {5, 1, 2, 3} (son 5 referans)
Bu işleme en az 4 frame ver!
```

**Kural:** Σ(Working Set boyutları) > Toplam Frame → Thrashing riski!

---

## 📌 3. İŞLEM SENKRONİZASYONU ⭐⭐

### 🎯 Temel Problem
> İki işlem aynı değişkeni aynı anda değiştirirse ne olur? Kaos!

### Race Condition

```c
// Paylaşılan değişken: counter = 5

// Thread 1                    // Thread 2
register1 = counter;           register2 = counter;
register1 = register1 + 1;     register2 = register2 - 1;
counter = register1;           counter = register2;

// Olası sonuçlar: 4, 5, veya 6! (sıraya bağlı)
```

**Sorun:** İşlemler atomic değil, araya girilebiliyor.

---

### Critical Section (Kritik Bölge)

Paylaşılan kaynağa erişilen kod bölümü. Korunmalı!

```c
entry_section();      // Giriş kontrolü
    critical_section; // Paylaşılan veriye eriş
exit_section();       // Çıkış işlemi
    remainder_section;
```

**3 Gereksinim:**

| Gereksinim | Açıklama | Örnek |
|------------|----------|-------|
| **Mutual Exclusion** | Aynı anda sadece 1 işlem | Tek kişilik tuvalet |
| **Progress** | Kimse içeride değilse, girmek isteyen girebilmeli | Boş tuvalet kilidi açık |
| **Bounded Waiting** | Sonsuza kadar beklemek yok | Sıra sistemi olmalı |

---

### Peterson's Solution (2 işlem için)

```c
int turn;           // Kimin sırası
bool flag[2];       // Kim girmek istiyor

// Process i
flag[i] = true;     // Ben girmek istiyorum
turn = j;           // Ama önce sen geç
while (flag[j] && turn == j); // O istiyorsa ve sırası ondaysa bekle

    // Critical Section

flag[i] = false;    // Çıktım
```

**Neden çalışıyor?**
- `flag`: Niyeti gösterir
- `turn`: Çakışmada kime öncelik

---

### Senkronizasyon Araçları

#### Mutex Lock

```c
acquire() {
    while (!available); // Busy waiting (spinlock)
    available = false;
}

release() {
    available = true;
}

// Kullanım:
acquire();
    // Critical Section
release();
```

**Özellik:** Sadece kilitleyen açabilir!

#### Semaphore

Bir sayaç. Negatif olunca bekle.

```c
wait(S) veya P(S):      signal(S) veya V(S):
    while (S <= 0);         S++;
    S--;
```

**Binary Semaphore:** S = 0 veya 1 (mutex gibi)
**Counting Semaphore:** S = n (n kaynak var)

**🔍 Örnek: 3 printer var**
```c
semaphore printer = 3;

// Her işlem:
wait(printer);     // Printer al (printer--)
    // Yazdır
signal(printer);   // Printer bırak (printer++)
```

#### Monitor

Yüksek seviyeli yapı. Otomatik mutual exclusion.

```java
monitor BankAccount {
    int balance;
    condition okToWithdraw;
    
    void withdraw(int amount) {
        while (balance < amount)
            okToWithdraw.wait();  // Bekle
        balance -= amount;
    }
    
    void deposit(int amount) {
        balance += amount;
        okToWithdraw.signal();    // Bekleyeni uyandır
    }
}
```

---

### Klasik Problemler ⭐⭐

#### 1. Producer-Consumer (Bounded Buffer)

```c
semaphore mutex = 1;    // Buffer'a erişim
semaphore empty = n;    // Boş slot sayısı
semaphore full = 0;     // Dolu slot sayısı

// PRODUCER                      // CONSUMER
while (true) {                   while (true) {
    // üret                          wait(full);    // Dolu var mı?
    wait(empty);   // Boş var mı?    wait(mutex);   // Buffer'ı kilitle
    wait(mutex);   // Kilitle        // tüket
    // buffer'a koy                  signal(mutex); // Kilidi aç
    signal(mutex); // Aç             signal(empty); // Boş slot arttı
    signal(full);  // Dolu arttı }
}
```

**⚠️ wait sırası önemli!** `wait(mutex)` önce olursa → Deadlock!

#### 2. Readers-Writers

```c
semaphore rw_mutex = 1;  // Yazma kilidi
semaphore mutex = 1;     // read_count koruması
int read_count = 0;

// WRITER                        // READER
wait(rw_mutex);                  wait(mutex);
    // yaz                       read_count++;
signal(rw_mutex);                if (read_count == 1)
                                     wait(rw_mutex); // İlk okuyucu kilitle
                                 signal(mutex);
                                     // oku
                                 wait(mutex);
                                 read_count--;
                                 if (read_count == 0)
                                     signal(rw_mutex); // Son okuyucu aç
                                 signal(mutex);
```

#### 3. Dining Philosophers

```
5 filozof, 5 çatal (chopstick)
Yemek için 2 çatal lazım (sol ve sağ)
```

**Naive çözüm → DEADLOCK:**
```c
wait(chopstick[i]);      // Sol çatalı al
wait(chopstick[(i+1)%5]); // Sağ çatalı al
// Herkes sol çatalı alırsa → Deadlock!
```

**Çözümler:**
1. En fazla 4 filozof sofraya otursun
2. Tek numaralılar önce sol, çift numaralılar önce sağ
3. Her iki çatalı atomik olarak al

---

## 📌 4. KİLİTLENMELER (DEADLOCK) ⭐⭐⭐ EN ÖNEMLİ

### 🎯 Tanım
> İşlemler birbirinin tuttuğu kaynağı bekliyor, kimse ilerleyemiyor.

**Gerçek hayat örneği:**
```
Dar köprüde iki araba karşı karşıya geldi.
İkisi de "önce sen geç" diyor ama ikisi de yerinden kıpırdamıyor.
```

---

### 4 Gerekli Koşul (AYNI ANDA HEPSİ)

| Koşul | Açıklama | Örnek |
|-------|----------|-------|
| **1. Mutual Exclusion** | Kaynak paylaşılamaz | Yazıcı tek kişi kullanabilir |
| **2. Hold and Wait** | Elindekini tut, başkasını bekle | Çatalı tutup diğerini bekle |
| **3. No Preemption** | Zorla alınamaz | Yazıcıyı yarıda alamazsın |
| **4. Circular Wait** | Döngüsel bekleme | P1→P2→P3→P1 |

**⚡ Biri bile yoksa → Deadlock OLMAZ!**

---

### Resource Allocation Graph (RAG)

```
P → R : Request Edge (işlem kaynağı istiyor)
R → P : Assignment Edge (kaynak işleme verilmiş)
```

**🔍 Örnek 1: Deadlock VAR**
```
P1 → R1 → P2 → R2 → P1  (döngü!)

R1, R2 tek instance → KESİN DEADLOCK
```

**🔍 Örnek 2: Döngü var ama Deadlock YOK**
```
R1 (2 instance): biri P1'de, biri P3'te
R2 (2 instance): biri P2'de, biri P3'te

P1 → R2, P2 → R1 (bekliyorlar)
P3 bitince kaynaklarını bırakır → döngü kırılır
```

**Kural:**
- Tek instance + Döngü → **Deadlock KESİN**
- Çoklu instance + Döngü → **Deadlock OLABİLİR**

---

### Deadlock Handling Stratejileri

#### 1. Prevention (Önleme)

Koşullardan birini engelle:

| Koşul | Nasıl Engellenir? | Dezavantaj |
|-------|-------------------|------------|
| Mutual Exclusion | Paylaşılabilir yap | Her zaman mümkün değil |
| Hold and Wait | Hepsini başta al veya hiçbirini tutma | Kaynak israfı |
| No Preemption | Zorla al | Tutarsızlık riski |
| Circular Wait | Kaynaklara numara ver, sırayla al | Zor uygulanır |

**Circular Wait Engelleme Örneği:**
```
Kaynaklar: R1=1, R2=2, R3=3

Kural: Sadece artan sırada kaynak al!
P1: R1 aldı, R3 isteyebilir ✓
P1: R3 aldı, R2 isteyemez ✗ (3 > 2)
```

#### 2. Avoidance (Kaçınma) - Banker's Algorithm ⭐⭐⭐

Her kaynak isteğinde "bu isteği verirsem safe state'te kalır mıyım?" diye kontrol et.

**Kavramlar:**
```
Available[m]    : Her kaynak türünden kaç tane boşta
Max[n][m]       : Her işlemin max ihtiyacı
Allocation[n][m]: Her işlemin şu an tuttuğu
Need[n][m]      : Daha ne kadar lazım = Max - Allocation
```

**🔍 ÖRNEK (Çok Önemli!):**

```
3 kaynak türü: A, B, C
Toplam: A=10, B=5, C=7

        Allocation    Max         Need
        A  B  C      A  B  C     A  B  C
P0      0  1  0      7  5  3     7  4  3
P1      2  0  0      3  2  2     1  2  2
P2      3  0  2      9  0  2     6  0  0
P3      2  1  1      2  2  2     0  1  1
P4      0  0  2      4  3  3     4  3  1

Available = (10-7, 5-2, 7-5) = (3, 3, 2)
```

**Safety Algorithm:**

```
Work = Available = (3, 3, 2)
Finish = [false, false, false, false, false]

Adım 1: Need[P1] = (1,2,2) ≤ Work(3,3,2) ✓
        P1 çalışıp biter
        Work = (3,3,2) + (2,0,0) = (5,3,2)
        Finish[P1] = true

Adım 2: Need[P3] = (0,1,1) ≤ Work(5,3,2) ✓
        P3 çalışıp biter
        Work = (5,3,2) + (2,1,1) = (7,4,3)
        Finish[P3] = true

Adım 3: Need[P0] = (7,4,3) ≤ Work(7,4,3) ✓
        P0 çalışıp biter
        Work = (7,4,3) + (0,1,0) = (7,5,3)
        Finish[P0] = true

Adım 4: Need[P2] = (6,0,0) ≤ Work(7,5,3) ✓
        P2 çalışıp biter
        Work = (7,5,3) + (3,0,2) = (10,5,5)
        Finish[P2] = true

Adım 5: Need[P4] = (4,3,1) ≤ Work(10,5,5) ✓
        P4 çalışıp biter
        Finish[P4] = true

Tüm işlemler bitti → SAFE STATE ✓
Safe Sequence: <P1, P3, P0, P2, P4>
```

**Resource Request Algorithm:**

```
P1: (1, 0, 2) istiyor

1. Request ≤ Need? (1,0,2) ≤ (1,2,2) ✓
2. Request ≤ Available? (1,0,2) ≤ (3,3,2) ✓
3. Geçici olarak ver:
   Available = (3,3,2) - (1,0,2) = (2,3,0)
   Allocation[P1] = (2,0,0) + (1,0,2) = (3,0,2)
   Need[P1] = (1,2,2) - (1,0,2) = (0,2,0)
4. Safety check yap
5. Safe ise → VER, değilse → BEKLET
```

#### 3. Detection & Recovery

**Detection:** Wait-for graph'ta döngü ara (periyodik olarak)

**Recovery:**
1. **İşlem Sonlandırma:**
   - Hepsini öldür (brutal)
   - Döngü kırılana kadar tek tek öldür
   
2. **Kaynak Preemption:**
   - Kaynağı al, başkasına ver
   - Rollback gerekebilir

**Victim Seçimi Kriterleri:**
- Öncelik
- Ne kadar süredir çalışıyor
- Kaç kaynak tutuyor
- Tamamlanmaya ne kadar kaldı

#### 4. Ignorance (Devekuşu Yaklaşımı)

```
Deadlock nadir oluyorsa → Maliyetine değmez
Sistem donunca → Restart at
```
Windows, Linux bu yaklaşımı kullanır!

---

## 🎯 FORMÜL VE HESAP ÖZETİ

### EAT (Effective Access Time)
```
EAT = (TLB_hit_ratio × TLB_hit_time) + (TLB_miss_ratio × TLB_miss_time)
TLB_hit_time = TLB_access + Memory_access
TLB_miss_time = TLB_access + 2×Memory_access
```

### Page Fault Rate Etkisi
```
EAT = (1-p) × memory_access + p × page_fault_time
p = page fault oranı
```

### Paging Adresi
```
Page Number = Logical_Address / Page_Size
Offset = Logical_Address % Page_Size
Physical = Frame_Number × Page_Size + Offset
```

---

## 📋 SINAV KONTROL LİSTESİ

| Konu | Kontrol | Örnek Yapabilir misin? |
|------|---------|----------------------|
| Page Replacement | FIFO, OPT, LRU, Clock | Tablo çizerek adım adım |
| Banker's Algorithm | Need hesapla, Safe sequence bul | ✓/✗ |
| Deadlock 4 koşul | Ezberle | Senaryo ver, hangisi eksik? |
| TLB/EAT hesabı | Formül | Sayısal problem |
| Senkronizasyon | wait/signal sırası | Producer-Consumer kodu |
| RAG | Döngü tespit | Şekil çiz, deadlock var mı? |

---

## 💡 SINAV TÜYOLARI

1. **Page Replacement:** Her adımı tablo halinde yaz, frame içeriklerini göster
2. **Banker's:** Need = Max - Allocation, sonra Work ile karşılaştır
3. **Deadlock:** 4 koşuldan biri yoksa deadlock OLMAZ
4. **Semaphore:** wait sırası çok önemli! Yanlış sıra = deadlock
5. **Safe vs Unsafe:** Unsafe ≠ Deadlock, sadece risk var

---

**Bol şans! 🍀**