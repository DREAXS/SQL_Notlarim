## **# SQL'de SUM Fonksiyonunun Kullanımı**

SQL'de `SUM` fonksiyonu, belirli bir sütundaki sayıların toplamını hesaplamak için kullanılır. Bu, genellikle finansal veriler veya sayısal veri analizleri için kullanışlıdır. `SUM` fonksiyonunun temel yapısı aşağıdaki gibidir:

```sql
SELECT SUM([alan]) FROM [tablo adı];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **[alan]**: Toplamını almak istediğiniz sütun.

## Örnek Kullanım

```sql
SELECT SUM(maas) FROM personel;
```

Bu sorgu, `personel` tablosundaki tüm çalışanların maaşlarının toplamını getirir.

```sql
SELECT SUM(maas) FROM personel WHERE departman = 'IT';
```

Bu sorgu, `personel` tablosunda departmanı 'IT' olan çalışanların maaşlarının toplamını döndürür.

```sql
SELECT SUM(tutar) FROM siparisler
WHERE siparis_tarihi BETWEEN '2023-01-01' AND '2023-12-31';
```

Bu sorgu, `siparisler` tablosunda 2023 yılındaki siparişlerin toplam tutarını döndürür.

&nbsp;

**_ÖZETLE_**

- **SUM**, belirli bir sütundaki sayıların toplamını hesaplamak için kullanılır.
- Finansal veriler veya sayısal veri analizleri için oldukça faydalıdır.
- **SUM** fonksiyonu, belirli koşullarla birlikte kullanılarak daha spesifik toplam hesaplamalarına olanak tanır.
  &nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
