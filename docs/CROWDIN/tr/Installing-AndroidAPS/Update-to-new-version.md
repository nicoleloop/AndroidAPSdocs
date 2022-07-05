# Yeni bir ana sürüme veya yan sürüme güncelleme

## Programı İndirmek yerine kendiniz oluşturun...

**AndroidAPS, tıbbi cihazlarla ilgili düzenlemeler nedeniyle indirilebilen bir uygulama değildir. Uygulamayı kendi kullanımınız için oluşturmak yasaldır, ancak bir kopyasını başkasına vermemelisiniz! Ayrıntılar için [SSS sayfasına](../Getting-Started/FAQ.md) bakın.**

## Önemli notlar

* Lütfen yeni bir sürüm çıktıktan sonra mümkün olan en kısa sürede güncelleyin. Yeni sürüm hakkında [AndroidAPS ana ekranında bilgi](../Installing-AndroidAPS/Releasenotes#release-notes) alacaksınız.
* 2.7 sürümünden itibaren depo konumu <https://github.com/nightscout/AndroidAPS> olarak değiştirildi. Git'e aşina değilseniz, güncellemenin en kolay yolu, AndroidAPS dizini kaldırmak ve [yeni bir klon](../Installing-AndroidAPS/Building-APK.md) oluşturmaktır.
* Apk'yi oluşturmak için lütfen **[Android Studio Sürüm 2020.3.1 (Arctic Fox)](https://developer.android.com/studio/)** veya daha yenisini kullanın.
* [Windows 10 32-bit sistemler](../Installing-AndroidAPS/troubleshooting_androidstudio#unable-to-start-daemon-process) Android Studio 2020.3.1 tarafından desteklenmez.
* Mevcut sürüm için [Sürüm Notlarını](../Installing-AndroidAPS/Releasenotes) okuduğunuzdan emin olun

## AndroidAPS sürümünüzü güncellemeye genel bakış

1. Telefonunuzdaki mevcut eski AAPS sürümünden [ayarlarınızı dışa aktarın](../Usage/ExportImportSettings#ayarlarinizi-disa-aktarin). İhtiyacınız olmayabilir, ancak üzülmektense kurtarmış olmak daha iyidir.
2. AndroidAPS kaynak kodunun [yerel kopyasını güncelleyin](../Installing-AndroidAPS/Update-to-new-version#update-your-local-copy) (Git->Fetch and Git -> Pull)
3. [İmzalı APK Derleyin](../Installing-AndroidAPS/Update-to-new-version#build-the-signed-apk)
4. [Derlenmiş apk'yı](../Installing-AndroidAPS/Building-APK#transfer-apk-to-smartphone) telefonunuza aktarın ve yükleyin
5. AndroidAPS'de [sürümü kontrol edin](#check-aaps-version-on-phone)
6. [KŞ kaynağınıza](../Configuration/BG-Source.rst) bağlı olarak, xDrip'te [alıcıyı tanımladığınızdan](../Configuration/xdrip#identify-receiver) emin olun veya ['Kendi Dexcom Uygulamanızı oluşturun (BYODA)'](../Hardware/DexcomG6#if-using-g6-with-build-your-own-dexcom-app).

Sorun yaşamanız durumunda, [Android Studio'da sorun giderme](../Installing-AndroidAPS/troubleshooting_androidstudio) konusu için ayrı sayfaya bakın.

## 1. Ayarlarınızı dışa aktarın

Bunu nasıl yapacağınızı hatırlamıyorsanız, [ayarları dışa & içe aktarma](../Usage/ExportImportSettings#export-settings) sayfasına bakın.

## 2. Yerel kopyanızı güncelleyin

2.7 sürümünden itibaren depo konumu <https://github.com/nightscout/AndroidAPS> olarak değiştirildi. Git'e aşina değilseniz, güncellemenin en kolay yolu, diskinizdeki AndroidAPS ile dizini kaldırmak ve [Yeni klon](../Installing-AndroidAPS/Building-APK.md) yapmak için talimatları takip etmektir.

URL'yi zaten değiştirdiyseniz veya 2.8.x sürümünden güncelleme yaptıysanız, şu adımları izleyin:

* Mevcut AndroidAPS projenizi Android Studio ile açın. Projenizi seçmeniz gerekebilir. AndroidAPS projesine (Çift) tıklayın.
    
    ![Android Studio - Proje Seç](../images/update/01_ProjectSelection.png)

* Android Studio'nun menü çubuğunda Git -> Fetch'i seçin
    
    ![Android Studio Menüsü - Git - Fetch](../images/update/02_GitFetch.png)

* Sağ alt köşede Fetch'in başarılı olduğuna dair bir mesaj göreceksiniz.
    
    ![Android Studio Menüsü - Git - Fetch başarılı](../images/update/03_GitFetchSuccessful.png)

* Menü çubuğunda şimdi Git -> Pull'u seçin
    
    ![Android Studio Menüsü - Git - Pull](../images/update/04_GitPull.png)

* Tüm seçenekleri olduğu gibi bırakın (Origin/master) ve Pull'u seçin
    
    ![Android Studio - Git - Pull iletişim kutusu](../images/update/05_GitPullOptions.png)

* İndirme devam ederken bekleyin, bunu alt çubukta bilgi olarak göreceksiniz. Tamamlandığında, bir başarı mesajı göreceksiniz. Not: Güncellenen dosyalar değişiklik gösterebilir! Bu bir gösterge değildir
    
    ![Android Studio - Git - Pull başarılı](../images/update/06_GitPullSuccess.png)

* Gradle Sync, bazı bağımlılıkları indirmek için birkaç saniye çalışacaktır. Tamamlanana kadar bekleyin.
    
    ![Android Studio - Gradle Sync](../images/studioSetup/40_BackgroundTasks.png)

## 3. İmzalı APK'yı Derleyin

Kaynak kodunuz artık yayınlanan güncel sürümdür. [İmzalı apk derle bölümünde](../Installing-AndroidAPS/Building-APK#generate-signed-apk) açıklandığı gibi bundan imzalı apk derlemenin zamanı geldi.

## 4. Apk dosyasını aktarma

Yükleyebilmeniz için apk'yı telefonunuza aktarmanız gerekir.

[APK'yi akıllı telefona aktarma](../Installing-AndroidAPS/Building-APK#transfer-apk-to-smartphone) talimatlarına bakın

## 5. Apk dosyasını kurun

Telefonunuzda bilinmeyen kaynaklardan kuruluma izin vermelisiniz. Bunun nasıl yapılacağına ilişkin kılavuzlar internette bulunabilir (yani [burada](https://www.expressvpn.com/de/support/vpn-setup/enable-apk-installs-android/) veya [burada](https://www.androidcentral.com/unknown-sources)).

## 6. Telefondaki AAPS sürümünü kontrol edin

Yeni apk'yı yükledikten sonra, sağ üstteki üç nokta menüsüne ve ardından Hakkında'ya tıklayarak telefonunuzdaki AAPS sürümünü kontrol edebilirsiniz. Mevcut sürümü görmelisiniz.

![Yüklü AAPS sürümü](../images/Update_VersionCheck282.png)

# Sorun giderme

Bir şeyler ters giderse, panik yapmayın.

Bir Nefes Alın!

Ardından, sorununuz zaten belgelenmişse, [Android Studio sorun giderme](../Installing-AndroidAPS/troubleshooting_androidstudio) sayfasına bakın!