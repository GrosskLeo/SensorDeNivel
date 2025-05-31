# Sistema de Alerta de Nível de Água com Detecção por Sensor Ultrassônico #

Este projeto tem como objetivo desenvolver um sistema de alerta simples e eficiente para monitoramento do nível da água em ambientes sujeitos a alagamentos, como rios, lagos, bueiros ou ruas. A solução foi desenvolvida utilizando a plataforma Arduino Uno, com simulação feita via Wokwi.

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
