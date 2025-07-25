# Chapter 02 물리 계층과 데이터 링크 계층

## 02-4 스위치

### 개요
이 섹션에서는 네트워크의 핵심 연결 장치인 스위치(Switch)에 대해 살펴봅니다. 데이터 링크 계층에서 동작하는 스위치의 특징과 MAC 주소 학습 방식, 그리고 가상 LAN(VLAN)의 개념과 구현 방법에 대해 학습합니다. 이를 통해 허브의 한계를 극복하고 효율적인 네트워크 구성이 가능해진 배경을 이해하고, 현대 네트워크의 기본 구성 요소에 대한 지식을 습득합니다.

### 스위치

#### 스위치의 특징
스위치(Switch)는 데이터 링크 계층(OSI 모델의 2계층)에서 동작하는 네트워크 장비로, 허브의 한계를 극복하고 네트워크 효율성을 크게 향상시킨 장치입니다. 스위치의 주요 특징은 다음과 같습니다:

1. **MAC 주소 기반 전송**: 스위치는 프레임의 목적지 MAC 주소를 확인하여 해당 주소가 연결된 포트로만 프레임을 전송합니다. 이는 허브의 브로드캐스트 방식과 대조적입니다.

2. **MAC 주소 테이블 관리**: 스위치는 각 포트에 연결된 장치의 MAC 주소를 학습하여 MAC 주소 테이블(또는 포워딩 테이블)에 저장합니다. 이 테이블을 참조하여 효율적인 프레임 전달이 가능합니다.

3. **개별 콜리전 도메인**: 스위치의 각 포트는 독립적인 콜리전 도메인을 형성합니다. 이로 인해 한 포트에서 발생한 충돌이 다른 포트에 영향을 미치지 않습니다.

4. **전이중 통신(Full-duplex) 지원**: 스위치는 전이중 통신을 지원하여 동시에 데이터를 송수신할 수 있습니다. 이는 네트워크 성능을 크게 향상시킵니다.

5. **높은 대역폭**: 스위치는 각 포트에 전용 대역폭을 제공하므로, 허브와 달리 연결된 장치 수가 증가해도 각 장치의 성능이 크게 저하되지 않습니다.

6. **자동 협상(Auto-negotiation)**: 스위치는 연결된 장치와 속도, 이중 모드 등을 자동으로 협상하여 최적의 연결 설정을 구성합니다.

스위치와 허브의 주요 차이점은 다음과 같습니다:

| 특성 | 스위치 | 허브 |
|------|--------|------|
| 동작 계층 | 데이터 링크 계층(2계층) | 물리 계층(1계층) |
| 프레임 전달 방식 | MAC 주소 기반 선택적 전달 | 모든 포트로 브로드캐스트 |
| 콜리전 도메인 | 포트별 독립적인 도메인 | 하나의 공유 도메인 |
| 통신 모드 | 전이중(Full-duplex) 지원 | 반이중(Half-duplex) 제한 |
| 대역폭 | 포트별 전용 대역폭 | 공유 대역폭 |
| 네트워크 효율성 | 높음 | 낮음 |

### MAC 주소 학습
스위치의 핵심 기능 중 하나는 MAC 주소 학습(MAC address learning)입니다. 이는 스위치가 네트워크 토폴로지를 자동으로 파악하고 효율적인 프레임 전달을 가능하게 하는 메커니즘입니다.

MAC 주소 학습 과정은 다음과 같습니다:

1. **초기 상태**: 스위치가 처음 작동하거나 재부팅된 경우, MAC 주소 테이블은 비어 있습니다.

2. **소스 MAC 주소 학습**: 스위치는 프레임이 수신될 때마다 프레임의 소스 MAC 주소와 해당 프레임이 수신된 포트 번호를 MAC 주소 테이블에 기록합니다.

