---
title: Reduce
description: What it is and how to use the reduce method
author: Mateusz Witomski | Orion
date: 2023-12-03 17:08
type: programmingNote
tags:
  - programming
  - basics
  - typescript
enableToc: true
openToc: true
---
# 🌀 Reduce

## Description

> [!quote]+ Array.prototype.reduce()
> The **`reduce()`** method of [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) instances executes a user-supplied **"reducer" callback function** on each element of the array, in order, passing in the return value from the calculation on the preceding element. The final result of running the reducer across all elements of the array is a single value. 
> 
> **The first time** that the callback is run there is no **"return value of the previous calculation"**. 
> If supplied, an initial value may be used in its place. 
> Otherwise the array element at **index 0** is used as the initial value and iteration starts from the next element (index 1 instead of index 0).
> 
> Reference: **(2)**
## Parameters

- `callbackfn` A function to **execute for each element in the array**. Its return value becomes the value of the `accumulator` parameter on the next invocation of `callbackFn`.
  The function is called with the following arguments:
    - `accumulator`
      The value resulting from the previous call to `callbackFn`. On the first call, its value is `initialValue` if the latter is specified; otherwise its value is `array[0]`.
    - `currentValue` 
      The value of the current element. On the first call, its value is `array[0]` if `initialValue` is specified; otherwise its value is `array[1]`.
    - `currentIndex`: 
      The index position of `currentValue` in the array. On the first call, its value is `0` if `initialValue` is specified, otherwise `1`.
    - `array`: 
      The array `reduce` was called upon.
- `initialValue` is an optional initial value for the accumulator. If provided, the `reduce` function starts with this value; otherwise, it starts with the first element of the array.

Reference: **(2), (3)**
## Examples

Examples below based on the video **(4)**;
### Sum

```typescript
const orders = [31.54, 19.99, 4.55];

order.reduce((total, amount) => total + amount); // Result: 56.08
```

### Average

```typescript
const orders = [31.54, 19.99, 4.55];

order.reduce((total, amount, index, array) => {
	total += amount;
	if(index === array.length -1 ) return total/array.length;
	return total;
}); // Result: 18.6933333333333
```

### Find an element from the array that meets the condition 

```typescript
// Define a type named MapaCzasoprzestrzenna representing a function
// that takes four numbers (x, y, z, czas) and returns a number.
export type MapaCzasoprzestrzenna = (
  x: number,
  y: number,
  z: number,
  czas: number
) => number;

//? Def: 'Reduce' - is used to iterate through the 'lokalizacje' array
//? and compare the results of the MapaCzasoprzestrzenna function for each element
//* Note: That this assumes the array is not empty, and it initializes with the first element.
const result = lokalizacje.reduce((maxLocation, currentLocation) => {
  // We need to asume that mapa it is type defined like: 
  // const mapa: MapaCzasoprzestrzenna = (x, y, z, czas) => x + y + z + czas;
  
  const maxLocationSum = mapa(
    maxLocation.x,
    maxLocation.y,
    maxLocation.z,
    maxLocation.czas
  );

  const currentLocationSum = mapa(
    currentLocation.x,
    currentLocation.y,
    currentLocation.z,
    currentLocation.czas
  );

    return currentLocationSum > maxLocationSum ? currentLocation : maxLocation;
}, lokalizacje[0]); // Initialize with the first element
```

## References
1. [Use .reduce() in typescript](https://sylhare.github.io/2022/03/08/Reduce-in-typescript.html),
2. [Array.prototype.reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce),
3. Chat GPT 3.5,
4. [Metoda Array.reduce() w Praktyce - JavaScript by Overment](https://www.youtube.com/watch?v=L5hBo9J_HlU)