**# SQL** **`CREATE TABLE`** **Komutu**

**### 1. Tablo Adı**

Tabloyu adlandırmak için `CREATE TABLE` ifadesinden sonra tablo adı yazılır.

**### 2. Alan Adları**

Her bir kolonun ismi, alan adı olarak geçer. Her kolonda ilgili verinin ne olduğunu belirtir (örneğin, müşteri adı, sipariş tarihi vs.).

**### 3. Veri Tipleri**

Verinin ne türde saklanacağını belirler. Yaygın veri tipleri:

- \***\*INT\*\***: Tam sayılar.
- \***\*VARCHAR(x)\*\***: Değişken uzunlukta karakter dizisi, `x` karakter sayısını belirtir.
- \***\*DATE\*\***: Tarih değerleri.
- \***\*DECIMAL(x, y)\*\***: Ondalıklı sayılar, `x` toplam basamak sayısı, `y` ondalık kısım.
- \***\*TEXT\*\***: Uzun metin veri türleri.

**### 4. Kısıtlamalar (Constraints)**

Kolonlara uygulanabilecek kısıtlamalardır:

- \***\*NOT NULL\*\***: Bu kolon boş geçilemez.
- \***\*NULL\*\***: Bu kolon boş bırakılabilir.
- \***\*PRIMARY KEY\*\***: Bu kolon her satır için benzersiz ve boş olamaz.
- \***\*DEFAULT\*\***: Varsayılan değer atar.

**### 5. Tablo Kısıtlamaları**

Tablonun genel yapısına yönelik kısıtlamalardır:

- \***\*PRIMARY KEY\*\***: Tablo içindeki bir alanı ya da alanları benzersiz kimlik olarak belirtir.
- \***\*FOREIGN KEY\*\***: Başka bir tablo ile ilişki kurar.
- \***\*UNIQUE\*\***: Her satırda benzersiz bir değer olmasını sağlar.
- \***\*CHECK\*\***: Belirtilen bir koşulu sağlar.

---

**### Örnek:** **`Musteriler`** **Tablosu**

Aşağıda bir müşteri bilgilerini saklayacak tablo örneği bulunmaktadır:

```sql
CREATE TABLE Musteriler (
    MusteriID INT NOT NULL PRIMARY KEY,
    Isim VARCHAR(100) NOT NULL,
    Email VARCHAR(150) NULL,
    DogumTarihi DATE NULL,
    Bakiye DECIMAL(10, 2) DEFAULT 0 NOT NULL
);

```

### Musteriler Tablosu Oluşumu ve Çıktısı

Yukarıdaki SQL kodunun çalıştırılmasıyla aşağıdaki gibi bir tablo yapısı oluşturulur.

#### Tablo Yapısı:

| \***\*MusteriID\*\*** | \***\*Isim\*\*** | \***\*Email\*\*** | \***\*DogumTarihi\*\*** | \***\*Bakiye\*\*** |
| --------------------- | ---------------- | ----------------- | ----------------------- | ------------------ |
| `INT`                 | `VARCHAR(100)`   | `VARCHAR(150)`    | `DATE`                  | `DECIMAL(10, 2)`   |
