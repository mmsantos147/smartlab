# DHT11

Arquivo de configuração .yaml
```yaml
sensor:
    - platform: dht
        pin: GPIO5
        temperature:
        name: "Temperatura DHT11"
        humidity:
        name: "Umidade"
        model: DHT11
        update_interval: 5s
```