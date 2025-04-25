

## Code Table Controler

| OPCode | Function |
| ------ | -------- |
| 0x0    | mv       |
| 0x1    |          |
| 0x2    |          |
| 0x3    |          |
| 0x4    |          |
| 0x5    |          |
| 0x6    |          |
| 0x7    |          |
| 0x8    |          |
| 0x9    |          |
| 0xA    |          |
| 0xB    |          |
| 0xF    |          |

## Code Table ALU

| OPCode | Function | Comp   |
| ------ | -------- | ------ |
| 0x0    | NOT      | 1 (!B) |
| 0x1    | OR       | 0      |
| 0x2    | AND      | 0      |
| 0x3    | XOR      | 0      |
| 0x4    | ADD/SUB  | 0/1    |
| 0x5    | XNOR     | x      |
| 0x6    | NOR      | x      |
| 0x7    | NAND     | x      |
| 0x8    | MUL      | x      |
| 0x9    | DIV      | x      |
| 0xA    | SHIFT L  | B      |
| 0xB    | SHIFT R  | B      |
| 0xF    | REM      | x      |
