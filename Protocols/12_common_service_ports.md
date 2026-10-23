# 주요 서비스와 포트 번호

## Port의 역할

IP 주소로 목적지 인터페이스를 구분하고, TCP나 UDP의 포트 번호로 해당 호스트의 서비스와 통신을 구분한다.

```text
목적지 IP   → 어느 호스트로 보낼 것인가?
목적지 Port → 어느 서비스로 보낼 것인가?
```

TCP와 UDP는 각각 별도의 포트 공간을 사용한다. 같은 번호라도 전송 프로토콜이 다르면 서로 다른 통신으로 구분한다.

## 자주 사용하는 서비스

아래는 기본 포트와 일반적인 사용 방식을 정리한 것이다. 실제 서비스는 설정에 따라 다른 포트를 사용할 수도 있다.

| 서비스 | 일반적인 전송 프로토콜 | 기본 포트 | 용도 |
|--------|------------------------|-----------|------|
| HTTP | TCP(일반적인 HTTP/1.1) | 80 | 웹 요청과 응답 |
| HTTPS | TCP(HTTP/1.1, HTTP/2), UDP 기반 QUIC(HTTP/3) | 443 | 암호화된 웹 통신 |
| SSH | TCP | 22 | 암호화된 원격 접속 |
| Telnet | TCP | 23 | 평문 기반 원격 접속 |
| DNS | UDP, TCP | 53 | 도메인 이름 조회 등 |
| DHCP(IPv4) | UDP | 서버 67, 클라이언트 68 | IP 주소와 네트워크 설정 할당 |
| SNMP | 주로 UDP | 161 | 네트워크 장비 정보 조회·관리 |
| SNMP 알림 | 주로 UDP | 162 | Trap·Inform 등 알림 수신 |

DNS는 UDP만 사용하는 프로토콜이 아니다. 일반 질의에도 TCP를 사용할 수 있으며, UDP 응답이 잘린 경우 TCP로 다시 질의하거나 영역 전송에 TCP를 사용하는 경우가 있다. DNS over TLS나 DNS over HTTPS는 위의 일반 DNS와 별도로 구분한다.

## 요청과 응답에서의 포트

클라이언트는 일반적으로 임시 포트를 출발지로 사용하고, 서버의 서비스 포트를 목적지로 지정한다.

```text
HTTP 요청
클라이언트 IP:임시 포트 → 서버 IP:80

HTTP 응답
서버 IP:80 → 클라이언트 IP:임시 포트
```

포트 번호만으로 서비스가 무엇인지 확정할 수는 없다. 어떤 전송 프로토콜을 사용하는지와 실제 서비스 설정도 함께 확인해야 한다.

## 참고

- [IANA — Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
- [RFC 7766 — DNS Transport over TCP](https://www.rfc-editor.org/rfc/rfc7766)
- [RFC 9114 — HTTP/3](https://httpwg.org/specs/rfc9114.html)
- [전송 계층](07_Transport_layer.md)
- [응용 계층](08_Application_layer.md)
