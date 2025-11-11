# Fotorresistor LDR

Arquivo de configuração .yaml
```yaml
sensor:
    - platform: adc
        pin: GPIO34
        name: "Luminosidade"
        update_interval: 5s
        attenuation: 11db
        filters:
        - lambda: |-
            float voltage = x;
            float percentage = ((3.0 - voltage) / 2.8) * 100.0;
            if (percentage < 0.0) return 0.0;
            if (percentage > 100.0) return 100.0;
            return percentage;
        unit_of_measurement: "%"
        accuracy_decimals: 1
```