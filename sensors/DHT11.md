# DHT11

Para o uso do DHT11 no sistema, utilizamos as informações contidas no site do [ESPHome DHT Temperature+Humidity Sensor](https://esphome.io/components/sensor/dht/).

## Comunicação

O sensor DHT11 requer um resistor pull-up para os dados. Para isso, conectamos um resistor de 10kΩ entre os dados e o terminal 3.3V do ESP32. O recomendado é utilizar resistor de 4.7kΩ, mas resistor de 10kΩ é funcional. 

## Implementação

Para conecta-lo ao Home Assistant foi necessário ajustar o arquivo de configuração yaml do ESPHome para ler os dados captados do sensor.

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
- Parâmetros configuráveis: 
    - pin (Obrigatório, Pin): O pino onde o DHT está conectado
    - temperature (Obrigatório): A informação do sensor de temperatura.
        - Recebe todas as opções da configuração base dos sensores, consultado no seguinte site: [ESPHome Sensor Component](https://esphome.io/components/sensor/).
    - humidity (Obrigatório): A informação do sensor de umidade.
        - Recebe todas as opções da configuração base dos sensores, consultado no seguinte site: [ESPHome Sensor Component](https://esphome.io/components/sensor/).
    - model (Optional, int): Especificar manualmente o modelo do DHT, pode ser um desses AUTO_DETECT, DHT11, DHT22, DHT22_TYPE2, AM2302, RHT03, SI7021, AM2120. O padrão é AUTO_DETECT. Detecção automática não funciona no seguinte modelo SI7021.
    - update_interval (Opcional, Time): Intervalo entre os monitoramentos. Padrão é 60s.
***
***

# DHT11

For using the DHT11 in the system, we utilized the information contained on the [ESPHome DHT Temperature+Humidity Sensor](https://esphome.io/components/sensor/dht/) website.

## Comunication

The DHT11 sensor requires a pull-up resistor for data. For this, we connected a 10kΩ resistor between the data and the 3.3V terminal of the ESP32. The recommended resistor is 4.7kΩ, but a 10kΩ resistor is functional.

## Implementation

To connect it to Home Assistant, it was necessary to adjust the ESPHome yaml configuration file to read the data captured from the sensor.

Configuration file .yaml
```yaml
sensor:
    - platform: dht
        pin: GPIO5
        temperature:
            name: "DHT11 Temperature"
        humidity:
            name: "Humidity"
            model: DHT11
        update_interval: 5s
```
- Configurable parameters:
    - pin (Required, Pin): The pin where the DHT is connected
    - temperature (Required): The temperature sensor information.
        - Accepts all options from the sensor base configuration, found on the following website: [ESPHome Sensor Component](https://esphome.io/components/sensor/).
    - humidity (Required): The humidity sensor information.
        - Accepts all options from the sensor base configuration, found on the following website: [ESPHome Sensor Component](https://esphome.io/components/sensor/).
    - model (Optional, int): Manually specify the DHT model, can be one of these AUTO_DETECT, DHT11, DHT22, DHT22_TYPE2, AM2302, RHT03, SI7021, AM2120. The default is AUTO_DETECT. Auto detection does not work on the SI7021 model.
    - update_interval (Optional, Time): Interval between monitoring. Default is 60s.