---
layout: default
title: Controlar un led con el DashBoard Blynk IoT
description: Haciendo uso de la plataforma IoT.
---

Se logró manipular la intensidad del led con un slider de esta plataforma. 

## Diagrama pictórico
![](/arduino_projects/led/led_imagen.png)

## Foto de la implementación
![](/arduino_projects/led/implementacion_led.png)

## Código
> En las primeras líneas se colocan sus credenciales para acceder a la plataforma IoT, asimismo, el nombre de la red local y su contraseña, para que el ESP32 pueda conectarse a internet.
>

```c++
#define IO_USERNAME ""
#define IO_KEY ""
#define WIFI_SSID ""
#define WIFI_PASS ""
#include "AdafruitIO_WiFi.h"

AdafruitIO_WiFi io(IO_USERNAME, IO_KEY, WIFI_SSID, WIFI_PASS);
#define LED_PIN 16

AdafruitIO_Feed *slider = io.feed("Pregunta1_Tarea4");

void setup() {
 Serial.begin(115200);
 while(! Serial);
 Serial.print("Conectandose a Adafruit IO");
 io.connect();
 slider->onMessage(Mensaje_WEB);
 while(io.status() < AIO_CONNECTED) {
 Serial.print(".");
 delay(500);
 }

 Serial.println();
 Serial.println(io.statusText());
}

void loop() {
 io.run();
}
void Mensaje_WEB(AdafruitIO_Data *data) {
 int reading = data->toInt();
 Serial.print("Recibido <- ");
 Serial.println(reading);
 analogWrite(LED_PIN, reading);
}
```