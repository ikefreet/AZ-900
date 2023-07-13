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
<br/>

**지역 쌍**
- 대부분의 Azure 지역은 300마일 이상 떨어져 있는 동일한 지리적 위치 내의 다른 Azure 지역과 쌍을 이룬다. 이를 통해 한 지리적 위치에서 리소스를 복제할 수 있고 장애로 인한 서비스 중단 현상이 일어날 가능성을 줄일 수 있다.
- Azure 운영 중단이 광범위하게 발생하는 경우 모든 쌍 중 한 개의 영역이 우선시되어 해당 영역 쌍에서 호스팅되는 애플리케이션에 대해 최소 한 개의 영역이 최대한 빨리 복원되도록 한다.
![alt text](https://learn.microsoft.com/ko-kr/training/wwl-azure/describe-core-architectural-components-of-azure/media/region-pairs-7c495a33.png)
