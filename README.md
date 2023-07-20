## 클라우드 개념
**사용량 기반 모델**
- CapEx(자본 지출)
  - 일반적으로 유형 리소스를 구입하거나 보호하기 위한 일회성 선불 지출
  - 새로운 건물, 주차장 재포장, 데이터 센터 구축 또는 회사 차량 구입이 예시
  
- OpEx(운영 지출)
  - 시간이 지남에 따라 서비스 또는 제품에 지출되는 비용
  - 클라우드 컴퓨팅은 소비 기반 모델에서 작동하므로 OpEx에 속한다.

<br/><br/>


## Azure 물리적 인프라

**물리적 인프라**
- Azure의 물리적 인프라는 데이터 센터에서 시작. 전용 전원, 냉각 및 네트워킹 인프라를 갖춘 랙에 배치된 리소스가 있는 시설.
<br/>

**영역**
- 지역이란 가까운 곳에 있고 대기 시간이 짧은 네트워크를 통해 연결된 데이터 센터를 하나 이상 포함하고 있는 지리적 영역을 의미한다.
- Azure는 각 Azure 지역의 리소스를 지능적으로 할당하고 제어하여 워크로드의 적절한 균형을 유지한다.
<br/>

**가용성 영역**
- 가용성 영역은 Azure 지역 내에서 물리적으로 분리된 데이터 센터이다.
- 가용성 영역은 격리 경계로 설저오딘다. 한 영역이 다운되어도 다른 영역은 계속 작동한다.
- 가용성 영역은 고속 프라이빗 광 네트워크를 통해 연결됨.

![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-core-architectural-components-of-azure/media/availability-zones-c22f95a3.png)
<br/><br/>

**지역 쌍**
- 대부분의 Azure 지역은 300마일 이상 떨어져 있는 동일한 지리적 위치 내의 다른 Azure 지역과 쌍을 이룬다. 이를 통해 한 지리적 위치에서 리소스를 복제할 수 있고 장애로 인한 서비스 중단 현상이 일어날 가능성을 줄일 수 있다.
- Azure 운영 중단이 광범위하게 발생하는 경우 모든 쌍 중 한 개의 영역이 우선시되어 해당 영역 쌍에서 호스팅되는 애플리케이션에 대해 최소 한 개의 영역이 최대한 빨리 복원되도록 한다.

![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-core-architectural-components-of-azure/media/region-pairs-7c495a33.png)
<br/><br/>

## Azure 관리 인프라
**Azure 리소스 및 리소스 그룹**
- 리소스
  - Azure의 기본 구성 요소로써 사용자가 만들고, 프로비저닝하고 배포하는 모든 것
    
- 리소스 그룹
  - 리소스를 만들면 리소스 그룹에 두어야 한다.
  - 리소스 그룹에는 많은 리소스가 포함될 수 있지만 리소스는 한 번에 하나의 리소스 그룹에만 속할 수 있다.
  - 일부 리소스는 리소스 그룹 간에 이동될 수 있지만 리소스를 새 그룹으로 이동하면 더 이상 이전 그룹과 연결되지 않는다.
  - 리소스 그룹은 중첩이 불가하다.
  - 리소스 그룹에 작업을 적용하면 해당 작업이 리소스 그룹 내의 모든 리소스에 적용이 된다.
  - 리소스 그룹 삭제 시 리소스 그룹 내 모든 리소스도 같이 삭제된다.

- 구독
  - Azure 제품 및 서비스에 대한 인증되고 권한이 부여된 액세스를 제공한다. 리소스를 프로비저닝하는 것도 가능함.
  - 구독 경계 방식
    - 청구 경계 : Azure 사용에 따른 Azure 계정 청구 방식을 결정한다. 다양한 유형의 청구 요구 사항에 따라 여러 개의 구독을 만들 수 있다. Azure는 비용을 구성하고 관리할 수 있도록 각 구독에 대해 별도의 청구 보고서 및 송장을 생성.
    - 액세스 제어 경계: Azure는 구독 수준에서 액세스 관리 정책을 적용하며, 다른 조직 구조를 반영하기 위해 별도의 구독을 생성한다.

- Azure 관리 그룹
  - 리소스는 리소스 그룹으로 모이고 리소스 그룹은 구독으로 모인다.
  - 관리 그룹은 사용하는 구독 유형에 관계 없이 대규모의 엔터프라이즈급 관리를 제공한다.
  - 관리 그룹은 중첩이 가능하다.


