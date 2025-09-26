# garbage-classification
Makine öğrenmesi ve derin öğrenme kullanarak çöp türlerini sınıflandırma projesi.

# GİRİŞ

Çevre bilincinin artması ve sürdürülebilirlik anlayışının yaygınlaşmasıyla birlikte, geri dönüşüm süreçlerinin verimli şekilde yürütülmesi her geçen gün daha kritik hale gelmektedir. Atıkların doğru sınıflandırılması, hem doğal kaynakların korunması hem de çevresel zararların azaltılması açısından temel bir gerekliliktir.

 Çalışmada kullanılan veri seti, 6 farklı atık türünü (plastik, cam, kağıt, metal, organik ve pil) içeren görsellerden oluşmaktadır.  
 Bu veri setinde toplam 4650 adet görüntü bulunmaktadır. Veri seti, sınıflandırma açısından dengeli bir dağılım göstermekte olup, modelin eğitim ve test süreçlerinde uygun bir temel sunmaktadır.
 
 # YÖNTEMLER
 
Bu projede, görüntü sınıflandırma için derin öğrenme tabanlı yöntemler kullanılmıştır. Özellikle Convolutional Neural Networks (CNN) mimarisi tercih edilmiştir. Kullanılan yöntem ve algoritmalar aşağıda özetlenmiştir:

- Convolutional Neural Networks (CNN): Görüntülerden öznitelik çıkarımı ve sınıflandırma için temel model.  
- Aktivasyon Fonksiyonları:
  - ReLU (Rectified Linear Unit): Ara katmanlarda doğrusal olmayanlık sağlamak için kullanıldı. 
  - Softmax: Çıkış katmanında sınıf olasılıklarını hesaplamak için ykullanıldı. 
  - Optimizasyon Algoritması
  - Adam (Adaptive Moment Estimation): Ağırlıkların güncellenmesi için kullanıldı.  
  - Kayıp Fonksiyonu
  - Categorical Cross-Entropy: Çok sınıflı sınıflandırma problemleri için kullanıldı.  
  - Düzenleme (Regularization) Teknikleri:
  - Dropout: Aşırı öğrenmeyi (overfitting) engellemek için kullanıldı. 
  - Data Augmentation (Veri Artırma): Görsellerin çeşitliliğini artırmak için (döndürme, çevirme, yakınlaştırma vb.) kullanıldı.
Bu çalışmayla, atıkların doğru sınıflandırılması için yapay zekâ tabanlı çözümlerin uygulanabilirliği gösterilmiştir.

# METRİKLER

Modelin performansını değerlendirmek için temel metrikler olarak doğruluk (accuracy) ve kayıp (loss) değerleri kullanılmıştır. Eğitim sürecinde ayrıca doğrulama (validation) seti üzerinde de takip yapılmıştır.
Modelimizi 15 epoch boyunca eğittik.

Eğitim doğruluğu %72.9, doğrulama doğruluğu %71.9 seviyesinde elde edilmiştir.
Eğitim ve doğrulama doğruluklarının birbirine yakın olması, modelin veriyi ezberlemek yerine genelleme yapabildiğini göstermektedir.
Ancak doğruluk oranlarının daha yüksek olabilmesi için epoch sayısı artırılabilir veya farklı mimariler denenebilir.

Elde edilen sonuçlara göre model, eğitim verisi üzerinde yüksek doğruluk elde etmiştir. Doğrulama ve test setlerindeki doğruluk değerleri de eğitim doğruluğu ile uyumlu olduğundan, modelin genelleme yeteneğinin başarılı olduğu söylenebilir.  

Ancak bazı sınıflarda (örneğin plastik ve kağıt) görsel benzerliklerden kaynaklı karışıklıklar gözlenmiştir. Bu durum, veri setindeki örneklerin dengesizliği ve sınıflar arasındaki görsel benzerliklerden kaynaklanabilir.  

Daha yüksek performans için:  
- Veri setine daha fazla örnek eklenebilir,  
- Daha derin bir CNN mimarisi kullanılabilir,    

Sonuç olarak, proje kapsamında elde edilen doğruluk oranı, çöp sınıflandırma gibi gerçek hayatta önemli bir problem için tatmin edici ve uygulanabilir düzeydedir.

# SONUÇ VE GELECEK ÇALIŞMALAR

Bu çalışma kapsamında, çöp sınıflandırma problemine yönelik olarak CNN tabanlı bir derin öğrenme modeli geliştirilmiş ve Kaggle ortamında eğitilmiştir. Eğitim ve doğrulama sonuçları, modelin sınıflandırma görevinde temel düzeyde başarılı olduğunu ortaya koymaktadır. Bu durum, projenin ödev kapsamında belirlenen hedeflere ulaştığını göstermektedir.

Bununla birlikte, projenin daha ileri düzeyde geliştirilmesi mümkündür. Gelecek çalışmalarda:  
- Daha geniş ve dengeli veri setleri kullanılarak modelin genelleme kabiliyeti artırılabilir.  
- Veri artırma (data augmentation) teknikleri ve transfer öğrenme yöntemleri uygulanarak daha yüksek doğruluk elde edilebilir.  
- Farklı ve daha derin mimariler (örneğin ResNet, EfficientNet) üzerinde denemeler yapılarak performans kıyaslamaları gerçekleştirilebilir.  
- Model, gerçek zamanlı tahmin yapabilecek bir arayüz ile entegre edilerek kullanıcıların kendi verileri üzerinde test yapmaları sağlanabilir.  
- Mobil ve gömülü sistemlere uyarlanabilecek daha hafif modeller (TensorFlow Lite vb.) geliştirilerek uygulamanın günlük hayatta kullanılabilirliği artırılabilir.  

Sonuç olarak, bu proje yalnızca bir ödev kapsamında değil, aynı zamanda geri dönüşüm süreçlerini kolaylaştırabilecek ve çevresel farkındalığı artırabilecek gerçek dünyaya uygulanabilir bir sistemin ilk adımı olarak değerlendirilebilir.
## KAGGLE NOTEBOOK LİNKİ

[Proje Notebook (Aslıhan Özcan) & (Ahmet Gökay Değer)] [ https://www.kaggle.com/code/aslhanzcan/garbageclassificationproject ]
[ https://www.kaggle.com/kernels/scriptcontent/264025765/download ]
