# Prompt Günlüğü

## Prompt 1 — Proje planlama
**Tarih:** 2026-06-28
**Adım:** Veri seti tanıma ve notebook bölüm planı

**Prompt:** Online Retail veri setiyle RFM + K-Means projesi planı, 
3 araştırma sorusu önerimle birlikte plan onayı istedim.

**Sonuç:** Veri seti 541.909 satır, 8 sütun. CustomerID'de %25 eksik veri 
(RFM için silinecek). İngiltere %91 ağırlıkta — çift panel grafik önerildi. 
9 hücrelik notebook planı çıktı: Import, Yükleme, Temizleme, 3 araştırma 
sorusu, EDA görselleri, RFM hesabı, K-Means kümeleme, Sonuçlar.

---

## Prompt 2 — Veri seti ön keşfi
**Tarih:** 2026-06-28
**Adım:** Veri seti keşfi ve istatistiksel özet
**Prompt:** `data/data.csv` dosyasının ilk satırlarını, sütunlarını, eksik değerlerini ve temel istatistiklerini oku ve özetle.
**Sonuç:** 541.909 satır, 8 sütun. CustomerID 135.080 satırda eksik (%25); 10.624 negatif Quantity, 9.288 "C" ile başlayan iptal faturası, 2.517 sıfır/negatif UnitPrice tespit edildi.

---

## Prompt 3 — Plan onayı ve iyileştirme talebi
**Tarih:** 2026-06-28
**Adım:** RFM + K-Means proje planının veri setine göre doğrulanması
**Prompt:** Önerilen 3 araştırma sorusu ve RFM + K-Means yaklaşımını veri setine bakarak onayla veya iyileştir.
**Sonuç:** Plan onaylandı; ülke geliri grafiğinin İngiltere ağırlığı (%91) nedeniyle çift panel (dahil/hariç) olması gerektiği belirlendi.

---

## Prompt 4 — 3 araştırma sorusunun kesinleştirilmesi
**Tarih:** 2026-06-28
**Adım:** Araştırma sorularının tanımlanması ve notebook yapısına yerleştirilmesi
**Prompt:** 1. Ülke gelirleri, 2. Aylık satış trendi/mevsimsellik, 3. RFM tabanlı müşteri segmentasyonu — bu 3 soru ödev şartını karşılıyor mu?
**Sonuç:** 3 soru onaylandı ve notebook'un 4., 5. ve 8. hücrelerine dağıtılarak iskelet planına yerleştirildi.

---

## Prompt 5 — Bölüm bölüm notebook iskelet planı
**Tarih:** 2026-06-28
**Adım:** Notebook iskeletinin oluşturulması
**Prompt:** Hangi hücrede ne olacağını gösteren bölüm bölüm plan çıkar.
**Sonuç:** 9 hücreli plan: Import → Yükleme → Temizleme → Ülke geliri → Aylık trend → EDA görselleri → RFM hesabı → K-Means kümeleme → Sonuçlar ve öneriler.

---

## Prompt 6 — Notebook oluşturma onayı
**Tarih:** 2026-06-28
**Adım:** Notebook kodlamasına başlanması
**Prompt:** "Evet, yaz." — Belirlenen 9 bölümlük planın notebook.ipynb olarak oluşturulması.
**Sonuç:** `nbformat` kütüphanesi kullanan `gen_notebook.py` betiği yazıldı; betik çalıştırılarak `notebook.ipynb` üretildi (19 hücre: 1 kapak + 9 markdown + 9 kod).

---

## Prompt 7 — Her hücre öncesine Türkçe markdown kuralı
**Tarih:** 2026-06-28
**Adım:** Türkçe açıklama hücrelerinin tasarlanması
**Prompt:** Her kod hücresinden ÖNCE bir markdown hücresi olsun ve o hücrede ne yapıldığını 2-3 cümleyle Türkçe açıkla.
**Sonuç:** 9 kod hücresinin tamamına, o hücrenin amacını ve yöntemini açıklayan birer Türkçe markdown hücresi eklendi.

---

## Prompt 8 — Kod içi Türkçe yorum satırları kuralı
**Tarih:** 2026-06-28
**Adım:** Kod içi dokümantasyon
**Prompt:** Kod içine de Türkçe yorum satırları ekle — sözlüde sorulduğunda açıklayabileyim diye.
**Sonuç:** Her hücrede `#` ile başlayan Türkçe açıklamalar eklendi; hangi satırın ne iş yaptığı kısaca belirtildi.

