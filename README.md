# Embedded Rust and Embassy and a display

PCA9548A test

## Hardware Requirements

* RP2040
* RPi Pico Probe (for downloading and status messages from the RP2040)
* I2C SSD1306 OLED display (128x64 pixel)
* PCA9548A connected to a 
* BMP280 for pressure and temperature

## Software Requirements

* Install target compiler:

```
$ rustup target add thumbv6m-none-eabi
```

* To use the Pico probe:

```
$ cargo binstall probe-rs
```

* To use various tools, e.g. to see the code size of the generated ELF (e.g. `cargo size`):

```
$ cargo binstall cargo-binutils
$ cargo size
    Finished `dev` profile [optimized + debuginfo] target(s) in 0.05s
   text    data     bss     dec     hex filename
  42356       0  103960  146316   23b8c rp-bmp280
```

## Running it

The OLED is connected to I2C0 (GPIO 4 and 5). The PCA9548A is connected to I2C1 (GPIO 2 and 3).
The BMP280 is connected to bus 2 of the PCA9548A.
