Başla

  Kullanıcının kartını okut
  Eğer kart geçerli değilse
    "Geçersiz kart" mesajı göster
    Bitir

  PIN kodunu gir
  Eğer PIN yanlışsa
    "Hatalı PIN" mesajı göster
    Bitir

  Kullanıcının mevcut bakiyesini sorgula

  "Çekmek istediğiniz tutarı girin:" mesajı göster
  ParaÇekilecekTutar değişkenine değeri al

  Eğer ParaÇekilecekTutar <= 0 ise
    "Geçersiz tutar" mesajı göster
    Bitir

  Eğer ParaÇekilecekTutar > MevcutBakiye ise
    "Yetersiz bakiye" mesajı göster
    Bitir

  Eğer ATM içinde yeterli para yoksa
    "ATM’de yeterli para bulunmamaktadır" mesajı göster
    Bitir

  MevcutBakiye'den ParaÇekilecekTutar kadar düş
  ATM’deki paradan ParaÇekilecekTutar kadar düş
  Nakit olarak ParaÇekilecekTutar'ı ver

  "İşleminiz başarıyla tamamlandı" mesajı göster
  "Kartınızı almayı unutmayın" mesajı göster

Bitir
