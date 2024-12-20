## **# SQL'de COUNT Fonksiyonunun Kullanımı**

SQL'de `COUNT` fonksiyonu, belirli bir sütundaki veya tüm kayıtların sayısını hesaplamak için kullanılır. Bu, veri setindeki kayıtların miktarını hızlı bir şekilde öğrenmek için oldukça faydalıdır. `COUNT` fonksiyonunun temel yapısı aşağıdaki gibidir:

```sql
SELECT COUNT([alan]) FROM [tablo adı];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **[alan]**: Saymak istediğiniz sütun. Eğer tüm kayıtları saymak istiyorsanız, `*` kullanabilirsiniz.

## Örnek Kullanım

```sql
SELECT COUNT(*) FROM personel;
```

Bu sorgu, `personel` tablosundaki toplam çalışan sayısını getirir.

```sql
SELECT COUNT(*) FROM personel WHERE departman = 'IT';
```

Bu sorgu, `personel` tablosunda departmanı 'IT' olan çalışanların sayısını döndürür.

```sql
SELECT COUNT(DISTINCT departman) FROM personel;
```

Bu sorgu, `personel` tablosundaki farklı departman sayısını hesaplar.

&nbsp;

**_ÖZETLE_**

- **COUNT**, belirli bir sütundaki veya tüm kayıtların sayısını hesaplamak için kullanılır.
- **COUNT** fonksiyonu, belirli koşullarla birlikte kullanılarak daha spesifik sayım işlemleri gerçekleştirebilir.
  &nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
