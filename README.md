# Digital-Stethoscope
Designing a Digital Stethoscope Using a Microphone

# Digital Stethoscope using ESP32

This project is a simple and affordable digital stethoscope built using an ESP32 microcontroller, a 2-pin electret microphone, and a signal amplification circuit. It captures heart sounds, amplifies them using either an LM386 or a 741 op-amp, and displays the resulting waveform or voltage on an LCD screen. The signal can also be viewed using the Serial Plotter as a real-time oscilloscope.

## Features

* Detects and amplifies heart sounds from the chest
* Amplifies weak signals using an LM386 or 741 op-amp
* Converts analog signal to digital using ESP32 ADC (GPIO34)
* Displays voltage output on an LCD
* Optionally plots the waveform on the Serial Plotter

## Hardware Components

* ESP32-WROOM-32 microcontroller
* 2-pin electret microphone
* LM386 or 741 op-amp
* Two 1k ohm resistors (biasing)
* 2.2 microfarad capacitor (AC coupling)
* 100 microfarad capacitor (optional for stability)
* LCD display (I2C 16x2 or SPI TFT)
* Breadboard and jumper wires
* USB cable for power

## Circuit Overview

The microphone signal is first biased using a voltage divider made from two 1k ohm resistors. A 2.2µF capacitor is used to remove DC offset. The signal is then fed into an amplifier (either LM386 or 741), and the amplified signal is passed to GPIO34 on the ESP32. The ESP32 samples the signal and displays the voltage or waveform.

## Amplifier Options

**LM386 Setup**:

* Connect microphone output (after coupling capacitor) to pin 3 of LM386
* Gain set using a 10µF capacitor between pins 1 and 8
* Output from pin 5 is connected to ESP32 GPIO34 (with optional capacitor)
* Pin 6 to 5V, pin 2 to ground

**741 Setup**:

* Use non-inverting amplifier configuration
* Feed biased mic signal to pin 3
* Connect output (pin 6) to ESP32 GPIO34
* Use appropriate resistor values to set gain

## Display

The ESP32 reads the analog value from GPIO34, converts it to voltage, and displays it on an LCD. The Serial Plotter can also be used to visualize the waveform as the heart beats.

## File Structure

* stethoscope\_code.ino – Arduino code for ESP32
* stethoscope\_circuit.png – Microphone biasing and input connection diagram
* lm386\_amplifier\_circuit.png – LM386 amplifier circuit
* 741\_amplifier\_circuit.png – 741 op-amp circuit
* lcd\_display\_demo.png – Example LCD output showing voltage
* oscilloscope\_view\.png – Serial Plotter waveform view
* audacity\_processing.txt – Notes for optional audio processing
* components\_list.txt – Parts used in the project

## How It Works

When the microphone detects a heartbeat sound, the signal is amplified and sent to the ESP32’s analog input. The ESP32 samples the voltage and either displays it or sends it to the Serial Plotter. The signal gives a visual representation of the heartbeat waveform in real time.
