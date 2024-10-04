# individual_research
주제: CSC 스마트 노인 돌봄을 위한 행동 및 상황인지 기술 연구2

* YOLOv8-Pose를 이용한 낙상 감지
이 프로젝트는 YOLOv8-Pose 모델을 사용하여 낙상 감지 시스템을 개발하는 데 중점을 두고 있습니다. 시스템은 신체의 관절 간 각도를 분석하여 영상에서 실시간으로 낙상을 감지합니다. 목표는 오탐(false positive) 비율을 줄이면서 정확한 낙상 감지를 달성하는 것입니다.

* 주요 기능
1. 실시간 사람 탐지: 사람을 인식하고, 바운딩 박스와 신뢰도 점수(예: `person 0.91`는 사람이 탐지되었을 확률이 91%라는 의미)를 표시합니다.
2. 자세 분석: 신체의 관절 좌표(어깨, 엉덩이, 다리 등)를 추출하여 관절 간의 각도를 계산합니다.
3. 낙상 감지: 상체와 하체 등 신체 부위 간의 각도 기준을 통해 낙상을 감지합니다. 신체 각도가 일정 임계값 이하로 떨어지고 일정 시간 이상 지속되면 낙상으로 판별하고 경고를 발생시킵니다.
4. 맞춤형 낙상 임계값 설정: 시스템은 다음 공식을 사용하여 낙상을 판단합니다: (첫 번째 키포인트 Y좌표 - 마지막 키포인트 Y좌표)  2/3 + 20
  이 공식에 따라 신체의 각도 및 자세가 임계값 이하로 떨어지면 낙상으로 간주됩니다.

* 진행 중인 개선 사항 및 작업 내용
1. 프레임에 낙상 감지(Fall Detected)를 표시: 현재 `person 0.91`과 같은 신뢰도만 출력되고 있으나, 낙상이 감지된 시점에 Fall Detected라는 텍스트를 프레임에 표시할 수 있도록 수정 중입니다.
2. 낙상 여부 기록 기능: 낙상이 발생한 시간대와 그 상태를 텍스트 파일에 기록하는 기능을 추가하여, 언제 낙상이 발생했는지 추적할 수 있도록 개선할 예정입니다.
3. 낙상 감지 시간 변경: 실험 중인 데이터셋의 영상이 10초 미만이므로, 사람이 누워있는 상태를 감지하는 시간 기준을 10초에서 2-3초로 줄일 계획입니다.
4. 정밀한 자세 분석: 앉거나 천천히 움직이는 동작을 낙상으로 잘못 판단하지 않도록 각도 변화와 움직임 속도를 더욱 세밀하게 분석할 예정입니다.
