---
layout: post
title:  "깃(Git) 설치하기"
date:   2022-03-12 15:08:59 +0530
comments: true
categories: [Version Control, Git]
---

최근 깃에 대해 공부를 시작하게 되었다. 공부를 시작하게 된 계기는 친구가 하고 있는 프로젝트에 나도 참여하기 시작하면서부터였다.   

친구는 깃허브를 통해 프로젝트를 수행하고 있었는데 먼저 프로젝트를 같이 협업하기 위해서 깃에 대한 지식이 필요했었다.   

그동안 나는 깃허브에 저장소를 만들고 코드를 저장하여 단순히 버전을 관리하는 용도로만 사용했었고 깃에 대한 전반적인 지식은 전무했었다. 친구 덕분에 깃의 필요성을 알게되었고 앞으로 하게 될 프로젝트를 위해서 깃을 제대로 알고 배우는 것이 중요하다고 느껴져서 이번에 깃을 공부하면서 배운 내용들을 앞으로 여기에 기록해두고자 한다.   

&nbsp;
## Git이란 무엇인가?   

컴퓨터 프로그램(소스코드, 문서)이 언제 수정되었고, 어떤 내용이 변경되었는지 변경사항을 추척, 관리하기 위한 분산 버전 관리(Distributed Version Control) 도구이다.   

일반적으로 많이 사용되고 있는 버전 관리 도구로 SVN과 Git이 있는데, SVN은 중앙 집중식 버전 관리 방식으로 중앙 서버에 연결하여 버전 관리하는 반면 Git은 분산 버전 관리 방식으로 로컬 저장소, 서버 저장소로 각각 독립적으로 버전 관리를 할 수 있어서 인터넷이 없는 환경에서도 버전 관리가 가능하다.   

