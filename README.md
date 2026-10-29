[README.md](https://github.com/user-attachments/files/34126653/README.md)
# ESP32 MQTT Temperatura

![version](https://img.shields.io/badge/version-0.3.0-blue)

Due schede: un **broker** ESP32 (broker MQTT + dashboard web) e un **publisher**
ABrobot ESP32-C3 che invia la temperatura interna del chip sul topic
`esp32/temperatura`.

- **Versione:** vedi `VERSION` (attuale `0.3.0`)
- **Stadio:** Alpha (`0.x.y`). Prototipo didattico, nessun criterio di rilascio GA definito.
- **Standard:** `GOLDEN_STD.md` 1.5.0 + addendum *Embedded Firmware & IoT*.
- **Branch di integrazione:** nessuno, la cartella non e' sotto git.
- **Documentazione moduli:** [`docs/INDEX.md`](docs/INDEX.md)

## Sorgenti di verita' (§16)

| File | Tipo | Come si aggiorna |
|---|---|---|
| `broker/broker.ino` | sorgente, modificabile | a mano |
| `publisher/publisher.ino` | sorgente, modificabile | a mano |
| `index.html` | sorgente della dashboard | a mano (si apre anche dal PC in modalita' demo) |
| `broker/index_html.h` | **generato** da `index.html` | copia manuale di `index.html` dentro `R"rawliteral( ... )rawliteral"` |

## Avvio rapido

1. Library Manager: installa **PicoMQTT** (entrambe le schede) e **U8g2** (solo publisher).
2. Imposta la stessa rete Wi-Fi in entrambi gli sketch (`STA_SSID`/`STA_PASS` nel broker,
   `WIFI_SSID`/`WIFI_PASS` nel publisher).
3. Carica `broker/broker.ino` sull'ESP32 broker e `publisher/publisher.ino` sull'ABrobot
   (scheda *ESP32C3 Dev Module*, *USB CDC On Boot = Enabled*). Il publisher trova il broker
   da solo via mDNS (`esp32-broker.local`): non serve conoscere l'IP.
4. Apri `http://esp32-broker.local` da un dispositivo sulla stessa rete Wi-Fi
   (se il dispositivo non supporta `.local`, usa l'IP stampato dal broker sul Serial Monitor).

## Build da riga di comando

```bash
CLI="/c/Program Files/Arduino IDE/resources/app/lib/backend/resources/arduino-cli.exe"
"$CLI" compile -b esp32:esp32:esp32 broker
"$CLI" compile -b esp32:esp32:esp32c3:CDCOnBoot=cdc publisher
```
