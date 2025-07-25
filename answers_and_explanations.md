# 정답 및 해설

이 문서는 각 장의 확인 문제에 대한 정답과 해설을 제공합니다.

## 목차
- [Chapter 01 컴퓨터 네트워크 시작하기](#chapter-01-컴퓨터-네트워크-시작하기)
  - [01-1 컴퓨터 네트워크를 알아야 하는 이유](#01-1-컴퓨터-네트워크를-알아야-하는-이유)
  - [01-2 네트워크 거시적으로 살펴보기](#01-2-네트워크-거시적으로-살펴보기)
  - [01-3 네트워크 미시적으로 살펴보기](#01-3-네트워크-미시적으로-살펴보기)
- [Chapter 02 물리 계층과 데이터 링크 계층](#chapter-02-물리-계층과-데이터-링크-계층)
  - [02-1 이더넷](#02-1-이더넷)
  - [02-2 NIC와 케이블](#02-2-nic와-케이블)
  - [02-3 허브](#02-3-허브)
  - [02-4 스위치](#02-4-스위치)
- [Chapter 03 네트워크 계층](#chapter-03-네트워크-계층)
  - [03-1 LAN을 넘어서는 네트워크 계층](#03-1-lan을-넘어서는-네트워크-계층)
  - [03-2 IP 주소](#03-2-ip-주소)
  - [03-3 라우팅](#03-3-라우팅)
- [Chapter 04 전송 계층](#chapter-04-전송-계층)
  - [04-1 전송 계층 개요: IP의 한계와 포트](#04-1-전송-계층-개요-ip의-한계와-포트)
  - [04-2 TCP와 UDP](#04-2-tcp와-udp)
  - [04-3 TCP의 오류·흐름·혼잡 제어](#04-3-tcp의-오류흐름혼잡-제어)
- [Chapter 05 응용 계층](#chapter-05-응용-계층)
  - [05-1 DNS와 자원](#05-1-dns와-자원)
  - [05-2 HTTP](#05-2-http)
  - [05-3 HTTP 헤더와 HTTP 기반 기술](#05-3-http-헤더와-http-기반-기술)
- [Chapter 06 실습으로 복습하는 네트워크](#chapter-06-실습으로-복습하는-네트워크)
  - [06-1 와이어샤크 설치 및 사용법](#06-1-와이어샤크-설치-및-사용법)
  - [06-2 와이어샤크를 통한 프로토콜 분석](#06-2-와이어샤크를-통한-프로토콜-분석)
- [Chapter 07 네트워크 심화](#chapter-07-네트워크-심화)
  - [07-1 안정성을 위한 기술](#07-1-안정성을-위한-기술)
  - [07-2 안전성을 위한 기술](#07-2-안전성을-위한-기술)
  - [07-3 무선 네트워크](#07-3-무선-네트워크)

## Chapter 01 컴퓨터 네트워크 시작하기

### 01-1 컴퓨터 네트워크를 알아야 하는 이유

#### 문제 1
**문제**: 인터넷을 '네트워크의 네트워크'라고 부르는 이유는 무엇인가요?

**정답**: 수많은 작은 네트워크들이 서로 연결되어 하나의 거대한 네트워크를 형성하기 때문에

**해설**: 인터넷은 전 세계의 수많은 작은 네트워크들이 서로 연결되어 하나의 거대한 네트워크를 형성하고 있습니다. 이러한 구조 때문에 '네트워크의 네트워크'라고 불립니다. 각 네트워크는 독립적으로 운영되지만, 표준화된 프로토콜(TCP/IP)을 통해 서로 통신할 수 있습니다.

#### 문제 2
**문제**: 다음 중 웹 개발자가 프로그램을 만드는 업무에서 네트워크 지식을 활용하는 경우가 아닌 것은?

**정답**: 데이터베이스 스키마 설계

**해설**: 데이터베이스 스키마 설계는 주로 데이터 모델링과 관련된 작업으로, 네트워크 지식보다는 데이터베이스 설계 원칙과 정규화 이론 등의 지식이 더 중요합니다. 반면, API 설계 최적화, 웹 애플리케이션 보안 강화, 네트워크 성능 최적화는 모두 네트워크 지식을 직접적으로 활용하는 업무입니다.

#### 문제 3
**문제**: 웹 개발자에게 네트워크 지식이 중요한 이유를 자신의 경험이나 예시와 함께 설명해보세요.

**모범 답안**: 웹 애플리케이션은 본질적으로 네트워크를 통해 작동하므로, 네트워크의 특성과 제약을 이해하는 것이 효율적이고 안정적인 애플리케이션을 개발하는 데 필수적입니다. 예를 들어, 네트워크 지연 시간을 고려한 비동기 처리, 대역폭 제한을 고려한 자원 최적화, 네트워크 보안 취약점에 대응하는 보안 조치 등이 중요합니다. 실제 개발 환경에서는 API 호출 최적화, 캐싱 전략 수립, CDN 활용, 네트워크 오류 처리 등 다양한 상황에서 네트워크 지식이 필요합니다.

### 01-2 네트워크 거시적으로 살펴보기

#### 문제 1
**문제**: 다음 중 LAN(Local Area Network)의 특징으로 옳지 않은 것은?

**정답**: 넓은 지리적 범위

**해설**: LAN은 제한된 지역 내에서 구성된 네트워크로, 일반적으로 한 건물이나 캠퍼스 내에 구축됩니다. LAN의 특징은 높은 데이터 전송 속도, 낮은 지연 시간, 제한된 지리적 범위, 단일 조직에 의한 소유 및 관리 등입니다. 넓은 지리적 범위는 WAN(Wide Area Network)의 특징입니다.

#### 문제 2
**문제**: 회선 교환 방식과 패킷 교환 방식의 차이점으로 옳은 것은?

**정답**: 회선 교환은 통신 전에 경로를 설정하고, 패킷 교환은 각 패킷이 독립적으로 경로를 찾아간다.

**해설**: 회선 교환 방식은 통신을 시작하기 전에 송신자와 수신자 간에 전용 통신 경로(회선)를 설정하고, 통신이 끝날 때까지 이 경로를 독점적으로 사용합니다. 반면, 패킷 교환 방식은 데이터를 패킷이라는 작은 단위로 나누어 각 패킷이 독립적으로 목적지까지 전송됩니다. 회선 교환은 전통적인 전화망에서 주로 사용되고, 패킷 교환은 인터넷에서 주로 사용됩니다.

#### 문제 3
**문제**: 네트워크에서 유니캐스트, 브로드캐스트, 멀티캐스트의 차이점을 설명하고, 각각의 사용 예시를 들어보세요.

**모범 답안**: 유니캐스트는 하나의 송신자가 하나의 특정 수신자에게 데이터를 전송하는 1:1 통신 방식입니다. 웹 브라우징, 이메일 전송, 파일 다운로드 등에 사용됩니다. 브로드캐스트는 하나의 송신자가 네트워크 내의 모든 호스트에게 데이터를 전송하는 1:모두 통신 방식입니다. ARP 요청, DHCP 요청, 라우팅 정보 업데이트 등에 사용됩니다. 멀티캐스트는 하나의 송신자가 특정 그룹에 속한 다수의 수신자에게 데이터를 전송하는 1:다수 통신 방식입니다. IPTV, 화상 회의, 소프트웨어 업데이트 배포 등에 사용됩니다. 유니캐스트는 특정 수신자만 데이터를 받고, 브로드캐스트는 네트워크 내 모든 호스트가 데이터를 받으며, 멀티캐스트는 특정 그룹에 속한 호스트만 데이터를 받는다는 점에서 차이가 있습니다.

### 01-3 네트워크 미시적으로 살펴보기

#### 문제 1
**문제**: 다음 중 OSI 모델의 7계층을 올바르게 나열한 것은?

**정답**: 물리, 데이터 링크, 네트워크, 전송, 세션, 표현, 응용

**해설**: OSI 모델은 국제표준화기구(ISO)에서 개발한 7계층 모델로, 아래에서 위로 물리 계층, 데이터 링크 계층, 네트워크 계층, 전송 계층, 세션 계층, 표현 계층, 응용 계층 순으로 구성됩니다. 각 계층은 특정 기능을 담당하며, 하위 계층은 상위 계층에 서비스를 제공합니다. 물리 계층은 비트 단위의 데이터 전송을, 데이터 링크 계층은 프레임 단위의 신뢰성 있는 전송을, 네트워크 계층은 패킷 라우팅을, 전송 계층은 종단 간 통신을, 세션 계층은 연결 관리를, 표현 계층은 데이터 형식 변환을, 응용 계층은 사용자 인터페이스와 네트워크 서비스를 제공합니다. TCP/IP 모델은 4계층으로 구성되어 있으며, 네트워크 인터페이스, 인터넷, 전송, 응용 계층으로 구성됩니다.

#### 문제 2
**문제**: 캡슐화 과정에서 데이터에 추가되는 것은?

**정답**: 헤더와 때로는 트레일러가 추가된다

**해설**: 캡슐화(Encapsulation)는 상위 계층에서 하위 계층으로 데이터가 전달될 때 각 계층에서 해당 계층의 제어 정보를 데이터에 추가하는 과정입니다. 이 제어 정보는 주로 헤더 형태로 데이터 앞에 추가되지만, 데이터 링크 계층과 같은 일부 계층에서는 트레일러도 데이터 뒤에 추가됩니다. 예를 들어, 이더넷 프레임은 헤더(목적지 MAC 주소, 출발지 MAC 주소, 타입/길이 필드 등)와 트레일러(FCS, Frame Check Sequence)를 모두 포함합니다. 헤더에는 주소 지정, 오류 검출, 프로토콜 식별 등의 정보가 포함되며, 트레일러에는 주로 오류 검출 코드가 포함됩니다. 역캡슐화 과정에서는 이러한 헤더와 트레일러가 제거되어 원래의 데이터만 상위 계층으로 전달됩니다.

#### 문제 3
**문제**: TCP/IP 모델의 전송 계층에서 사용되는 PDU의 이름은?

**정답**: 세그먼트(TCP) 또는 데이터그램(UDP)

**해설**: PDU(Protocol Data Unit)는 각 계층에서 데이터 단위를 지칭하는 용어입니다. TCP/IP 모델의 전송 계층에서는 프로토콜에 따라 PDU의 이름이 다릅니다. TCP(Transmission Control Protocol)를 사용할 경우 PDU는 '세그먼트(Segment)'라고 부르고, UDP(User Datagram Protocol)를 사용할 경우 '데이터그램(Datagram)'이라고 부릅니다. 세그먼트와 데이터그램은 모두 출발지 포트, 목적지 포트, 체크섬 등의 헤더 정보를 포함하지만, TCP 세그먼트는 신뢰성 있는 전송을 위한 시퀀스 번호, 확인 응답 번호 등의 추가 필드를 포함합니다. 다른 계층의 PDU로는 응용 계층의 데이터/메시지, 인터넷 계층의 패킷, 네트워크 인터페이스 계층의 프레임이 있습니다.

#### 문제 4
**문제**: 네트워크 성능을 측정하는 지표 중, 단위 시간당 실제로 전송되는 데이터의 양을 나타내는 것은?

**정답**: 처리율

**해설**: 처리율(Throughput)은 단위 시간당 실제로 네트워크를 통해 전송되는 데이터의 양을 의미합니다. 일반적으로 비트 단위로 측정되며, bps(bits per second)로 표현됩니다. 처리율은 실제 네트워크 성능을 나타내는 중요한 지표로, 이론적인 최대 전송 속도인 대역폭(Bandwidth)과는 구별됩니다. 대역폭이 네트워크가 처리할 수 있는 최대 데이터 전송 속도를 의미한다면, 처리율은 실제로 전송되는 데이터의 양을 의미합니다. 처리율은 네트워크 혼잡, 프로토콜 오버헤드, 하드웨어 제한 등 다양한 요인에 의해 대역폭보다 낮을 수 있습니다. 지연 시간(Latency)은 데이터가 출발지에서 목적지까지 도달하는 데 걸리는 시간을, 패킷 손실(Packet Loss)은 전송 중 손실되는 패킷의 비율을 나타내는 지표입니다.

#### 문제 5
**문제**: OSI 모델과 TCP/IP 모델의 가장 큰 차이점은?

**정답**: OSI 모델은 7계층, TCP/IP 모델은 4계층으로 구성된다

**해설**: OSI 모델과 TCP/IP 모델의 가장 큰 차이점은 계층의 수와 구성입니다. OSI 모델은 7개의 계층(물리, 데이터 링크, 네트워크, 전송, 세션, 표현, 응용)으로 구성되어 있는 반면, TCP/IP 모델은 4개의 계층(네트워크 인터페이스, 인터넷, 전송, 응용)으로 구성되어 있습니다. TCP/IP 모델의 네트워크 인터페이스 계층은 OSI 모델의 물리 계층과 데이터 링크 계층에 해당하고, 인터넷 계층은 네트워크 계층에, 전송 계층은 전송 계층에, 응용 계층은 세션, 표현, 응용 계층을 포함합니다. OSI 모델은 개념적이고 이론적인 모델로 실제 구현보다는 네트워크 통신을 이해하는 데 도움을 주는 반면, TCP/IP 모델은 실제 인터넷에서 사용되는 프로토콜 스택을 기반으로 합니다. 두 모델 모두 계층적 접근 방식을 통해 네트워크 통신의 복잡성을 관리하고, 각 계층이 독립적으로 발전할 수 있도록 합니다.

## Chapter 02 물리 계층과 데이터 링크 계층

### 02-1 이더넷

#### 문제 1
**문제**: 다음 중 이더넷 프레임의 구성 요소가 아닌 것은?

**정답**: IP 주소

**해설**: 이더넷 프레임은 데이터 링크 계층에서 사용되는 PDU로, 프리앰블, 수신지 MAC 주소, 송신지 MAC 주소, 타입/길이, 데이터, FCS(Frame Check Sequence)로 구성됩니다. IP 주소는 네트워크 계층(OSI 모델의 3계층)에서 사용되는 주소로, 이더넷 프레임 자체에는 포함되지 않습니다. 이더넷 프레임에는 데이터 링크 계층에서 사용하는 MAC 주소만 포함됩니다. IP 주소는 이더넷 프레임의 데이터 부분에 포함된 IP 패킷 내에 존재합니다.

#### 문제 2
**문제**: MAC 주소의 크기는 얼마인가요?

**정답**: 6바이트(48비트)

**해설**: MAC(Media Access Control) 주소는 네트워크 인터페이스 카드(NIC)에 할당된 고유 식별자로, 6바이트(48비트) 크기를 가집니다. MAC 주소는 일반적으로 16진수로 표현되며, 예를 들어 `00:1A:2B:3C:4D:5E`와 같은 형태를 가집니다. 처음 3바이트는 제조사를 식별하는 OUI(Organizationally Unique Identifier)이고, 나머지 3바이트는 제조사가 할당한 고유 번호입니다. MAC 주소는 데이터 링크 계층에서 장치를 식별하는 데 사용되며, 이더넷 프레임의 송신지와 수신지 주소 필드에 포함됩니다.

#### 문제 3
**문제**: 다음 중 이더넷 표준 표기법에서 '1000BASE-T'의 의미로 옳은 것은?

**정답**: 1Gbps 속도를 지원하는 기저대역 방식의 트위스티드 페어 케이블

**해설**: 이더넷 표준 표기법은 `<속도><전송 방식><매체 유형>`의 형식을 따릅니다. '1000BASE-T'에서 '1000'은 1000Mbps, 즉 1Gbps의 데이터 전송 속도를 의미합니다. 'BASE'는 기저대역(Baseband) 방식을 사용한다는 의미로, 디지털 신호를 변조 없이 직접 전송하는 방식입니다. 'T'는 트위스티드 페어(Twisted pair) 케이블을 사용한다는 의미입니다. 따라서 1000BASE-T는 1Gbps 속도로 기저대역 방식을 사용하며 트위스티드 페어 케이블을 통해 데이터를 전송하는 이더넷 표준입니다. 이는 기가비트 이더넷(Gigabit Ethernet)이라고도 불립니다.

#### 문제 4
**문제**: 이더넷과 토큰 링의 가장 큰 차이점은 무엇인가요?

**정답**: 이더넷은 CSMA/CD 방식을 사용하고, 토큰 링은 토큰 기반 접근 제어를 사용한다

**해설**: 이더넷과 토큰 링의 가장 큰 차이점은 매체 접근 제어(MAC) 방식입니다. 이더넷은 CSMA/CD(Carrier Sense Multiple Access with Collision Detection) 방식을 사용합니다. 이 방식에서는 장치가 전송 전에 매체가 사용 중인지 확인하고(Carrier Sense), 사용 중이지 않으면 데이터를 전송합니다. 여러 장치가 동시에 전송을 시도할 경우 충돌이 발생할 수 있으며, 충돌이 감지되면(Collision Detection) 장치들은 무작위 시간 동안 대기한 후 재전송을 시도합니다. 반면, 토큰 링은 토큰 기반 접근 제어 방식을 사용합니다. 특별한 프레임인 '토큰'이 링을 순환하며, 토큰을 가진 장치만 데이터를 전송할 수 있습니다. 이 방식은 충돌이 발생하지 않도록 설계되어 있어, 이더넷의 CSMA/CD와 같은 충돌 감지 메커니즘이 필요하지 않습니다. 또한 토큰 링은 링 토폴로지를 사용하는 반면, 이더넷은 주로 스타 또는 버스 토폴로지를 사용합니다.

### 02-2 NIC와 케이블

#### 문제 1
**문제**: NIC의 주요 역할이 아닌 것은?

**정답**: IP 주소 할당 및 관리

**해설**: NIC(Network Interface Card, 네트워크 인터페이스 카드)는 컴퓨터가 네트워크에 연결될 수 있도록 하는 하드웨어 장치로, 물리 계층과 데이터 링크 계층의 기능을 담당합니다. NIC의 주요 역할에는 컴퓨터와 네트워크 매체 간의 물리적 연결 제공, 디지털 데이터와 네트워크 신호 간의 변환, MAC 주소 제공, 데이터 프레임의 생성 및 처리 등이 있습니다. 그러나 IP 주소 할당 및 관리는 NIC의 역할이 아니라 네트워크 계층(OSI 모델의 3계층)의 기능으로, 운영 체제나 DHCP와 같은 네트워크 프로토콜에 의해 수행됩니다. NIC는 MAC 주소(하드웨어 주소)를 가지고 있지만, IP 주소(논리 주소)는 소프트웨어적으로 할당되고 관리됩니다.

#### 문제 2
**문제**: 다음 중 트위스티드 페어 케이블에서 전선을 꼬아놓는 주된 이유는?

**정답**: 전자기 간섭(EMI)을 줄이기 위해

**해설**: 트위스티드 페어 케이블에서 전선을 꼬아놓는 주된 이유는 전자기 간섭(EMI, Electromagnetic Interference)을 줄이기 위함입니다. 두 개의 평행한 전선은 안테나처럼 작용하여 외부 전자기장의 영향을 받기 쉽습니다. 그러나 전선을 서로 꼬아놓으면 각 전선에 유도되는 노이즈가 서로 상쇄되어 신호의 품질이 향상됩니다. 이는 차동 신호 전송 방식과 함께 작용하여 외부 간섭에 대한 내성을 높이고, 크로스토크(인접한 전선 간의 간섭)를 줄이는 데 도움이 됩니다. 전선을 꼬는 것은 물리적 강도를 높이거나 데이터 전송 속도를 직접적으로 높이기 위한 것이 아니며, 케이블 제조 비용을 절감하는 것과도 관련이 없습니다.

#### 문제 3
**문제**: Cat 6 케이블과 Cat 5e 케이블의 주요 차이점은?

**정답**: Cat 6는 더 높은 대역폭(250MHz)을 지원하고, Cat 5e는 100MHz를 지원한다

**해설**: Cat 6(Category 6) 케이블과 Cat 5e(Category 5 enhanced) 케이블의 주요 차이점은 지원하는 대역폭입니다. Cat 6는 최대 250MHz의 대역폭을 지원하는 반면, Cat 5e는 100MHz의 대역폭을 지원합니다. 이러한 대역폭 차이로 인해 Cat 6는 1Gbps 속도를 100m 거리까지 지원하고, 10Gbps 속도를 55m까지 지원할 수 있습니다. 반면 Cat 5e는 1Gbps 속도를 100m까지 지원하지만, 10Gbps는 지원하지 않습니다. 또한 Cat 6는 더 엄격한 사양과 더 나은 노이즈 감소 기능을 갖추고 있어, 더 높은 품질의 신호 전송이 가능합니다. 두 케이블 모두 UTP(Unshielded Twisted Pair)와 STP(Shielded Twisted Pair) 버전으로 제공될 수 있으며, 둘 다 구리 케이블입니다. 광섬유 케이블은 완전히 다른 종류의 케이블입니다.

#### 문제 4
**문제**: 싱글 모드 광섬유 케이블과 멀티 모드 광섬유 케이블의 차이점으로 옳은 것은?

**정답**: 싱글 모드는 코어 직경이 작고 장거리 전송에 적합하며, 멀티 모드는 코어 직경이 크고 중단거리 전송에 적합하다

**해설**: 싱글 모드 광섬유 케이블과 멀티 모드 광섬유 케이블의 주요 차이점은 코어 직경과 빛의 전파 방식입니다. 싱글 모드 광섬유는 코어 직경이 매우 작아(일반적으로 8~10μm) 하나의 빛 경로(모드)만 허용합니다. 이는 레이저 다이오드를 광원으로 사용하며, 빛의 분산이 적어 장거리(수십 km) 전송에 적합합니다. 반면, 멀티 모드 광섬유는 코어 직경이 상대적으로 큰(일반적으로 50μm 또는 62.5μm) 케이블로, 여러 빛 경로를 허용합니다. LED를 광원으로 사용하며, 빛의 분산이 커서 비교적 짧은 거리(최대 2km 정도)의 전송에 적합합니다. 두 유형 모두 유리나 플라스틱 코어를 사용할 수 있으며, 둘 다 데이터 전송에 빛을 사용합니다. 또한 두 유형 모두 여러 장치를 연결하는 네트워크에 사용될 수 있습니다.

#### 문제 5
**문제**: 다음 중 광섬유 케이블의 장점이 아닌 것은?

**정답**: 설치 및 유지 관리가 쉽고 비용이 저렴하다

**해설**: 광섬유 케이블은 전자기 간섭에 영향을 받지 않고, 더 긴 거리 전송이 가능하며, 더 높은 대역폭을 제공하는 등 여러 장점이 있습니다. 그러나 설치 및 유지 관리가 쉽고 비용이 저렴하다는 것은 광섬유 케이블의 장점이 아닙니다. 오히려 광섬유 케이블은 구리 기반의 트위스티드 페어 케이블에 비해 설치가 더 복잡하고 비용이 높습니다. 광섬유 케이블은 특수한 장비와 기술이 필요하며, 케이블 자체의 가격도 더 비쌉니다. 또한 광섬유 케이블은 물리적 손상에 더 취약하여 유지 관리가 더 어려울 수 있습니다. 이러한 단점에도 불구하고, 광섬유 케이블은 높은 성능과 긴 거리 전송 능력 때문에 백본 네트워크, 장거리 통신, 고속 데이터 전송이 필요한 환경에서 널리 사용됩니다.

### 02-3 허브

#### 문제 1
**문제**: 다음 중 허브의 특징으로 옳지 않은 것은?

**정답**: 목적지 MAC 주소를 기반으로 트래픽을 필터링한다

**해설**: 허브는 물리 계층에서 동작하는 네트워크 장비로, 주소 개념이 없는 물리 계층의 특성상 목적지 MAC 주소를 기반으로 트래픽을 필터링하는 기능이 없습니다. 허브는 한 포트에서 수신한 데이터를 단순히 모든 다른 포트로 재전송하는 브로드캐스트 방식으로 작동합니다. 목적지 MAC 주소를 기반으로 트래픽을 필터링하는 것은 데이터 링크 계층에서 동작하는 스위치의 특징입니다. 허브는 수신된 신호를 모든 포트로 재전송하고, 물리 계층에서 동작하며, 하나의 콜리전 도메인을 형성한다는 특징을 가집니다.

#### 문제 2
**문제**: 콜리전 도메인에 대한 설명으로 옳은 것은?

**정답**: 충돌이 발생할 수 있는 네트워크 영역이다

**해설**: 콜리전 도메인(Collision Domain)은 네트워크에서 충돌이 발생할 수 있는 영역을 의미합니다. 이더넷 환경에서 두 장치가 동시에 데이터를 전송하면 신호가 충돌하여 데이터가 손상될 수 있습니다. 허브에 연결된 모든 장치는 동일한 콜리전 도메인에 속하므로, 한 장치가 데이터를 전송하는 동안 다른 장치는 전송을 대기해야 합니다. 브로드캐스트 도메인은 브로드캐스트 트래픽이 전파되는 영역으로, 콜리전 도메인과는 다른 개념입니다. IP 주소가 동일한 장치들의 집합은 서브넷을 의미하며, 라우터로 분리되는 네트워크 세그먼트는 브로드캐스트 도메인을 의미합니다.

#### 문제 3
**문제**: CSMA/CD 프로토콜에서 충돌이 감지된 후 장치들이 취하는 행동은?

**정답**: 무작위 시간 동안 대기한 후 재전송을 시도한다

**해설**: CSMA/CD(Carrier Sense Multiple Access with Collision Detection) 프로토콜에서 충돌이 감지되면, 각 장치는 무작위 시간 동안 대기한 후 재전송을 시도합니다. 이를 이진 지수 백오프(Binary Exponential Backoff) 알고리즘이라고 하며, 연속적인 충돌이 발생할 경우 대기 시간의 범위가 점점 길어집니다. 이 방식은 여러 장치가 동시에 재전송을 시도하여 다시 충돌이 발생할 확률을 줄이기 위한 것입니다. 충돌이 감지되면 즉시 데이터 전송을 중단하고, 재밍 신호(jamming signal)를 전송하여 다른 장치들에게 충돌이 발생했음을 알립니다. 네트워크 관리자에게 알림을 보내거나 다른 전송 매체로 전환하는 것은 CSMA/CD 프로토콜의 일부가 아닙니다.

#### 문제 4
**문제**: 허브 기반 네트워크의 단점이 아닌 것은?

**정답**: 설정이 복잡하고 관리가 어렵다

**해설**: 허브는 구조가 단순하고 설정이 간단하여 관리가 쉽다는 장점이 있습니다. 따라서 "설정이 복잡하고 관리가 어렵다"는 것은 허브 기반 네트워크의 단점이 아닙니다. 허브 기반 네트워크의 실제 단점으로는 네트워크 대역폭이 모든 장치에 의해 공유되어 성능이 제한되고, 한 장치의 과도한 트래픽이 전체 네트워크 성능에 영향을 미치며, 모든 트래픽이 모든 장치에 전송되어 보안 위험이 있다는 점 등이 있습니다. 이러한 단점들로 인해 현대 네트워크에서는 허브 대신 스위치가 널리 사용됩니다.

#### 문제 5
**문제**: 물리 계층에서 주소 개념이 없는 이유로 가장 적절한 것은?

**정답**: 물리 계층은 단순히 비트 전송에만 집중하기 때문에

**해설**: 물리 계층(Physical Layer)은 OSI 모델의 최하위 계층으로, 비트 단위의 데이터를 전기 신호, 광 신호, 또는 전파로 변환하여 전송하는 역할을 담당합니다. 물리 계층에서 주소 개념이 없는 이유는 이 계층의 주요 목적이 단순히 비트를 한 장치에서 다른 장치로 전송하는 것에 집중하기 때문입니다. 주소 지정과 같은 더 복잡한 기능은 상위 계층(데이터 링크 계층, 네트워크 계층)의 역할입니다. 물리 계층은 비트의 전송 방법, 전송 매체의 특성, 신호의 인코딩/디코딩 등에 관한 사항을 정의하며, 데이터의 출발지나 목적지를 식별하는 기능은 포함하지 않습니다. 주소 지정이 너무 복잡하거나, 물리 계층 장비의 처리 능력이 제한적이거나, 주소 지정이 대역폭을 소모한다는 이유는 물리 계층에서 주소 개념이 없는 본질적인 이유가 아닙니다.

### 02-4 스위치

#### 문제 1
**문제**: 다음 중 스위치와 허브의 차이점으로 옳지 않은 것은?

**정답**: 스위치는 네트워크 계층 주소를 사용하고, 허브는 데이터 링크 계층 주소를 사용한다

**해설**: 스위치는 데이터 링크 계층(OSI 모델의 2계층)에서 동작하며 MAC 주소(데이터 링크 계층 주소)를 사용하여 프레임을 전달합니다. 허브는 물리 계층(OSI 모델의 1계층)에서 동작하며 주소 개념 없이 수신된 신호를 모든 포트로 재전송합니다. 네트워크 계층 주소(IP 주소)는 라우터와 같은 네트워크 계층 장비에서 사용됩니다. 스위치는 데이터 링크 계층에서 동작하고 허브는 물리 계층에서 동작한다는 점, 스위치는 MAC 주소 기반으로 프레임을 전달하고 허브는 모든 포트로 신호를 재전송한다는 점, 스위치의 각 포트는 독립적인 콜리전 도메인을 형성하고 허브는 하나의 콜리전 도메인을 형성한다는 점은 모두 스위치와 허브의 올바른 차이점입니다.

#### 문제 2
**문제**: MAC 주소 학습에 대한 설명으로 옳은 것은?

**정답**: 목적지 MAC 주소가 테이블에 없으면 스위치는 해당 프레임을 수신 포트를 제외한 모든 포트로 전송한다

**해설**: 스위치의 MAC 주소 학습 과정에서, 목적지 MAC 주소가 MAC 주소 테이블에 없는 경우(즉, 스위치가 해당 MAC 주소가 어느 포트에 연결되어 있는지 모르는 경우) 스위치는 해당 프레임을 수신 포트를 제외한 모든 포트로 전송합니다. 이를 플러딩(flooding)이라고 합니다. 스위치는 소스 MAC 주소를 학습하여 MAC 주소 테이블을 구성하며, 목적지 MAC 주소만을 학습하는 것이 아닙니다. MAC 주소 테이블은 휘발성 메모리에 저장되므로 스위치가 재부팅되면 초기화됩니다. 브로드캐스트 프레임(목적지 MAC 주소가 FF:FF:FF:FF:FF:FF)은 항상 수신 포트를 제외한 모든 포트로 전달되며, MAC 주소 테이블을 참조하지 않습니다.

#### 문제 3
**문제**: VLAN의 주요 이점으로 옳지 않은 것은?

**정답**: 네트워크 장비의 수를 줄여 하드웨어 비용을 절감한다

**해설**: VLAN은 물리적 네트워크 구성과 독립적으로 논리적 네트워크 세그먼트를 생성하는 기술로, 네트워크 장비의 수를 직접적으로 줄이지는 않습니다. 오히려 VLAN을 구현하기 위해서는 VLAN을 지원하는 스위치와 같은 특정 네트워크 장비가 필요합니다. VLAN의 실제 이점으로는 브로드캐스트 트래픽을 제한하여 네트워크 효율성을 높이고, 서로 다른 VLAN 간의 통신을 제한하여 보안을 강화하며, 물리적 위치와 관계없이 논리적 그룹으로 장치를 구성할 수 있다는 점이 있습니다. VLAN은 물리적 네트워크 재구성 없이 논리적 네트워크 구성을 변경할 수 있어 관리 유연성을 제공하지만, 하드웨어 비용 절감이 주요 목적은 아닙니다.

#### 문제 4
**문제**: 포트 기반 VLAN과 MAC 기반 VLAN의 차이점으로 옳은 것은?

**정답**: MAC 기반 VLAN은 사용자가 네트워크 내에서 이동해도 VLAN 멤버십이 유지되지만, 포트 기반 VLAN은 포트가 변경되면 VLAN도 변경된다

**해설**: 포트 기반 VLAN은 스위치의 물리적 포트에 VLAN을 할당하는 방식으로, 장치가 연결된 포트가 변경되면 VLAN 멤버십도 변경됩니다. 반면, MAC 기반 VLAN은 장치의 MAC 주소를 기반으로 VLAN을 할당하므로, 장치가 네트워크 내에서 다른 포트로 이동해도 동일한 VLAN 멤버십을 유지합니다. 이는 사용자 이동성이 높은 환경에서 유용합니다. 포트 기반 VLAN은 정적 할당 방식이며, MAC 기반 VLAN은 동적 할당 방식입니다. 802.1Q 태깅은 VLAN 구현 방식과는 별개로, 트렁크 포트를 통해 여러 VLAN 트래픽을 전송할 때 사용되는 기술입니다. 포트 기반 VLAN과 MAC 기반 VLAN 모두 레이어 2 스위치에서 구현 가능하며, 레이어 3 스위치는 VLAN 간 라우팅을 위해 사용됩니다.

## Chapter 03 네트워크 계층

### 03-1 LAN을 넘어서는 네트워크 계층

#### 문제 1
**문제**: 다음 중 데이터 링크 계층의 한계로 옳지 않은 것은?

**정답**: IP 주소를 사용하여 장치를 식별하므로 주소 공간이 제한적이다

**해설**: 데이터 링크 계층은 IP 주소가 아닌 MAC 주소를 사용하여 장치를 식별합니다. IP 주소는 네트워크 계층에서 사용되는 주소 체계입니다. 데이터 링크 계층의 실제 한계로는 동일한 네트워크 내의 장치 간 통신만 지원한다는 점, MAC 주소가 네트워크 토폴로지에 따라 구조화되어 있지 않아 대규모 네트워크에서 효율적인 라우팅이 어렵다는 점, 브로드캐스트 트래픽이 동일한 네트워크 내 모든 장치에 전달되어 네트워크 규모가 커질수록 성능 저하가 발생한다는 점 등이 있습니다.

#### 문제 2
**문제**: IPv4와 IPv6의 차이점으로 옳은 것은?

**정답**: IPv4는 헤더 체크섬 필드가 있지만, IPv6는 이 필드가 제거되었다

**해설**: IPv4 헤더에는 헤더 체크섬 필드가 포함되어 있어 헤더의 무결성을 검증합니다. 그러나 IPv6에서는 이 필드가 제거되었습니다. 이는 상위 계층 프로토콜(TCP, UDP 등)이 이미 체크섬을 제공하고, 링크 계층에서도 오류 검출 기능을 제공하기 때문에 중복된 기능으로 판단되었기 때문입니다. 이로 인해 라우터에서의 처리 효율성이 향상되었습니다. 다른 주요 차이점으로는 IPv4는 32비트 주소를 사용하고 IPv6는 128비트 주소를 사용한다는 점, IPv6는 내장된 보안 기능(IPsec)을 제공하지만 IPv4는 추가적인 보안 프로토콜이 필요하다는 점, IPv6는 자동 주소 구성(SLAAC)을 지원하지만 IPv4는 주로 DHCP를 통한 동적 할당에 의존한다는 점 등이 있습니다.

#### 문제 3
**문제**: ARP의 주요 기능은 무엇인가요?

**정답**: IP 주소를 MAC 주소로 변환한다

**해설**: ARP(Address Resolution Protocol)는 IP 주소를 MAC 주소로 변환하는 프로토콜입니다. 네트워크 계층(OSI 모델의 3계층)에서 사용하는 IP 주소와 데이터 링크 계층(OSI 모델의 2계층)에서 사용하는 MAC 주소 간의 매핑을 제공합니다. 호스트가 같은 네트워크에 있는 다른 호스트와 통신하려면, 목적지 IP 주소는 알지만 MAC 주소를 모르는 경우 ARP를 사용하여 해당 IP 주소에 대응하는 MAC 주소를 찾습니다. ARP는 브로드캐스트 요청을 보내고, 해당 IP 주소를 가진 호스트가 자신의 MAC 주소로 응답합니다. 이 정보는 ARP 캐시에 저장되어 이후 통신에 사용됩니다.

#### 문제 4
**문제**: IP 단편화를 피하는 방법으로 옳지 않은 것은?

**정답**: TTL 값을 증가시켜 패킷이 더 많은 홉을 통과할 수 있게 한다

**해설**: TTL(Time To Live) 값은 패킷이 네트워크에서 무한히 순환하는 것을 방지하기 위한 필드로, 패킷이 통과할 수 있는 최대 라우터(홉) 수를 제한합니다. TTL 값을 증가시키는 것은 패킷의 생존 시간을 늘리는 것이지, IP 단편화를 피하는 방법과는 관련이 없습니다. IP 단편화를 피하는 실제 방법으로는 경로 MTU 발견(PMTUD)을 사용하여 경로상의 최소 MTU에 맞게 패킷 크기를 조정하는 것, TCP MSS 옵션을 통해 세그먼트 크기를 MTU에 맞게 협상하는 것, 점보 프레임을 사용하여 MTU를 증가시키는 것, 애플리케이션 계층에서 데이터 크기를 제한하는 것 등이 있습니다.

#### 문제 5
**문제**: 다음 중 IPv6의 특징이 아닌 것은?

**정답**: NAT(Network Address Translation)가 기본으로 포함되어 있다

**해설**: NAT(Network Address Translation)는 IPv6의 기본 특징이 아닙니다. NAT는 주로 IPv4 주소 부족 문제를 해결하기 위해 사용되는 기술로, 사설 IP 주소를 공인 IP 주소로 변환합니다. IPv6는 128비트의 매우 큰 주소 공간을 제공하므로, 주소 부족 문제가 없어 NAT가 필요하지 않습니다. 실제로 IPv6의 설계 목표 중 하나는 NAT의 필요성을 제거하는 것이었습니다. IPv6의 실제 특징으로는 확장된 주소 공간(128비트), 헤더 구조 단순화, 주소 자동 구성(SLAAC) 기능, 내장된 보안(IPsec), 향상된 QoS 지원, 멀티캐스트 지원 강화, 모바일 IP 지원 등이 있습니다.

## Chapter 04 전송 계층

### 04-3 TCP의 오류·흐름·혼잡 제어

#### 문제 1
**문제**: TCP의 오류 제어 메커니즘 중 하나인 ARQ에 대한 설명으로 옳지 않은 것은?

**정답**: TCP는 항상 Stop-and-Wait ARQ만 사용한다.

**해설**: TCP는 실제로 여러 ARQ 기법을 조합하여 사용합니다. TCP는 기본적으로 슬라이딩 윈도우 기반의 Go-Back-N ARQ와 Selective Repeat ARQ의 특성을 모두 가지고 있습니다. 중복 ACK를 통한 빠른 재전송(Fast Retransmit)과 선택적 확인 응답(SACK, Selective Acknowledgment) 옵션을 통해 손실된 특정 세그먼트만 선택적으로 재전송할 수 있습니다. 따라서 TCP가 항상 Stop-and-Wait ARQ만 사용한다는 설명은 옳지 않습니다.

#### 문제 2
**문제**: TCP의 슬라이딩 윈도우에 대한 설명으로 옳은 것은?

**정답**: 수신자는 TCP 헤더의 윈도우 크기 필드를 통해 처리 가능한 데이터 양을 알린다.

**해설**: TCP의 슬라이딩 윈도우 메커니즘에서 수신자는 TCP 헤더의 윈도우 크기 필드를 통해 자신이 처리할 수 있는 데이터의 양(바이트 수)을 송신자에게 알립니다. 이를 통해 송신자는 수신자의 처리 능력을 초과하지 않는 범위 내에서 데이터를 전송할 수 있습니다. 슬라이딩 윈도우는 흐름 제어와 혼잡 제어 모두에 사용되며, 윈도우 크기는 네트워크 상황과 수신자의 버퍼 상태에 따라 동적으로 조정됩니다. 윈도우 크기가 0이 되면 연결이 종료되는 것이 아니라, 송신자는 데이터 전송을 일시 중지하고 윈도우 프로브를 통해 수신자의 상태를 주기적으로 확인합니다.

#### 문제 3
**문제**: TCP의 혼잡 제어 알고리즘에 대한 설명으로 옳은 것은?

**정답**: 혼잡 회피 단계에서는 혼잡 윈도우가 매 RTT마다 1 MSS씩 증가한다.

**해설**: TCP의 혼잡 제어 알고리즘에서 혼잡 회피(Congestion Avoidance) 단계는 혼잡 윈도우(cwnd)가 임계값(ssthresh)에 도달한 후 시작됩니다. 이 단계에서는 혼잡 윈도우를 선형적으로 증가시키는데, 구체적으로 매 RTT(Round Trip Time)마다 1 MSS(Maximum Segment Size)씩 증가시킵니다. 이는 슬로우 스타트 단계에서의 지수적 증가(매 RTT마다 2배)와 대조됩니다. 빠른 재전송은 타임아웃이 발생하기 전에 중복 ACK(일반적으로 3개)를 감지하면 즉시 수행됩니다. 빠른 회복 단계에서는 혼잡 윈도우를 1 MSS로 재설정하지 않고, 임계값으로 설정하여 혼잡 회피 단계부터 다시 시작합니다.

#### 문제 4
**문제**: ECN(Explicit Congestion Notification)에 대한 설명으로 옳지 않은 것은?

**정답**: ECN은 모든 인터넷 라우터에서 기본적으로 활성화되어 있다.

**해설**: ECN은 모든 인터넷 라우터에서 기본적으로 활성화되어 있지 않습니다. ECN을 사용하기 위해서는 송신자, 수신자, 그리고 경로상의 라우터 모두가 ECN을 지원해야 하며, 많은 네트워크 장비에서는 ECN이 기본적으로 비활성화되어 있거나 아예 지원하지 않는 경우도 있습니다. ECN은 패킷 손실 없이 네트워크 혼잡을 알리는 메커니즘으로, IP 헤더의 특정 필드를 사용하여 혼잡 상태를 표시합니다. ECN을 사용하려면 TCP 연결 수립 시 양쪽 호스트가 ECN을 지원하는지 확인하는 과정이 필요합니다.

#### 문제 5
**문제**: 다음 중 TCP의 흐름 제어와 혼잡 제어의 차이점으로 가장 적절한 것은?

**정답**: 흐름 제어는 수신자의 처리 능력을 고려하고, 혼잡 제어는 네트워크의 혼잡 상태를 고려한다.

**해설**: TCP의 흐름 제어와 혼잡 제어는 목적과 대상이 다릅니다. 흐름 제어는 송신자가 수신자의 처리 능력을 초과하는 속도로 데이터를 전송하는 것을 방지하는 메커니즘으로, 수신자의 버퍼 오버플로우를 방지하는 것이 주요 목적입니다. 반면, 혼잡 제어는 네트워크의 혼잡 상태를 감지하고 대응하여 네트워크 성능을 최적화하는 메커니즘으로, 네트워크 자원의 효율적인 사용과 패킷 손실 방지가 주요 목적입니다. 두 메커니즘 모두 TCP에서 구현되며, UDP에서는 기본적으로 제공되지 않습니다.

#### 문제 6
**문제**: TCP의 재전송 타임아웃(RTO)을 결정하는 요소로 가장 중요한 것은?

**정답**: 왕복 시간(RTT)의 평균과 변동성

**해설**: TCP의 재전송 타임아웃(RTO, Retransmission Timeout)은 주로 왕복 시간(RTT, Round Trip Time)의 평균과 변동성을 기반으로 결정됩니다. TCP는 RTT를 지속적으로 측정하고, 이를 바탕으로 평균 RTT와 RTT의 변동성(편차)을 계산합니다. 이 두 값을 조합하여 적절한 RTO 값을 설정합니다. 일반적으로 RTO는 평균 RTT보다 크게 설정되며, RTT의 변동성이 클수록 RTO도 더 크게 설정됩니다. 이는 네트워크 상황의 변화에 적응하기 위한 것으로, 송신자의 CPU 성능, 수신자의 윈도우 크기, 네트워크 인터페이스 카드의 속도 등은 RTO 결정에 직접적인 영향을 미치지 않습니다.

## Chapter 05 응용 계층

### 05-1 DNS와 자원

#### 문제 1
**문제**: DNS의 주요 기능은 무엇인가요?

**정답**: 도메인 이름을 IP 주소로 변환하는 것

**해설**: DNS(Domain Name System)는 사람이 이해하기 쉬운 도메인 이름(예: www.example.com)을 컴퓨터가 이해할 수 있는 IP 주소(예: 93.184.216.34)로 변환해주는 시스템입니다. 이는 인터넷의 '전화번호부' 역할을 하며, 사용자가 웹사이트에 접속하거나 이메일을 보내는 등의 인터넷 활동을 할 때 필수적인 기능입니다. DNS가 없다면 사용자는 모든 웹사이트의 IP 주소를 기억해야 하는 불편함이 있을 것입니다.

#### 문제 2
**문제**: 다음 중 DNS 계층 구조에 포함되지 않는 것은?

**정답**: 프록시 네임 서버

**해설**: DNS 계층 구조는 루트 네임 서버, TLD(최상위 도메인) 네임 서버, 권한 있는 네임 서버, 로컬 DNS 서버로 구성됩니다. 프록시 네임 서버는 DNS 계층 구조의 일부가 아니라, 웹 프록시 서버의 한 종류로 웹 트래픽을 중개하는 역할을 합니다. 루트 네임 서버는 DNS 계층의 최상위에 위치하며, TLD 네임 서버는 .com, .org 등의 최상위 도메인을 관리합니다. 권한 있는 네임 서버는 특정 도메인의 DNS 레코드를 관리하고, 로컬 DNS 서버는 사용자의 DNS 쿼리를 처리하는 첫 번째 서버입니다.

#### 문제 3
**문제**: URL의 구성 요소가 아닌 것은?

**정답**: 메타데이터(metadata)

**해설**: URL(Uniform Resource Locator)의 구성 요소는 스킴(scheme), 권한(authority), 경로(path), 쿼리(query), 프래그먼트(fragment)입니다. 메타데이터는 URL의 구성 요소가 아닙니다. 스킴은 사용할 프로토콜(http, https 등)을 지정하고, 권한은 호스트 이름과 포트 번호를 포함합니다. 경로는 서버 내 자원의 위치를, 쿼리는 자원에 전달할 매개변수를, 프래그먼트는 자원 내의 특정 부분을 가리키는 식별자입니다. 메타데이터는 데이터에 대한 데이터로, URL 자체가 아닌 자원에 대한 추가 정보를 의미합니다.

#### 문제 4
**문제**: example.com의 IP 주소를 찾기 위한 DNS 조회 과정의 올바른 순서는?

**정답**: 로컬 DNS 서버 → 루트 네임 서버 → TLD 네임 서버 → 권한 있는 네임 서버

**해설**: DNS 조회 과정은 일반적으로 다음 순서로 진행됩니다: 1) 사용자의 컴퓨터는 로컬 DNS 서버(보통 ISP가 제공)에 쿼리를 보냅니다. 2) 로컬 DNS 서버는 루트 네임 서버에 쿼리를 보내 TLD 서버 정보를 얻습니다. 3) 로컬 DNS 서버는 TLD 네임 서버(예: .com 서버)에 쿼리를 보내 권한 있는 네임 서버 정보를 얻습니다. 4) 로컬 DNS 서버는 권한 있는 네임 서버에 쿼리를 보내 최종적으로 도메인의 IP 주소를 얻습니다. 이 과정은 재귀적 쿼리 또는 반복적 쿼리 방식으로 수행될 수 있으며, 캐싱을 통해 효율성을 높일 수 있습니다.

#### 문제 5
**문제**: 다음 중 이메일 서버를 지정하는 DNS 레코드 타입은?

**정답**: MX 레코드

**해설**: MX(Mail Exchange) 레코드는 도메인의 이메일 서버를 지정하는 DNS 레코드 타입입니다. 이메일을 보낼 때, 메일 서버는 수신자 도메인의 MX 레코드를 조회하여 어떤 서버로 이메일을 전달해야 하는지 결정합니다. A 레코드는 도메인 이름을 IPv4 주소에 매핑하고, CNAME 레코드는 도메인의 별칭을 설정하며, TXT 레코드는 도메인에 대한 텍스트 정보를 저장합니다. 각 MX 레코드에는 우선순위 값이 있어, 여러 메일 서버가 있을 경우 어떤 서버를 먼저 시도할지 결정합니다.

#### 문제 6
**문제**: URI와 URL의 관계를 올바르게 설명한 것은?

**정답**: URL은 URI의 한 종류이다

**해설**: URI(Uniform Resource Identifier)는 인터넷 상의 자원을 식별하는 문자열의 일반적인 형식입니다. URL(Uniform Resource Locator)은 URI의 한 종류로, 자원의 위치를 지정하는 방식입니다. 모든 URL은 URI이지만, 모든 URI가 URL인 것은 아닙니다. URI의 또 다른 종류로는 URN(Uniform Resource Name)이 있으며, 이는 자원의 이름을 통해 자원을 식별합니다. 예를 들어, "https://www.example.com"은 URL이면서 URI이고, "urn:isbn:0451450523"은 URL이 아닌 URI(URN)입니다.

#### 문제 7
**문제**: DNS 캐싱의 주요 목적은 무엇인가요?

**정답**: DNS 조회 성능을 향상시키기 위해

**해설**: DNS 캐싱의 주요 목적은 DNS 조회 성능을 향상시키는 것입니다. DNS 조회 과정은 여러 단계를 거쳐야 하므로 시간이 소요됩니다. 한 번 조회한 도메인 이름과 IP 주소의 매핑 정보를 캐시에 저장해두면, 동일한 도메인에 대한 후속 요청 시 전체 DNS 조회 과정을 반복할 필요 없이 캐시에서 바로 정보를 제공할 수 있습니다. 이는 응답 시간을 크게 단축시키고, 네트워크 트래픽을 줄이며, DNS 서버의 부하를 감소시킵니다. 캐시된 정보는 TTL(Time To Live) 값에 따라 일정 시간 동안만 유효하며, 이후에는 새로운 조회가 필요합니다.

### 05-2 HTTP

#### 문제 1
**문제**: HTTP의 특성으로 옳지 않은 것은?

**정답**: 상태 유지(stateful) 프로토콜이다

**해설**: HTTP는 기본적으로 스테이트리스(stateless) 프로토콜입니다. 즉, 각 요청은 독립적이며 이전 요청과의 관계를 유지하지 않습니다. 서버는 클라이언트의 상태를 저장하지 않으며, 각 요청을 완전히 새로운 요청으로 처리합니다. 이러한 특성은 서버의 확장성을 높이지만, 사용자 세션과 같은 상태 정보가 필요한 웹 애플리케이션에서는 제약이 될 수 있습니다. 이 제약을 극복하기 위해 쿠키, 세션, 토큰 등의 메커니즘이 도입되었습니다.

#### 문제 2
**문제**: 다음 중 HTTP 메서드와 그 용도가 올바르게 짝지어진 것은?

**정답**: POST - 서버에 데이터를 제출하여 처리 요청

**해설**: POST 메서드는 서버에 데이터를 제출하여 새 리소스를 생성하거나 기존 리소스를 수정하는 등의 처리를 요청하는 데 사용됩니다. GET은 리소스의 표현을 요청하는 메서드로, 서버의 상태를 변경해서는 안 됩니다. PUT은 지정된 리소스를 요청 본문의 내용으로 완전히 대체하는 메서드이며, PATCH는 리소스의 일부만 수정하는 메서드입니다. DELETE는 지정된 리소스를 삭제하는 메서드입니다.

#### 문제 3
**문제**: HTTP 상태 코드 401과 403의 차이점으로 옳은 것은?

**정답**: 401은 인증 실패, 403은 권한 부족을 의미한다

**해설**: 401 Unauthorized는 인증이 필요한 리소스에 인증 없이 접근했거나 인증이 실패했음을 의미합니다. 클라이언트는 적절한 인증 정보를 제공해야 합니다. 403 Forbidden은 서버가 요청을 이해했지만 권한이 없어 거부했음을 의미합니다. 즉, 클라이언트가 누구인지 서버가 알고 있지만, 해당 리소스에 접근할 권한이 없는 경우입니다. 401은 "당신이 누구인지 모르니 인증해주세요"라는 의미이고, 403은 "당신이 누구인지 알지만 이 리소스에 접근할 권한이 없습니다"라는 의미입니다.

#### 문제 4
**문제**: HTTP/2의 주요 특징이 아닌 것은?

**정답**: UDP 기반 전송 프로토콜

**해설**: HTTP/2는 TCP를 기반으로 하는 프로토콜입니다. UDP 기반 전송 프로토콜은 HTTP/3의 특징으로, HTTP/3는 QUIC(Quick UDP Internet Connections)이라는 UDP 기반 프로토콜을 사용합니다. HTTP/2의 주요 특징으로는 바이너리 프로토콜, 멀티플렉싱(하나의 연결로 여러 요청과 응답을 동시에 처리), 헤더 압축, 서버 푸시, 스트림 우선순위 지정 등이 있습니다.

#### 문제 5
**문제**: HTTP 메시지의 구성 요소를 올바른 순서로 나열한 것은?

**정답**: 시작 라인(또는 상태 라인) → 헤더 → 빈 줄 → 본문

**해설**: HTTP 메시지는 요청 메시지와 응답 메시지로 구분되며, 둘 다 동일한 구조를 따릅니다. 요청 메시지는 시작 라인(메서드, URI, HTTP 버전), 헤더, 빈 줄, 본문 순으로 구성됩니다. 응답 메시지는 상태 라인(HTTP 버전, 상태 코드, 상태 메시지), 헤더, 빈 줄, 본문 순으로 구성됩니다. 빈 줄은 헤더와 본문을 구분하는 역할을 하며, 헤더가 끝나고 본문이 시작됨을 나타냅니다.

#### 문제 6
**문제**: 다음 중 멱등성(idempotent)을 가진 HTTP 메서드는?

**정답**: GET

**해설**: 멱등성(idempotent)이란 동일한 요청을 여러 번 수행해도 결과가 같은 성질을 말합니다. GET, HEAD, PUT, DELETE 메서드는 멱등성을 가집니다. GET은 리소스를 조회하는 메서드로, 여러 번 요청해도 동일한 결과를 반환합니다. POST는 일반적으로 멱등성을 가지지 않습니다. 예를 들어, 동일한 POST 요청을 여러 번 보내면 여러 개의 리소스가 생성될 수 있습니다. PATCH도 일반적으로 멱등성을 보장하지 않지만, 구현에 따라 멱등성을 가질 수도 있습니다.

### 05-3 HTTP 헤더와 HTTP 기반 기술

#### 문제 1
**문제**: 다음 중 요청 헤더가 아닌 것은?

**정답**: Set-Cookie

**해설**: Set-Cookie는 요청 헤더가 아닌 응답 헤더입니다. 서버가 클라이언트에게 쿠키를 설정하도록 지시할 때 사용됩니다. 반면, Host, User-Agent, Referer는 모두 요청 헤더입니다. Host는 요청하는 호스트와 포트 번호를 지정하는 헤더로 HTTP/1.1에서는 필수 헤더입니다. User-Agent는 클라이언트 애플리케이션의 정보를 제공하는 헤더이고, Referer는 현재 요청된 페이지의 이전 웹 페이지 주소를 지정하는 헤더입니다.

#### 문제 2
**문제**: Cache-Control 헤더의 지시어 중 캐시된 응답을 사용하기 전에 서버에 검증 요청을 보내야 함을 의미하는 것은?

**정답**: no-cache

**해설**: Cache-Control 헤더의 no-cache 지시어는 캐시된 응답을 사용하기 전에 서버에 검증 요청을 보내야 함을 의미합니다. 이는 캐시를 사용하지 말라는 의미가 아니라, 캐시된 응답을 사용하기 전에 서버에 해당 응답이 여전히 유효한지 확인해야 한다는 의미입니다. 반면, no-store는 어떤 캐시도 응답을 저장하지 않도록 지시하고, private은 브라우저와 같은 특정 사용자 캐시만 응답을 저장할 수 있도록 하며, public은 모든 캐시가 응답을 저장할 수 있도록 지시합니다.

#### 문제 3
**문제**: 쿠키의 SameSite 속성에 대한 설명으로 옳지 않은 것은?

**정답**: None: 모든 크로스 사이트 요청에 쿠키를 전송(Secure 속성 없이도 사용 가능)

**해설**: SameSite=None 설정은 모든 크로스 사이트 요청에 쿠키를 전송할 수 있게 하지만, 반드시 Secure 속성과 함께 사용해야 합니다. 즉, SameSite=None; Secure 형태로 설정해야 하며, Secure 속성 없이는 사용할 수 없습니다. 이는 보안상의 이유로, HTTPS 연결에서만 쿠키가 전송되도록 하기 위함입니다. SameSite=Strict는 같은 사이트의 요청에만 쿠키를 전송하고, SameSite=Lax는 같은 사이트와 일부 크로스 사이트 요청(주로 탑 레벨 네비게이션)에 쿠키를 전송합니다. 브라우저마다 SameSite의 기본값은 다를 수 있으며, 최근 많은 브라우저에서는 기본값을 Lax로 설정하고 있습니다.

#### 문제 4
**문제**: 다음 Accept-Language 헤더에서 가장 선호하는 언어는?
```
Accept-Language: fr-CH, fr;q=0.9, en;q=0.8, de;q=0.7, *;q=0.5
```

**정답**: fr-CH

**해설**: Accept-Language 헤더에서 품질 값(q)이 명시되지 않은 언어의 기본 q 값은 1입니다. 따라서 fr-CH의 q 값은 1로, 이는 fr(q=0.9), en(q=0.8), de(q=0.7), *(q=0.5)보다 높습니다. 즉, 이 헤더는 스위스 프랑스어(fr-CH)를 가장 선호하고, 그 다음으로 프랑스어(fr), 영어(en), 독일어(de) 순으로 선호함을 나타냅니다. 별표(*)는 모든 언어를 의미하며, 명시된 언어가 없을 경우 어떤 언어든 수용할 수 있음을 나타냅니다.

#### 문제 5
**문제**: 다음 중 ETag 헤더의 주요 용도로 가장 적절한 것은?

**정답**: 리소스의 특정 버전을 식별하여 캐시 검증에 사용

**해설**: ETag(Entity Tag) 헤더는 리소스의 특정 버전에 대한 식별자로, 리소스가 변경되면 ETag 값도 변경됩니다. 이는 주로 캐시 검증에 사용됩니다. 클라이언트는 이전에 받은 ETag 값을 If-None-Match 헤더에 포함시켜 서버에 요청을 보내고, 서버는 현재 리소스의 ETag와 비교하여 리소스가 변경되었는지 확인합니다. 리소스가 변경되지 않았다면 서버는 304 Not Modified 응답을 보내 클라이언트가 캐시된 응답을 사용하도록 합니다. 이를 통해 불필요한 데이터 전송을 줄이고 네트워크 효율성을 높일 수 있습니다.

## Chapter 06 실습으로 복습하는 네트워크

### 06-1 와이어샤크 설치 및 사용법

#### 문제 1
**문제**: 와이어샤크에서 HTTP 트래픽만 필터링하기 위한 올바른 디스플레이 필터는 무엇인가요?

**정답**: http

**해설**: 와이어샤크에서 HTTP 트래픽만 필터링하기 위해서는 디스플레이 필터 입력란에 간단히 "http"를 입력하면 됩니다. 이 필터는 HTTP 프로토콜을 사용하는 모든 패킷을 표시합니다. "http.traffic"은 유효한 필터가 아니며, "port 80"은 포트 80을 사용하는 모든 트래픽을 필터링하는데, 이는 HTTP 트래픽일 가능성이 높지만 다른 프로토콜도 포함될 수 있습니다. "protocol http"는 와이어샤크의 올바른 필터 문법이 아닙니다.

#### 문제 2
**문제**: 와이어샤크 화면의 세 가지 주요 창에 대한 설명으로 올바르지 않은 것은?

**정답**: 패킷 분석 창은 선택한 패킷의 보안 취약점을 자동으로 분석합니다.

**해설**: 와이어샤크의 세 가지 주요 창은 패킷 목록 창(상단), 패킷 상세 창(중간), 패킷 바이트 창(하단)입니다. 패킷 목록 창은 캡처된 모든 패킷을 시간순으로 나열하고, 패킷 상세 창은 선택한 패킷의 프로토콜 계층별 정보를 보여주며, 패킷 바이트 창은 선택한 패킷의 원시 데이터를 16진수와 ASCII 형식으로 표시합니다. "패킷 분석 창은 선택한 패킷의 보안 취약점을 자동으로 분석합니다"라는 설명은 올바르지 않습니다. 와이어샤크는 기본적으로 패킷의 보안 취약점을 자동으로 분석하는 전용 창을 제공하지 않습니다. 보안 분석은 사용자가 패킷 내용을 검토하고 해석해야 하는 수동 과정입니다.

#### 문제 3
**문제**: 맥OS에서 와이어샤크를 설치하는 방법 중 Homebrew를 사용한 명령어는 무엇인가요?

**정답**: brew install --cask wireshark

**해설**: 맥OS에서 Homebrew를 사용하여 와이어샤크를 설치하는 올바른 명령어는 "brew install --cask wireshark"입니다. 이 명령어는 Homebrew의 Cask 확장을 사용하여 GUI 애플리케이션인 와이어샤크를 설치합니다. "apt-get install wireshark"는 Debian 기반 Linux 배포판(Ubuntu 등)에서 사용하는 명령어입니다. "sudo install wireshark"는 유효한 설치 명령어가 아니며, "brew cask install wireshark"는 예전 Homebrew 버전에서 사용되던 명령어로, 현재는 "brew install --cask" 형식을 권장합니다.

### 06-2 와이어샤크를 통한 프로토콜 분석

#### 문제 1
**문제**: 와이어샤크에서 IPv4 단편화된 패킷을 필터링하기 위한 올바른 표현식은?

**정답**: ip.flags.mf == 1 || ip.frag_offset > 0

**해설**: IPv4 패킷이 단편화되면 두 가지 특징이 있습니다: 마지막 조각을 제외한 모든 조각은 More Fragments(MF) 플래그가 설정되어 있고, 첫 번째 조각을 제외한 모든 조각은 Fragment Offset 값이 0보다 큽니다. 따라서 단편화된 패킷을 필터링하기 위해서는 "ip.flags.mf == 1 || ip.frag_offset > 0" 표현식을 사용합니다. 이 표현식은 MF 플래그가 설정된 패킷 또는 Fragment Offset이 0보다 큰 패킷을 모두 표시합니다. "ip.fragmentation == 1"과 "ip.fragment == true"는 와이어샤크에서 유효한 필터 표현식이 아니며, "ip.fragment_flag == 1"은 정확한 필드 이름이 아닙니다.

#### 문제 2
**문제**: TCP 3-way 핸드셰이크의 두 번째 단계에서 서버가 보내는 패킷의 플래그 조합은?

**정답**: SYN-ACK

**해설**: TCP 3-way 핸드셰이크는 다음과 같은 세 단계로 이루어집니다: 1) 클라이언트가 SYN 플래그가 설정된 패킷을 서버에 보냅니다. 2) 서버는 SYN과 ACK 플래그가 모두 설정된 패킷(SYN-ACK)으로 응답합니다. 3) 클라이언트는 ACK 플래그가 설정된 패킷으로 응답합니다. 따라서 두 번째 단계에서 서버가 보내는 패킷의 플래그 조합은 SYN-ACK입니다. 이는 서버가 클라이언트의 연결 요청을 수락하고(SYN), 동시에 클라이언트의 SYN 패킷을 받았음을 확인(ACK)하는 의미입니다.

#### 문제 3
**문제**: 와이어샤크에서 TCP 재전송 패킷을 필터링하는 표현식은?

**정답**: tcp.analysis.retransmission

**해설**: 와이어샤크는 TCP 패킷 분석 중 재전송으로 판단되는 패킷을 자동으로 식별합니다. 이러한 패킷을 필터링하기 위해서는 "tcp.analysis.retransmission" 표현식을 사용합니다. 이 필터는 와이어샤크의 분석 엔진이 재전송으로 판단한 모든 TCP 패킷을 표시합니다. "tcp.retransmission"은 유효한 필터가 아니며, "tcp.flags.retransmit == 1"과 "tcp.resend == true"는 TCP 헤더에 재전송을 직접 나타내는 플래그가 없기 때문에 유효하지 않습니다. TCP는 시퀀스 번호와 타이머를 사용하여 재전송을 관리하며, 와이어샤크는 이러한 정보를 분석하여 재전송을 식별합니다.

#### 문제 4
**문제**: HTTP GET 요청과 해당 응답을 포함한 전체 대화를 보기 위해 와이어샤크에서 사용하는 기능은?

**정답**: Follow HTTP Stream

**해설**: 와이어샤크에서 HTTP GET 요청과 해당 응답을 포함한 전체 대화를 보기 위해서는 "Follow HTTP Stream" 기능을 사용합니다. 이 기능은 HTTP 패킷을 선택한 후 마우스 오른쪽 버튼을 클릭하여 나타나는 컨텍스트 메뉴에서 "Follow" → "HTTP Stream"을 선택하여 접근할 수 있습니다. 이 기능은 TCP 스트림을 재구성하여 HTTP 요청과 응답을 포함한 전체 대화를 텍스트 형식으로 보여줍니다. 클라이언트에서 서버로의 트래픽은 일반적으로 빨간색으로, 서버에서 클라이언트로의 트래픽은 파란색으로 표시됩니다. "View HTTP Headers", "Decode HTTP", "Extract HTTP Objects"는 와이어샤크에서 제공하는 정확한 기능 이름이 아닙니다.

#### 문제 5
**문제**: IPv6에서 패킷 단편화를 위해 사용하는 확장 헤더는?

**정답**: Fragment 헤더

**해설**: IPv6에서는 패킷 단편화를 위해 Fragment 확장 헤더를 사용합니다. IPv6는 기본적으로 라우터에서 패킷 단편화를 수행하지 않고, 대신 경로 MTU 발견 메커니즘을 사용하여 패킷 크기를 조정합니다. 그러나 필요한 경우 출발지 호스트는 Fragment 확장 헤더를 사용하여 패킷을 단편화할 수 있습니다. 다른 IPv6 확장 헤더로는 Hop-by-Hop Options 헤더(모든 홉에서 처리해야 하는 옵션), Routing 헤더(패킷이 거쳐야 할 경로 지정), Destination Options 헤더(목적지에서만 처리되는 옵션) 등이 있습니다. 와이어샤크에서는 `ipv6.nxt == 44` 필터를 사용하여 Fragment 헤더를 가진 IPv6 패킷을 필터링할 수 있습니다.

## Chapter 07 네트워크 심화

### 07-1 안정성을 위한 기술

#### 문제 1
**문제**: 다음 중 가용성 99.9%는 연간 허용 가능한 다운타임이 얼마인가?

**정답**: 약 8.76시간

**해설**: 가용성은 시스템이 정상적으로 작동하는 시간의 비율을 의미합니다. 99.9% 가용성은 연간 총 시간(365일 × 24시간 = 8,760시간)의 0.1%가 다운타임으로 허용됨을 의미합니다. 따라서 8,760시간 × 0.001 = 8.76시간이 연간 허용 가능한 다운타임입니다. 이는 약 8시간 46분에 해당합니다. 99% 가용성은 약 3.65일(87.6시간), 99.99% 가용성은 약 52.56분, 99.999% 가용성은 약 5.26분의 연간 다운타임을 의미합니다.

#### 문제 2
**문제**: 로드 밸런싱 알고리즘 중 현재 연결 수가 가장 적은 서버에 요청을 분배하는 방식은?

**정답**: 최소 연결

**해설**: 최소 연결(Least Connection) 알고리즘은 현재 활성 연결 수가 가장 적은 서버에 새로운 요청을 분배하는 방식입니다. 이 방식은 서버의 부하 상태를 고려하여 트래픽을 분산하므로, 처리 시간이 다양한 요청이 있는 환경에서 효과적입니다. 라운드 로빈은 요청을 순차적으로 각 서버에 분배하는 단순한 방식이고, 가중치 기반 라운드 로빈은 서버의 처리 능력에 따라 가중치를 부여하여 분배하는 방식입니다. IP 해시는 클라이언트의 IP 주소를 해싱하여 항상 같은 서버로 요청을 보내는 방식으로, 세션 유지에 유용합니다.

#### 문제 3
**문제**: 다음 중 이중화에 대한 설명으로 옳지 않은 것은?

**정답**: 이중화는 항상 비용 효율적이므로 모든 시스템 구성 요소에 적용해야 한다.

**해설**: 이중화는 시스템의 중요 구성 요소를 복수로 구성하여 장애 발생 시에도 서비스가 중단되지 않도록 하는 기술입니다. 그러나 이중화는 항상 비용 효율적인 것은 아닙니다. 이중화를 구현하려면 추가적인 하드웨어, 소프트웨어, 네트워크 자원이 필요하며, 이는 비용 증가로 이어집니다. 따라서 모든 시스템 구성 요소에 무조건 이중화를 적용하는 것보다는, 비즈니스 요구사항, 중요도, 비용 대비 효과 등을 고려하여 선택적으로 적용하는 것이 바람직합니다. 하드웨어 이중화, 데이터베이스 이중화, 지역적 이중화에 대한 설명은 모두 옳습니다.

#### 문제 4
**문제**: 포워드 프록시와 리버스 프록시의 차이점으로 옳은 것은?

**정답**: 포워드 프록시는 클라이언트가 인식하지만, 리버스 프록시는 클라이언트가 인식하지 못한다.

**해설**: 포워드 프록시는 클라이언트 측에서 사용되며, 클라이언트는 프록시 서버를 통해 인터넷에 접속하도록 명시적으로 구성됩니다. 따라서 클라이언트는 포워드 프록시의 존재를 인식합니다. 반면, 리버스 프록시는 서버 측에서 사용되며, 클라이언트는 리버스 프록시에 직접 연결하지만 이것이 프록시인지 실제 서버인지 구분할 수 없습니다. 클라이언트는 리버스 프록시의 존재를 인식하지 못하고, 마치 원래 서버와 직접 통신하는 것처럼 느낍니다. 포워드 프록시는 클라이언트 측에서, 리버스 프록시는 서버 측에서 사용되며, 포워드 프록시의 주요 목적은 클라이언트 익명성과 접근 제어인 반면, 리버스 프록시의 주요 목적은 로드 밸런싱과 보안 강화입니다.

#### 문제 5
**문제**: 로드 밸런서의 헬스 체크에 대한 설명으로 옳은 것은?

**정답**: 서버의 상태를 확인하여 문제가 있는 서버로의 트래픽 전송을 중단한다.

**해설**: 로드 밸런서의 헬스 체크는 백엔드 서버의 상태를 주기적으로 확인하는 메커니즘입니다. 서버가 정상적으로 응답하지 않거나 성능이 저하된 경우, 로드 밸런서는 해당 서버로의 트래픽 전송을 중단하고 정상 서버로만 트래픽을 분산합니다. 이를 통해 장애가 있는 서버로 인해 사용자 경험이 저하되는 것을 방지하고, 시스템의 전반적인 가용성을 유지할 수 있습니다. 헬스 체크는 클라이언트의 상태를 확인하거나, 네트워크 장비의 상태를 확인하거나, 데이터베이스의 상태를 확인하는 것이 아니라, 로드 밸런서가 트래픽을 분산하는 대상 서버의 상태를 확인하는 것입니다.

### 07-2 안전성을 위한 기술

#### 문제 1
**문제**: 다음 중 대칭 키 암호화 방식의 특징이 아닌 것은?

**정답**: 키 배포 문제가 없다.

**해설**: 대칭 키 암호화 방식은 암호화와 복호화에 동일한 키를 사용하는 방식입니다. 이 방식의 주요 단점 중 하나는 바로 키 배포 문제입니다. 통신하는 양측이 동일한 키를 공유해야 하는데, 이 키를 안전하게 교환하는 것이 어렵습니다. 만약 키가 전송 중에 유출되면 암호화의 의미가 없어집니다. 이러한 키 배포 문제를 해결하기 위해 공개 키 암호화 방식이 개발되었습니다. 대칭 키 암호화는 공개 키 암호화보다 계산 효율성이 높고 속도가 빠르며, 대용량 데이터 암호화에 적합하다는 특징이 있습니다.

#### 문제 2
**문제**: 디지털 서명의 주요 목적으로 옳지 않은 것은?

**정답**: 메시지 내용의 기밀성 보장

**해설**: 디지털 서명은 메시지의 출처(인증), 무결성, 부인 방지를 제공하지만, 메시지 내용의 기밀성은 보장하지 않습니다. 디지털 서명은 송신자의 개인 키로 메시지의 해시값을 암호화하는 과정으로, 이를 통해 메시지가 실제 송신자로부터 왔는지 확인하고(인증), 전송 중에 변조되지 않았는지 확인하며(무결성), 송신자가 나중에 메시지 전송 사실을 부인할 수 없게 합니다(부인 방지). 그러나 디지털 서명 자체는 메시지 내용을 암호화하지 않기 때문에 기밀성을 제공하지 않습니다. 메시지 내용의 기밀성을 보장하려면 별도의 암호화 과정이 필요합니다.

#### 문제 3
**문제**: TLS 핸드셰이크 과정에서 세션 키를 생성하기 위해 사용되는 것은?

**정답**: 프리마스터 시크릿과 양측이 교환한 랜덤 데이터

**해설**: TLS 핸드셰이크 과정에서 세션 키는 프리마스터 시크릿(pre-master secret)과 클라이언트와 서버가 교환한 랜덤 데이터를 조합하여 생성됩니다. 클라이언트는 프리마스터 시크릿을 생성하여 서버의 공개 키로 암호화한 후 서버에 전송합니다. 서버는 자신의 개인 키로 이를 복호화하여 프리마스터 시크릿을 얻습니다. 그런 다음 양측은 프리마스터 시크릿과 이전에 교환한 랜덤 데이터를 사용하여 동일한 세션 키를 생성합니다. 이 과정을 통해 안전하게 세션 키를 공유할 수 있으며, 이후 통신은 이 세션 키를 사용한 대칭 키 암호화로 보호됩니다.

#### 문제 4
**문제**: 다음 중 HTTPS의 이점이 아닌 것은?

**정답**: 서버 성능 향상

**해설**: HTTPS는 데이터 기밀성, 무결성, 인증 등 여러 보안 이점을 제공하지만, 서버 성능 향상은 HTTPS의 이점이 아닙니다. 실제로 HTTPS는 암호화/복호화 과정으로 인해 HTTP보다 약간의 성능 오버헤드가 발생합니다. 그러나 현대의 하드웨어와 최적화된 구현으로 이 오버헤드는 대부분의 응용 프로그램에서 무시할 수 있을 정도로 작아졌습니다. HTTPS의 실제 이점으로는 전송 데이터의 기밀성 보장, 웹사이트 신원 인증, 데이터 무결성 검증, 검색 엔진 최적화(SEO) 개선, 최신 웹 기술(HTTP/2, PWA 등) 지원 등이 있습니다.

#### 문제 5
**문제**: 인증서 체인에 대한 설명으로 옳은 것은?

**정답**: 루트 CA의 인증서는 브라우저나 운영체제에 미리 설치되어 있다.

**해설**: 인증서 체인은 디지털 인증서의 신뢰성을 검증하기 위한 계층적 구조입니다. 루트 CA(인증 기관)의 인증서는 브라우저나 운영체제에 미리 설치되어 있어, 이를 신뢰 앵커(trust anchor)로 사용합니다. 웹사이트는 자체 서명된 인증서보다는 신뢰할 수 있는 CA로부터 발급받은 인증서를 사용하는 것이 일반적입니다. 인증서 체인은 최종 사용자 인증서, 하나 이상의 중간 CA 인증서, 루트 CA 인증서로 구성될 수 있으며, 2개 이상의 인증서로 구성될 수 있습니다. 중간 인증 기관은 루트 CA로부터 권한을 위임받아 최종 사용자 인증서를 발급하고 검증할 수 있습니다.

### 07-3 무선 네트워크

#### 문제 1
**문제**: 다음 중 2.4GHz 대역의 특성으로 옳지 않은 것은?

**정답**: 사용 가능한 채널 수가 5GHz보다 많다.

**해설**: 2.4GHz 대역은 5GHz 대역보다 사용 가능한 채널 수가 적습니다. 2.4GHz 대역은 일반적으로 채널 1~13(일부 국가에서는 14)을 사용하며, 각 채널은 5MHz 간격으로 배치되어 있습니다. 반면 5GHz 대역은 국가 및 규제에 따라 다르지만, 일반적으로 더 많은 채널(최대 25개 이상)을 제공합니다. 2.4GHz 대역의 실제 특성으로는 장애물 투과성이 5GHz보다 좋고, 도달 거리가 5GHz보다 길며, 블루투스, 전자레인지 등 다른 기기와 간섭이 발생할 수 있다는 점이 있습니다.

#### 문제 2
**문제**: 다음 중 무선 네트워크에서 주파수 대역이 높아질수록 나타나는 특성은?

**정답**: 더 많은 채널을 사용할 수 있다

**해설**: 무선 네트워크에서 주파수 대역이 높아질수록 더 많은 채널을 사용할 수 있습니다. 이는 높은 주파수 대역이 더 넓은 스펙트럼을 제공하기 때문입니다. 예를 들어, 2.4GHz 대역은 일반적으로 채널 1~13(일부 국가에서는 14)을 사용하는 반면, 5GHz 대역은 더 많은 채널(최대 25개 이상)을 제공합니다. 반면, 주파수 대역이 높아질수록 장애물 투과성은 감소하고(벽이나 장애물을 통과하는 능력이 떨어짐), 도달 거리도 짧아집니다. 또한 높은 주파수 대역에서는 일반적으로 다른 기기와의 간섭이 감소하는 경향이 있습니다. 이러한 특성들은 본문의 주파수 대역별 특성 설명에서 확인할 수 있습니다.

#### 문제 3
**문제**: 무선 네트워크에서 사용하는 매체 접근 제어 방식은?

**정답**: CSMA/CA

**해설**: 무선 네트워크에서는 CSMA/CA(Carrier Sense Multiple Access with Collision Avoidance) 방식을 사용합니다. 이 방식은 데이터를 전송하기 전에 채널이 사용 중인지 확인하고(Carrier Sense), 사용 중이 아닐 때 전송을 시도하며, 충돌을 미리 회피(Collision Avoidance)하기 위한 메커니즘을 포함합니다. 유선 이더넷에서 사용하는 CSMA/CD(Collision Detection)와 달리, 무선 환경에서는 충돌을 감지하기 어렵기 때문에 충돌을 사전에 회피하는 방식을 채택했습니다. Token Ring은 유선 네트워크에서 사용되던 토큰 기반 접근 제어 방식이고, TDMA(Time Division Multiple Access)는 시간을 분할하여 각 장치에 할당하는 방식입니다.

#### 문제 4
**문제**: 다음 중 와이파이 보안 프로토콜을 시간순으로 올바르게 나열한 것은?

**정답**: WEP → WPA → WPA2 → WPA3

**해설**: 와이파이 보안 프로토콜은 시간이 지남에 따라 발전해왔으며, 올바른 시간순 나열은 WEP → WPA → WPA2 → WPA3입니다. WEP(Wired Equivalent Privacy)는 초기 보안 프로토콜로 1999년에 도입되었지만 심각한 보안 취약점이 발견되었습니다. WPA(Wi-Fi Protected Access)는 2003년에 WEP의 취약점을 해결하기 위한 임시 표준으로 도입되었습니다. WPA2는 2004년에 도입된 더 강력한 보안 표준으로, AES-CCMP 암호화를 사용합니다. WPA3는 2018년에 도입된 최신 보안 표준으로, SAE(Simultaneous Authentication of Equals) 등 향상된 보안 기능을 제공합니다.

#### 문제 5
**문제**: 여러 AP가 동일한 SSID로 연결된 무선 네트워크 구성을 무엇이라고 하는가?

**정답**: ESS (Extended Service Set)

**해설**: 여러 AP(액세스 포인트)가 동일한 SSID로 연결된 무선 네트워크 구성을 ESS(Extended Service Set)라고 합니다. ESS는 여러 BSS(Basic Service Set)가 분산 시스템(DS)을 통해 연결된 구조로, 사용자가 넓은 지역을 이동하면서도 끊김 없는 네트워크 연결을 유지할 수 있게 해줍니다. 이는 기업이나 캠퍼스 환경에서 흔히 볼 수 있는 구성입니다. BSS는 하나의 AP와 이에 연결된 클라이언트들로 구성된 기본 네트워크 단위이고, IBSS(Independent BSS)는 AP 없이 클라이언트 간 직접 연결되는 Ad-Hoc 네트워크입니다. MSS(Multiple Service Set)는 표준 용어가 아닙니다.

#### 문제 6
**문제**: 무선 클라이언트가 하나의 AP에서 다른 AP로 이동할 때 연결을 유지하는 과정을 무엇이라고 하는가?

**정답**: 로밍(Roaming)

**해설**: 무선 클라이언트가 하나의 AP에서 다른 AP로 이동하면서 네트워크 연결을 유지하는 과정을 로밍(Roaming)이라고 합니다. 로밍 과정에서 클라이언트는 신호 강도(RSSI), 신호 품질, 채널 사용률 등을 모니터링하고, 현재 연결된 AP보다 더 나은 조건의 AP를 발견하면 연결을 전환합니다. 이 과정은 사용자가 인식하지 못하는 사이에 자동으로 이루어지며, ESS 환경에서 끊김 없는 이동성을 제공합니다. 핸드오버(Handover)는 주로 셀룰러 네트워크에서 사용되는 용어이고, 스위칭과 브리징은 로밍과는 다른 네트워크 개념입니다.

#### 문제 7
**문제**: 다음 중 메시 네트워크의 특징이 아닌 것은?

**정답**: 모든 통신이 중앙 컨트롤러를 통해 이루어짐

**해설**: 메시 네트워크의 특징은 중앙 컨트롤러에 의존하지 않고 분산된 방식으로 작동한다는 점입니다. 따라서 "모든 통신이 중앙 컨트롤러를 통해 이루어짐"은 메시 네트워크의 특징이 아닙니다. 메시 네트워크에서는 각 노드(AP)가 다른 노드와 직접 통신할 수 있으며, 데이터는 여러 경로를 통해 목적지에 도달할 수 있습니다. 이러한 구조는 단일 장애점을 제거하고 네트워크의 안정성과 확장성을 향상시킵니다. 메시 네트워크의 실제 특징으로는 AP 간 무선 연결로 네트워크 확장, 자동 경로 설정 및 자가 복구 기능, 단일 장애점 제거로 안정성 향상 등이 있습니다.

#### 문제 8
**문제**: 무선 네트워크에서 비중첩 채널(non-overlapping channels)을 사용하는 주된 이유는?

**정답**: 채널 간 간섭을 최소화하기 위해

**해설**: 무선 네트워크에서 비중첩 채널을 사용하는 주된 이유는 채널 간 간섭을 최소화하기 위함입니다. 무선 채널은 특정 주파수 대역을 사용하는데, 인접한 채널들은 주파수 대역이 부분적으로 겹치게 됩니다. 이러한 겹침은 간섭을 일으켜 네트워크 성능 저하, 연결 불안정, 데이터 손실 등의 문제를 야기할 수 있습니다. 비중첩 채널(예: 2.4GHz 대역에서의 1, 6, 11)을 사용하면 각 채널이 사용하는 주파수 대역이 서로 겹치지 않아 간섭 없이 동시에 사용할 수 있습니다. 이는 여러 AP가 근접한 환경에서 특히 중요합니다. 비중첩 채널의 사용은 전송 속도 향상, 보안 강화, 전력 소비 감소와는 직접적인 관련이 없습니다.

#### 문제 9
**문제**: 다음 중 와이파이 네트워크의 식별자로 사용되는 것은?

**정답**: SSID

**해설**: SSID(Service Set Identifier)는 와이파이 네트워크의 이름 또는 식별자로 사용됩니다. 최대 32바이트 길이의 문자열로, 사용자가 네트워크를 식별하고 연결할 수 있게 해줍니다. AP는 일반적으로 SSID를 브로드캐스트하여 주변 장치들이 사용 가능한 네트워크를 발견할 수 있게 합니다. MAC 주소는 네트워크 장치의 물리적 주소이고, IP 주소는 네트워크 계층의 논리적 주소이며, DNS는 도메인 이름을 IP 주소로 변환하는 시스템입니다. 이들은 와이파이 네트워크 자체의 식별자가 아닙니다.

[이하 각 장의 문제와 정답 형식은 위와 동일하게 구성됩니다.]
