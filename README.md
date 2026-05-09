# L476-USART2-SimpleUpCounter
## STM32 UART Counter Example
Overview

This project demonstrates basic UART communication using an STM32 microcontroller and STM32 HAL library.

The firmware sends an incrementing counter value through USART2 every 1 second.

Example terminal output:
00
01
02
03
...
The data can be viewed using serial terminal software such as: PuTTY

Features
USART2 UART communication
9600 baud rate
Transmit counter value every second
STM32 HAL driver based
Simple beginner-friendly example

Hardware Requirements
STM32 development board
Example:
STM32 Nucleo-L476RG
USB cable
PC with serial terminal software

## UART Configuration
| Setting      | Value  |
| ------------ | ------ |
| Baud Rate    | 9600   |
| Word Length  | 8 Bits |
| Stop Bits    | 1      |
| Parity       | None   |
| Flow Control | None   |
| Mode         | TX/RX  |

## Main Logic
The main loop performs:

Convert counter value to string using sprintf()
Send string via UART using HAL_UART_Transmit()
Increment counter
Delay 1 second

Core code:
int Count = 0;
char buff[32];

while (1)
{
    sprintf(buff, "%5.2d \n\r", Count);

    HAL_UART_Transmit(
        &huart2,
        (uint8_t*) buff,
        strlen(buff),
        HAL_MAX_DELAY
    );

    Count++;

    HAL_Delay(1000);
}

## USART2 Pin Mapping
| Signal | Pin |
| ------ | --- |
| TX     | PA2 |
| RX     | PA3 |

## Important Notes
Line Ending

sprintf(buff, "%5.2d\r\n", Count);

Buffer Safety:
char buff[32];This size is safe for the current message format.

## Future Improvements

Possible upgrades:

Receive UART data
Echo received characters
Interrupt-based UART
DMA UART transmission
ADC + UART sensor monitoring
PWM control
Temperature monitoring system

