## **# SQL'de UPDATE İfadesinin Kullanımı**

SQL'de `UPDATE` komutu, mevcut bir kaydın verilerini güncellemek için kullanılır. Komutun temel yapısı aşağıdaki gibidir.

```sql
UPDATE [tablo adı]
SET [alan1] = deger1, [alan2] = deger2, ...
WHERE [koşul];
```

### Açıklaması:

- **[tablo adı]**: Güncellemek istediğiniz tablonun adıdır.
- **SET**: Güncellenecek alanları ve bu alanlara atanacak yeni değerleri belirtir.
- **WHERE**: Hangi kayıtların güncelleneceğini belirten koşuldur. Eğer `WHERE` kullanılmazsa, tüm kayıtlar güncellenir, bu yüzden dikkatli olunmalıdır.

## Örnek Kullanım

```sql
UPDATE personel
SET maas = 99999
WHERE ID = 65;
```

Bu örnekte, **personel** tablosundaki **ID** değeri 65 olan çalışanın maaşı 99999 olarak güncellenir.

&nbsp;

Birden fazla alanı güncellemek isterseniz, SET ifadesinde alanları virgülle ayırarak belirtebilirsiniz.

```sql
UPDATE personel
SET maas = 99999, bolum = 'CE'
WHERE ID = 65;

```

&nbsp;

**_ÖZETLE_**
´Bu formata göre **UPDATE** deyiminden sonra hangi veritabanı tablosunda güncelleme yapmak istiyorsak o tablonun adını yazıyoruz. **SET** deyiminden sonra değiştirmek istediğimiz bilgileri giriyoruz. Son olarak **WHERE** ifadesinden sonra değiştirme işlemi yapacağımız kayıtlarla ilgili şartı veya şartları yazıyoruz. WHERE ifadesinin kullanımı zorunlu değildir, fakat WHERE kullanılmazsa bütün kayıtlar değiştirme işleminden etkilenecektir.
