---
layout: post
title: TIL Udemy Javascript Unit Testing - Section1. Getting Started
description: What is Testing
summary: Unit, Integration, E2E 테스트 정의 및 쓰는 이유
tags: Udemy TIL javascript test
minute: 1
---

## What is Testing

> 의도한대로 작동 되는지 증명하는 것

**Manual Testing**

- 지루하고 번거로움
- 오류가 발생하기 쉬움
- 종종 불완전함(모든 시나리오가 적용되는 것이 아님)

**Automated Testing**

- 초기 테스트 코드를 작성하는 것 외엔 따로 신경쓸 것이 없음
- 예측 가능하고 일관성 있음
- 높은/완전한 코드 및 시나리오 커버리지 달성 가능함

## What Are Unit Tests?

- 앱의 구성 요소
- eg., a function, a class, a component
  - 보통은 함수를 unit이라 본다
- App = 모든 unit의 조합
- 모든 unit을 테스트한 경우 전체적인 앱이 작동되어야 한다.
  - Integration 테스트로 백업한다.
- 버그를 방지하기 위해 모든 unit에 대해 항상 변경된 사항들을 테스트한다.

## Why Unit Testing?

- 끝없는 수동 테스트 방지
- 코드 및 시나리오의 거의 100%를 커버할 수 있다.
- 코드가 변경되면 거의 즉시 모든 시나리오들이 테스트된다
- 메인 코드가 깨끗하고 좋은 방식으로 작성되면 테스트가 더 쉬워지게 때문에 더 나은 코드 작성할 수 있다.

## Unit, Integration & End-to-End (E2E) Testing 비교

**Unit Testing**

- 앱의 개별 구성 요소 테스트
- 모든 unit이 독립적으로 테스트됨
- 만약 모든 unit들이 작동한다면, 전체 앱이 잘 작동하는 것이다.

**Integration Testing**

- units의 조합을 테스트
- unit들이 함께 작동하는지 확인한다
- 모든 unit 테스트가 독립적으로 잘 작동하더라도 통합테스트는 실패할 수 있다.

**End-to-End(E2E) Testing**

- 전체 흐름 및 애플리케이션 기능을 테스트
  - 애플리케이션이 제공할 수 있는 특정 사용자 행동이나 특정 API 인터페이스에 초점을 맞추고 전체 흐름, 전체 애플리케이션 기능을 테스트한다.
- 실제 사용자가 수행할 작업을 테스트
- 예) 이미지 업로드 API [EndPoint](https://blog.naver.com/PostView.naver?blogId=ghdalswl77&logNo=222401162545&parentCategoryNo=&categoryNo=90&viewDate=&isShowPopularPosts=true&from=search)를 만드는 경우, 들어오는 요청에서 이미지를 추출한 다음 파일 시스템에 저장하는 등의 전체 이미지 업로드 워크플로우를 테스트할 수 있다.

  - Unit Testing을 사용하면 흐름을 구성하는 개별적인 부분을 테스트할 수 있다
  - 통합 테스트를 통해 이러한 Unit의 조합을 테스트할 수 있다
  - E2E테스트로 전체 흐름을 테스트할 수 있습니다. 실제 사용자 또는 프로그램과 상호 작용하는 실제 작업을 테스트한다.

  **모든 종류의 테스트를 결합해서 사용해야 하는 이유**

  - **Unit Testing**
    - 파손된 변경 사항 및 오류를 신속하게 찾아내지만 실제 사용자 행동 흐름 및 개입을 무시한다.
  - **Integration Testing**
    - 정확한 오류의 근원지를 찾는 것이 어려울 수 있다.
  - **End-to-End(E2E) Testing**
    - 가능한 모든 행동을 커버해서 테스트 하는 것이 어려울 수 있다.

## Test-Driven Development (TDD)

테스트를 작성하는 체계 / 철학. 다음의 방식으로 테스트를 작성하는 체계 / 철학이다.

> 1. 실패하는 테스트를 작성한다.
> 2. 테스트를 성공시키기 위한 코드를 구현한다.
> 3. 코드를 리팩토링한다.
> 4. 1번 과정을 다시 수행한다.

이번 강의는 TDD으로 하진 않는다. 테스트의 기초에 대해서 알아본다.