## Azure 아키텍셔 및 서비스
**Azure Virtual Machine**
- Azure VM을 사용하여 클라우드에서 VM을 만들고 사용 가능.


**Azure에서 VM Scaling**
- Virtual Machine Scale Sets
  - 부하 분산된 동일한 VM 그룹을 만들고 관리할 수 있다.
  - 중앙에서 몇 분 만에 VM을 관리, 구성, 업데이트 가능
  - VM 인스턴스의 양적 규모를 수요에 맞춰 자동으로 증감할 수 있으며 정해진 일정에 따라 Scaling 되도록 설정 가능

- 가상 머신 가용성 집합
  - 복원력이 뛰어나고 고가용성인 환경을 빌드하는 데 사용
  - 업데이드 도메인
    - 동시에 다시 부팅할 수 있는 VM을 그룹화
    - 한 번에 하나의 업데이트 도메인 그룹만 오프라인 상태가 되도록 하면서 업데이트를 적용할 수 있음.
    - 하나의 도메인에 있는 모든 컴퓨터가 업데이트됨.
    - 업데이트 프로세스를 진행하는 업데이트 그룹에는 다음 업데이트 도메인에 대한 유지 관리가 시작되기 전에 복구하는데 30분정도 소요됨.

  - 장애 도메인
    - 공통 전원 및 네트워크 스위치로 VM을 그룹화
    - 기본적으로 가용성 집합은 최대 3개의 장애 도메인으로 VM을 분할
    - VM을 각각의 장애 도메인에 두어(다른 전원 및 네트워킹 리소스에 연결되도록 함으로써) 물리적 전원 또는 네트워킹 오류로부터 보호할 수 있음.


**Azure Virtual Desktop**
- 클라우드에서 실행되는 데스크톱 및 애플리케이션 가상화 서비스
- 이를 통해 모든 위치에서 클라우드 호스트 버전의 Windows를 사용할 수 있다.
- 보안
  - 다단계 인증을 통해 사용자 로그인 보호
  - 세부적인 RBAC(역할 기반 액세스 제어)를 사용자에게 할당하여 데이터 엑세스 보호


**Azure Container**
- 컨테이너는 가상화 환경이다.
- Azure Container Instances는 가상 머신을 관리하거나 추가 서비스를 채택하지 않고도 Azure에서 컨테이너를 실행하는 가장 빠르고 간단한 방법이다.
- Azure Container Instances는 PaaS 제품


**Azure Functions**
- 이벤트 기반의 서버리스 컴퓨팅 옵션
- VM이나 컨테이너를 사용해 앱을 빌드한 경우에는 만든 앱의 기능을 작동하려면 이러한 리소스가 실행 중이어야 함.
- 기본 플랫폼이나 인프라가 아니라 서비스를 실행하는 코드에 대해서만 관심 있는 경우 이상적 (REST 요청을 통한 이벤트, 타이머 또는 다른 Azure 서비스로부터 받은 메시지에 대한 응답으로 작업을 수행해야하는 경우 등)
- 수요에 따라 자동으로 Scaling이 된다.
- 트리거 때 코드를 실행하고 함수가 완료될 때 자동으로 리소스 할당을 해제한다.


**Azure App Service**
- 인프라를 관리할 필요 없이 원하는 프로그래밍 언어로 웹앱, 백그라운드 작업, 모바일 백 엔드 및 RESTful API를 빌드하고 호스트 가능
- 자동 확장 기능과 고가용성을 제공
- Windows 및 Linux를 지원하며 GitHub, Azure DevOps 또는  Git 레포지토리에서 자동화 된 배포를 사용하여 지속적인 배포 모델을 지원
- 웹 애플리케이션, REST API 및 모바일 백 엔드를 호스트하는 HTTP 기반 서비스


**Azure Virtual Network**
- Azure Virtual Network와 Virtual Subnet을 사용하여 VM, 웹앱 및 데이터베이스와 같은 Azure 리소스가 서로 통신할 수 있고 인터넷의 사용자 및 온-프레미스 클라이언트 컴퓨터와 통신할 수 있다.
- Networking Functions
  - 격리 및 구분 : 격리된 여러 가상 네트워크를 생성 가능.
  - 인터넷 통신
  - Azure 리소스 간 통신
  - 온-프레미스 리소스와 통신
  - 네트워크 트래픽 라우팅
  - 네트워크 트래픽 필터링
  - Virtual Network 연결


