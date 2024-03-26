---
title:  "Proxmox 설치"
categories: blog
---
서버를 묶어서 통합적으로 관리하기 위해서 "Proxmox"라는 가상화 플랫폼을 설치 해보았다.

## 설치 방법

**1. "PROXMOX ISO 파일"을 다운받아 "USB"에 구워준다.**

**2. PROXMOX를 설치할 컴퓨터에 "USB( [ISO 파일을 다운 받은] )" 장착.**

**3. 컴퓨터가 켜질 때 "ESC" 키를 누르고, 잠시 기다려서 Startup Menu에 들어간다. ("ESC"가 아닌 다른 것일 수 있음)**

**4. "Boot Menu(F9)"에 들어간다. ("F9"이 아닌 다른 것일 수 있음)**

**5. 장착한 "USB 드라이브" 선택.**

**6. PROXMOX 설치 진행.**
![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/00.png)

**7. PROXMOX 이용 약관에 동의.**
![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/01.png)

**8. 설치할 디스크 또는 파티션을 선택.**
![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/02.png)
> 이번에 사용한 경로: [/dev/nvme0n1]

**9. 국가 : 한국 | 시간대 : 서울 | 키보드 레이아웃 : U.S. English 로 선택.**
![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/03.png)

**10. 사용할 비밀번호와 Email 입력.**
![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/04.png)

**11. 네트워크 설정**
![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/05.png)
관리 인터페이스, 호스트 이름, IP 주소, 게이트웨이, DNS 서버에 각각 값을 설정. 
>  이번에 사용한: [enp4sof2, "사용할 이름.{도메인}", 192.168.2.X/16, 192.168.1.1, 113.198.238.2]

**12. 최종 설정값 확인 후 설치.**
![img]({{ site.url }}{{ site.baseurl }}/assets/image/blog/proxmoxinstall/06.png)

**13. 설치후 콘솔에 로그인하라는 표시가 뜨면 설치 완료.**

- - -

## MAC 주소 확인 

로그인 후 "ip a" 입력하여 확인.

- - -
