# Hangi Twitter Kullanıcısı En Çok Hangi Konularda Tweetliyor
   Buradaki amacımız istediğimiz bir Twitter kullanıcısının (hesabı gizli olmayacak) en çok hangi konularda tweetler attığını görebilmektir. Bu sayede istediğimiz kulanıcının hangi konular üzerinde daha çok ilgilendiğini ve bu konularda nelerden bahsettiğini görebileceğiz.
   Yüklemiş olduğum bu Python kodu, belli bir Twitter kullanıcısının son 2000 tweetini alır ve bunlar arasından benzer olanları tespit etmek için KMeans yöntemini kullanır. KMeans yöntemi, verilen tweetleri belirli bir sayıda gruba (kümelere) ayırır ve her grup içinde benzer tweetleri bir arada tutar. Kodun çalışma biçimini özetleyecek olursak;
1.	İlk olarak, Twitter kullanıcısının tweetlerini ve tweetlerle ilgili bilgileri (tweet içeriği, tarih, beğenme sayısı vb.) toplamak için snscrape   kütüphanesini kullanır. Bu kütüphane sayesinde, belli bir kullanıcının tweetlerini bir liste olarak alırız.
2.	Daha sonra, bu tweetlerden istenilen sayı kadarını (burada 2000 tweet) bir pandas veri çerçevesine (dataframe) atarız.
3.	Tweetlerin içeriğini temizlemek için bir fonksiyon yazılır. Bu fonksiyon, tweetleri lowercase hale getirir, URL'leri siler, punctuation karakterlerini çıkartır ve kelimelere ayrılır. Daha sonra, tweetlerdeki kelimelerden stopwords (çok sık kullanılan ve anlamı olmayan kelimeler) çıkartılır. Bunun yanı sıra, kendi oluşturduğumuz bir stopwords listesiyle tweetlerdeki belirli kelimeler de çıkartılır.
4.	Temizlenen tweetler kontrol amaçlı oluşturulan cleanedtweets.csv isimli dosyayada kontrol edilir.
5.	Temizlenen tweetleri tekrar veri çerçevesine atarız ve TfidfVectorizer kullanarak tweetleri vektörize ederiz. TfidfVectorizer, verilen metinleri sayısal değerler dizisi olarak ifade eden bir yöntemdir. Böylece, tweetler arasındaki benzerlikleri daha kolay tespit etmemizi sağlar.
6.	Vektörize edilen tweetleri KMeans yöntemiyle belirli bir sayıda gruba (kümelere) ayırırız. Bu kodda, küme sayısı 5 olarak belirlenmiştir.
7.	Ayırılan grupların ortalama vektörlerini kelimelere çevirir ve bu kelimeleri grupların oluşturulma kriterleri olarak kullanırız.


Örnek olarak;

Aşağıdaki görselden kümelere bölünen gruplar arasından ilk grubun Mansur Yavaş'ın dilemiş olduğu baş sağlığı dilekleri hakkında olduğu, ikinci grubun sağlık,huzur ve günaydın dileklerini ileten tweetleri hakkında olduğu, üçüncü grubun yapmış olduğu kutlamalar hakkında attığı tweetleri, dördüncu grubun 
yaşanmış olan kayıplar hakkında taziyelerini belirten tweetleri hakkında ve son grubun ise beledeiye meclisinde düzenlenen basın toplantıları hakında olduğunu anlayabiliriz.

<img width="858" alt="Ekran Resmi 2023-01-05 22 52 00" src="https://user-images.githubusercontent.com/101113336/210868069-2ba8b83d-828a-4ee7-bbb5-55de64efa554.png">

İstersek de konu başlıklarını grafikte göstererek hangi konular hakkında daha fazla tweetler attığınıda inceleyebilriz.

<img width="1135" alt="Ekran Resmi 2023-01-05 22 51 38" src="https://user-images.githubusercontent.com/101113336/210868098-70189f8a-d710-4c94-a2d0-1f1c5c5895e2.png">


Öğrenci adı: Rıza Doğukan AKA - NO:193405001   //  Berkay Ali KANDEMİR - NO:193405031
