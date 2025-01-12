---
layout: post
catergories: post
title:  "Python 기본"
date:   2022-03-20
excerpt: “Python 기본 코드 실습(한글)”
tag:
- Python
author: Jiho Yeo
toc : true
comments: true
---


# "Python 기본"

> "Python 기본 코드 실습(한글)"


# Python Language Basics



## Python Language Basics



### Language Semantics


## 중괄호 아닌 들여쓰기


```

for x in array:

        if x < privot:

            less.append(x)

        else:

            greater.append(x)

```



```python
a = 5; b = 6; c = 7
```


```python
c
```

<pre>
7
</pre>
## 함수 및 객체 method 호출


괄호를 사용하여 함수를 호출하고 0 이상의 인수를 전달합니다.옵션으로 반환된 값을 변수에 할당합니다.



```

result = f(x,y,z)

g()

```


Python의 거의 모든 Object에는 Object의 내부 콘텐츠에 접근할 수 있는 Method라고 불리는 부가 함수가 있습니다. 다음 구문을 사용하여 호출할 수 있습니다.


```

obj.some_method(x,y,z)

```


### 변수 및 인수 전달



```python
a = [1,2,3]
```


```python
b = a
```


```python
a.append(4) # a라는 object에 4를 추가한다. #append는 a라는 object가 가지고 있는 함수
b
```

<pre>
[1, 2, 3, 4]
</pre>
## 데이터 타입



```python
#integer(정수)
a = 5
type(a)
```

<pre>
int
</pre>

```python
#string(문자열)
a = 'foo'
type(a)
```

<pre>
str
</pre>

```python
#float(실수)
a = 4.5
type(a)
```

<pre>
float
</pre>

```python
type(a)
```

<pre>
float
</pre>
## Attributes and methods


