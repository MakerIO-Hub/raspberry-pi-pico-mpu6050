# Shooter Pi: Motion-Controlled Space Combat Game with Raspberry Pi Pico

Shooter Pi is an immersive "Shoot 'em up" space arcade game controlled entirely by physical tilt movements, combining the processing power of the Raspberry Pi Pico with the precision of the MPU-6050 accelerometer. Build your own portable handheld gaming console using just a display, a few buttons, and a microcontroller!

📺 Watch the Full Project Video on YouTube: https://youtu.be/sREG-6Z4qks

## About the Project

In Shooter Pi, you pilot your spaceship by physically tilting the device left or right to evade and shoot down enemies and incoming orange rockets. The project runs on a custom physics engine that translates hardware accelerometer data into in-game coordinates, paired with an optimized graphical interface for the ILI9341 SPI display.

## Technical Specifications & Hardware

At the heart of the project is the Raspberry Pi Pico, managing all game logic and data flows at a 40MHz SPI speed.

| Component          | Role / Function                                              |
| ------------------ | ------------------------------------------------------------ |
| Raspberry Pi Pico  | Core game engine, sensor data processing, timing management. |
| MPU-6050           | Accelerometer and gyroscope for precise tilt control.        |
| ILI9341 (2.8" TFT) | High-speed graphics rendering and game UI drawing.           |
| Push Buttons (4x)  | Menu navigation, in-game selection, and firing.              |
| Passive Buzzer     | Instant sound effects for laser firing and collisions.       |

## Wiring & Pinout Diagram

Use the following table as a reference while wiring your circuit. Important Note: Proper power supply for VCC and backlight LED lines is critical for display stability and brightness.

| Part             | Pin Name        | Pico (GP) | Physical Pin | Power / Supply   |
| ---------------- | --------------- | --------- | ------------ | ---------------- |
| MPU-6050         | SDA             | GP0       | Pin 13       | 3V3 OUT          |
| MPU-6050         | SCL             | GP1       | Pin 2        | 3V3 OUT          |
| Button (Up)      | \---            | GP10      | Pin 14       | GND              |
| Button (Down)    | \---            | GP11      | Pin 15       | GND              |
| Button (Fire)    | \---            | GP12      | Pin 16       | GND              |
| Buzzer           | (+) Leg         | GP15      | Pin 20       | GND              |
| Display          | RST             | GP17      | Pin 22       | \---             |
| Display          | SCK             | GP18      | Pin 24       | \---             |
| Display          | MOSI            | GP19      | Pin 25       | \---             |
| Display          | CS              | GP20      | Pin 26       | \---             |
| Display          | DC              | GP21      | Pin 27       | \---             |
| Display          | LED (Backlight) | \---      | \---         | 3V3 OUT (Pin 36) |
| Display / Sensor | VCC             | \---      | \---         | 3V3 OUT (Pin 36) |

## Key Features

- Dynamic Difficulty Modulation: Enemy density increases after 300 points, scaling up the challenge.
- Rocket Attacks: Special orange rockets spawn after 150 points, introducing an extra layer of threat.
- Countdown "Continue" Screen: When your lives run out, the game doesn't end immediately; you have 10 seconds to press a button and continue with a small score penalty.
- Sleek HUD Layout: Top status bar displaying S:Score, L:Lives, and T:Minute:Second timers.
- Visual Feedback: 2-second "Invincible" status with spaceship blinking animation after taking damage.

## Getting Started

1. Assemble the Hardware: Complete your breadboard or soldered connections according to the pinout table.
2. Install Libraries: Ensure the ili9341 and mpu6050 driver modules are uploaded to your Pico's /lib directory.
3. Power Up: When connected via USB, a brief startup delay is defined for display initialization; if you see a blank white screen, check your wiring and press the reset button.
