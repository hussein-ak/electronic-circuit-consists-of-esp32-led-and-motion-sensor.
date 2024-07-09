# electronic-circuit-consists-of-esp32-led-and-motion-sensor.

## The link to my WOWki project
https://wokwi.com/projects/402930737081558017

## Simple explaination of the project
I developed an electronic system utilizing an ESP32 microcontroller, integrated with an LED and a motion sensor. The system is designed to function as follows:

1. Motion Detection: When the sensor detects movement in its vicinity, it triggers the system.
2. Automatic Illumination: Upon detecting motion, the LED automatically turns on, providing illumination.
3. Energy Efficiency: In the absence of motion, the LED remains off to conserve energy.
4. Real-time Response: The system continuously monitors for motion, ensuring immediate response to environmental changes.

This setup creates an intelligent, energy-efficient lighting solution that responds dynamically to human presence, ideal for applications such as smart home lighting or security systems.

## The C++ code
#include <Arduino.h>

const int motionSensorPin = 14; // GPIO pin for the motion sensor
const int ledPin = 19;          // GPIO pin for the LED

void setup() {
  // Initialize serial communication
  Serial.begin(115200);

  // Initialize the motion sensor pin as an input
  pinMode(motionSensorPin, INPUT);

  // Initialize the LED pin as an output
  pinMode(ledPin, OUTPUT);

  // Ensure the LED is off initially
  digitalWrite(ledPin, LOW);
}

void loop() {
  // Read the value from the motion sensor
  int motionState = digitalRead(motionSensorPin);

  // If motion is detected, turn on the LED
  if (motionState == HIGH) {
    Serial.println("Motion detected!");
    digitalWrite(ledPin, HIGH);
  } 
  // If no motion is detected, turn off the LED
  else {
    Serial.println("No motion detected.");
    digitalWrite(ledPin, LOW);
  }

  // Add a small delay to avoid bouncing effects
  delay(1000);
}