3. **목적지 MAC 주소 확인**: 프레임을 전달할 때, 스위치는 목적지 MAC 주소를 MAC 주소 테이블에서 검색합니다.
   - 목적지 MAC 주소가 테이블에 있는 경우: 해당 포트로만 프레임을 전달합니다.
   - 목적지 MAC 주소가 테이블에 없는 경우: 수신 포트를 제외한 모든 포트로 프레임을 플러딩(flooding)합니다.
   - 목적지가 브로드캐스트 주소(FF:FF:FF:FF:FF:FF)인 경우: 수신 포트를 제외한 모든 포트로 프레임을 전달합니다.

4. **테이블 업데이트**: MAC 주소 테이블의 각 항목은 일정 시간(일반적으로 300초) 동안 사용되지 않으면 만료됩니다. 이를 에이징 타임(aging time)이라고 합니다.

MAC 주소 학습의 이점:
- **효율적인 대역폭 사용**: 필요한 포트로만 프레임을 전달하여 불필요한 네트워크 트래픽을 줄입니다.
- **자동 구성**: 네트워크 관리자가 수동으로 MAC 주소를 설정할 필요가 없습니다.
- **동적 적응**: 네트워크 토폴로지가 변경되면 MAC 주소 테이블이 자동으로 업데이트됩니다.

### VLAN
VLAN(Virtual Local Area Network)은 물리적 네트워크 구성과 독립적으로 논리적인 네트워크 세그먼트를 생성하는 기술입니다. VLAN을 사용하면 하나의 물리적 스위치를 여러 개의 논리적 스위치처럼 사용할 수 있습니다.

VLAN의 주요 이점:
- **브로드캐스트 도메인 분할**: 각 VLAN은 별도의 브로드캐스트 도메인을 형성하여 브로드캐스트 트래픽을 제한합니다.
- **보안 강화**: 서로 다른 VLAN에 속한 장치들은 라우터나 레이어 3 스위치 없이는 직접 통신할 수 없습니다.
- **네트워크 관리 용이성**: 물리적 위치와 관계없이 논리적 그룹으로 장치를 구성할 수 있습니다.
- **비용 효율성**: 물리적 네트워크 재구성 없이 논리적 네트워크 구성을 변경할 수 있습니다.

#### 포트 기반 VLAN
포트 기반 VLAN(Port-based VLAN)은 가장 기본적이고 널리 사용되는 VLAN 구현 방식입니다. 이 방식에서는 스위치의 각 물리적 포트가 특정 VLAN에 할당됩니다.

포트 기반 VLAN의 특징:
- **구성 방식**: 스위치 관리자가 각 포트를 특정 VLAN에 수동으로 할당합니다.
- **간단한 구현**: 설정이 간단하고 대부분의 스위치에서 지원됩니다.
- **정적 구성**: 장치가 다른 포트로 이동하면 VLAN 멤버십도 변경됩니다.
- **액세스 포트와 트렁크 포트**:
  - **액세스 포트**: 하나의 VLAN에만 속하며, 일반적으로 최종 사용자 장치에 연결됩니다.
  - **트렁크 포트**: 여러 VLAN의 트래픽을 전달할 수 있으며, 일반적으로 스위치 간 연결에 사용됩니다. 802.1Q 태깅을 사용하여 프레임이 어떤 VLAN에 속하는지 식별합니다.

#### MAC 기반 VLAN
MAC 기반 VLAN(MAC-based VLAN)은 장치의 MAC 주소를 기반으로 VLAN 멤버십을 할당하는 방식입니다. 이 방식에서는 스위치가 프레임의 소스 MAC 주소를 확인하여 해당 장치가 속한 VLAN을 결정합니다.

MAC 기반 VLAN의 특징:
- **동적 할당**: 장치의 물리적 위치가 변경되어도 동일한 VLAN에 유지됩니다.
- **이동성 지원**: 사용자가 네트워크 내에서 이동해도 VLAN 멤버십이 유지됩니다.
- **구성 복잡성**: 각 MAC 주소와 VLAN의 매핑을 관리해야 하므로 포트 기반 VLAN보다 구성이 복잡합니다.
- **보안 고려사항**: MAC 주소는 변조될 수 있으므로, 보안 중요도가 높은 환경에서는 추가적인 보안 조치가 필요합니다.

