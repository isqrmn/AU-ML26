# 4. Ödev Uzak Bir Galaksinin Parlaklık Analizi

Bu proje uzak bir galaksiden elde edilen gürültülü gözlem verilerini kullanarak,
galaksinin gerçek parlaklığını ve hata payını Bayesian Inference yöntemiyle tahmin etmeyi amaçlamaktadır.

## Projenin Amacı

Astronomide kabul edilen **Bayesian Inference** kullanılmıştır. Bu yöntemin seçilmesinin temel nedeni sadece tek bir nokta tahmini yapmak yerine parametrelerin olasılık dağılımlarını hesaplayarak bize bir güven aralığı sunmasıdır.

## Tartışma Soruları

### 1. Prior Etkisi
**Soru:** Eğer parlaklık için çok dar bir prior seçseydiniz (örneğin 100-110 arası), sonuç nasıl değişirdi?

**Cevap:** Bayes teoremi, prior ile likelihood'un çarpımına dayanır. 
Eğer prior aralığını 100-110 olarak aşırı kısıtlasaydık, modelimiz gerçek değer olan 150'yi bulamayacaktı. 
Çünkü model, 110'un üzerindeki her değeri matematiksel olarak "imkansız" kabul edecekti.
Bu durum, posterior dağılımının 110 sınırına yığılmasına neden olur, veriyi ezer ve yanlış bir tahminle bizi bırakırdı.
Prior seçimi, modeli yönlendirirken burda engel olurdu.

### 2. Veri Miktarının Etkisi
**Soru:** Gözlem sayısını 5'e düşürdüğünüzde posterior dağılımının genişliği nasıl etkileniyor?

**Cevap:** Gözlem sayısı 50'den 5'e düştüğünde, elimizdeki bilgi miktarı azalır.
Bayesyen çıkarımda veri miktarı azaldıkça, likelihood'un etkisi zayıflar ve modelin belirsizliği artar. 
Görsel olarak ifade etmek gerekirse, posterior dağılımını gösteren çan eğrisi dar ve sivri bir yapıdan, çok daha geniş bir yapıya dönüşür.
Bu da tahminimizin hata payının çok daha genişlemesi anlamına gelir.

### 6.1. Merkezi Eğilim ve Doğruluk (Accuracy) Analizi
Sistemdeki yüksek gürültüye (10) rağmen, modelin tahmin ettiği medyan parlaklık değeri (147.79) gerçek değere (150) oldukça yakındır.
Bu durum, Bayesyen modelin ve MCMC örneklemesinin, arkasında yeterli veri olduğunda noisy 
ortamlarda bile merkezi eğilimi doğru yakalayabildiğini gösterir.

### 6.2. Tahmin Karşılaştırması
Veri setinin ortalamasını bulmak ile saçılımını bulmak farklıdır. 50 adet veri noktası, verilerin "merkez noktasını" yüksek bir kesinlikle saptamak için yeterli yoğunluğu sağlar.
Ancak standart sapma, aykırı değerlere daha duyarlıdır.

### 6.3. Olasılıksal Korelasyon Analizi
MCMC sonuçlarının görselleştirildiği plot incelendiğinde, parametrelerin kesişim noktasındaki çizgilerinin eksenlere dik veya paralel konumlandığı görülmektedir.
Eğer bu iki parametre birbirine bağımlı olsaydı, elipsler eğik gibi olurdu.
Elipslerin dik duruşu, galaksinin parlaklık tahmini ile cihazın gözlem hatası tahmini arasında korelasyon olmadığını,
bu iki parametrenin birbirinden bağımsız olarak tahmin edilebildiğini anlatır.
