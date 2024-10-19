## **# SQL'de GROUP BY İfadesinin Kullanımı**

SQL'de `GROUP BY` ifadesi, belirli bir sütundaki verileri gruplamak için kullanılır. Bu, aynı değere sahip kayıtların bir araya getirilmesini ve bu gruplar üzerinde toplama, ortalama gibi fonksiyonların uygulanmasını sağlar. `GROUP BY` ifadesinin temel yapısı aşağıdaki gibidir:

```
SELECT [alan1], [alan2], ... FROM [tablo adı]
GROUP BY [sütun1], [sütun2], ...;
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **[alan1], [alan2], ...**: Seçmek istediğiniz sütunlar. Gruplamak için kullanılan sütunlar `GROUP BY` ifadesinde belirtilmelidir.
- **[sütun1], [sütun2], ...**: Kayıtların gruplandığı sütunlar.

## Örnek Kullanım

```
SELECT departman, AVG(maas) AS Ortalama_Maas
FROM personel GROUP BY departman;
```

Bu sorgu, `personel` tablosundaki her departman için maaş ortalamalarını döndürür.

```
SELECT kategori, SUM(satis_miktari) AS Toplam_Satis
FROM urunler GROUP BY kategori;
```

Bu sorgu, `urunler` tablosundaki her kategori için toplam satış miktarlarını getirir.

```
SELECT musteri_id, SUM(tutar) AS Toplam_Tutar
FROM siparisler GROUP BY musteri_id;
```

Bu sorgu, `siparisler` tablosundaki her müşteri için toplam sipariş tutarını döndürür.

&nbsp;

**_ÖZETLE_**

- **GROUP BY**, belirli bir sütundaki verileri gruplamak için kullanılır.
- Aynı değere sahip kayıtları bir araya getirir ve gruplar üzerinde toplama, ortalama gibi fonksiyonların uygulanmasına olanak tanır.
