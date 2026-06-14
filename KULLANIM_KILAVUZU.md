# enkazdan kurtar - Kullanım Kılavuzu

## Uygulama Özeti

`enkazdan kurtar`, afet anında internet veya baz istasyonu erişimi olmadığında temel durum bilgisini cihazlar arasında paylaşmayı hedefleyen Android uygulamasıdır. Uygulama Bluetooth Low Energy, Wi-Fi P2P keşfi, yerel gateway kuyruğu, çevrimdışı acil nokta haritası ve flaş ile SOS sinyali özelliklerini içerir.

## APK Bilgisi

Oluşturulan debug APK dosyası:

```text
app/app/build/outputs/apk/debug/app-debug.apk
```

Uygulama adı:

```text
enkazdan kurtar
```

Uygulama logosu:

```text
launcher_preview.png
```

## Kurulum

### Android Studio ile Kurulum

1. Android Studio'yu açın.
2. `C:\Users\musta\OneDrive\Masaüstü\offline deprem\app` klasörünü proje olarak açın.
3. Telefonu USB ile bağlayın.
4. Telefonda `Geliştirici Seçenekleri > USB hata ayıklama` ayarını açın.
5. Android Studio'da cihazı seçip `Run` düğmesine basın.

### APK ile Kurulum

1. APK dosyasını telefona aktarın:

```text
app/app/build/outputs/apk/debug/app-debug.apk
```

2. Telefonda APK dosyasını açın.
3. Gerekirse `Bilinmeyen uygulamaları yükle` iznini verin.
4. Kurulumu tamamlayın.

### ADB ile Kurulum

PowerShell'de proje klasöründe şu komutu çalıştırın:

```powershell
adb install -r "app\app\build\outputs\apk\debug\app-debug.apk"
```

## Gerekli İzinler

Uygulama bazı özellikler için izin ister:

- Bluetooth / Yakındaki Cihazlar: Mesh ağ taraması ve BLE yayını için.
- Konum: Eski Android sürümlerinde BLE ve Wi-Fi P2P keşfi için gerekebilir.
- Kamera: Flaş ile SOS sinyali göndermek için.
- İnternet / Ağ Durumu: Gateway kuyruğunun internete aktarım durumunu anlamak için.

İzin verilmezse ilgili özellik çalışmayabilir; uygulama bu durumu `Ağ Durumu` bölümünde raporlar.

## Ana Ekran

Ana ekranda afet durum kayıtları görünür. Uygulama artık rastgele kişi veya yardım talebi göstermez. İlk açılışta liste boş olur.

Ekrandaki temel alanlar:

- `Durumunu Bildir`: Kendi durumunuzu eklemek için kullanılır.
- Üstteki SOS simgesi: Flaş ile SOS sinyali ekranını açar.
- Üstteki konum simgesi: Çevrimdışı harita ekranını açar.
- Üstteki tarama simgesi: Mesh ağ tarama ekranını açar.

## Durum Bildirme

1. Ana ekranda `Durumunu Bildir` düğmesine basın.
2. Adınızı ve konumunuzu girin.
3. Durum seçin:
   - Güvendeyim
   - Yardıma İhtiyacım Var
   - Enkaz Altındayım
   - Tıbbi Yardım Gerekli
4. `Mesh Ağına Gönder` düğmesine basın.

Gönderilen durum ana ekranda görünür ve cihaz uygunsa BLE üzerinden kısa acil durum yayını denenir. İnternet varsa gateway kuyruğu aktarımı yapılır; internet yoksa kayıt yerel kuyrukta bekler.

## Mesh Ağı Tarama

1. Ana ekrandaki tarama simgesine basın.
2. `Taramayı Başlat` düğmesine basın.
3. İzin istenirse Bluetooth, Yakındaki Cihazlar ve Konum izinlerini verin.
4. Ekranda şu bilgiler görünür:
   - BLE durumu
   - Wi-Fi P2P durumu
   - Gateway kuyruğu
   - Bulunan cihazlar
   - Raporlanan problemler

Not: Wi-Fi P2P tarafında şu an cihaz keşfi vardır. Üretim seviyesinde gerçek veri aktarımı için Wi-Fi P2P grup bağlantısı ve socket aktarımı ayrıca geliştirilmelidir.

## Çevrimdışı Harita

