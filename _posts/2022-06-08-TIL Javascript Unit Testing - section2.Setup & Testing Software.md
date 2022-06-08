---
layout: post
title: TIL Udemy Javascript Unit Testing - Section2. Setup & Testing Software
description: Testing Setup
summary: 자바스크립트 테스트 프레임워크의 구성과 종류에 대해서 설명한다.
tags: Udemy TIL javascript test jest vitest
minute: 1
---

## Testing Setup

**Test Runner(테스트 실행기)**

- 테스트 코드를 실행한다
- 자동으로 테스트 코드를 감지한다
- 결과를 보여준다
- e.g., Jest, Karma

**Assertion Library**

- 예상하는 결과를 정의하는데 사용한다.
- 예상하는 결과가 맞는지를 체크한다.
- 모든 종류의 예상 및 모드(sync / async)를 지원한다.
- e.g., Jest, Chai

### Jest vs Vitest

Jest는 페이스북에서 만든 Javascript Testing Framework로 현재 가장 인기가 많은 프레임 워크이다. 그러나 다음과 같은 단점이 있다.

- 다소 느린 편이다.
- commonJS를 사용하는 환경에서 사용하기 어렵다. (babel 설정을 해줘야함)

따라서 해당 강의에서는 Vitest를 사용한다. Vitest는 다음과 같은 장점이 있다.

- Jest보다 빠르다
- Jest 구문과 호환된다.
- 별도의 설치나 구성 없이 ES modules이나 commonJS를 지원한다.
- Jest와 같이 Vitest는 test runner이자 assertion library이다.
