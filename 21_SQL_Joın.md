# SQL JOIN İfadesinin Kullanımı ve Türleri

SQL’de **JOIN** ifadesi, iki veya daha fazla tabloyu birleştirmek için kullanılır. Veri tabanı tasarımında, veriler çeşitli tablolara ayrılarak düzenlenir. Ancak bu tablolarda tek başına anlamlı bir bilgi bulunmayabilir. Tablo birleştirme (JOIN) işlemi sayesinde, birleştirilen tablolardan anlamlı veri elde edilebilir.

## JOIN İfadesinin Temel Yapısı

JOIN ifadesinin genel yapısı şu şekildedir:

```sql
SELECT [kolon_ad1], [kolon_ad2], ...
FROM [tablo1] T1
[JOIN_TÜR] [tablo2] T2
ON T1.[id] = T2.[id];

```

### Açıklaması:

- **[tablo1]** ve **[tablo2]**: Birleştirilecek tablolardır.
- **T1** ve **T2**: Tabloya verilen takma isimlerdir (alias). Tabloların daha kolay okunabilmesi için kullanılır.
- **[JOIN_TÜR]**: Kullanılacak JOIN türünü belirtir. Bu, tablolardan hangi satırların birleştirileceğini belirler.
- **ON**: Tabloyu birleştirirken kullanılacak koşul. Genellikle iki tablonun ortak bir alanı üzerinden eşleştirme yapılır.

## JOIN Türleri

SQL’de birkaç farklı JOIN türü bulunur ve her biri, tablolardan hangi satırların birleştirileceğini belirler.

### 1. **INNER JOIN** (İç Birleştirme)

**INNER JOIN**, yalnızca her iki tabloda da bulunan ve eşleşen kayıtları getirir. Yani, iki tablodan yalnızca koşula uyan satırlar birleştirilir.

```sql

SELECT KISILER.ad, KITAPLAR.kategori
FROM KISILER K
INNER JOIN KITAPLAR KI ON K.ID = KI.kisi_id;

```

Bu sorgu, **KISILER** ve **KITAPLAR** tablolarını **kisi_id** ile birleştirir ve yalnızca her iki tabloda da karşılık gelen **kisi_id** değeri bulunan kayıtları döndürür.

### 2. **LEFT JOIN** (Sol Dış Birleştirme)

**LEFT JOIN** veya **LEFT OUTER JOIN**, sol tablodaki tüm kayıtları getirir ve sağ tablodan yalnızca eşleşen kayıtları döndürür. Eğer sağ tablodan bir eşleşme bulunmazsa, sağ tablonun tüm sütunları için **NULL** değerler döndürülür.

```sql
SELECT KISILER.ad, KITAPLAR.kategori
FROM KISILER K
LEFT JOIN KITAPLAR KI ON K.ID = KI.kisi_id;

```

Bu sorgu, **KISILER** tablosundaki tüm kişileri döndürecektir. Eğer bir kişinin kitabı yoksa, o kişinin **kategori** alanı **NULL** olacaktır.

### 3. **RIGHT JOIN** (Sağ Dış Birleştirme)

**RIGHT JOIN** veya **RIGHT OUTER JOIN**, sağ tablodaki tüm kayıtları getirir ve sol tablodan yalnızca eşleşen kayıtları döndürür. Eğer sol tablodan bir eşleşme bulunmazsa, sol tablonun tüm sütunları için **NULL** değerler döndürülür.

```sql
SELECT KITAPLAR.kategori, KISILER.ad
FROM KITAPLAR KI
RIGHT JOIN KISILER K ON K.ID = KI.kisi_id;

```

Bu sorgu, **KITAPLAR** tablosundaki tüm kitapları döndürecektir. Eğer bir kitabın yazarı yoksa (yani **kisi_id** değeri **NULL** olan kitaplar varsa), **ad** sütununda **NULL** değeri olacaktır.

### 4. **FULL OUTER JOIN** (Tam Dış Birleştirme)

**FULL OUTER JOIN**, her iki tablodaki tüm kayıtları döndürür. Eşleşmeyen satırlar için **NULL** değerleri gösterilir. Hem sol tablodan hem de sağ tablodan eşleşmeyen kayıtlar döndürülür.

```sql
SELECT KISILER.ad, KITAPLAR.kategori
FROM KISILER K
FULL OUTER JOIN KITAPLAR KI ON K.ID = KI.kisi_id;

```

Bu sorgu, **KISILER** ve **KITAPLAR** tablolarındaki tüm kayıtları döndürür. Eğer bir kişi kitabı yoksa veya bir kitap yazarı yoksa, o sütun için **NULL** değeri döndürülür.

## NULL Değerler ve JOIN’ler

**NULL** değerleri, bir kaydın bir alanda veri içermediği durumu belirtir. JOIN işlemlerinde NULL değerler, özellikle **LEFT JOIN**, **RIGHT JOIN** ve **FULL OUTER JOIN** türlerinde önemli rol oynar.

### NULL ve LEFT JOIN:

Bir **LEFT JOIN** sorgusunda, sağ tablodan eşleşen bir satır bulunmadığında, sol tablodaki satır ile ilgili sağ tablonun sütunlarında **NULL** değeri gösterilir. Bu, veri eksikliklerinin belirlenmesine yardımcı olur.

```sql
SELECT KISILER.ad, KITAPLAR.kategori
FROM KISILER K
LEFT JOIN KITAPLAR KI ON K.ID = KI.kisi_id;

```

Eğer **KISILER** tablosunda bir kişi varsa, ancak bu kişinin bir kitabı yoksa, **kategori** sütununda **NULL** değeri yer alacaktır.

### NULL ve RIGHT JOIN:

Bir **RIGHT JOIN** sorgusunda, sol tablodan eşleşen bir satır bulunmadığında, sağ tablodaki satır ile ilgili sol tablonun sütunlarında **NULL** değeri gösterilir.

```sql
SELECT KITAPLAR.kategori, KISILER.ad
FROM KITAPLAR KI
RIGHT JOIN KISILER K ON K.ID = KI.kisi_id;

```

Eğer **KITAPLAR** tablosunda bir kitap varsa, ancak bu kitabın yazarı **KISILER** tablosunda bulunmuyorsa, **ad** sütununda **NULL** değeri yer alacaktır.

&nbsp;

**\*\*****ÖZETLE****\*\***

- **JOIN**, SQL’de iki veya daha fazla tabloyu birleştirmek için kullanılır.
- **INNER JOIN**: Her iki tablodan eşleşen kayıtları getirir.
- **LEFT JOIN**: Sol tablodaki tüm kayıtları ve sağ tablodan eşleşen kayıtları döndürür; eşleşmeyen sağ tablonun sütunları **NULL** olur.
- **RIGHT JOIN**: Sağ tablodaki tüm kayıtları ve sol tablodan eşleşen kayıtları döndürür; eşleşmeyen sol tablonun sütunları **NULL** olur.
- **FULL OUTER JOIN**: Hem sol hem de sağ tablodaki tüm kayıtları döndürür; eşleşmeyen kayıtlar için **NULL** değeri gösterilir.
- **NULL değerler** JOIN işlemlerinde özellikle dış birleştirme türlerinde önemli bir rol oynar ve eksik verileri belirtir.
