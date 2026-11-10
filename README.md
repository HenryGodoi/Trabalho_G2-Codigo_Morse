# Código Morse por infravermelho

Atividade de aula (Trabalho G2) do curso de Sistemas de Informação da Antonio Meneghetti Faculdade, em 2026. Dois Arduinos trocam mensagens em código Morse usando luz infravermelha: um transmite, o outro recebe e decodifica. Cada Arduino tem uma página web própria, que conversa com ele pelo cabo USB.

![Interface receptora mostrando a mensagem decodificada "PENSAMENTO COMPUTACIONAL"](WhatsApp%20Image%202026-06-23%20at%2020.30.21.jpeg)

## Como funciona

1. Na **Interface 1 (transmissora)**, a pessoa digita uma mensagem e clica em "Enviar Mensagem via IR". A página manda o texto para a Máquina 1 pela porta serial.
2. A **Máquina 1** converte cada letra e número em Morse e pisca o LED infravermelho: 200 ms para o ponto e 600 ms para o traço, com pausas de 600 ms entre letras e 1400 ms entre palavras. No fim, manda um pulso longo de 1200 ms que marca o fim da mensagem.
3. A **Máquina 2** lê o fototransistor, mede quanto tempo dura cada pulso de luz e decide se é ponto, traço ou fim de mensagem. Os silêncios separam as letras e as palavras.
4. A **Interface 2 (receptora)** mostra ao vivo os pontos e traços recebidos, o código Morse completo e a palavra decodificada.

## Componentes

- 2 placas Arduino, uma para cada máquina
- LED infravermelho no pino 3 da Máquina 1
- Fototransistor com resistor de 10 kΩ em divisor de tensão, ligado ao pino A0 da Máquina 2
- LED do pino 13 de cada placa, que acende junto com a luz enviada ou recebida
- 2 cabos USB para ligar as placas ao computador

O circuito foi montado de verdade e depois desmontado. As fotos e os vídeos abaixo mostram o projeto funcionando.

<img src="WhatsApp%20Image%202026-06-23%20at%2020.30.04.jpeg" alt="Arduino ligado ao computador com a protoboard do circuito infravermelho" width="300">

## Fotos e vídeos

- [Vídeo 1 do funcionamento](WhatsApp%20Video%202026-06-23%20at%2020.27.50.mp4)
- [Vídeo 2 do funcionamento](WhatsApp%20Video%202026-06-23%20at%2020.28.17.mp4)
- Outras fotos: [1](WhatsApp%20Image%202026-06-23%20at%2020.30.04%20%281%29.jpeg), [2](WhatsApp%20Image%202026-06-23%20at%2020.30.10.jpeg), [3](WhatsApp%20Image%202026-06-23%20at%2020.30.10%20%281%29.jpeg)
- A apresentação do trabalho está em `Trabalho G2- Código Morse.docx`.

## Como rodar

1. Grave `Maquina 1.ino` na placa transmissora e `Maquina 2.ino` na receptora, pela Arduino IDE.
2. Abra `Interface1_transmissora.html` e `Interface2_receptora.html` no Google Chrome, no Edge ou no Opera. As páginas usam a Web Serial API, que esses navegadores aceitam.
3. Em cada página, clique em "Conectar Arduino" e escolha a porta da placa certa. A comunicação usa 9600 baud.
4. Digite a mensagem na Interface 1 e envie. A Interface 2 mostra o resultado.

Se a recepção falhar, ajuste o valor de `THRESHOLD` em `Maquina 2.ino` olhando as leituras no Monitor Serial, porque ele depende da luz do ambiente.

## Como foi feito

Desenvolvi o projeto sozinho, do zero, com auxílio de IA: os dois programas do Arduino, as duas interfaces web e a montagem. O Morse usa só letras de A a Z e números de 0 a 9.
