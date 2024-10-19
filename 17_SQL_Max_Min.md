## **# SQL'de MAX ve MIN Fonksiyonlarının Kullanımı**

SQL'de `MAX` ve `MIN` fonksiyonları, belirli bir sütundaki en yüksek ve en düşük değerleri bulmak için kullanılır. `MAX` fonksiyonu, bir sütundaki en yüksek değeri döndürürken, `MIN` fonksiyonu o sütundaki en düşük değeri döndürür. Her iki fonksiyon da genellikle sayısal veya tarih verileri üzerinde kullanılır ve veri analizi için oldukça faydalıdır. `MAX` ve `MIN` fonksiyonlarının temel yapısı aşağıdaki gibidir:

```
SELECT MAX([alan]) FROM [tablo adı];
SELECT MIN([alan]) FROM [tablo adı];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **[alan]**: En düşük veya en büyük değeri bulmak istediğiniz sütun.

## Örnek Kullanım

```
SELECT MAX(maas) FROM personel;
```

Bu sorgu, `personel` tablosundaki en yüksek maaşı getirir.

```
SELECT MAX(bitis_tarihi) AS En_Gec_Bitis,
 MIN(bitis_tarihi) AS En_Erken_Bitis FROM projeler;
```

Bu sorgu, `projeler` tablosundaki en geç ve en erken bitiş tarihlerini getirir.

```
SELECT MAX(satis_miktari) AS En_Yuksek_Satis,
 MIN(satis_miktari) AS En_Dusuk_Satis FROM satislar;

```

Bu sorgu, `personel` tablosundaki farklı departman sayısını hesaplar.

&nbsp;

**_ÖZETLE_**

- **COUNT**, belirli bir sütundaki veya tüm kayıtların sayısını hesaplamak için kullanılır.
- **MIN**, belirli bir sütundaki en düşük değeri bulmak için kullanılır.
- Her iki fonksiyon da genellikle sayısal veya tarih verileri üzerinde çalışır ve belirli koşullarla birlikte kullanılarak daha spesifik değer bulma işlemlerine olanak tanır.
