BASLA Kullanıcı Girişi
    EGER-ISE Kullanıcı kayıtlı ve giriş bilgileri doğru ISE
        Kullanıcıyı giriş yapmış olarak işaretle
    DEĞILSE
        Giriş hatası göster
BITIR

BASLA Ürün Seçimi ve Sepete Ekleme
    DONGÜ Kullanıcı ürün seçmeye devam ettiği sürece
        Ürünü seç
        EGER-ISE Ürün stokta mevcut ISE
            Sepete ekle
        DEĞILSE
            "Stokta yok" mesajı göster
    BITIR DONGÜ
BITIR

BASLA İndirim Kodu Uygulama
    EGER-ISE Kullanıcı indirim kodu girdi ISE
        EGER-ISE Kod geçerli ve kullanım hakkı varsa ISE
            İndirimi sepete uygula
        DEĞILSE
            Hata mesajı göster
BITIR

BASLA Kargo Hesaplama
    Teslimat adresini al
    Kargo ücretini hesapla
    Sepet toplamına kargo ücretini ekle
BITIR

BASLA Ödeme Aşaması
    Kullanıcı ödeme yöntemi seçer
    EGER-ISE Ödeme bilgileri geçerli ISE
        Ödeme sağlayıcısına talep gönder
        EGER-ISE Ödeme başarılı ISE
            Siparişi onayla
            Fatura oluştur ve kullanıcıya gönder
        DEĞILSE
            Ödeme başarısız mesajı göster
    DEĞILSE
        "Geçersiz ödeme bilgisi" mesajı göster
BITIR

BASLA Sipariş Tamamlama
    Sipariş durumu: "Onaylandı"
    Sipariş bilgilerini depo ve kargo sistemine gönder
BITIR
