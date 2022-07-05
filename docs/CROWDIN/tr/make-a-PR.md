# Dokümanlar nasıl düzenlenir

**Bu açıklama yalnızca İngilizce belgeleri düzenlemek içindir. Tüm yeni bilgiler önce İngilizce olarak eklenmelidir. Diğer dillere çeviri yapmak istiyorsanız (teşekkür ederim), lütfen [crowdin](https://crowdin.com/project/androidapsdocs) kullanın.**

Metnin nasıl biçimlendirileceğine (başlık, kalın...) ve bağlantıların ayarlanmasına ilişkin ipuçları için lütfen bu sayfanın ["code syntax"](./make-a-PR#code-syntax) bölümüne bakın.

## Genel

Herhangi bir sorunuz, geri bildiriminiz veya yeni fikirleriniz için [discord](https://discord.gg/4fQUWHZ4Mw) aracılığıyla dokümantasyon ekibiyle iletişime geçebilirsiniz. Çekme isteği yapmak zor değil, belgeleri düzenlemenize yardımcı olabiliriz.

Bir noktada bir çekme isteği (PR) yapmanız önerilecektir. PR, çekme isteğinin kısaltmasıdır ve GitHub'da depolanan bilgileri eklemenin veya düzenlemenin bir yoludur. Aslında bir tane yapmak çok zor değil ve katkıda bulunmak için harika bir yol. Bu dokümantasyonlar, sizin gibi insanlar PR'lar yaptığı için burada. Bir hata yapmaktan veya bir şekilde yanlış dokümantasyonu düzenlemekten endişe etmeyin. Değişiklikler "resmi" AndroidAPS belge deposunda birleştirilmeden önce her zaman bir inceleme süreci vardır. PR sürecindeki herhangi bir kazayla orijinalleri bozamazsınız. Genel PR prosesi:

* Mevcut içeriği düzenleyerek kod veya dokümanlarda düzenlemeler ve iyileştirmeler yapın.
* Düzenlemelerinizin iyi görünüp görünmediğini bir kez daha kontrol edin.
* İnsanların düzenlemeleri anlayabilmesi için nelerin değiştiğine dair birkaç not alın.
* Yöneticilerden değişikliklerinizi kullanmalarını isteyen bir çekme isteği oluşturun.
* Bir inceleme yapacaklar ve (1) değişikliklerinizi birleştirecekler, (2) değişiklikleriniz hakkında size geri dönüş yapacaklar veya (3) değişikliklerinizle yeni bir doküman başlatacaklar.

(Yan not: Görsel öğrenen biriyseniz, [burada](https://youtu.be/4b6tsL0_kzg) PR iş akışını gösteren bir YouTube videosu mevcuttur.)

Örneğimizde AndroidAPSdocs'ta bir düzenleme yapacağız. Bunun sadece bilgisayarınızdaki linux ortamında yapılması GEREKMEZ. Bu, herhangi bir Windows PC, Mac, vb. üzerinde yapılabilir. (İnternet erişimi olan herhangi bir bilgisayar).

1. https://github.com/openaps/AndroidAPSdocs adresine gidin ve havuzun kendi kopyasını oluşturmak için sağ üstteki Fork'a basın.

![çatal deposu](./images/PR0.png)

2. Herhangi bir sayfaya giderek ve düzenlemek istediğiniz dokümana ulaşın. Sayfanın sol alt kısmında yeşil "v: en son" veya benzeri bir kelime bulunan kara kutuya tıklayın. Görünen açılır pencerede GitHub'da düzenlemek için "düzenle" kelimesini tıklayın. 

![dokümanı düzenle](./images/PR1.png)

     Veya sağ üst köşedeki "GitHub'da Düzenle" bağlantısına tıklayabilir ve ardından düzenlenecek sayfa içeriğinin üst çubuğunda görünen kalem simgesine tıklayabilirsiniz.
    

![RTD io](./images/PR2.png)

3. Adım 2'deki seçeneklerden biri veya diğeri, düzenlemelerinizin kaydedileceği deponuzda yeni bir dal oluşturacaktır. Bu dosyada düzenlemelerinizi yapabilirsiniz.
  
  Farklı dosya uzantıları kullandığımızı unutmayın: .rst (ReStructuredText) ve .md (Markdown) ve sözdizimi ikisi arasında biraz farklılık gösterir. [Aşağıda açıklanan](./make-a-PR#code-syntax) doğru sözdizimini kullanmaya dikkat edin.

![Şubeyi düzenle](./images/PR3.png)

4. "<>Dosyayı düzenle" sekmesinde çalışıyorsunuz. Değiştirdiğiniz her şeyin istediğiniz gibi göründüğünden emin olmak için yeni bir görünüm için "Preview changes" "Değişiklikleri önizle" sekmesini seçin (yazım hataları vs.). Gerekli bir iyileştirme görürseniz, daha fazla iyileştirme yapmak için düzenleme sekmesine geri dönün. 

![önizleme modu](./images/PR5.png)

5. Düzenlemelerinizi bitirdiğinizde, sayfanın en altına gidin. Alttaki kutuda, "İsteğe bağlı bir genişletilmiş açıklama ekleyin..." yazan metin alanına yorumlarınızı girin. Varsayılan başlık dosya adıdır. Değişikliğin **nedenini** açıklayan bir cümle eklemeye çalışın. Nedeni ilişkilendirmek, gözden geçirenlerin PR ile ne yapmaya çalıştığınızı anlamasına yardımcı olur.

![yorum yap](./images/PR4.png)

6. Yeşil "Dosya değişiklikleri öner" veya "Değişiklikleri kabul et" düğmesini tıklayın. Açılan sayfada "Create Pull Request" "Çekme Talebi Oluştur" u tıklayın ve sonraki sayfada tekrar "Çekme Talebi Oluştur" u tıklayın.

![çekme isteği oluşturun](./images/PR6.png)

7. Bu, bir çekme isteğinin (PR) açılmasını tamamlar. GitHub, PR'ye başlıktan sonra bulunan bir sayı ve bir kare işaret atar. Geri bildirimi kontrol etmek için bu sayfaya dönün (veya size e-postayla GitHub bildirimleri gönderildiyse, PR ile ilgili herhangi bir etkinlik hakkında bilgilendiren e-postalar alacaksınız). Düzenleme şimdi, ekibin AndroidAPS için ana belgelere geçmeden önce gözden geçireceği ve potansiyel olarak geri bildirimde bulunacağı bir PR listesinde olacak! PR'nin ilerlemesini kontrol etmek isterseniz, GitHub hesabınızın sağ üst köşesindeki zil logosuna tıklayıp tüm PR'lerinizi görebilirsiniz.

![PR takibi](./images/PR7.png)

Not: Çatalınız (fork) ve şubeniz (branch) hala kendi kişisel GitHub hesabınızda kalıyor olacak. PR'nizin birleştiğine dair bir bildirim aldıktan sonra, işiniz bittiyse şubenizi silebilirsiniz (Adım 8'in bildirim alanı, kapatıldığında veya birleştiğinde şubeyi silmek için bir bağlantı sağlayacaktır). Gelecekteki düzenlemeler için, bu prosedürü izlerseniz, düzenlemeler her zaman AndroidAPSdocs depolarının güncellenmiş bir sürümüyle başlayacaktır. Bir PR isteği başlatmak için başka bir yöntem kullanmayı seçerseniz (örneğin, başlangıç noktası olarak çatallı deponuzun ana dalından başlayarak düzenleme), önce bir "karşılaştırma" gerçekleştirerek ve çatalınızı en son güncellemenizden bu yana gerçekleşen tüm güncellemeleri birleştirerek deponuzun güncel olduğundan emin olmanız gerekir. İnsanlar depolarını güncellemeyi unutmaya meyilli olduğundan, "karşılaştırma" yapmaya alışana kadar yukarıda özetlenen PR sürecini kullanmanızı öneririz.

## Sözdizimi kodları

Şu anda doküman sayfaları için kullanılan iki dil vardır:

* Markdown (.md) - orijinal olarak doküman sayfaları için kullanılan biçimlendirme dili
* reStructuredText (.rst) - yeni biçimlendirme dili

Orta vadede tüm doküman sayfalarını reStructuredText'ten Markdown formatına parça parça değiştireceğiz. Bu arada, metni biçimlendirirken veya bağlantı kurarken doğru sözdizimini kullanmanız önemlidir. Emin değilseniz, mevcut sayfalardaki biçim/bağlantı kodlarına bir göz atın.

### Görüntü boyutu

Görüntüler kullanıyorsanız lütfen makul boyutları kullanın. Ekran görüntüleri **250 piksel genişliğinde** olmalıdır.

### .md dosyaları

#### Metin Formatı

* kalın: `**metin**`
* italik: `*metin*`
* Başlık 1: `# başlık`
* Başlık 2: `## başlık`
* Başlık 3: `### başlık`

#### Görseller

* images: `![alt text](../images/file.png)`

#### Bağlantılar

* harici bağlantı: `[alt metin](www.url.tld)`
* .md sayfasına dahili bağlantı: `[alt metin](../folder/file.md)`
* .rst sayfasına dahili bağlantı: `[alt metin](../folder/file.rst)`
* başlığa dahili bağlantı: `[alt metin](../folder/file#headline)`

### .rst dosyaları

#### Metin Formatı

* kalın: `**metin**`
* italik: `*metin*`
* Başlık 1:
  
  `başlık`  
  `*****`

* Başlık 2:
  
  `başlık`  
  `=====`

* Başlık 3:
  
  `başlık`  
  `-----`

#### Görseller

* görüntüler:
  
  `.. image:: ../images/modules.png`  
  `:alt: alt text`

#### Bağlantılar

* harici bağlantı: `` `alt metin <www.url.tld>_` ``
* .md sayfasına dahili bağlantı: `` `alt metin <../folder/file.html>_` ``
* .rst sayfasına dahili bağlantı: `` `alt metin <../folder/file.html>_` ``
* başlığa dahili bağlantı: `` `alt metin <../folder/file.html#headline>_` ``

### Dahili bağlantılar

AndroidAPS dokümantasyonunda dahili bir bağlantı ayarlamak istiyorsanız, lütfen yalnızca **göreceli bağlantıları** kullanın. Yalnızca bu yöntem, bağlantının diğer dillerde de (Çekçe, Almanca...) çalışmasını sağlar.

#### **.md** ile biten dosyalarda:

* `[text](../Usage/Test.md)`, bulunduğunuz bir dizinden /Usage alt dizinine dahili bir köprü oluşturacaktır. Hedef dosyanın sonu .md veya .rst olmalıdır (.html değil)
* `[text](./Usage/Test.md)` bulunduğunuz yerden /Usage alt dizinine dahili bir köprü kurar. Hedef dosyanın sonu .md veya .rst olmalıdır (.html değil)
* Bağlantıyı bir **çapaya** (yani bir başlığa) ayarlamak için dosya uzantısını atlamanız gerekir. 
  * `[text](../Usage/Test.md#anchor)` yerine `[text](../Usage/Test#anchor)` kullanılmalı

#### **.rst** ile biten dosyalarda:

* `` `Text <../Usage/Test.hmtl>`_ ``, bulunduğunuz dizinden /Usage alt dizinine bir köprü kurar. Hedef dosyanın sonu .html olmalıdır.
  
  Bir toctree'de olman dışında. O zaman bunu şu şekilde yazmanız gerekir: `Text <../Usage/Test.md>` .md veya .rst ile (.html değil)

* `Text <./Usage/Test.md>` bulunduğunuz yerden /Usage dizinine bir köprü kurar.

* Bağlantıyı bir **çapaya** (yani bir başlığa) ayarlamak için bağlantıya çapa eklemeniz gerekir. 
  * `[text](../Usage/Test#anchor)` yerine `[text](../Usage/Test.html#anchor)`

## Belgelere birden çok görüntü ekleme

Dokümanların bazı bölümlerine görsel olarak yardımcı olacak görüntü ve fotoğraf eklemek de dahil çok sayıda düzenleme yapmayı planlıyorsanız (teşekkürler!), aşağıdaki yaklaşımı kullanmak isteyebilirsiniz:

* Ekran görüntülerini kaydederken ekran görüntülerini açıklayıcı bir adla yeniden adlandırın - ancak GitHub'ın kafasını karıştıracağı için boşluk kullanmamaya çalışın. Bunun yerine alt çizgi kullanın. "Örnek toplu görüntüler upload.png" yerine Örnek_toplu_görüntüler_upload.png. 
* Lütfen makul ölçüler kullanın. Ekran görüntüleri **250 piksel genişliğinde** olmalıdır.
* Görüntüleri toplu şekilde aşağıdakileri adımları uygulayıp kolayca yükleyebilirsiniz:
  
  1. Görüntüler klasörüne gidin (https://github.com/openaps/AndroidAPSdocs/tree/master/docs/EN/images - ancak bunu yapabilmek için dokümanlar Görüntüler klasörünün çatalında/kopyasında olduğunuzdan emin olun ( URL'deki "openaps" ifadesini GitHub kullanıcı adınızla değiştirin)).
  
  2. Sağ üst köşede "Dosya yükle" yazan yere tıklayın
  
  3. Resimlerinizi ekrana sürükleyip bırakın
  
  4. Bunları şubenize teslim edin
  
  5. Artık her dosyanın URL'sini/göreceli yolunu arayabilir ve bunu belgelerdeki bir sayfaya resim eklerken başvurmak için kullanabilirsiniz.
  
  6. Görsellerin nasıl ekleneceğine dair örnekleri görmek, görsellerin zaten başarıyla gömülü olduğu sayfadan bir örnek görmek için bir sayfanın "ham" koduna bakabilirsiniz. Bulunduğunuz sayfa türü (.md veya .rst) için [doğru kodu](./make-a-PR#code-syntax) kullandığınızdan emin olun. Ana amaç, düz bir metin açıklamasına sahip olmak ve ardından aşağıdaki gibi görüntüye göreli bir yol içeren bir bağlantıya sahip olmaktır:
    
    * .md sayfaları için: `![Görüntüleri toplu halde yükleme örneği](../images/Example_batch_images_upload.png)`
    * .rst sayfaları için: `.. image:: ../images/Example_batch_images_upload.png`  
      `:alt: Görüntüleri toplu halde yükleme örneği`

![Toplu halde resim yükleme örneği](./images/Example_batch_images_upload.png)

7. Resim ekledikten veya ayarlamalar yaptıktan sonra, AndroidAPSdocs'un ana dalına bir PR gönderebilirsiniz.