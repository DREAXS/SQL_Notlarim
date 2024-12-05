# **SQL'de Fonksiyonlar**

SQL'de **Fonksiyonlar**, belirli bir işlem yapmak için kullanılan ve bir değer döndüren özel sorgulardır. Bir fonksiyon, SQL Server'da belirli bir işlevi yerine getirebilmek için yazılır ve genellikle **veritabanı işlemleri**, **hesaplamalar** veya **veri dönüşümleri** için kullanılır. Fonksiyonlar, **dış sorgular** içinde kullanılabilir ve sorguların daha modüler ve yeniden kullanılabilir olmasını sağlar.

## FONKSİYON ÇEŞİTLERİ

- 1.Geriye sabit değer döndüren fonksiyonlar
- 2.Geriye Sorgu döndüren fonksiyonlar
- 3.Geriye tablo değişkeni döndüren fonksiyonlar

## Geriye Sabit Değer Döndüren Fonksiyonlar

```sql
CREATE FUNCTION fonksiyon_adi
(
  -- Parametrelerin eklendiği yer
  @param1 veritürü,
  @param2 veritürü
)
RETURNS geri_dönecek_değerin_veritürü
AS
BEGIN
  -- Önce geri dönecek değeri tanımlarız.
  DECLARE @donen veritürü;

  -- Burada SQL ifadeleri ile işlem yapılarak @donen değişkenine değer atanır.
  SET @donen = ( -- Bu kısımda bir sorgu çalıştırılabilir veya hesaplama yapılabilir.
    SELECT COUNT(*)
    FROM bazı_tablo
    WHERE kolon_adı = @param1
  );

  -- Fonksiyonun sonunda, sonuç olarak dönecek olan değeri belirtiriz.
  RETURN @donen;
END;
```

### **AÇIKLAMASI**

- **CREATE FUNCTION**: Fonksiyon oluşturma komutudur.

  - `fonksiyon_adi`: Fonksiyonun adı.
  - `@param1`, `@param2`: Fonksiyona geçilen parametreler.
  - `RETURNS geri_dönecek_değerin_veritürü`: Fonksiyonun geri döneceği değerin veri türüdür.

- **BEGIN...END**: Fonksiyonun gövdesi. Burada SQL ifadeleri yazılır ve işlem yapılır.

- **DECLARE**: Fonksiyonda kullanılacak geçici değişkenler burada tanımlanır.

- **SET**: Değişkene değer atamak için kullanılır. Bu örnekte, `@donen` değişkenine bir SQL sorgusunun sonucu atanmıştır.

- **RETURN**: Fonksiyonun geri döndüreceği değer belirtilir.

## Örnek SQL Sorgusu

```sql
CREATE FUNCTION GetKitapSayisiByKategori
(
  @kategori NVARCHAR(50)  -- Parametre olarak kategori alıyoruz
)
RETURNS INT  -- Geri dönecek veri türü integer (kitap sayısı)
AS
BEGIN
  -- Kitap sayısını hesaplayan sorgu
  DECLARE @kitapSayisi INT;

  -- Kitap sayısını belirleyen sorgu
  SET @kitapSayisi = (
    SELECT COUNT(*)
    FROM KITAPLAR
    WHERE Kategori = @kategori
  );

  -- Kitap sayısını geri döndür
  RETURN @kitapSayisi;
END;

```
