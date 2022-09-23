# Flutter'da Performans

## FLUTTER’ DA PERFORMANS (PERFORMANCE IN FLUTTER)

Bir uygulama geliştirici olduğunuzu ve en iyi özelliklerle, harika animasyonlarla en mükemmel uygulamayı geliştirdiğinizi düşünün. Bu harika bir şey olurdu değil mi ? Bu sorunun cevabı uygulamanın performansı iyiyse tabi ki evet olacaktır ancak uygulama gereken performansı sağlayamıyorsa tüm güzel özellikleri boşuna olacak olacak ve düşük performans uygulamanın değerini çok fazla düşürecektir.

Flutter geliştirmede yeniyseniz Flutter gerçekten performans sağlama açısından iyi ve hızlıdır, eğer Flutter’ın sınırlarını çok fazla zorlamazsanız ve kompleks hatalar ile uygulamayı boğmazsanız, uygulamanız gereken maksimum performansı size sağlayacaktır.

**Performans konusu işlenirken bilmeniz gereken terimler (Terminoloji) :**

Jank: Görsel bir teklemedir. Animasyon geçişleri sırasında görselin akıcı bir geçişi olması gerekirken takılı şekilde ilerlemesi bazı framelerin (çerçeve ya da görsel karelerinin) atlanmasıdır.
UI Thread : UI thread içinde widgetlar oluşturuyoruz ve bu thread içerisinde çok fazla zaman harcarsak uygulama Jank olur çünkü burada Flutter framework çalışır.
Tracing: Uygulamanın ne yaptığının kaydedilmesidir. Her hesaplamanın ne kadar süre alacağını gösterir.
Flame Chart : İzlenen olayın zaman çizelgesini almaktır. Ne ne zaman başladı sorularına cevap vermeyi kolaylaştırır. Uygulama büyüdükçe kompleks olur lakin anlaşılır bir şekildedir.
Trade- off : İki durum arasında kaldığında varacağın uzlaşmadır. Uygulamaya sayısız efekt ve özellik eklemek istersin ama aynı zamanda çok da hızlı çalışmasını istersin bu bir trade off örneğidir.

**Flutter performans nedir ve neden bu kadar çok önemlidir ?**

Performans, bir eylemin kendisinin yürütülmesi değildir aksine, bir şeyin ya da birisinin ne kadar iyi performans gösterebildiğidir. Basitçe söylemek gerekirse, performans önemli ve faydalıdır çünkü kapsamda performansın ölçülebilir özelliklere veya ölçülere sahip olması gerekir. Bu şu anlama gelir:

Bir performans raporunun metriklerinin kullanımının kolaylaştırılması
Performansın çok az belirsizliği vardır.
Performans karşılaştırılabilir ve dönüştürülebilir.
Performans adildir.
Aşağıda, burada tartışılan 4 nokta biraz farklı bir bakış açısıyla özetlenmektedir:

Performans metriklerinin kullanımını kolaylaştırın. Okuyucuları çok sayıda sayı veya kelime ile boğmayın. Çok sayıda sayı varsa, bunları daha küçük bir sayı kümesinde özetlemeye çalışın (örneğin, birçok sayıyı tek bir ortalama sayı olarak özetleyin). Okuyucuları yalnızca sayılar önemli ölçüde değiştiğinde bilgilendirin (örneğin, ani artışlar ve gerilemelerde otomatik uyarılar).

Performans ölçümlerini mümkün olduğunca açık hale getirin. Numaranın kullandığı birimi tanımlayın. Sayının nasıl ölçüldüğünü tam olarak açıklayın. Sayıyı kolayca tekrarlanabilir hale getirin. Çok fazla gürültü olduğunda, tam dağılımı göstermeye çalışın veya birçok gürültülü ölçümü bir araya getirerek gürültüyü mümkün olduğunca ortadan kaldırın.

Performansı karşılaştırmayı kolaylaştırın. Örneğin, mevcut sürümü eski sürümle karşılaştırmak için bir zaman çizelgesi sağlayın. Bir metriği diğerine dönüştürmek için yollar ve araçlar sağlayın. Örneğin, hem bellek artışını hem de fps düşüşlerini, düşen kullanıcı sayısına veya dolar cinsinden kaybedilen gelire dönüştürebilirsek, bunları karşılaştırabilir ve bilinçli bir takas yapabiliriz.

Performans metriklerinin mümkün olduğunca geniş bir popülasyonu izlemesini sağlayın, böylece kimse geride kalmaz.

**Performansı nasıl geliştirebilirim ?**

Performansı artırmak için öncelikle metriklere ihtiyacınız vardır bunlar sorunları ve iyileştirmeleri doğrulamak için bazı ölçülebilir sayılardır.

Performans geliştirmesini dört ana başlık halinde bölebiliriz. Bunlar sırası ile :

1. Hız (speed)
2. Hafıza (memory)
3. Uygulama Boyutu (App size)
4. Enerji (Energy)

**Flutter Performans Profili Oluşturma (Flutter Performance Profiling) Nedir ?**

Flutter Profiling yaparken dikkat etmemiz gereken iki önemli özellik vardır.Bunlardan ilki uygulamanın debug modda asla profile olarak çalıştırılmamasıdır çünkü debug mode production moddan daha yavaş çalışır ve size gerçek performansı vermez. İkinci olarak ise uygulamayı emülatörde çalıştırmaktan kaçınılması gerektiğidir ve yine gerçek performansı sağlamaz. Do it profiling in profile mode and do it on the real device.

**Kullanılan fotoğrafın uzantısına ve boyutuna göre performans ölçümü ve uygulama üzerindeki etkisi ?**

Bu durumu beraber gözlemleyeceğiz .Uygulayacağım aşamaları şu şekilde parçalara ayırdım

aynı uzantıda ama farklı boyuttaki görsellerin yüklenme hızı; bunları da jpg, png ve webp olarak üçe ayırdım kendi içlerinde karşılaştırma yapmak için.
aynı boyutta ama farklı uzantıdaki görsellerin yüklenme hızı
ve son olarak aynı boyuttaki farklı uzantıdaki fotoğrafların kapladıkları alanın kb cinsinden değeri
Not : Yazının geri kalanında test ettiğim ve tablolarla ilişkilendirdiğim üç fotoğraf formatından JPEG, PNG ve WebP formatı için şu bilgiler göz önüne alınmalıdır. PNG formatı JPEG’in 50 kat, WebP ise PNG’nin 50 kat sıkıştırılmasıyla oluşturulmuştur.

İlk öncelikle WebP uzantısına sahip 40 × 27 , 400 × 267 ve 4096 × 2731 fotoğrafların yüklenme hızlarını inceleyelim:




