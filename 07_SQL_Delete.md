## **# DELETE Komutunun Kullanımı**

SQL'de `DELETE` komutu, bir veritabanı tablosundan belirli kayıtları silmek için kullanılır. Komutun temel yapısı aşağıdaki gibidir.

```
DELETE FROM [tablo adı] WHERE [koşul];
```

### Açıklaması:

- **[tablo adı]**: Kayıtları silmek istediğiniz tablonun adıdır.
- **WHERE**: Hangi kayıtların silineceğini belirten koşuldur. Eğer `WHERE` kullanılmazsa, tablodaki tüm kayıtlar silinir.

## Örnek Kullanım

```
DELETE FROM personel WHERE ID = 65;
```

Bu örnekte, **personel** tablosundaki **ID** değeri 65 olan kayıt silinir.

&nbsp;

- **WHERE Koşulu**: `WHERE` ifadesi kullanmak, yalnızca belirli kayıtları silmenizi sağlar. Eğer bu koşul yoksa, tablodaki tüm kayıtlar silinir. Bu, istenmeyen veri kayıplarına yol açabilir.

&nbsp;

- **_Yedekleme_**: Silme işlemi geri alınamaz, bu yüzden önemli verilerinizi silmeden önce yedek almak iyi bir uygulamadır.

```
DELETE FROM personel;
```

**Bu komut, personel tablosundaki tüm kayıtları siler.**

&nbsp;

**_ÖZETLE_**

Bu formata göre **DELETE FROM** deyiminden sonra hangi veri tabanı tablosunda alan silmek istiyorsak o tablonun adını yazıyoruz. Son olarak **WHERE** ifadesinden sonra silmek isteğimiz kayıtlarla ilgili şartı veya şartları yazıyoruz. WHERE ifadesinin kullanımı zorunlu değildir, fakat WHERE kullanılmazsa bütün kayıtlar değiştirme işleminden etkilenecektir.
