# 네트워크 데이터 패킷

## 데이터 패킷(Packet)이란?

인터넷에서는 데이터를 작은 단위로 나누어 전송한다.

이렇게 전송되는 데이터의 단위를 **패킷(Packet)** 이라고 한다.

---

## 프레임(Frame)이란?

프레임(Frame)은 **데이터 링크 계층(Data Link Layer)** 에서 사용하는 데이터 전송 단위이다.

패킷을 전송하기 위해 이더넷 헤더와 트레일러가 추가된 형태이다.

---

# 인터넷 전송 데이터 패킷 분석

## 1. 데이터 링크 계층 (Data Link Layer)

- 이더넷(Ethernet) 프레임
- 송신 MAC 주소
- 수신 MAC 주소

---

## 2. 네트워크 계층 (Network Layer)

- IPv4 패킷
- 송신 IP 주소
- 수신 IP 주소

---

## 3. 전송 계층 (Transport Layer)

- TCP 프로토콜
- 송신 Port 번호
- 수신 Port 번호

---

## 4. 응용 계층 (Application Layer)

- URL 주소
- 웹 브라우저에서 요청한 데이터

---

# 인터넷 접속 여부 패킷 분석

## PING 테스트

- PING 명령을 이용하여 인터넷 연결 여부를 확인할 수 있다.
- PING은 **ICMP(Internet Control Message Protocol)** 를 사용하여 목적지와의 통신 가능 여부를 확인한다.