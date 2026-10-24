# Network Study

네트워크의 기본 개념과 TCP/IP 프로토콜을 학습하고, 직접 이해한 내용을 정리하는 저장소입니다.

단순한 개념 암기보다 **데이터가 네트워크를 통해 어떻게 전달되는지 이해하는 것**을 목표로 공부하고 있습니다.

## Goals

- 네트워크의 기본 구조와 동작 원리 이해
- TCP/IP 및 OSI 계층의 역할 이해
- IP Address, MAC Address, Port의 역할 이해
- Switch, Router, Gateway의 동작 원리 학습
- 주요 네트워크 프로토콜 학습
- Packet Tracer와 Wireshark를 활용한 실습
- Linux Server 및 AWS 학습에 필요한 네트워크 기반 지식 습득

## Contents

### Network Basic
- Network
- LAN / WAN
- Network Media
- Hub / Switch / Router
- Gateway
- Internet

추가 학습 정리:

- [네트워크 프로토콜의 규칙과 종류](Basic/05_network_protocol_types.md)
- [유니캐스트, 브로드캐스트, 멀티캐스트](Basic/06_network_transmission_methods.md)
- [MAC 주소와 IP 주소](Basic/07_mac_and_ip_address.md)
- [Ethernet 매체 표기와 케이블 종류](Basic/08_ethernet_media_standards.md)

### Protocols
- TCP/IP
- OSI 7 Layer
- Ethernet / MAC Address
- IPv4 / IPv6
- ARP / ICMP
- TCP / UDP
- HTTP / DNS / DHCP

주소와 데이터 전달 과정:

- [ARP와 MAC 주소 확인](Protocols/09_arp.md)
- [LAN과 WAN의 데이터 전달 과정](Protocols/10_lan_wan_data_delivery.md)
- [OSI와 TCP/IP 계층별 역할 비교](Protocols/11_osi_tcp_ip_comparison.md)
- [주요 서비스와 포트 번호](Protocols/12_common_service_ports.md)
- [IPv4 주소 체계와 서브넷 마스크](Protocols/13_ipv4_addressing.md)
- [IPv4 서브네팅](Protocols/14_subnetting.md)

### Lab
- IP 및 Gateway 설정
- Ping Test
- Packet Tracer
- Wireshark Packet Analysis
- Linux Network 실습

## Environment

- Windows 11
- Ubuntu 24.04 LTS
- VMware Workstation
- Cisco Packet Tracer
- Wireshark
- Visual Studio Code

## Learning Direction

네트워크를 독립적인 이론으로만 공부하지 않고 다음 분야와 연결하여 학습하고 있습니다.

**Network → Linux Server → Docker → AWS / Cloud**

앞으로 실제 서버 및 클라우드 환경에서 네트워크를 직접 구성하고, 문제가 발생했을 때 통신 구조를 기반으로 원인을 분석할 수 있는 역량을 키우는 것이 목표입니다.