## 문제: n진수 게임 (https://school.programmers.co.kr/learn/courses/30/lessons/17687)
```python
def solution(n, t, m, p):    
    cycle = '0'
    i = 1
    while len(cycle) < t*m:
        temp = ''
        j = i
        while j != 0:
            if j%n < 10:
                temp += str(j%n)
            else:
                temp += str(chr(j%n + 55))
            j //= n
        cycle += temp[::-1]
        i += 1
    
    return cycle[p-1:t*m:m]
```
m명의 사람이 n진수의 수를 0부터 순서대로 한 자릿수씩 부르는 게임을 할 때, p번째 순서인 사람이 외쳐야 할 숫자를 t개 구하는 문제다.  

매개변수가 많아서 설명이 좀 복잡해보이지만 실제로는 간단한 문제다.  
0부터 순서대로 충분한 수의 자연수들을 n진수로 변환하고, 이들을 string으로 바꿔 모두 이어붙이면 된다.  

n진수로 변환할 자연수를 나타내는 i와 이를 n진수로 변환하기 위한 복사값 j를 설정했다.  
j를 n으로 나눠가며 나머지를 확인하고 몫 연산을 적용하는 방식으로 n진수 변환을 구현해줬다.  
변환된 n진수는 cycle 변수에 추가하는데, cycle은 모든 사람이 불러야 할 숫자를 순서대로 나타낸 string이다.  

충분한 수의 자연수를 n진수로 변환했을 때, 즉 cycle의 전체 길이가 t\*m 이상일 때 n진수 변환을 종료한다.  
cycle의 p번째 값부터 m씩 건너뛰며 값을 읽어주면 된다.  
