# Team-Spark-Squad
//Define pin connections
const int motorPin = 9;     // PWM output to control motor speed
const int buzzerPin = 8;    // Digital output for buzzer
const int irSensorPin = 3;  // Input pin for IR sensor

void setup() 
{
  // Initialize serial communication for debugging
  Serial.begin(9600);

  // Set pin modes
  pinMode(motorPin, OUTPUT);  
  pinMode(buzzerPin, OUTPUT);
  pinMode(irSensorPin, INPUT);
}

void loop() 
{
  int irSensorState = digitalRead(irSensorPin);

  // Print states for debugging
  Serial.print(" | IR Sensor: ");
  Serial.println(irSensorState);

 if(irSensorState == HIGH) 
 {
    digitalWrite(motorPin, HIGH); // Full speed
    digitalWrite(buzzerPin, HIGH);
    Serial.println("Motor ON | Buzzer ON");
    delay(100);
  } 
  else 
  {
    digitalWrite(motorPin, LOW);   // Stop motor
    digitalWrite(buzzerPin, LOW);
    Serial.println("Motor OFF | Buzzer OFF");
    delay(100);
  }

  delay(100); // Small delay for stability
}
