# Icaro-I (Aviônica Aurora V1.0)

## Introdução 

### Motivação

A equipe Antares de espaçomodelismo da Unicamp tem como um de seus projetos desenvolvidos o foguete Aurora. Trata-se de um foguete de propulsão sólida com apogeu esperado de 1km. Como parte dos requisitos necessários para ter sucesso na missão, o foguete precisa de um sistema de aviônica que será responsável por coletar dados e tomar decisões previamente programadas durante o voo. 

### Objetivo

Sendo assim, o objetivo deste projeto é desenvolver um sistema de aviônica capaz de detectar o apogeu programado e acionar o sistema de recuperação. Deve também ser capaz de transmitir os dados de voo ao solo em tempo real e coletar informações sobre a posição do foguete, possibilitando sua localização após aterrisagem. Além disso, deve ser dimensionada para caber na estrutura interna do foguete.

### Soluções comerciais

Pelo fato de o sistema precisar ser personalizado, se ajustando ao sistema presente no foguete e aos demais requisitos específicos do projeto, não existem alternativas comerciais que cumpram integralmente o objetivo.

## Especificação
    - Microcontrolador: o dispositivo deverá ser capaz de fazer processamentos lógicos, sendo assim necessário um microcontrolador. Por motivos de acessibilidade e familiaridade, será utilizada a plataforma Arduino no MCU ESP-8266 12F.

    - Comunicação e dados: com o objetivo de enviar dados de telemetria do foguete, o dispositivo deverá ter um sistema transceptor, que será implementado por um módulo LoRA E32-915T20D. Além disso, contará com uma interface para cartão MicroSD, possibilitando que os dados brutos sejam armazenados para uma análise mais precisa posterior.

    - Interface: como interface, o dispositivo contará com conectores para alimentação externa, além de pinos seletores, que selecionam, principalmente, se o sistema é o principal ou uma redundância e se o acionamento será interno ou externo (para testes).

    - Ignição: a aviônica precisa implementar um sistema de ignição que será o responsável pela liberação da recuperação.

    - Alimentação: o sistema tem interface de alimentação externa.

    - Redundância: o dispositivo implementa solução para um sistema com redundância nos subsistemas críticos, provendo maior segurança.

    - Localização: a fim de garantir que seja possível localizar o foguete após o pouso, o sistema deve ser capaz de transmitir a posição em tempo real por meio de um sistema GPS e de emitir um aviso sonoro por meio de um buzzer.

    - Detecção de apogeu: para ser capaz de detectar o momento do apogeu, a aviônica deve implementar um altímetro.


## Pinagem

### Pinout conector Screw bateria 18650

Pino | Sinal
-----|------
1  | VBat
2  | GND

### Pinout conector Screw do Acionamento

Pino | Sinal
-----|------
  1  | NiCr_ISO
  2  | GND_ISO

### Pinout conector Screw da Redundancia

Pino | Sinal
-----|------
  1  | Redundancy_IN
  2  | Redundancy_OUT


### Pinout conector Seleção Redundância

Pino | Sinal
-----|------
  1  | Redundancy_OUT
  2  | IGN
  3  | Main_IGN

### Pinout conector Transistor PNP acionamento (interno)

Pino | Sinal
-----|------
  1  | Emissor
  2  | Coletor

### Pinout conector Optoacoplador acionamento (externo)

Pino | Sinal
-----|------
  1  | Coletor
  2  | Emissor


## Testes

    A fim de garantir que o sistema seja seguro e que tudo funcione como esperado, é necessário realizar testes controlados de cada parte do sistema, tentando antecipar possíveis falhas que possam ocorrer. 
    Como o sistema de ignição não pode ter acionamento indesejado, devem ocorrer testes em ambientes adversos, como, por exemplo, com componentes desconectados, e o resultado esperado é que o sistema não ative em nenhuma dessas situações.
    Além disso, todos os sensores presentes devem ser validados.