Git에 대한 자세한 설명은 아래 링크 참고   

 - [깃 (소프트웨어)](<https://ko.wikipedia.org/wiki/%EA%B9%83_(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4)>)
 - [GIT이란 무엇인가, GIT에 대하여](<https://www.tuwlab.com/ece/22202>)
 - [[웹개발 기초] 형상관리툴이란? (SVN GIT 간단비교)](<https://goddaehee.tistory.com/158>)

&nbsp;
## Git 설치 (Windows)
먼저 깃을 설치하기 위해 아래 사이트의 링크를 클릭한다.   
Git : <https://git-scm.com/>   

해당 사이트에서 우측 하단에 최신버전을 다운로드받을 수 있는 버튼이 있다.   

![git_install_01](https://baedi.github.io/assets/post/2022-03-12/git-install-01.png)   

![git_install_02](https://baedi.github.io/assets/post/2022-03-12/git-install-02.png)   

Click here to download 를 눌러 64비트 최신 버전을 다운로드받을 수 있다.   

&nbsp;
### 설치 과정 순서   
1. 라이선스 확인   
> &nbsp;   

2. Git 설치 경로 지정   
> &nbsp;   

3. 컴포넌트 선택   
![git_install_03](https://baedi.github.io/assets/post/2022-03-12/git-install-03.png)   
><b>Additional icons (추가 아이콘)</b>   
><b> - On the Desktop</b> : 바탕화면에 Git Bash 아이콘 추가
>
><b>Windows Explorer integration (Windows 탐색기 통합)</b>   
><b> - Git Bash Here </b> : 컨텍스트 메뉴에 Git Bash Here 추가   
><b> - Git GUI Here </b>	: 컨텍스트 메뉴에 Git GUI Here 추가   
>(바탕화면 혹은 폴더 화면에 마우스 우클릭시 확인 가능)   
>
><b>Git LFS (Large File Support)</b> : Git LFS 사용 (프로젝트에 대용량 파일을 관리해야 할 경우 필요)   
>
> <b>Associate .git* configuration files with the default text editor</b> : .git* 구성 파일을 기본 텍스트 편집기에 연결   
>
> <b>Associate .sh files to be run with Bash</b> : Bash와 실행할 .sh 파일 연결   
>
> <b>Check daily for Git for Windows updates</b> : 매일 Git 업데이트를 확인한다.   
>
> <b>Add a Git Bash Profile to Windows Terminal</b> : Windows 터미널에 Git Bash 프로필 추가 (윈도우 시작 화면에 Git Bash 아이콘이 추가된다.)   
> &nbsp;   

4. 시작 메뉴 폴더에 Git 추가 설정   
> &nbsp;   

5. Git 기본 편집기 사용   
![git_install_04](https://baedi.github.io/assets/post/2022-03-12/git-install-04.png)   
>Git 기본 편집기를 설정할 수 있다. 기본값은 Vim으로 설정되어 있다.   
> &nbsp;   

6. Git 리포지토리 생성시 초기 브랜치 이름 설정   
![git_install_05](https://baedi.github.io/assets/post/2022-03-12/git-install-05.png)   
>기본 선택시(Let Git decide) 나중에 리포지토리를 생성할 경우 초기 branch 이름을 "master"로 설정한다.   
> &nbsp;   

7. PATH 환경설정   
![git_install_06](https://baedi.github.io/assets/post/2022-03-12/git-install-06.png)   
> <b>Use Git from Git Bash only</b> :   
> Git Bash에서만 Git 명령어 사용 가능.   
>
> <b>Git from the command line and also from 3rd-party software</b> :   
> PATH에 최소한의 Git wrapper 추가함. Git Bash, 명령 프롬프트 및 윈도우의 PowerShell에서 Git 명령어 사용 가능.   
>
> <b>Use Git and optional Unix tools from the Command Prompt</b> :   
> Git과 Unix 도구를 PATH에 추가 (이 옵션을 사용할 경우 find, sort와 같은 Windows 도구가 재정의된다.)   
> &nbsp;   

8. SSH 실행 파일 선택   
![git_install_07](https://baedi.github.io/assets/post/2022-03-12/git-install-07.png)   
> <b>Use bundled OpenSSH (번들 OpenSSH 사용)</b> :    
> 이 경우 Git과 함께 제공되는 ssh.exe가 사용됨.   
>
> <b>Use external OpenSSH (외부 OpenSSH 사용)</b> :    
> 이 경우 외부 ssh.exe가 사용되며, Git은 자체 OpenSSH 바이너리를 설치하지 않고 PATH에서 찾을 수 있는 대로 사용한다.   
> &nbsp;   

9. HTTPS 전송 백엔드 선택   
![git_install_08](https://baedi.github.io/assets/post/2022-03-12/git-install-08.png)   
> <b>Use the OpenSSL library (OpenSSL 라이브러리 사용)</b> :   
> 서버 인증서는 ca-buncle.crt 파일을 사용하여 검증함.   
>
> <b>Use the native Windows Secure Channel library (기본 Windows Secure Channel 라이브러리 사용)</b> :   
> 서버 인증서는 Windows 인증서 저장소를 사용하여 검증하며, 또한 이 옵션을 사용할 경우 Active Directory 도메인 서비스를 통해 배포된 회사의 내부 루트 CA 인증서를 사용할 수 있다.   
> &nbsp;

10. 줄 끝 변환 구성   
![git_install_09](https://baedi.github.io/assets/post/2022-03-12/git-install-09.png)   
> <b>Checkout Windows-style, commit Unix-style line endings</b> :   
> 텍스트 파일을 checking out시 LF를 CRLF로 변환하고, 텍스트 파일을 commit 할 경우 CRLF를 LF로 변환한다. (Windows에서 권장하는 옵션)   
>
> <b>Checkout as-is, commit Unix-style line endings</b> :   
> 텍스트 파일을 checking out시 변환하지 않고, 텍스트 파일을 commit 할 경우 CRLF를 LF로 변환한다. (크로스 플랫폼 프로젝트의 경우 유닉스에서 권장하는 옵션)   
>
> <b>Checkout as-is, commit as-is</b> :   
> 텍스트 파일을 checking out 하거나 commit할 때 변환을 수행하지 않는다. (크로스 플랫폼 프로젝트에서 이 옵션을 권장하지 않음)   
> &nbsp;

11. Git Bash와 함께 사용할 터미널 에뮬레이터 구성   
![git_install_10](https://baedi.github.io/assets/post/2022-03-12/git-install-10.png)   
> <b>Use MinTTY (the default terminal of MSYS2)</b> :   
> Git Bash에 MinTTY(MSYS2의 기본 터미널)를 터미널 에뮬레이터로 사용한다. MinTTY에서 작동하려면 Windows 콘솔 프로그램을 winpty를 통해 시작해야 한다.   
>
> <b>Use Windows' default console window</b> :   
> Windows의 명령 프롬프트(cmd.exe)를 사용한다.   
> &nbsp;   

12. git pull의 기본 동작 설정   
![git_install_11](https://baedi.github.io/assets/post/2022-03-12/git-install-11.png)   
> <b>Default (fast-forward or merge)</b> :   
> git pull의 표준 동작. 가능하면 현재 branch를 가져온 branch로 fast-forward하고, 그렇지 않으면 병합 커밋을 만든다.   
>
> <b>Rebase</b> :   
> 가져온 branch에 현재 branch를 다시 배치한다.   
>
> <b>Only ever fast-forward (항상 fast-forward 만)</b> :   
> 가져온 branch로 fast-forward 수행. (fast-forward가 불가능할 경우 실패한다.)   
> &nbsp;   

13. 자격 증명 도우미 선택   
![git_install_12](https://baedi.github.io/assets/post/2022-03-12/git-install-12.png)   
> <b>Git Credential Manager (Git 자격 증명 관리자)</b> :   
> 교차 플랫폼 Git Credential Manager 사용   
>
> <b>None (없음)</b> :   
> 자격 증명 도우미를 사용하지 않음.   
> &nbsp;

14. 추가 옵션   
![git_install_13](https://baedi.github.io/assets/post/2022-03-12/git-install-13.png)   
> <b>Enable file system caching (파일 시스템 캐싱 사용)</b> :   
> 파일 시스템 데이터는 대량으로 읽히고 특정 작업에 대해 메모리에 캐시되어 ("core.fscache"는 "true"로 설정됨) 성능이 크게 향상된다.   
>
> <b>Enable symbolic links (심볼릭 링크 사용)</b> :   
> 심볼링 링크를 사용 (SeCreateSymbolicLink 사용 권한 필요), 기본 리포지토리에는 이 설정이 적용되지 않음.   
> &nbsp;   

15. 실험 옵션 구성   
![git_install_14](https://baedi.github.io/assets/post/2022-03-12/git-install-14.png)   
> <b>Enable experimental support for pseudo consoles.</b> :   
> Git Bash 창에서 Winpty를 사용하지 않고 Node나 Python 같은 네이티브 콘솔 프로그램을 실행할 수 있다. (그러나 현재 알려진 버그 존재함)   
>
> <b>Enable experimental built-in file system monitor</b> :   
> 기본 제공 파일 시스템 감시기를 자동으로 실행하여 많은 파일이 포함된 작업 트리에서 일반적인 명령어(git status, git add, git commit 등)의 속도를 높여준다.   
> &nbsp;

![git_install_15](https://baedi.github.io/assets/post/2022-03-12/git-install-15.png)   
설치가 끝나면 윈도우에 Git을 검색하여 Git Bash를 실행하여 Git을 사용할 수 있다.
