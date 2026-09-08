# React Ant Design Convention

## 적용 조건과 선택

- **STD-FE-REACT-070** React 프로젝트가 Ant Design을 UI library로 선택한 경우 이 문서의 모든 규칙을 적용합니다.
- **STD-FE-REACT-071** 관리자, 운영 도구와 data 중심 업무 화면에서는 Ant Design을 기본 후보로 검토하고, 선택 여부와 사용 범위를 최초 관련 Requirement에 기록합니다.
- **STD-FE-REACT-072** 브랜드 표현이나 독자적인 interaction이 Ant Design 구조와 충돌하는 사용자용 화면에는 관성적으로 도입하지 않고 화면 설계에 적합한 UI 구현 방식을 선택합니다.

## 구현

- **STD-FE-REACT-073** Ant Design의 theme은 application 경계의 `ConfigProvider`에서 구성하고 색상, typography, spacing, radius와 breakpoint를 화면 설계의 token과 정렬합니다.
- **STD-FE-REACT-074** Button, Form, Modal, Menu, Select와 Table처럼 Ant Design이 제공하는 공통 interaction을 같은 목적으로 다시 구현하지 않습니다.
- **STD-FE-REACT-075** 프로젝트 공통 기본값이나 domain 의미가 필요한 경우 얇은 wrapper component로 캡슐화하고 feature마다 동일한 설정을 복사하지 않습니다.
- **STD-FE-REACT-076** Form validation은 Requirement의 입력 규칙과 오류 계약을 기준으로 구성하고 client validation만으로 server validation을 대체하지 않습니다.
- **STD-FE-REACT-077** theme token과 공개 component API를 사용해 확장하고 내부 DOM 구조나 생성된 CSS class 이름에 의존하지 않습니다.
- **STD-FE-REACT-078** Ant Design component를 사용해도 semantic HTML, keyboard, focus, label과 오류 연결에 관한 Frontend 접근성 Standard를 그대로 적용합니다.
- **STD-FE-REACT-079** 도입하거나 major version을 변경할 때 실제 설치 version의 license, React 호환성, bundle 영향과 breaking change를 확인하고 검증 결과를 Requirement에 기록합니다.
