# Senai Maker - Guia do Usuário

Este é um guia para a configuração e utilização da impressora 3D Senai Maker.

## Instalação

- Faça o download do editor de código Visual Studio Code, disponível no endereço https://code.visualstudio.com/ e instale-o no seu computador.

- Após a instalação, abra o VSCode e instale as extensões Auto Build Marlin e PlatformIO IDE.

- Faça o download do firmware Marlin versão 2.1.x "bugfix" snapshot, disponvel no endereço https://github.com/MarlinFirmware/Marlin/archive/bugfix-2.1.x.zip

- Extraia o arquivo Marlin-bugfix-2.1.x.zip a pasta Marlin-bugfix-2.1.x no VSCode.

## Configuration.h

### Getting Started

- Defina o nome da impressora:

``` 
#define CUSTOM_MACHINE_NAME "Senai Maker"
```

- Defina o identificador único universal (UUID), que você pode gerar no endereço https://www.uuidgenerator.net/ (necessário para usar a impressora com junto com o OctoPrint):

```
#define MACHINE_UUID "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
```

- Defina o tipo do driver do motor Z2. Descubra o modelo do seu driver para alterar esta variável, no exemplo abaixo está declarado o tipo A4988:

```
#define Z2_DRIVER_TYPE A4988
```
### Thermal Settings

- Defina o sensor de temperatura da mesa aquecida:

```
#define TEMP_SENSOR_BED 1
```
### PID Settings

- Defina o controle de temperatura da extrusora por PID (Proporção, Integral e Derivada):

```
#define PIDTEMP
```

- Defina o controle de temperatura da mesa aquecida por PID (Proporção, Integral e Derivada):

```
#define PIDTEMPBED
```

- Defina a temperatura mínima para o funcionamento da extrusora:

```
#define EXTRUDE_MINTEMP 190
```
### Endstop Settings

- Se ao solicitar um retorno à origem (auto home) algum motor de passo não esteja chegando ao fim de curso, inverta a lógica do fim de curso. No caso abaixo, todos foram invertidos:

> :information_source: **O Z_MAX_ENDSTOP foi usado como fim de curso do segundo motor do eixo Z.**

```
#define X_MIN_ENDSTOP_INVERTING true
#define Y_MIN_ENDSTOP_INVERTING true
#define Z_MIN_ENDSTOP_INVERTING true
#define Z_MAX_ENDSTOP_INVERTING true
```
### Movement Settings

- Defina os valores padrão de passos por unidade de medida (mm), para o eixo X, eixo Y, eixo Z e extrusora, respectivamente. Este valores devem ser calibrados. 
    - Para calibrar o motor de passo da extrusora deve-se comparar a medida do filamento movimentado pelo motor de passo da extrusora (sem passar pelo bloco aquecedor ou a cabeça de impressão) e a medida descrita no firmware. 
    - Para calibrar os motores dos eixos X, Y e Z deve-se imprimir um cubo para verificar a diferença entre as medidas do impresso e a medida descrita no modelo 3D.

> :warning: **ATENÇÃO! Caso você tenha habilitado o EEPROM (#define EEPROM_SETTINGS) os valores salvos lá sobreescreverão os definidos aqui!**

```
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, 100 }
```

[...]


### LCD Controller Section

- Defina o tipo de tela LCD da impressora. Descubra o modelo da sua tela LCD para alterar esta variável, no exemplo abaixo está declarado o modelo RepRap (tela azul com caracteres brancos):

```
#define REPRAP_DISCOUNT_SMART_CONTROLLER
```
