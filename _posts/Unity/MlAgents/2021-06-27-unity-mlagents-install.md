---
layout: post
title:  "유니티 ML Agents 설치 및 세팅"
date:   2021-06-27 18:28:32 +0530
comments: true
categories: [Unity, ML Agents]
---

본 문서는 유니티의 ML-Agents를 구동하기 위하여 필요한 툴과 세팅환경에 대해 다루었다.   

본론에 앞서 ML-Agents는 버전마다 설치 방법, 환경설정이 다르므로 설치 시 버전을 잘 확인하고 설치해야 한다. 이 문서에서는 __Verifled Package 1.0.8__ 버전에 대해 다루었다.   

설치에 필요한 툴과 버전은 아래와 같이 구성하였다.   

(Tools)   
- Unity : <https://unity.com/kr>   
- Anaconda : <https://www.anaconda.com/products/individual>   
- ML-Agents Toolkit : <https://github.com/Unity-Technologies/ml-agents>      


(Version)   
- __OS__ : Windows 10   
- __Unity__ : 2021.1.12f1   
- __Anaconda3__ : 2021.05   
- __Python__ : 3.7.10   
- __ML-Agents Toolkit__ : Verifled Package 1.0.8   
- __ML-Agents Python package__ : 0.16.1   
- __ML-Agents Unity package__ : 1.0.8   
- __CUDA__ : 11.0      


#   
## 유니티 설치   

아래 링크를 통해 방문하여 라이선스를 선택한다.   
<https://unity.com/kr>   

일반 사용자인 경우 개인 탭의 Personal 라이선스를 선택하고 유니티 허브를 다운로드 후 설치를 진행한다. 설치가 끝나면 Unity Hub를 실행시켜 왼쪽에 “설치”를 누르고 추가 버튼을 눌러 버전을 설치할 수 있다.   

유니티 버전은 본인이 받으려고 하는 ML-Agents 툴킷 버전의 릴리즈 년도와 동일한 버전이나 최신 버전을 다운로드할 것을 권장한다.   
2019.2.17f1 으로 테스트한 결과 ML Agents 패키지를 추가해도 아무런 반응이 없는 현상이 확인되었다.   

