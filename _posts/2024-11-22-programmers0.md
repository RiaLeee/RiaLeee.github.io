---
title: Programmers_Level_0_Review
date: 2024-11-22 +09:00
categories: [Programmers, Basic]
tags: 
  - Programmers
  - 프로그래머스
  - java
  - python
  - 코딩테스트
excerpt: "프로그래머스 기초문제 0단계"
---
<!--more-->
# ❓ 홀짝에 따라 다른 값 반환하기

양의 정수 `n`이 주어질 때, `n`이 홀수라면 `n` 이하의 홀수인 모든 양의 정수의 합을 return하고, `n`이 짝수라면 `n` 이하의 짝수인 모든 양의 정수의 제곱의 합을 return하는 `solution` 함수를 작성해 주세요. (단, 1 <=n <=100)

### 문제 설명

- `n`이 홀수일 때: `n` 이하의 홀수들의 합을 구합니다.
- `n`이 짝수일 때: `n` 이하의 짝수들의 제곱의 합을 구합니다.

<details>
  <summary>코드 보기</summary>

 ```java
  class Solution {
      public int solution(int n) {
          int answer = 0;
          
          if (n % 2 == 1) {  // n이 홀수일 때
              for (int i = 1; i <= n; i += 2) {
                  answer += i;
              }
          } else {  // n이 짝수일 때
              for (int i = 2; i <= n; i += 2) {
                  answer += i * i;
              }
          }
          
          return answer;
      }
  }
</details> ```
