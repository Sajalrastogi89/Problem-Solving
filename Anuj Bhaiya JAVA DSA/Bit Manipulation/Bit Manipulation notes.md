# Anuj Bhaiya Java DSA Course: Bit Manipulation Notes

## Introduction to Binary Number System
- **Binary Representation**: Uses two digits, 0 and 1, to represent numbers.
- **Conversions**:
  - **Decimal to Binary**: Divide by 2 and record remainders.
  - **Binary to Decimal**: Sum each bit multiplied by 2 raised to its position power.

## Addition
- **Formula**: 
2*n + remainder => write remainder and make n as carry

## Substraction
- **Formula**: 
when you have to do substraction then convert second number to to its 2s compliment and then add with first number
2*n + remainder => write remainder and make n as carry

## Bitwise Operators
### AND (&)
- **Usage**: Sets each bit to 1 if both corresponding bits are 1.
- **Example**:
  ```java
  int a = 5; // 0101 in binary
  int b = 3; // 0011 in binary
  int result = a & b; // 0001 in binary, which is 1 
  ```

### OR (|)
- **Usage**: Sets each bit to 1 if at least one of the corresponding bits is 1.
- **Example**:
```java
Copy code
int a = 5; // 0101 in binary
int b = 3; // 0011 in binary
int result = a | b; // 0111 in binary, which is 7
```

### XOR (^)
- **Usage**: Sets each bit to 1 if only one of the corresponding bits is 1.
- **Example**:
```java
Copy code
int a = 5; // 0101 in binary
int b = 3; // 0011 in binary
int result = a ^ b; // 0110 in binary, which is 6
```

### NOT (~)
- **Usage**: Inverts all the bits.
- **Example**:
```java
Copy code
int a = 5; // 0101 in binary
int result = ~a; // 1010 in binary (in a 32-bit system, this is -6 due to two's complement)
```

### Left Shift (<<)
- **Usage**: Shifts bits to the left, adding zeros on the right. Each shift left multiplies the number by 2.
- **Example**:
```java
Copy code
int a = 5; // 0101 in binary
int result = a << 1; // 1010 in binary, which is 10 (5 * 2)
```

### Right Shift (>>)
- **Usage**: Shifts bits to the right, preserving the sign bit. Each shift right divides the number by 2.
- **Example**:
```java
Copy code
int a = 5; // 0101 in binary
int result = a >> 1; // 0010 in binary, which is 2 (5 / 2)
```

### For checking even and odd
- Modulo is expensive operation so we use n&1==0 => even else odd

## Common Bit Manipulation Techniques
### Setting a Bit
- **Formula**: number | (1 << bitPosition)
- **Example**:
```java
Copy code
int number = 5; // 0101 in binary
int bitPosition = 1;
int result = number | (1 << bitPosition); // Sets the 1st bit: 0111 in binary, which is 7
```

### Clearing a Bit
- **Formula**: number & ~(1 << bitPosition)
- **Example**:
```java
Copy code
int number = 5; // 0101 in binary
int bitPosition = 0;
int result = number & ~(1 << bitPosition); // Clears the 0th bit: 0100 in binary, which is 4
```

### Toggling a Bit
- **Formula**: number ^ (1 << bitPosition)
- **Example**:
```java
Copy code
int number = 5; // 0101 in binary
int bitPosition = 1;
int result = number ^ (1 << bitPosition); // Toggles the 1st bit: 0111 in binary, which is 7
```

## Checking a Bit
- **Formula**: (number & (1 << bitPosition)) != 0
- **Example**:
```java
Copy code
int number = 5; // 0101 in binary
int bitPosition = 2;
boolean isBitSet = (number & (1 << bitPosition)) != 0; // Checks if the 2nd bit is set: false
```

## Advanced Bit Manipulation
- **XOR Problems**
- **Finding the single non-duplicate element**:
```java
Copy code
int findSingle(int[] arr) {
    int result = 0;
    for (int num : arr) {
        result ^= num;
    }
    return result;
}
```

## Swapping two numbers without a temporary variable:

```java
Copy code
void swap(int x, int y) {
    x = x ^ y;
    y = x ^ y;
    x = x ^ y;
}
```

## Counting Set Bits
- **Counting the number of 1s in a binary number**:
```java
Copy code
int countOnes(int num) {
    int count = 0;
    while (num != 0) {
        count += (num & 1);
        num >>= 1;
    }
    return count;
} 
```

## Bit Masking
- **Creating masks for specific tasks**:
```java
Copy code
// Example: extracting the k-th bit
int extractBit(int number, int k) {
    return (number & (1 << k)) != 0 ? 1 : 0;
} 
```

## Practice Problems
- **Single Non-Duplicate Element**:
```java
Copy code
int findSingle(int[] arr) {
    int result = 0;
    for (int num : arr) {
        result ^= num;
    }
    return result;
}
```

- **Counting the number of 1s**:
```java
Copy code
int countOnes(int num) {
    int count = 0;
    while (num != 0) {
        count += (num & 1);
        num >>= 1;
    }
    return count;
}
```

### Important Points
- n^n=0
- n^0=n