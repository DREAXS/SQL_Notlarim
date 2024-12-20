# **SQL'de Fonksiyonlar**

SQL'de **Fonksiyonlar**, belirli bir işlem yapmak için kullanılan ve bir değer döndüren özel sorgulardır. Bir fonksiyon, SQL Server'da belirli bir işlevi yerine getirebilmek için yazılır ve genellikle **veritabanı işlemleri**, **hesaplamalar** veya **veri dönüşümleri** için kullanılır. Fonksiyonlar, **dış sorgular** içinde kullanılabilir ve sorguların daha modüler ve yeniden kullanılabilir olmasını sağlar.

## FONKSİYON ÇEŞİTLERİ

- 1.Geriye sabit değer döndüren fonksiyonlar
- 2.Geriye Sorgu döndüren fonksiyonlar
- 3.Geriye tablo değişkeni döndüren fonksiyonlar

## Geriye Sorgu Döndüren Fonksiyonlar

```sql
CREATE FUNCTION fonksiyon_adi
(
  -- Parametrelerin eklendiği yer
  @param1 veritürü,
  @param2 veritürü
)
RETURNS TABLE  -- Bu fonksiyonun bir tablo döndüreceğini belirtir
AS
RETURN
(
  -- Burada geriye dönecek olan SELECT sorgusunu yazıyoruz
  SELECT kolon1, kolon2
  FROM tablo_adı
  WHERE kolon1 = @param1 AND kolon2 = @param2
);

```

### **AÇIKLAMASI**

- **CREATE FUNCTION fonksiyon_adi**: Fonksiyonun oluşturulacağı komut.
- **@param1**, **@param2**: Fonksiyona dışarıdan gönderilecek parametreler.
- **RETURNS TABLE**: Fonksiyonun bir tablo döndüreceğini belirtir.
- **RETURN (SELECT ...)**: Fonksiyonun içinde, dönecek olan sorgu yazılır. Bu sorgu bir veya birden fazla satır döndürebilir.

## Örnek SQL Sorgusu

```sql
CREATE FUNCTION GetKitaplarByKategori
(
  @kategori NVARCHAR(50)  -- Parametre olarak kategori alıyoruz
)
RETURNS TABLE  -- Bu fonksiyon tablo döndürecek
AS
RETURN
(
  SELECT KitapAdi, Yazar, Fiyat
  FROM KITAPLAR
  WHERE Kategori = @kategori
);
```

&nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
