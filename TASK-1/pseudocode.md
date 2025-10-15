BAŞLA

  KARTI_OKUT()

  EĞER kart_geçerli_değilse THEN
    EKRANA_YAZ("Geçersiz kart.")
    BİTİR

  PIN = PIN_GİR()

  EĞER PIN_YANLIŞ(PIN) THEN
    EKRANA_YAZ("Hatalı PIN.")
    BİTİR

  BAKİYE = BAKİYE_SORGULA()
  ATM_PARASI = ATM_BAKİYE_SORGULA()

  EKRANA_YAZ("Çekmek istediğiniz tutarı giriniz:")
  TUTAR = TUTAR_GİR()

  EĞER TUTAR <= 0 THEN
    EKRANA_YAZ("Geçersiz tutar.")
    BİTİR

  EĞER TUTAR > BAKİYE THEN
    EKRANA_YAZ("Yetersiz bakiye.")
    BİTİR

  EĞER TUTAR > ATM_PARASI THEN
    EKRANA_YAZ("ATM'de yeterli para bulunmamaktadır.")
    BİTİR

  BAKİYE = BAKİYE - TUTAR
  ATM_PARASI = ATM_PARASI - TUTAR

  NAKİT_VER(TUTAR)

  EKRANA_YAZ("İşleminiz başarıyla tamamlandı.")
  EKRANA_YAZ("Kartınızı almayı unutmayınız.")

BİTİR
