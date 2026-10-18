# Uzay Navigasyonu Simülatörü

Gezegenler, Ay ve yakın yıldızlar arasında en tasarruflu ve en hızlı güzergahı hesaplayıp aşama aşama çizerek simüle eden, tarayıcıda çalışan **eğitim amaçlı** bir yörünge mekaniği uygulaması.

Tek dosyadır (`index.html`). Kurulum, sunucu ya da derleme gerekmez.

> **Canlı demo:** `[https://Selim-Tuna
.github.io/Space-Navigation-Simulator/](https://github.com/Selim-Tuna/Space-Navigation-Simulator.git)` 

## Özellikler

- **Efemeris:** Gezegen konumları JPL’in yaklaşık Kepler elemanlarından hesaplanır.
- **Lambert çözücü:** İki gezegen konumunu ve bir uçuş süresini birleştiren Güneş çekimi altındaki yörüngeyi bulur.
- **Porkchop taraması:** Kalkış günü ve uçuş süresi taranır; toplam Δv haritası çizilir. Ek Δv bütçesi çubuğuyla en tasarruflu ile en hızlı çözüm arasında geçiş yapılır.
- **Jüpiter gravite yardımı:** İki Lambert bacağı birleştirilir, yardım maliyeti dönüş açısı sınırıyla hesaplanır.
- **Aşamalı simülasyon:** Park yörüngesinde turlar, kaçış yanması, Güneş merkezli transfer, yakalanma (veya aerofren) ve yüzeye iniş ayrı ayrı çizilir.
- **Ay:** Dünya↔Ay (TLI, LOI) ve Ay↔gezegen rotaları.
- **Yıldız rotaları:** Işık yelkeni, füzyon, Parker hızı ve Voyager hızı senaryoları (kavramsal).
- **Ayarlanabilir etkenler:** Park yörüngesi yüksekliği, yüzeyden kalkış, yüzeye iniş, aerofren, zorlu uzay koşulları, rota hassasiyeti, çekim bozulmaları. Her değişiklik süre, Δv ve yakıt oranını anında günceller; kartlar “ideal” değerle farkı gösterir.
- **Uzay aracı galerisi:** 8 araç çizimi; tıklayınca özellikleri listelenir ve seçili görev için yakıt oranı hesaplanır.
- Malzeme listesi ve terimler sözlüğü.

## Çalıştırma

1. `index.html` dosyasını bir tarayıcıda açın.
2. Ya da GitHub Pages ile yayınlayın: **Settings → Pages → Branch: main → Save**.

## Yöntem

| Konu | Yaklaşım |
|---|---|
| Gezegen konumları | JPL yaklaşık Kepler elemanları (Standish), 1800–2050 arası geçerli, Kepler denklemi Newton yöntemiyle çözülür |
| Transfer | Lambert problemi, evrensel değişkenler yöntemi (Stumpff fonksiyonları, bisection) |
| Yörünge çizimi | Evrensel değişken ile Kepler ilerletme |
| Kalkış/varış | Yama konik yaklaşım: Δv = √(v∞² + 2μ/r) − √(μ/r) |
| Yakıt | Tsiolkovski denklemi (kimyasal Isp 450 s, elektrik Isp 3000 s) |
| Jüpiter yardımı | Giriş ve çıkış v∞ vektörlerinin farkı; dönüş açısı sınırı aşılırsa kalan fark yakıt maliyetidir |
| Dünya–Ay | Dairesel Ay yörüngesi, Hohmann tabanlı TLI ve LOI |

## Sınırlar ve dürüst notlar

Bu proje bir **öğretim ve keşif aracıdır**, görev tasarım aracı değildir.

- Gezegen konumları DE440 gibi tam efemeris kadar hassas değildir. Dünya konumu Dünya–Ay kütle merkezidir.
- Yama konik yaklaşım kullanılır; tam n-cisim entegrasyonu yoktur.
- Ay dairesel yörünge olarak modellenmiştir.
- Kalkan kütlesi, bekleme günleri, rota düzeltme (TCM) Δv’si, aerofren tasarrufu ve yerçekimi kaybı **tahmini katsayılardır**.
- Jüpiter yardımı yerel flyby görünümü olarak çizilmez.
- Yıldız rotaları kavramsaldır; mesafeler ışık yılı cinsinden doğrudandır, yıldız haritası gökyüzü izdüşümüdür.
- Uzay aracı özellikleri kamuya açık yaklaşık değerlerdir ve resmi kaynaklarla tek tek doğrulanmamıştır. Nükleer termal, Starshot ve Daedalus konsept düzeyindedir.
- Dünya→Mars penceresi gerçek 2026 Mars penceresiyle uyumlu çıkmıştır; ancak sonuçlar GMAT veya poliastro gibi bağımsız araçlarla sistematik olarak karşılaştırılmamıştır. Bu bir yapılacaklar maddesidir.

## Yapılacaklar

- [ ] Bağımsız araçlarla (poliastro, GMAT) doğrulama testleri ve karşılaştırma tablosu
- [ ] Jüpiter flyby için yerel görünüm
- [ ] Yörünge eğimleri ve 3B görünüm
- [ ] Hesap kodunu çizim kodundan ayırıp modüllere bölmek
- [ ] Daha hassas efemeris (ör. DE440 örneklemeleri)

## Yapay zekâ kullanımı

Kodun büyük bölümü Claude (Anthropic) ile birlikte geliştirilmiştir. Yöntemler ve katsayılar yazar tarafından gözden geçirilmelidir.

## Kaynaklar

- E. M. Standish, *Keplerian Elements for Approximate Positions of the Major Planets*, JPL (yaklaşık efemeris elemanları)
- H. D. Curtis, *Orbital Mechanics for Engineering Students* (Lambert problemi, evrensel değişkenler)
- NASA, ESA ve JAXA’nın kamuya açık görev sayfaları (araç özellikleri)

## Lisans

MIT. Ayrıntılar için `LICENSE` dosyasına bakın.
