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
