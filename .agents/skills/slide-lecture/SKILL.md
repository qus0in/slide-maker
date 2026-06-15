---
name: slide-lecture
description: Rules and guidelines for creating beginner-friendly, clean, and static-rendering programming lecture slides using Slidev, focusing on styling overrides, code segregation, blockquotes, and Mermaid standards.
---

# slide-lecture — Programming Lecture Slide Rules (Slidev)

본 스킬은 Slidev를 활용하여 프로그래밍 교안 슬라이드를 작성 및 편집할 때 준수해야 하는 교육 기획, 정보 구조, 포맷팅, 스타일 및 다이어그램에 대한 **원자화된 지배 규칙**을 제공한다.

## When to Use

- Slidev를 사용해 프로그래밍 교안 슬라이드를 생성, 수정 및 리팩토링할 때
- 교육 가독성을 높이기 위해 텍스트, 코드, 그리고 테이블 레이아웃을 조율할 때
- 슬라이드의 PDF 정적 렌더링 호환성과 테마를 점검할 때
- Mermaid 다이어그램을 활용해 런타임 흐름을 시각화할 때

## Core References

| Rule Category | Description | Reference Link |
| :--- | :--- | :--- |
| **교육 기획 원칙** | 단일 개념 원칙, 초심자 가독성, 직관 우선, 점진적 확장 지침 | [lecture-design](references/lecture-design.md) |
| **슬라이드 구조** | 공격적 슬라이드 분할, 하단 20% 여백(Bottom Margin Rule), 대문 미니멀리즘 | [slide-structure](references/slide-structure.md) |
| **코드 격리 및 제약**| 코드/설명 분리, 클래스 선언/활용 분리, 10줄 이내 물리적 제약 | [code-isolation](references/code-isolation.md) |
| **텍스트 포맷팅** | 체크리스트 `- [ ]` 포맷, 용어 정의 blockquote 규칙, 코드 헤더 네이밍 | [text-formatting](references/text-formatting.md) |
| **시각 테마 & CSS** | 색상계 테마, 타이포그래피(A2z, D2Coding 등), flex-start 고정, style.css 중앙 관리 | [style-overrides](references/style-overrides.md) |
| **Mermaid 다이어그램**| 다이어그램 단순화, themeVariables 고정, 분기 괄호 표기, span 라벨 스타일 패딩 우선 Gotcha | [mermaid-standards](references/mermaid-standards.md) |
| **렌더링 & 실행 정책**| PDF 정적 렌더링 보장(v-click 금지), 에이전트 우선순위 정책 | [rendering-policy](references/rendering-policy.md) |
