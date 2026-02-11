# Line-Following-Robot

Line Following Robot using Arduino
Project Overview

This project is a Line Following Robot built using an Arduino, IR sensors, and TT gear motors.
The robot detects a black line on a light surface and moves along the path automatically by adjusting motor direction and speed.

It uses two IR sensors to continuously check the position of the line and control the motors accordingly.


**Working Principle**

The robot follows a black line based on sensor readings:
| Left Sensor | Right Sensor | Robot Action  |
| ----------- | ------------ | ------------- |
| LOW         | LOW          | Move Straight |
| LOW         | HIGH         | Turn Left     |
| HIGH        | LOW          | Turn Right    |
| HIGH        | HIGH         | Stop          |


LOW → No black line detected

HIGH → Black line detected

**Components Required**

Arduino Uno / Nano

L298N Motor Driver (or similar)

2 × TT Gear Motors

2 × IR Sensor Modules

Robot chassis

Wheels + caster wheel

Battery pack (7–12V)

Jumper wires


**Pin Configuration**
IR Sensors
| Sensor          | Arduino Pin |
| --------------- | ----------- |
| Right IR Sensor | D11         |
| Left IR Sensor  | D12         |


Right Motor
| Motor Driver Pin   | Arduino Pin |
| ------------------ | ----------- |
| Enable Right Motor | D6          |
| IN1                | D7          |
| IN2                | D8          |


Left Motor
| Motor Driver Pin  | Arduino Pin |
| ----------------- | ----------- |
| Enable Left Motor | D5          |
| IN3               | D9          |
| IN4               | D10         |


This line increases the PWM frequency of pins D5 and D6.

TT motors do not rotate properly at very low PWM. A higher frequency allows:

Smoother motor control

Better low-speed movement

Stable line following

PWM frequency is set to 7812.5 Hz.



**Control Logic**

The robot continuously:

Reads both IR sensors.

Decides direction:

Both sensors off line → Move forward

One sensor on line → Turn towards line

Both sensors on line → Stop

Sets motor direction using rotateMotor()


Important Function
rotateMotor(int rightMotorSpeed, int leftMotorSpeed)

**Controls:**

Direction of motors

Speed using PWM

Positive value → Forward

Negative value → Reverse

Zero → Stop


**How to Run**

Connect all components as per pin configuration.
Upload the Arduino code.
Place the robot on a track with a black line on a white surface.
Power the robot.
It will automatically start following the line.



**Troubleshooting**
| Problem                  | Solution                          |
| ------------------------ | --------------------------------- |
| Robot not moving         | Check motor driver power          |
| Robot too fast           | Reduce `MOTOR_SPEED` value        |
| Not detecting line       | Adjust IR sensor sensitivity knob |
| Moves opposite direction | Swap motor wires                  |



**Future Improvements**

Add more IR sensors for better accuracy
Implement PID control
Add obstacle detection
Bluetooth/WiFi control
