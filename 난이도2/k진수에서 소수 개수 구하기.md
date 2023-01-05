## 문제: k진수에서 소수 개수 구하기 (https://school.programmers.co.kr/learn/courses/30/lessons/92335)  
  
```python
def solution(n, k):
    answer = 0
    reversed_n = ''
    while n:
        reversed_n += str(n%k)
        n = (n-n%k)//k
    
    temp = ''
    for i in reversed_n[::-1]:
        if i == '0':
            if temp:
                if isPrime(int(temp)):
                    answer += 1
                temp = ''
        else:
            temp += i
    if temp and isPrime(int(temp)):
        answer += 1
    return answer

def isPrime(n):
    if n == 1:
        return False
    for i in range(2,int(n**0.5)+1):
        if n%i == 0:
            return False
    return True
   ```

주어진 10진수를 k진수로 변환한 후 0 사이에 위치한 소수들이 몇 개인지 구하는 문제이다.  
k진수 변환, 소수 확인의 2가지 기능을 구현하고, 조건에 맞게 적용하면 된다.  

temp에 검사할 문자열을 저장하고 isPrime으로 소수를 판별하도록 구현했는데, 0을 기준으로 split하면 코드가 더 간결했을 것 같다.  
