---
layout: project
title: "Project 36: Ultrasonic Ranger"
project_number: 36
difficulty: intermediate
components: ["Ultrasonic Sensor", "Arduino UNO", "Jumper Wires"]
---

# Project 36: Ultrasonic Ranger

## **Description**
The ultrasonic sensor uses sonar to determine distance to an object. It offers excellent non-contact range detection with high accuracy and stable readings.

## **Specifications**
- **Detection Distance:** 2-40cm
- **IO Interface:** 4 wire interface (-/+/S/EN)  
- **Output Signal:** TTL voltage
- **Effective Angle:** 35°
- **Size:** 41.7×16.7mm
- **Weight:** 5g

## **Required Components**
- UNO Board × 1
- Ultrasonic Sensor × 1  
- USB Cable × 1
- Jumper Wires × 4

## **Connection Diagram**

![Ultrasonic Sensor Connection]({{ '/assets/images/ultrasonic-connection.png' | relative_url }})

| Sensor Pin | Arduino Pin |
|------------|-------------|
| VCC | 5V |
| GND | GND |
| Trig | Digital Pin 7 |
| Echo | Digital Pin 8 |

## **Sample Code**

```c
// Ultrasonic Sensor Distance Measurement V4
const int trigPin = 7;
const int echoPin = 8;

void setup() {
Serial.begin(9600);
pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);
}

void loop() {
long duration, distance;

// Clear the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Trigger the sensor
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Read the echoPin
duration = pulseIn(echoPin, HIGH);

// Calculate distance
distance = duration * 0.034 / 2;

Serial.print("Distance: ");
Serial.print(distance);
Serial.println(" cm");

delay(500);
}
```

## **How It Works**
1. The sensor sends out an ultrasonic pulse
2. The pulse reflects off objects and returns
3. The sensor measures the time between sending and receiving
4. Distance is calculated using: `Distance = (Time × Speed of Sound) / 2`

## **Applications**
- Robot obstacle avoidance
- Automatic parking systems  
- Liquid level measurement
- Security systems

## **Troubleshooting**
- **No readings:** Check wiring connections
- **Inconsistent readings:** Ensure sensor is mounted securely
- **Out of range:** Target may be too close (<2cm) or too far (>40cm)
