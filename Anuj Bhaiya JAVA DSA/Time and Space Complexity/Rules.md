# Time Complexity Representation

This document outlines the time complexity rules for various lengths of data. The time complexities are presented based on the specified length intervals.

**Note: This is the \(10^8\) operation rule, meaning all values must go to \(10^8\) at maximum.**

## Length vs Time Complexity

### Length ≤ 10
- **Time Complexity**: \( O(n!) \), \( O(n^6) \)

### Length 16 - 18
- **Time Complexity**: \( O(2^n * n^2) \)

### Length 100
- **Time Complexity**: \( O(n^4) \)

### Length 400
- **Time Complexity**: \( O(n^3) \)

### Length 2000
- **Time Complexity**: \( O(n^2 * log n) \)

### Length 10^4
- **Time Complexity**: \( O(n^2) \)

### Length 10^6
- **Time Complexity**: \( O(n * log n) \)

### Length 10^8
- **Time Complexity**: \( O(n) \), \( O(log n) \)