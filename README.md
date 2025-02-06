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
