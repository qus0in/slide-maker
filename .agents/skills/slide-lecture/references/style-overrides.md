# 시각 테마 및 스타일 오버라이드 규칙 (Styling & CSS Rules)

## 5.1 배경 우선 색상계 (Background-First Colors)
- **배경색 (Primary Background):** `#02343F` (딥 틸 그린)
- **전경색/텍스트색 (Primary Foreground):** `#F0EDCC` (따뜻한 라이트 옐로우 크림)
- **코드 블록 배경색 (Code Background):** `#0d2026` (맑은 틸-차콜 네이비)
- 슬라이드는 전체적으로 차분하고 집중도 높게 다크 테마를 고수한다.
- 네온, 그라데이션, 글로우(glow), 블러, 드롭 섀도우, 임의의 포인트 컬러 남발을 절대 금지한다.
- *참고: 사용자의 요구사항에 따라 옐로우-블랙(`F2AA4C`, `101820`) 등 프로젝트 커스텀 컬러셋으로 전역 테마가 오버라이드될 수 있다.*

## 5.2 전역 타이포그래피 (Global Typography)
- 모든 폰트는 시스템 기본 폰트를 배제하고 다음 웹폰트를 엄격히 일관되게 사용한다:
  - **제목 (Titles):** `A2z` (에이투지체)
  - **본문 및 내용 (Body):** `KoddiUDOnGothic` (국립재활원 온고딕)
  - **코드 및 에디터 (Code):** `D2Coding`
- 모든 제목, 리스트, 테이블, 캡션, 다이어그램 내 글자체에 동일하게 투영한다.

## 5.3 수직 처짐(my-auto) 무력화 및 상단 고정 (Vertical Alignment Reset)
- Slidev 컴파일러가 본문 요소를 수직 가운데로 밀어버려 내용이 아래로 처지는 현상을 완전 차단한다.
- `cover` 레이아웃을 제외한 일반 슬라이드는 최상위 래퍼의 마진을 조정하여 상단으로 강제 밀착 정렬(`flex-start`, `margin-top: 0 !important`) 시킨다.
- 대제목 뒤에 오는 첫 형제 요소(`h1 + *`)는 `margin-top: 2rem !important;`로 스페이싱을 고정하여 모든 슬라이드의 본문이 일률적인 위치에서 쾌적하게 시작되도록 통제한다.

## 5.4 가로 100% 확장 및 조밀한 줄간격 (100% Width & Line-Height Spacing)
- 블록 요소가 반토막 나거나 뭉개지지 않도록 코드 블록(`pre`), 인용구(`blockquote`), 체크리스트(`ul`)는 가로 100% 너비(`width: 100%`)로 확장 사용한다.
- 텍스트가 분산되지 않고 한눈에 파악되도록 본문 줄 간격(`line-height`)은 **`1.65`**로 정갈하게 제한한다.
- 단락 여백은 `margin-bottom: 0.8rem !important;`, 리스트 여백은 `margin-bottom: 0.55rem !important;`로 밀착하여 조밀하게 조율한다.

## 5.5 style.css 전역 중앙 관리 (style.css Centralization)
- `slides.md` 메인 마크다운 파일 내부에는 `<style>` 태그를 일체 기입하지 않는다.
- 모든 서체 로더, 색상 토큰 변수, 전역 요소 재지정 등 스타일 및 스타일 오버라이드 커스터마이징은 반드시 루트 폴더의 `style.css`에서 중앙 지배 관리한다.