**Azure VPN**
- VPN Gateway
  - Virtual Network Gateway 유형
  - 모든 데이터 전송은 인터넷을 통과할 때 프라이빗 터널 내부에서 암호화됨
  - 정책 기반 VPN Gateway
    - 각 터널을 통해 암호화되어야 하는 패킷의 IP 주소를 정적으로 지정
    - 이러한 유형의 디바이스는 해당 IP 주소 세트에 대해 모든 데이터 패킷을 평가하여 해당 패킷이 전송될 터널을 선택한다.
  - 경로 기반 Gateway
    - IPSec 터널이 네트워크 인터페이스 또는 가상 터널 인터페이스로 모델링된다.
    - IP 라우팅에 따라 각 패킷을 전송할 때 사용할 터널 인터페이스 중 하나가 결정된다.
    - 온-프레미스 디바이스에서 주로 사용되며 토폴로지 변경에 대한 복원력이 좋다.


**Azure ExpressRoute**
- Azure ExpressRoute를 사용하면 연결 공급자의 도움을 받아 프라이빗 연결을 통해 온-프레미스 네트워크를 Microsoft 클라우드로 확장 가능.
- Microsoft Azure 및 Microsoft 365와 같은 Microsoft 클라우드 서비스에 대한 연결 지원
- 연결은 공동 배치 시설의 연결 공급자를 통해 Any-to-Any(IP VPN) 네트워크, 지점 간 이더넷 네트워크 또는 가상 교차 연결에서 수행 가능
- 퍼블릭 인터넷 사용 안함.
- ExpressRoute Global Reach로 모든 지역에서 Microsoft 서비스에 글로벌 연결 가능
- BGP를 통한 네트워크와 Microsoft 간 동적 라우팅


**Azure DNS**
- Microsoft Azure 인프라를 사용하여 이름 분석을 하는 DNS 도메인용 호스팅 서비스
- 자격증명, API, 도구 및 대금 청구를 사용하여 DNS 레코드 관리 가능
- 이점
  - 안정성 및 성능
  - 보안
  - 사용 편의성
  - 사용자 지정 가능 가상 네트워크
  - 별칭 레코드



## Azure Storage

**Storage 계정**
- HTTP 또는 HTTPS를 통해 전 세계 어디에서나 액세스할 수 있는 Azure Storage 데이터에 고유한 네임스페이스를 제공
- 계정의 데이터는 안전하고 가용성과 내구성이 높으며 대규모 확장이 가능
- 계정 유형
  - LRS(로컬 중복 스토리지)
  - GRS(지역 중복 스토리지)
  - RA-GRS(읽기 액세스 지역 중복 스토리지)
  - ZRS(영역 중복 스토리지)
  - GZRS(지역 영역 중복 스토리지)
  - RA-GZRS(읽기 액세스 지역 영역 중복 스토리지)
 
**Storage 계정 Endpoint**
- Azure Storage 계정을 사용할 경우 데이터에 대해 Azure에 고유한 네임스페이스를 갖는다.
- 계정 이름과 Azure Storage 서비스 엔드포인트의 조합이 스토리지 계정의 엔드포인트가 된다.
- Storage 계정 이름은 3자에서 24자 사이여야 하고 숫자 및 소문자만 포함 가능
- Storage 계정 이름은 Azure 내에서 고유해야 한다.

**Azure Storage 중복성**
- 스토리지 계정이 오류 발생 시에도 가용성 및 내구성 목표를 충족하는지 확인
- 기본 지역의 중복성
  - Azure Storage 계정의 데이터는 항상 기본 지역에서 3번 복제된다.

  - 로컬 중복 Storage(LRS)
    - 기본 지역의 단일 데이터 센터내에서 데이터를 3번 복제
    - 지정된 1년 동안 개체에 11개의 9(99.9999%) 이상의 내구성을 제공
    - 가장 저렴한 중복성 옵션이지만 다른 옵션에 비해 내구성이 가장 낮음.
    - 서버 랙 및 드라이브 오류로부터 데이터를 보호
    
    ![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-azure-storage-services/media/locally-redundant-storage-37247957.png)
    <br/><br/>

  - 영역 중복 Storage(ZRS)
    - 가용성 영역 지원 지역의 경우, 주 지역의 3가지 Azure 가용성 영역에서 Azure Storage 데이터를 동기적으로 복제
    - 지정된 1년 동안 개체에 12개의 9(99.9999%) 이상의 내구성을 제공
    - 영역을 사용할 수 없게 되는 경우에도 읽기 및 쓰기 작업에 모두 계속해서 액세스 가능
    - 고가용성이 필요한 시나리오인 경우 사용됨.

    ![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-azure-storage-services/media/zone-redundant-storage-6dd46d22.png)
    <br/><br/>

