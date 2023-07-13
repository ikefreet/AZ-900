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
<br/><br/><br/><br/>


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
