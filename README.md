# Crazy Programmable Device (CPD)

##(Planned) Features
* 6MHz Z80 Processor
* UART Serial Communication
* 32k RAM
* 32k ROM
* CF Card Support (FAT16 or FAT12)

##Memory layout:
| Address       | Type |
| ------------- | ------------- |
| 0x0000-0x7FFF | ROM  |
| 0x8000-0xFFFF | RAM  |

##IO
| A7       | Device |
| ------------- | ------------- |
| 0 | IDE Port (CF Card)  |
| 1 | UART (16550)  |

## Circuit Diagram
![CPD](circuit.png)
