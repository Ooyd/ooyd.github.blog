---
layout: post
title:  코딩테스트 기록 6일차
date: '2024-04-05 03:00:00 +0900'
description: 'CodingTest'
categories: [til, algorithm]
tags: [til,codingtest,algorithm]

---
# 코딩테스트 기록 6일차

## 1. 1399번: ATM (메모리: 14548 KB, 시간: 144 ms)
[Problem Link](https://www.acmicpc.net/problem/11399) <br>
[Solved Link](https://github.com/Ooyd/algorithm-and-data-structure/tree/main/%EB%B0%B1%EC%A4%80/Silver/11399.%E2%80%85ATM)

### 문제 정리
 - ATM에서 돈을 인출하는데 걸린 시간의 합의 최솟값을 구하라.
  
### 개념 및 접근법
 - 오름차순으로 정렬하여 최소값부터 계산

### 추가 정리
- 처음에는 우선순위 큐를 사용한다 생각했는데, Array sort를 써도 된다라고 생각이들고, 같은 기능인데 어떤 상황일떄 쓰는게 유리할지 정리해보았다.
- Array 장점 :
  - 전체 데이터를 한 번에 메모리에 로딩, `Arrays.sort()`같은 효율적인 정렬 알고리즘을 사용해 빠르게 정렬가능.(Tim sort알고리즘)
  - 즉 데이터가 정적이고, 한번에 정렬을 해야 한다면 Array가 유리하다.
 - Priority Queue :
    - 삽입 및 삭제 연산이 자주 발생하는 동적인 데이터셋에 유용, 왜냐하면 각 삽입 및 삭제, 즉 데이터 변동이 있을때마다 내부적으로 정렬을 유지하기에 자원을 더 잡아먹음.
    - 즉 데이터가 동적이고, 삽입 및 삭제가 빈번하게 발생하는 상황일떄 Priority Queue가 유리하다.
<br>

## 2. 2805번: 나무 자르기 (메모리: 134968 KB, 시간: 2508 ms)
[Problem Link](https://www.acmicpc.net/problem/2075) <br>
[Solved Link](https://github.com/Ooyd/algorithm-and-data-structure/tree/main/%EB%B0%B1%EC%A4%80/Silver/2805.%E2%80%85%EB%82%98%EB%AC%B4%E2%80%85%EC%9E%90%EB%A5%B4%EA%B8%B0)

### 문제 정리
 - 상근이는 M미터의 나무가 필요하다. 나무를 집에 가져가기 위해 절단기에 설정할 수 있는 높이의 최대값을 찾아라.
### 개념 및 접근법
- 정적 데이터들을 정렬하여 내림차순으로 정렬한다.
- M미터의 나무가 필요하고 임의의 높이를가진 N개의 나무들이 있다.
- 내가 M미터의 나무를 가져갈 수 있는 절단기의 높이중 가장 최대값을 찾아라.

### 풀이 결과
 -  메모리 134968 ,시간 2508

### 추가 정리
- 내림차순 정렬시 Collections.reverseOrder()사용
- 내림차순은 byte,int,long 같은 Primitive Type 배열에는 적용이 불가능
- Integer,String같은 Wrapper class에 사용
- Collections.reverseOrder()는 Comparable Interface를 구현한 클래스의 객체만 매개변수로 받는다.
참조자료 : https://gguraeit.tistory.com/3<br>

하.. 정렬문제만 계속 보다보니 그냥 무조건 정렬로만 풀어야된다라고 생각이 박혀있었던거같다..
다른 글들을 참조하니 이글은 이진탐색으로 풀고있더라..

 ### 최종 정리
이 문제는 이진 탐색을 통해서 가능한 절단기 높이의 범위를 좁혀 나가 찾아나간다.<br>
  N과 M의 범위가 1<= N <= 1,000,000, 1<= M <= 2,000,000,000 로 말도안되게 높다..<br>
 이러면 log가 섞여있는 알고리즘(빠른 정렬 알고리즘, 이진탐색 등)을 사용해야함

 최소높이와 최대높이의 중간을 계산하고, 중간점을 절단기 높이로 설정후, 얻을 수 있는 나무의 양을 계산.<br>
  절단된 나무의 양이 M이상이면 조건만족.<br>
조건 만족 -> 최소높이를  중간 +1로 해서 탐색범위 좁힘<br>
 조건 불만족 -> 최대높이를 중간 - 1 해서 탐색범위 좁힘.

<br>

## 3. 18870번: 좌표 압축 (메모리: 269564 KB, 시간: 2024 ms)
[Problem Link](https://www.acmicpc.net/problem/18870) <br>
[Solved Link]()

### 문제 정리
 - 수직선 위에 N개의 좌표가 있다.
 - 문제 이해가 어려운데.. 입 출력을 분석해보니 배열의 값들보다 작은값들을 출력하면 되는거같다.
### 개념 및 접근법
  - Hash Map 접근 (시간초과..였으나 도움을 받아 해결!!)
    - Key X의 value값, y의 출력count값 저장
    - 임시로 사용할 정렬된 배열을 만들어서 비교할 수 있는 배열 생성
    - 비교한 알고리즘에서 나온 값들을 hashMap의 key와 비교해서 value에 카운트값 대입
    - value값 출력

### 후기
  해당 문제를 처음 풀때 시간초과가 나타났었다.<br>
 이유를 찾다 다른분 코드를 보고 알게되었는데,이 분은 나랑 로직이 거의 유사하다.<br>
 문제를 접근하는방식이 나와 비슷한데,
 다만 다른점이 출력을 배열에 값을 담는게아닌 bfw를 사용하신거였다.<br>
 나같은경우 배열로 계속 작업을하다보니 결과값도 자연스레 배열을 사용하게되었는데.. 컴퓨터적인 사고로는 효율적이지 않아, 다시생각하게 되는 부분이다. <br>
 코딩테스트같은 한정된 자원에서 문제를 해결하는거는 쓸데없는 로직은 지양해야 된다 느끼게되었음..<br>
 결국에는 괜히 결과값을 담을 배열을 생성해서 for문 2번돌리고 O(2N)을 잡아먹게된게 문제였지않을까..
 
<br>

## 4. 3079번: 입국심사 (메모리: 33028 KB, 시간: 540 ms)
[Problem Link](https://www.acmicpc.net/problem/3079) <br>
[Solved Link](https://github.com/Ooyd/algorithm-and-data-structure/tree/main/%EB%B0%B1%EC%A4%80/Gold/3079.%E2%80%85%EC%9E%85%EA%B5%AD%EC%8B%AC%EC%82%AC)

### 문제 정리
 - M명이 N개의 심사대에서 심사를 받는다, 이때 각 심사대마다 소요되는 시간이 다른데, 해당시간들을 고려하여 심사를 받는데 걸리는 시간의 최솟값을 출력하라.
  
### 개념 및 접근법
 - 1 ≤ N ≤ 100,000, 1 ≤ M ≤ 1,000,000,000 (int 사용)(계산시 long 고려) ->탐색범위가 큼
 - 이분탐색을 사용한다.(주어진 범위가 매우 크기떄문.)
 - 기준은 심사시간이며 정렬해야한다.

### 회고
  중간에 계속 오버플로우(백준으로는 틀렸습니다)가 나타났는데, 다른분이 도움을 주셨다.<br>
이진 탐색중 필요없는 반복문을 제거하기위한 조건문을 추가해야한다는 것이었다.<br>
심사 중 count가 M을 초과할때는 계산을 할 필요가 없기에 해당부분을 로직에 녹여줬어야했다.<br>
해당 얘기를 듣기전까지는 로직 틀린게 없다 생각을 하는데 왜 안되지 라고 무작정 내 코드 맞다만 생각했었는데, 결국 내 로직의 문제였으니 조금 반성하게 되었다.

