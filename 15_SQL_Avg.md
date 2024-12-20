## **# SQL'de AVG Fonksiyonunun Kullanımı**

SQL'de `AVG` fonksiyonu, belirli bir sütundaki sayıların ortalamasını hesaplamak için kullanılır. Genellikle sayısal veri tipindeki sütunlar üzerinde çalışır ve bir sorguda toplu veri analizine olanak tanır. `AVG` fonksiyonunun temel yapısı aşağıdaki gibidir:

```sql
SELECT AVG([alan]) FROM [tablo adı];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **[alan]**: Ortalama değerini hesaplamak istediğiniz sütun.

## Örnek Kullanım

```sql
SELECT AVG(maas) FROM personel;
```

Bu sorgu, `personel` tablosundaki tüm çalışanların maaşlarının ortalamasını getirir.

```sql
SELECT AVG(maas) FROM personel WHERE departman = 'IT';
```

Bu sorgu, `personel` tablosunda departmanı 'IT' olan çalışanların maaşlarının ortalamasını hesaplar.

```sql
SELECT AVG(maas) FROM personel WHERE yas > 30 AND departman = 'Pazarlama';
```

Bu sorgu, yaşı 30'dan büyük ve departmanı 'Pazarlama' olan çalışanların maaş ortalamasını getirir.

&nbsp;

**_ÖZETLE_**

- **AVG**, belirli bir sütundaki sayıların ortalamasını hesaplamak için kullanılır.
- Genellikle sayısal veri tipleri üzerinde çalışır ve toplu veri analizi için faydalıdır.
- **AVG** fonksiyonu, belirli koşullarla birlikte kullanılarak daha spesifik ortalama hesaplamalarına olanak tanır.
  &nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
