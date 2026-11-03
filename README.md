IoT Patient Health Monitoring and Emergency Alert System

Using LPC2129 ARM7 Microcontroller and ESP-01 Wi-Fi Module


Overview

The IoT Patient Health Monitoring and Emergency Alert System
continuously monitors a patient's body temperature, heart rate, and
blood oxygen saturation (SpO₂). The LPC2129 ARM7 microcontroller
collects sensor readings, checks them against predefined threshold
values, and controls local and remote alerts.


The ESP-01 Wi-Fi module connects the system to the Internet and uploads
patient information to an IoT cloud platform. Doctors and caregivers can
view the patient's condition remotely through a computer or smartphone.



Note: This project is an educational embedded-systems prototype.
It is not a certified medical device and must not be used as the sole
basis for medical diagnosis or emergency decisions.



Features


Continuous monitoring of body temperature, heart rate, and SpO₂.

Displays patient readings and system status on a 16×2 LCD.

Uses a green LED to indicate normal status.

Uses a red LED and buzzer to indicate an abnormal condition.

Sends patient readings and emergency information to an IoT cloud platform through Wi-Fi.

Supports remote monitoring using a cloud dashboard.

Automatically checks readings against thresholds configured in the program.


Hardware Components


  Component                           Purpose



  LPC2129 ARM7 Development Board      Reads sensors, processes values,
                                      and controls the system


  LM35 Temperature Sensor             Measures temperature


  Pulse Sensor                        Measures heart rate


  MAX30102 Sensor                     Measures blood oxygen saturation
                                      (SpO₂) and pulse rate


  ESP-01 Wi-Fi Module                 Provides Wi-Fi and cloud
                                      connectivity


  16×2 LCD                            Displays readings and warning
                                      messages


  Green LED                           Indicates normal condition


  Red LED                             Indicates warning/emergency
                                      condition


  Buzzer                              Provides an audible alert


  Push Button (optional)              Optional emergency input


  Regulated power supply              Supplies power to the circuit


  Breadboard and jumper wires         Circuit assembly and connections

Software and Tools


Embedded C

Keil µVision IDE

Flash Magic

ESP8266 AT firmware

ThingSpeak or Blynk IoT platform

Serial terminal for debugging


Communication Interfaces


GPIO: Controls LEDs, buzzer, and other digital input/output devices.

ADC: Converts analog signals from the LM35 and Pulse Sensor into digital readings.

UART: Provides serial communication between the LPC2129 and ESP-01 module. The controller sends AT commands to the ESP-01.

I²C: Used by the LPC2129 to communicate with the MAX30102 sensor.

Wi-Fi / Internet: Transfers patient information to the IoT cloud platform.


Working Principle


System initialization: The LPC2129 initializes GPIO, LCD, ADC, UART, and I²C. The sensors and ESP-01 are initialized.

Wi-Fi connection: The LPC2129 sends AT commands to the ESP-01 over UART. The ESP-01 connects to the configured Wi-Fi router.

Sensor data acquisition: The LM35 and Pulse Sensor provide analog signals that are read through the ADC. The MAX30102 sends data over I²C.

Data processing: The LPC2129 evaluates the readings and compares them with threshold values defined in the program.

Normal condition: The LCD displays patient readings, the green LED remains ON, and the ESP-01 uploads the data to the cloud.

Abnormal condition: The system displays a warning on the LCD, activates the red LED and buzzer, and sends emergency information to the cloud.

Continuous monitoring: The system repeats the monitoring and upload process while it is operating.


System Block Diagram

The project follows this data flow:


 LM35 Temperature Sensor ──┐
 Pulse Sensor ─────────────┼──> LPC2129 ARM7 ──> LCD Display
 MAX30102 Sensor (I²C) ────┘         │          ├──> Green / Red LEDs
                                    │          └──> Buzzer
                                    │
                                  UART
                                    │
                              ESP-01 Wi-Fi
                                    │
                              Wi-Fi Router
                                    │
                               Internet
                                    │
                             IoT Cloud Platform
                                    │
                         Doctor / Caregiver Dashboard

Normal and Emergency Indications

Normal condition


Green LED: ON

Red LED: OFF

Buzzer: OFF

LCD: Displays temperature, heart rate, and SpO₂

ESP-01: Uploads patient readings to the cloud


Abnormal condition

When a monitored value crosses its configured threshold:



Red LED: ON or blinking, according to the programmed behavior

Buzzer: ON

LCD: Displays the relevant warning

ESP-01: Uploads emergency information to the cloud


Example LCD readings shown in the project document:


TEMP : 36.8°C
HR   : 76 BPM
SpO2 : 98%

Example warning messages include HIGH TEMP ALERT,
HEART RATE ABNORMAL, and LOW SpO2 ALERT.


Applications


Demonstration of patient monitoring in hospitals and clinics.

Elderly-care monitoring prototypes.

Home healthcare monitoring demonstrations.

Learning embedded systems, biomedical sensor interfacing, UART, I²C, ADC, and IoT cloud connectivity.


Concepts Demonstrated


LPC2129 ARM7 microcontroller programming

GPIO and ADC interfacing

UART communication and ESP8266 AT commands

I²C sensor communication

LCD interfacing

Biomedical sensor data acquisition

Wi-Fi and IoT cloud communication

Threshold-based embedded decision-making


Important Implementation Notes


Configure the Wi-Fi credentials and cloud-platform settings in the ESP-01 communication code.

Set and validate the temperature, heart-rate, and SpO₂ thresholds for the intended demonstration. The project document does not specify numeric threshold values.

Check the sensor wiring, voltage requirements, and LPC2129/ESP-01 logic-level compatibility before powering the circuit.

Test local alerts and cloud updates independently before running the complete system.

Sensor readings and threshold-based alerts from this prototype are not a substitute for clinically validated monitoring equipment or professional medical care.


Future Enhancements

Possible extensions include adding secure communication, patient
identification, data logging, improved fault detection, and a validated
mobile notification workflow.


Project Summary

This project combines biomedical sensors, the LPC2129 ARM7
microcontroller, the ESP-01 Wi-Fi module, local alert devices, and an
IoT cloud dashboard to demonstrate continuous patient health monitoring
and remote emergency notification.

