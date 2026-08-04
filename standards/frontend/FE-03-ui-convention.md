# Frontend UI Convention

## 디자인과 재사용

- **STD-FE-030** 색상, spacing, typography, radius, elevation과 breakpoint는 Requirement의 화면 설계에서 정의하거나 참조한 token을 사용합니다.
- **STD-FE-031** 같은 의미와 상호작용을 가진 component를 feature마다 중복 구현하지 않고 실제 다중 소비가 확인되면 공유 component로 이동합니다.
- **STD-FE-032** component variant는 시각적 차이보다 의미와 상태를 기준으로 이름 붙입니다.
- **STD-FE-033** loading, empty, error, disabled, success, partial과 권한 상태를 화면 명세에 따라 명시적으로 구현합니다.

## 접근성

- **STD-FE-034** 가능한 경우 역할을 재구현하지 않고 의미에 맞는 semantic HTML 요소를 사용합니다.
- **STD-FE-035** 모든 interactive 요소는 keyboard로 도달하고 조작할 수 있으며 focus 표시가 보여야 합니다.
- **STD-FE-036** 색상만으로 상태와 오류를 전달하지 않습니다.
- **STD-FE-037** form control에는 인식 가능한 label을 연결하고 오류 메시지를 해당 입력과 연결합니다.
- **STD-FE-038** icon-only control에는 접근 가능한 이름을 제공하고 장식 이미지는 보조 기술에서 제외합니다.
- **STD-FE-039** modal, menu와 동적 알림은 focus 이동, 복귀, escape와 보조 기술 알림을 포함한 상호작용을 완성합니다.
