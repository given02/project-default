# External Document Access

## 목적

이 문서는 Agent가 Microsoft Excel과 Figma 산출물의 링크를 받았을 때 원본 문서에 접근하고 갱신하는 방법을 정의합니다. 링크만 기록하고 접근 방법을 추측하게 두지 않습니다.

## Microsoft 문서 접근 원칙

OneDrive 또는 SharePoint에 저장된 Microsoft Excel 통합 문서는 **SharePoint 앱을 기본 접근 수단**으로 사용합니다.

Agent는 Microsoft 문서 링크를 받거나 `customs/PROJECT.md`에서 읽으면 다음 순서로 처리합니다.

1. 현재 작업 환경에서 SharePoint 앱이 제공되고 Microsoft 계정에 연결되어 있는지 확인합니다.
2. 연결되어 있으면 SharePoint 앱으로 링크의 원본 파일과 metadata를 확인하고 현재 사용자에게 허용된 읽기·쓰기 action을 확인합니다.
3. 원본 파일을 읽은 뒤 현재 Requirement와 관련된 worksheet와 range를 식별합니다.
4. SharePoint 앱이 지원하는 action으로 안전하게 갱신할 수 있으면 원본 파일을 직접 갱신합니다.
5. 정밀한 Excel 편집이 SharePoint 앱만으로 지원되지 않으면 연결된 Microsoft Excel 문서 세션을 사용합니다.
6. 문서 세션도 없으면 원본을 임의로 덮어쓰지 않고 사용자가 Excel 세션을 연결하거나 `.xlsx` 파일을 작업공간에 제공하도록 요청합니다.
7. 갱신 후에는 변경한 worksheet와 range를 다시 읽어 실제 반영 여부를 확인합니다.

SharePoint 앱은 저장소 탐색과 원본 파일 접근을 담당합니다. Spreadsheet 또는 Excel 도구는 통합 문서 내용의 생성, 정밀 편집과 검증을 담당합니다. 도구가 제공하는 실제 action 범위를 확인하지 않고 읽기 또는 쓰기가 가능하다고 가정하지 않습니다.

## 연결되지 않은 경우

SharePoint 앱이 설치되지 않았거나 Microsoft 계정에 연결되지 않았으면 Agent는 다음을 수행합니다.

1. 해당 링크가 OneDrive 또는 SharePoint 문서임을 사용자에게 알립니다.
2. SharePoint 앱 설치 또는 Microsoft 계정 연결이 필요하다고 명확히 요청합니다.
3. 연결 후 같은 링크로 다시 접근을 시도합니다.
4. 사용자가 연결할 수 없을 때만 Excel 문서 세션 연결 또는 `.xlsx` 파일 제공을 대안으로 안내합니다.

앱 연결을 시도하지 않은 채 링크에 접근할 수 없다고 결론 내리거나 새 파일을 별도로 만들지 않습니다.

## Figma 접근 원칙

Figma Design 링크는 Figma 앱을 사용해 접근합니다. Figma 앱이 연결되지 않았거나 권한이 없으면 연결 또는 권한 부여를 요청하고, 접근하지 못한 파일을 갱신했다고 표현하지 않습니다.

## 권한과 보안

- 기존 OneDrive, SharePoint와 Figma 권한을 그대로 따릅니다.
- 공개 링크 전환이나 과도한 권한 부여를 요구하지 않습니다.
- credential, access token, session 정보와 공유 암호를 저장소에 기록하지 않습니다.
- 원본 파일을 교체하거나 전체 내용을 덮어쓰는 action은 대상과 영향 범위를 확인한 뒤 수행합니다.
- 읽기 전용이면 변경할 정확한 worksheet, range와 값을 Requirement에 기록하고 사용자에게 전달합니다.

## 접근 상태 기록

`customs/PROJECT.md`에는 각 외부 서비스의 접근 수단, 연결 상태와 마지막 확인 결과를 기록합니다. 연결 상태는 다음 중 하나를 사용합니다.

- `연결 확인`: Agent가 현재 환경에서 원본을 읽을 수 있음을 확인함
- `쓰기 확인`: Agent가 허용된 갱신과 재확인까지 완료함
- `연결 필요`: 앱 설치 또는 계정 연결이 필요함
- `권한 필요`: 앱은 연결됐지만 원본 파일 권한이 부족함
- `대체 파일 사용`: 사용자가 제공한 로컬 파일로 작업하며 클라우드 원본은 갱신하지 못함

대화가 바뀌면 연결이 유지된다고 가정하지 않고 실제 접근 전에 다시 확인합니다.
