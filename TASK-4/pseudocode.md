BAŞLA

// Kullanıcı giriş işlemi
GİRİŞ_YAP:
    EKRANA "Öğrenci numaranızı girin:" YAZ
    ÖĞRENCİ_NO ← KULLANICIDAN_VERİ_AL

    EKRANA "Şifrenizi girin:" YAZ
    ŞİFRE ← KULLANICIDAN_VERİ_AL

    EĞER KULLANICI_DOĞRULANDI(ÖĞRENCİ_NO, ŞİFRE) DEĞİLSE
        EKRANA "Giriş başarısız. Tekrar deneyin." YAZ
        GİT GİRİŞ_YAP
    SON

// Kayıt dönemi kontrolü
EĞER KAYIT_HAFTASI_MI() DEĞİLSE
    EKRANA "Şu an ders kayıt haftası değil. Lütfen ilgili tarihlerde tekrar deneyin." YAZ
    DUR
SON

// Alınabilecek dersleri listele
ALINABİLİR_DERSLER ← DERSLERİ_GETİR(ÖĞRENCİ_NO)
EKRANA "Alabileceğiniz dersler:" YAZ
DERSLERİ_GÖSTER(ALINABİLİR_DERSLER)

// Ders seçimi
SEÇİLEN_DERSLER ← BOŞ_LİSTE

TEKRAR:
    EKRANA "Bir dersin kodunu girin (veya kayıt işlemini tamamlamak için 'BİTİR' yazın):" YAZ
    DERS_KODU ← KULLANICIDAN_VERİ_AL

    EĞER DERS_KODU = "BİTİR" İSE
        GİT DANIŞMAN_ONAY
    SON

    EĞER DERS_KODU ALINABİLİR_DERSLER LİSTESİNDE YOKSA
        EKRANA "Geçersiz ders kodu. Lütfen tekrar girin." YAZ
        GİT TEKRAR
    SON

    EĞER DERS_KODU ZATEN SEÇİLEN_DERSLER LİSTESİNDE VARSA
        EKRANA "Bu dersi zaten seçtiniz." YAZ
        GİT TEKRAR
    SON

    EĞER DERS_KONTENJANI_DOLU(DERS_KODU) İSE
        EKRANA "Bu dersin kontenjanı dolmuş." YAZ
        GİT TEKRAR
    SON

    SEÇİLEN_DERSLER’E DERS_KODU EKLE
    EKRANA DERS_KODU + " dersi eklendi." YAZ
GİT TEKRAR

// Danışman onayı
DANIŞMAN_ONAY:
    EKRANA "Seçilen dersler:" YAZ
    DERSLERİ_GÖSTER(SEÇİLEN_DERSLER)

    EKRANA "Derslerinizi onaya göndermek istiyor musunuz? (E/H)" YAZ
    ONAY ← KULLANICIDAN_VERİ_AL

    EĞER ONAY = "E" İSE
        DERSLERİ_ONAYA_GÖNDER(ÖĞRENCİ_NO, SEÇİLEN_DERSLER)
        EKRANA "Dersler danışman onayına gönderildi." YAZ
    DEĞİLSE
        EKRANA "Kayıt işlemi iptal edildi." YAZ
    SON

DUR
