<div align="center">
  <img src="launcher_preview.png" alt="Enkazdan Kurtar Logo" width="120" height="120">
  <h1>🌍 Enkazdan Kurtar (Offline Deprem)</h1>
  <p><b>Afet anında internet ve baz istasyonuna ihtiyaç duymadan hayat kurtaran iletişim ağı.</b></p>

  <p>
    <img src="https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android" alt="Android" />
    <img src="https://img.shields.io/badge/Language-Kotlin-7F52FF?style=for-the-badge&logo=kotlin" alt="Kotlin" />
    <img src="https://img.shields.io/badge/UI-Jetpack%20Compose-4285F4?style=for-the-badge&logo=jetpackcompose" alt="Jetpack Compose" />
    <img src="https://img.shields.io/badge/Architecture-MVVM%20%2B%20Clean-FF6F00?style=for-the-badge" alt="Architecture" />
  </p>
</div>

## 🎯 Problem ve İnovatif Çözüm

Deprem veya doğal afet anlarında **baz istasyonları çökebilir** ve iletişim hatları kesilebilir. İnsanlar enkaz altındayken veya güvende olduklarını bildirmek isterken tamamen iletişimsiz kalırlar.

**Çözümümüz:** Akıllı telefonların **Bluetooth Low Energy (BLE)** ve **Wi-Fi P2P (Direct)** teknolojilerini kullanarak birbirine bağlanmasını ve zincirleme bir **Mesh Ağı** oluşturmasını sağlamak. 
Bu sistemde her telefon hem alıcı hem de verici görevi görür. Hayati durum bilgileri (ad, konum, aciliyet durumu) cihazdan cihaza aktarılarak geniş alanlara yayılır ve kurtarma ekiplerine (veya interneti olan bir uca) ulaşması sağlanır.

## 🚀 Temel Özellikler

*   📶 **Mesh Ağı İletişimi:** İnternetsiz ortamda BLE yayını ve Wi-Fi P2P keşfi ile cihazlar arası iletişim.
*   🚨 **Durum Bildirimi:** "Güvendeyim", "Yardıma İhtiyacım Var", "Enkaz Altındayım", "Tıbbi Yardım Gerekli" gibi hayati durumların ağa yayınlanması.
*   🔦 **SOS Işık Sinyali:** Enkaz altında yer belirlemeyi kolaylaştırmak için kamera flaşı ile otomatik Mors alfabesi (SOS) sinyali.
*   🗺️ **Çevrimdışı Acil Nokta Haritası:** Toplanma alanları, sağlık ve lojistik noktalarının internet olmadan görüntülenebildiği dahili harita.
*   ☁️ **Gateway Kuyruğu:** İnternet erişimi olmayan anlarda kaydedilen verilerin, cihaz internete bağlandığı anda buluta (veya merkeze) aktarılması için yerel veri kuyruğu.
*   🎨 **Modern Arayüz:** Jetpack Compose ve Material Design 3 ile geliştirilmiş, acil durumlarda hızlı kullanılabilen ergonomik tasarım.

## 📸 Ekran Görüntüleri

<div align="center">
  <table>
    <tr>
      <td align="center"><b>Ana Ekran</b></td>
      <td align="center"><b>Durum Bildir</b></td>
      <td align="center"><b>Mesh Ağı Tarama</b></td>
    </tr>
    <tr>
      <td><img src="https://via.placeholder.com/250x500.png?text=Ana+Ekran" alt="Ana Ekran" width="250"/></td>
      <td><img src="https://via.placeholder.com/250x500.png?text=Durum+Bildir" alt="Durum Bildir" width="250"/></td>
      <td><img src="https://via.placeholder.com/250x500.png?text=Mesh+Ag+Tarama" alt="Mesh Ağı Tarama" width="250"/></td>
    </tr>
    <tr>
      <td align="center"><b>Çevrimdışı Harita</b></td>
      <td align="center"><b>SOS Flaş Sinyali</b></td>
      <td align="center"></td>
    </tr>
    <tr>
      <td><img src="https://via.placeholder.com/250x500.png?text=Cevrimdisi+Harita" alt="Çevrimdışı Harita" width="250"/></td>
      <td><img src="https://via.placeholder.com/250x500.png?text=SOS+Flas" alt="SOS Flaş Sinyali" width="250"/></td>
      <td></td>
    </tr>
  </table>
