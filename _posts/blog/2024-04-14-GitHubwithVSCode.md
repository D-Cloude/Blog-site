---
title: "Visual Studio Code에서 GitHub 연동하기"
categories: blog
---
Windows를 기준으로 작성됨.

## 환경 구성

### 1. Git 설치
[https://git-scm.com/downloads](https://git-scm.com/downloads) 에 접속해서 자신의 운영체제에 맞게 다운로드한다.

![installGit](https://github.com/D-Cloude/Blog-site/assets/image/blog/GithubwithVSCode/00.png)

### 2. Visual Studio Code 설치

[https://code.visualstudio.com/](https://code.visualstudio.com/) 에 접속해서 자신의 운영체제에 맞게 다운로드한다.

![installVSCode](https://github.com/D-Cloude/Blog-site/assets/image/blog/GithubwithVSCode/01.png)

### 3. Github 계정 만들기

[https://github.com/](https://github.com/) 에 접속해서 계정을 만든다.

![signupGithub](https://github.com/D-Cloude/Blog-site/assets/image/blog/GithubwithVSCode/02.png)


## Repository 가져오기

### 1. 키보드 [F1]을 눌러 명령어 창을 켠 뒤 git clone을 입력하여 실행한다.
(만약 no matching commands라고 뜬다면 깃허브 설치가 안되어 있는 것이기에 깃허브를 먼저 설치한다.)

![GitClone](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/03.png)

### 2. Clone from GitHub를 클릭한다.

![CloneFromGitHub](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/04.png)

### 3. GitHub 로그인 팝업창이 뜨면 Allow를 클릭한다.

![allowSignin](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/05.png)

### 4. ID/PW를 입력하고 로그인한다.

![signinGitHub](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/06.png)

### 5. Authorize Visual-Studio-Code 버튼을 클릭한다.

![AuthorizeVSCode](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/07.png)

### 6. Visual Studio Code 열기를 클릭한다.

![openVSCode-1](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/08.png)

### 7. Open을 클릭한다.

![openVSCode-2](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/09.png)

### 8. 자신이 업로드 하고 싶은 repository의 주소를 입력한다.

![cloneRepository](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/10.png)

### 9. 로컬 저장소에서 저장할 위치를 선택한다.

![localRepository](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/11.png)

### 10. Git Connect 방법을 설정한다.
(Sign in with your browser를 선택하면 된다.)

![connectGit](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/12.png)


## GitHub 업로드

### 1. 좌측 3번째 아이콘을 클릭한다. 
### 2. 변경 내용을 모두 스테이징한다.
### 3. 커밋 내용 작성 후 Commit 버튼을 클릭한다.

![commit](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/14.png)

### 4. 업로드 된 걸 확인할 수 있다.

![check](https://github.com/D-Cloude/Blog-site/assets/image/blog/GitHubwithVSCode/15.png)