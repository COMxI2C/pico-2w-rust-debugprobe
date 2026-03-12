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

erify installation:

probe-rs --version
Verify the Debug Probe

Check USB devices:

lsusb

Expected output:

2e8a:000c Raspberry Pi Debugprobe on Pico (CMSIS-DAP)
Verify Target Communication
probe-rs info --chip RP2350

Expected output:

ARM Chip with debug port
Cortex-M33
Build Firmware

From the project directory:

cargo build

The firmware will be generated at:

target/thumbv8m.main-none-eabihf/debug/pico-2w-rust-debugprobe
Flash Firmware
probe-rs run target/thumbv8m.main-none-eabihf/debug/pico-2w-rust-debugprobe --chip RP235x

Expected output:

Erasing ✔
Programming ✔
Finished
Alternative: Cargo Integration

Install tools:

cargo install probe-rs-tools

Flash firmware:

cargo flash --chip RP235x

Or run with logging:

cargo embed
Example Firmware

The example firmware:

Uses Embassy async runtime

Uses defmt RTT logging

Toggles an LED every 1.5 seconds

Common Issue
Error
interface is busy (errno 16)

Cause:

Another process is already using the debug probe (RTT terminal or cargo embed).

Solution:

Close the RTT terminal or kill the process:

pkill probe-rs