# Meadow F7 Micro Beta Status


## GPIO

| Feature          | Tested Working      | Notes                             |
|------------------|---------------------|-----------------------------------|
| Basic Digital IO | Yes. | Output, Input, no interrupts. |
| PWM              | | Blocked on interrupts. |
| Serial (UART)    | | Blocked on interrupts. |
| I2C              | | Blocked on interrupts. |
| SPI              | | Blocked on interrupts. |
| CAN              | | Blocked on interrupts. |
| DAC              | | Not implemented. |

## Working GPIO Ports

| Feature          | Tested Working      | Notes                             |
|------------------|---------------------|-----------------------------------|
| @"Meadow.Hardware.DigitalOutputPort" | Yes | |
| @"Meadow.Hardware.DigitalInputPort" | Yes, no interrupts. | Interrupts blocked. |
| @"Meadow.Hardware.BiDirectionalPort" | Yes, no interrupts. | Interrupts blocked. |

## Communications

| Feature          | Tested Working      | Notes                             |
|------------------|---------------------|-----------------------------------|
| WiFi	| | Working on co-proc. Not hooked to API. |
| Bluetooth | | Working on co-proc. Not hooked to API. |

## Other Features

| Feature          | Tested Working      | Notes                             |
|------------------|---------------------|-----------------------------------|
| Battery Charing  | Yes. |
| Battery Voltage Level | | Waiting on co-proc comms integration. |
| Power Management | | Not implemented. |