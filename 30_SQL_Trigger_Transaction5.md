# **Trigger - Transaction**

Bir e-ticaret sisteminde Müşteri Customers), Ürün Products) ve Sipariş Orders) tabloları bulunmaktadır.

---

| CustomerID | Name        | Email                   |
| ---------- | ----------- | ----------------------- |
| 1          | Ayşe Yılmaz | ayse.yilmaz@example.com |
| 2          | Ahmet Kaya  | ahmet.kaya@example.com  |
| 3          | Elif Demir  | elif.demir@example.com  |

---

| ProductID | ProductName         | Stock | Price    |
| --------- | ------------------- | ----- | -------- |
| 1         | Laptop              | 10    | 15000.00 |
| 2         | Akıllı Telefon      | 25    | 8000.00  |
| 3         | Kulaklık            | 50    | 250.00   |
| 4         | Masaüstü Bilgisayar | 5     | 12000.00 |
| 5         | Tablet              | 15    | 5000.00  |

---

| OrderID | CustomerID | ProductID | Quantity | OrderDate       |
| ------- | ---------- | --------- | -------- | --------------- |
| 1       | 1          | 2         | 1        | 1.12.2024 10:00 |
| 2       | 2          | 1         | 2        | 2.12.2024 15:30 |
| 3       | 3          | 3         | 3        | 3.12.2024 12:45 |

---

**1- Bir müşteri bir üründen sipariş vermek istiyor. Sipariş işlemi sırasında:**

- a Stokta yeterli ürün olup olmadığı kontrol edilecek.
- b Yeterli stok varsa sipariş eklenecek ve stok güncellenecek.
- c Herhangi bir adımda hata oluşursa işlem geri alınacak.

```sql
BEGIN TRANSACTION;

DECLARE @Stock INT;
SELECT @Stock = Stock FROM Products WHERE ProductID = @ProductID;

IF @Stock >= @Quantity
BEGIN
    -- Sipariş ekle
    INSERT INTO Orders (CustomerID, ProductID, Quantity, OrderDate)
    VALUES (@CustomerID, @ProductID, @Quantity, GETDATE());

    -- Stok güncelle
    UPDATE Products
    SET Stock = Stock - @Quantity
    WHERE ProductID = @ProductID;

    COMMIT TRANSACTION;
END
ELSE
BEGIN
    PRINT 'Yeterli stok yok!';
    ROLLBACK TRANSACTION;
END;

```

&nbsp;

**2-Yeni bir sipariş eklendiğinde aşağıdaki işlemleri gerçekleştiren triggerı yazınız.**

- a Yeni bir sipariş eklendiğinde stok miktarı otomatik olarak azalsın.
- b Stok miktarı sıfırın altına düşerse sipariş eklenmesin.

```sql
CREATE TRIGGER trg_UpdateStockOnInsert
ON Orders
AFTER INSERT
AS
BEGIN
    DECLARE @ProductID INT, @Quantity INT;

    -- Yeni eklenen siparişin ProductID ve Quantity bilgilerini alıyoruz
    SELECT @ProductID = ProductID, @Quantity = Quantity
    FROM INSERTED;

    -- Stok miktarını güncelliyoruz
    UPDATE Products
    SET Stock = Stock - @Quantity
    WHERE ProductID = @ProductID;

    -- Eğer stok miktarı sıfırın altına düştüyse, işlem geri alınıyor
    IF EXISTS (SELECT 1 FROM Products WHERE ProductID = @ProductID AND Stock < 0)
    BEGIN
        PRINT 'Stok sıfırın altına düştü! Sipariş iptal ediliyor.';

        -- Sipariş eklemeden önce stok miktarını kontrol etmek için rollback yapılır
        ROLLBACK;
    END;
END;

```

&nbsp;

**3-Bir ürünün stoğu güncellendiğinde, bu işlemi bir log tablosuna kaydeden triggerı yazınız.**

```sql
CREATE TRIGGER trg_LogStockUpdate
ON Products
AFTER UPDATE
AS
BEGIN
    -- Stok değeri değiştiyse, log kaydı ekle
    IF UPDATE(Stock)
    BEGIN
        INSERT INTO StockLog (ProductID, OldStock, NewStock, ChangeDate)
        SELECT
            D.ProductID,
            D.Stock AS OldStock,
            I.Stock AS NewStock,
            GETDATE() AS ChangeDate
        FROM DELETED D
        INNER JOIN INSERTED I ON D.ProductID = I.ProductID;
    END
END;

```

&nbsp;

**4-Sipariş ekleme işlemini bir stored procedure içinde tanımlayınız.**

```sql
CREATE PROCEDURE AddOrder
    @CustomerID INT,
    @ProductID INT,
    @Quantity INT
AS
BEGIN
    BEGIN TRANSACTION;

    DECLARE @Stock INT;

    -- Ürünün mevcut stok miktarını alıyoruz
    SELECT @Stock = Stock FROM Products WHERE ProductID = @ProductID;

    -- Yeterli stok varsa işlemi gerçekleştir
    IF @Stock >= @Quantity
    BEGIN
        -- Siparişi ekle
        INSERT INTO Orders (CustomerID, ProductID, Quantity, OrderDate)
        VALUES (@CustomerID, @ProductID, @Quantity, GETDATE());

        -- Stok güncelle
        UPDATE Products
        SET Stock = Stock - @Quantity
        WHERE ProductID = @ProductID;

        -- İşlemi tamamla
        COMMIT TRANSACTION;
    END
    ELSE
    BEGIN
        -- Yeterli stok yoksa hata mesajı döndür
        RAISEERROR('Yeterli stok yok!', 16, 1);

        -- Transaction geri al
        ROLLBACK TRANSACTION;
    END;
END;

```

&nbsp;

**5-Bir sipariş silindiğinde, silinen siparişin miktarı kadar ürün stoğunu otomatik olarak geri yükleyen bir trigger yazınız.**

```sql
CREATE TRIGGER trg_RestoreStockOnDelete
ON Orders
AFTER DELETE
AS
BEGIN
    DECLARE @ProductID INT, @Quantity INT;

    -- Silinen siparişin ProductID ve Quantity değerlerini alıyoruz
    SELECT @ProductID = ProductID, @Quantity = Quantity
    FROM DELETED;

    -- Silinen siparişin miktarı kadar ürünün stok miktarını geri yükleriz
    UPDATE Products
    SET Stock = Stock + @Quantity
    WHERE ProductID = @ProductID;
END;

```

&nbsp;

**6-Belirli bir tarih aralığındaki tüm siparişlerin toplam maliyetini döndüren fonksiyonu yazınız.**

```sql
CREATE FUNCTION GetTotalCostByDateRange
    (@StartDate DATETIME, @EndDate DATETIME)
RETURNS DECIMAL(18, 2)
AS
BEGIN
    DECLARE @TotalCost DECIMAL(18, 2);

    -- Belirtilen tarih aralığındaki tüm siparişlerin toplam maliyetini hesapla
    SELECT @TotalCost = SUM(O.Quantity * P.Price)
    FROM Orders O
    INNER JOIN Products P ON O.ProductID = P.ProductID
    WHERE O.OrderDate BETWEEN @StartDate AND @EndDate;

    -- Hesaplanan toplam maliyeti döndür
    RETURN @TotalCost;
END;

```

&nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
