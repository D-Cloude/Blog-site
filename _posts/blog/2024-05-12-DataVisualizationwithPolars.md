---
title: "데이터 분석 및 시각화"
categories: blog
---

Polars와 Matplotlib을 사용하여 Titanic 데이터를 분석 및 시각화해보았다.

## Library 설치하기

### 1. cmd창을 연다.
### 2. 설치하려는 라이브러리에 맞게 아래 코드를 입력한다.
```python
pip install '라이브러리 이름'
```

## 데이터 불러오기
seaborn 라이브러리의 [Titanic 데이터](https://bskyvision.com/entry/python-seaborn-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC%EA%B0%80-%EC%A0%9C%EA%B3%B5%ED%95%98%EB%8A%94-%ED%83%80%EC%9D%B4%ED%83%80%EB%8B%89-%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%85%8B-%EC%84%A4%EB%AA%85)을 사용함.

```python
import seaborn as sns

dataset = sns.load_dataset('titanic')

print(dataset) # 확인을 위한 출력
```

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/5a9fb8a0-b8fa-4f6a-95d6-fe8ddc2b93a6)

## 데이터 전처리

### polars.DataFrame 으로 바꾸기
```python
# 필요한 열만 추출 후 영어로 된 값들을 한국어로 바꿈

import polars as pl

map = {True: '생존', False: '사망'}
df = pl.DataFrame(pl.Series('생존 여부', [map[i] for i in dataset['survived']]))

map = {'male': '남', 'female': '여'}
df.insert_column(df.width, pl.Series('성별', [map[i] for i in dataset['sex']]))

df.insert_column(df.width, pl.Series('나이', [(i // 10 * 10) for i in dataset['age']]))

map = {'man': '성인', 'woman': '성인', 'child': '미성년자'}
df.insert_column(df.width, pl.Series('미성년자 여부', [map[i] for i in dataset['who']]))

df.insert_column(df.width, pl.Series('동승자 수', dataset['sibsp'] + dataset['parch']))

print(df) # 확인을 위한 출력
```

> - DataFrame(): polars.DataFrame으로 만듦
> - Series(): polars.Series으로 만듦
> - insert_column(): 데이터 프레임에 열 추가

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/eb644bda-a3b7-4d05-8229-77e254067458)

## 데이터 시각화 및 분석
```python
# 한글 깨짐 현상 방지(Windows)

import matplotlib.pyplot as plt

plt.rcParams['font.family'] = 'Malgun Gothic'
```

### 1. 생존 여부에 대한 원 그래프
```python
# 필요한 데이터 추출

survived = df.group_by('생존 여부').len(name='인원 수')

print(survived) # 확인을 위한 출력
```

> - group_by('열 이름'): 특정 열에 대한 값을 기준으로 그룹을 나눔
> - len(): group_by에 대한 속성, 해당 열에 대한 값을 가지는 행의 개수를 셈

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/3a8447c9-0c1f-4f59-a49d-6cc56adaa1ed)

```python
# 그래프 그리기

plt.pie(survived['인원 수'], labels=survived['생존 여부'], autopct='%.1f%%', explode=[0.1, 0], shadow=True, colors=['lightgray', 'palegreen'])

plt.show() # 그래프 출력
```

> - labels: 각 영역 이름
> - autopct: 부채꼴 안에 표시될 숫자의 형식 지정
> - explode: 중심에서 벗어나는 정도 설정
> - shadow: 그림자
> - colors: 각 영역의 색상 설정

### 그래프 및 분석

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/e43fb2ed-fef6-44c0-9a35-1b1d16cb041f)

> - 생존한 탑승객보다 사망한 탑승객이 약 1.5배 가량 많다는 것을 알 수 있다.

### 2. 전체 탑승객의 성별 비율에 대한 원 그래프
```python
# 필요한 데이터 추출

sex = df.group_by('성별').len(name='인원 수')

print(sex) # 확인을 위한 출력
```

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/35e1a8a9-8385-44bf-b46f-f4d360338d4a)

```python
# 그래프 그리기

plt.pie(sex['인원 수'], labels=sex['성별'], autopct='%.1f%%', explode=[0.1, 0], shadow=True, colors=['pink', 'skyblue'])

plt.show() # 그래프 출력
```

### 그래프 및 분석

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/8938e5d1-2a28-430c-8666-53484fb9f6b3)

> - 남성이 여성보다 약 2배 가량 더 많았음을 알 수 있다.

### 3. 성별과 생존 여부에 대한 막대 그래프
```python
# 데이터 추출 없이 바로 그래프 그림

sns.countplot(data=df, x='성별', hue='생존 여부', palette=['lightgray', 'palegreen'])
```

> - data: 사용할 데이터
> - x: x축에 사용할 열
> - hue: 카테고리 구분 기준 추가
> - palette: 색상 설정

### 그래프 및 분석

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/99e78a15-30eb-4ce8-8c86-48f373ef98fe)

