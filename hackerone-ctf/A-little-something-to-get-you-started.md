# HackerOne101Ctf - A little something to get you started

- Yazar : [[EtherelSentinel](https://github.com/EtherealSentinel)\]

## Açıklama : 
> HackerOne sitesinin bize sunduğu hacker101 ctfleri serisinin ilk ctf'nin çözümü burada açıklanacaktır. Kısaca kendimden bahsetmek gerekirse siber güvenliğe adımını atmış gelişme konusunda hırslı,  sizlerden biriyim. Baştan açıklamakta fayda var çözümlerde flaglar
> paylaşılmayacaktır sadece gidiş yolları gösterilecektir umarım faydalı olur iyi okumalar.

## Çözüm :

### Adım 1
>Ctf'mizi başlatıyoruz. <br>
>Bu noktada startan başlattıktan bir süre sonra sizi yönlendirecektir.
>![image](https://github.com/user-attachments/assets/35a14bb8-bedb-460d-8964-5ed487dad725)
>
>Bu şekilde bir url üzerine sizi yönlendirecektir : https://xxxxxx.ctf.hacker101.com <br>
><br>
>verilen url girdikten sonra karşınıza düz bir sayfa çıkmakta içerisinde metin bulunan benim burada aklıma ilk gelen nokta şu oldu. bu sayfaya bağlı farklı dizinler var mı ? Console görüntüsünde bize ipuçları bırakılmış mı ? gözden kaçan bir alan var mı?  <br><br>
### Adım 2
>bu tarz soruları kendime sorduktan sonra en basit olan ve erişimi nispeten daha kolay olan ve her zaman fikrimce ilk aşamada kontrol etmemiz gereken sayfanın kaynak kodlarını ve Console kısmını inceliyorum.
>![image](https://github.com/user-attachments/assets/d545512f-573c-4288-aba4-250b476129cf) Bu şekilde ulaşabilirsiniz tarayıcınıza göre değişkenlik göstericektir
>![image](https://github.com/user-attachments/assets/fd246e12-bd6a-452d-a992-6ae63eb52de1) <br>
>Kaynak kodunu incelediğimiz zaman Header kısmında dikkatimizi çeken bir yönlendirme olduğunu görüyorum bu yönlendirmeyi merak ettiğim için network kısmına bakıyorum.<br><br>
>![image](https://github.com/user-attachments/assets/0690fa18-ecd3-4394-8a95-62c72d899ae2)
### Adım 3
><br> Evet görüldüğü üzere bir alt dizinimiz var. Alt dizine gittiğimizde ise şöyle bir sonuçla karşılaşıyoruz.
>![image](https://github.com/user-attachments/assets/8ea9c93f-60af-4a6c-bb45-50311e619a3e)
><br>Evet görüldüğü üzere Hedefimiz olan flag bulmuş olduk

