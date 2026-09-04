# Start Prompt

## 실행 조건

사용자가 공백을 제외하고 `start`만 입력하면 이 시작 절차를 실행합니다. 대소문자는 구분하지 않습니다.

Agent는 첫 응답에서 파일이나 코드를 만들지 않고 아래 질문만 합니다. 사용자의 답변을 받은 뒤 프로젝트 초기화를 진행합니다.

## 최초 응답

다음 내용을 한 메시지로 질문합니다. Agent는 [External Document Access](document-access.md)에 따라 연결을 확인하고 [Artifact Templates](artifacts.md)의 구조를 기준으로 산출물을 안내합니다.

```text
만들고 싶은 프로젝트를 자유롭게 설명해 주세요.

어떤 사용자를 위해 어떤 문제를 해결하는지, 가장 먼저 완성하고 싶은 기능이나 사용자 결과가 무엇인지 포함하면 좋습니다. 아직 정하지 못한 내용은 미정이라고 작성해도 됩니다.

프로젝트 진행 중 산출물을 함께 작성할 수 있도록 새 Microsoft Excel 통합 문서와 화면 설계용 Figma Design 파일을 만든 뒤 현재 작업 환경에서 접근 가능한 편집 링크를 입력해 주세요. Excel 통합 문서는 OneDrive 또는 SharePoint에 저장하고, Codex에서 SharePoint 앱을 Microsoft 계정에 연결해 주세요. 화면 설계에는 Figma 앱 연결이 필요합니다. 세부 worksheet와 column은 프로젝트 설명을 받은 뒤 Agent가 표준 구조에 맞춰 작성합니다. 링크를 불필요하게 공개로 설정할 필요는 없습니다.

1. 요구사항 정의서 — `Overview`, `요구사항 정의서` worksheet를 가진 Microsoft Excel 통합 문서
2. 기능 명세서 — `Overview`, `기능 명세서` worksheet를 가진 별도 Microsoft Excel 통합 문서
3. 화면 설계서 — Figma Design 파일
4. DB 테이블 정의서 — table 목록, table별 정의와 index를 관리할 Microsoft Excel 통합 문서
5. 테스트 시나리오 및 결과서 — Overview, 시나리오 목록, 테스트 케이스 및 결과를 관리할 Microsoft Excel 통합 문서

화면이나 Database를 사용하지 않는 프로젝트라면 해당 항목에 `해당 없음`이라고 작성해 주세요. 요구사항 정의서, 기능 명세서와 테스트 시나리오 및 결과서는 필수입니다.

아래 형식으로 답변해 주세요.

프로젝트 설명:
요구사항 정의 Microsoft Excel 편집 링크:
기능 명세 Microsoft Excel 편집 링크:
화면 설계 Figma 링크:
DB 테이블 정의 Microsoft Excel 편집 링크:
테스트 시나리오 및 결과 Microsoft Excel 편집 링크:
```

## 답변을 받은 뒤

1. 프로젝트 설명과 링크가 있는지 확인합니다.
2. Microsoft Excel 링크에는 SharePoint 앱, Figma 링크에는 Figma 앱을 사용해 실제 원본 접근을 시도합니다.
3. 앱이 없거나 연결되지 않았으면 파일을 다시 요청하기 전에 필요한 앱 설치 또는 계정 연결을 요청합니다.
4. 앱이 연결되어도 파일 권한이 없으면 해당 파일의 권한 부여를 요청합니다.
5. `customs/PROJECT.md`를 만들고 프로젝트 설명, 산출물 링크, 접근 수단과 확인한 연결 상태를 기록합니다.
6. 사용자의 첫 번째 완성 목표를 `REQ-001`로 제안하고 필요한 질문을 이어갑니다.
7. Requirement의 각 단계가 확정될 때 저장소 문서와 대응하는 Microsoft Excel 또는 Figma 산출물을 함께 갱신하고 실제 반영 내용을 다시 확인합니다.
8. 현재 주 컨텍스트는 Architect 역할로 Requirement를 `Ready`까지 작성합니다. 사용자가 구현 진행을 요청하면 [Context Handoff](context-handoff.md)에 따라 프로젝트 전용 Developer Agent 하나를 별도 컨텍스트로 실행합니다.

앱 연결과 파일 권한을 확인한 뒤에도 Microsoft Excel 통합 문서나 Figma에 직접 접근할 수 없으면 저장소 Requirement를 먼저 완성하고, 산출물에 반영할 정확한 내용을 사용자에게 제공합니다. 접근할 수 없는 산출물을 갱신했다고 표현하지 않습니다.
