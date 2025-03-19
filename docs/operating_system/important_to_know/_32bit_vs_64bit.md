# 32-bit & 64-bit Operating System

## Comparison 😈

| 32-bit      | 64-bit                          |
| ----------- | ------------------------------------ |
| A 32-bit OS has **32-bit registers**, and it **can access 2^32 unique memory addresses**. i.e., 4GB of RAM.       | A 64-bit OS has **64-bit** registers, and it **can access 2^64 unique memory addresses**. i.e., 17,179,869,184 GB of RAM.  |
| 32-bit CPU architecture can process 32 bits of data & information.      | 64-bit CPU architecture can process 64 bits of data & information. |

---

## Advantages of 64-bit OS over 32-bit OS 🤩

1. **Addressable Memory:** 32-bit CPU -> 2^32 memory addresses, 64-bit CPU -> 2^64 memory addresses.

2. **Resource usage:** Installing more RAM on a system with a 32-bit OS doesn't impact performance. However, upgrade that system with excess RAM to the 64-bit version of Windows, and you'll notice a difference.

3. **Performance:** **`All calculations take place in the registers`**. When you’re performing math in your code, operands are loaded from memory into registers. So, having larger registers allow you to perform larger calculations at the same time.

    - *32-bit processor can execute 4 bytes of data in 1 instruction cycle while 64-bit means that processor can execute 8 bytes of data in 1 instruction cycle*. (In 1 sec, there could be thousands to **billions of instruction cycles** depending upon a processor design, hence, **`64-bit can process much more data in 1 sec than 32-bit`**.)

4. **Compatibility:** 64-bit CPU can run both 32-bit and 64-bit OS. While 32-bit CPU can only
run 32-bit OS. (All the starting bits will be 0 in 64-bit CPU while working with 32-bit OS.)

5. **Better Graphics performance:** 8-bytes graphics calculations make graphics-intensive apps
run faster.