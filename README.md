A Gas Leakage Detection System using Arduino is a great project for home safety. It typically involves an MQ-2 or MQ-5 gas sensor to detect gas leaks (like LPG, methane, or propane) and triggers an alert via a buzzer, LED, and optionally an LCD display or GSM module for SMS alerts.

Components Required:
Arduino Uno (or any compatible board)
MQ-2 or MQ-5 Gas Sensor (Detects LPG, methane, propane, etc.)
Buzzer (For alarm)
LED (Indicates leakage)
16x2 LCD Display (Optional) (To show gas levels)
GSM Module (Optional) (For SMS alerts)
Relay Module (To turn off gas supply or activate an exhaust fan)
Power Supply (9V battery or adapter)
Jumper Wires & Breadboard
Circuit Connections:
MQ-2 Gas Sensor
VCC → 5V (Arduino)
GND → GND (Arduino)
AO (Analog Output) → A0 (Arduino)
Buzzer
Positive → D7 (Arduino)
Negative → GND
LED
Positive (Anode) → D6 (Arduino)
Negative (Cathode) → GND
Relay (Optional for fan/valve control)
Input → D8 (Arduino)
Common & Normally Open (NO) → Fan or Gas Valve
Arduino Code
Here’s a simple Arduino sketch for gas leakage detection:


#define gasSensor A0  // MQ-2 sensor connected to A0
#define buzzer 7      // Buzzer connected to pin 7
#define led 6         // LED connected to pin 6
int gasThreshold = 300; // Set gas threshold (adjust as needed)

void setup() {
    pinMode(gasSensor, INPUT);
    pinMode(buzzer, OUTPUT);
    pinMode(led, OUTPUT);
    Serial.begin(9600);
}

void loop() {
    int gasLevel = analogRead(gasSensor);
    Serial.print("Gas Level: ");
    Serial.println(gasLevel);
    
    if (gasLevel > gasThreshold) { 
        digitalWrite(buzzer, HIGH);
        digitalWrite(led, HIGH);
        Serial.println("Gas Leak Detected!");
        delay(2000);
    } else {
        digitalWrite(buzzer, LOW);
        digitalWrite(led, LOW);
    }
    
    delay(1000);
}
How It Works:
The MQ-2 sensor detects gas concentration and sends an analog signal to Arduino.
If gas concentration exceeds the threshold, the buzzer sounds, and the LED lights up.
(Optional) A relay can trigger an exhaust fan or shut off a gas valve.
(Optional) A GSM module can send an SMS alert in case of leakage.
Possible Enhancements:
Use WiFi (ESP8266/ESP32) to send alerts via the internet.
Display real-time gas levels on an LCD screen.
Integrate an IoT dashboard for remote monitoring.
