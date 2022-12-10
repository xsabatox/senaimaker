# Senai Maker - Guia do Usuário

Este é um guia para a configuração e utilização da impressora 3D Senai Maker.

## Instalação

- Faça o download do editor de código Visual Studio Code, disponível no endereço https://code.visualstudio.com/ e instale-o no seu computador.

- Após a instalação, abra o VSCode e instale as extensões Auto Build Marlin e PlatformIO IDE.

- Faça o download do firmware Marlin versão 2.1.x "bugfix" snapshot, disponvel no endereço https://github.com/MarlinFirmware/Marlin/archive/bugfix-2.1.x.zip

- Extraia o arquivo Marlin-bugfix-2.1.x.zip a pasta Marlin-bugfix-2.1.x no VSCode.

## Configuração

### Editando o arquivo ./Marlin/Configuration.h

- Defina o nome da impressora:

``` 
#define CUSTOM_MACHINE_NAME "Senai Maker"
```

- Defina o identificador único universal (UUID), que você pode gerar no endereço https://www.uuidgenerator.net/ (necessário para usar a impressora com junto com o OctoPrint):

```
#define MACHINE_UUID "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
```

- Defina o tipo do driver do motor Z2 (no exemplo abaixo está declarado o tipo A4988. Descubra o modelo do seu driver para alterar esta variável):

```
#define Z2_DRIVER_TYPE A4988
```

- Defina o sensor de temperatura da mesa aquecida:

```
#define TEMP_SENSOR_BED 1
```
