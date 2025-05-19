# FeelTrack-GenaritveAIFinalExam

# FeelTrack : Canlı Duygu Analizi ve Danışmanlık Destek Sistemi


**FeelTrack**, gerçek zamanlı sesli verilerden gelen konuşmaları yazıya çevirip duygusal analiz yaparak psikolojik öneriler sunan bir destek sistemidir.  
Özellikle rehber öğretmenler, psikologlar veya danışmanlar için geliştirilmiştir.

---

##  Özellikler

-  **Canlı Ses Analizi** (WhisperX ile):  
  Ses verileri anlık olarak yazıya çevrilir.

-  **Duygu Sınıflandırması** (BERT & RoBERTa):  
  Her 2 cümlede bir duygu analizi yapılır.  
  14 duygu ve durum kategorisi:
  - `üzüntü`, `öfke`, `umutlu`, `stres`, `intihar_düşüncesi`, `anksiyete`, `hakaret`, `nefret_söylemi`, `tehdit`, `sevinç`, `normal`, `güvensiz`, `kişilik_bȯzukluğu`, `ruh_hali_salınımı`

-  **Duygu Kombinasyonları Tanıma**:  
  Birden fazla duygu aynı anda analiz edilir ve özel öneriler sunulur.

-  **Canlı Öneri Üretimi**:  
  Örneğin:  
  `"Danışan anksiyete + stres + güvensizlik kombinasyonu sergiliyor. Sakinleştirici bir dil kullanın, güven duygusu oluşturmaya odaklanın."`

-  **Konuşmacı Ayrımı (İsteğe Bağlı)**:  
  `pyannote-audio` ile konuşmacı A (öğretmen/danışman) ve B (öğrenci/danışan) ayırt edilebilir.

---

##  Kullanılan Teknolojiler

| Teknoloji         | Açıklama                                               |
|------------------|--------------------------------------------------------|
| `WhisperX`        | Ses transkripsiyonu ve VAD (Voice Activity Detection) |
| `HuggingFace Transformers` | BERT, RoBERTa modelleriyle duygu tahmini         |
| `PyTorch`         | Model çalıştırma                                       |
| `pyannote-audio`  | Konuşmacı tanıma (opsiyonel)                           |
| `Scikit-learn`    | Veri işleme ve doğruluk hesaplama                      |

---

## 📂 Proje Yapısı

DataCleaningAndTokenization 

amodel_train_berts 

data_augmentation_and_balance 

final_out_GAN

model_train_robertaw 
---

## 🧪 Kurulum (Kaggle veya Colab)

1. Python 3.10+ ve aşağıdaki kütüphaneleri yükleyin:

```bash
pip install torch torchaudio transformers datasets scipy pyannote.audio==3.3.2 whisperx
HuggingFace erişim anahtarınızı tanımlayın:


from huggingface_hub import login
login("your_hf_token")
🔍 Kullanım
Ses dosyasını yükle (.wav)

transcribe_chunks.py dosyasını çalıştır → 30 saniyelik parçalara ayırır ve metne çevirir.

analyze_emotions.py ile her parçanın duygularını analiz eder.

Uygulama, her cümle kombinasyonu için anlık öneriler üretir.

 Uygulama Senaryosu
 Rehber öğretmen, danışman öğrencisiyle sesli görüşme yapıyor. Sistem, öğrencinin ifadelerini analiz ederek öğretmene şu öneriyi sunuyor:

"Danışanınız şu anda anksiyete ve çaresizlik belirtileri gösteriyor. 'Yalnız değilsin, buradayım' gibi cümlelerle destekleyici olun."

 Geliştirme Aşamasında Planlananlar
 Konuşmacı ayrımı
 Duygu kombinasyon önerileri
 Grafiksel duygu değişim zaman çizgisi
 Geri bildirimli öğrenme (Q-learning veya Reinforcement)
 GUI / web panel

