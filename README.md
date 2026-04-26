# Temperature-and-Humidity-Monitoring-System
This project measures temperature and humidity using a DHT sensor and displays the values on the Serial Monitor. It is useful for weather monitoring, smart homes, and IoT-based environmental systems.

Components Required :
Arduino Uno
DHT11 or DHT22 Sensor
Jumper wires
Breadboard (optional)

Connections :
VCC → 5V
GND → GND
DATA → Pin 2

Code :
C++
#include "DHT.h"

#define DHTPIN 2
#define DHTTYPE DHT11   // Change to DHT22 if using that

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  float humidity = dht.readHumidity();
  float temperature = dht.readTemperature();

  if (isnan(humidity) || isnan(temperature)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }

  Serial.print("Temperature: ");
  Serial.print(temperature);
  Serial.print(" °C  ");

  Serial.print("Humidity: ");
  Serial.print(humidity);
  Serial.println(" %");

  delay(2000);
}

Working :
The DHT sensor reads temperature and humidity
Arduino processes the data
Values are displayed on the Serial Monitor every 2 seconds
Output
Example:

Temperature: 28 °C  Humidity: 65 %
Applications
Weather monitoring systems
Smart homes
Agriculture monitoring
⚠️ Important
Install DHT library in Arduino IDE
Select correct sensor type (DHT11 or DHT22)
