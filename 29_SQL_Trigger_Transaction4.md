# \***\*Trigger - Transaction 4\*\***

---

## **_TRANSACTİON ÖRNEK_**

```sql
BEGIN TRANSACTION;  -- Transaction başlatılır

BEGIN TRY
    -- İlk işlem: 'Employees' tablosunda maaş artışı yapılır
    UPDATE Employees
    SET Salary = Salary + 1000
    WHERE Department = 'HR';

    -- İkinci işlem: 'Employees' tablosunda başka bir departmanda maaş artışı yapılır
    UPDATE Employees
    SET Salary = Salary + 2000
    WHERE Department = 'IT';

    -- Eğer her şey doğru giderse, transaction başarılı olursa commit yapılır
    COMMIT;
    PRINT 'Transaction successful!';
END TRY
BEGIN CATCH
    -- Eğer bir hata meydana gelirse, transaction geri alınır
    ROLLBACK;
    PRINT 'Error occurred, transaction rolled back.';
END CATCH;

```

## AÇIKLAMA:

1. **BEGIN TRANSACTION;** : Bu komut, transaction'ı başlatır. Bu noktada yapılacak tüm işlemler bir transaction içinde tutulacaktır. Eğer sonrasında bir hata olursa, işlemler geri alınabilir.
2. **BEGIN TRY** : Bu, TRY-CATCH bloğunun başlangıcıdır. `TRY` bloğunda yazılan SQL kodları çalıştırılacak ve herhangi bir hata oluşursa, `CATCH` bloğuna geçilecektir.
3. **UPDATE Employees SET Salary = Salary + 1000 WHERE Department = 'HR';** : Bu komut, `Employees` tablosundaki 'HR' departmanındaki çalışanların maaşlarını 1000 birim artırır.
4. **UPDATE Employees SET Salary = Salary + 2000 WHERE Department = 'IT';** : **Açıklama:** İkinci işlemde, `Employees` tablosundaki 'IT' departmanındaki çalışanların maaşları 2000 birim artırılır.
5. **COMMIT;** : Bu komut, transaction içindeki tüm işlemleri onaylar ve veritabanına kalıcı olarak kaydeder. `COMMIT` komutu çalıştırıldığında, `UPDATE` komutları geçerli olur.
6. **PRINT 'Transaction successful!';** : Bu komut, işlem başarılı olduğunda ekrana bir mesaj basar. Bu, kullanıcıya işlemin tamamlandığını bildirir.
7. **BEGIN CATCH** : Eğer TRY bloğunda herhangi bir hata oluşursa, CATCH bloğuna geçilir. Bu blok, hataları yakalamak için kullanılır.
8. **ROLLBACK;** : Eğer bir hata oluşursa, transaction geri alınır. Yani, bu komutla tüm değişiklikler iptal edilir ve veritabanı ilk durumuna döner.
9. **PRINT 'Error occurred, transaction rolled back.';** : Eğer transaction sırasında bir hata oluşursa, bu komut çalıştırılarak bir hata mesajı ekrana yazdırılır.

## **ÖZETLE**

Bu SQL Server transaction örneğinde, birden fazla işlem yapılır (maaş artışı örneğn). Eğer işlemler başarılı olursa, transaction commit edilir ve değişiklikler kaydedilir. Ancak bir hata oluşursa, tüm işlemler geri alınır (**ROLLBACK**) ve veritabanı tutarlı bir duruma döner. Bu yapı, veritabanındaki bütünlüğü ve güvenliği sağlamak için önemlidir.
