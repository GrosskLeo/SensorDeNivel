# Sistema de Alerta de Nível de Água com Detecção por Sensor Ultrassônico #

Este projeto tem como objetivo desenvolver um sistema de alerta simples e eficiente para monitoramento do nível da água em ambientes sujeitos a alagamentos, como rios, lagos, bueiros ou ruas. A solução foi desenvolvida utilizando a plataforma Arduino Uno, com simulação feita via Wokwi. Você pode acessar a simulação pelo [link](https://wokwi.com/projects/432484773644440577)

![ChatGPT Image 31 de mai  de 2025, 13_37_11](https://github.com/user-attachments/assets/4fa18e27-5cca-44eb-ab75-77efd93a49b3)


## 📌 Descrição do Projeto ##

O sistema utiliza um sensor ultrassônico para medir continuamente a distância entre o sensor e a superfície da água. Quando é detectado um movimento de aproximação da água além de um limite pré-estabelecido — indicando possível transbordamento — o sistema emite um aviso visual ao usuário por meio de um LED vermelho e uma mensagem em um display LCD.
⚙️ Componentes Utilizados

   Arduino Uno

   Sensor ultrassônico (HC-SR04)

   LED vermelho

   Display LCD 16x2 com interface I2C

   Resistores

   Jumpers e protoboard (emuladas na simulação)

## 🎯 Objetivo 

O objetivo principal do sistema é emitir alertas visuais imediatos em caso de risco de alagamento, contribuindo para ações preventivas em áreas vulneráveis. É um sistema simples, de baixo custo e ideal para fins educacionais, testes e até mesmo implementação em protótipos reais.
## 🧠 Funcionamento

   O sensor ultrassônico realiza medições contínuas da distância até a superfície abaixo dele.

   Se a água se aproxima do sensor além de um limite seguro (por exemplo, indicando que o nível está subindo rapidamente), o sistema ativa um LED vermelho.

   Simultaneamente, uma mensagem de alerta é exibida no display LCD, indicando a situação ao usuário.

   ![ChatGPT Image 31 de mai  de 2025, 13_39_20](https://github.com/user-attachments/assets/e8f87c8c-e28d-4652-963c-fc93b6692d0c)

## 🛠️ Possibilidades de Expansão

   Inclusão de comunicação via Wi-Fi ou GSM para envio de alertas remotos (SMS, e-mail ou app).

   Registro de dados em nuvem para análise histórica de níveis de água.

   Integração com sirenes ou outros dispositivos de alarme.
 

## 📍 Aplicações

   Monitoramento de rios e córregos urbanos

   Controle de níveis em caixas d’água e reservatórios

   Alerta em áreas urbanas sujeitas a enchentes

## 👥 Autores

   Leonardo Grosskopf (RM: 562255)

   Julia Schiavi (RM: 562418)

   Thayná Lopes (RM: 566349)

## 📺 Vídeo

   [Link para acessar o vídeo](https://drive.google.com/file/d/1CXTy4Ln-UYjAq3As-CGXwS6C0kyddf-Q/view?usp=sharing)

## 💻 Código

      // Inclui as bibliotecas necessárias
      #include <Wire.h>
      #include <LiquidCrystal_I2C.h>

      // Define os pinos para o sensor ultrassônico
      const int trigPin = 9;
      const int echoPin = 10;

      // Define o pino para o LED
      const int ledPin = 8;

      // Define a distância limite (em cm) para considerar o nível alto
      // Ajuste este valor conforme a necessidade do seu recipiente
      const int nivelAltoDistancia = 10;
      
      // Inicializa o LCD no endereço I2C 0x27 (pode variar), para um display 16x2
      LiquidCrystal_I2C lcd(0x27, 16, 2);
      
      // Variáveis para armazenar a duração do pulso e a distância
      long duration;
      int distance;
      
      void setup() {
        // Inicializa a comunicação serial para debug (opcional)
        Serial.begin(9600);
      
        // Inicializa o LCD
        lcd.init();
        lcd.backlight();
        lcd.setCursor(0, 0);
        lcd.print("Sensor Nivel");
        lcd.setCursor(0, 1);
        lcd.print("de Água");
        delay(1000);
        lcd.clear();
      
        // Define os pinos do sensor ultrassônico
        pinMode(trigPin, OUTPUT); // Pino TRIG como saída
        pinMode(echoPin, INPUT);  // Pino ECHO como entrada
      
        // Define o pino do LED como saída
        pinMode(ledPin, OUTPUT);
        digitalWrite(ledPin, LOW); // Garante que o LED comece desligado
      }
      
      void loop() {
        // Limpa o pino TRIG
        digitalWrite(trigPin, LOW);
        delayMicroseconds(2);
      
        // Define o pino TRIG em HIGH por 10 microsegundos para enviar o pulso ultrassônico
        digitalWrite(trigPin, HIGH);
        delayMicroseconds(10);
        digitalWrite(trigPin, LOW);
      
        // Lê o pino ECHO, retorna a duração do pulso em microsegundos
        duration = pulseIn(echoPin, HIGH);
      
        // Calcula a distância
        // Velocidade do som no ar = 343 m/s ou 0.0343 cm/µs
        // Distância = (Tempo do pulso * Velocidade do som) / 2 (ida e volta)
        distance = duration * 0.0343 / 2;
      
        // Limpa o LCD
        lcd.clear();
        lcd.setCursor(0, 0);
        lcd.print("Distancia: ");
        lcd.print(distance);
        lcd.print("cm");
      
        // Verifica se o nível da água está alto
        if (distance <= nivelAltoDistancia && distance > 0) { // distance > 0 para evitar leituras inválidas
          lcd.setCursor(0, 1);
          lcd.print("Nivel Alto!");
          digitalWrite(ledPin, HIGH); // Acende o LED
          Serial.print("Distancia: ");
          Serial.print(distance);
          Serial.println("cm");
        } else {
          lcd.setCursor(0, 1);
          lcd.print("Nivel OK");
          digitalWrite(ledPin, LOW); // Apaga o LED
          Serial.print("Distancia: ");
          Serial.print(distance);
          Serial.println("cm");
        }
      
        // Aguarda 500ms antes da próxima leitura
        delay(500);
      }



   
   
