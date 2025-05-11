# 나홀로 프로젝트02  (식사메뉴 추천프로그램 )

프로젝트 경위 :  언제나 고민하는 그것 오늘 점식은 고기 인가 떡볶인가 초밥인가 그 고민을 해결하기 위한 프로그램
## 사용된 기능

- while True: 반복문 
- if -조건문
- 자료구조 설계 - (딕셔너리)

###  다시보기
✅ 1. 딕셔너리 (Dictionary)
- key(장르)와 value(작품 목록)를 쌍으로 저장하는 자료구조입니다.

✅ 2. for 반복문
- 딕셔너리의 키(장르)들을 하나씩 꺼내서 출력.
- 리스트 출력, 추천 영화 출력 등에 사용됨.

✅ 3. input() 함수
-사용자로부터 입력을 받는 함수.문자열 형태로 받음 
- 만약 정수형 -(int) 실수형 -(float)

✅ 4. 조건문 (if, elif, else)
- 조건에 따라 다른 동작을 하도록 분기 처리.

✅ 5. 리스트 (List)
- 각 메뉴 종류별로  저장할 때 사용된 자료형.

✅ 6. while True: 반복문
- 프로그램을 사용자가 종료할 때까지 계속 실행되게 하는 무한 루프

✅ 7. break
- while 반복문에서 즉시 빠져나오고 프로그램을 종료함.

✅ 8. import random (랜덤 모듈)
- 사용법\
a = [1, 2, 3, 4, 5, 6, "good"]

a = random.choice(a)

## Code 

```python
import random
recommendationse ={"한식":["김치찌개","닭도리탕","갈치조림","갈비찜","냉면","백반"],
                   "중식":["탕수육","마라탕","마라샹궈","짬뽕","짜장면","칠리새우","양장피"],
                   "일식":["초밥","소바","라멘","오코노미야끼","우동","돈까스","야끼소바"],
                   "고기":["삼겹살","갈비","등심","항정살","갈매기살","목살","안심"],
                   "야식":["닭발","족발","오돌뼈","보쌈","떡볶이","찜닭","야채곱창"],
                   "치킨":["황금올리브","뿌링클","허니오리지널","슈프림치킨","레드콤보","핫후라이드","마늘 통닭"],
                   "피자":["고구마 피자","치즈피자","페퍼로니피자","하와이안 피자","포테이토 피자","콤비네이션 피자"],
                   "편의점":["편의점 도시락","컵라면","닭가슴살","핫바","과자","삼각김밥","샌드위치"]}

while True :
 print("🍴어서오세요 맛잘알 추천기 입니다.🍴")
 print("👉 선택 가능한 음식 종류:")
 for kind in recommendationse:
    print(f"{kind}")

 user_choice =input("🤤땡기는음식을 선택하시오🤤 ")
 if user_choice in recommendationse:
    menu = random.choice(recommendationse[user_choice]) 
    print(f"{user_choice} 중  식사메뉴는  🤤두구구두구🤤")
    print(f"{menu}")
  
 #for menu in recommendationse[user_choice]:
    
  #  print(f"👉 오늘의 추천 메뉴{menu}")

 else: 
    print("⚠️ 존재하지 않는 음식 종류입니다. 다시 입력해주세요 ")

 print("프로그램 종류를 원하시면 0 번을 계속하시기를 원한다면 1번을 누루시오")
 number = input()
 if number == "0":
    print("👋 프로그램을 종료합니다. 맛있게 드세요!")
    break
 elif number == "1" :
   print(" 🍽 다시 추천을 시작합니다!")
 else:
   print("❗ 잘못된 입력입니다❗ 계속 진행합니다")
```

#한줄평 

- 랜덤으로 하나 씩 출력 하려면  import random을 사용해야 한다.

- https://docs.python.org/ko/3.13/library/random.html# 