- 보조 지역의 중복성
  - 높은 내구성이 필요한 애플리케이션의 경우 스토리지 계정의 데이터를 주 지역에서 수백 킬로 떨어진 보조 지역에 추가로 복사할 수 있다.
  - 기본적으로 기본 지역에 대한 장애 조치가 없는 한 보조 지역의 데이터는 읽거나 쓸 수 없다.
  - 장애 조치가 완료되면 보조 지역은 기본 지역이 되고 데이터를 다시 읽고 쓰기가 가능하다.
    
  - 지역 중복 Storage(GRS)
    - LRS를 사용하여 주 지역의 단일 물리적 위치 내에서 데이터를 동기적으로 3번 복사
    - 그 후 LRS를 사용하여 보조지역(지역 쌍)의 단일 물리적 위치에 데이터를 비동기적으로 복사
    - 지정된 1년 동안 16개의 9(99.9999%) 이상의 내구성을 제공

    ![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-azure-storage-services/media/geo-redundant-storage-3432d558.png)
    <br/><br/>
    
  - 지역 영역 중복 Storage(GZRS)
    - 가용성 영역 전체의 중복성으로 제공되는 고가용성과 지역에서 복제를 통해 제공되는 지역 중단 방지를 결합
    - GZRS Storage 계정의 데이터는 주 지역의 Azure 가용성 영역에 복사되며 지역 재해로부터 보호하기 위해 LRS를 사용하여 보조 지리적 지역에도 복제됨.
    - 재해 복구를 위해 최대 일관성, 내구성과 가용성, 뛰어난 성능 및 복원력이 필요한 경우 사용됨.

    ![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-azure-storage-services/media/geo-zone-redundant-storage-138ab5af.png)
    <br/><br/>


**Azure Storage Service**
- Azure Blob : 텍스트 및 이진 데이터에 대한 확정성이 뛰어난 Storage. 빅 데이터 분석에도 쓰임
- Azure Files : 클라우드 또는 온-프레미스 배포에 대한 관리되는 파일 공유
- Azure Queue : 애플리케이션 구성 요소 간에 안정적인 메시징을 위한 메시징 저장소
- Azure Disk : Azure VM용 블록 수준 Storage Volume

- 이점
  - 내구성 및 고가용성
  - 보안
  - Scaling 기능
  - 자동 관리
  - 액세스 가능(HTTPS&HTTPS, REST API...etc)


**Azure Migrate**
- 온-프레미스 환경에서 클루아드로 Migration하는 데 사용

- Azure Data Box
  - 빠르고 저렴하며 신뢰할 수 있는 방식으로 대량의 데이터 전송을 지원하는 물리적 Migration Service
  - 디바이스의 최대 사용 가능한 스토리지 용량 = 80TB


**Azure 파일 이동 옵션**
- AzCopy
  - 파일을 복사하는데 사용되는 명령줄 유틸리티
  - Storage 계정 간에 파일을 복사하고 동기화하는 것도 가능

- Azure Storage Explorer
  - Azure Storage 계정에서 파일 및 Blob을 관리하는 그래픽 인터페이스를 제공하는 독립 실행형 애플리케이션
  - Windos, Linux, MacOS에서도 지원됨

- Azure 파일 동기화
  - Azure Files에서 파일 공유를 중앙 집중화하고 Windows 파일 서버의 유연성, 성능 및 호환성을 유지하는 도구
  - SMB, NFS 및 FTPS를 포함하여 로컬로 데이터에 액세스하기 위해 Windows Server에서 사용할 수 있는 모든 프로토콜을 사용 가능
  - 전 세계에서 필요한만큼의 많은 캐시를 가질 수 있다.
  - 동일한 데이터 센터 내에서 서버 이전이 가능


