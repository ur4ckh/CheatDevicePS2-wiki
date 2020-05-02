Cheat Device's engine is borrowed from ps2rd, which closely supports the code types used by CodeBreaker. This page documents each supported code type with any caveats to be aware of.

## 0: 8-bit constant write
```
0aaaaaaa 000000vv
```
Constantly writes the 8-bit value `v` to address `a`.

## 1: 16-bit constant write
```
1aaaaaaa 0000vvvv
```
Constantly writes the 16-bit value `v` to address `a`.

**NOTE**: `a` must be short-aligned (`a % 2 == 0`).

## 2: 32-bit constant write
```
2aaaaaaa vvvvvvvv
```
Constantly writes the 16-bit value `v` to address `a`.

**NOTE**: `a` must be word-aligned (`a % 4 == 0`).

## 3: Increment/Decrement
This code has multiple forms:

### 8-bit increment
```
300000vv 0aaaaaaa
```

### 8-bit decrement
```
301000vv 0aaaaaaa
```

### 16-bit increment
```
3020vvvv 0aaaaaaa
```

### 16-bit decrement
```
3030vvvv 0aaaaaaa
```

### 32-bit increment
```
30400000 0aaaaaaa
vvvvvvvv 00000000
```

### 32-bit decrement
```
30500000 0aaaaaaa
vvvvvvvv 00000000
```

Increment or decrement the current value at address `a` by value `v`.

## 4: 32-bit constant serial write
```
4aaaaaaa nnnnssss
vvvvvvvv iiiiiiii
```
Starting with address `a`, this code type will write the 32-bit value `v` to `n` addreses. In each cycle, the address is incremented by `s`*4 and the value is incremented by `i`.

## 5: Copy bytes
```
5sssssss nnnnnnnn
0ddddddd 00000000
```
Copy `n` bytes from source address `s` to destination address `d`.

## 6: Pointer write

### 8-bit write
```
6aaaaaaa 000000vv
0000nnnn    p_0
   p_1      p_2
........ ........
 p_(n-1)    p_n
```

### 16-bit write
```
6aaaaaaa 0000vvvv
0001nnnn    p_0
   p_1      p_2
........ ........
 p_(n-1)    p_n
```

### 32-bit write
```
6aaaaaaa vvvvvvvv
0002nnnn    p_0
   p_1      p_2
........ ........
 p_(n-1)    p_n
```
#### Single dereference (`n` <= 1)

Loads the 32-bit base address from address `a`, adds offset `p_0` to it, and constantly writes the value `v` to the final address.

#### Multiple dereferences (`n` > 1)

Loads the 32-bit base address from address `a`, adds offset `p_0` to it to get an initial pointer address `P_0`. Dereference `P_0` and add `p_1` to the result to get the next pointer address `P_1`. This is done `n` times until the final address `P_n` is found, at which point the value `v` is written to it.

**NOTE:** Execution of this code type will stop if a NULL pointer is encountered to prevent a crash.

## 7: Bitwise operation

### 8-bit OR
```
7aaaaaaa 000000vv
```

### 16-bit OR
```
7aaaaaaa 0010vvvv
```

### 8-bit AND
```
7aaaaaaa 002000vv
```

### 16-bit AND
```
7aaaaaaa 0030vvvv
```

### 8-bit XOR
```
7aaaaaaa 004000vv
```

### 16-bit XOR
```
7aaaaaaa 0050vvvv
```

Performs a bitwise logical operation between value `v` and the value stored at address `a`.

## 8: 8-bit / 16-bit constant serial write

**NOTE**: This code type is unique to Cheat Device.

### 8-bit write
```
8aaaaaaa nnnnssss
000000vv 000000ii
```

### 16-bit write
```
8aaaaaaa nnnnssss
1000vvvv 0000iiii
```

Starting with address `a`, this code type will write the value `v` to `n` addresses. In each cycle, the address is incremented by `s` or `s`*2 and the value is incremented by `i`.

## C: 32-bit conditional
```
Caaaaaaa vvvvvvvv
```

If the 32-bit value at address `a` is equal to value `v`, all subsequent codes will be executed.

## D: Multi-line conditional

### 16-bit test
```
Daaaaaaa nnt0vvvv
```

### 8-bit test
```
Daaaaaaa nnt1vvvv
```

Compares the value at address `a` to value `v`, and executes the next `n` code lines only if the test condition `t` is true.

|`t`|Test Condition|
|---|---|
|0|==|
|1|!=|
|2|<|
|3|>|
|4|NAND|
|5|AND|
|6|NOR|
|7|OR|


## E: Multi-line conditional (deprecated)

### 16-bit test
```
E0nnvvvv taaaaaaa
```

## 8-bit test
```
E1nnvvvv taaaaaaa
```

This code-type is equivalent to the D-type and is included for backward compatibility.