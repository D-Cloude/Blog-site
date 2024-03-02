---
title:  "Proxmox 설치"
categories: blog
---
우리는 이번에 서버를 묶어서 통합적으로 관리하기 위해서 Proxmox라는 가상화 플랫폼을 설치 해보기로 했다.

## 설치 방법

1. "PROXMOX ISO 파일"을 다운받아 "USB"에 구워준다.

2. "USB( [ISO 파일을 다운 받은] )" 장착후 전원 ON.

3. 컴퓨터가 켜질 때 "ESC" 키를 누르고, 잠시 기다려서 Startup Menu에 들어간다.

4. "Boot Menu(F9)"에 들어간다.

5. 장착한 "USB 드라이브"를 선택.
![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/00.png)

### 6. PROXMOX 창이 뜨면 설치 진행.

![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/01.png)

### 7. PROXMOX 이용 약관에 동의.

![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/02.png)
### 8. 설치할 디스크 또는 파티션을 선택 후 다음으로. 

> 이번에 사용한: [/dev/nvme0n1]

![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/03.png)

###  9. 국가 : 한국 | 시간대 : 서울 | 키보드 레이아웃 : U.S. English 로 선택 후 다음으로.

![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/04.png)
###  10. 사용할 비밀번호와 Email 입력 후 다음으로.

> 이번에 사용한: [dod54321!, {Email}]

![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/05.png)
### 11. 네트워크 설정 
관리 인터페이스, 호스트 이름, IP 주소, 게이트웨이, DNS 서버에 각각 값을 설정 후 다음으로. 

>  이번에 사용한: [enp4sof2, "사용할 이름.{도메인}", 192.168.2.X/16, 192.168.1.1, 113.198.238.2]

![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/06.png)
###12. 최종 설정값 확인 후 설치.
### 13. 설치후 잠시 기다리면 콘솔에 뜨는 로그인하라고 뜨면 설치 완료.

## MAC 주소 확인 

로그인 후 "ip a" 입력하여 확인.