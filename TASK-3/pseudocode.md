Başla

// Hasta bilgilerini al
Hasta_Bilgileri_Al():
    Yazdır("Adınızı giriniz:")
    hasta_ad = Oku()
    Yazdır("Soyadınızı giriniz:")
    hasta_soyad = Oku()
    Yazdır("TC Kimlik Numaranızı giriniz:")
    hasta_tc = Oku()
    Yazdır("Telefon numaranızı giriniz:")
    hasta_telefon = Oku()
    Döndür (hasta_ad, hasta_soyad, hasta_tc, hasta_telefon)

// Doktor listesini göster ve doktor seçimini al
Doktor_Secim():
    doktorlar = ["Dahiliye", "Kardiyoloji", "Ortopedi", "Göz", "KBB"]
    Yazdır("Lütfen bir branş seçiniz:")
    Her doktor in doktorlar:
        Yazdır(doktor_indeks + 1, "-", doktor)
    doktor_secim = Oku()
    Eğer doktor_secim geçerli değilse:
        Yazdır("Geçersiz seçim, tekrar deneyiniz.")
        doktor_secim = Doktor_Secim()
    Döndür doktorlar[doktor_secim - 1]

// Randevu saatlerini getir ve seçimi al
Randevu_Saatleri_Getir(doktor_brans):
    // Örnek saatler, gerçek sistemde veri tabanından çekilir
    randevu_saatleri = ["09:00", "10:00", "11:00", "13:00", "14:00", "15:00"]
    uygun_saatler = []
    
    Her saat in randevu_saatleri:
        Eğer saat dolu değilse (saat müsaitse):
            uygun_saatler_ekle(saat)
    
    Eğer uygun_saatler boşsa:
        Yazdır("Bu branşta müsait randevu yok.")
        Döndür boş liste
    Yazdır("Müsait saatler:")
    Her saat_index, saat in uygun_saatler:
        Yazdır(saat_index + 1, "-", saat)
    Yazdır("Lütfen bir saat seçiniz:")
    saat_secim = Oku()
    Eğer saat_secim geçerli değilse:
        Yazdır("Geçersiz seçim, tekrar deneyiniz.")
        saat_secim = Randevu_Saatleri_Getir(doktor_brans)
    Döndür uygun_saatler[saat_secim - 1]

// Randevuyu kaydet
Randevu_Kaydet(hasta, doktor_brans, saat):
    // Gerçek sistemde veri tabanına kayıt yapılır
    Yazdır("Randevunuz kaydediliyor...")
    Bekle(1 saniye)
    Yazdır(hasta.ad, hasta.soyad, "isimli hasta için", doktor_brans, "branşında", saat, "randevusu oluşturuldu.")
    Döndür Başarılı

// Ana program akışı
Ana():
    hasta = Hasta_Bilgileri_Al()
    doktor_brans = Doktor_Secim()
    saat = Randevu_Saatleri_Getir(doktor_brans)
    
    Eğer saat boş değilse:
        başarılı = Randevu_Kaydet(hasta, doktor_brans, saat)
        Eğer başarılı:
            Yazdır("Randevunuz başarıyla oluşturuldu. İyi günler!")
        Değilse:
            Yazdır("Randevu oluşturulurken hata oluştu.")
    Değilse:
        Yazdır("Randevu alınamadı.")

Son
