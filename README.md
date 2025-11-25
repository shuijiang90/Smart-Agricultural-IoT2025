#  IoT-Based Environmental Monitoring and Control System for Greenhouse

A microservices-based Smart Agriculture system for real-time environmental monitoring and automated greenhouse control.  
This project collects and analyzes sensor data, triggers actuators based on dynamic thresholds, stores values in AWS DynamoDB, and supports system interaction through a Telegram bot and web RESTful API.
This system enables greenhouse environmental automation using IoT and cloud services.  
It supports multiple sensors and actuators and adopts a decoupled design using MQTT messaging for modular and scalable microservices.

Project guided by Prof. Lorenzo Bottaccioli & Pietro Rando Mazzarino<br/>
Team 4 — Yuxuan Wu, Shui Jiang, Ning Zhang



###  System Architecture


- **Sensors** (Temperature, Light, Soil Moisture, CO₂) publish data via MQTT
- **Controllers** subscribe to sensor topics and automatically trigger actuators based on configured thresholds
- **Actuators** include Heater, Cooler, Drip Irrigation, Exhaust Fan, LED light, Sunshade net
- **AWS DynamoDB** stores real-time and historical data
- **Telegram Bot** enables remote interaction
- **MQTT Broker** handles all messaging across services



### Architecture Components

| Module | Description |
|--------|------------|
| Sensor Service | Collects environmental data and publishes via MQTT |
| Controller Service | Makes decisions based on thresholds |
| Actuator Service | Executes automated actions |
| AmazonAwsAdapter | Stores data in DynamoDB |
| TelegramBot | Remote monitoring & actuator control |
| HTTP/REST Services | RESTful API for dashboard & integrations |
| MQTT Broker | message routing bus |
| config/log | system configuration & runtime logging |



###  Technology Stack

| Category | Technology |
|----------|------------|
| Messaging | MQTT (mqtt.eclipseprojects.io : 1883) |
| Backend | Python, CherryPy microservices |
| Cloud | AWS DynamoDB |
| Communication | RESTful APIs, Telegram Bot |
| Architecture | Distributed microservices |
| Storage | Cloud database with historical data queries |



### Start microservice servers (Page 9) :contentReference[oaicite:6]{index=6}

| Server | Port | Endpoint |
|--------|-------|--------------|
| HttpServer | 8080 | `/` |
| SensorServer | 8081 | `/sensor` |
| ControllerServer | 8082 | `/controller` |
| ActuatorServer | 8083 | `/actuator` |
| DynamoDB Reader | 8084 | `/DBreader` |
| DynamoDB Writer | background | — |
| TeleBot Server | background | — |



###  TelegramBot Features

- Sensor & actuator management
- Modify threshold values
- Query environment status in real time
- Add / remove sensors & actuators dynamically


