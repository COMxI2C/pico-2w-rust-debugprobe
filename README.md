# Raspberry Pi Pico 2W Debugging with Rust

This project demonstrates how to use **two Raspberry Pi Pico 2W (RP2350)** boards:

- One as a **CMSIS-DAP Debug Probe**
- One as the **Target MCU**

The firmware is written in **Rust using the Embassy async framework**, and flashing/debugging is performed using **probe-rs**.

---

# Hardware Required

- 2 × Raspberry Pi Pico 2W (RP2350)

One board will act as:

- Debug probe

The other board will act as:

- Target MCU

---

# Flash Debug Probe Firmware

Download the firmware:

https://github.com/raspberrypi/debugprobe/releases

Use the file:
