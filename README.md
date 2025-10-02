# STM32 Ultrasonic Distance Sensor with LED Indicator

This project uses an STM32 microcontroller and an HC-SR04 ultrasonic sensor to measure distance and display the result visually on a series of 5 LEDs. The closer an object is, the fewer LEDs light up, creating a simple bar graph indicator.



---

## 📋 Features

* **Distance Measurement**: Utilizes an HC-SR04 ultrasonic sensor for non-contact distance sensing.
* **Visual Feedback**: Displays the measured distance on 5 LEDs, acting as a proximity bar graph.
* **Timer-Based Precision**: Uses STM32's hardware timers (TIM4) for precise echo pulse measurement, ensuring accuracy.
* **Push-Button Activation**: The measurement cycle is initiated by pressing an onboard user button.

---

## 🛠️ Hardware & Software Requirements

### Hardware
* An STM32 development board (e.g., Nucleo, Discovery, or a custom board)
* HC-SR04 Ultrasonic Sensor
* 5x LEDs (any color)
* 5x Current-limiting resistors (e.g., 220Ω or 330Ω)
* 1x Push-button
* Breadboard and jumper wires

### Software
* **STM32CubeIDE**: The project is configured to be built with the STM32CubeIDE.
* **STM32 HAL Drivers**: The code is based on the HAL (Hardware Abstraction Layer) library.

---

## ⚙️ How It Works

1.  **Trigger**: When the user button is pressed, the STM32 sends a 10-microsecond pulse to the sensor's `TRIGGER` pin.
2.  **Echo**: The HC-SR04 sensor emits an ultrasonic wave. When the wave hits an object and returns, the sensor sets its `ECHO` pin to HIGH. The duration of this HIGH signal is proportional to the distance.
3.  **Measurement**: The STM32's timer captures the start (rising edge) and end (falling edge) of the `ECHO` pulse to measure its duration.
4.  **Calculation**: The firmware calculates the distance in millimeters using the formula:
    `Distance = (Pulse Duration * Speed of Sound) / 2`
5.  **Display**: Based on the calculated distance, the LEDs are lit up as follows:
    * **0 - 100 mm**: 1 LED
    * **101 - 200 mm**: 2 LEDs
    * **201 - 300 mm**: 3 LEDs
    * **301 - 400 mm**: 4 LEDs
    * **401 - 500 mm**: 5 LEDs
    * **> 500 mm**: All LEDs off

---

## 🚀 Getting Started

### Pin Configuration
Ensure your pins in STM32CubeMX are configured as follows:
* **HC-SR04 Trigger**: GPIO Output (e.g., `PB10`)
* **HC-SR04 Echo**: Timer Input Capture (e.g., `PB6` for `TIM4_CH1`)
* **LEDs**: 5x GPIO Output pins (e.g., `PA0` to `PA4`)
* **Button**: GPIO Input (e.g., `PB3`)

### Setup
1.  Clone this repository or download the source code.
2.  Open the project in STM32CubeIDE.
3.  Ensure the `.ioc` file reflects your specific board and pin connections. If not, modify it and regenerate the code.
4.  Build the project (compile and link).
5.  Flash the generated `.elf` file to your STM32 board using a programmer (like an ST-LINK).
6.  Power on the board and press the button to start measuring!

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
