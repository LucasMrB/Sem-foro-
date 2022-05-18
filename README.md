# Semáforo

Semáforo feito através do App Tinkercad.

O TinkerCad é um App web que faz simulações de um Arduino, sua programação é toda em C++, porém você pode usar a "programação em blocos" para melhorar seu raciocínio lógico. 
No meu projeto, deicidi fazer dois semáforos em uma encruzilhada, os semáforos são tanto para pedestres, quanto para pessoas (existem semáforos distintos). 
Enquanto um semáforo estiver vermelho, o outro estara verde e vice-versa. 

1 - Pra que serve um semáforo? 
 O semáfaro é um instrumento utilizado para controlar o tráfego de veículos e de 
pedestres ou peões nas cidades, assim mantendo uma organização nas ruas.

2 - Realização do projeto
2.2 - Hardware
2.2.1 - O primeiro passo foi saber como o semáforo funciona (ordem das cores).
 O semáforo é composto por três cores (verde, amarelo e vermelho). 
 A cor verde significa que carro pode avançar.
 A cor amarela signica que o sinal está prestes a fechar (ficar vermelho).
 A cor vermelha significa que o motorista deve esperar o sinal ficar verde.
Ordem das cores: verde, amarelo, vermelho (o sinal segue a ordem de esquerda para 
direita, quando chega ao final da ordem (vermelho), ele vai direto para o verde).

2.2.3 - Explicando o hardware
Comecei pegando um Arduino e uma placa de ensaio pequena, depois peguei três
resistores (um para os LEDs e outro para os botões), precisei usar três pois a resistência 
dos LEDs e dos botões são diferentes. Fiz a linha horizontal inferior (de baixo) ficar toda 
com uma resistência de 150 ohms (unidade de medida) (essa decisão foi tomada pois 
existem muitos LEDs e todos precisam da resistência), os outros dois, eu usei na carga 
positiva de 5 watts.
Depois pensei em como organizar melhor os fios do sistema, então decidi usar o preto 
para o GRD, o vermelho para sinal positivo e para o LED vermelho, o amarelo para o LED 
amarelo, o verde para o LED verde e por fim o laranja para os botões.
Agora, decidi organizar todos os LEDs e os botões, fiz as ligações de cada fio (você pode 
ver com detalhe na imagem acima). Os LEDs que estão centralizados (os três do meio, 
vermelho, amarelo e verde) simbolizam um semáforo de carros, os das laterais (os quatro, 
onde tem dois de cada lado, vermelho e verde) simbolizam um sinal para pedestres. 
A posição dos LEDs, indicam a direção para qual a via segue, se a parte da frente do 
semáforo está para esquerda, a direção será para esquerda. 
Fiz as ligações dos botões, coloquei o resistor na carga positiva (essa foi a minha 
dificuldade, aprendi a fazer assistindo um vídeo no youtube), vi como funcionava um 
botão, que sua carga é de 5 watts, quando apertado sua carga vai para 0 watts, assim 
podendo realizar alguma ação (no meu exemplo foi assim). 
O primeiro botão é o botão que deve ser usado para quando o primeiro sinal estiver 
verde, o segundo botão deve ser usado para quando o segundo sinal estiver verde.

2.3 - Software
2.3.1 - Semáforo 

Programa em C++:
// C++ code
//
int contador = 0;
void setup()
{
 pinMode(13, OUTPUT);
 pinMode(12, OUTPUT);
 pinMode(11, OUTPUT);
 pinMode(1, OUTPUT);
 pinMode(2, OUTPUT);
 pinMode(3, OUTPUT);
 pinMode(8, INPUT);
 pinMode(9, INPUT);
}
void loop()
{
 contador = (contador + 1);
 if (contador < 500) {
 digitalWrite(13, HIGH);
 digitalWrite(12, LOW);
 digitalWrite(11, LOW);
 digitalWrite(1, HIGH);
 digitalWrite(2, LOW);
 digitalWrite(3, LOW);
 if (digitalRead(8) == 0) {
 contador = 500;
 }
 }
 if (contador >= 500 && contador < 800) {
 digitalWrite(13, HIGH);
 digitalWrite(12, LOW);
 digitalWrite(11, LOW);
 digitalWrite(1, LOW);
 digitalWrite(2, HIGH);
 digitalWrite(3, LOW);
 }
 if (contador >= 800 && contador < 1300) {
 digitalWrite(13, LOW);
 digitalWrite(12, LOW);
 digitalWrite(11, HIGH);
 digitalWrite(1, LOW);
 digitalWrite(2, LOW);
 digitalWrite(3, HIGH);
 if (digitalRead(9) == 0) {
 contador = 1300;
 }
 }
 if (contador >= 1300 && contador < 1600) {
 digitalWrite(13, LOW);
 digitalWrite(12, HIGH);
 digitalWrite(11, LOW);
 digitalWrite(1, LOW);
 digitalWrite(2, LOW);
 digitalWrite(3, HIGH);
 }
 if (contador >= 1600 && contador < 2100) {
 digitalWrite(13, HIGH);
 digitalWrite(12, LOW);
 digitalWrite(11, LOW);
 digitalWrite(1, HIGH);
 digitalWrite(2, LOW);
 digitalWrite(3, LOW);
 }
 if (contador >= 2100) {
 contador = 0;
 }
 delay(10); // Delay a little bit to improve simulation performance
}


Código em C++.

Link do projeto:
https://www.tinkercad.com/things/dEHeUfsTlxb