## Azure ID, 액세스 및 보안
**Azure Active Directory**
- Microsoft 클라우드 애플리케이션과 개발하는 클라우드 애플리케이션 모두에 로그인하고 액세스할 수 있는 Directory 서비스
- ID 계정을 관리하며 Microsoft에서 해당 서비스를 전역적으로 사용할 수 있도록 지원
- 제공되는 서비스
  - 인증
  - Single Sing-On
  - 애플리케이션 관리
  - 디바이스 관리
- Active Directory와 Azure AD를 연결하여 클라우드와 온-프레미스 간에 일관된 ID 환경을 사용할 수 있다.

**Azure Active Directory Domain Service**
- 도메인 조인, 그룹 정책, LDAP(Lightweight Directory Access Protocol) 및 Kerberos/NTLM 인증과 같은 관리되는 도메인 서비스를 제공하는 서비스
- 작동 방식
  - Azure AD DS 관리되는 도메인을 만들 때 고유한 네임스페이스를 정의
  - 이 네임스페이스는 도메인 이름
  - 두 개의 Windows Server 도메인 컨트롤러가 선택한 Azure 지역에 배포. 이 DC 배포를 복제본 세트라고 합니다.
  - 이러한 DC를 관리, 구성 또는 업데이트할 필요가 없다. Azure 플랫폼은 Azure Disk Encryption을 사용한 저장 데이터 백업 및 암호화를 포함하여 관리되는 도메인의 일부로 DC를 처리한다.


**Azure 인증 방법**
- Single Sign-On : 사용자가 한 번 로그인하고 해당 자격 증명을 사용하여 여러 공급자의 여러 리소스 및 애플리케이션에 액세스. 다른 애플리케이션과 공급자가 초기 인증자를 신뢰해야함
  
- 다단계 인증(MFA) : 로그인 프로세스 중에 사용자에게 식별의 추가 양식을 요청하는 프로세스
  
- 암호 없는 인증 : 암호가 제거되고 사용자가 소유하고 있거나 알고 있는 인증 수단으로 대체되는 수단(애플리케이션 인증, 지문, PIN...etc)
  - Azure의 암호 없는 인증 수단
    - 비즈니스용 Windows Hello : 지정된 Windows PC 정보 사용
    - Microsofot Authenticator 앱
    - FIDO2 보안 키

**Azure 역할 기반 액세스 제어**

![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-azure-identity-access-security/media/role-based-access-scope-4b12a8f3.png)

- Azure RBAC은 계층 구조로써 부모 범위에서 액세스 권한을 부여할 때 해당 권한은 모든 자식 범위에서 상속된다.


**심층 방어**
- 정보를 보호하고 무단 접근을 통한 도난 방지 목적
- 데이터에 무단으로 액세스하기 위한 공격 진행 속도를 늦추는 여러 메커니즘을 사용하는 전략

- 방어 계층

  ![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-azure-identity-access-security/media/defense-depth-486afc12.png)

  - 물리적 보안
    - 물리적으로 건물에 대한 액세스를 보호하고 데이터 센터 내의 컴퓨팅 하드웨어에 대한 액세스를 제어

  - ID 및 액세스
    - ID를 안전하게 보호하고, 필요한 것에만 액세스 권한을 부여하고 로그인 이벤트 및 변경 내용이 기록되게 함
    - 인프라에 대한 접근 및 제어 변경을 통제
    - SSO(Single Sign-On) 및 다단계 인증을 사용
    - 이벤트 및 변경 내용 감사

  - 경계
    - 리소스에 대한 네트워크 기반 공격으로부터 보호
    - DDoS 방지 기능을 사용하여 사용자의 시스템 가용성에 영향을 주기 전에 대규모 공격을 필터링
    - 경계 방화벽을 사용하여 네트워크에 대한 악의적인 공격을 식별하고 경고

  - 네트워크
    - 모든 리소스에 대한 네트워크 연결을 제한하여 필요한 것만 허용하는 역할을 함
    - 리소스 간의 통신 제한
    - 기본적으로 Deny
    - 인바운드 인터넷 액세스를 금지하고 필요한 경우 아웃바운드 액세스를 제한
    - 온-프레미스 네트워크에 대한 보안 연결을 구현

  - Compute
    - 컴퓨팅 리소스를 안전하게 보호하고 보안 문제를 최소화하는 적절한 제어 방식 생성
    - 가상 머신에 대한 액세스 보호
    - 디바이스에 Endpoint 보호 구현 및 시스템을 최신 상태로 업데이트

  - 애플리케이션
    - 애플리케이션이 안전하고 취약성이 없는지 검사
    - 중요한 애플리케이션 비밀을 안전한 저장 매체에 저장

  - 데이터
    - 데이터의 기밀성, 무결성 및 가용성을 보장하기 위한 제어 및 프로세스 적용