VLAN 간 통신을 위해서는 라우터나 레이어 3 스위치가 필요합니다. 이를 인터-VLAN 라우팅(Inter-VLAN routing)이라고 하며, 서로 다른 VLAN에 속한 장치들이 통신할 수 있게 해줍니다.

### 4가지 키워드로 정리하는 핵심 포인트
1. **스위치**: 데이터 링크 계층에서 동작하며 MAC 주소 기반으로 프레임을 전달하는 네트워크 장비로, 각 포트가 독립적인 콜리전 도메인을 형성하여 네트워크 효율성을 높임
2. **MAC 주소 학습**: 스위치가 프레임의 소스 MAC 주소를 학습하여 MAC 주소 테이블을 구축하고, 이를 기반으로 효율적인 프레임 전달을 수행하는 메커니즘
3. **VLAN**: 물리적 네트워크 구성과 독립적으로 논리적 네트워크 세그먼트를 생성하는 기술로, 브로드캐스트 도메인 분할과 보안 강화에 기여
4. **포트/MAC 기반 VLAN**: 포트 기반 VLAN은 스위치 포트에 VLAN을 할당하는 방식이고, MAC 기반 VLAN은 장치의 MAC 주소를 기준으로 VLAN을 할당하는 방식으로, 각각 정적/동적 환경에 적합

### 확인 문제
1. 다음 중 스위치와 허브의 차이점으로 옳지 않은 것은?
   - [ ] 스위치는 데이터 링크 계층에서 동작하고, 허브는 물리 계층에서 동작한다
   - [ ] 스위치는 MAC 주소 기반으로 프레임을 전달하고, 허브는 모든 포트로 신호를 재전송한다
   - [ ] 스위치의 각 포트는 독립적인 콜리전 도메인을 형성하고, 허브는 하나의 콜리전 도메인을 형성한다
   - [x] 스위치는 네트워크 계층 주소를 사용하고, 허브는 데이터 링크 계층 주소를 사용한다

2. MAC 주소 학습에 대한 설명으로 옳은 것은?
   - [ ] 스위치는 목적지 MAC 주소만을 학습하여 MAC 주소 테이블을 구성한다
   - [x] 목적지 MAC 주소가 테이블에 없으면 스위치는 해당 프레임을 수신 포트를 제외한 모든 포트로 전송한다
   - [ ] MAC 주소 테이블은 스위치가 재부팅되어도 유지된다
   - [ ] 브로드캐스트 프레임은 MAC 주소 테이블을 참조하여 특정 포트로만 전달된다

3. VLAN의 주요 이점으로 옳지 않은 것은?
   - [ ] 브로드캐스트 트래픽을 제한하여 네트워크 효율성을 높인다
   - [ ] 서로 다른 VLAN 간의 통신을 제한하여 보안을 강화한다
   - [ ] 물리적 위치와 관계없이 논리적 그룹으로 장치를 구성할 수 있다
   - [x] 네트워크 장비의 수를 줄여 하드웨어 비용을 절감한다

4. 포트 기반 VLAN과 MAC 기반 VLAN의 차이점으로 옳은 것은?
   - [ ] 포트 기반 VLAN은 동적 할당을 지원하고, MAC 기반 VLAN은 정적 할당만 지원한다
   - [ ] 포트 기반 VLAN은 802.1Q 태깅을 사용하지 않지만, MAC 기반 VLAN은 항상 802.1Q 태깅을 사용한다
   - [x] MAC 기반 VLAN은 사용자가 네트워크 내에서 이동해도 VLAN 멤버십이 유지되지만, 포트 기반 VLAN은 포트가 변경되면 VLAN도 변경된다
   - [ ] 포트 기반 VLAN은 레이어 3 스위치에서만 구현 가능하고, MAC 기반 VLAN은 모든 스위치에서 구현 가능하다

> [정답 및 해설 보기](../answers_and_explanations.md#02-4-스위치)