## **# SQL'de LIKE Komutunun Kullanımı**

SQL'de `LIKE` komutu, belirli bir kalıba uyan verileri sorgulamak için kullanılır. Özellikle metin sütunlarında, belirli bir dizeyi veya dize kalıbını aramak için kullanılabilir. `LIKE` komutunun temel yapısı aşağıdaki gibidir:

```
SELECT [alan1], [alan2], ... FROM [tablo adı]
WHERE [alan] LIKE [kalıp];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **[alan1], [alan2], .**: Seçmek istediğiniz sütunlar. Tüm sütunları seçmek için `*` kullanabilirsiniz.
- **[kalıp]**: Arama kriterlerini belirten dize. `%` ve `_` karakterleri özel anlam taşır

| **%**                                        | **\_**                                |
| -------------------------------------------- | ------------------------------------- |
| Sıfır veya daha fazla karakteri temsil eder. | Tam olarak bir karakteri temsil eder. |

## Örnek Kullanım

```
SELECT * FROM personel WHERE isim LIKE 'A%';
```

Bu sorgu, ismi 'A' harfi ile başlayan tüm personel kayıtlarını getirir.

```
SELECT * FROM personel WHERE isim LIKE '%an%';
```

Bu sorgu, ismi içinde "an" geçen tüm personel kayıtlarını getirir.

```
SELECT * FROM personel WHERE isim LIKE '%a';
```

Bu sorgu, ismi 'a' harfi ile biten tüm personel kayıtlarını getirir.

```
SELECT * FROM personel WHERE isim LIKE '_a%';
```

Bu sorgu, ismi ikinci karakteri 'a' olan tüm personel kayıtlarını getirir.

**_ÖZETLE_**

- **LIKE**, belirli bir kalıba uyan verileri sorgulamak için kullanılır.
- `%` ve `_` karakterleri, kalıp belirlemede önemli rol oynar.
- **LIKE** ifadesi, metin aramalarında esneklik sağlar ve daha spesifik sonuçlar elde etmenizi mümkün kılar.
