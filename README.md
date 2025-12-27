# WaterMeterESPHome
Water Meter with Inductive Proximity Sensor in ESPHome

What you need:
- ESP8266 or ESP32
- Household water meter with inductive (non‑magnetic) sensing
e.g., Diehl Corona MCI 
<img width="763" height="635" alt="image" src="https://github.com/user-attachments/assets/8d89fd51-2dba-448c-8de7-794619da77b4" />


- Inductive proximity sensor LJ18A3‑8‑Z/BX NPN 5V
- Home Assistant with ESP add‑on
  
How it works:
- Use the wasserzaehler.yaml file to flash the ESP.
- Connect the inductive proximity sensor to the ESP.
Example: ESP8266 wiring
- Connect ESP8266 5V to the brown wire of the inductive proximity sensor
- Connect ESP8266 GND to the blue wire of the sensor
- Connect ESP8266 D5 to the black wire of the sensor
- Since the ESP8266 input pins only support 3.3V, the sensor’s output (black → D5) should be level‑shifted from 5V to 3.3V using either a level shifter or a resistor divider.
  <img width="945" height="301" alt="image" src="https://github.com/user-attachments/assets/62eb51a7-0d5a-498f-b97a-c347e158ce67" />

- Attach the inductive proximity sensor to the water meter using thin double‑sided tape or a suitable 3D‑printed mount.
  
Functionality:
- Measures pulses from the water meter. You may need to adjust the amount of water per pulse in the code.
Default setting: 1 liter per pulse.
- Water flow is calculated. If no new pulse is detected for 180 seconds, the flow rate is reset to 0 L/min. This is important for the alarm logic.
- An alarm is triggered when water flow is detected for longer than the configured time. Home Assistant can then send a notification.
- Using the pulse counters, consumption sensors can be created in Home Assistant.