1. Ana ekrandaki konum simgesine basın.
2. Harita ekranında önbellekli acil noktaları görüntüleyin.
3. Filtrelerden nokta türü seçebilirsiniz:
   - Toplanma Alanı
   - Sağlık Noktası
   - Lojistik Noktası
   - Riskli Bölge

Not: Bu ekran Mapbox/OSM tile paketi kullanmaz. Uygulama içi kayıtlı acil nokta verilerini ve Canvas tabanlı harita görünümünü kullanır.

## SOS Işık Sinyali

1. Ana ekrandaki SOS simgesine basın.
2. `SOS Başlat` düğmesine basın.
3. Kamera izni istenirse izin verin.
4. Telefon flaşı Mors alfabesine göre SOS döngüsü göndermeye başlar.
5. Durdurmak için `Durdur` düğmesine basın.

Not: Bu özellik emülatörde çalışmayabilir. Fiziksel cihazda kamera flaşı bulunmalıdır.

## Test Etme

### Derleme Testi

PowerShell'de:

```powershell
cd "C:\Users\musta\OneDrive\Masaüstü\offline deprem\app"
$env:JAVA_HOME="C:\Program Files\Android\openjdk\jdk-21.0.8"
$env:Path="C:\Program Files\Android\openjdk\jdk-21.0.8\bin;" + $env:Path
$env:GRADLE_USER_HOME="C:\Users\musta\.gradle"
& "C:\Users\musta\.gradle\wrapper\dists\gradle-9.1.0-bin\9agqghryom9wkf8r80qlhnts3\gradle-9.1.0\bin\gradle.bat" testDebugUnitTest assembleDebug --offline --no-configuration-cache --no-build-cache
```

Başarılı çıktıda şunu görmelisiniz:

```text
BUILD SUCCESSFUL
```

### Fiziksel Cihaz Testi

En doğru test için en az iki fiziksel Android cihaz önerilir:

1. Her iki cihaza APK'yı kurun.
2. Bluetooth ve Wi-Fi açık olsun.
3. İlk cihazda durum bildirin.
4. İkinci cihazda Mesh tarama ekranını açıp tarama başlatın.
5. Ağ durumu ve bulunan cihazlar bölümünü kontrol edin.

## Bilinen Sınırlamalar

- BLE yayını kısa beacon seviyesindedir; büyük mesaj aktarımı için GATT/protokol katmanı gerekir.
- Wi-Fi P2P gerçek veri aktarımı henüz tam socket/grup bağlantısı seviyesinde değildir.
- Çevrimdışı harita gerçek OSM/Mapbox tile cache kullanmaz.
- SOS flaş özelliği emülatörde çalışmayabilir.
- Debug APK imzalıdır; Play Store yayını için release imzası ve production ayarları gerekir.

## Sorun Giderme

### Uygulama Kurulmuyor

- Telefonda eski sürüm varsa kaldırıp tekrar kurun.
- `Bilinmeyen uygulamaları yükle` iznini açın.
- ADB ile kuruyorsanız cihazın bağlı olduğunu kontrol edin:

```powershell
adb devices
```

### Bluetooth Taraması Çalışmıyor

- Bluetooth açık olmalı.
- Yakındaki cihazlar izni verilmiş olmalı.
- Android 12 ve üzeri cihazlarda `BLUETOOTH_SCAN`, `BLUETOOTH_CONNECT`, `BLUETOOTH_ADVERTISE` izinleri gerekir.

### SOS Çalışmıyor

- Fiziksel cihaz kullanın.
- Kamera izni verin.
- Cihazda flaş donanımı olduğundan emin olun.

### APK Yeniden Oluşturma

```powershell
cd "C:\Users\musta\OneDrive\Masaüstü\offline deprem\app"
$env:JAVA_HOME="C:\Program Files\Android\openjdk\jdk-21.0.8"
$env:Path="C:\Program Files\Android\openjdk\jdk-21.0.8\bin;" + $env:Path
$env:GRADLE_USER_HOME="C:\Users\musta\.gradle"
& "C:\Users\musta\.gradle\wrapper\dists\gradle-9.1.0-bin\9agqghryom9wkf8r80qlhnts3\gradle-9.1.0\bin\gradle.bat" assembleDebug
```

Yeni APK şu konuma yazılır:

```text
app/app/build/outputs/apk/debug/app-debug.apk
```
