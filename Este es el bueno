// Definir las variables 
const int echo = 2;
const int trig = 3;
volatile unsigned int distancia;
const int cerca = 15;
const unsigned long duracionMaxPulso = 5000;

// Para controlar los motores
const int NA = 11;
const int IZ1 = 9;
const int IZ2 = 8;
const int ER1 = 6;
const int ER2 = 7;
const int NB = 10;

void setup() {
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);
  pinMode(NA, OUTPUT);
  pinMode(IZ1, OUTPUT);
  pinMode(IZ2, OUTPUT);
  pinMode(ER1, OUTPUT);
  pinMode(ER2, OUTPUT);
  pinMode(NB, OUTPUT);
}
// El bucle de que fija el sensor de 
void loop() {
  medir();
  if (distancia < cerca) {
    obstaculo();
  } else {
    adelante();
  }
}

void medir() {
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);
  distancia = pulseIn(echo, HIGH, duracionMaxPulso) / 29.1 / 2;
  if (distancia == 0) {
    distancia = duracionMaxPulso / 29.1 / 2;  // Corrige el cálculo de la distancia cuando no hay retorno
  }
}

void adelante() {
  digitalWrite(IZ1, HIGH);
  digitalWrite(IZ2, LOW);
  digitalWrite(ER1, HIGH);
  digitalWrite(ER2, LOW);
  analogWrite(ENA, 90);
  analogWrite(ENB, 90);
}

void derecha() {
  digitalWrite(IZ1, HIGH);
  digitalWrite(IZ2, LOW);
  digitalWrite(ER1, LOW);
  digitalWrite(ER2, HIGH);
  analogWrite(NA, 150);
  analogWrite(NB, 200);
}

void detenido() {
  digitalWrite(IZ1, LOW);
  digitalWrite(IZ2, LOW);
  digitalWrite(ER1, LOW);
  digitalWrite(ER2, LOW);
  analogWrite(NA, 0);
  analogWrite(NB, 0);
}
// La accion al detectar un objeto u obstaculo
void obstaculo() {
  detenido();
  delay(300);
  derecha();
  delay(230);  
  detenido();
  delay(100);   
}
