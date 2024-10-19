## **# SQL'de IN Yapısının Kullanımı**

SQL'de `IN` yapısı, belirli bir sütundaki verilerin belirli bir liste içindeki değerlerle karşılaştırılmasını sağlar. Bu, birden fazla değeri kontrol etmek için pratik bir yol sunar. `IN` ifadesinin temel yapısı aşağıdaki gibidir:

```
SELECT [alan1], [alan2], ... FROM [tablo adı]
WHERE [alan] IN (değer1, değer2, ...);
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **[alan]**: Karşılaştırma yapmak istediğiniz sütun.
- **(değer1, değer2, ...)**: Kontrol etmek istediğiniz değerlerin listesidir.

## Örnek Kullanım

```
SELECT * FROM personel WHERE departman IN ('IT', 'Pazarlama', 'HR');
```

Bu sorgu, departmanı 'IT', 'Pazarlama' veya 'HR' olan tüm personel kayıtlarını getirir.

```
SELECT * FROM personel WHERE yaş IN (25, 30, 35);
```

Bu sorgu, yaşı 25, 30 veya 35 olan tüm personel kayıtlarını getirir.

```
SELECT * FROM siparisler WHERE durum IN ('Tamamlandı', 'Beklemede');
```

Bu sorgu, durumu 'Tamamlandı' veya 'Beklemede' olan tüm sipariş kayıtlarını getirir.

**_ÖZETLE_**

- **IN**, belirli bir sütundaki verilerin, belirli bir değer listesiyle karşılaştırılmasını sağlar.
- Birden fazla değeri kontrol etmek için kullanışlıdır ve sorguları daha okunabilir hale getirir.
- **IN** ifadesi, birden fazla değeri aynı anda kontrol etmek için etkili bir yöntem sunmaktadır.
