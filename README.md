# IoT-Based GSM GPS Tracker with SMS Alert System

## Introduction
This project is an IoT-based GPS tracking and alert system, designed to provide real-time location and speed details of a vehicle or device. The system utilizes an ESP32 microcontroller, a SIM800 GSM module, and a Neo-6M GPS module to receive GPS data and communicate with a remote phone number via SMS. With simple SMS commands, users can request location, speed information, or control an alarm remotely.

## Problem Statement
In situations where tracking a vehicle or device's location in real-time is essential, conventional GPS trackers with internet-based applications can be costly and limited in network coverage. This project offers a low-cost, offline alternative by using GSM-based communication for tracking, making it useful in remote areas without internet connectivity.

## Approach and Impact
By using SMS commands, the GSM GPS tracker can send real-time location coordinates as Google Maps links and provide speed data. This approach provides an affordable and straightforward method for monitoring assets in regions with poor internet connectivity. The system also allows for controlling an onboard alarm, adding a layer of security.

## Circuit Diagram
The circuit consists of an ESP32, SIM800 GSM module, and Neo-6M GPS module. The connections are as follows:

| Component          | ESP32 Pin | Module Pin |
|--------------------|-----------|------------|
| GSM Module RX      | GPIO 4    | TX         |
| GSM Module TX      | GPIO 2    | RX         |
| GPS Module RXD2    | GPIO 16   | TXD        |
| GPS Module TXD2    | GPIO 17   | RXD        |
| LED (Alarm)        | GPIO 5    | -          |

### Circuit Diagram Explanation
- **GSM Module**: Connected to the ESP32 via UART communication on GPIO 4 (RX) and GPIO 2 (TX).
- **GPS Module**: Also connected to the ESP32 via UART communication, using GPIO 16 (RXD2) and GPIO 17 (TXD2).
- **LED Alarm**: Connected to GPIO 5 to act as a visual alert when specific commands are received.

## Features
1. **Send Location**: The system receives GPS coordinates from the Neo-6M GPS module and sends a Google Maps link to the user.
2. **Send Speed**: The system retrieves the current speed from the GPS module and sends it via SMS.
3. **Alarm Control**: The user can remotely turn the alarm (LED) on or off via SMS commands.

## Commands
- **get location**: Sends current GPS location as a Google Maps link.
- **get speed**: Sends the current speed in km/h.
- **alarm on**: Turns the alarm (LED) on.
- **alarm off**: Turns the alarm (LED) off.

## Code Explanation
### Dependencies
- `TinyGPS++`: A library for decoding GPS data.
- `HardwareSerial`: Used for serial communication with the GSM and GPS modules.

### Setup
1. Initialize serial communication for debugging.
2. Set up GSM and GPS modules to receive and parse SMS commands.
3. Configure the ESP32 to parse SMS commands and respond accordingly.

### Main Functions
- **parseData(String buff)**: Parses incoming SMS data, identifies the command, and triggers respective functions based on SMS content.
- **sendLocation()**: Retrieves GPS coordinates and sends them as a Google Maps link via SMS.
- **sendSpeed()**: Retrieves current speed from the GPS module and sends it via SMS.
- **extractSms(String buff)**: Extracts details like the sender's number, SMS content, and date from the received SMS data.

### Screenshots
<div align="center">
  <img src="https://github.com/user-attachments/assets/7a15076d-a6de-4c32-a05e-cdcaf78197ed" alt="Circuit Diagram" width="400" height="300">
  <img src="https://github.com/user-attachments/assets/0a7c91ba-babf-411b-b95b-888c676a08ec" alt="Screenshot" height="300">
</div>


---

This system is ideal for vehicle tracking, asset monitoring, and simple IoT applications that require remote communication without internet access. The use of GSM and GPS provides a robust solution for areas with limited connectivity.
