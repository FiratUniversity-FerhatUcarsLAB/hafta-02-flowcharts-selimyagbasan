# ATM Para Çekme Sistemi (kaba model)

bakiye = 5000           # Hesaptaki mevcut para
gunluk_limit = 2000     # Günlük para çekme limiti
cekilen_toplam = 0      # Günlük toplam çekilen miktar
dogru_pin = "1234"      # Doğru PIN
hak = 3                 # PIN deneme hakkı

# PIN kontrol döngüsü
while hak > 0:
    girilen_pin = input("PIN kodunuzu girin: ")
    if girilen_pin == dogru_pin:
        print("PIN doğrulandı.\n")
        break
    else:
        hak -= 1
        print(f"Hatalı PIN! Kalan deneme hakkı: {hak}")
else:
    print("3 hatalı giriş. Kart bloke edildi.")
    exit()

# İşlem döngüsü
while True:
    print(f"\nMevcut bakiyeniz: {bakiye} TL")
    tutar = int(input("Çekmek istediğiniz tutarı girin: "))

    # Koşul 1: 20 TL’nin katı mı?
    if tutar % 20 != 0:
        print("Tutar 20 TL'nin katı olmalı.")
        continue

    # Koşul 2: Günlük limit kontrolü
    if cekilen_toplam + tutar > gunluk_limit:
        print("Günlük limit aşıldı!")
        continue

    # Koşul 3: Yeterli bakiye var mı?
    if tutar > bakiye:
        print("Yetersiz bakiye!")
        continue

    # Tüm kontroller geçtiyse para verilir
    bakiye -= tutar
    cekilen_toplam += tutar
    print(f"{tutar} TL verildi. Kalan bakiye: {bakiye} TL")
    print("Fişiniz veriliyor...")

    # Başka işlem isteği
    tekrar = input("Başka işlem yapmak ister misiniz? (E/H): ").strip().upper()
    if tekrar != "E":
        print("Kartınızı almayı unutmayın. İyi günler!")
        break
