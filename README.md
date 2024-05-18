Hastane Veritabanı Yönetim Sistemi


Genel Bakış

Bu proje, bir hastanenin çeşitli operasyonlarını yönetmek için tasarlanmış kapsamlı bir Hastane Veritabanı Yönetim Sistemi'dir. Sistem, randevu planlama, hasta muayenesi ve ilaç dağıtımı gibi işlemleri yönetir. Hasta, doktor, sekreter ve diğer personel gibi farklı rolleri içerir ve her biri veritabanı ile belirli işlevler ve tetikleyiciler aracılığıyla etkileşime girer.


Proje Üyeleri

Gökberk Çakır (G191210450) - gokberk.cakir@ogr.sakarya.edu.tr
Gökhan Özcan (G201210052) - gokhan.ozcan5@ogr.sakarya.edu.tr
Adem Bilgin (S211210226) - adembilgin509@hotmail.com


Özellikler

Varlık-İlişki Modeli: Çeşitli varlıkları ve bunların ilişkilerini yakalayan sağlam bir ER modeli üzerine inşa edilmiştir.
İlişkisel Model: hasta, doktor, sekreter, personel gibi detaylı ilişkisel tablolar içerir.
Fonksiyonlar ve Tetikleyiciler: Veritabanı işlemleri için gerekli fonksiyonlar ve tetikleyiciler içerir.
Grafik Kullanıcı Arayüzü: Kayıt ekleme ve silme için bir arayüz sağlar.


Veritabanı Şeması


Varlıklar:


hasta

doktor

sekreter

personel

ilaç

reçete

randevu

depo

tedarikçi

sigorta

kan_grubu


Tablolar:


cinsiyet(cinsiyetid INTEGER, cinsiyet VARCHAR)

kisi(kisiid INTEGER, ad VARCHAR, soyad VARCHAR, telefon VARCHAR, email VARCHAR, cinsiyetid INTEGER)

hasta(kisiid INTEGER, boy VARCHAR, kilo VARCHAR, kan_grubuid INTEGER, sigortaid INTEGER, tc_no VARCHAR)

doktor(kisiid INTEGER, unvan VARCHAR, egitim VARCHAR, klinikid INTEGER, katilim_tarihi DATE)

sekreter(kisiid INTEGER)

personel(kisiid INTEGER)

kan_grubu(kan_grubuid INTEGER, kan_grubu VARCHAR)

sigorta(sigortaid INTEGER, sigorta_adi VARCHAR)

randevu(randevuid INTEGER, tarih DATE, hastaid INTEGER, doktorid INTEGER, sekreterid INTEGER, klinikid INTEGER)

reçete(reçeteid INTEGER, ilac_id INTEGER, muayeneid INTEGER)

klinik(klinikid INTEGER, klinik_adi VARCHAR)

depo(depoid INTEGER, kisiid INTEGER, ilac_id INTEGER, stok BIGINT)

ilaç(ilac_id INTEGER, ilac_adi VARCHAR, ilac_mg INTEGER, tedarikci_id INTEGER)

tedarikçi(tedarikci_id INTEGER, tedarikci_adi VARCHAR, tedarik_tarihi DATE)


Fonksiyonlar ve Tetikleyiciler


Fonksiyonlar:


cocukilac(ilacmg DOUBLE PRECISION): Çocuk ilaçlarının dozajını yarıya indirir.

kisigetir(prmt VARCHAR): Bir arama parametresine göre kişi listesini getirir.

maksboy(): Hastalar arasındaki maksimum boyu döndürür.

makskilo(): Hastalar arasındaki maksimum kiloyu döndürür.


Tetikleyiciler:


doktorarttir(): Doktor sayısını artırır.

doktorazalt(): Doktor sayısını azaltır.

hastaarttir(): Hasta sayısını artırır.

hastaazalt(): Hasta sayısını azaltır.


Kurulum


Depoyu Klonlayın:

sh
git clone https://github.com/yourusername/hospital-database-system.git
cd hospital-database-system

Veritabanını Kurun:

PostgreSQL'in yüklü ve çalışır durumda olduğundan emin olun.
Veritabanı şemasını kurmak ve başlangıç verilerini eklemek için sağlanan SQL betiklerini çalıştırın.

sh
Kodu kopyala
psql -U postgres -f setup.sql


Uygulamayı Çalıştırın:

Veritabanı ile etkileşime geçmek için özel bir uygulama arayüzü veya bir veritabanı yönetim aracını kullanabilirsiniz.

Kullanım

Kayıt Ekleme: Veritabanına yeni kayıtlar eklemek için arayüzü kullanın.
Kayıt Silme: Veritabanından mevcut kayıtları silmek için arayüzü kullanın.
Veri Sorgulama: Veritabanından belirli verileri getirmek için sağlanan fonksiyonları kullanın.
