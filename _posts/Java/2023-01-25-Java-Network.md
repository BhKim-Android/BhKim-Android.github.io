## Java 네트워크

### 네트워크 기본 개념

#### IP 주소 (Internet Protocol Address)

- IP 주소 : 인터넷 상에서 장치간 통신을 위해 <span style="color:#ff5a54">장치를 식별하는 주소</span>

##### IPv4

- 현재 일반적으로 사용되는 주소로 32bit 구성 (약 43억개)
- [0-255].[0-255].[0-255].[0-255] 와 같이 10진수 4개를 .으로 구분하여 표기 (예, 192.168.0.2)
- 특정 IP는 특별용도로 예약되어 사용 (예, 127.0.01 로컬호스트 주소)

##### IPv6

- IPv4에서의 IP 부족현상을 해결하기 위한 방법으로 128bit로 구성 (43억 * 43억 * 43억 * 43억)
- [0000-FFFF]:[0000-FFFF]:[0000-FFFF]:[0000-FFFF]:[0000-FFFF]:[0000-FFFF]:[0000-FFFF] 와 같이 4자리 16진수 8개를 콜론 으로 연결하여 표기



#### 서브넷 마스크

- 네트워크 ID (NetID)와 호스트 ID(HostID)를 구분하는 마스크
- IP 주소 & 서브넷마스크 = 네트워크 ID
- 예) IP(128.123.222.123), Subnet Mask(255.255.0.0) -> NetID = 128.123.0.0

<span style="color:#ff5a54">하나의 네트워크를 다시 여러 서브 네트워크로 변환하는 경우에도 사용</span>



##### 공인 IP

- 인터넷 상에 서로 다른 장치들 간의 <span style="color:#ff5a54">유일한 식별에 사용</span>되는 IP
- <span style="color:#ff5a54">나라별 별도의 기관에서 관리</span>하며 한국은 인터넷진흥원에서 관리

##### 사설 IP

- 내부망 내에서만 한정적으로 사용되는 IP
- 내부에서만 사용되기 때문에 네트워크별로 중복 가능





### 포트(Port)

- 호스트 내에서 실행되고 있는 <span style="color:#ff5a54">프로세스를 구분</span>하기 위한 16비트의 논리적 할당 (0~65535)
- 호스트의 IP가 집주소 해당하는 개념이라면 Port는 <span style="color:#ff5a54">방반호</span>에 해당
- 호스트의 IP가 컴퓨터를 찾기 위한 정보라면 Port는 프로그램에 해당 (어떤 프로그램이 사용하는 정보인지)

포트번호 : 0 ~ 1023
잘 알려진 포트로 대표적인 인터넷 프로그램이 미리 예약하여 사용하는 포트



#### TCP

- 신뢰성이 높음 (오류시 재전송)
- 연결형 프로토콜 : 통시과정에서 <span style="color:#ff5a54">연결 유지 필요</span> (통신상대가 많은 경우 시스템 부하가 높음)
- 전송데이터 크기는 제한이 없음
- 파일 전송과 같이 신뢰성이 필요한 서비스에 주로 사용
- 전화통신과 유사한 개념



#### UDP

- 신뢰성이 낮음(오류시 또는 미전달시 데이터그램(전달데이터) 삭제)
- 비연결형 프로토콜 : 통신과정에서 <span style="color:#ff5a54">연결 유지 불필요</span> (통신 상대가 많아도 시스템 부하가 낮음)
- 전송데이터의 크기는 65,536 바이트(헤더 포함)로 초과시 나누어 전송
- 실시간성과 같은 성능이 중요한 서비스에 주로 사용
- 우편(소포) 통신과 유사한 개념



### 1:1 통신과 1:N 통신

#### 유니캐스팅

- 두 장치간 1:1 통신 방식 (특정 장치의 주소를 지정하여 통신)
- 물리주소(mac주소)를 기반으로 통신 (자신의 무리주소가 아닌 패킷이 도착하면 프레임을 버림)
- <span style="color:#ff5a54">동일한 내용을 여러 사용자</span>에게 보내고자 하는 경우 비효율적임

#### 브로드캐스팅

- UDP 기반 호스트가 속해 있는 네트워크 내의 모든 장치에 패킷을 전달하는 <span style="color:#ff5a54">1:N 통신 방식</span>
- 라우터의 설정에 따라 라우터를 경유하지 못할 수도 있으며 주로 내부 네트워크에만 한점
- 동일한 내용을 여러 사용자에게 보내고자 하는 경우 효율적임

#### 멀티캐스팅

- 특정 장치들이 데이터를 전달하는 1:N 통신 방식
- 실제 호스트 주소가 아닌 가상 D 클래스 IP 주소에 가입된 호스트에게 데이터 전달
- D 클래스 IP주소 [224-239].[0~255].[0~255].[0~255]