</div>
*(Not: Placeholder resimlerin yerine uygulamanın gerçek ekran görüntülerini proje klasörüne ekleyerek yollarını güncelleyebilirsiniz.)*

## 📐 Mimari ve Teknoloji Yığını

Proje, **Clean Architecture** prensiplerine sadık kalınarak, **MVVM** deseni ile tasarlanmıştır.

```text
┌──────────────────────────────────────┐
│          UI (Jetpack Compose)        │  ← Ekranlar, Animasyonlar, Theme
├──────────────────────────────────────┤
│       ViewModel (MVVM)               │  ← StateFlow, İş Mantığı
├──────────────────────────────────────┤
│     Domain (Interface + Entity)      │  ← Saf Kotlin, Bağımsız Kurallar
├──────────────────────────────────────┤
│     Data (Repository Impl.)          │  ← BLE, Wi-Fi P2P, Local DB, Gateway
└──────────────────────────────────────┘
```

*   **Dil:** Kotlin
*   **UI Framework:** Jetpack Compose, Material Design 3
*   **Mimari:** Clean Architecture, MVVM
*   **Asenkron İşlemler:** Kotlin Coroutines & Flow
*   **Ağ Bağlantısı:** Bluetooth LE (Beacon/Advertise), Wi-Fi P2P (Direct)

## 📌 Kurulum ve Çalıştırma

### 1. Android Studio ile Kurulum (Önerilen)
1. Android Studio'yu açın.
2. Bu projeyi proje olarak açın.
3. Android cihazınızı USB ile bilgisayara bağlayın ve `Geliştirici Seçenekleri > USB Hata Ayıklama` ayarını aktif edin.
4. Android Studio'da cihazınızı seçip **▶ Run** düğmesine basın.

### 2. APK ile Kurulum
Oluşturulan Debug APK dosyasını doğrudan cihazınıza kurabilirsiniz:
`app/app/build/outputs/apk/debug/app-debug.apk`
*(Kurulum sırasında "Bilinmeyen uygulamaları yükle" iznini vermeniz gerekebilir.)*

### 3. ADB ile Kurulum (Komut Satırı)
Projeyi terminalden kurmak için proje dizininde:
```bash
adb install -r "app\app\build\outputs\apk\debug\app-debug.apk"
```

## 🔐 Gerekli İzinler

Uygulamanın tam kapasiteyle çalışabilmesi için aşağıdaki izinlere ihtiyacı vardır:
*   **Bluetooth & Yakındaki Cihazlar:** Mesh ağı taraması ve BLE yayını için hayati öneme sahiptir.
*   **Konum:** Özellikle eski Android sürümlerinde BLE ve Wi-Fi P2P taramalarının yapılabilmesi için gereklidir.
*   **Kamera:** Enkaz altında yerinizi belli edebilmek için Flaş ile SOS sinyali göndermekte kullanılır.
*   **İnternet / Ağ Durumu:** Gateway kuyruğunda biriken verilerin, internet bağlantısı sağlandığında sunucuya aktarımı için.

## ⚠️ Bilinen Sınırlamalar

*   **BLE Sınırları:** Şu anki BLE yayını kısa beacon boyutlarındadır (reklam paketleri). Büyük mesajların aktarımı için GATT ve özel bir protokol katmanı entegrasyonu gereklidir.
*   **Wi-Fi P2P:** Gerçek veri aktarımından çok şu an için cihazların birbirini keşfetmesi aşamasındadır.
*   **Emülatör Kısıtlamaları:** Flaş (SOS) ve Bluetooth/Wi-Fi özellikleri Android emülatörlerinde test edilemez; uygulamanın **fiziksel cihazlarda** test edilmesi zorunludur.

## 👨‍💻 Geliştirici

Bu proje geliştirme ve test amacıyla hazırlanmış olup, modern Android geliştirme süreçleri referans alınarak oluşturulmuştur.
