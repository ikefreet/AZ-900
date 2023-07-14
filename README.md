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