---

## Prompt 9 — Tüm 9 hücreyi tek seferde oluşturma şartı
**Tarih:** 2026-06-28
**Adım:** Atomik notebook üretimi
**Prompt:** Tüm 9 hücreyi (plan değerlendirmesindeki) tek seferde oluştur.
**Sonuç:** `gen_notebook.py` betiği, hücreleri sırayla bir listeye ekleyip `nbformat.write()` ile tek seferde `notebook.ipynb`'ye yazan yapıda tasarlandı.

---

## Prompt 10 — Türkçe grafik başlıkları ve eksen etiketleri kuralı
**Tarih:** 2026-06-28
**Adım:** Görselleştirme lokalizasyonu
**Prompt:** Grafikler Türkçe başlık ve eksen etiketleriyle olsun.
**Sonuç:** `set_title()`, `set_xlabel()`, `set_ylabel()` çağrılarının tamamına Türkçe metinler yazıldı; `suptitle` ile üst başlıklar da Türkçeleştirildi.

---

## Prompt 11 — Okunabilir figsize kuralı
**Tarih:** 2026-06-28
**Adım:** Grafik boyut ve okunabilirlik ayarları
**Prompt:** Görsellerin figsize'ı okunabilir olsun (örn. 10x6).
**Sonuç:** Tekli grafikler için `(10,6)` veya `(13,6)`, çift panel grafikler için `(16,7)` veya `(17,7)` boyutları atandı.

---

## Prompt 12 — random_state=42 tekrarlanabilirlik kuralı
**Tarih:** 2026-06-28
**Adım:** K-Means modelinin deterministik hale getirilmesi
**Prompt:** K-Means için random_state=42 kullan (tekrarlanabilirlik için).
**Sonuç:** `KMeans(n_clusters=4, random_state=42, n_init=10)` olarak sabitlendi; Elbow döngüsündeki her k değeri de aynı `random_state` ile çalıştırıldı.

---

## Prompt 13 — Her hücre bağımsız çalışabilir olmalı kuralı
**Tarih:** 2026-06-28
**Adım:** Hücre bağımsızlığı ve sıralı tutarlılık testi
**Prompt:** Her hücre TEK BAŞINA çalıştırılabilir olmalı, ama sırayla çalıştırılınca da tutarlı olmalı.
**Sonuç:** `jupyter nbconvert --execute` ile uçtan uca doğrulandı; 9 kod hücresinin tamamı hatasız çalıştı, 4 PNG dosyası üretildi.

---

## Prompt 14 — f-string SyntaxError hata ayıklama
**Tarih:** 2026-06-28
**Adım:** Notebook hata ayıklama ve düzeltme
**Prompt:** (Otomatik tespit) `nbconvert` çalıştırınca Hücre 5'te f-string literal içinde gerçek satır sonu karakteri SyntaxError verdi.
**Sonuç:** Generator betiğindeki `\n` kaçış dizileri 4 satırda `\\n` olarak düzeltildi; notebook yeniden üretilip ikinci çalıştırmada tüm hücreler temiz geçti.

---

## Prompt 15 — Prompt günlüğü dokümantasyonu
**Tarih:** 2026-06-28
**Adım:** Proje dokümantasyonu ve sohbet geçmişi kaydı
**Prompt:** Sohbet geçmişindeki önemli prompt'ları kronolojik sırayla prompts.md dosyasına ekle; mevcut Prompt 1'i koru, altına yeni maddeleri ekle.
**Sonuç:** Sohbet geçmişinden 14 anlamlı prompt türetildi ve belirlenen formatta prompts.md dosyasına eklendi.

---

## Prompt [16] — Raporun yazdırılması
**Tarih:** 2026-06-28
**Adım:** 3-5 sayfalık akademik rapor üretimi
**Prompt:** Notebook'taki gerçek bulgulara dayanarak 6 bölümlü 
(problem, veri, yöntem, bulgular, sınırlamalar, öğrenilenler) 
akademik bir rapor yaz, gorseller/ klasörüne referans ver.
**Sonuç:** report/rapor.md oluştu, Markdown PDF eklentisiyle 
rapor.pdf'e çevrildi.