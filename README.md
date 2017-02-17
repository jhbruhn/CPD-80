# Crazy Programmable Device (CPD)

##(Planned) Features
* 6MHz Z80 Processor
* UART Serial Communication
* 64k RAM
* 32k ROM
* CF Card Support (FAT16 or FAT12)

##Memory layout:
| Address       | Type |
| ------------- | ------------- |
| 0x0000-0x7FFF | ROM / RAM  |
| 0x8000-0xFFFF | RAM  |

##IO
| A11| A10| A9 | A8 | Device                                                  |
| ---|----|----|----|---------------------------------------------------------|
| 0  | 0  | 0  | 0  | IDE Port (CF Card)                                      |
| 0  | 0  | 0  | 1  | UART (16550)                                            |
| 0  | 0  | 1  | 0  | PS/2 Keyboard                                           |
| 0  | 0  | 1  | 1  | RTC-72421                                               |
| 0  | 1  | 0  | 0  | MemoryBank (write 0 for ROM and 2 for RAM in first 32k) |
| 0  | 1  | 0  | 1  | Video (TMS9918)                                         |
| 0  | 1  | 1  | 0  | Audio (AY-3-8910A)                                      |


To Address device 0:

B = 0

OUT (C), d


To Address device 1:

B = 1

OUT (C), d

etc...

sdcc:
__banked __ad(0x16c) int pedabaumert oder so

##Future:
Video Card with TMS9918. Also PS/2 keyboard input (or something similar). Real time Clock?

## Boot:
* start at 0x0000.
* load Bootsector from CF card to 0x8000, or into BANK RAM at 0x0000.
* jump to 0x8000 (0x0000)
* Bootsector loads FAT files, executes KERNEL.ULF or something like that. Autoexec.
