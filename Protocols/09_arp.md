# ARP와 MAC 주소 확인

## ARP란?

ARP(Address Resolution Protocol)는 IPv4 over Ethernet에서 같은 링크에 있는 장비의 **IPv4 주소에 대응하는 MAC 주소를 알아내는 프로토콜**이다.

```text
알고 있는 주소: IPv4 주소
알아낼 주소  : MAC 주소
```

IP와 MAC을 서로 변환하는 모든 절차를 ARP라고 부르는 것은 아니다. 여기서는 IPv4 주소를 기준으로 MAC 주소를 확인하는 과정을 말한다.

## Request와 Reply

| 구분 | 일반적인 전달 방식 | 내용 |
|------|--------------------|------|
| ARP Request | Broadcast | 이 IPv4 주소를 사용하는 장비의 MAC 주소를 요청 |
| ARP Reply | Unicast | 요청한 장비에 자신의 MAC 주소를 응답 |

일반적인 주소 확인 요청은 Ethernet 브로드캐스트 주소인 `FF:FF:FF:FF:FF:FF`로 보낸다. 따라서 ARP 전체가 항상 브로드캐스트로만 동작하는 것은 아니다.

## 같은 LAN에서 확인하는 예시

다음 두 PC는 같은 스위치와 VLAN에 연결되어 있고, `/24`로 설정되어 있다고 가정한다. PC 1의 ARP 캐시에는 아직 PC 2의 정보가 없다.

| 장비 | IPv4 주소 | MAC 주소 |
|------|-----------|----------|
| PC 1 | `211.253.120.10/24` | `02:00:00:00:00:10` |
| PC 2 | `211.253.120.12/24` | `02:00:00:00:00:12` |

IP 주소는 제공된 학습 예시이며, 실제 실습에서는 사설 주소를 사용한다.

### 1. PC 1이 요청 전송

PC 1은 `211.253.120.12`로 데이터를 보내기 위해 ARP Request를 보낸다.

```text
PC 1: "211.253.120.12를 사용하는 장비가 누구야?"
    ↓ ARP Request / Broadcast
Switch
    ↓ 같은 VLAN에서 수신 포트를 제외한 포트들로 전달
PC 2를 포함한 같은 브로드캐스트 도메인의 장비들
```

### 2. PC 2가 응답 전송

PC 2는 요청에 적힌 IP 주소가 자신의 주소이므로 ARP Reply를 보낸다.

```text
PC 2: "그 IP는 나야. 내 MAC 주소는 02:00:00:00:00:12야."
    ↓ ARP Reply / Unicast
Switch
    ↓ PC 1의 MAC 주소에 해당하는 포트로 전달
PC 1
```

일반적인 학습 스위치는 앞선 요청의 출발지 MAC 주소를 보고 PC 1이 연결된 포트를 학습한다. 스위치가 ARP 질의에 대신 답하는 것은 아니다.

### 3. ARP 캐시에 저장하고 데이터 전송

PC 1은 확인한 IP와 MAC의 대응 관계를 ARP 캐시에 저장한다.

```text
211.253.120.12 → 02:00:00:00:00:12
```

이제 해당 MAC 주소를 목적지로 지정한 Ethernet 프레임을 만들어 전송할 수 있다. 유효한 캐시 정보가 있으면 전송할 때마다 ARP Request를 다시 보낼 필요는 없다.

## 다른 네트워크로 보낼 때

목적지가 다른 네트워크라면 원격 서버의 MAC 주소를 ARP로 직접 찾지 않는다. 경로에 따라 선택한 다음 홉, 일반적으로 기본 게이트웨이의 MAC 주소를 확인한다.

ARP Request는 라우터를 넘어 원격 네트워크까지 전달되지 않는다. IPv6에서는 ARP 대신 Neighbor Discovery를 사용한다.

## 참고

- [RFC 826 — Ethernet Address Resolution Protocol](https://www.rfc-editor.org/rfc/rfc826)
- [LAN과 WAN의 데이터 전달 과정](10_lan_wan_data_delivery.md)
