#include <Servo.h>
Servo motor;
int dos = 12;//dos es entrada echo
int tres = 8;//tres es salida trigger
int led = 13;//salida led
int buzzer = 10;
unsigned int duracion;
unsigned int distancia;

void setup (){
motor.attach(9);
pinMode(buzzer, OUTPUT);
pinMode(dos, INPUT);
pinMode(tres, OUTPUT);
pinMode(led, OUTPUT);
digitalWrite(led, HIGH);
delay(1000);
digitalWrite(led, LOW);
delay(1000);
noTone(buzzer);
motor.write(0);

}
void loop (){

	digitalWrite(tres, LOW);
	delay(500);
	digitalWrite(tres, HIGH);
	delay(500);
	digitalWrite(tres, LOW);
 

	duracion = pulseIn(dos, HIGH);
	distancia = duracion / 58;

	if (distancia <= 15){
		digitalWrite(led, HIGH);
		delay(50);
    tone(buzzer, 528);
    delay(4000);
    motor.write(90);
    delay(3000);
    noTone(buzzer);
	}
	else{ 
		    digitalWrite(led,LOW);
		    delay(1000);
        noTone(buzzer);
        motor.write(0);
	}

}