> - 위의 2번째 분석에 따라 남성의 수가 여성의 수보다 많다는 걸 알 수 있다.
> - 남성은 사망자의 수가 생존자의 수보다 약 4배 이상 많다는 걸 알 수 있다.
> - 여성은 생존자의 수가 사망자의 수보다 약 2.5배 많다는 걸 알 수 있다.
> - 남성보다는 여성이 우선적으로 구조됐다고 예상할 수 있다.

### 4. 나이대와 생존 여부에 대한 막대 그래프
```python
# 필요한 데이터 추출

import math

# 필요한 데이터 리스트로 추출
age = []
for i in df['나이']:
    if math.isnan(i):
        age.append('불명')
    else:
        age.append(str(int(i)) + '대')
        
# polars.DataFrame 으로 변경 후 '생존 여부' 열 추가
age = pl.DataFrame(pl.Series('나이대', age))
age.insert_column(0, df['생존 여부'])

print(age) # 확인을 위한 출력
```

> - NaN: 결측치
> - math.isnan(): 괄호 안의 값이 결측치이면 True, 아니면 False 반환
> - sort(): group_by에 대한 속성, 괄호 안의 열을 기준으로 정렬

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/f4c9b5c6-de8f-4a01-9bad-7b1891f7dd7e)

```python
# 그래프 그리기

sns.countplot(data=age, x='나이대', hue='생존 여부', palette=['lightgray', 'palegreen'], order=age.group_by('나이대').len().sort('나이대')['나이대'])
```

> - order: 주어진 값을 기준으로 정렬

### 그래프 및 분석

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/7becbf0d-721b-439d-89a5-fdb44317eccc)

> - 10~70대는 모두 사망자의 비율이 더 높다.
> - 노약자를 우선적으로 구조했다는 것을 예상해 볼 수 있다.
> - 나이를 알 수 없는 탑승자의 수가 많다는 것을 알 수 있다.
> - 이외에는 20~30대가 많다는 것을 알 수 있다.

### 5. 나이대와 생존 여부에 대한 상자 그래프
```python
# 필요한 데이터 추출

age = [[], []] # boxplot에는 리스트가 사용되기에 필요한 데이터를 리스트로 추출

for i in range(df.height):
    if(not math.isnan(df.row(i)[4])):
        if df.row(i)[0] == '생존':
            age[0].append(df.row(i)[4])
        else:
            age[1].append(df.row(i)[4])
        
print(age[0]) # 확인을 위한 출력
print(age[1]) # 확인을 위한 출력
```

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/0e402c40-de9f-499e-8e89-cf3df56862af)

```python
# 그래프 그리기

plt.boxplot(age)
plt.xticks([1, 2], ['생존', '사망'])

plt.show() # 그래프 출력
```

> - xticks(): x축의 이름

### 그래프 및 분석

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/4dea75a3-70eb-4f24-82d4-0ee70ee2f7a6)

> - 위의 4번째 분석을 통해 결측치가 많다는 것을 알았다.
> - 그로인해 이 그래프는 정확한 분석을 하기에는 부적절하다고 생각한다.
> - 80대 탑승객은 생존했음을 알 수 있다.
> - 0~10대의 어린 탑승객들은 대부분이 생존자에 속한다는 것을 알 수 있다.
> - 사망자의 대부분은 20대라는 것을 알 수 있다.

### 6. 동승자 수에 대한 원 그래프
```python
# 필요한 데이터 추출
family = df.group_by('동승자 수').len('인원 수').sort('동승자 수')

print(family) # 확인을 위한 출력
```

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/92b292de-f1d6-4a51-ad10-56e0da0f27d3)

```python
# 그래프 그리기

plt.pie(family['인원 수'], labels=family['동승자 수'], autopct='%.1f%%', explode=[0, 0.1, 0.1, 0.1, 0.2, 0.2, 0.2, 0.2, 0.2], shadow=True, colors=['pink', 'skyblue', 'lightcoral', 'orange', 'yellow', 'palegreen', 'aquamarine', 'violet', 'cornflowerblue'])

plt.show() # 그래프 출력
```

### 그래프 및 분석

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/d30e8b1e-00ca-46d0-bca3-092304d53579)

> - 혼자 탑승한 사람이 대부분이라는 것을 알 수 있다.
> - 이외에도 1~2명 정도만 같이 탑승한 사람이 많고, 나머지는 별로 없다.

### 7. 동승자 수와 생존 여부에 대한 막대 그래프
```python
# 데이터 추출 없이 바로 그래프 그림

sns.countplot(data=df, x='동승자 수', hue='생존 여부', palette=['palegreen', 'lightgray'])
```

### 그래프 및 분석

![image](https://github.com/D-Cloude/Blog-site/assets/166680203/836c4197-8536-4d07-ac4e-9b3a18b2418a)

> - 위의 5번째 분석에 따라 혼자 탑승한 탑승객이 대부분이라는 것을 한번 더 확인할 수 있다.
> - 동승자가 4명 이상인 경우에는 대부분이 사망했다는 것을 알 수 있다.
> - 동승자가 1~3명인 경우에는 사망자보다는 생존자 비율이 더 높다는 것을 알 수 있다.

---