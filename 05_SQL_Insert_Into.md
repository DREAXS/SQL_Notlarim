## **# SQL'de INSERT INTO İfadesinin Kullanımı**

---

SQL'de veritabanına kayıt eklemek için `INSERT INTO` deyimini kullanırız. Komutun temel yapısı aşağıdaki gibidir.

```sql
INSERT INTO [tablo adı] (alan adları) VALUES (veriler);
```

---

### Açıklaması:

- **[tablo adı]**: Kayıt eklemek istediğiniz tablonun adıdır.
- **(alan adları)**: Kayıt ekleyeceğiniz alanların adlarıdır. Tüm alanlara değer girileceği zaman bu kısım isteğe bağlıdır.

- **(veriler)**: İlgili alanlara eklemek istediğiniz verilerdir.

## Örnek Kullanım

```sql
INSERT INTO personel (ID, isim, bolum, dtarihi, dyeri, maas)
VALUES (65, 'ALPER BİLGİN', 'CE', 2003, 'KONYA', 00000);
```

---

- Bu örnekte, **personel** tablosuna yeni bir kayıt ekleniyor. Burada tüm alanlar için değerler verildiği için alan adlarını belirtmek zorundayız.

&nbsp;

- Eğer tablonun tüm alanlarına bilgi girilecekse, bu durumda alan adlarını yazmamıza gerek yoktur. Ancak, bazı alanları **NULL** olarak bırakmak istiyorsak, yalnızca değer vermek istediğimiz alanları belirtebiliriz.

```sql
INSERT INTO personel (ID, isim, bolum)
VALUES (65, 'Alper Bilgin', 'CE');
```

---

\*Bu örnekte, yalnızca `ID`, `isim` ve `bolum` alanlarına değer ekleniyor. `dtarihi`, `dyeri` ve `maas` alanları boş kalacak ve bu alanlar için varsayılan değerler kullanılacaktır (eğer varsa).
