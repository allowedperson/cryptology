<div align="center">

# 🔐 Custom Feistel Block Cipher

### Dinamik S-Box ve Değişken Tur Sayılı Özgün Blok Şifreleme Algoritması
### Modern Tkinter GUI ile Birlikte

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey)](https://github.com)
[![GUI](https://img.shields.io/badge/GUI-Tkinter-orange)](https://docs.python.org/3/library/tkinter.html)
[![Status](https://img.shields.io/badge/Status-Stable-success)]()

*Sıfırdan tasarlanmış Feistel ağ tabanlı, eğitim amaçlı blok şifreleme uygulaması.*

</div>

---

## 📖 İçindekiler

- [Özellikler](#-özellikler)
- [Ekran Görüntüleri](#-ekran-görüntüleri)
- [Kurulum](#-kurulum)
- [Kullanım](#-kullanım)
- [Algoritma Detayları](#-algoritma-detayları)
- [Avalanche Testi](#-avalanche-testi)
- [Proje Yapısı](#-proje-yapısı)
- [Güvenlik Uyarısı](#️-güvenlik-uyarısı)
- [Lisans](#-lisans)

---

## ✨ Özellikler

### 🔐 Kriptografi
- 🎲 **Dinamik S-Box Üretimi** — Anahtara bağlı Fisher-Yates karıştırma ile 256 elemanlı bijective S-Box
- 🔄 **Değişken Tur Sayısı** — Anahtara göre 6-10 arası dinamik tur sayısı
- 📦 **64-bit Blok Boyutu** — Klasik Feistel network mimarisi
- 🔑 **Esnek Anahtar Sistemi** — Hex (`DEADBEEF`) veya normal metin/parola (`gizli şifrem`) — Türkçe karakter desteği
- 🧬 **SHA-256 Anahtar Türetme** — Metin girişler güvenli şekilde 64-bit anahtara dönüştürülür
- 📏 **PKCS7 Padding** — Standart blok hizalama
- ⚡ **Tek Geçişli Şifreleme** — Pure Python, ek bağımlılık yok

### 🖥️ Kullanıcı Arayüzü
- 🌑 **Modern Catppuccin Mocha Teması** — Göz dostu koyu tema
- 📑 **4 Sekmeli Düzen** — Şifrele, Deşifre, Algoritma Detayları, Avalanche Testi
- 👁 **Anahtar Göster/Gizle** — Güvenli giriş için
- 📋 **Tek Tıkla Kopyalama** — Çıktıyı hızla panoya alma
- ℹ️ **Anlık Durum Çubuğu** — Her işlem sonucu görünür
- ⚠️ **Akıllı Hata Mesajları** — Kullanıcı dostu uyarılar

### 🧪 Analiz Araçları
- 📊 **Algoritma Analiz Paneli** — Round key'ler, S-Box önizleme, bijective doğrulama
- 🧪 **Avalanche Effect Testi** — Diffusion gücü ölçümü
- 🚀 **Kapsamlı Test Modu** — 50 farklı bit pozisyonu için ortalama hesaplama
- 🎯 **Otomatik Değerlendirme** — Sonuç renk kodlu (Mükemmel/İyi/Orta/Zayıf)

---

## 📸 Ekran Görüntüleri

<div align="center">

### 🔒 Şifreleme Sekmesi
![Encrypt Tab](screenshots/encrypt_tab.png)

### 🔓 Deşifre Sekmesi
![Decrypt Tab](screenshots/decrypt_tab.png)

### 📊 Algoritma Detayları
![Algorithm Details](screenshots/algorithm_details.png)

### 🧪 Avalanche Testi
![Avalanche Test](screenshots/avalanche_test.png)

</div>

---

## 🚀 Kurulum

### Gereksinimler
- **Python 3.8+** (Tkinter dahil — ek kurulum gerekmez)
- Windows, Linux veya macOS

### Adımlar

```bash
# 1. Repoyu klonla
git clone https://github.com/KULLANICI_ADIN/custom-feistel-cipher.git
cd custom-feistel-cipher

# 2. Uygulamayı çalıştır
python cipher_gui.py
```

> 💡 **Not:** Hiçbir ek paket (pip install) gerekmez. Tüm bağımlılıklar Python ile birlikte gelir.

---

## 📘 Kullanım

### 1️⃣ Şifreleme

1. **"🔒 Şifrele"** sekmesine geçin
2. **Anahtar** alanına bir değer girin:
   - Hex format: `DEADBEEF`, `1A2B3C4D`, `0xFF00`
   - Veya normal metin: `benim gizli şifrem 2024`
3. **Şifrelenecek metni** yazın (Türkçe ve emoji desteklenir)
4. **🔒 ŞİFRELE** butonuna tıklayın
5. Hex çıktıyı **📋 Kopyala** ile panoya alın

### 2️⃣ Deşifreleme

1. **"🔓 Deşifre Et"** sekmesine geçin
2. Şifrelemede kullandığınız **aynı anahtarı** girin
3. Hex metni yapıştırın
4. **🔓 DEŞİFRE ET** butonuna tıklayın

### 3️⃣ Algoritma Analizi

**"📊 Algoritma Detayları"** sekmesinde:
- Round key'lerin tam dökümü
- S-Box'ın ilk 32 değeri
- Bijective doğrulama
- Tur sayısı hesaplaması
- İstatistiksel analiz

### 4️⃣ Avalanche Testi

**"🧪 Avalanche Testi"** sekmesinde üç farklı mod:
- **Anahtar Avalanche:** Anahtarın 1 bitini değiştirir
- **Metin Avalanche:** Metnin 1 bitini değiştirir
- **Kapsamlı Test:** 50 farklı bit pozisyonu dener, ortalama verir

İdeal sonuç: **~%50 değişim** (güçlü diffusion göstergesi)

---

## 🔬 Algoritma Detayları

### Genel Yapı

```
┌─────────────────────────────────────────────────────┐
│              CUSTOM FEISTEL CIPHER                  │
├─────────────────────────────────────────────────────┤
│ Blok Boyutu     : 64-bit (8 byte)                   │
│ Anahtar Boyutu  : 64-bit (SHA-256'dan türetilen)    │
│ Tur Sayısı      : 6-10 (anahtara göre dinamik)      │
│ S-Box           : 256 eleman, anahtara özel         │
│ Padding         : PKCS7                              │
│ Yapı            : Asimetrik Feistel Network         │
└─────────────────────────────────────────────────────┘
```

### F-Fonksiyonu

```python
def f_function(right, round_key, sbox):
    temp = (right + round_key) mod 256   # Modüler toplama
    temp = left_rotate(temp, 3)          # Bit rotasyonu
    temp = sbox[temp]                    # S-Box substitution
    temp = temp ^ round_key              # XOR mixing
    temp = left_rotate(temp, 2)          # İkinci rotasyon
    return temp
```

### Anahtar Türetme

```
Kullanıcı Girişi
       │
       ▼
   Hex mi?  ──── Evet ───▶ int(key, 16)
       │
       Hayır
       │
       ▼
SHA-256(key.encode("utf-8"))[:8] ──▶ 64-bit Master Key
```

### Round Key Üretimi

```python
key = master_key
for i in range(num_rounds):
    key = (key << 5 | key >> 27) & 0xFFFFFFFF   # Sol rotasyon
    key ^= (i * 0x87654321) ^ 0xA5A5A5A5         # Sabitlerle XOR
    round_keys.append(key)
```

### Şifreleme Akışı

```
Plaintext (64-bit)
       │
       ▼
   ┌───────┐  ┌───────┐
   │ LEFT  │  │ RIGHT │
   └───┬───┘  └───┬───┘
       │          │
       │     ┌────▼────┐
       │     │    F    │ ◀── Round Key
       │     └────┬────┘
       └─────XOR──┘
          (Asimetrik Swap)
       │
       │  (6-10 tur tekrar)
       ▼
   Ciphertext (64-bit)
```

---

## 🧪 Avalanche Testi

**Avalanche Effect**, kriptografik algoritmaların kalitesini ölçen temel bir testtir. Girişte (anahtar veya metin) 1 bitlik değişiklik, çıktıda yaklaşık **%50 bit değişimine** yol açmalıdır.

### Değerlendirme Skalası

| Oran | Değerlendirme | Renk |
|:----:|:-------------|:----:|
| %45 – %55 | 🟢 **MÜKEMMEL DIFFUSION** | Yeşil |
| %40 – %45 veya %55 – %60 | 🟡 **İYİ DIFFUSION** | Sarı |
| %30 – %40 veya %60 – %70 | 🟠 **ORTA DIFFUSION** | Turuncu |
| Diğer | 🔴 **ZAYIF DIFFUSION** | Kırmızı |

---

## 📂 Proje Yapısı

```
custom-feistel-cipher/
├── cipher_gui.py           # Ana uygulama (GUI + algoritma)
├── README.md               # Bu dosya
├── LICENSE                 # MIT lisansı
├── .gitignore              # Git ignore
└── screenshots/            # Ekran görüntüleri
    ├── encrypt_tab.png
    ├── decrypt_tab.png
    ├── algorithm_details.png
    └── avalanche_test.png
```

---

## 🎨 Tema Renkleri

UI, popüler **Catppuccin Mocha** paletini kullanır:

| Element | Hex Kod | Önizleme |
|---------|---------|----------|
| Arkaplan | `#1e1e2e` | ![#1e1e2e](https://placehold.co/15x15/1e1e2e/1e1e2e.png) |
| Vurgu | `#89b4fa` | ![#89b4fa](https://placehold.co/15x15/89b4fa/89b4fa.png) |
| Başarı | `#a6e3a1` | ![#a6e3a1](https://placehold.co/15x15/a6e3a1/a6e3a1.png) |
| Hata | `#f38ba8` | ![#f38ba8](https://placehold.co/15x15/f38ba8/f38ba8.png) |
| Uyarı | `#f9e2af` | ![#f9e2af](https://placehold.co/15x15/f9e2af/f9e2af.png) |

---

## ⚠️ Güvenlik Uyarısı

> 🚨 **ÖNEMLİ:** Bu proje **eğitim ve akademik araştırma amaçlıdır**.

### ❌ KULLANMAYIN:
- Gerçek hassas verileri korumak için
- Üretim sistemlerinde
- Finansal veya tıbbi verileri şifrelemek için
- Profesyonel güvenlik gerektiren projelerde

### ✅ KULLANIN:
- Kriptografi öğrenmek için
- Feistel network mimarisini anlamak için
- Akademik ödevler ve projeler için
- Algoritma tasarım deneyleri için

### 🔒 Gerçek Dünya İçin Alternatifler:
- **AES-256-GCM** (NIST onaylı, endüstri standardı)
- **ChaCha20-Poly1305** (Google tarafından tercih edilen)
- **`cryptography`** Python kütüphanesi (`pip install cryptography`)

---

## 🏆 Akademik Başarı

> Bu algoritma ve terminal implementasyonu **bilgisayar mühendisliği kriptografi dersi** kapsamında değerlendirilmiş, brute-force kombinasyon testlerinden başarıyla geçmiş ve **100/100** not almıştır.

---

## 🛠️ Teknik Özellikler

| Kategori | Detay |
|----------|-------|
| Dil | Python 3.8+ |
| GUI Kütüphanesi | Tkinter (standart kütüphane) |
| Hash Algoritması | SHA-256 (anahtar türetme) |
| Encoding | UTF-8 (Türkçe karakter desteği) |
| Çıktı Formatı | Hexadecimal (uppercase) |
| Mimari | Asimetrik Feistel Network |
| Bağımlılıklar | **Yok** (sıfır ek paket) |

---

## 🔮 Gelecek Planları

- [ ] **CBC ve CTR modları** ekleme (şu an ECB)
- [ ] **Dosya şifreleme** desteği
- [ ] **PyInstaller** ile `.exe` çıktısı
- [ ] **Komut satırı (CLI)** versiyonu
- [ ] **Birim testler** (pytest)
- [ ] **İngilizce dil desteği**
- [ ] **Şifre güç göstergesi**
- [ ] **Toplu (batch) şifreleme**

---

## 🤝 Katkıda Bulunma

Katkılar memnuniyetle karşılanır! Lütfen şu adımları izleyin:

1. Repoyu fork edin
2. Yeni bir branch oluşturun (`git checkout -b feature/yeni-ozellik`)
3. Değişikliklerinizi commit edin (`git commit -m 'feat: yeni özellik eklendi'`)
4. Branch'i push edin (`git push origin feature/yeni-ozellik`)
5. Pull Request açın

---

## 📄 Lisans

Bu proje **MIT Lisansı** altında dağıtılmaktadır. Detaylar için [LICENSE](LICENSE) dosyasına bakınız.

```
MIT License - Copyright (c) 2024 [İsminiz]
İstediğiniz gibi kullanın, değiştirin ve dağıtın.
```

---

## 👤 Geliştirici

**[İsminiz Soyisminiz]**

- 🌐 GitHub: [@KULLANICI_ADIN](https://github.com/KULLANICI_ADIN)
- 💼 LinkedIn: [linkedin.com/in/profilin](https://linkedin.com/in/profilin)
- 📧 E-mail: senin@email.com

---

## ⭐ Beğendiyseniz...

Eğer bu proje işinize yaradıysa veya ilginizi çektiyse, lütfen **⭐ yıldız** vererek destek olun!

<div align="center">

### 🔐 Cipher ile güvenli kalın!

[![Made with Python](https://img.shields.io/badge/Made%20with-Python-yellow?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Made with Love](https://img.shields.io/badge/Made%20with-❤️-red?style=for-the-badge)]()

</div>
