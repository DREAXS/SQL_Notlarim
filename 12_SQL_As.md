## **# SQL'de AS İfadesinin Kullanımı**

SQL'de `AS` ifadesi, bir sütuna veya tabloya takma ad (alias) vermek için kullanılır. Bu, sorgu sonuçlarının daha okunabilir olmasını sağlar ve daha anlamlı isimler kullanmanızı sağlar. `AS` ifadesinin temel yapısı aşağıdaki gibidir:

```
SELECT [alan1] AS [takma_ad], [alan2] AS [takma_ad] FROM [tablo adı];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **([alan1], [alan2]...)**: Seçmek istediğiniz sütunlar.
- **AS [takma_ad]**: Seçilen sütun veya tablo için belirlediğiniz takma ad.

## Örnek Kullanım

```
SELECT isim AS Çalışan_İsmi, maas AS Çalışan_Maaşı FROM personel;
```

Bu sorgu, isim sütununu "Çalışan_İsmi" ve maaş sütununu "Çalışan_Maaşı" olarak gösterir.

```
SELECT * FROM personel AS p;
```

Bu sorgu, `personel` tablosuna "p" takma adını verir. Sonraki sorgularda "p" kullanılarak tabloya referans verilebilir.

```
SELECT (maas * 12) AS Yıllık_Maaş FROM personel;
```

Bu sorgu, çalışanların yıllık maaşlarını "Yıllık_Maaş" adıyla gösterir.

**_ÖZETLE_**

- **AS**, bir sütuna veya tabloya takma ad vermek için kullanılır.
- Sonuçların daha okunabilir ve anlamlı olmasını sağlar
- **AS** ifadesi, sorgularda daha kısa ve anlaşılır referanslar kullanmanıza olanak tanır.
