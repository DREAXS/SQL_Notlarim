# **SQL'de Fonksiyonlar**

SQL'de **Fonksiyonlar**, belirli bir işlem yapmak için kullanılan ve bir değer döndüren özel sorgulardır. Bir fonksiyon, SQL Server'da belirli bir işlevi yerine getirebilmek için yazılır ve genellikle **veritabanı işlemleri**, **hesaplamalar** veya **veri dönüşümleri** için kullanılır. Fonksiyonlar, **dış sorgular** içinde kullanılabilir ve sorguların daha modüler ve yeniden kullanılabilir olmasını sağlar.

## FONKSİYON ÇEŞİTLERİ

- 1.Geriye sabit değer döndüren fonksiyonlar
- 2.Geriye Sorgu döndüren fonksiyonlar
- 3.Geriye tablo değişkeni döndüren fonksiyonlar

## Geriye Tablo Döndüren Fonksiyonlar

```sql

CREATE FUNCTION fonksiyon_adi
(
  -- Parametrelerin eklendiği yer
  @param1 veritürü,
  @param2 veritürü
)
RETURNS
@tablo TABLE
(
  -- Tablo değişkeninin kolonlarını burada tanımlıyoruz
  kolon1 veritürü,
  kolon2 veritürü
)
AS
BEGIN
  -- Tablo değişkenine veri eklemek için INSERT INTO kullanılır
  INSERT INTO @tablo
  SELECT kolon1, kolon2
  FROM tablo_adı
  WHERE kolon1 = @param1 AND kolon2 = @param2;

  -- Fonksiyon sonunda, tabloyu döndürüyoruz
  RETURN;
END;

```

### **AÇIKLAMASI**

- **@tablo TABLE**: Fonksiyonun döndüreceği tabloyu tanımlar. Burada, fonksiyonun döndüreceği tablonun kolonları ve veri türleri belirtilir.
- **INSERT INTO @tablo**: Bu komut, fonksiyon içinde işlem yapılırken **@tablo** adlı geçici tabloya veriler ekler.
- **RETURN**: Fonksiyonun sonunda **@tablo** değişkeni, döndürülecek tabloyu içerdiği için fonksiyonun sonunda **RETURN** komutu kullanılır. SQL Server, bu tabloyu fonksiyonun sonucu olarak döndürecektir.

## Örnek SQL Sorgusu

```sql
CREATE FUNCTION GetKitaplarBySatisMiktari
(
  @minSatis INT  -- Parametre olarak minimum satış miktarı alıyoruz
)
RETURNS
@tablo TABLE  -- Döndürülecek tabloyu tanımlıyoruz
(
  KitapAdi NVARCHAR(100),
  Yazar NVARCHAR(100),
  SatisMiktari INT
)
AS
BEGIN
  -- Tabloyu belirli bir satış miktarına göre dolduruyoruz
  INSERT INTO @tablo
  SELECT KitapAdi, Yazar, SatisMiktari
  FROM KITAPLAR
  WHERE SatisMiktari > @minSatis;

  -- Fonksiyon sonunda, tabloyu döndürüyoruz
  RETURN;
END;

```
