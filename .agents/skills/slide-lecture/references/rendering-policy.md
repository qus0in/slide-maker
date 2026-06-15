# 출력 및 에이전트 실행 지침 (Rendering & Agent Behavior)

## 7.1 정적 렌더링 보장 (Static Rendering Only)
- 모든 슬라이드는 PDF로 내보내기(Export) 되었을 때 화면 깨짐이나 누락 없이 완벽히 정적으로 인쇄되어야 한다.
- 다음의 실시간 컴파일 기반 동적 인터랙션 및 애니메이션 기법은 **사용을 엄격히 금지**한다:
  - `v-click`, `v-clicks` 등 클릭 기반 노출 시스템
  - transition 효과 및 모션 연출
  - 호버(hover)를 통해서만 정답이나 설명이 밝혀지는 구조
- 슬라이드가 열리자마자 모든 필수 교육 정보가 화면에 즉각적으로 표출되어 고착되어 있어야 한다.

## 7.2 에이전트 실행 및 우선순위 정책 (Agent Priority & Execution)
- AI 에이전트는 교안 작성 시 화려한 기교나 복잡한 레이아웃을 피하고 오직 **가독성, 교육적 효과, 여백 확보**에 모든 역량을 집중한다.
- 우선순위 순서:
  1. **교육적 전달력 및 구조적 명확성** (Pedagogical Clarity)
  2. **초심자 중심의 간결성** (Beginner Readability)
  3. **코드 분량 및 세로 10줄 이내 규칙 준수** (Code Block Limits)
  4. **Bottom Margin Rule 여백 보장** (Bottom Margin Rule)
  5. **정적 PDF 출력 호환성** (Static Compatibility)
  6. **전역 스타일 시트 일관성** (Visual Consistency)