python의 object는 일반적으로 attributes(다른 python object가 object를 "저장"하고 있는 것)과 method('object의 내부 데이터에 접근할 수 있는 objcet와 관련된 것)를 모두 가지고 있습니다.



```python
a = 'foo'
```


```python
#a.<Press Tab>

#string type으로 객체를 할당하면 .을 찍으면 사용할 수 있는 함수들이 나온다.
```


```python
# ex)
a.capitalize() #capitalize() : 문자열 str의 첫 번째 알파벳을 대문자로 바꾸고, 다른 알파벳은 모두 소문자로 변경한다.
```

<pre>
'Foo'
</pre>

```python
a.upper() #upper() : 문자열 str의 모든 알파벳을 대문자로 변경한다.
```

<pre>
'FOO'
</pre>
### ~~Duck Typing~~



```python
#for loop문에 넣었을 때 반복적으로 돌아가는지 아닌지 알 수 있는 함수
def isiterable(obj):
    try:
        iter(obj)
        return True
    except TypeError: #not iterable
        return False
```


```python
isiterable('a string')
```

<pre>
True
</pre>

```python
isiterable([1,2,3])
```

<pre>
True
</pre>
## **Imports**


Python에서 모듈은 단순히 Python 코드를 포함하는 .py 확장자를 가진 파일입니다.   

다음 모듈이 있다고 가정합니다.


```

##### some_module.py #####

PI = 3.14159



def f(x):

    return x + 2



def g(a,b):

    return a + b

```


같은 디렉토리에 있는 다른 파일에서 some_moduel.py에 정의된 변수와 함수에 액세스하려면 다음을 수행합니다.



```python
import some_module

result = some_module.f(5)
result
```

<pre>
7
</pre>

```python
# 변수도 가져오기 가능
pi = some_module.PI #some_module에 ctrl을 누르면 some_module에 정의된 변수와 함수를 볼 수 있음
pi
```

<pre>
3.14159
</pre>
매번 앞에 some_module을 쓰는 게 힘들 때 함수를 바로 불러오는 법



```python
from some_module import f, g, PI #some_module에서 direct로 f,g함수와 PI변수를 input 해줌
result = g(5,PI)
result
```

<pre>
8.14159
</pre>
as 키워드를 사용하면 모듈이름과, 함수와 변수의 이름들을 간단하게 줄일 수 있음  



ex

```

import pandas ad pd

```




```python
import some_module as sm
from some_module import PI as pi, g as gf

r1 = sm.f(pi)
r2 = gf(6,pi)
```


```python
r1
```

<pre>
5.14159
</pre>

```python
r2
```

<pre>
9.14159
</pre>
## 변경 가능한 object와 불가능한 object


lists, dicts, NumPy arrays 및 대부분의 사용자 정의 유형(classes)과 같은 Python의 대부분의 object는 변경 가능합니다.  

즉, 포함된 object 또는 값(value)을 변경할 수 있습니다.




```python
a_list = ['foo',2,[4,5]]
a_list[2] = (3,4)
a_list
```

<pre>
['foo', 2, (3, 4)]
</pre>
반면에, 문자열과 tuple은 변경 불가능합니다.  

단, 속도는 빠름


Tuple



```python
# a_tuple = (3,5,(4,5))
# a_tuple[1] = 'four'
```

String



```python
# a = 'this is a string'
# a[10] = 'f'
# #string이기 때문에 변경 불가능
```


```python
#replace라는 method를 사용하면 바꿀 수 있음
b = a.replace('string','longer string')
b
```

<pre>
'this is a longer string'
</pre>
문자열은 일련의 유니코드 문자이므로 list나 tuple 등 다른 시퀀스와 동일하게 취급할 수 있습니다



```python
s = 'python'
list(s)
```

<pre>
['p', 'y', 't', 'h', 'o', 'n']
</pre>

```python
s[:3]
```

<pre>
'pyt'
</pre>
두 개의 문자열을 함께 추가하여 그것들을 연결하고 새로운 문자열을 생성합니다.



```python
a = 'this is the first half'
b = 'and this is the second half'
a + b
```

<pre>
'this is the first halfand this is the second half'
</pre>

```python
# 이럴 때 자주 씀
file_dir = 'G:/tmp/'
file_name = 'test.csv'

file_dir + file_name
```

<pre>
'G:/tmp/test.csv'
</pre>
문자열 object에는 포맷된 인수를 문자열로 대체하여 새로운 문자열을 생성하기 위해 사용할 수 있는 format method가 있습니다.



```python
template = '{0:.2f} {1:s} are worth US${2:d}'
template
```

<pre>
'{0:.2f} {1:s} are worth US${2:d}'
</pre>
* {0:2f} 는 첫 번째 인수의 형식을 소수점 2자리 부동 소수점 숫자로 지정합니다.

* {1:s} 는 두 번째 인수의 형식을 문자열로 지정합니다.

* {2:d} 는 세 번째 인수의 형식을 정확한 정수로 지정합니다.



```python
template.format(4.5560, 'Argentine Pesos',1)
```

<pre>
'4.56 Argentine Pesos are worth US$1'
</pre>

```python
template.format(1263.23,'won',1)
```

<pre>
'1263.23 won are worth US$1'
</pre>
## None


Python에서 변수에 아무 값도 넣고 싶지 않을 때



```python
a = None
a is None
```

<pre>
True
</pre>

```python
a #값은 없지만 object로 할당은 되었음
```

None은 함수 인수의 공통 기본값이기도 합니다.



```python
def add_and_maybe_multiply(a,b,c=None):
    result = a + b

    if c is not None:
        result = result * c

    return result
```


```python
add_and_maybe_multiply(5,3)
```

<pre>
8
</pre>

```python
add_and_maybe_multiply(5,3,10)
```

<pre>
80
</pre>
## 날짜와 시간


내장된 Python datetime 모듈은 datetime, date 및 time types을 제공합니다. datetime 유형은 예상대로 날짜와 시간에 저장된 정보를 조합하여 가장 일반적으로 사용됩니다.



```python
from datetime import datetime, date, time
dt = datetime(2011,10,29,20,30,21)
dt
```

<pre>
datetime.datetime(2011, 10, 29, 20, 30, 21)
</pre>

```python
dt.day
```

<pre>
29
</pre>
datetime 인스턴스를 지정하면 동일한 이름의 datetime method를 호출하여 동일한 날짜 및 시간 개체를 추출할 수 있습니다.



```python
dt.date()
```

<pre>
datetime.date(2011, 10, 29)
</pre>

```python
dt.time()
```

<pre>
datetime.time(20, 30, 21)
</pre>
strftime 메서드는 datetime을 string으로 포맷합니다.



```python
dt.strftime('%m %d %Y %H : %M')
```

<pre>
'10 29 2011 20 : 30'
</pre>

```python
dt.strftime('%Y/%m/%d %H:%M')
```

<pre>
'2011/10/29 20:30'
</pre>
strptime method는 datetime을 string으로 포맷합니다.



```python
datetime.strptime('20091031','%Y%m%d')
```

<pre>
datetime.datetime(2009, 10, 31, 0, 0)
</pre>
시계열 데이터를 집계하거나 그룹화할 때, 분 및 초 field를 0으로 바꾸는 것과 같이 일련의 데이터 시간 field를 바꾸는 것이 유용할 수 있습니다.



```python
dt.replace(minute=0,second=0)
```

<pre>
datetime.datetime(2011, 10, 29, 20, 0)
</pre>

```python
dt2 = datetime(2011,11,15,22,30)
delta = dt2- dt
delta
```

<pre>
datetime.timedelta(days=17, seconds=7179)
</pre>

```python
type(delta)
```

<pre>
datetime.timedelta
</pre>
## 삼항 연산자(Ternary Operator)


```value = true-expr if condition else false-expr```



여기서 true-expr 및 false-expr은 임의의 Python 식입니다. 자세한 내용은 다음과 같습니다.



```

if condition:

    value = true-expr

else:

    value = false-expr

```



```python
x = 5
'None-negative' if x >= 0 else 'Negative'
```

<pre>
'None-negative'
</pre>

```python
x = 5

a = 100 if x >= 0 else -100
a
```

<pre>
100
</pre>
## **제어문**


python은 다른 프로그래밍 언어에서 볼 수 있는 조건부 논리, 루프 및 기타 표준 제어 흐름 개념을 위한 여러 bulit-in 키워드를 가지고 있습니다.


### **if , elif and else**


if 문은 가장 잘 알려진 제어 흐름문 유형 중 하나입니다.  

True일 경우 다음 블록의 코드를 평가하는 조건을 체크합니다.



```python
x = -5

if x < 0:
    print('It is negative')
```

<pre>
It is negative
</pre>
if 문 뒤에 옵션으로 하나 이상의 elif 블록과 모든 조건이 false인 경우 catch all other 블록을 사용할 수 있습니다.



```python
x = -5

if x < 0:
    print('It is negative')
elif x == 0:
    print('Equal to zero')
elif 0 < x < 5:
    print('Positive but smaller than 5')
else:
    print('Positive and larger than or equl to 5')
```

<pre>
It is negative
</pre>
어느 하나의 조건이 참일 경우 더 이상의 elif 또는 블록에 도달하지 않습니다. and 또는 or 를 사용하는 복합 조건에서는 조건이 왼쪽에서 오른쪽으로 평가되어 단락됩니다.



```python
a = 5; b = 7
c = 8; d = 4
if a < b or c > d:
    print('Made it')
```

<pre>
Made it
</pre>
이 예에서는 첫 번째 비교가 True였기 때문에 c>d 비교는 평가되지 않습니다.  

연쇄 비교도 가능합니다.



```python
4 > 3 > 2 > 1
```

<pre>
True
</pre>

```python
3>5 or 2>1
```

<pre>
True
</pre>

```python
3>5>2>1
```

<pre>
False
</pre>
**Pass**


pass는 Python에서 "no-op"("No operation") 문입니다.  

액션이 수행되지 않는 블록(또는 아직 구현되지 않은 코드의 자리 표시자)에서 사용할 수 있습니다.   

Python은 블록을 구분하기 위해 공백을 사용하기 때문에 필요합니다.



```python
x = -1

if x < 0:
    print("negative!")
elif x == 0:
    # TODO: put something smart here
    pass
else:
    print("positive!")
```

<pre>
negative!
</pre>
### **For loops**


for loop는 컬렉션(list나 tuple 등) 또는 반복기로 반복하기 위한 것입니다.  

for loop의 표준 구문은 다음과 같습니다.

```

for value in collection:

    #do something with value

```


continue 키워드를 사용하여 for loop를 다음 반복으로 진행하고 나머지 블록을 건너뛸 수 있습니다. 이 코드는 list의 int를 집계하고 None 값을 건너뜁니다.    



```python
# sequence = [1,2, None, 4, None, 5]
# total = 0

# for value in sequence:
#     total += value
```


```python
sequence = [1,2, None, 4, None, 5]
total = 0

for value in sequence:
    if value is None:
        continue
    total += value
```


```python
total
```

<pre>
12
</pre>
for loop는 break 키워드를 사용하여 모두 종료할 수 있습니다. 이 코드는 5에 도달할 때까지 목록의 요소를 집계합니다.



```python
sequence = [1,2,0,4,6,5,2,1]
total_until_5 = 0
for value in sequence:
    if value == 5:
        break
    total_until_5 += value
```


```python
total_until_5
```

<pre>
13
</pre>
break 키워드는 가장 안쪽의 for loop만 종료합니다.outer for loop는 계속 실행됩니다.



```python
for i in range(4):
    for j in range(4):
        if j > i:
            break
        print((i,j))
```

<pre>
(0, 0)
(1, 0)
(1, 1)
(2, 0)
(2, 1)
(2, 2)
(3, 0)
(3, 1)
(3, 2)
(3, 3)
</pre>
? 컬렉션 또는 반복기 내의 요소가 시퀀스(튜플 또는 리스트 등)인 경우 쉽게 for loop 스테이트먼트의 변수로 압축 해제할 수 있습니다.

```

for a, b, c in iterator:

    # do something

```    



```python
for a, b, c in [[1,2,3],[4,5,6],[7,8,9]]:
    print(a,b,c)
```

<pre>
1 2 3
4 5 6
7 8 9
</pre>
### **While loops**


while loop문은 조건이 False로 평가되거나 루프가 명시적으로 break으로 종료될 때까지 실행되는 조건 및 코드 블록을 지정합니다.



```python
x = 256
total = 0
while x > 0:
    if total > 500:
        break
    total += x
    x = x // 2
```


```python
total
```

<pre>
504
</pre>

```python
x
```

<pre>
4
</pre>
### **Range**


range 함수는 균일한 간격의 정수 시퀀스를 생성하는 반복기를 반환합니다.



```python
range(10)
```

<pre>
range(0, 10)
</pre>

```python
list(range(10))
```

<pre>
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
</pre>
시작, 종료 및 단계(음수일 수 있음)를 모두 지정할 수 있습니다.



```python
list(range(0,20,2))
```

<pre>
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
</pre>

```python
list(range(5,0,-1))
```

<pre>
[5, 4, 3, 2, 1]
</pre>
보시다시피 range는 끝점을 포함하지 않는 정수를 생성합니다.range의 일반적인 용도는 인덱스로 시퀀스를 반복하는 것입니다.



```python
seq = [1,2,3,4]
for i in range(len(seq)):
    val = seq[i]
```


```python
val
```

<pre>
4
</pre>
list와 같은 함수를 사용하여 범위별로 생성된 모든 정수를 다른 데이터 구조에 저장할 수 있지만, 종종 기본 반복자 형식이 원하는 것이 됩니다. 이 스니펫에서는 3 또는5의 배수인0 ~ 99,999 의 모든 수치를 집계하고 있습니다.



```python
sum = 0
for i in range(100000):
    # % is the modulo operator
    if i % 3 == 0 or i % 5 == 0:
        sum += i
```
