# Top interview 150

This repository contains my solutions to the LeetCode "Top interview 150". I'm on a journey to test my skills, and I'm excited to share my progress with you. Explore the solutions, learn from them, and join me on this coding adventure as we explore the world of JavaScript / typescript together!

> **All the problems are solved using Typescript JS.**

[My Leetcode Profile 😊](https://leetcode.com/itsharvihere/)

[Join the Challenge 😍](https://leetcode.com/studyplan/top-interview-150/)

## Table of Contents

- [Bit manipulation](#bit-manipulation)
  - [01 Add binary](#01-add-binary)
  - [02 Reverse Bits](#02-reverse-bits)
  - [03 Number of 1 Bits](#03-number-of-1-bits)
  - [04 Single Number](#04-single-number)
  - [05 Single Number II](#05-single-number-ii)
  - [06 Bitwise AND of Numbers Range](#06-bitwise-and-of-numbers-range)
- [Math](#math)
  - [01 Palindrome Number](#01-palindrome-number)
  - [02 Plus One](#02-plus-one)
  - [03 Factorial Trailing Zeroes](#03-factorial-trailing-zeroes)
  - [04 Sqrt(x)](#04-sqrtx)
  - [05 Pow(x, n)](#05-powx-n)

## Bit manipulation

### 01 Add binary

#### [Problem Statement ↗️](https://leetcode.com/problems/add-binary/description/?envType=study-plan-v2&envId=top-interview-150)

Given two binary strings a and b, return their sum as a binary string.

#### Solution

```js
function addBinary(a: string, b: string): string {
  return (BigInt(`0b${a}`) + BigInt(`0b${b}`)).toString(2);
}
```

### 02 Reverse Bits

#### [Problem Statement ↗️](https://leetcode.com/problems/reverse-bits/?envType=study-plan-v2&envId=top-interview-150)

Reverse bits of a given 32 bits unsigned integer.

#### Solution

```js
function reverseBits(n: number): number {
  const bits = n.toString(2);
  const bitDigits = ("0".repeat(32 - bits.length) + bits).split("");
  return parseInt(bitDigits.reverse().join(""), 2);
}
```

### 03 Number of 1 Bits

#### [Problem Statement ↗️](https://leetcode.com/problems/number-of-1-bits/?envType=study-plan-v2&envId=top-interview-150)

Write a function that takes the binary representation of an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).

#### 01 Solution using toString method

```js
function hammingWeight(n: number): number {
  return n
    .toString(2)
    .split("")
    .filter((num) => num === "1").length;
}
```

#### 02 Solution using bit wise and operator

```js
function hammingWeight(n: number): number {
  let count = 0;
  while (n) {
    n = n & (n - 1);
    count++;
  }
  return count;
}
```

#### 03 Solution using bit masking and right shift operator

```js
function hammingWeight(n: number): number {
  let mask = 1;
  let count = 0;
  for (let i = 0; i < 32; i++) {
    if ((n & mask) !== 0) {
      count++;
    }
    mask = mask << 1;
  }
  return count;
}
```

### 04 Single Number

#### [Problem Statement ↗️](https://leetcode.com/problems/single-number/?envType=study-plan-v2&envId=top-interview-150)

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

#### Solution by using XOR operator

```js
function singleNumber(nums: number[]): number {
  let ans = nums[0];
  for (let i = 1; i < nums.length; i++) {
    ans = ans ^ nums[i];
  }
  return ans;
}
```

#### Solution by using Map

```js
function singleNumber(nums: number[]): number {
  let myMap = new Map();
  for (let i = 0; i < nums.length; i++) {
    if (myMap.has(nums[i])) {
      myMap.set(nums[i], myMap.get(nums[i]) + 1);
    } else {
      myMap.set(nums[i], 0);
    }
  }

  for (let item of myMap) {
    if (item[1] === 0) {
      return item[0];
    }
  }
}
```

### 05 Single Number II

#### [Problem Statement ↗️](https://leetcode.com/problems/single-number-ii/description/?envType=study-plan-v2&envId=top-interview-150)

Given an integer array nums where every element appears three times except for one, which appears exactly once. Find the single element and return it.

#### Solution by using Map

```js
function singleNumber(nums: number[]): number {
  let myMap = new Map();
  for (let i = 0; i < nums.length; i++) {
    if (myMap.has(nums[i])) {
      myMap.set(nums[i], myMap.get(nums[i]) + 1);
    } else {
      myMap.set(nums[i], 0);
    }
  }

  for (let item of myMap) {
    if (item[1] === 0) {
      return item[0];
    }
  }
}
```

### 06 Bitwise AND of Numbers Range

#### [Problem Statement ↗️](https://leetcode.com/problems/bitwise-and-of-numbers-range/?envType=study-plan-v2&envId=top-interview-150)

Given two integers left and right that represent the range [left, right], return the bitwise AND of all numbers in this range, inclusive.

#### Solution

```js
function rangeBitwiseAnd(left: number, right: number): number {
  if (left * 2 <= right) return 0;
  let output = left;
  for (let i = left + 1; i <= right; i++) {
    output = output & i;
  }
  return output;
}
```

## Math

### 01 Palindrome Number

#### [Problem Statement ↗️](https://leetcode.com/problems/palindrome-number/?envType=study-plan-v2&envId=top-interview-150)

Given an integer x, return true if x is a
palindrome, and false otherwise.

#### Solution

```js
function isPalindrome(x: number): boolean {
  const stringNumber = String(x);
  const reversedStringNumber = stringNumber.split("").reverse().join("");
  if (stringNumber === reversedStringNumber) {
    return true;
  } else {
    return false;
  }
}
```

### 02 Plus One

#### [Problem Statement ↗️](https://leetcode.com/problems/plus-one/?envType=study-plan-v2&envId=top-interview-150)

You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.

#### Solution

```js
function plusOne(digits: number[]): number[] {
  const nums = BigInt(digits.join("")) + BigInt(1);
  return String(nums)
    .split("")
    .map((num) => Number(num));
}
```

### 03 Factorial Trailing Zeroes

#### [Problem Statement ↗️](https://leetcode.com/problems/factorial-trailing-zeroes/?envType=study-plan-v2&envId=top-interview-150)

Given an integer n, return the number of trailing zeroes in n!.

#### Solution

```js
function trailingZeroes(n: number): number {
  let factorial = BigInt(1);
  if (n === 0) {
    return 0;
  }
  for (let i = n; i >= 1; i--) {
    factorial *= BigInt(i);
  }

  const factorialString = String(factorial);
  let count = 0;
  for (let i = factorialString.length - 1; i >= 0; i--) {
    if (factorialString[i] === "0") {
      count++;
    } else {
      break;
    }
  }
  return count;
}
```

### 04 Sqrt(x)

#### [Problem Statement ↗️](https://leetcode.com/problems/sqrtx/?envType=study-plan-v2&envId=top-interview-150)

Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.

#### Solution

```js
function mySqrt(x: number): number {
  for (let i = 1; i <= x / 2 + 1; i++) {
    if (i * i === x) {
      return i;
    } else if (i * i > x) {
      return i - 1;
    }
  }
}
```

### 05 Pow(x, n)

#### [Problem Statement ↗️](https://leetcode.com/problems/powx-n/?envType=study-plan-v2&envId=top-interview-150)

Implement pow(x, n), which calculates x raised to the power n (i.e., x raised power n).

#### Solution using double astricks

```js
function myPow(x: number, n: number): number {
  return x ** n;
}
```

#### Solution using Math method

```js
function myPow(x: number, n: number): number {
  return Math.pow(x, n);
}
```
