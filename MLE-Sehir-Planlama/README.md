***MLE - Akıllı Şehir Trafik Modelleme***
*Bu proje, akıllı şehir sistemlerinde trafik yoğunluğunu modellemek amacıyla Maximum Likelihood Estimation yönteminin teorik ve pratik uygulamasını içermektedir.*

**1. Problem Tanımı**
Bu çalışmada, trafik akışının Poisson Dağılımı ile temsil edilebileceği varsayılmıştır. Temel amaç, gözlemlenen trafik verilerinden hareketle dağılımın ana parametresi değerini en doğru şekilde tahmin etmektir.

**2. Veri**(
    Veri seti toplam 14 gözlemden oluşmakta ve araç yoğunluğu değişimlerini içermektedir.

**3. Yöntem**
Proje iki çözüm sunar:
    Teorik Çözüm: Poisson PMF kullanılarak Likelihood ve Log-Likelihood fonksiyonları türetilmiştir. Matematiksel türev sonucunda, Poisson dağılımı için MLE parametre tahmin edicisinin örneklem ortalamasına eşit olduğu kanıtlanmıştır.
    Nümerik Çözüm: Python üzerinde scipy.optimize kütüphanesi kullanılarak Negative Log-Likelihood fonksiyonu minimize edilmiş ve parametre nümerik olarak hesaplanmıştır.

**4. Sonuçlar**
    Nümerik ve analitik sonuçların birbirine son derece yakın olması, modelin tutarlılığını doğrulamaktadır.

**5. Yorum ve Tartışma**
    Model Uyumu: Poisson modelinin oluşturulan histogram ve PMF grafiği üzerinden veriyle uyumlu olduğu, olay temsilinde başarılı bir performans sergilediği görülmüştür.
    Outlier Analizi: Veriye 200 gibi ekstrem bir değer eklendiğinde modelin bu durumdan nasıl etkilendiği incelenmiştir.
    Genel Değerlendirme: Bu modelleme yaklaşımı, gelecekteki trafik yoğunluklarını tahmin etmek (sampling) ve trafik sinyalizasyon sistemlerini optimize etmek için temel bir yapı taşı olarak kullanılabilir.
    
