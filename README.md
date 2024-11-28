# La Ursa Walk
 La Ursa Walk é um projeto que promove caminhadas interativas pela área do Recife Antigo, incentivando a prática de atividade física enquanto proporciona uma experiência educativa sobre os pontos turísticos no bairro do Recife.

## Utilização do código:
---
### Bibliotecas necessárias:
#### Python:
-**Serial**
-**Pygame**

#### Arduino:
-**PN532**
-**NDEF**
-**Adafruit DMA Neopixel**

-**Como instalar as bibliotecas**: Abra a IDE do arduino, clique na aba que possui ícone de livros e escreva a biblioteca que deseja instalar na barra de pesquisas, depois clique em instalar. No python, digite import e o nome da bibloteca que você deseja usar.

---

### Codigo
- Explicar codigo LEDs
- E a posicao dos pinos que sao conectados
- Explicar codigo NFC
- Explicar codigo audio python
- Explicar as partes mais importantes desses codigos 

### Codigo de LEDs


### Posições dos pinos


### Codigo NFC
#### Bibliotecas:
```c++
#include <SoftwareSerial.h>
#include <PN532_SWHSU.h>
#include <PN532.h>
```
- Voce precisa importar as bibliotecas PN532, NDEF e a PN532_SWHSU que se encontra no [Github](https://github.com/elechouse/PN532)
##### Instalação de bibliotecas
1. Estraia os arquivos do PN532-PN532_HSU
1. Compacte as bibliotecas PN532, NDEF e PN532_SWHSU no formato zip
1. Entre no arduino IDE
1. Va para sketch no canto superior esquerdo
1. Va para include library
1. Escolha Add .Zip library
1. Va para a pasta onde estão os arquivos e escolha eles
#### Serial e NFC:
```c++
void setup(void) {
  Serial.begin(115200);
  Serial.println("Hello Maker!");
  
  nfc.begin();

  uint32_t versiondata = nfc.getFirmwareVersion();
  if (! versiondata) {
    Serial.print("Didn't Find PN53x Module");
    while (1);
  }
}
```
- Certifiquece que a comunicação serial seja __115200__.
- o "nfc.begin()" configura o nfc e o "nfc.getFirmwareVersion()" verifica se a versão esta correta.

#### Temporizador:
```c++
void loop() {
  readNFC();
  delay(2000);
}
```
- A cada 2 segundos o sera lido um NFC, se ouver um NFC perto.


### Codigo de Audio em python