![unity_add_version](https://baedi.github.io/assets/post/20210627_02_01_unity_add_version.png)      

#   
## 아나콘다 설치   

아래 링크를 클릭하여 아나콘다를 다운로드 후 설치를 진행한다.   
<https://www.anaconda.com/products/individual>   

설치 시 별다른 설정 없이 계속 다음 버튼을 누르면 된다. 설치 후 윈도우 검색창에 Anaconda를 입력하여 Anaconda Prompt 프로그램이 설치되어 있는지 확인한다.   

![anaconda_prompt](https://baedi.github.io/assets/post/20210627_02_02_anaconda_prompt.png)      

#   
## ML-Agents Toolkit 설치   

아래 링크를 클릭하면 깃허브의 ML-Agents Toolkit 문서를 확인할 수 있다.   
<https://github.com/Unity-Technologies/ml-agents>   

스크롤을 아래로 내려가다 보면 아래와 같은 표가 나타날 것이다.   

![github_mlagent_version](https://baedi.github.io/assets/post/20210627_02_03_github_mlagent_version.png)   

Verifled Package 1.0.8 버전에 대해 download 버튼을 클릭하여 바탕화면에 저장해두고 압축을 해제해둔다. 이 버전에서 파이썬 패키지는 0.16.1, 유니티 패키지는 1.0.8을 요구하고 있다.   

그리고 해당 버전의 문서에서 가상환경에 관한 문서를 확인해보니 파이썬 버전은 3.6 ~ 3.7 버전을 요구하고 있다.   

나중에 아나콘다를 이용하여 각 패키지 설치를 진행할 때 반드시 이 버전에서 요구하는 파이썬 버전과  패키지 버전으로 설치해야 된다. 필요한 툴을 모두 받았을 경우 이제 ML-Agent를 구동하기 위한 환경설정이 필요하다.   


#   
## 가상환경 생성, 패키지 설치   

먼저 윈도우 검색창에 Anaconda를 검색하여 __Anaconda Prompt__ 프로그램을 실행시킨다.   

처음 프로그램을 실행하면 가상환경이 base로 설정되어 있는데, 여기서는 ML-Agent를 위한 가상환경을 생성한 뒤 해당 가상환경에서 사용할 파이썬 버전과 패키지를 설치할 것이다. (다른 파이썬 프로젝트와 충돌 방지를 위함)   

가상환경을 생성하기 위하여 아래처럼 명령어를 입력하고 Proceed가 나오면 y를 입력한다. 여기서 가상환경 이름은 mlagent_test로 하였다. (다른 이름을 사용해도 된다.)   

>   
> conda create --name mlagent_test   
>   

![conda_create](https://baedi.github.io/assets/post/20210627_02_04_conda_create.png)      


가상환경이 잘 생성되었는지 확인하기 위해 아래 명령어를 입력하여 확인한다.   

>   
> conda env list   
>   

![conda_envlist](https://baedi.github.io/assets/post/20210627_02_05_conda_envlist.png)      


본인이 입력한 이름이 리스트에 나타났다면 정상적으로 생성이 된 것이다.   

이제 해당 가상환경에서 필요한 작업을 수행하기 위해서 아래 명령어를 입력하여 해당 가상환경을 활성화한다. 이 명령어는 Prompt를 다시 실행할 때 필요하다.   

>   
> conda activate ml-agent   
>      

base에서 다른 이름으로 바뀌었다면 해당 가상환경이 활성화된 것이다. 패키지 설치를 진행하기 이전에 파이썬 패키지를 먼저 확인해보자.   

>   
> python --version   
>   

이 명령어를 입력했을 때 파이썬 버전이 나오는지 확인한다. 아마 버전은 안 나타나고 Python 문구만 나타날 것이다.   

앞서 문서에서 설치한 툴킷 버전에서 필요한 파이썬 버전은 3.6 ~ 3.7 버전이기 때문에 반드시 해당 파이썬 버전을 설치해야 된다.   

아래 명령어를 입력하여 파이썬 3.7 설치를 진행한다.   

>   
> conda install python=3.7   
>   

그 후 다시 버전을 확인한다면 3.7 버전이 설치되어 있을 것이다.   

![python_version](https://baedi.github.io/assets/post/20210627_02_06_python_version.png)      


다음은 mlagents 파이썬 패키지 설치가 필요하다. 앞서 문서에서 설치한 툴킷의 Python Package 버전에 맞게 설치해야 하므로 여기서는 0.16.1 버전을 설치한다.   

참고문서 : <https://pypi.org/project/mlagents/#history>      


아래 명령어를 입력하여 mlagents 패키지를 설치한다. 설치 시 시간이 다소 걸린다.   

>   
> pip install mlagents==0.16.1   
>   

설치가 끝났다면 mlagents가 정상 구동되는지 확인하기 위해 아래 명령어를 입력한다.   

>   
> mlagents-learn   
>   

![mlagents_learn1](https://baedi.github.io/assets/post/20210627_02_07_mlagents_learn1.png)   

명령어를 입력했더니 한 가지 문제가 발생하였다. cudart64_110.dll 파일을 찾을 수 없다고 나타났다.   
확인해보니, 내 PC에 CUDA가 설치되지 않았다. 물론 설치되었다 해도 버전이 다를 경우 동일한 문제가 발생할 수 있다.   

아래 사이트에서 CUDA 11.0을 다운로드한다.   
<https://developer.nvidia.com/cuda-11.0-download-archive?target_os=Windows&target_arch=x86_64&target_version=10>      


![cuda_download](https://baedi.github.io/assets/post/20210627_02_08_cuda_download.png)   

CUDA 설치 이후 Prompt 창을 다시 껐다가 켜서 mlagents-learn 명령어를 다시 실행하면 된다.      


![mlagents_learn2](https://baedi.github.io/assets/post/20210627_02_09_mlagents_learn2.png)   

해당 명령어를 다시 입력하면 이전과는 다르게 Successfully opened dynamic library curart64_110.dll 메시지가 나왔음을 확인할 수 있는데 이 메시지가 나왔다면 패키지 세팅 작업이 완료된 것이다.   



#   
## 유니티 ML-Agent 사용   

이제 유니티 허브를 열어서 프로젝트를 생성한다. 템플릿은 3D로 설정하고, 프로젝트 이름을 입력한 뒤 생성 버튼을 누른다.      


![unity_create_project](https://baedi.github.io/assets/post/20210627_02_10_unity_create_project.png)   

유니티 프로젝트가 열렸다면 Window 탭을 누르고 Package manager를 선택한다.   
패키지 매니저 창에서 왼쪽 상단의 '+' 버튼을 누르고 Add package from disk... 를 클릭한다.   

![unity_mlagents_f2](https://baedi.github.io/assets/post/20210627_02_11_unity_mlagents_f2.png)   

경로 지정은 자신이 ML-Agents Toolkit를 설치하여 압축을 풀었던 폴더의 com.unity.ml-agents 폴더에 들어가면 package.json 파일이 하나 있다. 그 파일을 선택하면 잠시 후에 해당 패키지를 설치하게 된다.   

다시 툴킷 폴더로 돌아와서 Project\Assets 폴더를 확인해보면 아래와 같은 파일들이 있을 것이다.      


![unity_mlagents_assets](https://baedi.github.io/assets/post/20210627_02_12_unity_mlagents_assets.png)   

이 파일들을 모두 선택하고 드래그하여 현재 유니티 창의 Asset 폴더에 드롭한다.      


![unity_mlagents_assets2](https://baedi.github.io/assets/post/20210627_02_13_unity_mlagents_assets2.png)   

적용 이후 콘솔 창에 수십 개의 Warning 메시지가 나타났으나 에러는 발생되지 않았다. (이보다 최신버전인 2021.1.12f1 버전의 경우 Warning도 발생되지 않았다.)   

이제 ML-Agents 폴더의 Examples 폴더에서 원하는 프로젝트를 하나 골라서 Scene 폴더에 있는 씬 하나를 열어본다. 작성자의 경우 WallJump 씬을 열어보았다.      


![unity_run](https://baedi.github.io/assets/post/20210627_02_14_unity_run.png)   

해당 씬을 열고 플레이 버튼을 누르니 캐릭터가 블록을 이용하여 벽을 넘어서 목적지에 여러 번 도달하는 광경을 볼 수 있었다. 이제 마지막으로 확인해야 할 것은 mlagents 파이썬 패키지를 이용하여 학습시킬 수 있는지를 확인해봐야 한다.   

다시 툴킷 폴더로 가서 config 폴더를 확인해보면 몇 가지 yaml 형식의 파일이 존재하는데 trainer_config.yaml 파일을 복사해서 바탕화면에 붙여넣기한다. 이 파일을 열어보게 되면 각 config 설정들을 확인해볼 수 있다.   

다시 Anaconda Prompt 창을 열어서 아래 명령어를 입력하여 학습을 시작한다. (run-id는 아무거나 적으면 된다.)   

>   
> conda activate mlagent_test   
> mlagents-learn C:\Users\사용자\Desktop\trainer_config.yaml --run-id=TestBigJump   
>      

![mlagents_learn_start_f2](https://baedi.github.io/assets/post/20210627_02_15_mlagents_learn_start_f2.png)   

유니티 로고 창이 나타나고 Listening on port 5004. Start training byh pressing the Play button메시지가 나타나면 유니티에서 시작 버튼을 누르면 학습이 시작되고 빠르게 학습 과정을 확인할 수 있다.      


![mlagents_learn_process](https://baedi.github.io/assets/post/20210627_02_16_mlagents_learn_process.png)   

처음에는 에이전트가 엉뚱한 곳을 돌아다녀 계속 실패하는 상황만 보이다가 시간이 지날수록 벽이 없는 상태에서 목적지에 도달하고, 작은 벽을 넘게 되고, 좀 더 많이 학습시키면 큰 블럭을 이용하여 목적지에 도달하는 광경까지 볼 수 있었다.   

학습을 중지하려면 Prompt 창에서 Ctrl + Z 를 누르면 종료할 수 있다. 학습이 종료되면 본인이 mlagents-learn 명령어를 실행시킨 경로에 models 폴더가 생성되어 있을 것인데 (cd 명령어를 사용하지 않았다면 보통은 사용자 폴더에 있을 것이다.) 그 폴더 안에서 학습 결과물을 확인할 수 있다.      


![mlagents_learn_result](https://baedi.github.io/assets/post/20210627_02_17_mlagents_learn_result.png)   

안에 내용물을 확인해본다면 nn 확장자 파일이 있을 것인데 이 파일을 에이전트에게 적용시키고 유니티를 실행하면 그동안의 학습 결과를 볼 수 있다. 짧은 시간동안만 학습했기 때문에 벽을 넘기는 것이 아직 미숙하지만...   
