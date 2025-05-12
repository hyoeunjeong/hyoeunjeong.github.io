# 나홀로 프로젝트_03(로또 번호 추첨기)

프로젝트 경위  :나도 로또 당첨되고 싶다.....


## Code 

```python

import random #랜덤으로 숫자 추출

print("💲💲Welcome💲💲")
print("로또 번호 랜덤 프로그램에 오신 여러분 환영합니다.😁")
print("인생 역전을 하고싶으신가요?? ")
print("🤞행운을 빕니다.🤞") 


def generate_lotto_numbers():   ##def 함수정의
     lotto_numbers = random.sample(range(1, 46), 6)  #1~45 중 6개 
     lotto_numbers.sort()  # 오름차순 번호를 정렬하기  
     ##lotto_numbers.sort(reverse=True) 내림차순 정렬하기
 
     return lotto_numbers


recommended_numbers = generate_lotto_numbers()
print("추천 번호:", recommended_numbers)


```
