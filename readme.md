# 2018/12/17에 배운 내용

## 파이썬 기초

### 카카오톡 챗봇 이용하기

- 카카오톡 챗봇 친구 추가하기
  - @sspy-003 검색하기
  - 친구 추가하기
    - 다른 반과 섞이지 않도록 주의
  - 안녕 메세지 보내서 인증번호 받기
  - 인증번호 받아서 채팅창에 입력하기
  - 인증 완료



![고양이](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTopcG9aTZvFE1qaT02DsoYj4Ch2zabw7uAL6hvNG2HA9oDCH7x)



1. '미세먼지'를 입력하여 미세먼지를 확인할 수 있다.
   1. 미세먼지 농도에 따른 등급을 확인할 수 있도록 수정하였음.
2. '날씨'의 경우 위치기반 날씨를 확인할 수 있다.
3. '점심메뉴'를 통해 랜덤하게 점심 장소를 출력받을 수 있다.
   1. 딕셔너리를 활용하여 해당 장소의 특정 메뉴를 추천받을 수 있다.
4. '로또'를 통해 금주의 로또 번호를 확인할 수 있도록 추가하였다.



- 수정한 미세먼지 등급 코드

***미세먼지.py***

```python
...

print('오늘의 미세먼지 단계는', end=' ')

if(dust > 150):
  print('매우 나쁨', end=' ')
elif(dust > 60):
  print('나쁨', end=' ')
elif(dust > 30):
  print('보통', end=' ')
else:
  print('좋음', end=' ')

print('입니다.') 
```



- **로또번호** 확인 코드

***로또. py***

```python
import requests
from bs4 import BeautifulSoup

url = 'http://www.lotto.co.kr/'
response = requests.get(url).text
soup = BeautifulSoup(response, 'html.parser')
test = soup.find('div', {'class' : 'current_result'})
txt = str(test)
txt_0 = txt
#print(txt)

print('이번 주 당첨 번호는', end=' ')
for i in range(6):
  s1 = txt[txt.find("on/")+3:txt.find(".png")]
  print(s1, end=', ')
  txt = txt[txt.find(".png")+4:]
print('입니다.')

s2 = txt_0[txt_0.find("bonus/")+6:]
s2 = s2[:s2.find(".png")]
print('보너스 번호는 {0} 입니다.'.format(s2))
```



전체 기능을 확인하려면 다음의 링크로 접속하세요.

[접속하기](https://s3.py.hphk.io/bots)



예외사항을 표기할 때 다음과 같이 표시합니다.

> ">"을 이용해서 만들어낼 수 있습니다.
>
> > > > 줄을 여러개 늘려나갈 수 있습니다.



| 예시를 위한 표 | columm  | 정렬이 가능합니다. | 쉽게 |
| :------------: | :------ | -----------------: | :--: |
|                | 153,500 |              1,508 |      |



## Git Hub 다루기

git bash를 설치하고 이를 이용해 remote repository를 관리해본다.