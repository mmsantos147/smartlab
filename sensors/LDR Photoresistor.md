# Fotorresistor LDR

Para o uso do Fotorresistor LDR no sistema, utilizamos as informações contidas no site do [ESPHome ADC Sensor](https://esphome.io/components/sensor/adc.html).

## Comunicação

O fotorresistor LDR (Light Dependent Resistor) é um componente que varia sua resistência de acordo com a intensidade de luz incidente. Para realizar a leitura, o sensor é conectado em um divisor de tensão e o ESP32 lê o valor analógico através de um conversor ADC (Analog-to-Digital Converter).

O fotorresistor utiliza um pino ADC do ESP32 (GPIO34) que converte o sinal analógico (tensão variável de 0V a 3.3V) em um valor digital que pode ser processado pelo microcontrolador.

## Implementação

Para conectá-lo ao Home Assistant foi necessário ajustar o arquivo de configuração yaml do ESPHome para ler os dados captados do sensor.

Arquivo de configuração .yaml:
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

- Parâmetros configuráveis:
  - sensor
    - platform: adc - Define que o sensor utiliza o conversor analógico-digital
    - pin (Obrigatório, Pin): O pino ADC onde o fotorresistor está conectado
      - Neste caso: GPIO34
      - Nota: Apenas alguns pinos do ESP32 possuem capacidade ADC (GPIO32-GPIO39)
    - name (Obrigatório): Nome que aparecerá no Home Assistant
      - Luminosidade: Nome descritivo do sensor
    - attenuation (Opcional): Define a atenuação do ADC, que determina a faixa de tensão máxima de leitura
      - 11db: Permite leitura de 0V a ~3.3V (faixa completa)
      - Outras opções: 0db (0-1.1V), 2.5db (0-1.5V), 6db (0-2.2V)
      - Padrão: 0db
    - update_interval (Opcional, Time): Intervalo entre os monitoramentos
      - Padrão: 60s
    - filters (Opcional): Filtros para processar os dados brutos
      - lambda: Permite executar código C++ customizado para transformar o valor lido
        - Neste caso: converte a tensão lida em percentual de luminosidade (0-100%)
        - x: representa o valor de tensão lido (0-3.3V)
    - unit_of_measurement (Opcional): Unidade de medida exibida
      - %: Percentual de luminosidade
    - accuracy_decimals (Opcional, int): Número de casas decimais
      - 1: Exibe uma casa decimal (ex: 45.3%)
      - Padrão: varia conforme o sensor

## Circuito

<img src="images/esquema luz editado.png" alt="Exemplo de Automação" width="500">

***

# LDR Photoresistor

For using the LDR Photoresistor in the system, we utilized the information contained on the [ESPHome ADC Sensor](https://esphome.io/components/sensor/adc.html) website.

## Communication

The LDR (Light Dependent Resistor) photoresistor is a component that varies its resistance according to the incident light intensity. To perform the reading, the sensor is connected in a voltage divider and the ESP32 reads the analog value through an ADC (Analog-to-Digital Converter).

The photoresistor uses an ADC pin of the ESP32 (GPIO34) that converts the analog signal (variable voltage from 0V to 3.3V) into a digital value that can be processed by the microcontroller.

## Implementation

To connect it to Home Assistant, it was necessary to adjust the ESPHome yaml configuration file to read the data captured from the sensor.

Configuration file .yaml:
```yaml
sensor:
    - platform: adc
        pin: GPIO34
        name: "Luminosity"
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

- Configurable parameters:
  - sensor
    - platform: adc - Defines that the sensor uses the analog-to-digital converter
    - pin (Required, Pin): The ADC pin where the photoresistor is connected
      - In this case: GPIO34
      - Note: Only some ESP32 pins have ADC capability (GPIO32-GPIO39)
    - name (Required): Name that will appear in Home Assistant
      - Luminosity: Descriptive name of the sensor
    - attenuation (Optional): Defines the ADC attenuation, which determines the maximum voltage reading range
      - 11db: Allows reading from 0V to ~3.3V (full range)
      - Other options: 0db (0-1.1V), 2.5db (0-1.5V), 6db (0-2.2V)
      - Default: 0db
    - update_interval (Optional, Time): Interval between monitoring
      - 5s: Updates every 5 seconds
      - Default: 60s
    - filters (Optional): Filters to process raw data
      - lambda: Allows executing custom C++ code to transform the read value
        - In this case: converts the read voltage into luminosity percentage (0-100%)
        - x: represents the voltage value read (0-3.3V)
    - unit_of_measurement (Optional): Unit of measurement displayed
      - %: Luminosity percentage
    - accuracy_decimals (Optional, int): Number of decimal places
      - 1: Displays one decimal place (e.g., 45.3%)
      - Default: varies according to the sensor

## Circuit

<img src="images/esquema luz editado.png" alt="Exemplo de Automação" width="500">