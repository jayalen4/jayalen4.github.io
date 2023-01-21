---
layout: default
title: Amperímetro y Voltímetro
description: Midiendo estos parámetros con un ESP32
---

Para el caso de este ejercicio se está realizando la medición de voltaje y corriente de una batería 
de 3.7V y 2000mAh de capacidad. Para poder realizar la medición se realiza un divisor de voltaje:

Vout= Vin x (R2/(R1+R2))

Y para la medición de la corriente se está usando una resistencia de 15 Ω, debido a que no se tiene 
una resistencia shunt, en la fórmula, R3 = 15 Ω,
V3 = V2-V1,
current = V3/R3.

## Diagrama pictórico

![](/arduino_projects/voltimetro/foto_fritzing.png)

## Foto de la implementación 

En la implementación, adicionalmente se usaron los módulos RTC y de lector de tarjeta microSD, para tener el tiempo exacto y guardar la medición de los datos en un archivo .csv.

![](/arduino_projects/voltimetro/Foto1.png)

## Código

> En las primeras líneas se colocan sus credenciales para acceder a la plataforma IoT, asimismo, el nombre de la red local y su contraseña, para que el ESP32 pueda conectarse a internet.
>

```c++
#define BLYNK_TEMPLATE_ID ""
#define BLYNK_DEVICE_NAME "Multímetro"
#define BLYNK_AUTH_TOKEN ""

#define BLYNK_FIRMWARE_VERSION "0.1.0"
#define BLYNK_PRINT Serial
#define APP_DEBUG

#define Pin_Voltaje V4
#define Pin_Corriente V5

//Your WiFi Credentials
char auth[] = "";
char ssid[] = "";
char pass[] = "";

//------------------------------

#define BLYNK_PRINT Serial
#include <WiFi.h>
#include <WiFiClient.h>
#include <BlynkSimpleEsp32.h>
#include <Adafruit_GFX.h>

#include "RTClib.h"
#include <Wire.h>

#include "SD.h"
#include "SPI.h"

//Puertos
const int puertoVoltaje = 34;
const int puertoVoltaje_2 = 32;

//Variables
int Voltaje_leido = 0;
int Voltaje_leido_2 = 0;
float vout = 0.0;
float vout_2 = 0.0;
float vin_1 = 0.0;
float vin_2 = 0.0;
float current = 0.0;
const int CSpin = 2;
File sensorData;

float R1 = 100000;  //Resistencia 1
float R2 = 15;      //Resistencia 2
float R3 = 10000;   //Resistencia 3

char daysOfTheWeek[7][12] = {"Domingo", "Lunes", "Martes", "Miercoles", "Jueves", "Viernes", "Sabado"};

String $vin_1 = "0";
String $vin_2 = "0";
String data ="";

RTC_DS3231 rtc;

void setup() {
  // put your setup code here, to run once:
  Blynk.begin(auth, ssid, pass);
  Serial.begin(115200);
  delay(1000);
  pinMode(puertoVoltaje,INPUT_PULLUP);
  pinMode(puertoVoltaje_2,INPUT_PULLUP);
  if(!rtc.begin()){
    Serial.println("No se pudo encontrar RTC");
    while(1);    
  }
  rtc.adjust(DateTime(__DATE__, __TIME__));

  Serial.println("Initializing SD card...");
   if (!SD.begin(CSpin)) {
    Serial.println("Card failed, or not present");
    return;
   }
   Serial.println("card initialized."); 

}

void guardaDatoCSV(float voltaje, float corriente, DateTime now){
  data = String(voltaje) + ";" + String(corriente)+";"+String(now.hour())+":"+String(now.minute());
  sensorData = SD.open("/data.csv", FILE_APPEND);
  if (sensorData){
  sensorData.println(data);
  sensorData.close(); // close the file
  Serial.println("DATO GUARDADO EXITOSAMENTE");
}
else{
  Serial.println("Problema");
}
}

void loop() {
  
  // put your main code here, to run repeatedly:
  DateTime now = rtc.now();
  Voltaje_leido = analogRead(puertoVoltaje);
  vout = (Voltaje_leido * 5)/4095.0;
  vin_1 = vout/((R2+R3)/(R1+R2+R3));
  $vin_1 = String(vin_1);
  Serial.print("Voltaje V1 = ");
  Serial.println(vin_1,3);

  Voltaje_leido_2 = analogRead(puertoVoltaje_2);  
  vout_2 = (Voltaje_leido_2 * 5)/4095.0;
  vin_2 = vout_2/(R3/(R1+R2+R3));
  //$vin_2 = String(vin_2);
  
  current = (vin_1-vin_2)/R2;

  //Serial.print("Voltaje V2 = ");
  //Serial.println(vin_2,3);

  Serial.print("Corriente = ");
  Serial.println(current,3);
  Blynk.virtualWrite(V4, vin_1);
  Blynk.virtualWrite(V5, current);
  Blynk.run();
  guardaDatoCSV(vin_1,current,now); 
  delay(3000);

  
  Serial.print("Hora: ");
  Serial.print(now.hour());  
  Serial.print(":");
  Serial.print(now.minute());  
  Serial.print(" - ");
  Serial.print(daysOfTheWeek[now.dayOfTheWeek()]);  
  Serial.print(" "); 
  Serial.print(now.day());
  Serial.print("/"); 
  Serial.print(now.month());
  Serial.print("/"); 
  Serial.println(now.year());
}

```