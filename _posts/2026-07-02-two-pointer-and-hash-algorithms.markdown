---
layout: post
title:  "투 포인터(Two Pointer)와 해시(Hash) 알고리즘 정리"
date:   2026-07-02 17:47:00 +0900
categories: algorithm
---

안녕하세요! 오늘은 알고리즘 문제 해결에서 자주 사용되는 두 가지 핵심 알고리즘/자료구조 기법인 **투 포인터(Two Pointer)**와 **해시(Hash)**에 대해 알아보겠습니다.

---

## 1. 투 포인터 (Two Pointer) 알고리즘

### 개념
**투 포인터**는 리스트나 배열에서 **두 개의 포인터(위치를 가리키는 변수)**를 사용하여 대상을 탐색하는 방법입니다. 보통 브루트 포스(완전 탐색) 방식으로 해결하면 $O(N^2)$ 이상의 시간이 걸리는 문제를, 두 포인터의 위치 조작을 통해 **$O(N)$**으로 단축시킬 수 있습니다.

### 대표적인 접근 방식
1. **양끝에서 시작하는 포인터**: 배열이 정렬되어 있을 때, 하나는 맨 앞(`left`), 다른 하나는 맨 뒤(`right`)에서 출발하여 조건에 따라 두 포인터를 좁혀 나가는 방식입니다. (예: 두 수의 합 찾기)
2. **같은 방향으로 진행하는 포인터**: 주로 슬라이딩 윈도우(Sliding Window)나 부분 배열의 합을 구할 때 사용됩니다. 두 포인터가 모두 시작 지점에서 출발하여 진행합니다.

### 예제: 정렬된 배열에서 합이 `target`인 두 수 찾기 (Python)

```python
def find_two_sum(arr, target):
    left = 0
    right = len(arr) - 1
    
    while left < right:
        current_sum = arr[left] + arr[right]
        if current_sum == target:
            return (arr[left], arr[right])
        elif current_sum < target:
            left += 1  # 합이 작으므로 더 큰 값을 더하기 위해 left 증가
        else:
            right -= 1  # 합이 크므로 더 작은 값을 더하기 위해 right 감소
            
    return None

# 테스트
numbers = [1, 3, 5, 8, 11, 15]
target_val = 13
print(find_two_sum(numbers, target_val))  # 출력: (3, 10)
```

---

## 2. 해시 (Hash) 알고리즘 및 해시 테이블

### 개념
**해시**는 키(Key)를 해시 함수(Hash Function)에 입력하여 고유한 인덱(Hash Value)로 매핑하고, 이를 사용해 데이터(Value)를 저장하고 검색하는 방법입니다. 
데이터의 양에 관계없이 평균적으로 **$O(1)$**이라는 매우 빠른 시간 복잡도로 데이터를 조회, 삽입, 삭제할 수 있어 탐색이 중요한 문제에서 강력한 위력을 발휘합니다.

### 특징 및 활용
- **빠른 데이터 탐색**: 특정 값이 존재하는지 여부를 확인하거나 개수를 세는 문제에 적합합니다.
- **해시 충돌(Collision)**: 다른 키가 동일한 해시 값을 갖게 되는 현상으로, 체이닝(Chaining)이나 개방 주소법(Open Addressing) 등을 통해 해결합니다.
- Python의 `dict`와 `set`이 대표적인 해시 테이블 기반 자료구조입니다.

### 예제: 배열에서 등장하는 요소들의 빈도수 계산하기 (Python)

```python
def count_frequencies(arr):
    hash_map = {}
    for item in arr:
        if item in hash_map:
            hash_map[item] += 1
        else:
            hash_map[item] = 1
    return hash_map

# 테스트
fruits = ["apple", "banana", "apple", "orange", "banana", "apple"]
print(count_frequencies(fruits))
# 출력: {'apple': 3, 'banana': 2, 'orange': 1}
```

---

## 요약

- **투 포인터**는 배열의 인덱스를 가리키는 두 개의 포인터를 똑똑하게 움직여 탐색 범위나 조건을 조절하는 기법입니다. (주로 정렬 상태나 부분 연속 구간에 사용)
- **해시**는 키-값 형태로 데이터를 바로 연결하여 원하는 데이터를 즉시 찾아낼 수 있는 강력한 자료구조 기법입니다.
