# I2C SSD1306 DMA Bare-Metal Driver

This repository contains a minimal SSD1306 OLED display driver implemented for bare-metal systems using I2C.

Tested only on STM32F4

## Overview

The driver provides basic functionality for initializing the SSD1306 controller, managing a frame buffer, and transmitting display data over I2C.
## Features

- Bare-metal implementation without HAL or RTOS
- I2C communication with optional (unable now) DMA transfers
- Command and data transmission to the SSD1306 controller
- Frame buffer handling

## Usage
```c
void delay_ms(uint32_t ms){
    volatile uint32_t count;
    while(ms--){
        count = 18000;
        while(count--) __asm__("nop");
    }
}

int main(void){
    I2C1_init(); 
    SSD1306_Init(); 
    SSD1306_Clear(); 

    
    for(uint8_t x=10; x<20; x++) {
        for(uint8_t y=10; y<20; y++) {
            SSD1306_DrawPixel(x, y, 1); 
        }
    }

    SSD1306_UpdateScreen();

    delay_ms(2000);

    
    SSD1306_DrawString(0, 16, "Hello, world!");
    SSD1306_UpdateScreen(); 

    delay_ms(2000);

    
    const uint8_t smiley[8] = {0x3C,0x42,0xA5,0x81,0xA5,0x99,0x42,0x3C};
    SSD1306_DrawBitmap(50, 16, smiley, 8, 8);
    SSD1306_UpdateScreen();

    delay_ms(2000);

    while(1) {
        ...
    }
}
```
