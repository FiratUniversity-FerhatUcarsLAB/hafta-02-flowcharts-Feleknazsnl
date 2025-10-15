Başlangıç

    // Sensörler ve cihazlar tanımlanır
    HareketSensörü = TRUE   // Hareket algılama sensörü açık
    KapıPencereSensörü = TRUE  // Kapı ve pencere sensörleri açık
    GüvenlikKamerası = TRUE    // Güvenlik kameraları aktif
    AlarmSistemi = FALSE      // Alarm başlangıçta kapalı
    KullanıcıTelefonu = "bağlantı kurulmuş" // Kullanıcı telefonunun durumu

    // Evde kimse yok mu kontrol et
    Eğer EvdeKimseYok() ise
        // Evde kimse yoksa alarm sistemi aktif olmalı
        AlarmSistemi = TRUE
        KameraYayınıBaşlat()  // Kameralar görüntü kaydına başlar
        MesajGönder("Evde kimse yok, güvenlik alarmı aktif edildi.")
    Sonraki
    Eğer EvdeKimseVar() ise
        // Evde kimse varsa güvenlik sistemi pasif
        AlarmSistemi = FALSE
        KameraYayınıDurdur()  // Kameralar durur
    Sonraki

    // Hareket sensörlerini kontrol et
    Eğer HareketAlgıla() ise
        // Eğer hareket algılanırsa alarm sistemi tetiklenir
        AlarmSistemi = TRUE
        MesajGönder("Evde hareket tespit edildi. Güvenlik alarmı tetiklendi.")
    Sonraki

    // Kapı veya pencere sensörlerini kontrol et
    Eğer KapıPencereAçıldı() ise
        // Kapı veya pencere açıldığında alarm tetiklenir
        AlarmSistemi = TRUE
        MesajGönder("Kapı veya pencere açıldı. Güvenlik alarmı tetiklendi.")
    Sonraki

    // Alarm durumunu kontrol et
    Eğer AlarmSistemi = TRUE ise
        // Eğer alarm aktifse, güvenlik servisine bildir
        GüvenlikServisiBildir()
    Sonraki

    // Kullanıcıya anlık bildirim gönder
    Eğer AlarmSistemi = TRUE ve KullanıcıTelefonu "bağlantı kurulmuş" ise
        MesajGönder("Evde güvenlik ihlali tespit edildi. Lütfen durumu kontrol edin.")
    Sonraki

    // Sistem durumu kontrol et
    Eğer AlarmSistemi = FALSE ve HareketAlgıla() = FALSE ve KapıPencereAçıldı() = FALSE ise
        // Ev güvenli, sistem normal çalışıyor
        MesajGönder("Ev güvenli, tüm sistemler normal.")
    Sonraki

Son
