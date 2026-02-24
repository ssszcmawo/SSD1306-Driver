# I2C SSD1306 DMA Bare-Metal Driver

This repository contains a minimal SSD1306 OLED display driver implemented for bare-metal systems using I2C with DMA support.

Tested only on STM32F4

## Overview

The driver provides basic functionality for initializing the SSD1306 controller, managing a frame buffer, and transmitting display data over I2C using DMA.
## Features

- Bare-metal implementation without HAL or RTOS
- I2C communication with optional (unable now) DMA transfers
- Command and data transmission to the SSD1306 controller
- Frame buffer handling
## Directory Structure

- `src/` Source files of the driver
- `include/` Header files
- `test/` Simple usage examples and test code
