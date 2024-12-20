# **Stored Procedure (SP)**

## SQL Stored Procedure (SP) ve JOIN Kullanımı

SQL’de **Stored Procedure (SP)**, veritabanında saklanan ve birden fazla SQL komutunu bir arada çalıştırabilen programlama yapılandırmasıdır. **JOIN** ifadeleri, veritabanı sorgularında iki veya daha fazla tablonun verilerini birleştirerek daha anlamlı sonuçlar elde etmemize yardımcı olur. Stored Procedure (SP), bu JOIN ifadelerinin daha düzenli ve tekrar kullanılabilir bir şekilde çalıştırılmasına olanak tanır.

## Stored Procedure (SP) Nedir?

**Stored Procedure (SP)**, veritabanı üzerinde belirli bir görevi gerçekleştiren bir sorgu veya bir dizi sorgudur. Genellikle birden fazla SQL komutunun bir arada yazılmasına olanak tanır ve veritabanı sunucusunda saklanır. SP'ler daha verimli olabilir çünkü her defasında sorgu yazmak yerine önceden tanımlanmış bir prosedür çağrılır.

## SP Faydaları?

- Procedure’e bağlı işlemler için çağrılacak olan işlem basamakları oluşturmamızı sağlar.

- Performansı artırır.

- Güvenliği artırır.

- Çalışma anında bir planlama sağlamaktadır ve tekrar tekrar kullanılabilmektedir. Bir kez yazılır çok kez kullanılır.

- Ağ trafiğini yormadan işlev görürler.

- Veritabanı nesnelerine güvenli bir yoldan ulaşmamızı sağlar.

```sql
CREATE PROC PROC_ISIM /*PARAMETRELER*/
AS
    //ÖZELLİKLER
BEGIN
    //İŞLEMLER
END
```

```sql
CREATE PROC SP_KisiGuncelle
  (
    @firstname nvarchar(20),
    @lastname nvarchar(10),
    @city nvarchar(15),
    @Id int
  )
AS
BEGIN
  UPDATE EMPLOYEE
  SET firstname = @firstname,
      lastname = @lastname,
      city = @city
  WHERE EmployeeId = @Id
END
```

### **Açıklaması:**

- **CREATE PROC** komutu, yeni bir Stored Procedure (SP) oluşturmak için kullanılır
- **SP_KisiGuncelle** prosedürünün adıdır. Bu, prosedürün çağrıldığı zaman kullanılacak isimdir.
- **AS** anahtar kelimesi, prosedürün gövdesinin başladığını belirtir ve prosedürün içindeki SQL komutlarını kapsar.
- **BEGIN** ve **END** blokları, prosedürün çalıştıracağı SQL komutlarını kapsar. Bu bloklar, birden fazla komut içeriyorsa gereklidir, çünkü tüm komutlar bu iki anahtar kelime arasına yazılır.
- **UPDATE** komutu, veritabanındaki bir tablodaki mevcut verileri güncellemek için kullanılır. Bu komut, **EMPLOYEE** tablosunda değişiklik yapmak amacıyla kullanılır. **EMPLOYEE**, çalışanların verilerini saklayan tablonun adıdır.
- **SET** komutu, güncellenmesi gereken kolonları belirler.
- **WHERE** koşulu, **UPDATE** komutunun hangi kaydı güncellemesi gerektiğini belirler.
- **END** komutu, prosedürün sonunu belirtir. Yani, prosedür burada tamamlanır.
-

### ÖZETLE

Bu Stored Procedure, **EMPLOYEE** tablosunda bir çalışanın adı, soyadı ve şehri gibi bilgilerini güncellemek için tasarlanmıştır. Prosedür, güncelleme işlemi yapılacak çalışanın **EmployeeId** değerini ve yeni bilgileri parametre olarak alır. Bu değerler kullanılarak, sadece belirli bir çalışanın bilgileri güncellenir.

** _Bu prosedürü çalıştırmak için aşağıdaki gibi bir komut kullanılabilir:_ **

```sql
EXEC SP_KisiGuncelle
    @firstname = 'ALPER',
    @lastname = 'BİLGİN',
    @city = 'İstanbul',
    @Id = 3;

```

## Stored Procedure Kullanarak JOIN İfadesi

Stored Procedure içerisinde JOIN ifadeleri kullanarak veritabanındaki farklı tablolardan veri çekebiliriz.

```sql
CREATE PROCEDURE GetBookCategoryByPersonID(@PersonID INT)
AS
BEGIN
    SELECT KISILER.ad, KITAPLAR.kategori
    FROM KISILER K
    LEFT JOIN KITAPLAR KI ON K.ID = KI.kisi_id
    WHERE K.ID = @PersonID;
END;

```

**Açıklamalar:**

- **@PersonID**: Prosedüre parametre olarak bir PersonID değeri verilmiştir. Bu değer, belirli bir kişiyi sorgulamak için kullanılır.
- **LEFT JOIN**: Sol tablodaki (**KISILER**) tüm kayıtları ve sağ tablodaki (**KITAPLAR**) eşleşen kayıtları döndüren **LEFT JOIN** kullanılmıştır. Eşleşmeyen kayıtlar için sağ tablodan **NULL** döndürülür.
- **WHERE K.ID = @PersonID**: Bu koşul, sadece belirli bir kişinin bilgilerini almak için kullanılacaktır.
  &nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
