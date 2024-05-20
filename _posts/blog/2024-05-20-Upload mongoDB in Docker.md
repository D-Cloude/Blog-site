---
title:  "Docker컨테이너에 mongoDB 생성하기"
categories: blog
---

# 도커에 mongoDB를 생성하는 법
## 1️⃣ 도커 이미지 다운로드
먼저 도커에 mongoDB 이미지를 다운로드 합니다.
아래와 같은 코드를 입력하면 Docker에 mongoDB이미지를 다운로드 할 수 있습니다.

```bash
docker pull mongo
```


![스크린샷 2024-05-20 시간: 10 37 23](https://github.com/D-Cloude/Blog-site/assets/95969488/db43fa5f-b0f5-4191-a8fc-3b5cdcc5bd1e)

```bash
docker images
```
 코드를 통해 mongoDB가 Docker에 제대로 설치되었는지 확인해줍니다.

![스크린샷 2024-05-20 시간: 10 43 48](https://github.com/D-Cloude/Blog-site/assets/95969488/91a66985-846b-4a05-a411-8f44cfea0eed)

위 사진과 같이 mongo가 생성되어있으면 성공입니다.

## 2️⃣ mongoDB Docker 컨테이너 생성 및 실행

```bash
docker run -d -p 987:27017 -v ~/mongodb-yourDBname-docker:/data/db --name mongodb mongo:latest
```
위 코드를 통해 컨테이너를 생성시켜준다. 

```bash
docker ps -a
```
그리고 위 코드를 통해 컨테이너가 제대로 생성되었는지 확인해줍니다.

![스크린샷 2024-05-20 시간: 11 15 31](https://github.com/D-Cloude/Blog-site/assets/95969488/7a0a9781-2efb-43d9-b435-6bbe3526518c)
사진과 같이 로컬 987포트에서 27017번의 컨테이너포트에서 매핑이 되어있는것을 확인할 수 있다.


코드에 포함되는 문법을 아래에 표로 정리해보았다.

| Syntax | Description |
| ----------- | ----------- |
| -d | 컨테이너를 백그라운드에서 실행합니다. |
| -p | 포트 987번 포트를 컨테이너의 27017포트와 매핑한다. |
| -v | Volume Mount 호스트의 디렉토리나 파일을 컨테이너에 마운트하여 지속성을 보장 형식: -v [호스트 경로]:[컨테이너 경로]|
| -a | all 생성되어있는 컨테이너를 전부 확인한다.|

## 3️⃣ Docker에 접속해서 mongoDB 실행하기

```bash
docker exec -it mongodb bash
```
위 코드로 도커에 mongoDB컨테이너에 접속해줍니다.
그리고
```bash
mongosh
```
를 입력하여 mongoDB에 접속할 수 있습니다.

혹시 mongosh부분에서 에러가 발생한다면 mongoDB 버전을 확인해주세요
mongoDB 6.0이하 버전에서는 `mongo`명령어를 통해 mongoDB에 접속할 수 있습니다.

![스크린샷 2024-05-20 시간: 11 19 34](https://github.com/D-Cloude/Blog-site/assets/95969488/87bb84f8-9c7a-49c8-8dd5-7248e3cef100)

그러면 Docker컨테이너에 mongo가 생성되었습니다 ! 🎉 🎉 🎉

## ✅
이제 로컬했던 것처럼 DB를 생성해주면 

![스크린샷 2024-05-20 시간: 03 04 15](https://github.com/D-Cloude/Blog-site/assets/95969488/308cb3e4-dcfb-4ca7-a45f-1b70aeb0c6cf)

위 사진과 같이 도커컨테이너에서 생성한 DB가 잘 작동하는것을 확인할 수 있습니다. 🔥
