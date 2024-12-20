# **Trigger - Transaction 2 **

---

## **Trigger Kullanımı**

```sql
CREATE TRIGGER trg_SatisSonrasiStokGuncelle
ON Urunler
AFTER INSERT
AS
BEGIN
    -- Yeni ürün eklendikten sonra stok miktarını güncelleme
    UPDATE Stok
    SET Miktar = Miktar - 1
    WHERE UrunID IN (SELECT UrunID FROM inserted)
END

```

### _AÇIKLAMA_

1. **CREATE TRIGGER trg_SatisSonrasiStokGuncelle**: Yeni bir tetikleyici oluşturur. Adı `trg_SatisSonrasiStokGuncelle`.
2. **ON Urunler**: Tetikleyici **Urunler** tablosuna eklenen verilerle çalışacak.
3. **AFTER INSERT**: Bu tetikleyici, **Urunler** tablosuna yeni bir ürün eklendikten sonra çalışacak.
4. **AS BEGIN...END**: Tetikleyici içindeki SQL komutlarını belirler.
5. **UPDATE Stok SET Miktar = Miktar - 1**: **Stok** tablosunda, eklenen ürüne ait stok miktarını 1 azaltır.
6. **WHERE UrunID IN (SELECT UrunID FROM inserted)**: Yeni eklenen ürünün **UrunID**'sini alır ve ilgili stok miktarını günceller.

<$>[note]
**!!!  `inserted`**, veritabanına eklenen yeni verileri (ya da güncellenen verilerin yeni hallerini) tutan bir sanal tablodur.
<$>

```sql
INSERT INTO Urunler (UrunID, UrunAdi, Fiyat)
VALUES (101, 'Telefon', 1500)

```

- Bu **INSERT** komutunun çalışması ile **Urunler** tablosuna bir ürün eklenecek ve tetikleyici (`trg_SatisSonrasiStokGuncelle`) devreye girerek, **Stok** tablosundaki ilgili ürünün stok miktarını 1 azaltacaktır.

---

## **Trigger Örnek**

```sql
CREATE TRIGGER silMusteri
ON musteri
FOR DELETE
AS
BEGIN
    -- Silinen müşteri verilerini tutmak için değişkenler tanımlıyoruz
    DECLARE @id INT;
    DECLARE @ad NCHAR(10);
    DECLARE @adres NCHAR(10);
    DECLARE @sehir NCHAR(10);
    DECLARE @puan DECIMAL(18,0);

    -- Silinen müşteri bilgilerini 'deleted' tablosundan alıyoruz
    SELECT @id = MusteriID,
           @ad = MusteriAd,
           @adres = MusteriAdres,
           @sehir = Sehir,
           @puan = Puan
    FROM deleted;

    -- Silinen müşteri verisini başka bir tabloya (deletedMusteri) ekliyoruz
    INSERT INTO deletedMusteri (MusteriID, MusteriAd, MusteriAdres, Sehir, Puan)
    VALUES (@id, @ad, @adres, @sehir, @puan);
END;

```

### _AÇIKLAMA_

1. **CREATE TRIGGER silMusteri** : silMusteri adlı bir tetikleyici oluşturulur bu tetikleyici, musteri tablosunda **DELETE** işlemi yapıldığında çalışır.
2. **FOR DELETE** : **DELETE** işlemi tetikleyiciyi başlatacak. Yani, **musteri** tablosundan bir satır silindiğinde bu tetikleyici devreye girer.
3. **DECLARE** : Silinen müşteri verilerini tutmak için 5 değişken tanımlanır : `@id` (MusteriID) `@ad` (MusteriAd) `@adres` (MusteriAdres) `@sehir` (Sehir) `@puan` (Puan)
4. **SELECT from deleted** : **`deleted`** sanal tablosu, silinen satırları içerir. Buradan müşteri bilgileri alınır ve daha önce tanımlanan değişkenlere atanır.
5. **INSERT INTO deletedMusteri** : **deletedMusteri** adında bir başka tabloya, silinen müşteri verileri eklenir. Bu işlem, müşteri silindiğinde, silinen verilerin yedeğini tutmak için yapılır.

```sql
SELECT * FROM deletedMusteri;
DELETE FROM musteri WHERE MusteriID = 3;
SELECT * FROM deletedMusteri;

```

1. **SELECT \* FROM deletedMusteri** : Bu, silinen müşteri bilgilerini görmek için kullanılır (trigger içinde yedeklenen veriler).
2. **DELETE FROM musteri WHERE MusteriID = 3** : **musteri** tablosunda **MusteriID**'si 3 olan satır silinir. Bu işlem **silMusteri** tetikleyicisini devreye sokar ve tetikleyici, silinen veriyi **deletedMusteri** tablosuna ekler.
3. **SELECT \* FROM deletedMusteri** : Bu, silinen müşteri verilerinin doğru bir şekilde **deletedMusteri** tablosuna eklenip eklenmediğini görmek için yapılır.

### _ÖZETLE_

- **Trigger**: **silMusteri** tetikleyicisi, **musteri** tablosundan bir müşteri silindiğinde devreye girer ve silinen müşteri verilerini **deletedMusteri** tablosuna ekler.
- **ELETE**: Silme işlemi yapıldığında, tetikleyici devreye girer ve müşteri verileri yedeklenir.
- **SELECT**: **deletedMusteri** tablosundaki silinen müşteri verilerini sorgulamak için kullanılır.

&nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
