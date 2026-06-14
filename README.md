# 🌍 Offline Deprem — Mesh Network Bilgi Paylaşım Ağı
🌍 Enkazdan Kurtar (Offline Deprem)
Afet anında internet ve baz istasyonuna ihtiyaç duymadan hayat kurtaran iletişim ağı.
  <p>
    <img width="150" height="300" alt="WhatsApp Image 2026-06-14 at 19 43 06" src="https://github.com/user-attachments/assets/509bd390-0ab1-4d7b-8f34-bc79993ad1ec" />
    <img width="150" height="300" alt="WhatsApp Image 2026-06-14 at 19 40 38" src="https://github.com/user-attachments/assets/e0d477b3-c3c4-48c0-a376-69814c66c1dc" />
   <img width="150" height="300" alt="WhatsApp Image 2026-06-14 at 19 40 39 (1)" src="https://github.com/user-attachments/assets/fb8194af-ddaa-4f5c-9c2e-a0c083e13e96" />
    <img width="150" height="300" alt="WhatsApp Image 2026-06-14 at 19 40 39" src="https://github.com/user-attachments/assets/f94757d6-162f-44c2-bf05-450b111c7dea" />
  </p>
</div>
Bluetooth Low Energy ve Wi-Fi P2P teknolojilerini kullanarak cihazlar arası zincirleme (mesh) ağ kuran, çevrimdışı acil nokta haritası ve SOS sinyali gibi hayati özellikler barındıran; tamamen internetsiz çalışabilen bir afet haberleşme uygulaması.
## 🎯 Problem ve İnovatif Çözüm
Android Kotlin Jetpack Compose Clean Architecture MVVM
Deprem veya doğal afet anında **baz istasyonları çöker** ve insanlar iletişimsiz kalır. Ailelerine "güvendeyim" mesajı bile gönderemezler.
📌 Çözdüğü Problem
Deprem veya doğal afet anlarında baz istasyonları çöker ve iletişim hatları kesilir. İnsanlar enkaz altındayken veya güvende olduklarını yakınlarına bildirmek isterken tamamen iletişimsiz kalırlar.
**Çözümümüz:** Telefonların **Bluetooth Low Energy (BLE) ve Wi-Fi Direct** üzerinden birbirine bağlanarak **zincirleme Mesh ağı** oluşturması. Her telefon hem alıcı hem verici olur. Sadece birkaç kilobaytlık durum bilgisi (ad, konum, durum) "kulaktan kulağa" aktarılarak uzak mesafelere ulaşır.
Enkazdan Kurtar (Offline Deprem), bu iletişimsizliği kırmak için telefonların kendi aralarında ağ oluşturmasını sağlar:
> **Bu proje MVP (Minimum Viable Product) aşamasında olup Mesh ağı simülasyonu içermektedir.**
Kulaktan kulağa durum bilgisi aktarımı (mesh network)
İnternet olmadan önbellekteki acil toplanma noktalarını bulma
Arama-kurtarma ekiplerine yer belirtmek için otomatik SOS sinyali gönderme
## 📐 Mimari — Clean Architecture + MVVM
💡 İnovasyon: Uygulama, Bluetooth Low Energy (BLE) ve Wi-Fi P2P (Direct) kullanarak cihazları birbirine bağlar. Her telefon hem alıcı hem de verici görevi görür. İnternet erişimi olmayan anlarda cihazda tutulan veriler, herhangi bir cihaz internete bağlandığı anda buluta aktarılmak üzere yerel bir gateway kuyruğunda tutulur.
```
┌──────────────────────────────────────┐
│          UI (Jetpack Compose)        │  ← Ekranlar, Animasyonlar
│  HomeScreen / ReportScreen / Sync    │
├──────────────────────────────────────┤
│       ViewModel (MVVM)               │  ← StateFlow, İş mantığı
│  HomeVM / ReportVM / SyncVM          │
├──────────────────────────────────────┤
│     Domain (Interface + Entity)      │  ← Saf Kotlin, bağımsız
│  StatusRepository / UserStatus       │
├──────────────────────────────────────┤
│     Data (Repository Impl.)          │  ← In-Memory / Room / BLE
│  InMemoryStatusRepository            │
└──────────────────────────────────────┘
```
✨ Özellikler
📶 Mesh Ağı İletişimi — Kulaktan Kulağa
İnternetsiz ortamda BLE yayını (Advertise) ve Wi-Fi P2P keşfi ile cihazlar arası iletişim kurulur.
Herkes etrafındaki diğer cihazları tarayarak sinyal durumlarını görebilir.
- **domain/** — Entity sınıfları ve Repository Interface'i (hiçbir Android bağımlılığı yok)
- **data/** — Repository implementasyonu (MVP: In-Memory, sonra Room veya BLE)
- **ui/** — Compose ekranları ve ViewModeller
- **theme/** — Material Design 3 renk şeması ve tipografi
🚨 Durum Bildirimi — Hayati Mesajlar
"Güvendeyim", "Yardıma İhtiyacım Var", "Enkaz Altındayım", "Tıbbi Yardım Gerekli" gibi kritik durumların mesh ağına yayınlanması.
Kişinin adı ve konumu ağdaki diğer cihazlara aktarılır.
## 🚀 Özellikler
🔦 SOS Işık Sinyali — Hayat Kurtaran Flaş
Enkaz altında sesinizi duyuramadığınız durumlarda yerinizi belli etmeyi kolaylaştırmak için kamera flaşı ile otomatik Mors alfabesi (SOS) döngüsü.
| Özellik | Açıklama |
|---------|----------|
| 📶 **Mesh Ağ Simülasyonu** | Bluetooth/Wi-Fi Direct cihaz tarama animasyonu |
| 📝 **Durum Bildirimi** | "Güvendeyim", "Yardıma İhtiyacım Var", "Enkaz Altındayım", "Tıbbi Yardım" |
| 📡 **Radar Animasyonu** | Gerçek zamanlı cihaz tarama görseli (pulse animation) |
| 🎨 **Material Design 3** | Modern, edge-to-edge, acil durum renk paleti |
| ⚡ **Mikro-animasyonlar** | Kart giriş animasyonları, progress göstergeleri, sayaç animasyonları |
| 🏗️ **Clean Architecture** | Domain ↔ Data ↔ UI katman ayrımı |
| 🔄 **MVVM + StateFlow** | Reaktif UI, yaşam döngüsüne duyarlı |
🗺️ Çevrimdışı Acil Nokta Haritası — İnternetsiz Yönlendirme
Toplanma alanları, sağlık ve lojistik noktalarının internet olmadan da görüntülenebildiği dahili harita.
Tamamen çevrimdışı çalışarak kullanıcıyı güvenli alanlara yönlendirir.
## 💻 Teknoloji Yığını
🎨 Deneyim — Modern ve Ergonomik Arayüz
Jetpack Compose ve Material Design 3 ile geliştirilmiş, acil durumlarda panik anında bile hızlıca kullanılabilecek, erişilebilirliği yüksek karanlık tema (Dark Mode) tasarımı.
- **Kotlin** — Dil
- **Jetpack Compose** — Modern deklaratif UI
- **Material Design 3** — Tasarım sistemi
- **Navigation 3** — Ekran geçişleri
- **ViewModel + StateFlow** — Durum yönetimi
- **Coroutines** — Asenkron işlemler
📸 Ekran Görüntüleri
## 📌 Kurulum ve Çalıştırma
<div align="center">
  <table>
    <tr>
      <td align="center"><b>Ana Ekran</b></td>
      <td align="center"><b>Durum Bildir</b></td>
      <td align="center"><b>Mesh Ağı Tarama</b></td>
    </tr>
    <tr>
      <td><img src="screenshots/ana_ekran.png" alt="Ana Ekran" width="250"/></td>
      <td><img src="screenshots/durum_bildir.png" alt="Durum Bildir" width="250"/></td>
      <td><img src="screenshots/mesh_agi_tarama.png" alt="Mesh Ağı Tarama" width="250"/></td>
    </tr>
    <tr>
      <td align="center"><b>Çevrimdışı Harita</b></td>
      <td align="center"><b>SOS Flaş Sinyali</b></td>
      <td align="center"></td>
    </tr>
    <tr>
      <td><img src="screenshots/cevrimdisi_harita.png" alt="Çevrimdışı Harita" width="250"/></td>
      <td><img src="screenshots/sos_flas_sinyali.png" alt="SOS Flaş Sinyali" width="250"/></td>
      <td></td>
    </tr>
  </table>
</div>
		
*(Not: Resimlerin doğru görünmesi için uygulamanın ekran görüntülerini proje içindeki `screenshots` klasörüne `ana_ekran.png`, `durum_bildir.png` vb. isimlerle eklemelisiniz.)*
```bash
# 1. Projeyi klonla
git clone https://github.com/KULLANICI_ADIN/Offline-Deprem.git
🏗️ Mimari
Enkazdan Kurtar katmanlı Clean Architecture ve MVVM yapısı kullanır; arayüz, durum (state) ve iş mantığı net biçimde ayrılır:
# 2. Android Studio'da aç
# File → Open → app/ klasörünü seç
Görünüm (UI): ui/ — Jetpack Compose ekranları, Navigation ve tema bağımlı bileşenler.
Durum / ViewModel: StateFlow kullanılarak reaktif iş mantığı yönetimi.
Alan / Veri (Domain): domain/ — Saf Kotlin, iş kuralları, Entity ve Repository arayüzleri. (Android kütüphanelerinden tamamen bağımsız)
Veri (Data): data/ — BLE, Wi-Fi P2P ve yerel veritabanı (Repository implementasyonları).
# 3. Çalıştır
# ▶ Run tuşuna bas (emülatör veya fiziksel cihaz)
```
OfflineDeprem/
├── app/src/main/java/...
│   ├── domain/           # Saf Kotlin, bağımsız kurallar (Interface + Entity)
│   ├── data/             # Repository impl. (BLE, Wi-Fi P2P, In-Memory)
│   ├── ui/               # Compose ekranları ve ViewModeller
│   └── theme/            # Material 3 tasarım token'ları
└── build.gradle.kts      # Proje yapılandırması
## 📸 Ekran Görüntüleri
🛠️ Teknoloji Yığını
Çatı: Android SDK
Dil: Kotlin
Arayüz & Navigasyon: Jetpack Compose, Material Design 3, Compose Navigation
Mimari: Clean Architecture, MVVM
Asenkron & Reaktif: Kotlin Coroutines & Flow
Ağ Bağlantısı: Bluetooth LE (Beacon/Advertise), Wi-Fi P2P (Direct)
*(Bu alana uygulamanın çalışırken alınmış ekran görüntüleri eklenecektir.)*
🚀 Kurulum
Gereksinimler: Android Studio, Android 8.0 (API 26) ve üzeri fiziksel bir cihaz (Bluetooth/Wi-Fi donanımı gerektiği için emülatörde tam test edilemez).
| Ana Ekran | Durum Bildir | Mesh Ağı Tarama |
|-----------|-------------|-----------------|
| *(screenshot)* | *(screenshot)* | *(screenshot)* |
# Depoyu klonla
git clone https://github.com/KULLANICI_ADIN/Offline-Deprem.git
cd Offline-Deprem
## 👥 Geliştirici
# Android Studio'da aç ve cihazına kur
Proje dizinini Android Studio ile açın. Telefonunuzu USB ile bağlayıp USB Hata Ayıklama modunu açın. "Run" tuşuna basarak cihazınızda çalıştırın.
- **Ad Soyad** — *Proje sahibi*
ADB ile hızlı kurulum:
adb install -r "app\app\build\outputs\apk\debug\app-debug.apk"
---
🗺️ Yol Haritası
✅ Tamamlanan
 Cihazlar arası BLE yayın (Advertise) ve tarama (Scan) yeteneği
 Wi-Fi P2P cihaz keşfi
 Durum bildirme (Güvendeyim, Enkaz Altındayım vb.)
 Çevrimdışı acil toplanma alanları haritası
 Kamera flaşı ile otomatik Mors alfabesi (SOS) sinyali
 MVVM ve Clean Architecture altyapısı
*Bu proje, Nesne Yönelimli Programlama (OOP) dersi Final teslimi için geliştirilmiş olup, Clean Architecture, MVVM, ve Agile (Sprint) süreçleri uygulanarak hazırlanmıştır.*
🔜 Planlanan
 Wi-Fi P2P üzerinden gerçek cihazdan cihaza socket veri aktarımı
 BLE GATT katmanı ile daha büyük veri paketlerinin aktarımı
 Gateway Kuyruğu: İnternet bağlantısı geldiğinde bekleyen verilerin buluta senkronizasyonu
 Play Store ve App Store (KMP geçişi ile) yayını
⚠️ Sorumluluk Reddi
Enkazdan Kurtar (Offline Deprem) MVP (Minimum Viable Product) aşamasında bir projedir. Gerçek bir afet anında iletişimin kesintisiz sağlanacağının garantisini veremez; çevresel faktörlere, donanım limitlerine ve etraftaki cihaz yoğunluğuna bağlıdır. 
🆘 Acil bir durumda 112'yi arayın. AFAD ve resmi kurtarma ekiplerinin yönlendirmelerine uyun.
👨💻 Geliştirici
Bu proje, Nesne Yönelimli Programlama (OOP) ve modern Android geliştirme süreçleri (Clean Architecture, MVVM) referans alınarak geliştirilmiştir.
🌍 "Her karanlığın ardında bir aydınlık, her enkazın altında bir umut vardır."
