# SQL Veri Tipleri

Aşağıda SQL'de kullanılan temel veri tipleri ve açıklamaları bulunmaktadır.

## Karakter Veri Tipleri

- **CHAR**

  - Unicode olmayan sabit uzunlukta karakter verisi saklar.
  - En fazla 8000 karakter veri saklayabilir.

- **VARCHAR**

  - Unicode olmayan değişken uzunlukta karakter verisi saklar.
  - Belirlenmiş veri kapasitesi 8000 karakterdir.

- **NCHAR**

  - Sabit uzunlukta 4000 karakter Unicode karakter verisi saklar.
  - Kısa olan değerler atanan uzunluğa tamamlanır.

- **NVARCHAR**
  - Değişken uzunlukta Unicode karakter verisi saklar.
  - Belirlenmiş maksimum uzunluk 4000 karakterdir.

## Sayısal Veri Tipleri

- **BIT**

  - 1 byte uzunluğunda tamsayı veri tipidir.
  - Tablodaki ilk bit bir byte büyüklüğünde yer kaplar, sonraki yedi bit aynı byte’ı kullanabilir.

- **TINYINT**

  - 1 byte büyüklüğünde, 0 ile 255 arasında değer alabilen tamsayı veri tipidir.

- **SMALLINT**

  - 2 byte büyüklüğünde, -32768 ile 32767 arasında değer alabilen tamsayı veri tipidir.

- **INT**

  - 4 byte büyüklüğünde, yaklaşık -2 milyar ile +2 milyar arasında değer alabilen tamsayı veri tipidir.

- **BIGINT**

  - 8 byte büyüklüğünde, -2^63 ile +2^63 arasında değer alabilen tamsayı veri tipidir.

- **DECIMAL ve NUMERIC**

  - Decimal ve numeric veri tipleri adları farklı olmasına rağmen kullanımları aynıdır.
  - Boyutu değişken olup, -10^38 ile +10^38 arasında ondalık ve tamsayı türünde verileri saklayabilir.

- **FLOAT**
  - Boyutu ve doğruluğu (ondalık kısım duyarlılığı) aldığı parametreye göre değişen kayan noktalı sayılar için kullanılır.

## Tarih ve Zaman Veri Tipleri

- **DATE**

  - Tarihleri YYYY-MM-DD formatında saklayan 3 byte uzunluğunda veri tipidir.
  - 0001-01-01 ile 9999-12-31 tarihleri arasındaki tüm değerleri tutabilir.

- **DATETIME**
  - YYYY-MM-DD hh:mm:ss.mmm formatında tarih ve zaman verilerini tutan 8 byte uzunluğunda veri tipidir.
  - 1753-01-01 00:00:00.000 ile 9999-12-31 23:59:59.999 arası değerlerini saklar.

## Binary Veri Tipleri

- **BINARY**
  - Maksimum 8000 byte boyutunda, sabit uzunlukta binary veri saklamak için kullanılır.
