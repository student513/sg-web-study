## Javascript

1. promise.all

- 비동기적으로 실행되는 함수 배열을 받아 그 결과를 배열로 받아볼 수 있다.
- 의존적이지 않은 api구문을 효율적으로 처리가능
- 프로미스 내에서 return을 해야 실행이 완료된 리졸브가 반환된다.
- 프로미스가 하나라도 리졸브되지 않을 경우 모든 프로미스가 리졸브되지 않음
- 몇 개라도 프로미스를 건지고 싶다면 promise.allSettled 사용

2. 비동기 처리 관점에서의 forEach와 Promise.all 비교

- promise.all은 리졸브까지 전부 반환하고 루프가 끝난 후, 다음 코드 실행
- forEach는 리졸브가 반환되기 전에 다음 코드 실행. 콜백만 실행하고 끝나버리기에 비동기 작업의 처리 상태를 추적하지 못함
- forEach 는 배열을 돌며 callback을 호출하기만 하면, pending 상태에서 resolve를 반환하기 전에  맡은 바 임무를 다 한 것으로 생각하고 종료된다
- [출처](https://velog.io/@hanameee/%EB%B0%B0%EC%97%B4%EC%97%90-%EB%B9%84%EB%8F%99%EA%B8%B0-%EC%9E%91%EC%97%85%EC%9D%84-%EC%8B%A4%EC%8B%9C%ED%95%A0-%EB%95%8C-%EC%95%8C%EC%95%84%EB%91%90%EB%A9%B4-%EC%A2%8B%EC%9D%84%EB%B2%95%ED%95%9C-%EC%9D%B4%EC%95%BC%EA%B8%B0%EB%93%A4)

2. forEach와 map의 비교

   - forEach: 배열의 각 요소에 대해 callback을 실행
   - map: 배열의 각 요소에 대해 callback을 실행 후 실행결과를 모은 새 배열 리턴
   - forEach 는 배열 요소를 돌면서 callback을 실행할 뿐, 한 callback이 끝날때 까지 기다렸다가 다음 callback을 실행하는 것이 아니다.

3. this

- 스코프에 따라 가리키는 객체

  - 전역공간/함수 내부: window/global 전역객체
  - 메소드: 메소드 호출 주체
  - callback: 기본적으로 함수와 동일. callback의 제어권을 넘겨받은 함수가 call, apply, bind 등으로 this 주체를 설정 가능
  - 생성자함수: 인스턴스

  - arrow function의 등장배경: 객체 내 함수의 this가 전역객체를 가리키지않고 메소드처럼 호출 주체를 부르도록 하기 위해서
  - call, apply, bind등으로 this의 주체를 직접 설정 가능
  - call: 매개변수 무한으로 넘겨줄 수 있다.
  - apply: 매개변수가 담긴 배열 하나 넘겨준다
  - bind: call, apply는 즉시호출. bind는 새로운 함수 생성

16. setInterval과 setTimeOut의 차이?

- setInterval
  - 일정 간격으로 함수 실행
  - 실행중 다른 setInterval로 인해 함수가 호출되면 기존에 실행되던 함수는 종료된다.
- setTimeout
  - 일정 시간 후 함수 한번 호출
  - 실행중 다른 setTimeout로 인해 함수가 호출되도 기존에 실행된 함수에 영향을 주지 않는다.

4. localStorage vs sessionStorage

- sessionStorage: 브라우저에서 같은 웹사이트를 여러 탭이나 창에 띄우면, 여러 개의 세션 스토리지에 데이터가 서로 격리되어 저장되며, 각 탭이나 창이 닫힐 때 저장해 둔 데이터도 함께 소멸합니다.
- localStorage: 로컬 스토리지의 경우 여러 탭이나 창 간에 데이터가 서로 공유되며 탭이나 창을 닫아도 데이터는 브라우저에 그대로 남아 있습니다.
- [출처](https://www.daleseo.com/js-web-storage/)

5. web cache

- 사용자(client)가 웹 사이트(server)에 접속할 때, 정적 컨텐츠(이미지, JS, CSS 등)를 특정 위치(client, network 등)에 저장하여, 웹 사이트 서버에 해당 컨텐츠를 매번 요청하여 받는것이 아니라, 특정 위치에서 불러옴으로써 사이트 응답시간을 줄이고, 서버 트래픽 감소 효과를 볼 수 있다.

- 첫 요청 시에 파일을 내려받아 특정 위치에 복사본을 저장(USING SPACE)하고, 이후 동일한 URL의 Resource요청은 다시 내려 받지 않고 내부에 저장한 파일을 사용하여 더 빠르게 서비스(SAVE TIME)하기 위한 것입니다.

- 종류

  - Browser Caches

    - 브라우저 또는 HTTP요청을 하는 Client Application에 의해 내부 디스크에 캐쉬
    - Cache된 Resource를 공유하지 않는 한 개인에 한정된 Cache
    - 브라우저의 Back버튼 또는 이미 방문한 페이지를 재 방문하는 경우 극대화

  - Proxy Caches

    - Browser Cache와 동일한 원리로 동작하며 Client나 Server가아닌 네트워크 상에서 동작.
    - 큰회사나 IPS의 방화벽에 설치 되며 대기시간 & 트래픽 감소, 접근정책 & 제한 우회, 사용률 기록등 수행
    - 한정된 수의 클라이언트을 위하여 무한대의 웹서버의 컨텐츠를 캐쉬

  - Gateway Caches (REVERSE OR SURROGATE PROXY)
    - 서버 앞 단에 설치되어 요청에 대한 캐쉬 및 효율적인 분배를 통해 가용성, 신뢰성, 성능등을 향상
    - Encryption / SSL acceleration, Load balancing, Serve/cache static content, Compression등을 수행
    - 무한대의 클라이언트들에게 한정된 수(또는 하나)의 웹서버 컨텐츠를 제공

- 캐쉬 컨트롤
  - HTML Meta Tags
  - HTTP Headers
- 어떻게 캐쉬가 동작하나?
  - 첫 요청
    - 브라우저는 서버에 index.html 파일을 요청합니다.
    - 서버는 index.html파일을 찾아보고 존재 하는 파일이라면 파일 내용을 브라우저에게 몇 가지 header값과 함께 응답합니다.
    - 브라우저는 응답 받은 내용을 브라우저에 표시하고 응답 헤더의 내용에 따라 캐쉬 정책을 수행합니다.
  - 재 요청
    - 최초응답 시 받은 값을 헤더에 포함시켜 페이지 요청
    - 요청 파일의 수정시간을 헤더와 비교하여 동일하면 304 not modified로 응답하고 다르면 200 OK와 함께 새로운 값을응답헤더에 전송
- [출처](https://hahahoho5915.tistory.com/33)

## babel

1. 바벨이란? 레거시 브라우저에 서비스가 구동되도록한 경험이 있나?

- 자바스크립트 트랜스파일러이다.
- 나날이 변화하는 esnext 문법을 기존의 브라우저가 이해할 수 있도록 예전 문법으로 변환시켜준다
- typescript 또한 javascript로의 변환이 필요하다.
- polyfill
  - 폴리필(polyfill) 은 개발자가 특정 기능이 지원되지 않는 브라우저를 위해 사용할 수 있는 코드 조각이나플러그인을 의미 합니다.
  - 브라우저에서 지원하지 않는 기능들에 대한 호환성 작업을 채워 넣는다고 해서 polyfill 이라고 칭합니다.
  - babel 은 이러한 polyfill 을 손쉽게 지원하기 위해 babel-polyfill 기능을 지원합니다.
  - 즉, babel 은 컴파일시에 실행되고 babel-polyfill 은 런타임에 실행되는 것입니다.

## webpack

1. 웹팩이란?

- 웹팩은 기본적으로 모듈 번들러다.
- 의존성 그래프에서 엔트리로 그래프의 시작점을 설정하면 웹팩은 모든 자원을 모듈로 로딩한 후 아웃풋으로 묶어준다. 로더로 각 모듈별로 바벨, 사스변환 등의 처리하고 이 결과를 플러그인이 받아 난독화, 텍스트 추출 등의 추가 작업을 한다.

## node.js

1. node.js란?

- 웹 서버는 node.js로 구축할 수 있는 기능 중 하나일 뿐, node.js가 웹 서버 그 자체는 아니다.
- javascript 런타임(프로그래밍 언어가 구동되는 환경)이다.
- 특징: 이벤트 기반으로 개발이 가능하며 Non-Blocking I/O를 지원하기 때문에 비동기식 프로그래밍이 가능
  - 비동기 I/O 처리: Node.js 라이브러리의 모든 API는 비동기식(async)입니다, 멈추지 않는다는거죠 (Non-blocking). Node.js 기반 서버는 API가 실행되었을때, 데이터를 반환할때까지 기다리지 않고 다음 API 를 실행합니다. 그리고 이전에 실행했던 API가 결과값을 반환할 시, Node.js의 이벤트 알림 메커니즘을 통해 결과값을 받아옵니다.
  - 빠른 속도: 구글 크롬(Google Chrome)의 V8 자바스크립트 엔진(JavaScript Engine)을 사용하여 빠른 코드 실행을 제공합니다.
  - 단일 쓰레드와 뛰어난 확장성: Node.js는 이벤트 루프와 함께 단일 쓰레드 모델을 사용합니다. 이벤트 메커니즘은 서버가 멈추지않고 반응하도록 해주어 서버의 확장성을 키워줍니다. 반면, 아파치(Apache)같은 일반적인 웹서버는 요청을 처리하기 위하여 제한된 쓰레드를 생성합니다. Node.js 는 쓰레드를 한개만 사용하고 아파치(Apache)같은 웹서버보다 훨씬 많은 요청을 처리할 수 있습니다.

2. 자바스크립트 엔진 vs 자바스크립트 런타임

- 자바스크립트 엔진은 자바스크립트 코드를 실행하는 프로그램 혹은 인터프리터를 말합니다
- 자바스크립트 런타임환경은 프로그램에 실행동안 사용 가능한 내장된 라이브러리를 제공합니다. window 객체나 DOM api를 사용하는 것이 포함됨

3. node.js 디버깅

- [출처](https://www.a-mean-blog.com/ko/blog/%EB%8B%A8%ED%8E%B8%EA%B0%95%EC%A2%8C/_/node-js-%EB%94%94%EB%B2%84%EA%B9%85-%EB%B0%A9%EB%B2%95)

## React

1. react 컴포넌트를 나누는 기준

- 리액트의 가장 큰 특징은 컴포넌트 단위의 상태관리는 Virtual DOM을 이용해 뷰의 변화를 부분적이고 효율적으로 적용한다.
- 변화하는 뷰와 그를 제어하는 상태를 하나의 단위로 묶어서 컴포넌트로 관리해야함

2. 전역 상태 관리

- redux, mobx 이용
- contest api : 여러 개의 props를 용이하게 다른 컴포넌트에 보내는 방법

3. hoc이 뭘까?

- [Higher Order Component](https://velopert.com/3537)

## git

1. 브랜칭전략

- git flow
  - master: 제품 배포 브랜치입니다
  - develop : 개발 브랜치로 개발자들이 이 브랜치를 기준으로 각자 작업한 기능들을 합(Merge)칩니다.
  - feature : 단위 기능을 개발하는 브랜치로 기능 개발이 완료되면 develop 브랜치에 합칩니다.
  - release : 배포를 위해 master 브랜치로 보내기 전에 먼저 QA(품질검사)를 하기위한 브랜치 입니다.
  - hotfix : master 브랜치로 배포를 했는데 버그가 생겼을 떄 긴급 수정하는 브랜치 입니다.
- develop - feature 브렌치간 머지 : Squash and Merge가 유용합니다. 일반적으로 머지 후에 feature 브렌치를 삭제해버리는 점을 떠올려 보면, feature 브렌치의 커밋 히스토리를 모두 develop 브렌치에 직접 연관 지어 남길 필요가 없습니다.
- master - develop 브렌치간 머지 : Rebase and Merge가 유용합니다. develop의 내용을 master에 추가할 때에는 별도의 새로운 커밋을 생성할 이유가 없기 때문입니다.
- hotfix - develop, hotfix - master 브렌치간 머지 : Merge 또는 Squash and Merge 모두 유용합니다.

2. rebase와 merge 비교: 커밋 메시지 기준

- Merge는 branch를 통합하는 것이고, Rebase는 branch의 base를 옮긴다는 개념의 차이가 있습니다.
- rebase를 하고 merge할 경우 커밋 히스토리가 깔끔해진다.