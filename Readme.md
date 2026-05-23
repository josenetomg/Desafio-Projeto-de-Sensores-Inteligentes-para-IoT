# Desafio IoT: Projeto de Sensores Inteligentes para IoT
## Evolução da Detecção de Objetos e TinyML

Este desafio apresentou mais dois desafios a url citada não mais existe e o doc de descrição também não abre, ai restou apresentar o trabalho de outra forma.
O assunto e interessantissimo e a evolução no mesmo é contínua. 
Então resolvemos mudar um pouco a exposição e nos aprofundar com uma pesquisa sobre o que a de "novo" sobre este assunto.

Este projeto documenta a rápida transição da detecção de objetos de sistemas complexos baseados em PC para soluções de **TinyML** (Machine Learning em microcontroladores) que podem ser treinadas no navegador e executadas em um **Arduino Nano 33 BLE**.

## 1. A Evolução Tecnológica: Da Complexidade à Simplicidade

Até recentemente, implementar a detecção de objetos era um processo altamente técnico que exigia um sólido domínio de matemática aplicada e milhares de linhas de código. Sistemas baseados na biblioteca **ImageAI** permitiram simplificar essa tarefa, mas ainda dependiam de ambientes robustos:

*   **Requisitos Tradicionais:** Python 3.5.1+, TensorFlow, OpenCV, Keras e bibliotecas de suporte como Numpy e SciPy.
*   **Algoritmos Pesados:** Uso de modelos como **YOLOv3** (capaz de reconhecer 80 objetos diferentes) ou **RetinaNet**, que muitas vezes exigiam GPUs potentes para processamento em tempo real.
*   **Resultados:** A detecção era exibida com caixas delimitadoras e probabilidades em porcentagem em vídeos ou câmeras IP.

**Hoje**, ferramentas como o **Teachable Machine** permitem que qualquer pessoa treine modelos diretamente no navegador sem precisar programar, exportando versões reduzidas para microcontroladores.

## 2. Fluxo de Trabalho Moderna (Exemplo: Banana Madura)

Para resolver o desafio de classificar o estado de uma fruta (ex: **Banana Madura** vs. **Banana Verde**), seguimos um fluxo otimizado:

1.  **Hardware:** Conectamos uma câmera **OV7670** ao **Arduino Nano 33 BLE** usando cabos fêmea-fêmea.
2.  **Coleta de Dados:** Usando o sketch **TMUploader** no Arduino e o **TMConnector** no Processing, enviamos imagens em tempo real para o Teachable Machine.
3.  **Treinamento:** Gravamos amostras de bananas maduras e verdes no site e clicamos em "Treinar Modelo".
4.  **Exportação:** O modelo é convertido para **TensorFlow Lite para Microcontroladores** e baixado como um sketch pronto para o Arduino.

> **[INFOGRÁFICO: FLUXO DE IA EM MICROCONTROLADORES]**
>

## 3. Configuração de Hardware e Software

### Conexão dos Pinos (Câmera OV7670 para Arduino)
| OV7670 | Arduino Nano 33 BLE |
| :--- | :--- |
| 3.3V | 3.3V |
| SCL/SDA | A5 / A4 |
| VSYNC/HREF/PCLK | D8 / A1 / A0 |
| D7 a D0 | D4, D6, D5, D3, D2, RX, TX, D10 |

### Bibliotecas Necessárias
*   **Arduino IDE:** `Arduino_TensorFlowLite` (v2.4.0-ALPHA+) e `Arduino_OV767X`.
*   **Processing:** `ControlP5` e `Websockets`.

## 4. Resultados e Referências

Após carregar o modelo final no Arduino, os resultados de confiança (variando de **-128 a 127**) podem ser monitorados diretamente no **Monitor Serial** da IDE.

### Links de Referência
*   **Resultados em Vídeo (Método Tradicional):** [Detecção de Objetos com TensorFlow](https://youtu.be/xZW8j-umdgs).
*   **Artigo ImageAI:** [Detecting objects in videos and camera feeds](https://heartbeat.fritz.ai/detecting-objects-in-videos-and-camera-feeds-using-keras-opencv-and-imageai-c869fe1ebcdb).
*   **Guia TinyML:** [Getting Started with Embedded Teachable Machine](https://github.com/googlecreativelab/teachablemachine-community/blob/master/snippets/markdown/tiny_image/GettingStarted.md).

---

### Galeria de Processo

| Treinamento | Conexão de Dispositivo | Monitor Serial |
| :---: | :---: | :---: |
| ![Amostras de Treinamento](train_data.png) | ![Sketches de Conexão](sketches.png) | ![Monitor Serial](serial_mon.png) |
| *Interface de treinamento do modelo.* | *Preparação para envio de dados.* | *Confiança da detecção em tempo real.* |

---
*Este documento foi criado para fins educativos, demonstrando a facilidade das tecnologias modernas de IA incorporada.*
