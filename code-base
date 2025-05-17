#include <Servo.h>

const int pinX = A0;
const int pinY = A1;
const int servoPin = 9;

Servo meuServo;

int posicaoAtual = 80;  // posição inicial do servo
int posicaoAlvo = 80;

void setup() {
  Serial.begin(9600);
  meuServo.attach(servoPin);
  meuServo.write(posicaoAtual);
}

void loop() {
  int x = analogRead(pinX) - 512;
  int y = analogRead(pinY) - 512;

  float angle = atan2((float)y, (float)x) * 180.0 / PI;
  if (angle < 0) angle = 180 + angle;

  // Define a direção desejada
  if (abs(x) > 100 || abs(y) > 100) {
    if (angle < 22.5) {
      posicaoAlvo = 160; // Direita
    } else if (angle < 67.5) {
      posicaoAlvo = 120; // Meio-direita
    } else if (angle < 112.5) {
      posicaoAlvo = 80;  // Frente
    } else if (angle < 157.5) {
      posicaoAlvo = 40;  // Meio-esquerda
    } else {
      posicaoAlvo = 0;   // Esquerda
    }
  }

  // Movimento suave, contínuo e gradual
  if (posicaoAtual < posicaoAlvo) {
    posicaoAtual++;
    meuServo.write(posicaoAtual);
  } else if (posicaoAtual > posicaoAlvo) {
    posicaoAtual--;
    meuServo.write(posicaoAtual);
  }

  delay(10); // velocidade do movimento (ajuste conforme necessário)
}
