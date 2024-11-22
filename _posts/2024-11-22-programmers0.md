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
## ❓ 홀짝에 따라 다른 값 반환하기

양의 정수 `n`이 주어질 때, `n`이 홀수라면 `n` 이하의 홀수인 모든 양의 정수의 합을 return하고, `n`이 짝수라면 `n` 이하의 짝수인 모든 양의 정수의 제곱의 합을 return하는 `solution` 함수를 작성해 주세요. (단, 1 <=n <=100)

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
  }```

</details>

## ❓ 조건문자열
문자열에 따라 다음과 같이 두 수의 크기를 비교하려고 합니다.

두 수가 `n`과 `m`이라면
">", "=" : n >= m
"<", "=" : n <= m
">", "!" : n > m
"<", "!" : n < m
두 문자열 `ineq`와 `eq`가 주어집니다. ineq는 "<"와 ">"중 하나고, eq는 "="와 "!"중 하나입니다. 그리고 두 정수 n과 m이 주어질 때, n과 m이 ineq와 eq의 조건에 맞으면 1을 아니면 0을 return하도록 solution 함수를 완성해주세요.

<details>
  <summary>코드 보기</summary>
```java
class Solution {
    public int solution(String ineq, String eq, int n, int m) {
        boolean result= false;
        
        // 나올수있는기호: >=,<=,>,<
        if(ineq.equals(">") && eq.equals("=")){
            result=(n>=m);
        }
        else if(ineq.equals("<") && eq.equals("=")){
            result=(n<=m);
        }
        else if(ineq.equals(">") && eq.equals("!")){
            result=(n>m);
        }
        else {result=(n<m);}

        return result?1:0;
    }
}

</details>

## ❓ 코드 처리하기
문자열 code가 주어집니다.
code를 앞에서부터 읽으면서 만약 문자가 "1"이면 mode를 바꿉니다. mode에 따라 code를 읽어가면서 문자열 ret을 만들어냅니다.

mode는 0과 1이 있으며, idx를 0 부터 code의 길이 - 1 까지 1씩 키워나가면서 code[idx]의 값에 따라 다음과 같이 행동합니다.

mode가 0일 때
code[idx]가 "1"이 아니면 idx가 짝수일 때만 ret의 맨 뒤에 code[idx]를 추가합니다.
code[idx]가 "1"이면 mode를 0에서 1로 바꿉니다.
mode가 1일 때
code[idx]가 "1"이 아니면 idx가 홀수일 때만 ret의 맨 뒤에 code[idx]를 추가합니다.
code[idx]가 "1"이면 mode를 1에서 0으로 바꿉니다.
문자열 code를 통해 만들어진 문자열 ret를 return 하는 solution 함수를 완성해 주세요.

단, 시작할 때 mode는 0이며, return 하려는 ret가 만약 빈 문자열이라면 대신 "EMPTY"를 return 합니다.

<details>
  <summary>코드 보기</summary>
  
class Solution {
    public String solution(String code) {
        
        int mode=0; // 또는 1      
        String ret = "";
        
        for(int i=0; i < code.length(); i++) {
            char c = code.charAt(i);
            
            
            if(mode==0) { //mode가 0일 때
                if(c == '1'){
                    mode=1;
                }
                else if(i%2==0){
                    ret+=c;
                }
            }
            else { //mode가 1일 때
                 if(c =='1'){
                     mode=0;
                }
                else if(i%2==1) { 
                        ret+=c;
                }
            }
          
        } //for
               
        return ret.isEmpty() ? "EMPTY" : ret;
    }
}

</details>

## ❓ 등차수열의 특정한 항만 더하기

두 정수 a, d와 길이가 n인 boolean 배열 included가 주어집니다. 첫째항이 a, 공차가 d인 등차수열에서 included[i]가 i + 1항을 의미할 때, 이 등차수열의 1항부터 n항까지 included가 true인 항들만 더한 값을 return 하는 solution 함수를 작성해 주세요.

<details>
  <summary>코드 보기</summary>

class Solution {
    public int solution(int a, int d, boolean[] included) {
        int answer = 0;
        
        for(int i=0; i<included.length; i++) {
            if(included[i]) { //true 인 경우
                int currentTerm= a+i*d;
                answer+=currentTerm;
            }           
        }           
        return answer;
    }
}
</details>

## ❓ 원소들의 곱과 합

정수가 담긴 리스트 num_list가 주어질 때, 모든 원소들의 곱이 모든 원소들의 합의 제곱보다 작으면 1을 크면 0을 return하도록 solution 함수를 완성해주세요.

<details>
  <summary>코드 보기</summary>

class Solution {
    public int solution(int[] num_list) {
        int sum = 0;
        int x = 1;
        
        // 곱 < 합의 제곱 이면, 1
        // 곱 > 합의 제곱 이면, 0
        
        for(int num : num_list){
            // 합
            sum+= num;
            // 곱
            x*=num;
        }        
        if (x < sum*sum) {
            return 1;
        }
        else {
            return 0;
        }
    }
}
</details>

## ❓ 공백으로 구분하기2

단어가 공백 한 개 이상으로 구분되어 있는 문자열 my_string이 매개변수로 주어질 때, my_string에 나온 단어를 앞에서부터 순서대로 담은 문자열 배열을 return 하는 solution 함수를 작성해 주세요.
<details>
  <summary>코드 보기</summary>

class Solution {
    public String[] solution(String my_string) {        
        String[] answer = my_string.trim().split("\\s+");
        return answer;
    }
}

</details>

## ❓ 마지막 두 원소

정수 리스트 num_list가 주어질 때, 마지막 원소가 그전 원소보다 크면 마지막 원소에서 그전 원소를 뺀 값을 마지막 원소가 그전 원소보다 크지 않다면 마지막 원소를 두 배한 값을 추가하여 return하도록 solution 함수를 완성해주세요.

<details>
  <summary>코드 보기</summary>


import java.util.Arrays;

class Solution {
    public int[] solution(int[] num_list) {
        // 마지막 원소 > 그전 원소 보다 크면, 마지막 원소 - 그전 원소
        // 마지막 원소 < 그전 원소 보다 크면, 마지막 원소 2배
        
        int last = num_list[num_list.length-1]; //마지막 원소
        int belast = num_list[num_list.length-2]; //그전 원소
        int result;

        if (last > belast) {
            result=last-belast;
        }
        else {result=last*2;}
        
        int[] new_num_list = Arrays.copyOf(num_list,num_list.length+1);
        new_num_list[new_num_list.length-1]=result;
        
        return new_num_list;
    }
}
</details>
