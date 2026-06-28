# Online Retail Müşteri Segmentasyonu

Bu projede Birleşik Krallık merkezli bir e-ticaret şirketinin 2010–2011 yıllarına ait işlem verisi kullanılarak RFM (Recency, Frequency, Monetary) analizi ve K-Means kümeleme yöntemiyle müşteri segmentasyonu gerçekleştirilmiştir. Temizlenmiş 397.884 işlem kaydından elde edilen 4.338 müşteri, dört anlamlı segmente ayrılmış; ülke bazlı gelir dağılımı ve aylık satış mevsimselliği de incelenmiştir.

---

## 👥 Proje Ekibi

| Alan | Bilgi |
|---|---|
| Öğrenci No | [1306230066] |
| Ad Soyad | [Mahmut Arda Eren] |
| Ders | Veri Bilimi |
| Dönem | 2025–2026 Bahar |

---

## 🎯 Proje Amacı

Proje, aşağıdaki üç araştırma sorusuna yanıt aramaktadır:

1. **Hangi ülkeler en yüksek geliri sağlamaktadır?** — Pazarlama yatırımlarının coğrafi önceliklendirilmesi.
2. **Aylık satış trendi nasıldır, mevsimsellik var mıdır?** — Stok ve kampanya planlaması için dönemsel kalıpların tespiti.
3. **Müşteriler RFM'e göre kaç anlamlı segmente ayrılmaktadır ve bu segmentlerin özellikleri nelerdir?** — Kişiselleştirilmiş pazarlama için müşteri profilleri oluşturma.

---

## 📊 Veri Seti

| Özellik | Değer |
|---|---|
| **Kaynak** | UCI Machine Learning Repository — Online Retail |
| **Bağlantı** | https://archive.ics.uci.edu/dataset/352/online+retail |
| **Lisans** | UCI ML Repository kullanım koşulları (akademik kullanım serbest) |
| **Atıf** | Chen, D. (2015). Online Retail [Dataset]. UCI ML Repository. https://doi.org/10.24432/C5BW33 |
| **Ham boyut** | 541.909 satır × 8 sütun |
| **Tarih aralığı** | 01.12.2010 — 09.12.2011 |
| **Temiz boyut** | 397.884 satır, 4.338 benzersiz müşteri |

---

## 🛠️ Kullanılan Kütüphaneler

| Kütüphane | Sürüm | Amaç |
|---|---|---|
| `pandas` | 3.0.3 | Veri yükleme, temizleme, gruplandırma |
| `numpy` | 2.5.0 | Sayısal hesaplamalar |
| `matplotlib` | 3.11.0 | Grafik çizimi |
| `seaborn` | 0.13.2 | Grafik stili |
| `scikit-learn` | 1.9.0 | `StandardScaler`, `KMeans` |
| `scipy` | 1.18.0 | Bilimsel hesaplamalar |
| `jupyter` | 1.1.1 | Notebook ortamı |
| `jupyterlab` | 4.6.0 | JupyterLab arayüzü |
| `nbformat` | 5.10.4 | Notebook dosyası üretimi |
| `nbconvert` | 7.17.1 | Notebook'u çalıştırma ve dönüştürme |

Tüm bağımlılıklar için `requirements.txt` dosyasına bakınız.

---

## 📁 Proje Yapısı

```
online-retail-proje/
│
├── data/
│   └── data.csv                  # Ham veri (UCI'dan indirilmeli, repoda yok)
│
├── gorseller/
│   ├── 01_ulke_geliri.png        # Şekil 1 — Ülke gelirleri çift panel
│   ├── 02_aylik_trend.png        # Şekil 2 — Aylık satış trendi
│   ├── 03_eda_gorselleri.png     # Şekil 3 — EDA tamamlayıcı görseller
│   └── 04_kmeans_segmentasyon.png# Şekil 4 — Elbow + segment dağılımı
│
├── report/
│   └── rapor.md                  # Akademik rapor (Markdown)
│
├── notebook.ipynb                # Ana analiz notebook'u (9 kod hücresi)
├── prompts.md                    # Geliştirme sürecindeki prompt günlüğü
├── requirements.txt              # Python bağımlılıkları
└── README.md                     # Bu dosya
```

---

## 🚀 Kurulum ve Çalıştırma

### 1. Repoyu klonla

```bash
git clone <repo-url>
cd online-retail-proje
```

### 2. Sanal ortam oluştur

**Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**macOS / Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Bağımlılıkları kur

```bash
pip install -r requirements.txt
```

### 4. Veri seti

Veri seti repoda `data/data.csv` olarak mevcuttur, ekstra indirme gerekmez.

### 5. Notebook'u çalıştır

**VS Code'da:**
1. `notebook.ipynb` dosyasını aç
2. Sağ üstten Python sanal ortamını seç (`venv`)
3. `Kernel → Restart & Run All` ile tüm hücreleri çalıştır

**JupyterLab'da:**
```bash
jupyter lab notebook.ipynb
```
Menüden `Run → Run All Cells` seçeneğini kullan.

---

## 📈 Sonuçlar

- **Veri:** 397.884 satır temiz işlem kaydı, **4.338 benzersiz müşteri** analiz edildi
- **Ülke gelirleri:** Birleşik Krallık toplam gelirin **%82,0'ini** (£7.308.392) oluşturmaktadır
- **Mevsimsellik:** Kasım 2011 zirve ayı (£1.161.817); yılın son çeyreği diğer aylara göre **1,46×** daha yüksek ciro üretmektedir
- **Müşteri segmentleri:** K-Means (k=4) ile 4 segment tespit edildi:

| Segment | Müşteri | Ort. Harcama | Profil |
|---|---|---|---|
| Şampiyonlar | 13 | £127.338 | Çok aktif, çok değerli |
| Sadık Müşteriler | 204 | £12.709 | Düzenli, yüksek değerli |
| Risk Altındakiler | 3.054 | £1.359 | Aktif ama az sıklıkta |
| Kayıp Müşteriler | 1.067 | £481 | 8+ aydır alışveriş yapmıyor |

Detaylı bulgular için: [`report/rapor.md`](report/rapor.md)

---

## 📝 Notlar

- Bu proje **"vibe coding"** yaklaşımıyla [Claude Code](https://claude.ai/code) kullanılarak geliştirilmiştir. Kod yazımı yerine analitik yönlendirme, soru formülasyonu ve sonuç değerlendirmesi ön planda tutulmuştur.
- Geliştirme sürecindeki 15 prompt'un tam listesi ve her adımın açıklaması [`prompts.md`](prompts.md) dosyasında belgelenmiştir.
