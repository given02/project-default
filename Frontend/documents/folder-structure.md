# Frontend Folder Structure

- Owner: Frontend Developer
- Purpose: Frontend 폴더와 feature 경계를 정의합니다.
- Audience: Frontend Developer
- Dependencies: `../../documents/architecture/dependency-rule.md`
- Next Reading: `frontend-convention.md`

## 구조

```text
{{SOURCE_DIRECTORY}}/
├── app/          # application bootstrap와 provider
├── pages/        # route-level composition
├── features/     # 사용자 기능별 코드
├── components/   # 여러 feature에서 재사용하는 UI
├── api/          # API client 기반
├── assets/       # 정적 asset
├── styles/       # theme와 global style
├── types/        # 순환 의존성이 없는 공유 type
└── utils/        # domain 의미가 없는 utility
```

## 규칙

- feature 전용 코드는 해당 feature 아래에 둡니다.
- 재사용 가능성이 아니라 실제 다중 소비를 근거로 shared 위치로 이동합니다.
- page는 route 조합을 담당하고 복잡한 business interaction은 feature에 위임합니다.
- Backend persistence 구조를 Frontend 폴더 구조에 복제하지 않습니다.
