# HackerOne101Ctf - A little something to get you started

- Yazar : [[EtherelSentinel](https://github.com/EtherealSentinel)\]

## Açıklama : 
> HackerOne sitesinin bize sunduğu hacker101 ctfleri serisinin ikinci ctf'nin çözümü burada açıklanacaktır. Kısaca kendimden bahsetmek gerekirse siber güvenliğe adımını atmış gelişme konusunda hırslı,  sizlerden biriyim. Baştan açıklamakta fayda var çözümlerde flaglar
> paylaşılmayacaktır sadece gidiş yolları gösterilecektir umarım faydalı olur iyi okumalar.

## Çözüm :

### Adım 1

> Ctf'mizi başlatıyoruz. <br>
> Bu şekilde bir url üzerine sizi yönlendirecektir : https://xxxxxx.ctf.hacker101.com <br>
> <br>
> verilen url girdikten sonra karşınıza düz bir sayfa çıkmakta içerisinde metin bulunan benim burada aklıma ilk gelen nokta şu oldu. bu sayfaya bağlı farklı dizinler var mı ? Console görüntüsünde bize ipuçları bırakılmış mı ? gözden kaçan bir alan var mı?  <br><br>

### Adım 2 (keşif)
> Siteyi kurcalamaya keşfetmeye başlıyoruz tek tek bütün bize verilen linklere giriyoruz bizi nerelere götürdükleri her zaman önemlidir.<br>
> ilk linke tıkladığımda (testing) url sonunda page 1 e gittiğimi görüyorum <br>
> ![image](https://github.com/user-attachments/assets/f1bfd419-7f50-46ab-9198-dcf9c8ab27b5) <br><br><br>
> bu kısımda dikkatimi çeken bir edit kısmının olması<br><br>
> edit kısmına tıkladığımda <br><br>
> ![image](https://github.com/user-attachments/assets/c35cac2a-3407-4dd5-8436-ba99ea64d835)
> <br>bu şekilde bir forum sayfası önümüze çıkıyor ayrıca url de değişen bazı şeyler var. https://xxxxxxx.ctf.hacker101.com/page/edit/1 şeklinde bir urlemiz var bu kısımda direk benim aklıma sqli tarzı bir durumun olabileceği
> diğer bir dikkatimi çeken durum genelde forumlarda oluşabilen açıklar Xss tarzı bir açık olabilir. sırasıyla aklımıza gelenleri deniyoruz
<br>

### Adım 3 

> https://xxxxxxx.ctf.hacker101.com/page/edit/1 şeklinde olan url mizin sonuna (') karakterini ekliyoruz <br><br>
>
> ![image](https://github.com/user-attachments/assets/6d04957e-e0ac-4e4f-8b25-65b31a0de124) (FLAG1) <br>
>  Ve evet beklediğimiz oluyor sayfamızda bir sqli açığımız var. Normalde bu ekranda bir hata alırsın ve hataya göre ilerlersiniz ya da başlangıç noktanıza göre farklı bir şey yapar web sunucusu bunu zaten farkedersiniz. ( Sql İnjection uzun bir konu olduğu için burda anlatmayacağım )
> <br>
> Diğer dikkatimizi çeken kısma bakalım text box tarzı olan inputumuzun içerisine klasik olarak bilinen xss payloadlarından birini yazıyoruz.
> <script>alert('XSS')</script> --> bunu yazdığımızda çalışmadığını göreceksiniz daha derinlemesine incelediğinizde bir filtrenin bulunduğunu ve script tarzı girdileri filtrelediğini farkedeceksiniz. Bu aşamadı aklıma şu geldi.
> <br> başlık kısmına bunu yazsak ne olur . Öncelikle bir test yazısı 'a' yazıyorum 'a' yazdığımda ve oluştur tuşuna bastığımda ana sayfaya bunu gönderdiğini farkettim. Aklıma direk Stored Xss olabileceği geldi. Başlık kısmına aynı payloadı ekledim
> <br><br> ![image](https://github.com/user-attachments/assets/2684d488-0b70-487c-8533-598e59919390)
><br> Bu şekilde çalıştırınca koyduğumuz payloadı ana menüde kısıma yazmasını bekliyorum. <br>
> ![image](https://github.com/user-attachments/assets/76bc0c38-fcd9-4680-a8c9-d8d341c1b15e) (FLAG2) <br>
> Ve evet 2. flag da bu noktada önümüze çıkıyor. 
><br>
><br>
> markdown test sayfamıza geldiğimizde dikkatimizi çeken bir şey denk geliyor bir image var image varsa demek oluyor ki bu textboxun içerisinde image ekleyebiliyoruz. Burdan çıkaracağımız anlam script olarak kullanamadığımız payloadımızı
> bu noktada biraz daha gizleyerek filtreyi atlatacak şekilde değiştirerek deniyoruz şu şekilde bir payload deniyoruz <br> <img src=x onerror=alert('XSS')>
><br>
>![image](https://github.com/user-attachments/assets/297a1c9c-3b97-4a7a-8ac5-16afe4e67b14)
> <br> bu şekilde denediğimizde
> <br> ![image](https://github.com/user-attachments/assets/15ae1c6e-f49f-42c7-bb6e-99fdea45793f) <br> bu noktada payloadımızın eklendiğini ve eklenen payloadın yanında 3. Flag'ın orda durduğunu görüyoruz ( Console ekranında bakabilirsiniz)
> <br>![image](https://github.com/user-attachments/assets/14efd049-223c-4b6b-8f63-84756128fce7) <br> (3.Flag)
> <br> Geriye son bir flag kaldı.
> <br> https://xxxxxx.ctf.hacker101.com/page/10 url ye dikkatli bakınca 10 gibi aslında sıralamaya uygun olmayan bir indeksden başladığını dikkatimi çekiyor geriye doğru sayfaları yazmaya başlıyorum. Ve başımıza ilginç bir durum denk geliyor.
> <br> 7 indekse geldiğimizde bu sayfanın gizli olduğunu farkediyoruz. Gizli olan bu sayfaya aslında erişmenin bir yolunu bulmuştuk dikkat ederseniz edit isteği url üzerinden gidiyor. Neden şansımızı denemeyelim ki
> <br><br><br>https://xxxxxx.ctf.hacker101.com/page/edit/7  şu şekilde url yi değiştirdiğimizde.<br><br>
> <br>![image](https://github.com/user-attachments/assets/6bfa9fda-ea89-42c7-95e5-2b667d062b77) (4.FLAG) <br>
>gizli sayfaya ulaşmış ve bu gizli sayfada son flag olan 4. Flag'ı bulmuş oluyoruz. <br>




