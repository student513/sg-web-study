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

5. setInterval과 setTimeOut의 차이?

- setInterval
  - 일정 간격으로 함수 실행
  - 실행중 다른 setInterval로 인해 함수가 호출되면 기존에 실행되던 함수는 종료된다.
- setTimeout
  - 일정 시간 후 함수 한번 호출
  - 실행중 다른 setTimeout로 인해 함수가 호출되도 기존에 실행된 함수에 영향을 주지 않는다.

6. localStorage vs sessionStorage

- sessionStorage: 브라우저에서 같은 웹사이트를 여러 탭이나 창에 띄우면, 여러 개의 세션 스토리지에 데이터가 서로 격리되어 저장되며, 각 탭이나 창이 닫힐 때 저장해 둔 데이터도 함께 소멸합니다.
- localStorage: 로컬 스토리지의 경우 여러 탭이나 창 간에 데이터가 서로 공유되며 탭이나 창을 닫아도 데이터는 브라우저에 그대로 남아 있습니다.
- [출처](https://www.daleseo.com/js-web-storage/)

7. web cache

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
