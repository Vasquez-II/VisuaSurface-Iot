# VisuaSurface-Iot: Transmissor Braille com ESP32 e Bluetooth Low Energy

Projeto de um sistema transmissor de caracteres em Braille utilizando um microcontrolador ESP32 e comunicação Bluetooth Low Energy (BLE).

O sistema recebe uma mensagem enviada por um dispositivo móvel, converte cada letra para sua representação em Braille e aciona seis saídas digitais correspondentes aos seis pontos de uma célula Braille.

## Objetivo

Desenvolver uma solução capaz de:

* receber textos por Bluetooth Low Energy;
* converter letras do alfabeto para o padrão Braille;
* representar cada caractere por meio de seis pontos;
* permitir a visualização sequencial das letras recebidas.

## Tecnologias utilizadas

* ESP32;
* Arduino IDE;
* linguagem C/C++;
* Bluetooth Low Energy;
* biblioteca BLE para ESP32.

## Funcionamento

O ESP32 cria um servidor BLE com o nome:

```text
ESP32_Braille_BLE
```

Após a conexão com um aplicativo compatível com BLE, o usuário pode enviar uma palavra ou mensagem.

Cada caractere é convertido para uma combinação de seis valores binários. Esses valores controlam os seis pinos associados aos pontos da célula Braille.

Cada letra permanece sendo exibida durante 2 segundos. Em seguida, a célula é limpa por 500 milissegundos antes da apresentação do próximo caractere.

## Pinos utilizados

| Ponto da célula Braille | GPIO do ESP32 |
| ----------------------- | ------------: |
| Ponto 1                 |             4 |
| Ponto 2                 |             5 |
| Ponto 3                 |             6 |
| Ponto 4                 |             7 |
| Ponto 5                 |            15 |
| Ponto 6                 |            16 |

## Comunicação BLE

O projeto utiliza os seguintes UUIDs:

```text
Service UUID:
6E400001-B5A3-F393-E0A9-E50E24DCCA9E

Characteristic RX UUID:
6E400002-B5A3-F393-E0A9-E50E24DCCA9E
```

A característica RX possui permissão de escrita e é responsável por receber as mensagens enviadas pelo dispositivo conectado.

## Como executar o projeto

1. Instale a Arduino IDE.
2. Adicione o suporte à placa ESP32.
3. Abra o arquivo:

```text
transmissor_braille_esp32.ino
```

4. Selecione a placa ESP32 utilizada.
5. Selecione a porta correspondente.
6. Compile e envie o código para a placa.
7. Abra o Monitor Serial com velocidade de `115200 baud`.
8. Conecte-se ao dispositivo `ESP32_Braille_BLE` utilizando um aplicativo compatível com BLE.
9. Envie uma palavra para visualizar sua tradução sequencial em Braille.

## Estrutura do projeto

```text
transmissor_braille_esp32/
├── transmissor_braille_esp32.ino
└── README.md
```

## Limitações atuais

* O sistema reconhece apenas letras de `A` a `Z`.
* Números, acentos e símbolos ainda não possuem representação implementada.
* As letras são apresentadas individualmente em uma única célula Braille.
* O tempo de apresentação dos caracteres é fixo.

## Possíveis melhorias

* adicionar suporte a números e caracteres acentuados;
* permitir a configuração do tempo de exibição;
* desenvolver um aplicativo próprio para envio das mensagens;
* adicionar múltiplas células Braille;
* implementar confirmação de recebimento por BLE;
* incluir controle de velocidade e pausa.

## Autores

Projeto desenvolvido por:

* **Gabi**
* **Nome do outro integrante**
