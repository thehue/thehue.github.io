---
layout: post
title: TIL Udemy Javascript Unit Testing - Section3. Testing Basics
description: Testing Basics
summary: 테스트 기본 원리에 대해서 공부
tags: Udemy TIL javascript test jest vitest
minute: 1
---

## Basic Test File & Project Setup

```jsx
import { test } from 'vitest';
```

를 생략하고 싶다면 package.json scripts 속성에 다음과 같이 `—globals`를 추가한다.

## The AAA Pattern - Arrange, Act, Assert

- Arrange - 테스트 환경 및 값을 정의
- Act - 테스트할 실제 코드, 함수를 실행
- Assert - 생성된 값과 결과를 평가하고 기대값과 결과를 비교

```jsx
// math.js
export function add(numbers) {
  let sum = 0;

  for (const number of numbers) {
    sum += number;
  }
  return sum;
}
```

```jsx
// math.test.js
import { expect, it } from 'vitest';

import { add } from './math';

it('should summarize all number values in an array', () => {
  // Arrange
  const numbers = [1, 2];

  // Act
  const result = add(numbers);

  // Assert
  const expectedResult = numbers.reduce(
    (previousValue, currentValue) => previousValue + currentValue,
    0,
  );
  expect(result).toBe(expectedResult);
});
```

## Defining Behaviors & Fixing Errors In Your Code

> 지금 당장 어떤 방식으로 작동 하더라도, 다른 개발자들이 미래에 해당 함수의 코드를 수정한다면 더 이상 예전처럼 작동하지 않을 수도 있기 때문에 가능한 많은 테스트와 기댓값을 정의하는 것이 중요하다.

여러가지 상황에 대한 테스트 코드를 작성한다.

```jsx
// math.js
it('should yield NaN if a least one invalid number is provided', () => {
  const inputs = ['invalid', 1];

  const result = add(inputs);

  expect(result).toBeNaN();
});

it('should yield a correct sum if an array of numeric string values is provided', () => {
  const numbers = ['1', '2'];

  const result = add(numbers);

  const expectedResult = numbers.reduce(
    (previousValue, currentValue) => +previousValue + +currentValue,
    0,
  );
  expect(result).toBe(expectedResult);
});
```

![failed test results](https://user-images.githubusercontent.com/45552388/176831701-d5350037-3c0e-4240-8ca4-d49415a95783.png)

테스트 코드를 통과시키기 위해서 `add` 함수를 다음과 같이 수정한다.

```jsx
export function add(numbers) {
  let sum = 0;

  for (const number of numbers) {
    sum += +number;
  }
  return sum;
}
```

## Error 테스트 하기

```jsx
it('should throw an error if no value is passed in to the function', () => {
  const resultFn = () => {
    add();
  };

  expect(resultFn).toThrow();
  expect(resultFn).toThrow(/numbers is not iterable/);
});
```

## Tests With Multiple Assertions (Multiple Expectations)

```jsx
export function transformToNumber(value) {
  return +value;
}
```

Number 타입으로 변환시켜주는 함수 **transformToNumber**에 대한 테스트 코드를 다음과 같이 작성할 수 있다.

```jsx
import { it, expect } from 'vitest';

it('should transform a string number to a number of type number', () => {
  const input = '1';

  const result = transformToNumber(input);

  expect(result).toBeTypeOf('number');
});

it('should yield NaN for non-transformable values', () => {
  const input = 'invalid';

  const result = transformToNumber(input);

  expect(result).toBeNaN();
});
```

하지만 이 코드는 함정이 있다. 만약 transformToNumber 함수가 잘못 구현 되어서 항상 NaN을 return하는 함수라면 테스트 결과가 어떻게 될까?

```jsx
export function transformToNumber(value) {
  return NaN;
}
```

![transformToNumber function test](https://user-images.githubusercontent.com/45552388/176831957-3808e1b4-882a-4740-b0c1-61bf5f6a0338.png)

NaN의 type은 Number이기 때문에 첫 번째 테스트를 통과하게 된다.

따라서 실제값을 예측하는 테스트코드를 추가하여 모순을 피한다.

non-transformable value를 넣으면 NaN값을 return하는 테스트 케이스에는 다른 케이스도 추가하여 함수의 안정성을 높인다.

```jsx
it('should transform a string number to a number of type number', () => {
  const input = '1';

  const result = transformToNumber(input);

  **expect(result).toBe(+input);**
});

it('should yield NaN for non-transformable values', () => {
  const input = 'invalid';
  const input2 = {};

  const result = transformToNumber(input);
  const result2 = transformToNumber(input2);

  expect(result).toBeNaN();
  expect(result2).toBeNaN();
});
```
