## **# SQL'de DISTINCT İfadesinin Kullanımı**

SQL'de `DISTINCT` ifadesi, sorgu sonuçlarında tekrar eden kayıtları kaldırarak yalnızca birbirinden farklı (eşsiz) verileri görüntülemek için kullanılır. Bu, veri setlerinde yinelenen değerlerin önüne geçer ve daha anlamlı sonuçlar elde etmenizi sağlar. `DISTINCT` ifadesinin temel yapısı aşağıdaki gibidir:

```sql
SELECT DISTINCT [alan1], [alan2], ... FROM [tablo adı];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **([alan1], [alan2]...)**: Seçmek istediğiniz sütunlar.

## Örnek Kullanım

```sql
SELECT DISTINCT departman FROM personel;
```

Bu sorgu, `personel` tablosundaki birbirinden farklı departman isimlerini getirir.

```sql
SELECT DISTINCT maas FROM personel;
```

Bu sorgu, `personel` tablosundaki farklı maaş değerlerini döndürür.

```sql
SELECT DISTINCT isim, departman FROM personel;
```

Bu sorgu, her isim ve departman kombinasyonunun kayıtlarını gösterir.

**_ÖZETLE_**

- **DISTINCT**, sorgu sonuçlarında yalnızca benzersiz verileri görüntülemek için kullanılır.
- Tekrar eden kayıtları kaldırarak daha anlamlı ve temiz sonuçlar elde etmenizi sağlar.
- **DISTINCT** ifadesi, bir veya daha fazla sütun için uygulanabilir.
