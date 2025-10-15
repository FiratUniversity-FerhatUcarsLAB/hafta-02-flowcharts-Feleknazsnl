ALGORİTMA ATM_Para_Cekme

BAŞLA

  // 1. Kart Okuma
  KART = KART_OKUT()
  
  EĞER KART.GEÇERLİ_DEĞİLSE İSE
    EKRANA_YAZ("Geçersiz kart. Lütfen tekrar deneyin.")
    BİTİR

  // 2. PIN Doğrulama
  PIN = PIN_GİR()
  DOĞRU_PIN = KART.PIN

  EĞER PIN ≠ DOĞRU_PIN İSE
    EKRANA_YAZ("Hatalı PIN. İşlem sonlandırıldı.")
    BİTİR

  // 3. Bakiye ve ATM Parası Sorgulama
  HESAP_BAKİYESİ = KART.BAKİYE
  ATM_BAKİYESİ = ATM_PARASINI_SORGULA()

  // 4. Para Çekme Tutarını Alma
  EKRANA_YAZ("Lütfen çekmek istediğiniz tutarı girin:")
  TUTAR = KULLANICIDAN_TUTAR_AL()

  // 5. Geçerli Tutar Kontrolü
  EĞER TUTAR ≤ 0 İSE
    EKRANA_YAZ("Geçersiz tutar. Lütfen sıfırdan büyük bir tutar girin.")
    BİTİR

  // 6. Yeterli Bakiye Kontrolü
  EĞER TUTAR > HESAP_BAKİYESİ İSE
    EKRANA_YAZ("Yetersiz bakiye. İşlem sonlandırıldı.")
    BİTİR

  // 7. ATM’de Yeterli Nakit Var mı?
  EĞER TUTAR > ATM_BAKİYESİ İSE
    EKRANA_YAZ("ATM’de yeterli para bulunmamaktadır. Lütfen başka bir tutar girin.")
    BİTİR

  // 8. İşlem Onayı ve Nakit Verme
  HESAP_BAKİYESİ ← HESAP_BAKİYESİ - TUTAR
  ATM_BAKİYESİ ← ATM_BAKİYESİ - TUTAR
  NAKİT_VER(TUTAR)

  // 9. Bilgilendirme
  EKRANA_YAZ("İşleminiz başarıyla tamamlandı.")
  EKRANA_YAZ("Kartınızı almayı unutmayınız.")

BİTİR

SON_ALGORİTMA
