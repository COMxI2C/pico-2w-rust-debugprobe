# Pico 2W Rust Debug Probe

Using two Raspberry Pi Pico 2W boards as Debug Probe and Target with Rust and probe-rs.

## Hardware Setup

![Hardware Setup](docs/images/hardware_setup.jpg)

Example project showing how to use **two Raspberry Pi Pico 2W (RP2350)** boards as:

* **Debug Probe** (CMSIS-DAP)
* **Target MCU**

The firmware is written in **Rust using the Embassy async framework**, and flashing/debugging is done with **probe-rs**.

---

# Hardware

Required components:

* 2 × Raspberry Pi Pico 2W (RP2350)

One board acts as the **debug probe**, the other as the **target device**.

Both boards are connected to the PC via USB.

---

# Flash Debug Probe Firmware

Download the firmware from:

https://github.com/raspberrypi/debugprobe/releases

Use the file:

```
debugprobe_on_pico2.uf2
```

Steps:

1. Hold the **BOOTSEL** button on the Pico.
2. Connect it to the PC via USB.
3. Drag the `.uf2` file to the mounted USB drive.

After flashing, the board will appear as a **CMSIS-DAP debug probe**.

---

# Wiring

| Debug Probe | Target |
| ----------- | ------ |
| GP3         | SWDIO  |
| GP2         | SWCLK  |
| GND         | GND    |

Both boards remain powered through their USB connections.

---

# Install probe-rs

Install the probe-rs tools:

```bash
curl -LsSf https://github.com/probe-rs/probe-rs/releases/latest/download/probe-rs-tools-installer.sh | sh
```

Verify installation:

```bash
probe-rs --version
```

---

# Verify Debug Probe

Check that the probe is detected:

```bash
lsusb
```

Expected output example:

```
2e8a:000c Raspberry Pi Debugprobe on Pico (CMSIS-DAP)
```

---

# Verify Target Connection

```bash
probe-rs info --chip RP2350
```

Expected output:

```
ARM Chip with debug port
Cortex-M33
```

---

# Build the Firmware

From the project directory run:

```bash
cargo build
```

The compiled firmware will be generated at:

```
target/thumbv8m.main-none-eabihf/debug/pico-2w-rust-debugprobe
```

---

# Flash and Run

Flash and run the firmware:

```bash
probe-rs run target/thumbv8m.main-none-eabihf/debug/pico-2w-rust-debugprobe --chip RP235x
```

Expected terminal output:

```
Erasing ✔
Programming ✔
Finished
```

---

# Alternative Cargo Tools

Install:

```bash
cargo install probe-rs-tools
```

Flash firmware:

```bash
cargo flash --chip RP235x
```

Run with RTT logging:

```bash
cargo embed
```

---

# Common Issue

### Error

```
interface is busy (errno 16)
```

Cause: another process is already using the debug probe (for example a running RTT terminal).

Solution:

```bash
pkill probe-rs
```

or close the active debugging terminal.

---

# License

MIT
