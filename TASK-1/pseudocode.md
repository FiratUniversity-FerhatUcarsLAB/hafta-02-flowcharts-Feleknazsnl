ALGORİTMA ATM_Para_Cekme_Sade

BAŞLA

  // Kartı okuma
  KART ← KART_OKUT()
  EĞER KART.geçerli_değilse THEN
    EKRANA_YAZ("Geçersiz kart")
    BİTİR

  // PIN doğrulama
  PIN ← PIN_GİR()
  EĞER PIN ≠ KART.kayıtlı_PIN THEN
    EKRANA_YAZ("Hatalı PIN")
    BİTİR

  // Hesap ve bakiye bilgisi
  HESAP ← KART.hesap
  BAKİYE ← HESAP.bakiye

  // Çekilecek tutarı alma
  EKRANA_YAZ("Çekmek istediğiniz tutarı girin:")
  TUTAR ← TUTAR_GİR()

  // Geçersiz tutar kontrolü
  EĞER TUTAR ≤ 0 THEN
    EKRANA_YAZ("Geçersiz tutar")
    BİTİR

  // Hesap bakiyesi kontrolü
  EĞER TUTAR > BAKİYE THEN
    EKRANA_YAZ("Yetersiz bakiye")
    BİTİR

  // ATM nakit kontrolü
  ATM_NAKİT ← ATM_PARASINI_SORGULA()
  EĞER TUTAR > ATM_NAKİT THEN
    EKRANA_YAZ("ATM’de yeterli nakit yok")
    BİTİR

  // Para verme işlemi
  HESAP.bakiye ← BAKİYE − TUTAR
  ATM.parası ← ATM_NAKİT − TUTAR
  NAKİT_VER(TUTAR)

  EKRANA_YAZ("İşlem tamamlandı. Kartınızı alınız.")
  
BİTİR


