# Çöp Sınıflandırma Projesi (Garbage Classification Project)
# Proje Özeti
- Çevre bilincinin artması ve sürdürülebilirlik anlayışının yaygınlaşmasıyla birlikte, geri dönüşüm süreçlerinin verimli şekilde yürütülmesi her geçen gün daha kritik hale gelmektedir. Atıkların doğru sınıflandırılması, hem doğal kaynakların korunması hem de çevresel zararların azaltılması açısından temel bir gerekliliktir.

- Çalışmamızda makine öğrenmesi / derin öğrenme teknikleri kullanılarak atık türlerinin otomatik olarak ayrıştırılması hedeflenmiştir.

- Bu doğrultuda çalışmamızda, çöp atıklarının altı kategoriye (metal, cam, organik, kâğıt, pil ve plastik) ayrılması için derin öğrenme tabanlı bir görüntü sınıflandırma modeli geliştirilmiştir. Model, görüntülerden öğrenme yoluyla atıkların doğru kategorilere atanmasını hedeflemektedir.

- Projede kullanılan veri kümesi, Kaggle platformunda yayınlanan “Garbage Classification” ( /kaggle/input/garbage-classification-6-classes-775class ) adlı veri setidir.

- Bu veri setinde toplam 4650 adet görüntü bulunmaktadır. Veri seti, sınıflandırma açısından dengeli bir dağılım göstermekte olup, modelin eğitim ve test süreçlerinde uygun bir temel sunmaktadır.

# Yöntemler
Bu projede, atık görüntülerini sınıflandırmak için Convolutional Neural Network (CNN) tabanlı bir derin öğrenme modeli geliştirilmiştir. Amaç, görsel verilerden organik ve geri dönüştürülebilir atıkları doğru şekilde ayırt etmektir. İzlenen adımlar:

1. Veri Ön İşleme (Data Preprocessing):
- Görsellerin yeniden boyutlandırılması (image resizing)

- Piksel değerlerinin 0–1 aralığına normalize edilmesi

- Veri artırma (Data Augmentation) işlemleri uygulanmıştır:

Döndürme (rotation),

Yatay çevirme (horizontal flip),

Yakınlaştırma (zoom),

Kaydırma (shift).

2. Model Mimarisi (Model Architecture): 
   
CNN modeli sırasıyla Conv2D → MaxPooling2D → Dropout → Flatten → Dense katmanlarından oluşturulmuştur.

Aktivasyon fonksiyonu olarak ReLU, çıktı katmanında Softmax kullanılmıştır.

Adam optimizer ve categorical_crossentropy loss fonksiyonu tercih edilmiştir.

Model 15 epoch boyunca eğitilmiştir.

3. Hiperparametre Denemeleri:
   
Dropout oranı: 0.3’ten 0.5’e çıkarılarak overfitting azaltılmaya çalışılmıştır.

Batch size: 16, 32, 64 değerleriyle farklı denemeler yapılmıştır.

Test Time Augmentation (TTA): Test sürecinde veri çeşitliliğini artırmak amacıyla uygulanmıştır.

4. Model Değerlendirme:

Eğitim ve doğrulama setleri ayrılarak modelin genelleme başarımı analiz edilmiştir.

Eğitim sürecindeki doğruluk (accuracy) ve kayıp (loss) değerleri grafiklerle takip edilmiştir.

Metrikler
- Modelin performansını değerlendirmek için temel metrikler olarak doğruluk (accuracy) ve kayıp (loss) değerleri kullanılmıştır. Eğitim sürecinde ayrıca doğrulama (validation) seti üzerinde de takip yapılmıştır. Model 15 epoch boyunca eğitilmiştir.

- Eğitim doğruluğu %72.9, doğrulama doğruluğu %71.9 seviyesinde elde edilmiştir. Eğitim ve doğrulama doğruluklarının birbirine yakın olması, modelin veriyi ezberlemek yerine genelleme yapabildiğini göstermektedir. Ancak doğruluk oranlarının daha yüksek olabilmesi için epoch sayısı artırılabilir veya farklı mimariler denenebilir.

