# Pico 2W Rust Debug Probe

Using two **Raspberry Pi Pico 2W** boards to build a **SWD debug probe** for embedded development with **Rust** and **probe-rs**.

This repository documents the hardware setup, firmware, and debugging workflow.

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