## Azure 관리 및 거버넌스

**Azure 비용 관리**
- Azure는 인프라 및 시설을 구축하고 유지 관리하는 데 드는 CapEx(자본 비용)에서 컴퓨팅, 스토리지, 네트워킹 등과 같이 필요에 따라 인프라를 임대하는 OpEx(운영 비용)로 개발 비용을 전환
- OpEx 비용에 영향을 주는 요인
  - 리소스 유형
  - Consumption(종량제)
    - 청구 기간 동안 사용하는 리소스에 대해 지불하는 클라우드 결제 모델 사용량만큼 지불
    - 미리 정해진 양의 클라우드 리소스를 사용할 것을 약정하는 예약 모델도 존재. 경우에 따라 최대 72% 할인
  - 유지 관리
  - Geography
  - 구독 유형
  - Azure Marketplace

- 요금 계산기
  - Azure에서 리소스를 프로비저닝하기 위한 예상 비용을 제공
  - 어디까지나 예측 및 추정용

- TCO 계산기 온-프레미스 인프라를 실행하는 비용을 Azure 클라우드 인프라와 비교하는데 도움이 되도록 설계됨

- Azure Cost Management
  - Azure 리소스 비용을 신속하게 확인하고, 리소스 지출에 따라 경고를 만들고, 리소스 관리를 자동화하는 데 사용할 수 있는 예산을 생성하는 기능 제공


**Azure Blueprints**
- 클루아두 구독 또는 환경 배포를 표준화
- 새 구독마다 Azure Policy와 같은 기능을 구성하는 대신 새 구독을 만들 때 적용되는 반복 가능한 설정 및 정책을 정의할 수 있음

- 아티팩트
  - 청사진 정의의 각 구성 요소
  - Azure Blueprints는 연결된 아티팩트에서 모든 요구 사항, 설정 및 구성에 따라 새 환경을 배포하는데 다음과 같은 항목을 포함할 수 있다.
    - 역할 할당
    - 정책 할당
    - Azure Resource Maanger 템플릿
    - Resource Group

**Azure Policy**
- Resource를 제어하거나 감사하는 정책을 만들며 관리할 수 있는 서비스
- Resource를 평가하고 사용자가 만든 정책을 준수하지 않는 Resource를 강조
- 정책 미준수 Resource 및 구성을 자동으로 수정하여 무결성 보장

**리소스 잠금**
- 리소스를 실수로 삭제하거나 변경하는 것을 방지


## Azure 리소스 관리 및 배포용 기능과 도구

**Azure와의 상호 작용 도구**
- Azure Portal
  - 명령줄 도구의 대안을 제공하는 웹 기반의 통합 콘솔
  - 그래픽 사용자 인터페이스를 사용하여 Azure 구독을 관리할 수 있다.
  - 복원력 및 지속적인 가용성을 위해 설계됨

- Azure Cloud Shell
  - Shell을 사용하여 Azure 리소스를 만들고 구성하고 관리할 수 있는 브라우저 기반 Shell 도구
  - Azure PowerShell 및 Bash Shell인 Azure CLI 지원

- Azure PowerShell
  - 개발자, DevOps 및 IT 전문가가 cmdlet이라는 명령을 실행할 수 있는 Shell
  - cmdlet을 통해 Azure REST API를 호출하여 Azure에서 관리 작업을 수행
  - 스크립트로 명령을 캡처하면 프로세스의 반복 및 자동화 가능

- Azure CLI
  - 기능적으로는 Azure PowerShell과 동일하지만 명령 구문이 다르다.
  - 불연속 작업을 처리하거나 코드를 통해 복잡한 작업을 오케스트레이션할 수 있다.