- Elde edilen sonuçlara göre model, eğitim verisi üzerinde yüksek doğruluk elde etmiştir. Doğrulama ve test setlerindeki doğruluk değerleri de eğitim doğruluğu ile uyumlu olduğundan, modelin genelleme yeteneğinin başarılı olduğu söylenebilir.

- Ancak bazı sınıflarda (örneğin plastik ve kağıt) görsel benzerliklerden kaynaklı karışıklıklar gözlenmiştir. Bu durum, veri setindeki örneklerin dengesizliği ve sınıflar arasındaki görsel benzerliklerden kaynaklanabilir.

- Daha yüksek performans için:
-Veri setine daha fazla örnek eklenebilir,
-Daha derin bir CNN mimarisi kullanılabilir,

Sonuç olarak, proje kapsamında elde edilen doğruluk oranı, çöp sınıflandırma gibi gerçek hayatta önemli bir problem için tatmin edici ve uygulanabilir düzeydedir.

# Sonuç ve Gelecek Çalışmalar
- Bu çalışmada, çöp sınıflandırma problemine yönelik bir CNN tabanlı derin öğrenme modeli geliştirilmiştir. Veriler üzerinde ön işleme ve data augmentation yöntemleri uygulanmış, ardından model farklı hiperparametre denemeleri (dropout oranı, batch size, TTA gibi) ile optimize edilmiştir. Elde edilen sonuçlara göre:

- Model, eğitim ve doğrulama setinde yüksek doğruluk elde etmiştir. Confusion matrix ve classification report incelendiğinde, modelin sınıflar arasında genel olarak dengeli bir performans sergilediği görülmüştür. TTA (Test Time Augmentation) denemesi ile modelin kararlılığı artırılmıştır. Doğru ve yanlış sınıflandırılan örnek görseller, modelin güçlü ve zayıf yönlerini görselleştirmeye yardımcı olmuştur.

Ayrıca modelin karar mekanizmasını görselleştirmek için Grad-CAM yöntemi denenmiş ancak teknik uyumsuzluklardan dolayı başarıyla uygulanamamıştır. Bu durum gelecek çalışmalarda giderilerek, modelin hangi bölgeleri dikkate aldığı daha ayrıntılı incelenebilir.

Bununla birlikte, projenin daha ileri düzeyde geliştirilmesi mümkündür. Gelecek çalışmalarda:

- Daha geniş ve dengeli veri setleri kullanılarak modelin genelleme kabiliyeti artırılabilir.
- Farklı ve daha derin mimariler (örneğin ResNet, EfficientNet) üzerinde denemeler yapılarak performans kıyaslamaları gerçekleştirilebilir.
- Model, gerçek zamanlı tahmin yapabilecek bir arayüz ile entegre edilerek kullanıcıların kendi verileri üzerinde test yapmaları sağlanabilir.
- Mobil ve gömülü sistemlere uyarlanabilecek daha hafif modeller (TensorFlow Lite vb.) geliştirilerek uygulamanın günlük hayatta kullanılabilirliği artırılabilir.
Sonuç olarak, bu proje yalnızca bir ödev kapsamında değil, aynı zamanda geri dönüşüm süreçlerini kolaylaştırabilecek ve çevresel farkındalığı artırabilecek gerçek dünyaya uygulanabilir bir sistemin ilk adımı olarak değerlendirilebilir.

# KAGGLE NOTEBOOK LİNKİ
[Proje Notebook (Aslıhan Özcan) & (Ahmet Gökay Değer)] [ https://www.kaggle.com/code/aslhanzcan/garbageclassificationproject ] [ https://www.kaggle.com/kernels/scriptcontent/264025765/download ]
