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
