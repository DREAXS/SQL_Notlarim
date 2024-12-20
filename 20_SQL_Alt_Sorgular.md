# İç İçe Sorgular (Alt Sorgular) ve Kullanımı

SQL’de **İç İçe Sorgular** veya **Alt Sorgular** (subqueries), başka bir SQL sorgusunun içinde yer alan sorgulardır. Bu sorgular, genellikle veri filtreleme, belirli bir koşulu sağlamadaki yardımcı işlemler veya başka tablolardan veri çekme amacıyla kullanılır. İç içe sorgular, ana sorgunun (dış sorgu) bir parçası olarak çalışır ve genellikle `WHERE`, `FROM`, `SELECT`, ya da `HAVING` gibi ifadelerle kullanılır.

## İç İçe Sorguların Temel Yapısı

Bir iç içe sorgunun temel yapısı şu şekildedir:

```sql
SELECT [kolon_adı1], [kolon_adı2], ...
FROM [üst_tablo]
WHERE [kolon_adı] [operatör]
  (SELECT [kolon_adı1], [kolon_adı2], ...
   FROM [alt_tablo]
   WHERE [koşul]);

```

### Açıklaması:

- **[üst_tablo]**: Ana sorgunun çalıştığı tablo
- **[alt_tablo]**: İç sorgunun çalıştığı tablo
- **[operatör]**: `=`, `IN`, `NOT IN`, `ANY`, `ALL` gibi karşılaştırma operatörleri. İç sorgu ile dış sorgu arasındaki ilişkiyi belirler
- İç sorgu, dış sorgudan önce çalışır ve sonuçlarını dış sorguya aktarır.

## Örnek Kullanım

### 1. **Basit İç İçe Sorgu Kullanımı**

Aşağıdaki sorguda, `YAZARLAR` tablosundaki bir yazara ait bilgileri almak için, yazarın yazdığı kitaplardan **kategori** ve **baskı sayısı** 'na göre filtreleme yapılmaktadır.

```sql
SELECT *
FROM YAZARLAR AS K
WHERE K.ID =
  (SELECT KT.YZ_ID
   FROM KITAPLAR AS KT
   WHERE KT.Kategori = 'Roman'
     AND KT.BASKI_SAYISI = '8');

```

Bu sorgu, **Roman** kategorisinde 8. baskısı yapılan kitabı yazan yazarı sorgulamaktadır. İç sorgu (`SELECT KT.YZ_ID FROM KITAPLAR AS KT WHERE KT.Kategori = 'Roman' AND KT.BASKI_SAYISI = '8'`) yazara ait ID’yi bulur, dış sorgu ise bu ID’ye sahip yazarı getirir.

### 2. **IN Operatörü ile İç İçe Sorgu Kullanımı**

Birden fazla yazara ait kitapları belirli bir kategoriye göre seçmek istiyorsak, iç sorguyu `IN` operatörüyle kullanabiliriz.

```sql
SELECT ISIM, ULKE, YAS
FROM YAZARLAR AS K
WHERE K.ID IN
  (SELECT KT.YZ_ID
   FROM KITAPLAR AS KT
   WHERE KT.Kategori = 'Kişisel Gelişim');

```

Bu sorgu, **Kişisel Gelişim** kategorisinde kitap yazan tüm yazarları listeleyecektir. İç sorgu birden fazla satır döndürebileceğinden, dış sorgu bu satırları `IN` operatörüyle karşılaştırarak uygun yazarları getirir.

### 3. **ANY ve ALL Operatörleri ile İç İçe Sorgu Kullanımı**

`ANY` ve `ALL` operatörleri, alt sorgudan dönen bir dizi değeri karşılaştırmak için kullanılır. Bu operatörlerle daha esnek sorgular yazabiliriz.

**ANY Operatörü:**

```sql
SELECT ISIM, YAS
FROM YAZARLAR
WHERE YAS > ANY
  (SELECT YAS FROM YAZARLAR WHERE ULKE = 'Türkiye');

```

Bu sorgu, **Türkiye**’deki herhangi bir yazardan daha yaşlı olan yazarları listeleyecektir. İç sorgu, Türkiye’deki yazarlardan yaş bilgilerini döndürecek, dış sorgu ise bu yaşlardan herhangi birinden büyük olan yazarları seçecektir.

**ALL Operatörü:**

```sql
SELECT ISIM, YAS
FROM YAZARLAR
WHERE YAS > ALL
  (SELECT YAS FROM YAZARLAR WHERE ULKE = 'Türkiye');

```

Bu sorgu ise, **Türkiye**’deki tüm yazarlardan daha yaşlı olan yazarları listeleyecektir. İç sorgu tüm Türkiye'deki yazarlardan yaşları döndürecek, dış sorgu ise bu yaşlardan her birinden büyük olan yazarları filtreleyecektir.

### 4. **FROM Tümcesinde İç İçe Sorgu Kullanımı**

İç sorgular sadece `WHERE` ifadesinde kullanılmakla sınırlı değildir. Bazen `FROM` ifadesinde de iç içe sorgulara ihtiyaç duyulabilir. Bu, bir alt sorgudan dönen sonuçları geçici bir tablo gibi kullanmak için yaygın bir tekniktir.

```sql
SELECT A.kategori, A.toplam_satis
FROM
  (SELECT kategori, SUM(satis_miktari) AS toplam_satis
   FROM urunler
   GROUP BY kategori) AS A
WHERE A.toplam_satis > 1000;

```

Bu örnekte, iç sorgu (`SELECT kategori, SUM(satis_miktari) FROM urunler GROUP BY kategori`) her kategori için toplam satış miktarını hesaplar ve dış sorgu bu sonuçları filtreleyerek 1000'in üzerinde satış yapan kategorileri getirir.

### 5. **HAVING ile İç İçe Sorgu Kullanımı**

`HAVING` ifadesi, `GROUP BY` ile gruplanmış veriler üzerinde koşul koymak için kullanılır. İç içe sorgular, gruplanmış verilere uygulanan filtreler için de kullanılabilir.

```sql
SELECT departman, AVG(maas) AS Ortalama_Maas
FROM personel
GROUP BY departman
HAVING AVG(maas) >
  (SELECT AVG(maas) FROM personel WHERE departman = 'IT');

```

Bu sorgu, **IT** departmanındaki maaş ortalamasından yüksek maaş ortalamasına sahip departmanları getirir.

&nbsp;

**\*\*\*\***ÖZETLE\***\*\*\***

- **İç İçe Sorgular**, başka bir SQL sorgusunun içinde yer alan sorgulardır ve genellikle `WHERE`, `FROM`, `SELECT`, `HAVING` gibi ifadelerde kullanılır.
- **IN, ANY, ALL** gibi operatörler ile iç sorgulardan dönen sonuçlar arasında karşılaştırmalar yapılabilir.
- **HAVING** ve **GROUP BY** ifadeleri ile gruplanmış verilere filtre uygulamak için de iç içe sorgular kullanılabilir.
- İç sorgular, dış sorgudan önce çalışır ve sonuçlarını dış sorguya aktarır.
  &nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
