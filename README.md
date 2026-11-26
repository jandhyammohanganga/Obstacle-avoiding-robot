# Obstacle Avoiding Robot

An autonomous robot built on the Arduino Uno (ATmega328P). An ultrasonic sensor
mounted on a servo detects obstacles, and the robot steers toward the side with
more free space.

## How it works
1. The robot drives forward continuously.
2. If an obstacle is within **20 cm**, it stops.
3. The servo turns the ultrasonic sensor to the left, then to the right, and measures both distances.
4. The robot turns toward the side with the larger distance, then continues forward.

## Hardware
| Component | Purpose |
|---|---|
| Arduino Uno (ATmega328P) | Main controller |
| L293D motor driver | Drives the two DC motors |
| Ultrasonic distance sensor | Measures distance to obstacles |
| Servo motor | Rotates the sensor left and right |
| 2 x DC geared motors | Movement |
| Power supply | Battery / regulated 5 V (7805 based supply described in the report) |

## Pin connections
| Signal | Arduino Pin |
|---|---|
| ENA (Motor 1 enable) | 13 |
| IN1 | 5 |
| IN2 | 6 |
| IN3 | 9 |
| IN4 | 10 |
| ENB (Motor 2 enable) | 12 |
| Ultrasonic Trig | 7 |
| Ultrasonic Echo | 8 |
| Servo signal | 11 (change `SERVO_PIN` in the code to match your wiring) |

## Repository structure
```
obstacle-avoiding-robot/
├── README.md
├── firmware/
│   └── obstacle_avoiding_robot/
│       └── obstacle_avoiding_robot.ino
└── docs/
    └── Project_Report.pdf
```

## How to run
1. Install the [Arduino IDE](https://www.arduino.cc/en/software).
2. Open `firmware/obstacle_avoiding_robot/obstacle_avoiding_robot.ino`.
3. Select **Tools > Board > Arduino Uno** and the correct **Tools > Port**.
4. Click **Upload**.
5. Open the Serial Monitor at **9600 baud** to see distance readings.

## Notes
- ENA and ENB are on pins 13 and 12, which are not PWM pins on the Uno, so the motors run at full speed (on/off) rather than variable speed.
- The `Servo` library disables PWM on pins 9 and 10; this is fine here because they are only used with `digitalWrite`.

## Documentation
Full project report: [docs/Project_Report.pdf](docs/Project_Report.pdf)

## Author
Jandhyam Mohan Ganga
