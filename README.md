# Flutter'da Performans

## FLUTTER’ DA PERFORMANS (PERFORMANCE IN FLUTTER)

This site was built using [Medium](https://medium.com/@humeyraapolat/flutter-da-performans-performance-in-flutter-308454cb2f33).

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

Flutter Profiling yaparken dikkat etmemiz gereken iki önemli özellik vardır.Bunlardan ilki uygulamanın debug modda asla profile olarak çalıştırılmamasıdır çünkü debug mode production moddan daha yavaş çalışır ve size gerçek performansı vermez. İkinci olarak ise uygulamayı emülatörde çalıştırmaktan kaçınılması gerektiğidir ve yine gerçek performansı sağlamaz. *Do it profiling in profile mode and do it on the real device.*

**Kullanılan fotoğrafın uzantısına ve boyutuna göre performans ölçümü ve uygulama üzerindeki etkisi ?**

Bu durumu beraber gözlemleyeceğiz .Uygulayacağım aşamaları şu şekilde parçalara ayırdım

aynı uzantıda ama farklı boyuttaki görsellerin yüklenme hızı; bunları da jpg, png ve webp olarak üçe ayırdım kendi içlerinde karşılaştırma yapmak için.
aynı boyutta ama farklı uzantıdaki görsellerin yüklenme hızı
ve son olarak aynı boyuttaki farklı uzantıdaki fotoğrafların kapladıkları alanın kb cinsinden değeri
*Not : Yazının geri kalanında test ettiğim ve tablolarla ilişkilendirdiğim üç fotoğraf formatından JPEG, PNG ve WebP formatı için şu bilgiler göz önüne alınmalıdır. PNG formatı JPEG’in 50 kat, WebP ise PNG’nin 50 kat sıkıştırılmasıyla oluşturulmuştur.*

**İlk öncelikle WebP uzantısına sahip 40 × 27 , 400 × 267 ve 4096 × 2731 fotoğrafların yüklenme hızlarını inceleyelim:**

1. 40 × 27 boyutundaki fotoğrafın  yüklenme hızı :

![image](https://user-images.githubusercontent.com/71139790/191954895-9b22d189-6458-4f0d-aa7d-b7dd71ef561b.png)

2. 400 × 267 boyutundaki fotoğrafın yüklenme hızı :

![image](https://user-images.githubusercontent.com/71139790/191955151-12e7da9f-70b6-4277-9734-126a251dbec8.png)

3. 4096 × 2731 boyutundaki fotoğrafın yüklenme hızı :

![image](https://user-images.githubusercontent.com/71139790/191955219-135bb6ee-e4f4-4d67-90cc-d113c57ecc80.png)

**Şimdi aynı boyutlarda PNG uzantılı fotoğrafları inceleyelim :**

1. 40 × 27 boyutundaki fotoğrafın  yüklenme hızı :

![image](https://user-images.githubusercontent.com/71139790/191955441-be20a602-6020-4e87-82be-a0fb8a846c67.png)


2. 400 × 267 boyutundaki fotoğrafın yüklenme hızı :

![image](https://user-images.githubusercontent.com/71139790/191955536-c58f2e58-92c6-4f18-935d-fd406d758b92.png)

3. 4096 × 2731 boyutundaki fotoğrafın yüklenme hızı :

![image](https://user-images.githubusercontent.com/71139790/191955716-cd705327-500e-49e5-afc1-03415ac352d7.png)

**Son olarak da aynı boyuttaki fotoğrafları JPEG formatında fotoğrafları inceleyelim**

1. 40 × 27 boyutundaki fotoğrafın  yüklenme hızı :
![image](https://user-images.githubusercontent.com/71139790/191955760-ab47bf26-2283-463c-9798-b82a5282f5e5.png)


2. 400 × 267 boyutundaki fotoğrafın yüklenme hızı :

![image](https://user-images.githubusercontent.com/71139790/191955809-6e354602-c9f9-42f0-abe5-9fa1f5c48dee.png)

3. 4096 × 2731 boyutundaki fotoğrafın yüklenme hızı :

![image](https://user-images.githubusercontent.com/71139790/191966651-8322c60b-9213-4ac6-ba55-4c371d305680.png)

Profile modunda çalıştırdığım uygulamamda tracingleri ölçümledim ve fotoğrafların uzantısı aynı kaldığı takdirde üç uzantı (jpg, png, webp) için şunu söyleyebilirim; fotoğrafların boyutları uzantısı ne olursa olsun arttıkça yüklenme süresi uzuyor. Küçük boyutlarda fotoğraf kullanmanın önemi gözle görülebilir oluyor. Daha detaylı anlatım yapabilmek açısında yukarıdaki görsellerde summary kısımlarını tablolaştırılmış şekilde sizlere anlatacağım.

![image](https://user-images.githubusercontent.com/71139790/191955946-e85dc5db-4192-42fc-8551-b0238e8cc0dd.png)

Yukarıdaki tabloda gördüğünüz üzere farklı üç boyuttaki fotoğraflar için en etkili fotoğraf uzantı boyutunun Webp olduğunu gözlemledik. Tabloyu dikkatli bir şekilde incelerseniz eğer fotoğraf 40 × 27 gibi küçük boyutta olduğu zaman PNG veya WebP kullanmak birbirine çok yakın iki seçenek gibi gözükse bile fotoğraf boyutunu her kenardan 10 kat arttırdığımız zaman WebP uzantılı fotoğraf kullanmak bize 20 kat oranda hız kazandırıyor ve fotoğrafın boyutunu 4096 × 2731 gibi çok büyük bir boyuta ayarlarsa ise bize ortalama 40 kat daha hızlı bir dönüş sağlıyor. Tabloda inceleyeceğimiz bir diğer durum ise JPEG formatının PNG formatıyla olan karşılaştırmasıdır. JPEG uzantısı küçük fotoğraf karelerinde daha yavaş sonuç verirler fotoğraf büyüdükçe uygulamayı yavaşlatmaya başladığını görebiliyoruz. Son olarak şu sonuca varıyoruz ki uygulamanın performansı sadece istenilen fonksiyonları tamamlaması olarak ölçülmediği gibi yavaş bir arayüzün kullanıcıyı da sıkacağını göz önüne alırsak WebP uzantısı ile uygulamanın hız açısından  performansını maksimize edebiliriz. 

Şimdi ise uygulamanın performansını arttırmak açısında önemli olan bir diğer konumuz olan fotoğrafların uzantılarına göre kapladıkları alanları inceleyelim. 

![image](https://user-images.githubusercontent.com/71139790/191966803-a832ab19-fbf6-4d39-81ab-93185c050824.png)


Yukarıdaki tabloya baktığımız zaman üç farklı fotoğraf boyutu için üç farklı uzantının uygulama içinde ne kadar yer kapladığını görebiliyoruz. JPEG ve PNG uzantılı fotoğrafların kapladığı alanın tartışmasız çok fazla olduğunu söylemek mümkün. 40 × 27 boyutundaki sütuna baktığımız zaman bile WEbP uzantılı bir fotoğrafın diğer iki uzantıdaki fotoğraftan neredeyse on kat daha az yer kapladığını gözlemliyoruz. Bu veriler tek bir görsel için bu kadar fark yaratırken uygulamamız büyüdükçe kullandığımız fotoğraf boyutu ve uzantısına göre alandan 3 ila 10 kat arası tasarruf sağlayabiliriz. 

Fotoğrafın kapladığı alan ve yüklenme süresi(tracing) beraber göz önüne alındığı zaman şu sonuca ulaşırız : kullanılacak fotoğrafın uzantısı ne olursa olsun boyutu küçüldükçe hem kapladığı alan hem de yüklenmesi için gereken süre azalıyor. Uygulamanın performansını hem hız hem de boyut (kapladığı alan) maksimize etmek istediğimizde kullanılan fotoğrafların formatlarını WebP uzantısına çevirerek hem hız konusunda  hem de alanda tasarruf sağlarız. 
















