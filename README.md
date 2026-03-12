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

Use the file: debugprobe_on_pico2.uf2


Steps:

1. Hold **BOOTSEL**
2. Connect Pico to USB
3. Drag the UF2 file into the mounted drive

After flashing, the board will appear as a **CMSIS-DAP debug probe**.

---

# Wiring

| Debug Probe | Target |
|-------------|--------|
| GP3 | SWDIO |
| GP2 | SWCLK |
| GND | GND |

Both boards should be powered via **USB from the PC**.

---

# Install probe-rs

Install probe-rs tools:

```bash
curl -LsSf https://github.com/probe-rs/probe-rs/releases/latest/download/probe-rs-tools-installer.sh | sh
