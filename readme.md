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

#### Solution

```js
function hammingWeight(n: number): number {
  // by using toString method
  // const nums = n.toString(2).split("");
  // const filteredNums = nums.filter(num => num === "1");
  // return filteredNums.length;

  // by using toString in one line
  return n
    .toString(2)
    .split("")
    .filter((num) => num === "1").length;
}
```