**Azure Arc**
- 일관적인 다중 클라우드 및 온-프레미스 관리 플랫폼을 제공하여 거버넌스 및 관리를 간소화
- Azure Resource Manager(ARM) 활용 시, 규정 준수 및 모니터링을 하이브리드 및 다중 클라우드 구성으로 확장 가능
- 다음 작업을 수행할 수 있는 통합된 방법을 제공
  - 기존의 비 Azure 리소스를 ARM에 프로젝팅하여 전체환경을 함께 관리
  - 마치 Azure에 실행되는 것처럼 멀티 클라우드 및 하이브리드 가상 머신, Kubernetes 클러스터 및 데이터베이스를 관리
  - 실제 위치에 관계없이 친숙한 Azure 서비스 및 관리 기능 사용
  - Azure Arc 지원 Kubernetes 클러스터 및 클러스터 확장을 기반으로 사용자 지정 위치를 추상화 계층으로 구성


**Azure Resource Manager 및 Azure ARM 템플릿**
- ARM은 Azure용 배포 및 관리 서비스이다.
- 스크립트가 아닌 선언적 템플릿을 통해 인프라 관리
- 리소스를 개별적으로 처리하는 대신, 솔루션의 모든 리소스를 그룹으로 배포, 관리 및 모니터링
- 개발 수명 주기 내내 솔루션을 다시 배포
- 리소스가 올바른 순서로 배포되도록 리소스 간의 종속성 정의
- 모든 서비스에 액세스 제어를 적용
- 리소스에 태그를 적용하여 구독의 모든 리소스를 논리적으로 구성

- ARM 템플릿
  - Resource Manager 템플릿은 Azure에 무엇을 배포하는지 정의하는 JSON 파일
  - 이점
    - 선언적 구문
    - 반복 가능한 결과
    - 오케스트레이션
    - 모듈식 파일
    - 확장성


## Azure 모니터링 도구

**Azure Advisor**
- Azure 리소스를 평가하고, 안정성, 보안 및 성능 개선, 운영 우수성 달성 및 비용 절감에 도움이 되는 권장 사항 제공
- 제공되는 권장 사항은 다음과 같다
  - 안정성
  - 보안
  - 성능
  - 운영 우수성
  - 비용

**Azure Service Health**
- 특별히 배포된 리소스와 Azure의 전반적인 상태를 추적 가능
- Azure 상태, 서비스 상태 및 리소스 상태를 사용하여 Azure 서비스 및 지역의 전역 상태부터 특정 리소스까지 Azure 환경을 완전히 볼 수 있다.


**Azure Monitor**
- 리소스에 대한 데이터를 수집하고, 해당 데이터를 분석하고, 정보를 시각화하고, 결과에 대한 작업을 수행하는 플랫폼
- Azure 리소스, 온-프레미스 리소스, 다른 클라우드 공급자와 호스트되는 가상 머신과 같은 다중 클라우드 리소스를 모니터링할 수 있다.

![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-monitoring-tools-azure/media/azure-monitor-overview-614cd2fd.svg)


**Azure Log Analytics**
- Azure Monitor에서 수집한 데이터에 대한 로그 쿼리를 작성하고 실행하는 Azure Portal 도구
- 간단하고 복잡한 쿼리와 데이터 분석을 모두 지원하는 강력한 도구
- 레코드 집합을 반환하는 간단한 쿼리를 작성한 다음, Log Analytics 기능을 사용하여 레코드를 정력, 필터링, 분석할 수 있다.


**Application Insights**
- 웹 애플리케이션을 모니터링
- Azure, 온-프레미스 또는 다른 클라우드 환경에서 실행되는 애플리케이션을 모니터링할 수 있다
- 다음과 같은 광범위한 정보를 모니터링 할 수 있다.
  - 요청 속도, 응답 시간 및 실패율
  - 외부 서비스로 인해 속도가 느려지는지 확인하기 위한 종속성 횟수, 응답 시간 및 실패율
  - 사용자의 브라우저에서 보고된 페이지 보기 및 로드 성능
  - 속도, 응답 시간 및 실패율을 포함하여 웹 페이지의 AJAX 호출
  - 사용자 및 세션 수
  - CPU, 메모리 및 네트워크 사용량과 같은 Windows 또는 Linux 서버 컴퓨터의 성능 카운터
