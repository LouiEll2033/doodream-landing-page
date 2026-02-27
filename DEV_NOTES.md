# 🗒️ DEV NOTES — 두드림AI 개발 메모장

> 개발 중 발견한 이슈, 기술 결정, 참고 사항을 자유롭게 기록합니다.  
> 최신 항목이 위에 오도록 작성해 주세요.

---

## 2026-02-27

### 📌 프로젝트 문서화 시작
- `PROJECT_OVERVIEW.md` — 전체 구조 분석 문서 생성
- `CHANGELOG.md` — 변경 이력 관리 시작
- `TODO.md` — 할 일 목록 관리 시작
- `DEV_NOTES.md` — 개발 메모 시작

---

## 2026-02-24

### 🔧 Baserow API 연동 결정 사항
- **테이블 ID:** `828897`
- **API 토큰:** `KcgCAHCoExTu25HynZgOKHVmWtEOHIHy`
- 컬럼명은 한글 그대로 사용 (`이름`, `연락처`, `이메일`, `신청동기`, `신청일시`)
- `user_field_names=true` 파라미터로 컬럼명을 한글로 사용 가능

### ⚠️ 주의사항
- API 토큰이 클라이언트 JS에 노출되어 있음 → 추후 서버사이드 처리 권장
- 연락처 입력 시 앞자리 0이 숫자 변환으로 사라지는 버그 발견 → `startsWith('0')` 로 보완

### 📱 모달 반응형 처리
- 모바일(`< 768px`): 슬라이드업 (translateY)
- 데스크탑(`>= 768px`): 페이드 + 스케일 (opacity + scale)
- `applyModal` z-index를 200으로 설정 (currModal 100보다 위)

---

## 2026-02-23

### 🔒 2, 3단계 카드 잠금 처리
- `onclick` 이벤트 제거 대신 CSS로 `cursor-not-allowed` + `opacity` 처리
- 2단계: `opacity-70`, 3단계: `opacity-60` (점점 흐릿하게)
- 잠금 메시지: "🔒 X단계 수료 후 개설 예정"

### 📋 커리큘럼 모달 구조 결정
- `max-h-[92dvh]` + `overflow-y-auto` 로 긴 콘텐츠 스크롤 처리
- 헤더는 `sticky top-0` 로 고정
- ESC 키로 모달 닫기 공통 처리 (`document.addEventListener`)

---

## 개발 환경 메모

### 🛠️ 사용 중인 주요 외부 서비스
| 서비스 | 용도 | 비고 |
|--------|------|------|
| Tailwind CSS CDN | 스타일링 | 빌드 없이 바로 사용 |
| Google Fonts | Lexend 폰트 | |
| Google Material Symbols | 아이콘 | Outlined 스타일 |
| **Baserow** | 신청 데이터 DB | 테이블 ID: 828897 |

### 📁 파일 구조 원칙
- 단일 파일 (`index.html`) 으로 유지 (별도 CSS/JS 파일 없음)
- 이미지는 `images/` 폴더에 관리
- 추후 기능 확장 시 파일 분리 고려

### 🎨 색상 기준
```
primary   #a23d15  → 메인 브랜드 (갈색)
secondary #1E4D2B  → 서브 (짙은 초록)
accent    #FA925C  → 강조 (살구/오렌지)
soft-bg   #F2EBD3  → 배경 (아이보리)
```

---

## 🔗 참고 링크
- [Baserow API 문서](https://baserow.io/docs/apis%2Frest-api)
- [Tailwind CSS 공식](https://tailwindcss.com/docs)
- [Material Symbols](https://fonts.google.com/icons)
- [Google Fonts - Lexend](https://fonts.google.com/specimen/Lexend)
