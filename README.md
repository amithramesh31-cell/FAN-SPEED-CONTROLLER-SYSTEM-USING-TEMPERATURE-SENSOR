
# FAN-SPEED-CONTROLLER-SYSTEM-USING-TEMPERATURE-SENSOR
# EXP 1(A) FAN SPEED CONTROLLER SYSTEM USING TEMPERATURE SENSOR

### Name: PRADEEP N
### Reg No: 212223060201

# Aim:
	To measure the Temperature using DHT11/DHT22/TMP36  sensor with Arduino UNO Board/ESP-32 using Tinker CAD.

# Hardware / Software Tools required:
	PC/ Laptop with Internet connection
    Tinker CAD tool (Online)
	Arduino UNO Board/ESP-32
	Temperature Sensor (DHT11/DHT22/TMP36)

# Circuit Diagram:
![WhatsApp Image 2025-10-28 at 18 05 16_12e3474c](https://github.com/user-attachments/assets/74febc99-28d9-4b55-b39e-8ac189549ee7)

---


# Procedure // Modify the procedure based on your circuit

Step 1: Set Up the Tinkercad Environment
1.	Log in to Tinkercad: Open Tinkercad in your web browser and log in to your account.
2.	Create a New Circuit: In the Tinkercad dashboard, click on "Circuits" and then select "Create New Circuit."
Step 2: Add Components to the Circuit
1.	Arduino Uno: Drag an Arduino Uno board from the components panel onto the workspace.
2.	TMP36 Sensor: Search for the TMP36 sensor in the components panel and drag it into the workspace.
3.	Breadboard: Drag a small breadboard to the workspace to help with wiring connections.
4.	Resistor (Optional): A resistor may not be necessary for this simple setup, but you can include it for more accurate readings.
5.	Wires: Use wires to connect the components.

Step 3: Connect the TMP36 Sensor to the Arduino
1.	TMP36 Pins:
o	Vout (Middle Pin): Connect this to an analog input pin on the Arduino (e.g., A0).
o	GND (Right Pin): Connect this pin to the ground (GND) on the Arduino.
o	Vs (Left Pin): Connect this to the 5V pin on the Arduino.
2.	Breadboard Wiring:
o	TMP36 Vout (Middle Pin) to Arduino A0: Use a wire to connect the middle pin (Vout) of the TMP36 sensor to the A0 analog input pin on the Arduino.
o	TMP36 GND (Right Pin) to Breadboard GND Rail: Connect the GND pin of the TMP36 sensor to the ground rail of the breadboard.
o	TMP36 Vs (Left Pin) to Breadboard 5V Rail: Connect the Vs pin of the TMP36 sensor to the 5V rail of the breadboard.
o	Arduino GND to Breadboard GND Rail: Connect a wire from the Arduino GND pin to the ground rail on the breadboard.
o	Arduino 5V to Breadboard 5V Rail: Connect a wire from the Arduino 5V pin to the power rail on the breadboard.
Step 4: Write the Arduino Code
1.	Code Editor: Click on the "Code" button at the top of the Tinkercad workspace to open the code editor.
2.	Set the Coding Mode: Ensure the editor is in "Text" mode to write your code in C/C++.
3.	Enter the Code: Write the following code to read the temperature from the TMP36 sensor
Step 5: Simulate the Circuit
1.	Start Simulation: Click the "Start Simulation" button at the top of the workspace to run the circuit and code.
2.	Monitor Output: Open the serial monitor by clicking the "Serial Monitor" button to view the temperature readings in both Celsius and Fahrenheit.
Step 6: Troubleshoot and Refine
1.	Check Connections: Ensure that all connections are made correctly on the breadboard and the Arduino.
2.	Adjust Code: If needed, tweak the code to improve accuracy or change the format of the output.
Step 7: Save Your Work
1.	Stop Simulation: Click "Stop Simulation" to end the simulation.
2.	Save the Circuit: Click "Save" to keep your circuit design and code for future use.


# Program
```
// Define analog input pins
const int tempSensorPin = A0;
const int humiditySensorPin = A1;

// Define variables
int tempRawValue = 0;
int humidityRawValue = 0;
double voltage = 0;
double tempC = 0;
double tempF = 0;

void setup() {
  Serial.begin(9600);     // Initialize serial communication
  pinMode(tempSensorPin, INPUT);
  pinMode(humiditySensorPin, INPUT);
}

void loop() {
  // Read temperature sensor value
  tempRawValue = analogRead(tempSensorPin);
  voltage = (tempRawValue / 1023.0) * 5000; // Convert to millivolts
  tempC = (voltage - 500) * 0.1;            // LM35-like formula
  tempF = (tempC * 1.8) + 32;               // Convert °C to °F

  // Print temperature data
  Serial.print("Raw Value = ");
  Serial.print(tempRawValue);
  Serial.print("\t MilliVolts = ");
  Serial.print(voltage, 0);
  Serial.print("\t Temperature (°C) = ");
  Serial.print(tempC, 1);
  Serial.print("\t Temperature (°F) = ");
  Serial.println(tempF, 1);

  // Read humidity sensor value
  humidityRawValue = analogRead(humiditySensorPin);

  // Map analog value (0–1023) to humidity percentage (10–70%)
  int humidityPercent = map(humidityRawValue, 0, 1023, 10, 70);

  // Print humidity data
  Serial.print("Humidity: ");
  Serial.print(humidityPercent);
  Serial.println("%");

  // Wait 5 seconds before next reading
  delay(5000);
}
```
# Output
![WhatsApp Image 2025-10-28 at 18 05 27_1ecef56c](https://github.com/user-attachments/assets/787db476-26fb-4ee9-833e-4158a9ef48ad)


# Result
The temperature and humidity values are measured using DHT11/DHT22/TMP36 sensor with Arduino UNO Board/ESP-32 and Simulated using Tinker CAD.
