# Senai Maker - Guia do Usuário

Este é um guia para a configuração e utilização da impressora 3D Senai Maker.

## Instalação

- Faça o download do editor de código Visual Studio Code, disponível no endereço https://code.visualstudio.com/ e instale-o no seu computador.

- Após a instalação, abra o VSCode e instale as extensões Auto Build Marlin e PlatformIO IDE.

- Faça o download do firmware Marlin versão 2.1.x "bugfix" snapshot, disponvel no endereço https://github.com/MarlinFirmware/Marlin/archive/bugfix-2.1.x.zip

- Extraia o arquivo Marlin-bugfix-2.1.x.zip a pasta Marlin-bugfix-2.1.x no VSCode.

---

## Configuration.h

### Getting Started

- Determine as informações do autor das alterações no arquivo de configuração:

``` 
#define STRING_CONFIG_H_AUTHOR "(nome do autor, SENAI config)"
``` 

- Determine o nome da impressora:

``` 
#define CUSTOM_MACHINE_NAME "Senai Maker"
```

- Determine o identificador único universal - UUID (necessário para usar a impressora com junto com o OctoPrint):

> :information_source: Você pode gerar no endereço https://www.uuidgenerator.net/ 

```
#define MACHINE_UUID "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
```

- Determine o tipo do driver do motor Z2. Descubra o modelo do seu driver para alterar esta variável, no exemplo abaixo está declarado o tipo A4988:

```
#define Z2_DRIVER_TYPE A4988
```

### Thermal Settings

- Habilite o sensor de temperatura da mesa aquecida:

```
#define TEMP_SENSOR_BED 1
```

- Determine uma janela de tempo maior para o aquecimento da mesa aquecida:

```
 #define TEMP_BED_RESIDENCY_TIME 20
```

### PID Settings

- Habilite o controle de temperatura da extrusora por PID (Proporção, Integral e Derivada):

```
#define PIDTEMP
```

- Habilite o controle de temperatura da mesa aquecida por PID (Proporção, Integral e Derivada):

```
#define PIDTEMPBED
```

- Determine a temperatura mínima para o funcionamento da extrusora:

```
#define EXTRUDE_MINTEMP 170
```

### Endstop Settings

- Habilite o fim de curso do segundo motor de passo do eixo Z:

```
#define USE_ZMAX_PLUG
```

- Se ao solicitar um retorno à origem (auto home) algum motor de passo não esteja chegando ao fim de curso, habilite a inversão da lógica do fim de curso (no exemplo abaixo todos foram invertidos):

> :information_source: O Z_MAX_ENDSTOP foi usado como fim de curso do segundo motor do eixo Z.

```
#define X_MIN_ENDSTOP_INVERTING true
#define Y_MIN_ENDSTOP_INVERTING true
#define Z_MIN_ENDSTOP_INVERTING true
#define Z_MAX_ENDSTOP_INVERTING true
```
### Movement Settings

> :warning: **ATENÇÃO! Caso você tenha habilitado o uso da EEPROM (#define EEPROM_SETTINGS) os valores salvos lá sobreescreverão os definidos aqui!**

- Determine os valores padrão de passos por unidade de medida (mm), para o eixo X, eixo Y, eixo Z e extrusora, respectivamente. Este valores devem ser calibrados. 
    - Para calibrar o motor de passo da extrusora deve-se comparar a medida do filamento movimentado pelo motor de passo da extrusora (sem passar pelo bloco aquecedor ou a cabeça de impressão) e a medida descrita no firmware. 
    - Para calibrar os motores dos eixos X, Y e Z deve-se imprimir um cubo para verificar a diferença entre as medidas do impresso e a medida descrita no modelo 3D.

```
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, 100 } // X, Y, Z, E0
```

- Caso o movimento de algum motor de passo esteja invertido, inverta o conector do motor na placa de impressão ou determine a inversão do movimento (no exemplo abaixo o motor de passo do eixo Y foi invertido):
```
#define INVERT_X_DIR false
#define INVERT_Y_DIR true
#define INVERT_Z_DIR false
```

- Habilite a sondagem manual para nivelar a mesa aquecida sem uma sonda:

```
#define PROBE_MANUALLY
```

- Habilite o nivelamento da mesa aquecida em malha/grid:

```
#define MESH_BED_LEVELING
```

- Habilite o sub-menu de nivelamento da mesa aquecida no painel LCD:

```
#define LCD_BED_LEVELING
```

### Additional Features

- Habilite o armazenamento persistente das configurações entre reinícios da impressora:

```
#define EEPROM_SETTINGS 
```

### LCD and SD Support

- Determine a linguagem usada na tela LCD:

```
#define LCD_LANGUAGE pt_br
```

- Habilite o suporte a cartão SD:

```
#define SDSUPPORT
```

- Habilite a verificação cíclica de redundância (CRC) do cartão SD:

```
#define SD_CHECK_AND_RETRY
```

- Determine o tipo de tela LCD da impressora. O exemplo abaixo está declarado o modelo RepRap (tela azul com caracteres brancos):

```
#define REPRAP_DISCOUNT_SMART_CONTROLLER
```

---

Configuration_adv.h

- Habilite múltiplos fim de curso para o eixo Z:

```
#define Z_MULTI_ENDSTOPS
```

- Habilite o auto alinhamento do eixo Z:

```
#define Z_STEPPER_AUTO_ALIGN
```
