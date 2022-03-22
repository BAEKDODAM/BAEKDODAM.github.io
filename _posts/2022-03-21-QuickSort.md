---
layout: post
title:  "Quick Sort"
date:  "2022-03-21 18:36:06"
categories: jekyll update
---

# Quick Sort
* 피봇(pivot)이라 일컷는 배열의 원소(숫자)를 기준으로 피못보다 작은 숫자들은 왼편으로, 큰 숫자들은 오른편에 위치하도록 분할하고 피봇들을 그 사이에 놓는 것이다.
* 퀵 정렬은 분할된 부분 문제들에 대하여서도 위와 동일한 과정을 순환적으로 수행하여 정렬한다.
* 피봇 선정 방법
    * 랜덤하게 선정
    * 가장 왼쪽, 오른쪽, 가운데 값 중 중앙값
    * 중앙값들의 중앙값. 입력을 3등분하여 각 부분의 세 중앙값들 중의 중앙값
---


## 알고리즘
<pre>
<code>
QuickSort(A, left, right)
입력: 배열 A[left]~A[right]  
출력: 정렬된 배열 A[left]~A[right]
if (left < right) {
    피봇을 A[left] ~A[right] 중에서 선택하고, 피봇을 A[left]와 자리를 바꾼 후, 
    피봇과 배열의 각 원소를 비교하여 피봇보다 작은 숫자들은 A[left]~A[q-1]로 옮기고,
    피봇보다 큰 숫자들은 A[p+1]~A[right]로 옮기며, 피봇은 A[p]에 놓는다.
    QuickSort(A, left, p-1) // 피봇보다 작은 그룹
    QuickSort(A, p+1, right) // 피봇보다 큰 그룹
}
</code>
</pre>
---
## 예제(with python)
~~~python
A = [6,3,11,9,12,2,8,15,18,10,7,14]
B = [1,17,42,9,18,23,31,11,26]
def QuickSort(A, start, end) :
    if start >= end :
        return
    # 처음, 중간, 끝값 중 중간값을 피벗으로 설정
    middle = [A[end],A[start],A[(end+start+1)//2]]
    middle.sort()
    p = A.index(middle[1])

    A[start], A[p] = A[p], A[start]
    pivot = A[start]
    right = end
    left = start

    while left <= right:
        while right > start and A[right] >= pivot: # 오른쪽에서 피봇보다 작은 값 찾을 때까지 반복
            right -= 1
            
        while left <= end and A[left] <= pivot: # 왼쪽에서 피봇보다 큰 값 찾을 때까지 반복
            left += 1
            
        if left > right :
            A[right], A[start] = A[start], A[right] 
        else:
            A[left], A[right] = A[right], A[left] # 찾은 값 자리 바꾸기
    print(A)    
    QuickSort(A, start, right-1) # 왼쪽 퀵정렬
    QuickSort(A, right+1, end) # 오른쪽 퀵정렬
~~~

