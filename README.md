# Assembly Instruction Set

## Registers
- **ACC** - Accumulator (8-bit, 0-255)
- **PC** - Program Counter

## Memory
- 256 bytes (addresses 0-255)
- All values are 8-bit (0-255)

## Instructions

### Data Movement

| Instruction | Operand | Description |
|-------------|---------|-------------|
| `SET n` | Value (0-255) | Load immediate value into ACC |
| `LAST n` | Address (0-255) | Load value from memory address into ACC |
| `LAGR n` | Address (0-255) | Store ACC value to memory address |

### Arithmetic

| Instruction | Operand | Description |
|-------------|---------|-------------|
| `ADD n` | Address (0-255) | Add memory[n] to ACC (wraps at 255) |
| `SUB n` | Address (0-255) | Subtract memory[n] from ACC (wraps at 0) |

### Control Flow

| Instruction | Operand | Description |
|-------------|---------|-------------|
| `HOPP n` | Line number | Jump unconditionally to line n |
| `HOPPN n` | Line number | Jump to line n if ACC == 0 |
| `HOPPIN n` | Line number | Jump to line n if ACC != 0 |
| `STOPP` | None | Halt program execution |

### Input/Output

| Instruction | Operand | Description |
|-------------|---------|-------------|
| `UT n` | Address (0-255) | Output character from memory[n] |
| `UTREG` | None | Output character from memory[ACC] |
| `LES n` | Address (0-255) | Read input character from provided file to memory[n] |

## Notes

- All arithmetic wraps around (255 + 1 = 0, 0 - 1 = 255)
- Line numbers start at 0
- Comments start with `;` or `#`
- Empty lines are ignored
- Instructions are case-insensitive

## Example Program

```assembly
; Print "Hi"
SET 72          ; 'H'
LAGR 0
SET 105         ; 'i'
LAGR 1
UT 0
UT 1
STOPP
```

## Running
Run code with the `run` program:

```
run program.utn
```

or with an input file
```
run program.utn [input.txt]
```
