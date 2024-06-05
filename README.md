myservo.write(90);

Serial.begin(9600);

}

// Ejecución contínua

void loop() {

delay(50);

distance = medirDistancia();

Serial.println(distance);

if(distance < 15){

stopCar();

// Miramos a la derecha

myservo.write(10);

delay(600);

servoReadRight = medirDistancia();

// Miramos a la izquierda

myservo.write(170);

delay(600);

servoReadLeft = medirDistancia();

// Miramos de frente

myservo.write(90);

delay(600);

if(servoReadLeft > servoReadRight){

Serial.println("Giro izquierda");

turnLeftCar();

}

if(servoReadRight >= servoReadLeft){

Serial.println("Giro derecha");

turnRightCar();

}

}

if(distance > 15){

Serial.println("Recto");

moveForwardCar();

}

}

void stopCar(){
