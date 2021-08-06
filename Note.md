# BlockchainLecture
https://www.youtube.com/watch?v=1g7YF1Wjsvw

블록체인 소개 및 활용

블록체인
- 블록체인이란 관리 대상 데이터를 ‘블록’이라고 하는 소규모 데이터들이, P2P 방식을 기반으로 생성된 체인 형태의 연결고리 기반 분산 데이터 저장 환경에 저장되어 누구라도 임의로 수정할 수 없고 누구나 변경의 결과를 열람할 수 있는 분산 컴퓨팅 기술 기반의 데이터 위변조 방지 기술

전자서명(Digital Signature)
- PKI (Public Key Infrastructure) 기술을 이용한 사용자 확인, Tx 무결성, 부인 방지 제공
- 자산 소유 증명, Tx 생성 행위 증명
- Authentication(인증): reason to believe the message was created and sent by the claimed sender
- Integrity(무결성): ensures that the message was not altered in transit
- Non-repudiation(부인 방지): sender can not deny having sent the message later on

위변조 불가능한 블록 생성 (분산원장)
- 블록체인의 가장 큰 특징인, 위변조 불가능한 블록 생성
- 이전 Block의 Hash 값을 다음 Block에 포함시켜, Block 내의 값이 변경되면 다음 Block에서 확인할 수 있음
- Hash Function
    - 해시 함수(hash function)는 임의의 길이의 데이터를 고정된 길이의 데이터로 매핑하는 함수
    - 해시 함수는 결정론적으로 작동해야 하며, 따라서 두 해시 값이 다르다면 그 해시값에 대한 원래 데이터도 달라짐
    - 한 방향 계산은 쉬우나 역방향 계산은 매우 어려운 수식

위변조 불가능한 블록 생성
- Block 생성 시 검증을 위해서 다수의 노드가 참여하여 합의를 통해서 생성된 Block 검증 함
- 다수의 노드가 동일한 블록 데이터를 저장하고 있음


합의 알고리즘에 따른 블록체인 분류
- 블록생성 자격
    - PoW (Proof of Work)
    - PoS (Proof of Stake), DPOS (Delegated POS),
    - PoA (Proof of Authority)
- 합의 방법 (블록 검증/선택)
    - Nakamoto
    - PBFT (Practical Byzantine Fault Tolerant)

- PoW (Proof of Work)
    - Node identity management
        - Open, fully decentralized
    - Finality(완결성)
        - No (probabilistic, 확률론적)
    - Scalability(확장성) - nodes
        - Excellent
    - Scalability - clients
        - Excellent
    - Performance
        - Limited(7 TPS for bitcoin, 20 TPS for Ethereum)
        - * TPS(Transaction per second): 초당 트랜잭션 수
    - Power consumption
        - Very poor

- PBFT
    - Node identity management
        - Permissioned
    - Finality(완결성)
        - Yes
    - Scalability(확장성) - nodes
        - Limited
    - Scalability - clients
        - Excellent
    - Performance
        - Excellent(> 1000 TPS)
        - * TPS(Transaction per second): 초당 트랜잭션 수
    - Power consumption
        - Good 

노드 참여 제한에 따른 블록체인 분류
- 블록생성/검증 노드 참여 방법: public, consortium, private

- Public 블록체인
    - 읽기 권한
        - 누구나 열람 가능
    - 거래 검증 및 승인
        - 누구나 네트워크에 참여하면 거래 검증 및 승인을 수행
    - 트랜잭션 생성자
        - 누구나 트랜잭션을 생성
    - 합의 알고리즘
        - 부분 분기를 허용하는 작업 증명이나 지분증명 알고리즘
    - 권한 관리
        - 모두가 모든 일을 할 수 있다
    - 예시
        - 비트코인, 이더리움

- Private 블록체인
    - 읽기 권한
        - 허가된 기관만 열람 가능
    - 거래 검증 및 승인
        - 승인된 기관과 감독 기관
    - 트랜잭션 생성자
        - 법적 책임을 지는 기관만 참여
    - 합의 알고리즘
        - 부분 분기를 허용하지 않는 BFT계열의 합의 알고리즘
    - 권한 관리
        - Private Channel, Tierd System 등을 통해 읽기 쓰기 권한 관리가 가능
    - 예시
        - ICONLOOP’s loop chain, IBM Hyperledger Fabric, R3 Corda

Oracle Problem
- 블록체인 내의 데이터에 대해서는 신뢰하지만, 블록체인 밖으로부터의 데이터는 신뢰할 수 없음


스마트 컨트랙트 (Smart Contract)
- 서면으로 이루어지던 계약을 코드로 구현하고, 특정 조건이 충족되었을때 해당 계약이 이행되게 하는 스크립트
- 블록체인의 특성을 이용하여, 누구나 코드와 결과를 확인 가능하고, 위변조 불가능한 실행결과 생성


스마트 컨트랙트 구현 시 주의사항
- Code should be deterministic as it will run on multiple nodes
    - Should avoid any business logic that depends on non-deterministic input such as clock time, random number, or external data source
    - “Oracle” as an external data carrier

