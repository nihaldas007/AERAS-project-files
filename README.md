# AERAS-project-files
AERAS: An IoT-based e-rickshaw hailing system designed for accessible transport for seniors and individuals with special needs.

By Team: IOT_One_Zero

An IoT-based e-rickshaw hailing system designed for accessible transport for seniors and individuals with special needs.

<!--

(📌 Edit this file to add your project's intro image here)

-->

<!-- Example:  -->

📋 Table of Contents

Introduction

Problem Statement

Features

System Architecture

Workflow

Hardware Components

Software Components

Use Case Scenario

Future Improvements

Conclusion

License

🚀 Introduction

The Accessible E-Rickshaw Automation System (AERAS) is an IoT-based solution designed to assist individuals with special needs and senior citizens. It provides an automated and accessible method to request an e-rickshaw, focusing on reducing communication barriers and ensuring a safe, contact-free interaction.

🎯 Problem Statement

People with disabilities or special needs often face difficulties in daily commuting. This can include trouble communicating with drivers, signaling for a rickshaw, or operating traditional hailing apps. AERAS aims to solve these issues by providing:

Hands-free or low-effort activation.

Simple, gesture-based input.

A clear visual feedback system.

Direct IoT-based communication to the driver, bypassing verbal barriers.

<!--

(📌 Add your Problem Illustration Image here)

-->

<!-- Example:  -->

✨ Features

Contactless Activation: Uses an ultrasonic sensor to detect user presence and activate the system.

Gesture-Based Hailing: A laser and LDR sensor combination allows for a simple gesture to confirm a ride request.

Instant Driver Notification: Transmits the request directly to a driver-side web interface via WiFi (ESP32).

Real-Time Visual Feedback: On-device Red/Green LEDs instantly inform the user if their ride is accepted or rejected.

Simple Driver UI: A clean web dashboard for drivers with "Accept" and "Reject" buttons.

Low Cost & Scalable: Built with common, affordable electronic components.

🔧 System Architecture

The system is divided into two main parts: the User-Side Device and the Driver-Side Web Interface.

High-Level Block Diagram

 [ USER SIDE DEVICE ]
 -----------------------
 | Ultrasonic Sensor   |----> Detects User Presence
 | Laser Module        |----> User Gesture
 | LDR Sensor          |----> Gesture Reading
 | Microcontroller     |----> Data Processing
 | WiFi Module (ESP32) |----> Sends Request
 | LEDs (Green/Red)    |----> Feedback
 -----------------------
            |
            | (HTTP Request)
            V
 -----------------------
 |  WEB SERVER (Driver) |
 -----------------------
            |
      (Accept / Reject)
            |
            V
  (Feedback to Device)


<!--

(📌 Add your System Block Diagram Image here)

-->

<!-- Example:  -->

Complete Architecture

    +--------------------+
    |    User Device     |
    |--------------------|
    | Ultrasonic Sensor  |
    | Laser + LDR Input  |
    | Microcontroller    |
    | WiFi Communication |
    +---------+----------+
              |
              | HTTP Request (JSON)
              V
    +-------------------------+
    |   Cloud / Local Server  |
    |-------------------------|
    | Request Handling Logic  |
    | Web Dashboard Backend   |
    +-----------+-------------+
                  |
             Web Interface
                  |
    +-------------------------+
    |   Driver’s Smartphone   |
    |-------------------------|
    | Accept / Reject Buttons |
    +-----------+-------------+
                  |
                  | Response
                  V
    +-------------------------+
    | User Device LEDs        |
    |   Green / Red Feedback  |
    +-------------------------+


<!--

(📌 Add your full Architecture Diagram Image here)

-->

<!-- Example:  -->

🌊 Workflow

Here is the step-by-step flow for the user and driver.

Functional Flow

A. User-Side Device

Detects user presence using an ultrasonic sensor.

Activates after the user stands within range for 3 seconds.

Accepts a confirmation gesture (laser input detected by LDR).

Sends the ride request to the server.

Shows a Green LED for an accepted ride or a Red LED for a rejected ride.

B. Driver-Side Web Interface

Receives the ride request and displays it on the dashboard.

Shows "Accept" / "Reject" buttons.

Sends the decision back to the user's device instantly.

Flowchart Logic

    User Approaches Device
            |
            V
   Ultrasonic Sensor Detects
            |
    (Distance < Threshold)
            |
            V
   Start 3-Second Activation Timer
            |
    (If user stays) -> Continue
            |
            V
      Device Activated
            |
            V
   User Gives Laser Gesture Input
            |
            V
    Gesture Detected by LDR
            |
            V
    Request Sent to Web Server
            |
            V
   Driver Sees Request (Accept/Reject)
            |
    +----------+----------+
    |                     |
    V                     V
  ACCEPT                REJECT
    |                     |
    V                     V
 Green LED ON          Red LED ON


<!--

(📌 Add your Workflow Flowchart Image here)

-->

<!-- Example:  -->

🛠️ Hardware Components

Microcontroller: ESP32 / Arduino

Presence Sensor: Ultrasonic Sensor (HC-SR04)

Input: Laser Module & LDR (Light Dependent Resistor)

Visual Feedback: LEDs (Red, Green)

Connectivity: WiFi Module (built into ESP32)

Power: Power Supply / Battery

Other: Resistors, Wires, Casing

Circuit Logic

        +----------------------+
        |     ESP32/Arduino    |
        +----------------------+
          |     |      |     |
          |     |      |     |
Trig (D5) -+     |      |     |
Echo (D18)-+     |      |     |
                 |      |     |
LDR (A0) --------+      |     |
                        |     |
Green LED (D14) --------+     |
Red LED (D13) ----------------+

(Ultrasonic, Laser VCC -> 5V)
(Ultrasonic, Laser GND -> GND)
(LDR with 10k Resistor -> GND)


<!--

(📌 Add your Circuit Diagram Image here)

-->

<!-- Example:  -->

💻 Software Components

Device Firmware: Arduino (C/C++) code for the ESP32 to manage sensors, connect to WiFi, and handle HTTP requests/responses.

Web Server / Backend: (e.g., Node.js, Python/Flask, or PHP) to handle API requests from the ESP32 and serve the driver dashboard.

Driver Dashboard (Frontend): Simple HTML, CSS, and JavaScript for the driver's web interface.

Communication Protocol: JSON-based communication over HTTP.

Driver Web UI (Layout)

 ----------------------------------------
|        AERAS DRIVER DASHBOARD          |
 ----------------------------------------
|  Incoming Request From User: YES       |
|                                        |
|    [ ACCEPT ]      [ REJECT ]          |
|                                        |
|  Status: Waiting for Driver Action...  |
 ----------------------------------------


<!--

(📌 Add your Web UI Screenshot here)

-->

<!-- Example:  -->

🚶 Use Case Scenario

A differently-abled person or senior citizen arrives at the AERAS stand.

The device detects their presence and activates automatically after 3 seconds.

The user provides the simple laser gesture to confirm they need a ride.

The nearest e-rickshaw driver receives the request instantly on their dashboard.

The driver presses "Accept".

The user sees the Green LED light up, confirming their ride is on the way.

<!--

(📌 Add a Use Case / Project Photo here)

-->

<!-- Example:  -->

🔮 Future Improvements

[ ] Voice Command: Add support for voice-based ride requests.

[ ] Mobile App: Develop a dedicated mobile app for users and drivers.

[ ] GPS Integration: Automatically detect the nearest driver based on GPS location.

[ ] Digital Payments: Integrate a simple digital payment system.

[ ] Emergency SOS: Add a physical SOS button for emergencies.

🏁 Conclusion

AERAS creates a vital bridge between e-rickshaw drivers and differently-abled passengers, ensuring a safe, user-friendly, and automated transport request system. This project highlights how IoT technology can be leveraged to create a significant positive impact on accessibility in our communities.

<!--

(📌 Add your Team Photo or Ending Image here)

-->

<!-- Example:  -->

📄 License

This project is licensed under the MIT License. See the LICENSE file for details.
