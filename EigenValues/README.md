***EigenValues***

**1. Soru: Matrisler ve AI**

Matrisler sadece birden fazla denklemin bir ifadesidir bu değerleri somutlaştıran bizim modelleme biçimimizdir. Aynı şekilde bir "eigenvalue" vs. dediğimizde onun ne olduğu da bize kalmıştır: Bir oyun motoru yapıyorsanız eigenvector sizin dönüş ekseninizdir, matematik yapıyorsanız dönüşümün karakterini anlatan bir parçadır veya ml için bakıyorsanız kapalı formüllerin içine bakamadığı bu dünyada eigenler sadece hilelerdir, güvenilen bir algoritmayı rahat uygulatmak için yardımcı araçtır.  
İlişki aslında basittir A * x = lambda * x. X eigenvector olur lambda ise eigenvalue. ML'de en somut uygulaması kovaryanstır, veri setinden kovaryans çekilince yönleri ve ilişkileri net bir şekilde görürüz. Bazen de nümerik hataları göze alarak yine ayrışım yapmada kullanılır ama temele inince aslında hep ordadır.
Popüler uygulamaları arasında öneri algoritmaları da vardır, bunlardan en bilineni pagerank denebilir.
Aynı zamanda PCA gibi algoritmalarda kullanılır hatta "insan yüzü 60 elemandır"ı yayacak kadar da başarılıdır sıkıştırmada.

**2. Soru: EIG**
numpy.linalg.eig fonksiyonu, karesel bir matrisin özdeğerlerini ve özvektörlerini hesaplayan temel arayüzdür. Kullanımı w, v = np.linalg.eig(A) şeklindedir.

Girdi Çıktı:
  A: Kare Matris Input.
  w (Eigenvalues): Matrisin özdeğerlerini içeren tek boyutlu bir dizi, sırasız.
  v (Eigenvectors): Normalize edilmiş özvektörler (sütunlar okunmalı tek alınırsa).

Arka Plan:
  Numpy bu karmaşık hesaplamaları python ile sıfırdan yapmaz, arkada aslında low-level kod vardır.
  LAPACK Kütüphanesi: Dökümantasyon aslında çoğu matematiksel işin Lapack'a devredildiğini yazmış.
  _geev ve QR: Numpy, genel matrisler için LAPACK içindeki _geev fonksiyonlarını çağırır. 5X5 den büyük matrislerde iteratif yöntemlere geçerek yakınsamaya çalışır.
  Karmaşık Sayı Yönetimi: Sonuçlar karmaşık sayı çıkabilir. Fonksiyon bu durumu da yönetir ama kullanıcı görmez.

İteratif-Mantıksal Yapısı:
  A = QR  ayrışımı bulunur sonra A_new = R * Q şeklinde güncellenir ardından değerlerle yakınsama kontrolü yaparak belli bir adıma veya toleransa ulaşıncaya kadar devam eder (mini_qr'dakinin low level hali aslında). Ardından vektör normalize edilir uzunluğu 1 yapılır ve return edilir.

**Kaynak**
https://linear.axler.net/LADR4e.pdf
https://codesignal.com/learn/courses/navigating-data-simplification-with-pca/lessons/mastering-pca-eigenvectors-eigenvalues-and-covariance-matrix-explained
https://numpy.org/doc/2.1/reference/generated/numpy.linalg.eig.html
