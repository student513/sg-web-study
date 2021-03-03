1. HTTP란? HTTP(hypertext transfer protocol)

   - 텍스트 기반의 통신 규약으로, 인터넷에서 데이터를 주고 받을 수 있는 프로토콜이다. 클라이언트와 서버가 요청과 응답을 주고 받습니다.
   - 통신상대를 확인하지 않기 때문에 위장이 가능합니다. 의미 없는 리퀘스트도 받기 때문에 DDos 공격에도 취약합니다.
   - 서버나 클라이언트에서 보낸 정보의 정확성을 증명할 수 없기 때문에 보안에 취약합니다.

2. HTTPS란?

   - HTTP + Secure.
   - HTTPS를 사용하여 전송되는 데이터는 SSL를 통해 보호된다.
   - 통신상대를 확인하는 증명서를 이용합니다
   - HTTP가 통신하는 소켓부분을 SSL로 대체하는 것 뿐입니다.
   - 통신 자체를 암호화 SSL(Secure Socket Layer) or TLS(Transport Layer Security)라는 다른 프로토콜을 조합함으로써 HTTP 의 통신 내용을 암호화할 수 있다.
   - HTTP 는 원래 TCP 와 직접 통신했지만, HTTPS 에서 HTTP 는 SSL 과 통신하고 SSL 이 TCP 와 통신 하게 된다

3. TCP는?

   - transport layer의 프로토콜이다
   - connection oriented + reliable
   - ACK와 시퀀스 넘버를 주고받으며 flow control과 error control을 한다.
   - 신뢰성 과 순차적인 전달

4. UDP는?

   - transport layer의 프로토콜이다
   - connectionless + unreliable.
   - 실시간 프로세스 통신에 사용되며, 간단하고 속도가 빠르다
   - flow control, error control을 하지 않는다.
   - UDP를 사용한 것들에는 DNS가 있다. 어떤 호스트 네임의 IP 주소를 찾을 필요가 있는 프로그램은, DNS 서버로 호스트 네임을 포함한 UDP 패킷을 보낸다. 이 서버는 호스트의 IP 주소를 포함한 UDP 패킷으로 응답한다.

5. 3 Way Handshaking

   - TCP에서 connection을 형성하기 위한 메커니즘
   - 클라이언트가 SYN 세그먼트를 보낸다
   - 서버는 SYN, ACK를 보낸다
   - 클라이언트는 ACK를 보낸다
   - 세 단계를 거치면 통신 준비 완료

6. 방화벽이란?

   - 특정 규칙에 따라 접근하려는 특정 네트워크를 제한하는 시스템. IP, 포트를 사용하여 제한하는 방식 등 다양한 규칙이 있다.

7. 레이어별 address

   - transport layer: port
   - network layer: ip address
   - datalink layer: mac address

8. 우리가 Chrome 을 실행시켜 주소창에 특정 URL 값을 입력시키면 어떤 일이 일어나는가?

   1. url 에 입력된 값을 브라우저 내부에서 결정된 규칙에 따라 그 의미를 조사한다.
   2. 조사된 의미에 따라 HTTP Request 메시지를 만든다.
   3. 만들어진 메시지를 웹 서버로 전송한다.

9. HTTP의 GET과 POST
   - GET 방식은 요청하는 데이터가 HTTP Request Message의 Header 부분의 url 에 담겨서 전송된다.
     때문에 url 상에 ? 뒤에 데이터가 붙어 request 를 보내게 되는 것이다.
     이러한 방식은 url 이라는 공간에 담겨가기 때문에 전송할 수 있는 데이터의 크기가 제한적이다.
     또 보안이 필요한 데이터에 대해서는 데이터가 그대로 url 에 노출되므로 GET방식은 적절하지 않다
     GET 은 가져오는 것이다. 서버에서 어떤 데이터를 가져와서 보여준다거나 하는 용도이지 서버의 값이나 상태 등을 변경하지 않는다.
   - POST 방식의 request 는 HTTP Message의 Body 부분에 데이터가 담겨서 전송된다.
     데이터 크기가 GET 방식보다 크고 보안면에서 낫다.
     POST 는 서버의 값이나 상태를 변경하기 위해서 또는 추가하기 위해서 사용된다.
