# **Trigger - Transaction 1 **

---

## **Tetikleyiciler (Triggers)**

- **Tetikleyici (Trigger) Yapısı**: İlişkisel veri tabanı yönetim sistemlerinde, belirli olaylar gerçekleştiğinde otomatik olarak çalışan özel bir _store procedure_ türüdür.
- **Çalışma Zamanı**: Tetikleyiciler, bir tabloda **ekleme**, **güncelleme** veya **silme** işlemlerinden biri gerçekleştiğinde veya gerçekleşmeden önce otomatik olarak çalışır.
- **Amaç**: Bir tabloda ya da başka bir tabloda, belirli işlemlerin yapılmasını sağlamak için kullanılır.

### **Örnekler**:

- Satış tablosunda satış işlemi gerçekleştiğinde, ürünün **stok miktarının** otomatik olarak eksiltilmesi.
- Banka hesabında işlem gerçekleştikten sonra, kullanıcıya **otomatik e-posta** gönderilmesi.

---

## **Tetikleyici (Trigger) Türleri**

### **DML Tetikleyicileri**:

- **DML Tetikleyicileri**, veriler her değiştirildiğinde, yani **INSERT**, **UPDATE** ve **DELETE** işlemleri yapıldığında tetiklenir.
- **DML tetikleyicileri**, **AFTER** ve **INSTEAD OF** olmak üzere iki tipte sınıflandırılır:
- - **AFTER Tetikleyicileri**: Bir tabloda **INSERT**, **UPDATE** veya **DELETE** işlemleri yapıldıktan sonra belirli işlemlerin yapılmasını sağlar.
- - **INSTEAD OF Tetikleyicileri**: Bir tablo veya view yapısında **INSERT**, **UPDATE** veya **DELETE** işlemlerini atlar ve bunun yerine tetikleyici içinde tanımlanan diğer ifadeleri yerine getirir.

### **DDL Tetikleyicileri**:

- **DDL Tetikleyicileri**, **CREATE**, **ALTER** ve **DROP** ifadeleri kullanıldığında devreye girer ve veritabanı yapısal değişiklikleri takip eder.

### **Logon Tetikleyicileri**:

- **Logon Tetikleyicileri**, SQL Server'da **güvenlik** ve **kontrol** amaçlı kullanılır.
- _Örnek:_ Bir kullanıcı veritabanına dışarıdan bilinmeyen bir bilgisayardan bağlanmaya çalıştığında engellenebilir. Ayrıca yalnızca şirket bilgisayarlarından bağlanılmasına izin verilebilir.

&nbsp;

&nbsp;

<**_[Alper BİLGİN](https://github.com/DREAXS)_**>
