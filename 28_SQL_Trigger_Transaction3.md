# \***\*Trigger - Transaction 3\*\***

---

## **_TRANSACTİON_**

### Transaction Nedir?

- Transaction, daha küçük parçalara ayrılamayan bir işlemdir.
- Bir grup işlem, arka arkaya gerçekleşse de seri işlemler olarak ele alınır.

### Transaction'ın Temel Özellikleri

- Transaction bloğu içerisindeki işlemlerin tamamı gerçekleşene kadar tüm işlemler, gerçekleşmemiş sayılır.
- Bir işlem başarılı olursa, tüm veri işlemleri gerçekleştirilir ve veritabanının tutarlı bir parçası haline gelir.
- Bir işlem hata veya istisnalarla karşılaşırsa, tüm veri değişiklikleri geri alınarak tutarsız veri girişinin önüne geçilir.

### Transaction Yönetimi için Kullanılan İfadeler

- **BEGIN**: Transaction başlatmak için kullanılır.
- **ROLLBACK**: Yapılan işlemleri geri almak için kullanılır.
- **COMMIT**: Transaction’ı bitirip yapılan değişiklikleri kalıcı hale getirmek için kullanılır.
- **SAVE**: Kayıt noktaları oluşturmak için kullanılır.

<$>[note]
Transaction’lar, veri tutarlılığı sağlarken, doğru şekilde yönetilmezse performans sorunlarına ve deadlock gibi problemlere yol açabilir.
<$>
