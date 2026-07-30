# UI Convention

- Owner: Frontend Developer
- Purpose: 시각적 일관성, 접근성, responsive와 interaction 규칙을 정의합니다.
- Audience: Frontend Developer
- Dependencies: `frontend-convention.md`, `../../documents/product/requirements.md`

## 디자인 기반

- Design source: {{DESIGN_SYSTEM_OR_REFERENCE}}
- Styling: {{STYLING_SOLUTION}}
- Token 위치: {{TOKEN_LOCATION}}

## 규칙

- 색상, spacing, typography와 radius는 token을 사용합니다.
- 동일한 의미의 component와 interaction을 중복 구현하지 않습니다.
- 색상만으로 상태를 전달하지 않습니다.
- keyboard navigation, focus visibility와 semantic HTML을 지원합니다.
- form control에는 연결된 label과 명확한 오류 메시지를 제공합니다.
- loading, empty, error, disabled와 success 상태를 정의합니다.
- supported viewport에서 content와 주요 interaction이 손실되지 않게 합니다.

## 접근성 목표

{{ACCESSIBILITY_STANDARD_AND_LEVEL}}

## 지원 환경

- Browser: {{SUPPORTED_BROWSERS}}
- Viewport: {{SUPPORTED_VIEWPORTS}}
