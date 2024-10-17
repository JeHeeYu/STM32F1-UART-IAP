# STM32F1-UART-IAP

<br>

## Introduction
This project is an STM32F10x series example code and IAP(In-Application-Programming) example code using UART.

<br>

## Usage

### 1. Project Run application
- When checking Teraterm after execution, ... is displayed.

![1](https://github.com/user-attachments/assets/a8f33385-71d9-461f-ab1c-1c225ada4943)

<br>

### 2. Press any key
- When you input a key, a selection screen is displayed as shown in the picture.

![2](https://github.com/user-attachments/assets/8fe1408a-fdf2-4ba8-9873-10b94718d240)

<br>

### 3. Press number 1
- Program update ready

<br>

### 4. File upload
- Upload the .bin file using the File - Transfer - Y-Modem - Send menu.

![4](https://github.com/user-attachments/assets/fafcb569-9612-41da-bba7-e8a8e56cdde7)

<br>

### 5. Update complete
- The file name and size appear.

![5](https://github.com/user-attachments/assets/a8199813-0838-4c83-86e5-6f330b994700)

<br>

### 6. Run application
- The user application runs.

![6](https://github.com/user-attachments/assets/72f1bda5-8fc0-4333-b61c-98d2801ddc64)

<br>

## Setting the starting flash memory address
- The address is in STM32xxx_FLASH.ld.

- IAP code start flash memory address
```
MEMORY
{
  RAM    (xrw)    : ORIGIN = 0x20000000,   LENGTH = 20K
  FLASH    (rx)    : ORIGIN = 0x8004000,   LENGTH = 16K
}
```

- User application start flash memory address
```
MEMORY
{
  RAM    (xrw)    : ORIGIN = 0x20000000,   LENGTH = 20K
  FLASH    (rx)    : ORIGIN = 0x8004000,   LENGTH = 64 - 16K
}
```

## Other setting
Additional settings are required in the user application.

### 1. Add USER_HAL_DRIVER define
- Project - Properties - C/C++ Build - Settings - MCU GCC Compiler - Proprocessor - Add USER_HAL_DRIVER

![6](https://github.com/user-attachments/assets/30896f1f-ba7c-4c98-91fc-61a926a8f75c)

<br>

### 2. Modify VECT_TAB_OFFSET
- Modify VECT_TAB_OFFSET value in SRC/system_stm32f1xx.c file

![image](https://github.com/user-attachments/assets/028d0bd8-67cb-4ebc-b0f5-4778fa431c86)

- Adding number 1 will activate it.
