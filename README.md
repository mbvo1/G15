# La Ursa Walk
 La Ursa Walk é um projeto que promove caminhadas interativas pela área do Recife Antigo, incentivando a prática de atividade física enquanto proporciona uma experiência educativa sobre os pontos turísticos no bairro do Recife.
 
## Como utilizá-la?
- O usuário do programa deve aproximar um cartão no nariz do protótipo para dar início ao sistema
- Uma vez iniciado, as leds se acendem e se movimentam, silumando olhos
- Para cada passo, o usuário deve aproximar o seu cartão para prosseguir o programa, até ele ser encerrado
- Durante seu funcionamento, uma caixa dentro do protótipo reproduz áudios já gravados
- O funcionamento é bem prático e fácil, visto que o usuário só necessita aproximar um cartão no sensor para prosseguir

## Utilização do código:
---
### Link para baixar a IDE Arduino
[Clique aqui](https://www.arduino.cc/en/software)
### Bibliotecas necessárias:
#### Python:
- **Serial**
- **Pygame**

#### Arduino:
- **PN532**
- **NDEF**
- **Adafruit DMA Neopixel**

-**Como instalar as bibliotecas**: Abra a IDE do arduino, clique na aba que possui ícone de livros e escreva a biblioteca que deseja instalar na barra de pesquisas, depois clique em instalar. No python, digite import e o nome da bibloteca que você deseja usar.

---

### Códigos:

### Código de LEDs
#### Bibliotecas:
```c++
#include <Adafruit_NeoPixel.h>

#define PIN 7
#define NUMPIXELS 128 
#define BRIGHTNESS 28

Adafruit_NeoPixel pixels(NUMPIXELS, PIN, NEO_GRB + NEO_KHZ800);
```
- Você precisa ira utilizar o Adafruit DMA Neopixel que tem no library manager do arduino. 
##### Instalação de bibliotecas
1. Siga as instruções que estão na area de "Bibliotecas necessárias".

##### Olhos:
```c++
void displayPattern(int pattern[8][8]) {
  for (int y = 0; y < 8; y++) {
    for (int x = 0; x < 8; x++) {
      int pixelIndex1 = y * 8 + x;
      int pixelIndex2 = 64 + y * 8 + x;
      if (pattern[y][x] == 2) {
        pixels.setPixelColor(pixelIndex1, pixels.Color(210,105,30)); 
        pixels.setPixelColor(pixelIndex2, pixels.Color(210,105,30)); 
      } else if (pattern[y][x] == 1) {
        pixels.setPixelColor(pixelIndex1, pixels.Color(255, 255, 255)); 
        pixels.setPixelColor(pixelIndex2, pixels.Color(255, 255, 255));
      } else {
        pixels.setPixelColor(pixelIndex1, pixels.Color(0, 0, 0)); 
        pixels.setPixelColor(pixelIndex2, pixels.Color(0, 0, 0)); 
      }
    }
  }
  pixels.show();
}
```
- Aqui é configurado a cor do olho, é configurado pelo padrão de RGB, RED, GREEN e BLUE, como voce pode o 2 esta mais puxado para o vermelho
```c++
  int eyeOpen[8][8] = {
    {0, 0, 1, 1, 1, 1, 0, 0},
    {0, 1, 1, 1, 1, 1, 1, 0},
    {1, 1, 1, 0, 0, 1, 1, 1},
    {1, 1, 0, 2, 2, 0, 1, 1},
    {1, 1, 0, 2, 2, 0, 1, 1},
    {1, 1, 1, 0, 0, 1, 1, 1},
    {0, 1, 1, 1, 1, 1, 1, 0},
    {0, 0, 1, 1, 1, 1, 0, 0}
  };
```
- Aqui é bem intuitivo, os numeros 1 formam um íris enquanto o 2 a pupila do olho

### Posições dos pinos


### Codigo NFC
#### Bibliotecas:
```c++
#include <SoftwareSerial.h>
#include <PN532_SWHSU.h>
#include <PN532.h>
```
- Voce precisa importar as bibliotecas PN532, NDEF e a PN532_SWHSU que se encontra no [Github](https://github.com/elechouse/PN532), elas não existem no library manager do arduino IDE.
##### Instalação de bibliotecas
1. Estraia os arquivos do PN532-PN532_HSU
1. Compacte as bibliotecas PN532, NDEF e PN532_SWHSU no formato zip
1. Entre no arduino IDE
1. Va para sketch no canto superior esquerdo
1. Va para include library
1. Escolha Add .Zip library
1. Vá para a pasta onde estão os arquivos e os escolha 
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
- o "nfc.begin()" configura o nfc e o "nfc.getFirmwareVersion()" verifica se a versão está correta.

#### Temporizador:
```c++
void loop() {
  readNFC();
  delay(2000);
}
```
- A cada 2 segundos será lido um NFC, se ouver um NFC perto.


### Codigo de Audio em python

