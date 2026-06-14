# 🌍 Enkazdan Kurtar — Çevrimdışı Deprem İletişim Ağı

> Afet anında internet ve baz istasyonuna ihtiyaç duymadan hayat kurtaran mesh ağ uygulaması

<div align="center">
  <p>
    <img width="150" height="300" alt="Uygulama Ekranı 1" src="https://github.com/user-attachments/assets/509bd390-0ab1-4d7b-8f34-bc79993ad1ec" />
    <img width="150" height="300" alt="Uygulama Ekranı 2" src="https://github.com/user-attachments/assets/e0d477b3-c3c4-48c0-a376-69814c66c1dc" />
    <img width="150" height="300" alt="Uygulama Ekranı 3" src="https://github.com/user-attachments/assets/fb8194af-ddaa-4f5c-9c2e-a0c083e13e96" />
    <img width="150" height="300" alt="Uygulama Ekranı 4" src="https://github.com/user-attachments/assets/f94757d6-162f-44c2-bf05-450b111c7dea" />
  </p>
</div>

---

## 📥 Hızlı İndirme

### 🚀 Son Sürüm: v2.0
[**APK İndir (v2.0)**](https://github.com/Cafein-Sentinel/Enkaz_YardimProjesi/releases/download/v2.0/Enkaz_YardimProjesi-v2.0.apk)

> **Kurulum Talimatı:**
> 1. Yukarıdaki linke tıklayarak APK dosyasını indirin
> 2. Telefonunuzda: `Ayarlar` → `Güvenlik` → `Bilinmeyen Kaynaklar` ✓ etkinleştirin
> 3. İndirilen APK dosyasını açın ve kurulumu tamamlayın

---

## 🎯 Problem ve Çözüm

### 📌 Problem Nedir?
Deprem veya doğal afet anında:
- ❌ Baz istasyonları çöker
- ❌ İnternet bağlantısı kesilir
- ❌ İnsanlar iletişimsiz kalır
- ❌ Ailelerine "güvendeyim" mesajı gönderemez

### ✨ Çözüm: Mesh Ağ İletişimi
**Enkazdan Kurtar**, telefonların kendi aralarında ağ oluşturmasını sağlar:

- ✅ **Bluetooth Low Energy (BLE)** ve **Wi-Fi Direct** kullanarak cihazlar birbirine bağlanır
- ✅ Herkes hem **alıcı** hem **verici** olur
- ✅ **Zincirleme (mesh) ağ** oluşturulur
- ✅ "Kulaktan kulağa" iletişim gerçekleşir
- ✅ İnternet olmadan çalışır

> **Not:** Bu proje MVP (Minimum Viable Product) aşamasında olup Mesh ağı simülasyonu içermektedir.

---

## 🚀 Temel Özellikler

| Özellik | Açıklama |
|---------|----------|
| 📶 **Mesh Ağ Simülasyonu** | BLE/Wi-Fi Direct cihaz tarama animasyonu |
| 📝 **Durum Bildirimi** | "Güvendeyim", "Yardıma İhtiyacım Var", "Enkaz Altındayım", "Tıbbi Yardım" |
| 📡 **Radar Animasyonu** | Gerçek zamanlı cihaz tarama görseli (pulse animation) |
| 🗺️ **Çevrimdışı Harita** | İnternet olmadan toplanma alanları ve acil noktaları görüntüle |
| 🔦 **SOS Flaş Sinyali** | Kamera flaşı ile otomatik Mors alfabesi (SOS) döngüsü |
| 🎨 **Modern Tasarım** | Material Design 3, Dark Mode, erişilebilir arayüz |
| ⚡ **Smooth Animasyonlar** | Kart giriş, progress göstergeleri, sayaç animasyonları |

---

## 💻 Teknoloji Yığını

### Platformu
- **Android SDK** (Minimum API 26 / Android 8.0)
- **Kotlin** — Modern programlama dili

### Arayüz & Tasarım
- **Jetpack Compose** — Deklaratif UI framework
- **Material Design 3** — Google tasarım sistemi
- **Compose Navigation** — Ekran yönetimi

### Mimari & Durum Yönetimi
- **Clean Architecture** — Katman ayrımı (Domain, Data, UI)
- **MVVM (Model-View-ViewModel)** — Reaktif mimari
- **Kotlin Coroutines** — Asenkron işlemler
- **StateFlow** — Durum yönetimi

### Ağ Bağlantısı
- **Bluetooth Low Energy (BLE)** — Beacon ve Advertise
- **Wi-Fi P2P (Direct)** — Cihaz keşfi

---

## 🏗️ Proje Mimarisi

```
┌────────────────────────────────────────┐
│     UI (Jetpack Compose)               │
│  HomeScreen / ReportScreen / SyncUI    │
├────────────────────────────────────────┤
│     ViewModel (MVVM)                   │
│  HomeVM / ReportVM / SyncVM            │
│  (StateFlow ile reaktif durum yönetimi)│
├────────────────────────────────────────┤
│     Domain (İş Kuralları)              │
│  Entity, Repository Interface          │
│  (Saf Kotlin, Android bağımsız)        │
├────────────────────────────────────────┤
│     Data (İmplementasyon)              │
│  Repository Impl., BLE, Wi-Fi P2P      │
│  (In-Memory, Room, BLE entegrasyonu)   │
└────────────────────────────────────────┘
```

### Klasör Yapısı

```
Enkaz_YardimProjesi/
├── app/src/main/java/
│   ├── domain/              # Saf Kotlin, Entity ve Repository arayüzleri
│   ├── data/                # Repository implementasyonu (BLE, Wi-Fi P2P)
│   ├── ui/                  # Jetpack Compose ekranları ve ViewModeller
│   └── theme/               # Material Design 3 renk ve tipografi
└── build.gradle.kts         # Proje konfigürasyonu
```

---

## 📋 Kurulum ve Çalıştırma

### ✅ Gereksinimler

- ✔️ **Android Studio** (Hedgehog v2023.1.1 veya üzeri)
- ✔️ **Android 8.0+** (API Level 26+)
- ✔️ **Fiziksel cihaz** (Emülatörde tam test edilemez — Bluetooth/Wi-Fi donanımı gerekli)
- ✔️ **USB Hata Ayıklama** etkinleştirilmiş

### 🔧 Adım Adım Kurulum

**1. Depoyu Klonla**
```bash
git clone https://github.com/Cafein-Sentinel/Enkaz_YardimProjesi.git
cd Enkaz_YardimProjesi
```

**2. Android Studio'da Aç**
- Android Studio'yu açın
- `File` → `Open` → Proje dizinini seçin
- Gradle senkronizasyonunun tamamlanmasını bekleyin

**3. Fiziksel Cihazı Hazırla**
- USB kablosu ile telefonunuzu bilgisayara bağlayın
- Telefonda: `Ayarlar` → `Geliştirici Seçenekleri` → `USB Hata Ayıklama` ✓
- Android Studio'dan cihazı tanıyıp listelendiğini doğrulayın

**4. Uygulamayı Çalıştır**
- ▶️ **Run** tuşuna basın veya `Shift + F10`
- Uygulamanın cihazınızda yüklenmesini bekleyin

### ⚡ Alternatif: ADB ile Hızlı Kurulum

```bash
adb install -r "app/app/build/outputs/apk/debug/app-debug.apk"
```

---

## 📸 Ekran Görüntüleri

| İşlevsellik | Açıklama |
|-------------|----------|
| **Ana Ekran** | Mesh ağı durumu, bağlı cihazlar, durum göstergeleri |
| **Durum Bildir** | Hızlı durum bildirimi (Güvendeyim, Yardıma İhtiyacım, vb.) |
| **Mesh Ağı Tarama** | Aktif cihazları göster, sinyal gücü görseli |
| **Çevrimdışı Harita** | Toplanma alanları, sağlık merkezleri, lojistik noktaları |
| **SOS Flaş Sinyali** | Kamera flaşı ile Mors alfabesi (SOS) gönderimi |

> *Uygulamanın ekran görüntüleri proje içindeki `screenshots/` klasörüne şu isimlerle eklenecektir:*
> - `ana_ekran.png`
> - `durum_bildir.png`
> - `mesh_agi_tarama.png`
> - `cevrimdisi_harita.png`
> - `sos_flas_sinyali.png`

---

## ✅ Tamamlanan Özellikler

- ✅ BLE Advertise (yayın) ve Scan (tarama) yeteneği
- ✅ Wi-Fi P2P cihaz keşfi
- ✅ Durum bildirme sistemi (4 durum tipi)
- ✅ Çevrimdışı acil toplanma alanları haritası
- ✅ Kamera flaşı ile otomatik Mors alfabesi (SOS)
- ✅ MVVM ve Clean Architecture altyapısı
- ✅ Material Design 3 modern tasarım
- ✅ Jetpack Compose deklaratif UI

---

## 🔜 Planlanan Özellikler

- 🔲 Wi-Fi P2P üzerinden gerçek cihazdan cihaza socket veri aktarımı
- 🔲 BLE GATT katmanı ile büyük veri paketlerinin iletimi
- 🔲 Gateway Kuyruğu (Internet bağlantısı geldiğinde bulut senkronizasyonu)
- 🔲 Google Play Store ve App Store yayını (KMP geçişi ile)
- 🔲 Konum tabanlı otomatik durum bildirimi
- 🔲 Çoklu dil desteği

---

## ⚠️ Sorumluluk Reddi

**Enkazdan Kurtar**, MVP (Minimum Viable Product) aşamasında bir projedir.

- ⚠️ Gerçek afet anında iletişim **kesintisiz sağlanacağının garantisini veremez**
- ⚠️ Çevresel faktörlere, cihaz mimarisine ve RF ortamına bağlıdır
- ⚠️ **Test amaçlı geliştirilmiştir** — Üretim ortamında kullanılmadan önce kapsamlı test yapılmalıdır

### 🆘 Acil Durumlarda
**Lütfen resmi acil hizmetleri arayın: 112**

- AFAD (Afet ve Acil Durum Yönetimi Başkanlığı)
- Resmî kurtarma ekipleri
- Yardım koordinasyon merkezleri

---

## 👨‍💻 Geliştirici

**Proje Sahibi:** Mustafa Arda Özcan 202442501065

**Eğitim Bağlamı:** 
- Nesne Yönelimli Programlama (OOP) Dersi Final Projesi
- Clean Architecture ve MVVM prensipleri uygulanmıştır
- Agile/Sprint metodolojisi kullanılmıştır

---

## 📖 Referanslar & Kaynaklar

- [Android Jetpack Compose Dokümanı](https://developer.android.com/jetpack/compose)
- [Material Design 3](https://m3.material.io/)
- [Kotlin Coroutines](https://kotlinlang.org/docs/coroutines-overview.html)
- [Bluetooth Low Energy (BLE)](https://developer.android.com/guide/topics/connectivity/bluetooth/ble-overview)
- [Wi-Fi Direct (P2P)](https://developer.android.com/guide/topics/connectivity/wifip2p)

---

## 📝 Lisans

Bu proje eğitim amaçlı geliştirilmiştir. Kullanım şartları için proje sahibi ile iletişime geçiniz.

---

## 💭 Proje Felsefesi

> **"Her karanlığın ardında bir aydınlık, her enkazın altında bir umut vardır."**

Enkazdan Kurtar, teknoloji aracılığıyla afet anlarında hayat kurtarmaya ve insanlar arasında iletişim köprüsü kurmaya adanmıştır.

---

**⭐ Projeyi beğendiyseniz star atabilirsiniz!**
