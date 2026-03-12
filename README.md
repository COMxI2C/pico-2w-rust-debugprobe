# Pico 2W Rust Debug Probe

This project demonstrates how to transform two **Raspberry Pi Pico 2W** boards into a complete **Serial Wire Debug (SWD) debugging environment** for ARM microcontrollers using **Rust** and **probe-rs**.

**SWD (Serial Wire Debug)** is the standard debugging interface used by most **ARM Cortex-M microcontrollers**, allowing developers to **flash firmware, halt execution, inspect memory, set breakpoints, and perform real-time debugging**.

In this setup:

* One **Pico 2W** acts as the **debug probe**
* The second **Pico 2W** acts as the **target microcontroller**

Using the open-source **probe-rs ecosystem**, this configuration enables a fully functional **embedded debugging workflow** without requiring commercial debug hardware such as ST-Link or J-Link.

This repository provides:

* A **step-by-step hardware setup**
* The **precompiled firmware** required for the debug probe
* The **wiring configuration** between probe and target
* The **Rust-based debugging workflow** using probe-rs

The goal is to build a **low-cost, open-source debugging platform** while exploring the internals of **SWD communication and Rust embedded tooling**.

---

## Hardware Setup

![Hardware Setup](docs/images/hardware_setup_pico.jpeg)

Two Pico boards are connected using the **SWD interface**.

One board acts as the **debug probe**, while the second board is the **target device**.

---

## Download Precompiled Firmware

You can download the compiled debug probe firmware here:

https://github.com/raspberrypi/debugprobe/releases

Flash the firmware into the Pico that will act as the **debug probe**.

---

## Hardware Required

* 2 × Raspberry Pi Pico 2W
* Breadboard
* Jumper wires
* USB cables

---

## Wiring

| Debug Probe | Target Pico |
| ----------- | ----------- |
| SWDIO       | SWDIO       |
| SWCLK       | SWCLK       |
| GND         | GND         |

---

## Software Stack

This project uses:

* Rust
* cargo
* probe-rs
* probe-rs-tools

---

## Flashing Example

Example command using probe-rs:

```bash
probe-rs run --chip RP2040 target/thumbv6m-none-eabi/debug/app
```

---

## Repository Structure

```
pico-2w-rust-debugprobe
│
├── src
├── Cargo.toml
├── README.md
│
└── docs
    └── images
        └── hardware_setup.jpeg
```

---

## Future Improvements

* Add wiring diagram (Fritzing)
* RTT logging example
* Step-by-step setup tutorial
* Debugging benchmarks

---

## License

MIT License
