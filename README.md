# PIC18F4550 LCD Infusion Timer

Embedded C project for the PIC18F4550 microcontroller implementing an LCD-based infusion timer interface. The system allows the user to configure a countdown time using push buttons, displays the selected time on an LCD, and shows a simple animated drop while the timer is running.

This project was developed as an academic embedded systems practice and later organized as part of a technical portfolio focused on biomedical engineering, microcontroller programming, and medical device interface prototyping.

## Features

* LCD-based user interface for time configuration and countdown display.
* Four-button control system for adjusting and confirming the programmed time.
* Custom LCD characters for a simple animated infusion/drop indicator.
* Countdown logic using minutes and seconds in `MM:SS` format.
* PIC18F4550 configuration and port setup.
* Modular LCD control through separate source and header files.
* Compiled `.hex` file included for microcontroller programming.

## Technologies Used

* C
* PIC18F4550 microcontroller
* MPLAB X / XC8
* 16x2 LCD display
* Digital input/output ports
* Push-button interface
* Custom LCD characters

## Project Structure

```text
.
├── main.c              # Main application logic
├── LCD_PORTD.c         # LCD control functions
├── LCD_PORTD.h         # LCD function declarations and pin definitions
├── LCD_commands.h      # LCD command definitions
├── Characters.h        # Custom LCD character definitions
├── config.h            # PIC18F4550 configuration bits
└── PROYECTO3.hex       # Compiled HEX file
```

## How It Works

1. The PIC18F4550 initializes the LCD and configures the required input/output ports.
2. The LCD displays the title `INFUSION` and an initial timer value of `00:00`.
3. The user adjusts the time using four push buttons:

   * `UP`: increases the selected digit.
   * `LEFT`: moves the cursor to the previous editable digit.
   * `RIGHT`: moves the cursor to the next editable digit or confirms the configuration.
4. After confirmation, the system starts the countdown.
5. While the countdown runs, a custom drop animation is displayed on the LCD.
6. When the timer reaches the end, the LCD displays `END`.

## Button Mapping

| Button | PIC Pin / Input | Function                    |
| ------ | --------------- | --------------------------- |
| UP     | RB0             | Increase selected digit     |
| LEFT   | RB1             | Move cursor left            |
| RIGHT  | RB2             | Move cursor right / confirm |
| DOWN   | RB3             | Reserved / defined in code  |

## LCD Interface

The LCD is controlled through PORTD, with control pins defined through PORTE/LATE:

| LCD Signal | PIC18F4550 Pin Definition |
| ---------- | ------------------------- |
| RS         | `LATEbits.LE0`            |
| EN         | `LATEbits.LE1`            |
| Data lines | PORTD                     |

The project includes custom LCD functions such as:

```c
iniLCD();
LCDcommand();
LCDchar();
LCDprint();
MoveCursor();
GenChar();
```

## Custom Characters

The file `Characters.h` defines two custom drop symbols used for the infusion animation. These characters are loaded into the LCD CGRAM and displayed alternately to simulate movement.

## Main Functions

| Function             | Description                                                                      |
| -------------------- | -------------------------------------------------------------------------------- |
| `main()`             | Initializes the oscillator, ports, LCD, and starts the infusion timer interface. |
| `practicaInfusion()` | Main application routine for displaying the interface and running the timer.     |
| `programarTiempo()`  | Allows the user to configure the countdown time.                                 |
| `check4Buttons()`    | Reads button inputs and updates the selected timer digit.                        |
| `contar()`           | Performs countdown logic for minutes and seconds.                                |
| `animateDrop()`      | Displays the animated drop on the LCD.                                           |
| `myChars()`          | Loads custom LCD characters into CGRAM.                                          |

## Learning Outcomes

Through this project, I practiced:

* Embedded C programming for PIC microcontrollers.
* LCD interfacing using digital I/O ports.
* Button-based user input handling.
* Custom character generation for LCD displays.
* Countdown logic using character-based numeric values.
* Modular code organization using `.c` and `.h` files.
* Basic interface design for a biomedical-inspired embedded system.

## Possible Improvements

* Add button debouncing for more stable input detection.
* Use hardware timers instead of software delays for more accurate timing.
* Improve the DOWN button functionality.
* Add a pause/resume option.
* Add a circuit diagram or simulation screenshot.
* Reorganize source files into `src/`, `include/`, and `build/` folders.

## Notes

This project is an academic prototype and is not intended for real medical use. It was designed for learning purposes and demonstrates embedded systems concepts related to LCD interfaces, timers, and biomedical device-inspired applications.
