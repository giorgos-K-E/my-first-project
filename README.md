# my-first-project
einai-to-proto-upload





# Arduino UNO R4 WiFi – Two LEDs Blink With Button Press

## Overview
This project demonstrates how to connect **two LEDs and one push button** to an **Arduino UNO R4 WiFi**.  
Each time the button is pressed, **both LEDs blink once**.

This is a simple beginner project that covers:
- Digital input (button)
- Digital output (LEDs)
- Basic debouncing logic
- Using the Arduino UNO R4 WiFi

---

## Components Required
- Arduino UNO R4 WiFi
- 2 × LEDs
- 2 × 220Ω resistors (for LEDs)
- 1 × Push button
- Breadboard
- Jumper wires

---

## Circuit Connections

### LEDs
- **LED 1**
  - Long leg (anode) → Digital pin **8** through a 220Ω resistor
  - Short leg (cathode) → **GND**

- **LED 2**
  - Long leg (anode) → Digital pin **9** through a 220Ω resistor
  - Short leg (cathode) → **GND**

### Button
- One side of the button → Digital pin **2**
- Other side of the button → **GND**

> The button uses the Arduino’s internal pull-up resistor, so no external resistor is needed.

---

## Arduino Code

```cpp
const int led1 = 8;
const int led2 = 9;
const int buttonPin = 2;

int lastButtonState = HIGH;
int buttonState;

void setup() {
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(buttonPin, INPUT_PULLUP);

  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
}

void loop() {
  buttonState = digitalRead(buttonPin);

  // Detect button press (HIGH → LOW)
  if (lastButtonState == HIGH && buttonState == LOW) {
    // Blink both LEDs once
    digitalWrite(led1, Low);
    digitalWrite(led2, HIGH);
    delay(200);
    digitalWrite(led1, LOW);
    digitalWrite(led2, LOW);
  }

  lastButtonState = buttonState;
}
