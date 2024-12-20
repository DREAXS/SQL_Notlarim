## **# SQL'de ORDER BY ve TOP Komutlarının Kullanımı**

**ORDER BY**: SQL'de `ORDER BY` ifadesi, sorgu sonuçlarını belirli bir sütuna göre sıralamak için kullanılır. Sonuçlar, artan (ASC) veya azalan (DESC) sırada düzenlenebilir. `ORDER BY` ifadesinin temel yapısı aşağıdaki gibidir:

```sql
SELECT [alan1], [alan2], ... FROM [tablo adı]
ORDER BY [sütun1] [ASC|DESC];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **([alan1], [alan2]...)**: Seçmek istediğiniz sütunlar.
- **[sütun1]**: Sıralamak istediğiniz sütun
- **ASC**: Artan sıralama (varsayılan).
- **DESC**: Azalan sıralama.

## Örnek Kullanım

```sql
SELECT * FROM personel ORDER BY maas DESC;
```

Bu sorgu, `personel` tablosundaki kayıtları maaşa göre azalan sırada getirir.

```sql
SELECT * FROM personel ORDER BY isim ASC;
```

Bu sorgu, `personel` tablosundaki kayıtları isme göre artan sırada listeler.

&nbsp;

**TOP**: SQL'de `TOP` ifadesi, sorgu sonuçlarından yalnızca belirli sayıda kaydı almak için kullanılır. Genellikle büyük veri setlerinde performansı artırmak için kullanılır. `TOP` ifadesinin temel yapısı aşağıdaki gibidir:

```sql
SELECT TOP [n] [alan1], [alan2], ... FROM [tablo adı];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **([alan1], [alan2]...)**: Seçmek istediğiniz sütunlar.
- **[n]**: Almak istediğiniz kayıt sayısı.

## Örnek Kullanım

```sql
SELECT TOP 5 * FROM personel;
```

Bu sorgu, `personel` tablosundaki ilk 5 kaydı getirir.

```sql
SELECT TOP 3 * FROM personel ORDER BY maas DESC;
```

Bu sorgu, `personel` tablosundaki en yüksek maaşa sahip 3 çalışanı listeler.

**_ÖZETLE_**

- **ORDER BY**, sorgu sonuçlarını belirli bir sütuna göre sıralamak için kullanılır
- **TOP**, sorgu sonuçlarından yalnızca belirli sayıda kaydı almak için kullanılır
- **ORDER BY** ifadesi, sıralama yaparak verileri daha düzenli hale getirirken, **TOP** ifadesi ise performansı artırmak için veri miktarını sınırlamaya yardımcı olur.
  &nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
