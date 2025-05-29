


# 🌊 Sistema de Alerta para Nível de Água com Arduino

Este projeto apresenta um **sistema de alerta para monitoramento do nível da água** desenvolvido com **Arduino UNO** e simulado na plataforma **Wokwi**. O sistema é projetado para alertar o usuário sobre o risco de **transbordamento em rios, lagos ou vias públicas** por meio de sinais **visuais e sonoros**, utilizando **LEDs (verde e vermelho)**, um **buzzer** e um **display LCD 16x2** com interface I2C.

🔗 [Simulação no Wokwi](https://wokwi.com/projects/432217472355232769)

---

## 📌 Objetivo

O objetivo do sistema é oferecer uma **solução simples, acessível e eficiente** para alertar a população ou operadores sobre situações de risco relacionadas ao aumento do nível da água, como enchentes ou alagamentos. É ideal para uso em áreas ribeirinhas, regiões urbanas com histórico de alagamentos, ou como sistema auxiliar de defesa civil.

---

## 🔧 Componentes Utilizados

* **Arduino UNO**
* **Sensor PIR (simulando o acionamento em caso de água em determinado nível)**
* **LED Verde** – Indica condição normal (nível de água seguro)
* **LED Vermelho** – Indica alerta de nível elevado
* **Buzzer** – Emite alarme sonoro quando o nível de água está crítico
* **Display LCD 16x2 I2C** – Exibe o status do sistema
* **Jumpers e resistores**
* **Simulação online via Wokwi**

---

## ⚙️ Funcionamento do Sistema

Embora o sistema utilize um **sensor PIR** na simulação do Wokwi, este representa de forma conceitual o **gatilho de alerta** causado por sensores de nível d'água (como sensores ultrassônicos, de boia ou resistivos, que podem ser implementados em uma versão física).

1. **Nível de água normal:**

   * **LED verde** aceso
   * **LED vermelho** e **buzzer** desligados
   * **Display** exibe: `Nível seguro`

2. **Nível de água elevado (sensor ativado):**

   * **LED vermelho** aceso
   * **LED verde** apagado
   * **Buzzer** emite alarme
   * **Display** exibe: `Risco de Alagamento!`

Esse comportamento permite alertar rapidamente usuários e autoridades sobre a necessidade de evacuação ou de medidas preventivas.

---

## ▶️ Como Testar

Você pode simular o funcionamento completo do sistema diretamente no Wokwi:

🔗 [Clique aqui para abrir a simulação](https://wokwi.com/projects/432217472355232769)

Para utilizar em hardware real:

1. Instale o [Arduino IDE](https://www.arduino.cc/en/software)
2. Instale a biblioteca `LiquidCrystal_I2C` via Gerenciador de Bibliotecas
3. Monte o circuito conforme o esquema da simulação
4. Faça upload do código `.ino` para sua placa Arduino UNO

---

## 📁 Estrutura do Projeto

```
├── main.ino           # Código principal do Arduino
├── README.md          # Documentação do projeto
```

---

## 💡 Possíveis Melhorias

* Substituir o sensor PIR por sensor de nível d'água real (ultrassônico, boia, condutivo, etc.)
* Adicionar módulo Wi-Fi (ESP8266/ESP32) para envio de alertas por internet
* Integração com sistema de SMS, aplicativo ou plataforma de monitoramento
* Registro histórico dos níveis em cartão SD ou servidor remoto

---

## 👨‍💻 Autores

* **Leonardo Grosskopf** – RM: 562255
* **Julia Schiavi** – RM: 562418
* **Thayná Lopes** – RM: 566349


