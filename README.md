# Smart-Thermostat-with-Arduino-and-Temperature-Sensor
Regulating temperature in a smart home using Arduino and a temperature sensor.
#include <DHT.h>

#define DHTPIN 2
#define DHTTYPE DHT11

DHT dht(DHTPIN, DHTTYPE);

void setup() {
    Serial.begin(9600);
    dht.begin();
}

void loop() {
    delay(2000);
    float temperature = dht.readTemperature();
    Serial.print("Temperature: ");
    Serial.println(temperature);

    if (temperature > 25.0) {
        // Turn on air conditioning or cooling system
        Serial.println("Turning on air conditioning");
    } else if (temperature < 20.0) {
        // Turn on heating system
        Serial.println("Turning on heating");
    }
}
