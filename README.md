# Pico 2W Rust Debug Probe

Using two **Raspberry Pi Pico 2W** boards to create a **SWD Debug Probe** for embedded development using **Rust** and **probe-rs**.

This project demonstrates how to configure one Pico as a **debug probe** and another Pico as the **target device**, enabling debugging, flashing, and RTT logging.

---

## Hardware Setup

![Hardware Setup](docs/images/hardware_setup.jpg)

Two Pico 2W boards are connected through the **SWD interface**.
One board acts as the **debug probe**, while the other is the **target microcontroller** being programmed and debugged.

---

## Project Goals

* Build a **low-cost debug probe**
* Learn **embedded debugging with Rust**
* Understand **SWD communication**
* Use **probe-rs** tooling
* Document the complete setup

---

## Hardware

Required components:

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

This project uses the following tools:

* Rust
* cargo
* probe-rs
* probe-rs-tools
* OpenOCD (optional)

---

## Flashing the Firmware

Example using `probe-rs`:

```bash
probe-rs run --chip RP2040 target/thumbv6m-none-eabi/debug/app
```

---

## Debugging

You can start a debugging session using:

```bash
probe-rs debug --chip RP2040
```

---

## Project Structure

```
pico-2w-rust-debugprobe
│
├── src
├── Cargo.toml
├── README.md
│
└── docs
    └── images
        └── hardware_setup.jpg
```

---

## Future Improvements

* Add a **Fritzing wiring diagram**
* Implement **RTT logging example**
* Add **step-by-step setup guide**
* Measure **debugging performance**

---

## License

MIT License
