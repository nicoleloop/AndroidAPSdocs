# Omnipod DASH

Bu talimatlar **Omnipod DASH** nesil pompayı yapılandırmak içindir **(Omnipod Eros DEĞİL)**. Omnipod sürücüsü, 3.0 sürümünden itibaren AndroidAPS'nin (AAPS) bir eklentisi olarak mevcuttur.

**Bu yazılım bir DIY (Kendin Yap) yapay pankreas çözümünün bir parçasıdır ve bir ürün değildir, ancak nasıl kullanılacağı da dahil olmak üzere sistemi okumanızı, öğrenmenizi ve anlamanızı gerektirir. Yazılımla yaptıklarınızdan yalnızca siz sorumlusunuz.**

## Omnipod DASH özellikleri

**Omnipod DASH**'ın özellikleri ve onu **Omnipod EROS**'dan ayıran özellikler şunlardır:

* DASH podları mavi bir iğne kapağıyla tanımlanır (EROS'un şeffaf bir iğne kapağı vardır). Podlar, fiziksel boyutlar açısından birbirinin aynıdır
* Bağlantı için ayrı bir BLE bağlantı/köprü cihazına gerek yoktur (RileyLink, OrangeLink veya EmaLink gerekmez).
* BT bağlantısı yalnızca komut göndermek için gerektiğinde yapılır ve hemen sonra bağlantı kesilir!
* Artık "köprü cihazına bağlantı yok / pod" hataları yok
* AAPS komutları göndermek için pod erişilebilirliğini bekleyecek
* Aktifleştirmede, AAPS yeni bir DASH podunu bulacak ve bağlayacaktır.
* Beklenen menzil: 5-10 metre (YMMV)

## Donanım/Yazılım Gereksinimleri

* Yeni bir **Omnipod DASH Pod** (Mavi iğne kapağıyla anlaşılır)

![Omnipod Pod](../images/DASH_images/Omnipod_Pod.png)

* BLE Bluetooth bağlantısına sahip **Uyumlu Android telefon**
   -  Tüm telefon donanımları ve Android sürümlerinin çalışması garanti edilmez. Lütfen [**DASH Test Edilen telefonları**](https://docs.google.com/spreadsheets/d/1zO-Vf3wv0jji5Gflk6pe48oi348ApF5RvMcI6NG5TnY) kontrol edin veya sadece telefonunuzla deneyin ve sonucu bize bildirin (telefon referansı ve coğrafi bölge, Android sürümü, "çalıştı / bazı zorluklar mevcut / çalışmadı" şeklinde).
   - **Önemli not: Yazılım sürümü 3.XX.X olan pod ile birlikte kullanırken birçok kalıcı, kurtarılamaz bağlantı kaybı vakası olmuştur. Bu eski yazılımlı podları AndroidAPS ile kullanırken özellikle diğer bluetooth cihazları telefonunuza bağlı ise dikkatli olun!**  
     AAPS Omnipod Dash sürücüsünün her komut gönderdiğinde Bluetooth aracılığıyla Dash POD'a bağlandığını ve hemen ardından bağlantısının kesildiğini unutmayın. Bluetooth bağlantıları AAPS çalıştıran telefona bağlı olan kulaklık vb. diğer cihazlar tarafından bozulabilir, (bazı telefon modellerinde ender durumlarda bağlantı sorununa veya etkinleştirme sırasında veya sonrasında pod hatalarına/kaybına neden olabilir) veya etkilenebilir.
   -  [**APK Derle**](../Installing-AndroidAPS/Building-APK.html#) talimatları kullanılarak **AndroidAPS'nin 3.0 veya daha yeni sürümü derleyin ve yükleyin**.
* [**Sürekli Glikoz İzleme (CGM)**](https://androidaps.readthedocs.io/en/latest/Configuration/BG-Source.html)

Bu talimatlar, yeni bir pod oturumu başlattığınızı varsayacaktır; durum böyle değilse, lütfen sabırlı olun ve bir sonraki pod değişikliğinizde bu işleme başlayın.

## Başlamadan önce

**ÖNCE GÜVENLİK** - bir hatadan kurtulamayacağınız bir ortamda bu işlemi denemeyin (ekstra pod, insülin ve telefon cihazları olmazsa olmazdır).

**AAPS Dash sürücüsü podunuzu etkinleştirdikten sonra Omnipod Dash PDM'niz artık çalışmayacaktır.** Önceden Dash podunuza komut göndermek için Dash PDM'nizi kullanıyordunuz. Bir Dash podu, yalnızca tek bir cihazın kendisiyle iletişim kurmak için komutlar göndermesine izin verir. Podu başarıyla etkinleştiren cihaz, o andan itibaren onunla iletişim kurmasına izin verilen tek cihazdır. Bu Android telefonunuzla AAPS Dash sürücüsü aracılığıyla bir Dash podunu etkinleştirdiğinizde, **PDM'nizi artık o podla kullanamayacağınız anlamına gelir**. Android telefonunuzdaki AAPS Dash sürücüsü artık vekil PDM'nizdir.

*Bu PDM'nizi atmanız gerektiği anlamına GELMEZ, yedek olarak ve örneğin telefonunuz kaybolduğunda veya AAPS düzgün çalışmadığında acil durumlar için bir kenarda tutmanız önerilir.*

**Podunuz, AndroidAPS'ye bağlı olmadığında insülin vermeyi durdurmaz**. Varsayılan bazal oranlar, geçerli etkin profilde tanımlandığı gibi etkinleştirme sırasında poda programlanır. AndroidAPS çalışır durumda olduğu sürece, maksimum 120 dakika boyunca çalışan bazal oran komutları gönderir. Herhangi bir nedenle pod herhangi bir yeni komut almadığında (örneğin, Pod - telefon mesafesi nedeniyle iletişimin kesilmesi) pod otomatik olarak varsayılan bazal oranlarına geri dönecektir.

**30 dk Bazal Oranı Profilleri AndroidAPS'de DESTEKLENMEZ.** **AndroidAPS Profili, 30 dakikalık bir bazal oran zaman dilimini desteklemiyor.** AndroidAPS'de yeniyseniz ve bazal oran profilinizi ilk kez oluşturuyorsanız, yarım saatlik bazal oranların desteklenmediğini ve başlangıç için bazal oran profilinizi saatlik olarak ayarlamanız gerekeceğini lütfen unutmayın. Örneğin, 09:30'da başlayan ve 11:30'da biten 2 saatlik bir süresi olan 1,1 birimlik bir bazal oranınız varsa, bu çalışmayacaktır. Bu 1,1 birim bazal oranını 9:00-11:00 veya 10:00-12:00 zaman aralığına değiştirmeniz gerekecektir. Omnipod Dash donanımının kendisi 30 dakikalık bazal oran profili artışlarını desteklese de, AndroidAPS şu anda algoritmalarıyla bunları hesaba katamıyor.

## AAPS'de Dash Sürücüsünü Etkinleştirme

Dash sürücüsünü AAPS'de **iki şekilde** etkinleştirebilirsiniz:

### Seçenek 1: Yeni kurulum

AndroidAPS'yi ilk kez kurarken, **Kurulum Sihirbazı**, AndroidAPS'yi yüklemeniz için size rehberlik edecektir. Pompa seçimine ulaştığınızda “DASH” seçeneğini seçin.

![Enable_Dash_1](../images/DASH_images/Enable_Dash/Enable_Dash_1.png)

Şüphe duyduğunuzda, AndroidAPS'yi kurduktan sonra “Sanal Pompa”yı ve daha sonra “DASH”ı da seçebilirsiniz (bkz. seçenek 2).

### Seçenek 2: Konfigürasyon ayarları

Mevcut bir kurulumda, Konfigürasyon ayarları altında **DASH** pompasını seçebilirsiniz:

Sol üst köşede **hamburger menüsü** seçilip **Konfigürasyon ayarları (1)**\ ➜\ **Pompa**\ ➜\ **Dash**\ ➜**Dişli Çark (3)** Dash satırındaki ** radyo butonu (2)** seçilir.

**Dişli çark (3)**'ın yanındaki **onay kutusu (4)**'nun seçilmesi, Dash menüsünün AAPS arayüzünde **DASH** başlıklı bir sekme olarak görüntülenmesini sağlar. Bu kutuyu işaretlemek, AAPS kullanırken DASH komutlarına erişiminizi kolaylaştıracaktır.

**NOT:** [**Dash ayarlarına**](#dash-settings) erişmenin daha hızlı bir yolunu, aşağıda bu dokümantasyonun Dash ayarları kısmında bulabilirsiniz.

![Enable_Dash_3](../images/DASH_images/Enable_Dash/Enable_Dash_3.png)

### Omnipod Sürücü Seçiminin Doğrulanması

Eğer kutucuğu (4) işaretlediyseniz, AAPS'de Dash pompasını etkinleştirdiğinizi doğrulamak için, **Giriş** sekmesinde **sola kaydırarak** **DASH** sekmesine ulaşmanız gerekir. Kutucuğu işaretlemediyseniz, sol üstteki hamburger menüsünde pompalar kısmında DASH satırında bulacaksınız.

![Enable_Dash_4](../images/DASH_images/Enable_Dash/Enable_Dash_4.jpg)

## Dash Konfigürasyonu

Lütfen **sola kaydırıp** tüm pod işlevlerini yönetebileceğiniz **DASH** sekmesine ulaşın.(bu işlevlerden bazıları etkin bir pod oturumu olmadan etkinleştirilmez veya görünmez):

![Refresh_LOGO](../images/DASH_images/Refresh_LOGO.png) Pod bağlantısını ve durumunu yenileyin, pod bip sesleri pod alarmlarında susturabilir.

![POD_MGMT_LOGO](../images/DASH_images/POD_MGMT_LOGO.png) Pod Yönetimi (Etkinleştir, Devre Dışı Bırak, Test bip sesini çal ve Pod geçmişi)

### Pod Etkinleştirme

1. **DASH** sekmesine gidin. **POD YNTM (1)** butonuna ve ardından **Pod Etkinleştir (2) **butonuna tıklayın.

![Activate_Pod_1](../images/DASH_images/Activate_Pod/Activate_Pod_1.png)    ![Activate_Pod_2](../images/DASH_images/Activate_Pod/Activate_Pod_2.png)

2. **Podu Doldur** ekranı görüntülenir. Yeni bir podu en az 80 ünite insülinle doldurun ve podun kullanıma hazır olduğunu belirten iki bip sesini dinleyin. 3 gün boyunca ihtiyacınız olan toplam insülin miktarını hesaplarken, pod hazırlamanın ilave 3-10 ünite kullanacağını lütfen göz önünde bulundurun.

![Activate_Pod_3](../images/DASH_images/Activate_Pod/Activate_Pod_3.png)    ![Activate_Pod_4](../images/DASH_images/Activate_Pod/Activate_Pod_4.jpg)

Yeni podun ve AAPS yüklü telefonun birbirine yakın olduğundan emin olun ve **İleri** butonunu tıklayın.

**NOT**: Aşağıdaki hata mesajını almanız durumunda (bu olabilir), panik yapmayın. **TEKRAR DENE** butonunu tıklayın. Çoğu durumda etkinleştirme başarıyla devam eder.

![Activate_Pod_3](../images/DASH_images/Activate_pod_error.png)

3. **Pod'u Başlat** ekranında, pod hazırlanmaya başlar (pod kendini hazırlarken bir tıklama ve ardından bir dizi tıkırtı sesi duyarsınız).  Başarılı kullanıma hazırlamanın ardından yeşil bir onay işareti gösterilecek ve **İleri** butonu aktif olacaktır. Pod hazırlama işlemini tamamlamak ve **Pod Ekle** ekranını görüntülemek için **İleri** butonunu tıklayın.

![Activate_Pod_5](../images/DASH_images/Activate_Pod/Activate_Pod_5.jpg)    ![Activate_Pod_6](../images/DASH_images/Activate_Pod/Activate_Pod_6.jpg)

4. Ardından, yeni podun infüzyon bölgesini hazırlayın. Podun plastik iğne kapağını çıkarın. Poddan dışarı çıkan bir şey görürseniz, işlemi iptal edin ve yeni bir pod ile başlayın. Her şey yolunda görünüyorsa, yapışkanın arkasındaki beyaz kağıdı çıkarın ve podu vücudunuzdaki seçtiğiniz bölgeye uygulayın. Bitirdiğinizde, **İleri** butonunu tıklayın.

![Activate_Pod_8](../images/DASH_images/Activate_Pod/Activate_Pod_8.jpg)

5. **Pod Ekle** iletişim kutusu şimdi görünecektir. **Kanülü vücudunuza yerleştirmeye hazırsanız Tamam düğmesini tıklayın**.

![Activate_Pod_9](../images/DASH_images/Activate_Pod/Activate_Pod_9.jpg)

6. **Tamam**'a bastıktan sonra, Dash podunun yanıt vermesi ve kanülü yerleştirmesi biraz zaman alabilir (en fazla 1-2 dakika), bu yüzden sabırlı olun.

 *NOT: Kanül takılmadan önce, kanül yerleştirme noktasının etrafındaki cildi sıkıştırmak iyi bir uygulamadır. Bu iğnenin düzgün bir şekilde yerleştirilmesini sağlar ve tıkanıklık oluşturma şansınızı azaltır.*

![Activate_Pod_10](../images/DASH_images/Activate_Pod/Activate_Pod_10.png)    ![Activate_Pod_11](../images/DASH_images/Activate_Pod/Activate_Pod_11.jpg)

7. Başarılı bir kanül yerleştirilmesinden sonra yeşil bir onay işareti görünür ve **İleri** butonu aktif olur. **İleri** butonunu tıklayın.

![Activate_Pod_12](../images/DASH_images/Activate_Pod/Activate_Pod_12.jpg)

9. **Pod etkinleştirildi** ekranı görüntülenir. Yeşil **Bitti** düğmesini tıklayın. Tebrikler! Artık yeni bir aktif pod oturumu başlattınız.

![Activate_Pod_13](../images/DASH_images/Activate_Pod/Activate_Pod_13.jpg)

10. **Pod yönetimi** menüsünde şimdi **Pod Etkinleştir (1)** butonu <em x-id"3"=>devre dışı</em> olmalı ve **Pod'u Devre Dışı Bırak (2)** butonu *aktif olmalıdır.*. Bunun nedeni, bir podun artık etkin olması ve o anda etkin olan podu devre dışı bırakmadan ek bir pod etkinleştirememenizdendir.

    **DASH** sekme ekranına dönmek için telefonunuzdaki geri düğmesini tıklayın. Şimdi aktif pod oturumunuz için mevcut bazal oran, pod rezervuar seviyesi, iletilen insülin, pod hataları ve uyarılar dahil Pod bilgileri görüntülenecektir.

    Görüntülenen bilgilerle ilgili daha fazla ayrıntı için bu dokümantasyonun [**DASH Sekmesi**](#dash-tab) bölümüne gidin.

![Activate_Pod_14](../images/DASH_images/Activate_Pod/Activate_Pod_14.png)    ![Activate_Pod_15](../images/DASH_images/Activate_Pod/Activate_Pod_15.jpg)

Podu etkinleştirdikten SONRA ayarları dışa aktarmak akıllıca olacaktır. Bunu her pod değişikliğinde yapın ve ayda bir dışa aktarılan dosyayı internet sürücünüze (cloud) kopyalayın. [**Dışarı aktarma ayarları dokümantasyonuna bakabilirsiniz **](https://androidaps.readthedocs.io/en/latest/Usage/ExportImportSettings.html?highlight=exporting#export-import-settings).


### Pod'u Devre Dışı Bırakma

Normal koşullar altında, bir podun beklenen ömrü üç gündür. (72 saat) Pod sona erme uyarısından sonra ek 8 saattlik süre ile toplam 80 saat olabilir.

Bir Podu devre dışı bırakmak (süre sonundan veya bir pod hatasından dolayı):

1. **DASH** sekmesine gidin, **POD YNTM (1)** butonunu tıklayın, **pod yönetimi** ekranında **Pod'u Devre Dışı Bırak (2)** butonunu tıklayın.

![Deactivate_Pod_1](../images/DASH_images/Deactivate_Pod/Deactivate_Pod_1.jpg)    ![Deactivate_Pod_2](../images/DASH_images/Deactivate_Pod/Deactivate_Pod_2.png)

2. **Pod'u Devre Dışı Bırak** ekranında, podu devre dışı bırakma işlemini başlatmak için **İleri** butonunu tıklayın. Devre dışı bırakmanın başarılı olduğuna dair poddan bir onay bip sesi alacaksınız.

![Deactivate_Pod_3](../images/DASH_images/Deactivate_Pod/Deactivate_Pod_3.jpg) ![Deactivate_Pod_4](../images/DASH_images/Deactivate_Pod/Deactivate_Pod_4.jpg)

3. Başarılı bir şekilde devre dışı bırakmanın ardından yeşil bir onay işareti görünecektir. Pod devre dışı ekranını görüntülemek için **İleri** butonunu tıklayın. Etkin oturum devre dışı bırakıldığı için artık podunuzu çıkartabilirsiniz.

![Deactivate_Pod_5](../images/DASH_images/Deactivate_Pod/Deactivate_Pod_5.jpg)

4. **Pod Yönetimi** ekranına dönmek için yeşil butona tıklayın.

![Deactivate_Pod_6](../images/DASH_images/Deactivate_Pod/Deactivate_Pod_6.jpg)

5. Artık **Pod Yönetimi** menüsündesiniz; **DASH** sekmesine dönmek için telefonunuzdaki geri butonuna basın. **Pod durumu:** alanında bir **Aktif pod yok** mesajının görüntülendiğini doğrulayın.

![Deactivate_Pod_7](../images/DASH_images/Deactivate_Pod/Deactivate_Pod_7.png) ![Deactivate_Pod_8](../images/DASH_images/Deactivate_Pod/Deactivate_Pod_8.jpg)

### İnsülin İletimini Sürdür

**Not**: Profil geçişleri sırasında dash, yeni bazal profili ayarlamadan önce iletimi askıya almalıdır. İki komut arasında iletişim başarısız olursa, iletim askıya alınabilir. Daha fazla ayrıntı için sorun giderme bölümündeki [**İletim askıya alındı**](#delivery-suspended) konusunu okuyun.

Aktif şu anda askıya alınmış Pod'unuzun insülin iletimini yeniden başlatma talimatı vermek için bu komutu kullanın. Komut başarıyla işlendikten sonra insülin, aktif bazal profilden geçerli zamana dayalı olarak mevcut bazal oranı kullanarak normal iletimi sürdürecektir. Pod bolus, GBO ve SMB için komutları tekrar kabul edecektir.

1. **DASH** sekmesine gidin ve **Pod durumu (1)** satırında **ASKIYA ALINDI** mesajının görünmesi gerekir, ardından mevcut podun normal insülin iletimini sürdürmesi talimatını vermek için **İLETİME DEVAM ET (2)** butonuna basın. **Pod Durumu (3)** satırında **İleme Devam Et** mesajı görüntülenir.

![Resume_1](../images/DASH_images/Resume/Resume_1.jpg)   ![Resume_2](../images/DASH_images/Resume/Resume_2.jpg)

2. İletimi sürdür komutu başarılı olduğunda, bir onay iletişim kutusu **İnsülin iletimi yeniden başlatıldı.** mesajını görüntüler. Onaylamak ve devam etmek için **Tamam**'ı tıklayın.

![Resume_3](../images/DASH_images/Resume/Resume_3.png)

3. **DASH** sekmesi, **Pod durumu (1)** satırını **ÇALIŞIYOR** olarak günceller ve **İletime Devam Et** butonu artık görüntülenmez.

![Resume_4](../images/DASH_images/Resume/Resume_4.jpg)

### Pod Alarmlarını Susturma

*NOT - ALARMLARI SUSTUR butonu yalnızca **DASH** sekmesinde pod sona erme veya düşük rezervuar uyarısı tetiklendiğinde kullanılabilir. Alarmları Sustur butonu görünmüyorsa ve poddan bip sesleri duyuyorsanız, 'Pod durumunu yenilemeyi' deneyin.*

Aşağıdaki süreç, aktif 72 saatlik (3 gün) pod süresi sona ermeden önce uyarı süresi sınırına ulaştığında pod bip seslerini nasıl onaylayacağınızı ve kapatacağınızı gösterecektir. Bu uyarı zaman sınırı, Dash uyarıları ayarında **Kapanmadan kaç saat önce?** satırında tanımlanır. Bir pod'un maksimum ömrü 80 saattir (3 gün 8 saat), ancak Insulet 72 saat (3 gün) sınırının aşılmamasını önermektedir.

1. Tanımlanan **Kapanmadan kaç saat önce?** uyarı süresi sınırına ulaşıldığında, pod sona erme zamanına yaklaştığını size bildirmek için uyarı bip sesleri çıkaracak ve yakında pod değişikliği gerekecektir. Bunu **DASH** sekmesinde doğrulayabilirsiniz, **Pod Sona Erme: (1)** satırı tam zamanı gösterecektir. Pod'un süresi dolar (etkinleştirmeden 72 saat sonra) ve bu süre geçerse metin **kırmızı** olacaktır. **Etkin pod alarmları (2)** satırında, **Pod'un süresi yakında dolacak** durum mesajı görüntülenir. Bu aynı zamanda **ALARMLARI SUSTUR (3)** butonunun görüntülenmesini de tetikler.

![ACK_alerts_1](../images/DASH_images/ACK_Alerts/ACK_ALERTS_1.png)

2. **DASH** sekmesine gidin ve **ALARMLARI SUSTUR (2)** butonuna basın. AAPS, pod sona erme uyarı bip seslerini devre dışı bırakmak için pod'a komutu gönderir ve **Pod durumu (1)** satırını **BİLİNEN UYARILAR ** olarak günceller.

![ACK_alerts_2](../images/DASH_images/ACK_Alerts/ACK_ALERTS_2.png)

3. Uyarıların **başarıyla devre dışı bırakılması** üzerine, etkin pod tarafından **2 bip** sesi verilir ve bir onay iletişim kutusunda **Etkin alarmlar susturuldu.** mesajı görüntülenir. İletişim kutusunu onaylamak ve kapatmak için **Tamam** butonunu tıklayın.


![ACK_alerts_3](../images/DASH_images/ACK_Alerts/ACK_ALERTS_3.png)

4. **DASH** sekmesine gidin. **Etkin Pod Alarmları** satırında, uyarı mesajı artık görüntülenmez ve etkin pod artık sona erme uyarısı bip sesi vermez.

### Pod Geçmişini Görüntüle

Bu bölüm, aktif pod geçmişinizi nasıl gözden geçireceğinizi ve farklı eylem kategorilerine göre nasıl filtreleyeceğinizi gösterir. Pod geçmişi aracı, üç günlük (72 - 80 saat) ömrü boyunca şu anda etkin olan pod'unuza yönelik eylemleri ve sonuçları görüntülemenize olanak tanır.

Bu özellik, pod'a gönderilen bolusların, GBO'larin ve bazal komutların doğrulanmasında yardımcı olur. Kalan kategoriler, genel olarak sorunları gidermek ve bir arızaya yol açan olayların sırasını belirlemek için kullanışlıdır.

*NOT:* **Yalnızca son komut belirsiz olabilir**. **son 'belirsiz' komut 'onaylanan' veya 'reddedilen'** olana kadar yeni komutlar *gönderilmeyecektir*. Belirsiz komutları 'düzeltmenin' yolu, **'pod durumunu yenilemek'**tir.

1. **DASH** sekmesine gidin ve **POD YNTM (1)** butonuna basarak **Pod Yönetimi** menüsüne gidin ve ardından pod geçmişi ekranına erişmek için **Pod geçmişi (2)** butonuna basın.

![Pod_history_1](../images/DASH_images/Pod_History/Pod_history_1.jpg) ![Pod_history_2](../images/DASH_images/Pod_History/Pod_history_2.jpg)

2. **Pod geçmişi ** ekranında, **All (1)** (Tümü) varsayılan kategorisi ile tüm pod **Eylemleri (3)** ve **Sonuçları (4)** **Tarih ve Saat (2)** ters kronolojik sırada görüntülenir. Ana AAPS arayüzünde **DASH** sekmesine dönmek için telefonunuzun **geri butonunu 2 kez** kullanın.


![Pod_history_3](../images/DASH_images/Pod_History/Pod_history_3.jpg) ![Pod_history_4](../images/DASH_images/Pod_History/Pod_history_4.jpg)

## DASH Sekmesi

Aşağıda, ana AAPS arayüzündeki **DASH** sekmesindeki simgelerin ve durum satırlarının düzeninin ve anlamının bir açıklaması bulunmaktadır.

*NOT: **DASH** sekmesi durum satırları raporunda herhangi bir mesaj varsa (belirsiz), bunu temizlemek ve pod durumunu yenilemek için Yenile butonuna basmanız gerekir.*

![DASH_Tab_1](../images/DASH_images/DASH_Tab/DASH_Tab_1.png)

### Alanlar

* **Bluetooth Adresi:** Bağlı Pod'un mevcut bluetooth adresini görüntüler.
* **Bluetooth Durumu:** Mevcut bağlantı durumunu görüntüler.
* **Sıra Numarası:** Etkin POD'un sıra numarasını görüntüler.
* **Firmware Versiyonu:** Etkin bağlantının firmware sürümünü görüntüler.
* **Pod üzerindeki zaman:** Bölmedeki geçerli saati görüntüler.
* **Pod Sona Erme:** Pod'un süresinin dolacağı tarih ve saati görüntüler.
* **Pod durumu:** Pod durumunu görüntüler.
* **Son bağlantı:** Pod ile son iletişimin zamanını görüntüler.

   - *Biraz önce* - 20 saniyeden kısa bir süre önce.
   - *Bir dakikadan kısa bir süre önce* - 20 saniyeden uzun, ancak 60 saniyeden kısa bir süre önce.
   - *1 dakika önce* - 60 saniyeden uzun ancak 120 saniyeden kısa (2 dakika)
   - *XX dakika önce* - XX değeriyle tanımlanan 2 dakikadan daha uzun bir süre önce

* **Son bolus:** Etkin pod'dan gönderilen son bolus miktarını ve ne kadar süre önce verildiğini parantez içinde görüntüler.
* **Bazal oranı:** Bazal oran profilinden geçerli zaman için programlanmış bazal oranı görüntüler.
* **Geçici bazal oranı:** Şu anda çalışmakta olan Geçici Bazal Oranı aşağıdaki biçimde görüntüler

   - {Units per hour} @{TBR start time}  ({minutes run}/{total minutes TBR will be run})
   - *Örnek:* 0,00Ü/s @18:25 ( 90/120 dakika)

* **Rezervuar:** Rezervuarda 50 üniteden fazla insülin olduğuda 50+Ü'den fazla kalanı gösterir. 50 Ü'nin altında, tam birimler görüntülenir.
* **Toplam iletilen:** Rezervuardan iletilen toplam insülin ünite miktarını görüntüler. Bu miktar etkinleştirme ve hazırlama için kullanılan insülini de içerir.
* **Hatalar:** Karşılaşılan son hatayı görüntüler. Geçmiş hatalar ve daha ayrıntılı bilgiler için [Pod geçmişini](#view-pod-history) ve günlük dosyalarını inceleyin.
*  **Etkin pod alarmları:** Etkin pod alarmlarını gösteren satırdır.

### Butonlar


![Refresh_Icon](../images/DASH_images/Refresh_LOGO.png) : İletişimi güncellemek için aktif pod'a bir yenileme komutu gönderir.

   * Pod durumunu yenilemek ve metin içeren (belirsiz) durum satırlarını yenilemek için kullanın.
   * Ek bilgi için aşağıdaki Sorun Giderme bölümüne bakın.

![POD_MGMT_Icon](../images/DASH_images/POD_MGMT_LOGO.png) : Pod yönetimi menüsüne gider.

![ack_alert_logo](../images/DASH_images/ack_alert_logo.png) : Pod uyarı biplerini ve bildirimleri devre dışı bırakır (pod süre sonu, düşük rezervuar..).

   * Bu buton, yalnızca pod kullanım süresi (72saat) aşılmışsa görüntülenir.
   * Başarılı bir devre dışı bırakmanın ardından bu simge artık görünmeyecektir.

![RESUME_Icon](../images/DASH_images/DASH_tab_icons/RESUME_Icon.png) : Aktif pod üzerinde askıya alınmış insülin iletimini sürdürür.

### Pod Yönetim Menüsü

Aşağıda, **DASH** sekmesindeki **POD YNTM (0)** butonuna basılarak erişilen **Pod Yönetimi** menüsündeki butonların anlamları verilmiştir. ![DASH_Tab_2](../images/DASH_images/DASH_Tab/DASH_Tab_2.png) ![DASH_Tab_3](../images/DASH_images/DASH_Tab/DASH_Tab_3.png)

* 1 - [**Pod Etkinleştir**](#activate-pod) : Yeni bir pod'u hazırlar ve etkinleştirir.
* 2 - [**Pod'u Devre Dışı Bırak**](#deactivate-pod) : Şu anda etkin olan pod'u devre dışı bırakır.
* 3 - **Test Bip Sesi Çal** : Basıldığında pod'dan test bip sesi çalar.
* 4 - [**Pod geçmişi**](#view-pod-history) : Pod etkinlik geçmişini görüntüler.

## Dash Ayarları

Dash sürücüsü ayarları, sol üst köşedeki **hamburger menüsüne** basılıp **Konfigürasyon ayarları (1)**\ ➜\ **Pompa**\ ➜\ **Dash**\ ➜\ **Dişli Çark (3)**, **Dash** başlıklı **radyo düğmesi (2)** seçerek yapılandırılabilir. **Dişli çark (3)**'ın yanındaki **onay kutusu (4)**'nun seçilmesi, Dash menüsünün AAPS arayüzünde **DASH** başlıklı bir sekme olarak görüntülenmesini sağlar.

![Dash_settings_1](../images/DASH_images/Dash_settings/Dash_settings_1.png) ![Dash_settings_2](../images/DASH_images/Dash_settings/Dash_settings_2.png)

**NOT:** **Dash ayarlarına** daha hızlı erişmenin bir yolu da, <strong x-id="1 **DASH** sekmesinde iken sağ üst köşesindeki **3 noktalı menü (1)** ye basıp açılan menüden **Dash tercihler'ini (2)** seçmektir.

![Dash_settings_3](../images/DASH_images/Dash_settings/Dash_settings_3.png)

Ayar grupları aşağıda listelenmiştir; aşağıda açıklanan çoğu ayarı bir geçiş anahtarı aracılığıyla etkinleştirebilir veya devre dışı bırakabilirsiniz:

![Dash_settings_4](../images/DASH_images/Dash_settings/Dash_settings_4.jpg)

*NOT: Yıldız işareti (\*), varsayılan ayarın etkin olduğunu gösterir.*

### Onay Bildirimleri

Bolus, bazal, SMB ve GBO iletimi ve değişiklikleri için pod üzerinden onay bip sesleri sağlar.

* **Bolus bip seslerini etkinleştir:** Bolus iletildiğinde onay biplerini etkinleştirin veya devre dışı bırakın.
* **Bazal bip seslerini etkinleştir:** Yeni bir bazal oran ayarlandığında, aktif bazal oran iptal edildiğinde veya mevcut bazal oran değiştirildiğinde onay biplerini etkinleştirin veya devre dışı bırakın.
* **SMB bip seslerini etkinleştir:** Bir SMB teslim edildiğinde onay biplerini etkinleştirin veya devre dışı bırakın.
* **GBO (TBR) bip seslerini etkinleştir:** Bir GBO ayarlandığında veya iptal edildiğinde onay biplerini etkinleştirin veya devre dışı bırakın.

### Alarmlar

Tanımlanan eşik değerlerine dayalı olarak pod sona erme, kapatma, düşük rezervuar için AAPS alarm verir.

*Herhangi bir alarm tetiklendikten sonra pod ile her iletişimde tetiklenen alarm için bir AAPS bildiriminin alınacağını unutmayın. Gelen uyarıyı kapatmak, "Pod uyarılarını otomatik olarak sustur" etkin değilse, bildirimin tekrar gelmesini ENGELLEMEZ. Uyarıyı MANUEL OLARAK kapatmak için **DASH** sekmesini ziyaret etmeli ve **ALARMLARI SUSTUR** butonuna basmalısınız.*

* **Süre sonu hatırlatıcısını etkinleştir:** Kapanmadan önce tanımlanan saat süresine ulaşıldığında tetiklenecek şekilde pod sona erme hatırlatıcısını etkinleştirin veya devre dışı bırakın.
* **Kapanmadan kaç saat önce:** Etkin pod kapanmadan önceki saat süresini tanımlar, bu daha sonra pod süre sonu hatırlatıcısı alarmını tetikler.
* **Düşük rezervuar uyarısını etkinleştir:** Pod, ünite satırında belirlenen alt rezervuar sınırına ulaştığında bir alarm etkinleştirin veya devre dışı bırakın.
* **Ünite:** Pod düşük rezervuar alarmının tetikleneceği ünite sayısı.

### Bildirimler

GBO, SMB, bolus veya teslimatı askıya alınan başarılı olayları için AAPS bildirimleri ve sesli telefon uyarıları sağlar.

*NOT: Bunlar yalnızca bildirimlerdir, sesli uyarı yapılmaz.*

* **Belirsiz GBO (TBR) bildirimleri için sesi etkinleştir:** Bir Geçici Bazal Oranının başarılı bir şekilde ayarlanıp ayarlanmadığı AAPS tarafından belirsiz olduğunda sesli bir uyarı ve görsel bildirim tetiklemek için bu ayarı etkinleştirin veya devre dışı bırakın.
* **Belirsiz SMB bildirimleri için sesi etkinleştir:** Bir SMB'nin başarıyla teslim edilip edilmediğinden AAPS emin olmadığında sesli bir uyarı ve görsel bildirimi tetiklemek için bu ayarı etkinleştirin veya devre dışı bırakın.
* **Belirsiz bolus bildirimleri için sesi etkinleştir:** AAPS'nin bir bolusun başarıyla iletildiğinden emin olmadığı durumlarda sesli uyarı ve görsel bildirimi tetiklemek için bu ayarı etkinleştirin veya devre dışı bırakın.
* **İletimin askıya alındığı bildirimi etkinleştirildiğinde sesle uyar:** İletimi askıya alma başarıyla tamamlandığında sesli bir uyarı ve görsel bildirimi tetiklemek için bu ayarı etkinleştirin veya devre dışı bırakın.

## Eylemler (EYLEM) Sekmesi

Bu sekme, ana AAPS dokümantasyonunda detaylı bir şekilde anlatılmıştır. Ancak bu sekmede, özellikle yeni bir pod uygulandıktan sonra, Omnipod Dash podunun hortum tabanlı pompalardan farklılıklarına dair birkaç detay verilecektir.

1. Ana AAPS arayüzünde **Eylemler (EYLEM)** sekmesine gidin.

2. **Bakımportalı (1)** bölümünün altında **İnsülin** ve **Kanül** alanları her pod değişikliğinden sonra **yaşlarını 0 gün ve 0 saat ** olacak şekilde sıfırlayacaktır. Bu Omnipod pompasının çalışma şekli nedeniyle böyle yapılmaktadır. Pod, kanülü doğrudan pod uygulama bölgesinde deriye yerleştirdiği için, Omnipod pompalarında hortum kullanılmaz. *Bu nedenle, bir pod değişikliğinden sonra bu değerlerin her birinin yaşı otomatik olarak sıfırlanır.* **Pompa pil yaşı** pod pili her zaman kendi ömründen daha fazla olacağı için (maksimum 80 saat) rapor edilmez. **Pompa pili** ve **insülin rezervuarı**, her pod içinde yer almaktadır.

![ACT_1](../images/DASH_images/Actions_Tab/ACT_1.png)

### Seviye

**İnsülin Seviyesi**

Görüntülenen insülin seviyesi, Omnipod DASH tarafından bildirilen miktardır. Bununla birlikte, pod sayısal insülin rezervuar seviyesini yalnızca 50 ünitenin altında olduğunda bildirir. O zamana kadar “50 ünitenin üzerinde” şeklinde görüntülenecektir. Bildirilen miktar kesin değildir: pod çoğu durumda "boş" olduğunu bildirdiğinde bile rezervuarda hala biraz ek insülin kalacaktır. Omnipod DASH sekmesi, aşağıda açıklandığı gibi görüntülenecektir:

  * **50 Ünitenin Üzerinde** - Pod, şu anda rezervuarda 50 üniteden fazla insülin olduğunu rapor ediyor.
  * **50 Ünitenin Altında** - Pod tarafından bildirilen rezervuarda kalan insülin miktarı.

Ek not:
  * **SMS** - SMS yanıtlarında insülin seviyesi 50+Ü veya değer görünür.
  * **Nightscout** - Nightscout'a (sürüm 14.07 ve daha eski) 50 üniteden fazla olduğunda 50 değerini yükler.  Daha yeni sürümler, 50 ünite üzerinde olduğunda 50+ değerini bildirir.

## Sorun giderme

### İletimi askıya alma

  * Artık iletimi askıya alma butonu yok. Pod insülin iletimini "askıya almak" istiyorsanız, x dakika için sıfır GBO ayarlayabilirsiniz.
  * Profil geçişleri sırasında, dash pompa yeni bazal profili ayarlamadan önce iletimi askıya almalıdır. İki komut arasında iletişim başarısız olursa, iletim askıya alınabilir. Bu olduğunda:
     - Bazal, SMB, Manuel bolus vb. içeren insülin iletimi olmayacaktır.
     - Komutlardan birinin onaylanmadığına dair bir bildirim olabilir: bu, hatanın ne zaman gerçekleştiğine bağlıdır.
     - AAPS, her 15 dakikada bir yeni bazal profili ayarlamaya çalışacaktır.
     - APPS, iletim hala askıya alınmışsa iletimin her 15 dakikada bir askıya alındığını bildiren bir bildirim gösterecektir. (iletim devam ettirilemedi)
     - [**İletime devam et**](#resuming-insulin-delivery) butonu etkin olacak ve kullanıcı iletimi manuel olarak sürdürmeyi seçebilecektir.
     - AAPS kendi kendine iletimi sürdüremezse (bu, Pod'a ulaşılamıyorsa, ses kapatılmışsa vb. olabilir), pod 3 dakika için her dakikada bir 4 kez bip sesi çıkarmaya başlar, ardından iletim 20 dakikadan daha uzun süre askıda kalırsa bu her 15 dakikada bir tekrarlanır.
  * Onaylanmamış komutlar için "pod durumunu yenile" komutu, bunları onaylamalı/reddetmelidir.

**Not:** Pod bip seslerini duyduğunuzda, telefonu kontrol etmeden iletimin devam ettiğini varsaymayın, iletim askıya alınmış olabilir, **bu yüzden kontrol etmeniz gerekiyor!**

### Pod Hataları

Pod'larda, kendisiyle ilgili donanım sorunları da dahil olmak üzere çeşitli sorunlar nedeniyle ara sıra hatalar olabiliyor. AAPS onaylanmış bir kullanım şekli olmadığından, bunları Insulet'e bildirmemek en iyi seçenektir. Nedenini belirlemeye yardımcı olacak hata kodlarının bir listesi [**burada bulunabilir.**](https://github.com/openaps/openomni/wiki/Fault-event-codes)

### 49 numaralı Pod hatasını önleme

Bu hata bir komut için yanlış bir pod durumu veya bir insülin iletim komutu sırasındaki bir hata ile ilgilidir. Bu, sürücü ve Pod'un gerçek durum üzerinde anlaşamadığı zaman meydana gelir. Pod (yerleşik bir güvenlik önlemi dışında), daha sonra kurtarılamaz bir 49 (0x31) hata koduyla tepki verir ve sonunda "çığlık atan" olarak bilinen bir hatayla sonuçlanır: yalnızca pod'un arkasındaki uygun yerde bir delik açılarak durdurulabilen uzun rahatsız edici bir bip sesi. "49 pod arızasının" kesin kök nedenini izlemek çoğu zaman zordur. Bu hatanın meydana gelmesinde şüphelenilen durumlar, örneğin uygulama çökmeleri, bir geliştirme sürümünün çalıştırılması veya yeniden kurulumdur.

### Pompaya Ulaşılamıyor Uyarıları

Önceden yapılandırılmış bir süre boyunca pod ile iletişim kurulamadığında, "Pompaya ulaşılamıyor" uyarısı verilir. Pompaya erişilemiyor uyarıları, sağ üst taraftaki üç noktalı menüye gidip **Tercihler**\ ➜\ **Yerel uyarılar**\ ➜\ **Pompa ulaşılamaz eşiği [dk]** öğesi seçilerek yapılandırılabilir. Önerilen değer, **120** dakika sonra uyarı vermesidir.

### Ayarları Dışa Aktarma

AndroidAPS ayarlarını dışa aktarmak, tüm ayarlarınızı ve belki daha da önemlisi tüm gerçekleştirdiğiniz görevleri geri yükleyebilmenizi sağlar. AndroidAPS'i kaldırıp/yeniden yükledikten sonra veya telefonun kaybolması durumunda yeni telefona yeniden yüklemeniz durumunda ayarları "bilinen son çalışma durumuna" geri yüklemeniz gerekebilir.

Not: Aktif pod bilgileri, dışa aktarılan ayarlara dahildir. Dışa aktarılan "eski" bir dosyayı içe aktarırsanız, aktif podunuz "kullanım dışı olacaktır". Bu durumda mevcut podu değiştirmekten başka bir alternatif yoktur. Bazı durumlarda (_programlı_ bir telefon değişikliği gibi), ** bir pod kullanırken ** AndroisAPS ayarlarını geri yüklemek için dışa aktarılan dosyayı kullanmanız gerekebilir. Bu durumda, yalnızca o anda aktif olan podu içeren, yakın zamanda dışa aktarılmış ayarlar dosyasının kullanılması önemlidir.

**Bu sebeple bir pod etkinleştirdikten hemen sonra ayarları dışa aktarmak akıllıcadır**. Bu şekilde, bir sorun olması durumunda (Örneğin, başka bir yedek telefona geçerken) her zaman aktif pod'u geri yükleyebileceksiniz.

Dışa aktarılan ayarlarınızı, gerektiğinde herhangi bir telefon tarafından erişilebilen güvenli bir yere (bulut sürücüsü) düzenli olarak kopyalayın (örneğin, telefonun kaybolması veya fabrika ayarlarına sıfırlanması durumunda).

### Ayarları İçe Aktarma

**UYARI** Ayarları içe aktarmanın eski bir Pod durumunu içe aktarabileceğini lütfen unutmayın. Sonuç olarak, aktif Pod'u kaybetme riski vardır! (bkz. **Ayarları Dışa Aktarma**). Aktif pod kullanırken, başka seçeneğiniz kalmazsa denenebilir.

Ayarları etkin bir pod ile içe aktarırken, dışa aktarılan ayarların o anda etkin olan pod ile yapıldığından emin olun.

**Etkin bir pod kullanırken içe aktarma:** (Pod'u kaybetme riskiniz vardır!)

1. Şu anda etkin olan Pod ile yakın zamanda dışa aktarılan ayarları içe aktardığınızdan emin olun.
2. Ayarlarınızı içe aktarın
3. Tüm tercihleri kontrol edin

**İçe aktarma (etkin Pod kullanımı yok)**

1. Yakın zamanda dışa aktarılan bir dosyanın içe aktarılması işe yarayacaktır (yukarıya bakın)
2. Ayarlarınızı içe aktarın.
3. Tüm tercihleri kontrol edin.
4. İçe aktarma ayarları herhangi bir etkin pod verisi içeriyorsa, "mevcut olmayan" pod'u **devre dışı bırakmanız** gerekebilir.

### Etkin olmayan bir pod durumunu içeren ayarları içe aktarma

Aktif olmayan bir pod verileri içeren ayarları içe aktarırken, AndroidAPS onunla bağlanmaya çalışacak ve başarısız olacaktır. Bu durumda yeni bir Pod etkinleştiremezsiniz.

Eski Pod oturumunu kaldırmak için Pod'u devre dışı bırakmayı “deneyin”. Devre dışı bırakma başarısız olur. “Yeniden Dene”yi seçin. İkinci veya üçüncü denemeden sonra pod'u kaldırma seçeneğine sahip olacaksınız. Eski pod kaldırıldıktan sonra yeni bir pod etkinleştirebilirsiniz.

### AndroidAPS'i yeniden yükleme

AndroidAPS'i kaldırdığınızda tüm ayarlarınızı, hedeflerinizi ve mevcut Pod oturumunu kaybedersiniz. Bunları geri yüklemek için, yakın zamanda dışa aktarılmış bir ayar dosyanız olduğundan emin olun!

Etkin bir pod kullanırken, mevcut pod oturumu için bir dışa aktarılan dosyanız olduğundan emin olun, aksi takdirde eski ayarları içe aktarırken o anda etkin olan pod'u kaybedersiniz.

1. Ayarlarınızı dışa aktarın ve bir kopyasını güvenli bir yerde saklayın.
2. AndroidAPS'i kaldırın ve telefonunuzu yeniden başlatın.
3. AndroidAPS'in yeni sürümünü yükleyin.
4. Ayarlarınızı içe aktarın
5. Tüm tercihleri doğrulayın (isteğe bağlı olarak ayarları tekrar içe aktarın)
6. Yeni bir pod etkinleştirin
7. Tamamlandığında, mevcut ayarları dışa aktarın

### AndroidAPS'i daha yeni bir sürüme güncelleme

Çoğu durumda, mevcut kurulumu kaldırmaya gerek yoktur. Yeni sürüm için kurulumu başlatarak “üzerine” kurulum yapabilirsiniz. Bu aktif bir Pod kullanırken de mümkündür.

1. Ayarlarınızı dışa aktarın.
2. Yeni AndroidAPS sürümünü yükleyin.
3. Kurulumun başarılı olduğunu doğrulayın
4. Mevcut pod'a DEVAM EDİN veya yeni bir pod etkinleştirin.
5. Tamamlandığında, mevcut ayarları dışa aktarın.

### Omnipod sürücü uyarıları

Omnipod Dash sürücüsü **Giriş sekmesinde** çeşitli uyarılar sunmakla birlikte bunların çoğu bilgi amaçlıdır ve kapatılabilirken, bazıları da kullanıcıya tetiklenen uyarının nedenini çözmek için bir eylemde bulunmasını sağlar. Karşılaşabileceğiniz başlıca uyarıların bir özeti aşağıda listelenmiştir:

* Etkin pod yok Etkin Pod oturumu algılanmadı. (pod not activated) Bu uyarı, **ERTELE**'ye basılarak geçici olarak kapatılabilir, ancak yeni bir pod etkinleştirilmedikçe tetiklenmeye devam edecektir. Pod etkinleştirildiğinde bu uyarı otomatik olarak kapatılır.
* Pod askıya alındı Pod'un askıya alındığına dair bilgi uyarısı.
* Bazal profil ayarlanamadı : İletim askıya alınabilir! Lütfen Omnipod sekmesindeki Pod durumunu manuel olarak güncelleyin ve gerekirse teslimi devam ettirin.. Pod bazal profili ayarının başarısız olduğuna ve Dash sekmesinde *Yenile*'ye basmanız gerektiğine dair bilgi uyarısı.
* SMB bolusunun başarılı olup olmadığı doğrulanamıyor. Bolus'un başarılı olmadığından eminseniz, SMB girişini Tedaviler'den manuel olarak kaldırmalısınız. SMB bolus komutunun başarısının doğrulanamadığına dair uyarı, SMB bolusunun başarılı olup olmadığını görmek için DASH sekmesindeki *Son bolus* alanını doğrulamanız ve iletilmedi ise tedaviler sekmesinden girişi kaldırmanız gerekir.
* "Görev bolus/GBO/SMB"nin tamamlanıp tamamlanmadığı belirsizse, lütfen başarılı olup olmadığını manuel olarak doğrulayın.

## Omnipod DASH sürücüsü için nereden yardım alınabilir?

Omnipod DASH sürücüsü için tüm geliştirme çalışmaları topluluk tarafından **gönüllü** temelinde yapılır; Yardım talep etmeden önce bu gerçeği hatırlamanızı ve aşağıdaki yönergeleri kullanmanızı rica ediyoruz:

-  **Seviye 0:** Sorun yaşadığınız işlevin nasıl çalışması gerektiğini anladığınızdan emin olmak için bu dokümantasyonun ilgili bölümünü okuyun.
-  **Seviye 1:** Bu dokümantasyonu kullanmanıza rağmen hâlâ çözemediğiniz sorunlarla karşılaşıyorsanız, lütfen [bu davet bağlantısını](https://discord.gg/4fQUWHZ4Mw) kullanarak **Discord**'da * #androidaps* kanalına gidin.
-  **Seviye 2:** Sorununuzun daha önce [ sorunlar adresinde ](https://github.com/nightscout/AndroidAPS/issues)bildirilmiş olup olmadığını görmek için mevcut sorunları arayın. Sorunuz burada mevcutsa, lütfen onaylayın/yorum yapın/ekleyin. Yoksa, lütfen bir [yeni sorun](https://github.com/nightscout/AndroidAPS/issues) oluşturun ve [günlük dosyalarınızı ekleyin](../Usage/Accessing-logfiles.md).
-  **Sabırlı olun - topluluğumuzun üyelerinin çoğu iyi huylu gönüllülerden oluşur ve sorunları çözmek genellikle hem kullanıcılar hem de geliştiriciler için zaman ve sabır gerektirir.**