- Blockchain is not a cloud computing or database
    - Do not make any long-running operations inside Smart Contract, nor store large data on blockchain.


블록체인 주요 특징
- 탈중앙화
    - 신뢰할 수 없는 환경에서 제3의 신뢰기관 없이 거래를 신뢰할 수 있어야 함

- 분산저장
    - 데이터 가용성(Data Availability), 일부 서버 장애 상황에서도 항상 데이터를 조회/검증/생성할 수 있어야 함

- 투명성 / 안정성
    - 이전 블록 해시를 다음 블록에 넣는 방식으로 위변조 방지
    - 다수 노드의 합의를 통한 이중 지불 방지

- Smart Contract
    - 데이터의 신뢰 뿐만 아니라, 계산(Computing)의 신뢰
    - 트랜잭션마다 정해진 프로그램(계약) 실행 가능

- 성능(Scalability)
    - 트랜잭션 처리 속도(TPS) 향상
    - 빠른 블록 확정(Finality) 확보

- 상호호환성(Interoperability)
    - 블록체인 및 스마트 컨트랙트 간의 데이터 교환

- 프라이버시
    - 개인 데이터 주권 확보
    - 개인정보 보호

Blockchain as a Trust Platform
- Trust is foundational element of business.
- Maintaining trust is expensive, time-consuming, inefficient.
- Blockchain removes the need of trusted 3rd parties.


블록체인이 풀려고 하는 문제들(해외 적용사례)
- 금융주도의 블록체인 활용 사례
- 중개 기관이 필요하거나 디지털화되지 않은 서비스(SWIFT, 장외주식거래등)에 대해 절차 간소화, 자동화하는 데 주로 사용됨
    - 청산결제
        - Digital Asset
            - 자회사간, 국가간 운영되는 청산 결제 시스템을 대체하기 위한 것으로 절차간소화, 자동화를 위한 스마트계약 등 활용
            - 거래를 보다 신속하게 처리하는 것을 목적
            - 중개기관을 없애고 비용과 위험성 절감
    - 해외송금
        - CBW Bank
            - 개인간, 기업간 해외송금을 보다 저렴하고 빠르게 서비스를 제공하기 위해 블록체인 활용
            - 미국과 서유럽간의 국가간 송금에 Ripple에서 개발한 실시간 결제 프로토콜 이용
    - 증권거래
        - Nasdaq
            - 주식시장(장외시장) 등에 블록체인, 스마트계약을 적용, 중개기관의 필요성을 없애고 거래시간 단축
            - 분산된 장부를 통해 주식거래의 개념 증명
            - 투자자에게 주식을 처음으로 이전하기 위해 블록체인 사용
    - 투자
        - KPCB
            - 투자 플랫폼을 통해 창업자에 관한 정보를 제공하고, 투자자는 투자자를 선택하여 디지털 화폐로 직접 투자할 수 있는 기능을 활용
            - 투자자들에게 Edge Coin이 담긴 웹 지갑을 부여하여 스타트업 창업자에게 코인 직접투자 가능
    - 보험
        - Aviva
            - 고가상품(다이아몬드)에 대한 정보를 등록, 관리하며 상품의 움직임을 기록함으로 보험사기 방지와 연계 가능
            - 디지털 통화를 이용하여 보험사와 구매자들이 보석의 거래 기록을 확인, Everledger라는 온라인 레코드북 만듦

- 정부주도의 블록체인 활용 사례
- 거래 내역의 투명성, 추적 가능성 등을 이용하여 정보를 안전하고, 편리하게 보관할 수 있도록 기능을 제공함에 따라 공공 서비스를 위해 블록체인 활용함
    - 전자투표
        - 스페인
            - 투표진행결과를 블록체인에 기록하여 투명성을 유지할 수 있도록 하여 정당투표, 상원 선거 등에 활용
            - 스페인 정당인 자유동맹당은 블록체인 투표시스템을 내부 투표에서 시범적으로 사용
    - 전자화폐
        - 필리핀
            - 국가별 중앙은행에서 발행, 관리하는 공식적인 화폐로 활용 예정
            - 필리핀 내에서 온라인 결제를 위한 공식적인 매개체로 사용될 수 있는 ‘e-peso’ 신설법안 도입
    - 전자시민권
        - 에스토니아
            - 블록체인에 개인의 신원정보를 저장하여, 정부기관에 의해 디지털 신원확인이 가능하도록 기능을 활용
            - 언제 어디서나 에스토니아 정부에 의해 디지털 신원확인이 가능하고 규제 내 온라인 서비스 이용 가능
    - 소유권 기록
        - 온두라스
            - 토지의 소유권을 블록체인에 등록하여 안전하게 저장, 관리하는데 활용
            - 블록체인의 기본기능을 사용하여 안전한 토지 소유권 등록을 구축하기 위해 Factom과 파트너쉽
    - 기록물 관리
        - 미국(Vermont)
            - 정부에서 작성, 발행한 문서 등 기록물 관리 위해 블록체인을 활용
            - 국가 기록물, 스마트계약 및 기타 애플리케이션에 대한 비트코인 기술을 사용하기 위해 입법조치

