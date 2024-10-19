## **# SQL'de BETWEEN Yapısının Kullanımı**

SQL'de `BETWEEN` yapısı, bir sütundaki verilerin belirli bir aralıkta olup olmadığını kontrol etmek için kullanılır. Bu, genellikle tarih veya sayısal veriler için aralık sorgulamaları yapmak için kullanılır. `BETWEEN` ifadesinin temel yapısı aşağıdaki gibidir:

```
SELECT [alan1], [alan2], ... FROM [tablo adı]
 WHERE [alan] BETWEEN [değer1] AND [değer2];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **[alan]**: Karşılaştırma yapmak istediğiniz sütun.
- **[değer1]**: Aralığın alt sınırı.
- **[değer2]**: Aralığın üst sınırı.

## Örnek Kullanım

```
SELECT * FROM siparisler WHERE siparis_tarihi
BETWEEN '2024-01-01' AND '2024-12-31';

```

Bu sorgu, 2024 yılı içindeki tüm sipariş kayıtlarını getirir.

```
SELECT * FROM personel WHERE yaş BETWEEN 25 AND 35;
```

Bu sorgu, yaşı 25 ile 35 arasında olan tüm personel kayıtlarını getirir.

```
SELECT * FROM personel WHERE maas BETWEEN 40000 AND 60000;
```

Bu sorgu, maaşı 40.000 ile 60.000 arasında olan tüm personel kayıtlarını getirir.

**_ÖZETLE_**

- **BETWEEN**, belirli bir sütundaki verilerin, belirtilen bir aralıkta olup olmadığını kontrol etmek için kullanılır.
- Aralık belirlemek için etkili bir yöntem sunar ve sorguları daha okunabilir hale getirir.
- **BETWEEN** ifadesi, hem alt hem de üst sınırları dahil ederek sorgulama yapar.
