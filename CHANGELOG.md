# Changelog

## 0.3.0 (2026-10-28)

- **Broker**: si annuncia via mDNS come `esp32-broker.local` (servizi `_mqtt._tcp` 1883 e `_http._tcp` 80).
- **Publisher**: `BROKER_IP` sostituito da `BROKER_NAME`; l'IP del broker si trova via mDNS all'avvio e di nuovo ogni 10 s
  finche' MQTT non e' connesso, quindi un cambio di IP del broker non richiede modifiche al codice. Il seriale distingue
  invii riusciti da `NON inviato`.
- **Docs**: aggiornati `README.md`, `docs/modules/broker.md`, `docs/modules/publisher.md`. `dashboard.md` rivisto, invariato.
- **Validazione**: `arduino-cli compile` riuscito per broker (`esp32`, 76% flash) e publisher (`esp32c3`, 81% flash).
  Non eseguiti: caricamento e smoke test hardware (broker non collegato al PC).

## 0.2.0 (2026-10-28)

- **Publisher**: portato sulla scheda ABrobot ESP32-C3 con OLED 0.42" (72x40, I2C SDA=GPIO5 / SCL=GPIO6):
  temperatura mostrata sul display, LED GPIO8 (attivo basso) lampeggia in connessione e a ogni invio,
  potenza TX Wi-Fi ridotta a 8.5 dBm per l'antenna debole della scheda. Nuova dipendenza U8g2, disattivabile con `USE_OLED 0`.
- **Broker/Publisher**: entrambi si collegano al router `Auricle` (`USE_ACCESS_POINT 0`). `BROKER_IP` va aggiornato
  con l'IP assegnato dal router al broker.
- **Docs**: aggiunti `README.md`, `VERSION`, `CHANGELOG.md`, `docs/INDEX.md` e `docs/modules/*.md`; commenti sorgente con
  rimando ai documenti; corretti i commenti del publisher non piu' validi in modalita' router.
- **Validazione**: `arduino-cli compile` riuscito per publisher (`esp32c3`) e broker (`esp32`).
  Non eseguiti: caricamento sulle schede e smoke test hardware (IP del broker non ancora noto, broker non collegato al PC).

## 0.1.0 (2026-10-28)

- **Iniziale**: broker MQTT + dashboard web su ESP32 in modalita' Access Point, publisher ESP32 con sensore interno.