금투업권 블록체인 컨소시엄 - Chain ID
- 금융투자업 컨소시엄 참가사들을 대상으로 Authentication, Post-Trading, Trading 관련 시스템을 블록체인 기반으로 전환 및 상용화 추진
- 중앙화된 인증 기관 대신 블록체인 특성을 활용한 인증 서비스망 구축으로, 제3자의 영향력을 축소하고 사용자 편의성을 향상시킴
- 블록체인 기반 인증서 관리 시스템
   - 계약 내용
        - 인증서 및 인증서 상태 정보를 스마트 컨트랙트로 공유
        - 각 노드가 전송하는 거래 내역에 인증서 발급 필수 정보(DN, 유효기간, 사용자 공개키 등) 포함
        - 거래 내역이 포함된 노드의 전자서명이 정당할 경우, 발급 요청 정보를 기반으로 인증서 발급 및 계약 데이터 포함
        - 기존 인증 시스템과는 달리 별도의 인증 기관 불필요
        - 별도의 인증 기관 없이 블록체인 자체가 인증기관이 됨
        - SCORE 기반으로 인증서 발급키를 블록마다 생성하여 사용하며, 별도의 인증서 발급키 관리없이 X.509 형식의 인증서 발급
        - 금융기관은 공인인증체계와 같이 RA 역할을 수행
        - 스마트 컨트랙트 기반으로 보안성 강화

    - 계약 내용
        - 인증서 및 인증서 상태 정보를 스마트 컨트랙트로 공유
        - 각 노드가 전송하는 거래 내역에 인증서 발급 필수 정보(DN, 유효기간, 사용자 공개키 등) 포함
        - 거래 내역이 포함된 노드의 전자서명이 정당할 경우, 발급 요청 정보를 기반으로 인증서 발급 및 계약 데이터 포함
        - 기존 인증 시스템과는 달리 별도의 인증 기관 불필요
        - 별도의 인증 기관 없이 블록체인 자체가 인증기관이 됨
        - SCORE 기반으로 인증서 발급키를 블록마다 생성하여 사용하며, 별도의 인증서 발급키 관리없이 X.509 형식의 인증서 발급
        - 금융기관은 공인인증체계와 같이 RA 역할을 수행
        - 스마트 컨트랙트 기반으로 보안성 강화


실용적 블록체인(Practical Blockchain)
- 보험 및 헬스케어컨소시엄 - 스마트보험금청구서비스
    - 간편 인증을 통해서 보험금 청구에 필요한 의무기록을 보험사로 전송하고 보험금 지급까지 원스톱으로 처리
        - 블록체인 기술 적용으로 고객의 보험금 자동청구 실현
        - Smart Contract를 활용한 보험금청구 인증체계 구축 
- 관세청 수입 개인통관정보 블록체인화
    - 관세청 수입 개인통관정보를 블록체인화하여 공공 분야의 다양한 기관 업무에서 활용


- 서울시 블록체인 플랫폼 구축
    - 서울시민이 믿고 사용할 수 있는 서비스 구축을 위해서 블록체인 플랫폼을 구축하는 시범사업 수행


DID (Decentralized Identifier, 분산 ID, 자기주권 ID)
- DID(탈중앙화 신원증명, Decentralized Identifier, 분산아이디, 이하 “DID”)는 기존 신원확인 방식과 달리, 중앙 시스템에 의해 통제되지 않으며 개개인이 자신의 정보에 완전한 통제권(self-sovereign)을 갖도록 하는 기술
    - ID/암호/개인정보가 개인의 통제 하에 있는 모바일 단말에만 저장됨

- DID 서비스 흐름
    - 1. 신원인증기관 DID 등록
    - 2. 신원주 DID 등록
    - 3. Claim 요청
        - Cliam: 신원주가 제출한 주민등록번호, 성별 등의 신원 정보에 대한 주장
    - 4. Verifiable Credential 발급
        - Verifiable Credential: 신원인증기관에 의해 인증되어 증명 가능한 신원 단위 -> 모바일 신분증이라고 생각하면 된다
    - 5. Verifiable Presentation 제출
    - 6. 블록체인 검증
    - 7. 서비스 접근허가

- DID 서비스
    - 발급 기관으로부터 인증 받은 신원을 자신의 단말에만 저장하고 있다가, 필요한 시점에 필요한 서비스에 필요한 정보만 선택적으로 제공
    - 주민등록증을 동사무소로부터 발급 받아, 자신이 소지하고 있다가, 필요한 곳에서 보여주고 신원 확인 받는 오프라인 절차와 동일함

- DID와 DID Document
    - DID는 식별자(Identifier)
    - DID Document는 DID가 자신의 소유임을 증명할 수 있는 문서로 블록체인을 통해 위변조 되지 않았음을 확인

- VC (Verifiable Credential)
    - 신원인증기관에 의해 발급(서명)된 하나 이상의 Claim의 모임. 암호학적 증명이 가능한 Claim(주장)들임
    - 신원인증기관에서 발급한 디지털 신분증이라고 보면 됨
    - 개인정보가 포함되어 있어 자신의 단말에만 저장되는 정보임
