# Akıllı Ev Güvenlik Sistemi - Pseudocode

# Sistem aktiflik durumu
def system_active():
    # Sistem aktifse True, değilse False döner
    return True  # Örnek

# Sensör kontrolleri
def check_motion_sensor():
    # Hareket algılanırsa True döner
    return False

def check_door_window_sensor():
    # Kapı/pencere açılırsa True döner
    return False

def is_owner_home():
    # Ev sahibi evdeyse True döner
    return False

def activate_camera():
    print("Kamera aktif edildi ve kayıt başladı.")

def determine_alarm_level(motion, door_window):
    if motion and door_window:
        return 3  # Yüksek alarm
    elif motion or door_window:
        return 2  # Orta alarm
    else:
        return 1  # Düşük alarm

def send_notifications(level):
    print(f"Bildirim gönderildi! Alarm seviyesi: {level}")
    # SMS, App, Email gönder

def alarm_cleared_by_owner():
    # Ev sahibi alarmı sıfırlamak isterse True döner
    return False

def reset_alarm():
    print("Alarm sıfırlandı.")

def continue_alarm():
    print("Alarm devam ediyor!")

def wait(seconds):
    # Bekleme süresi (örnek)
    pass


# ----------------------------
# Ana döngü
# ----------------------------
while True:
    if not system_active():
        wait(5)
        continue  # Sistem aktif değilse bekle ve tekrar kontrol et

    # Sensörleri oku
    motion_detected = check_motion_sensor()
    door_window_breach = check_door_window_sensor()

    # Alarm kontrolü
    if motion_detected or door_window_breach:
        if is_owner_home():
            print("Yanlış alarm: Ev sahibi evde")
        else:
            # Alarm seviyesi belirle
            alarm_level = determine_alarm_level(motion_detected, door_window_breach)
            
            # Kamera aktivasyonu
            activate_camera()
            
            # Bildirim gönder
            send_notifications(alarm_level)
            
            # Alarmı sıfırlama veya devam ettirme
            if alarm_cleared_by_owner():
                reset_alarm()
            else:
                continue_alarm()

    # Döngü arası bekleme
    wait(2)
