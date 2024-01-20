# PRACTICA-NIVEL-DE-AGUA
Este repositorio muestra como podemos programar una ESP32 con el sensor HC-SR04 ULTRASONICO

## Introducción
### Descripción
La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```HC-SR04```) para adquirir el nivel del agua; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).

## Material Necesario
Para realizar esta practica necesitas lo siguiente
- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor HC-SR04
- Luces LED
- Resistor

## Instrucciones
### Requisitos previos
Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).

### Instrucciones de preparación de entorno 
1. Abrir la terminal de programación y colocar la siguente programación:

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=2 && safetyDistance<=5)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=5 && safetyDistance<=10) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else
{
 digitalWrite(led1,  LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}
```
2. Es importante mencionar que para esta practica en particular no se necesita instalar ninguna libreria.
3. Hacer la conexion de **HC-SR04** con la **ESP32** como se muestra en la siguente imagen.
![]()
4. Hacer la conexion del **LED** y el **Resisyor** con la **ESP32** como se muestra en la siguente imagen.
![]()
### Instrucciónes de operación
1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.

## Resultados
Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.
![]()

# Créditos
Desarrollado por Ing. Montañez Mejia Cristian
