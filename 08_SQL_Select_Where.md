## **# SELECT VE WHERE Komutlarının Kullanımı**

SQL'de `SELECT` ve `WHERE` komutlarının kullanımı ile ilgili bir açıklama yapalım. `SELECT` komutu, veritabanından veri almak için kullanılırken, `WHERE` komutu bu verilerin filtrelenmesini sağlar. Komutun temel yapısı aşağıdaki gibidir.

```
SELECT [alan1], [alan2], ... FROM [tablo adı];
```

### Açıklaması:

- **[tablo adı]**: Sorgulamak istediğiniz verilerin bulunduğu tablonun adı.
- **[alan1], [alan2], .**: Seçmek istediğiniz sütunlar. Tüm sütunları seçmek için `*` kullanabilirsiniz.

## Örnek Kullanım

```
SELECT * FROM personel;
```

```
SELECT isim, maas FROM personel;
```

Yukarıdaki SQL sorgusu sadece isim ve maaş sütunlarını almak için kullanılır

&nbsp;

# WHERE KOŞULU

```
SELECT [alan1], [alan2], ... FROM [tablo adı] WHERE [koşul];
```

**\*[koşul]**: Hangi kayıtların seçileceğini belirten kriterlerdir. Örneğin, belirli bir ID veya yaş aralığı gibi.

```
SELECT * FROM personel WHERE ID = 65;
```

## Birden Fazla Koşul Kullanımı

Birden fazla koşul belirlemek için `AND` ve `OR` anahtar kelimelerini kullanabilirsiniz.

```
SELECT * FROM personel WHERE maas > 50000 AND departman = 'IT';
```

**_ÖZETLE_**

- **SELECT**: Belirli bir tablodan veri seçmek için kullanılır.
- **WHERE**: Hangi kayıtların seçileceğini belirlemek için kullanılır.
- WHERE ifadesi, filtreleme yaparak daha spesifik sonuçlar elde etmenizi sağlar.
