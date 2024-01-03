# IOT-BASED-SMART-IRRIGATION-SYSTEM-
Revolutionize agriculture with our IoT-based Smart Irrigation System. Using real-time data, it optimizes water usage, ensuring efficient and sustainable crop growth. Embrace precision farming for maximum yield and environmental conservation.


#include <Wire.h>
#include <Servo.h>

const int moisturePin = A0;  // Moisture sensor analog pin
const int relayPin = 7;      // Relay control pin
Servo servoMotor;            // Servo motor object

void setup() {
  Serial.begin(9600);
  pinMode(relayPin, OUTPUT);
  servoMotor.attach(9);  // Attach servo to pin 9
}

void loop() {
  int moistureValue = analogRead(moisturePin);
  Serial.print("Moisture Level: ");
  Serial.println(moistureValue);

  if (moistureValue < thresholdValue) {
    activateIrrigation();
  } else {
    deactivateIrrigation();
  }
}

void activateIrrigation() {
  digitalWrite(relayPin, HIGH);  // Turn on irrigation system
  servoMotor.write(90);           // Adjust servo position as needed
  delay(1000);                    // Run irrigation for a set time
  servoMotor.write(0);            // Reset servo position
}

void deactivateIrrigation() {
  digitalWrite(relayPin, LOW);  // Turn off irrigation system
  // Additional logic if needed
}
