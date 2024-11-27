# ESPNOW
import espnow
import network
import time

# Configurar el ESP32 como estación Wi-Fi (aunque no se conectará a una red Wi-Fi)
wlan = network.WLAN(network.STA_IF)
wlan.active(True)

# Inicializar ESP-NOW
espnow.init()

# Dirección MAC del receptor (debe configurarse con la dirección MAC del otro ESP32)
mac_receptor = b'\x30\xae\xa4\x12\x34\x56'  # Cambiar a la MAC del receptor

# Enviar datos
while True:
    message = "Hola desde el transmisor ESP32!"
    espnow.send(mac_receptor, message.encode())
    print("Mensaje enviado:", message)
    time.sleep(2)
