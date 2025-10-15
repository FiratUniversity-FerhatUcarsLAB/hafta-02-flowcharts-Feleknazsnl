Başla

ÜRÜNLER = [
    {id: 1, isim: "Laptop", fiyat: 20000},
    {id: 2, isim: "Telefon", fiyat: 12000},
    {id: 3, isim: "Kulaklık", fiyat: 1500}
]

SEPET = []

Fonksiyon AnaMenu():
    Döngü:
        Yazdır "1. Ürünleri Listele"
        Yazdır "2. Sepete Ürün Ekle"
        Yazdır "3. Sepeti Görüntüle"
        Yazdır "4. Sepetten Ürün Sil"
        Yazdır "5. Ödeme Yap"
        Yazdır "6. Çıkış"
        Girdi SECIM

        Eğer SECIM == 1: UrunleriListele()
        Eğer SECIM == 2: UrunEkle()
        Eğer SECIM == 3: SepetiGoruntule()
        Eğer SECIM == 4: UrunSil()
        Eğer SECIM == 5: OdemeYap()
        Eğer SECIM == 6: Çık
        Aksi halde: Yazdır "Geçersiz seçim"

Fonksiyon UrunleriListele():
    Her ürün içinde ÜRÜNLER:
        Yazdır ürün.id, ürün.isim, ürün.fiyat, "TL"

Fonksiyon UrunEkle():
    Yazdır "Ürün ID gir:"
    Girdi ID
    Yazdır "Adet gir:"
    Girdi ADET
    Eğer ID geçerli ise:
        SEPET'e {id: ID, adet: ADET} ekle
        Yazdır "Ürün sepete eklendi"
    Aksi: Yazdır "Ürün bulunamadı"

Fonksiyon SepetiGoruntule():
    Eğer SEPET boşsa:
        Yazdır "Sepet boş"
        Dön
    TOPLAM = 0
    Her ürün içinde SEPET:
        ÜRÜN = ÜrünBul(ürün.id)
        ARA_TOPLAM = ÜRÜN.fiyat * ürün.adet
        Yazdır ÜRÜN.isim, "-", ürün.adet, "adet -", ARA_TOPLAM, "TL"
        TOPLAM = TOPLAM + ARA_TOPLAM
    Yazdır "Toplam:", TOPLAM, "TL"

Fonksiyon UrunSil():
    Yazdır "Silmek istediğiniz ürün ID:"
    Girdi ID
    SEPET'ten ID'ye sahip ürün sil

Fonksiyon OdemeYap():
    SepetiGoruntule()
    Yazdır "Ödemeyi onayla? (E/H)"
    Girdi CEVAP
    Eğer CEVAP == "E":
        Yazdır "Ödeme başarılı"
        SEPET = []

Fonksiyon ÜrünBul(ID):
    Her ürün içinde ÜRÜNLER:
        Eğer ürün.id == ID:
            Dön ürün
    Dön null

AnaMenu()

Bitir
