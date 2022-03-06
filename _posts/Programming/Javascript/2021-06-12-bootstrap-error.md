---
layout: post
title:  "Bootstrap css 적용시 일부 컴포넌트 스타일 깨짐 현상"
date:   2021-06-12 15:46:17 +0530
comments: true
categories: [Programming, Javascript]
---

리액트를 독학하면서 reactstrap와 bootstrap 패키지를 받아서 부트스트랩 모듈을 다뤄보는 시간을 가질 수 있었다.   
일단 부트스트랩을 이용하면 프론트엔드 디자인을 쉽게 구현할 수 있고, React 개발환경에서 사용할 때 필요한 패키지가 바로 리액트스트랩이다.   

리액트 독학용 교재를 참조하여 두 모듈을 설치하고 코드를 짜보고 테스트해보니 부트스트랩에서 지원하는 모듈 일부를 제외하고 문제가 발생했다.   

일단 아래와 같이 작성된 코드를 먼저 확인해보자.   

```javascript
import React, {Component} from 'react';
import {Alert, Badge, Button, UncontrolledAlert} from 'reactstrap';

class ReactStrapTest extends Component{
    render(){
        return(
            <div id="rsMain" style={{padding:"30px"}}>
                <Alert color="info">Alert info</Alert>
                <UncontrolledAlert color="dark">This is UncontrolledAlert component.</UncontrolledAlert>
                <span>
                    <b>Badge List : </b>
                    <Badge color="danger">DANGER BADGE</Badge>
                    <Badge color="warning">WARNING BAD0E</Badge>
                    <Badge color="success">SUCCESS BADGE</Badge>
                </span>

                <div id="rsButton" style={{textAlign:"right"}}>
                    <Button color="primary">Confirm</Button> &nbsp;
                    <Button color="secondary">Cancel</Button>
                </div>
            </div>
        )
    }
}

export default ReactStrapTest;
```

![reactstrap_issue](https://baedi.github.io/assets/post/20210612_01_reactstrapissue.png)

위 코드로 실행을 해보니 Button은 잘 나왔지만 Badge, UncontrolledAlert 등 이 컴포넌트의 스타일이 제대로 나타나지 않는 현상이 발생했다. Badge는 아예 표시되어 있지 않은 것처럼 보이겠지만 흰색 텍스트로 표현되고 있었고, UncontrolledAlert는 원래같은 경우 맨 우측에 X 표시가 나와야 되지만 여기서는 바로 앞에 닫기 버튼으로 표현되고 있어 지저분하다.   

Alert의 경우 UncontrolledAlert와 동일한 기능을 수행하도록 속성을 설정해 두어도 똑같은 현상이 발생했고 다른 컴포넌트의 경우 샘플에서 확인했던 것과 다른 결과가 나타나는 경우도 있었다.   

이 현상을 해결하기 위해 부트스트랩을 재설치하고 임포트할 부트스트랩의 css 파일도 바꿔보았지만 여전히 문제가 해결되지 않았다.   

결국 하루 삽질 끝에 내가 받은 부트스트랩의 css 파일에 문제가 있음을 생각하고 웹사이트에서 부트스트랩을 별도로 받아서 프로젝트에 적용 후 테스트해보니 드디어 문제를 해결하였다.   

만약 터미널에서 부트스트랩과 리액트스트랩을 받고 위와 같은 문제가 발생했다면 먼저 아래 절차를 시도해보자.   
>   
> 1. Bootstrap 사이트 방문 : <https://getbootstrap.com/docs/4.4/getting-started/download/>
>   
> 2. Compiled CSS and JS 의 본문 아래에 있는 Download 버튼을 통해 부트스트랩을 다운로드한다.
>   
> 3. 파일 압축을 해제하고 bootstrap-버전-dist\css 폴더에서 아래 파일들을 프로젝트에 추가한다.   
>  (필자는 index.js 파일이 존재하는 폴더에 넣어주었다.)
>  - bootstrap.min.css   
>  - bootstrap.min.css.map   
>   
>   
> 4. 기존에 가져오기했던 부트스트랩 css를 지우고 새로 가져온 css 파일을 임포트한다.   
>   
>  import './bootstrap.min.css'
>

![reactstrap_issue_complete](https://baedi.github.io/assets/post/20210612_01_reactstrapissue_complete.png)

순서대로 진행한 뒤 화면을 갱신하면 위 화면처럼 정상적으로 부트스트랩 css 스타일이 적용된다.   

+   
혹시나 부트스트랩을 적용시켰는데 일부 컴포넌트가 제대로 표시되지 않는다면 부트스트랩을 최신 버전으로 받아볼 것을 권장한다.   
