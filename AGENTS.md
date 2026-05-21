# AGENTS.md — Programming Lecture Slide Rules (Slidev)

> [!CRITICAL]
> This document defines the highest-priority rules for AI coding agents generating or editing programming lecture slides with Slidev in this workspace.
>
> All lecture materials must prioritize:
>
> - educational clarity
> - beginner readability
> - static PDF rendering
> - conceptual separation
> - consistent visual structure

# Core Teaching Principles

## 1. One Concept Per Slide

Each slide should teach exactly one core idea.

Good:
- variable
- function
- loop
- closure
- async/await
- context window

Bad:
- combining multiple unrelated concepts
- entire chapter summaries on one slide

If content becomes dense:
- split into multiple slides
- prefer slide count over compression

## 2. Beginner-Friendly Structure

Assume learners:
- are motivated
- are new to CS terminology
- may struggle with abstraction

Slides should:
- introduce terminology gradually
- explain unfamiliar concepts immediately
- minimize cognitive overload

Preferred:
```md
## Closure

- 함수가 생성될 때
- 주변 변수 기억
- 이후에도 접근 가능
```

Avoid:
```md
- JavaScript lexical environment 기반의 execution context...
```

## 3. Explanation Before Detail

Teaching order should usually follow:

1. intuition
2. simple example
3. terminology
4. deeper mechanics
5. edge cases

Do not start with:
- formal definitions
- specification-heavy wording
- implementation internals

# Information Density & Layout Rules

## 4. Aggressive Slide Splitting

Prefer:
- many short slides
- short bullets
- progressive concept building

Avoid:
- large paragraphs
- full documentation dumps
- textbook-style slides

Target:
- 3~5 bullets per slide
- short lines
- minimal scrolling

**Bottom Margin Rule:**

Leave approximately 20% of slide height empty at the bottom.

- Do not fill slides to the bottom edge
- If content feels tight, split into two slides
- Use `<br>` or blank lines to add breathing room between sections

## 4a. Cover Slide (대문 슬라이드) 미니멀리즘 규칙 [신설]

대문 슬라이드(첫 장)는 완벽한 강의 첫인상과 몰입감을 주기 위해 고도로 절제된 단일 타이틀 디자인을 고수한다.

- **프론트매터 설정:** 반드시 `layout: cover`와 `class: text-center`를 적용하여 수직/수평 완전 정중앙 정렬을 부여한다.
- **콘텐츠 미니멀리즘:** 슬라이드 내에 **부제, 부연 설명, 강의 정보, 작성자 정보(morgan 등)를 전격 배제**하고, 오직 대제목 `#` 하나만 정중앙에 고귀하게 노출시킨다.
- **타이틀 스타일링:** 대문용 메인 제목은 `border-bottom` 밑줄 데코레이션을 생략하고 폰트 크기를 `3.5rem`으로 웅장하게 확대하여 모던하고 절제된 미학을 제공한다.

## 4b. Slidev 수직 처짐(my-auto) 무력화 및 상단 고정 규칙 [신설]

Slidev 컴파일러가 본문 내용을 수직 가운데로 밀어붙여 어정쩡하게 처지게 만드는 현상을 완벽히 차단한다.

- **my-auto 무력화:** 일반 default 및 two-cols 레이아웃에 대해, 최상위 본문 래퍼(`> .my-auto`, `> div.my-auto`)의 상하 마진을 `margin-top: 0 !important; margin-bottom: auto !important;`로 리셋하여 강제로 상단 고정시킨다.
- **일관된 상단 간격 (Breathing Room):** 대제목 `h1` 바로 뒤에 오는 형제 요소(`h1 + *`)는 `margin-top: 2rem !important;`로 스페이싱을 강제 지정하여 모든 페이지에서 똑같은 위치에 정갈하게 본문이 시작되도록 설계한다.

## 4c. 가로 100% 와이드 캔버스 및 촘촘한 가독성 스페이싱 [신설]

블록 요소가 반토막 나거나 가로로 흐려지는 현상을 철폐하고 단단한 밀착 구조를 유지한다.

- **가로 100% Stretch:** 코드 블록(`pre`), 인용구(`blockquote`), 체크리스트(`ul`)는 수축되지 않고 가로 100% 너비(`width: 100%`, `align-items: stretch`)를 전면 사용한다.
- **촘촘한 줄간격 결속:** 문장들이 산만하게 흩어지지 않도록 본문 줄 간격(`line-height`)은 **`1.65`**로 정갈하게 단축한다.
- **여백 초슬림화:** 
  - 단락 여백은 `margin-bottom: 0.8rem !important;`, 리스트 여백은 `margin-bottom: 0.55rem !important;`로 밀착 조율한다.
  - 인용구(`blockquote`)는 내부 패딩(특히 하단 패딩을 `0.3rem`으로 조절) 및 외부 마진(`margin: 0.5rem 0 0.6rem 0`)을 초슬림화하여 Bottom Margin Rule을 완벽히 확보한다.

# Visual Rules

## 5. Background-First Color System

Use:
- `#02343F` as the primary background color
- `#F0EDCC` as the primary foreground/UI/text color
- `#0d2026` as the code block background color (맑은 틸-차콜 네이비)

Recommended usage:
- dark background slides by default
- light text and borders
- minimal accent usage

Preferred:
- flat background
- strong readability contrast
- minimal decoration
- subtle section separation

Do not use:
- neon
- gradients
- glow
- glassmorphism
- blur
- decorative shadows
- random accent colors

Slides should feel:
- stable
- focused
- minimal
- lecture-oriented

## 6. Typography Rules

| Usage | Font |
|---|---|
| Titles | A2z |
| Body | KoddiUDOnGothic |
| Code | D2Coding |

Apply consistently to:
- headings
- bullets
- tables
- diagrams
- captions
- code explanations

# Programming Lecture Rules

## 7. Code Example Policy

Code examples must be:
- short
- isolated
- focused on one idea

Preferred:
```js
const name = "kim"
console.log(name)
```

Avoid:
- full applications
- long setup code
- unrelated imports
- production boilerplate

## 8. Progressive Code Expansion

Teach incrementally.

Preferred flow:
1. minimal example
2. slightly expanded example
3. practical usage
4. edge case

Avoid:
- showing final complex code immediately

## 9. Code Block Constraints

Keep code:
- vertically short
- visually scannable
- syntax-focused

Preferred:
```js
if (loggedIn) {
  showProfile()
}
```

Avoid:
```js
if (
  user &&
  user.profile &&
  user.profile.settings &&
  ...
)
```

## 10. Terminology Rules

When introducing important terminology:
- explain immediately
- use Korean-first wording when possible
- include English term once

Preferred:
```md
> Closure
> 함수가 주변 상태를 기억하는 특성
```

Avoid:
```md
> Lexical Scope Chain Resolution
```

## 10a. Checklist Format

Checklist items must use the `- [ ]` syntax (dash, not asterisk).

Preferred:
```md
- [ ] 함수 선언문과 표현식의 차이 구분 여부
- [ ] 화살표 함수 축약 규칙 이해 여부
```

Avoid:
```md
* [ ] 함수 선언문과 표현식의 차이 구분 여부
```

If checklist items exceed 4~5 entries, split into two slides (1/2, 2/2).

## 10b. Blockquote Term Convention

When using a blockquote to introduce a concept:

1. **First line:** Term only — bold, Korean name + English name in parentheses
2. **Blank `>` line:** Visual separator between term and description
3. **Remaining lines:** Definition in plain Korean

Preferred:
```md
> **클로저 (Closure)**
>
> 함수가 생성될 때 주변 변수를 기억하고,
> 이후에도 접근할 수 있는 특성
```

Avoid:
```md
> **클로저 (Closure)**
> 함수가 생성될 때 주변 변수를 기억하고 이후에도 접근할 수 있는 특성
```

The blank `>` line between the term and the description is mandatory.

## 10c. 미션 카드형 체크리스트 UI 규칙 [신설]

밋밋한 체크리스트 대신 수강생의 학습 성취를 유도하는 미션 카드형 스타일을 엄수한다.

- **카드형 플레이트:** 개별 체크리스트 항목은 은은한 반투명 플레이트 배경(`background: rgba(240, 237, 204, 0.03)`)과 부드러운 외곽 테두리를 주어 미션 카드 형태로 렌더링한다.
- **와일드카드 격퇴:** checklist 내부 요소들의 유연한 가로 flex 정렬 및 정돈을 위해, CSS 전역 와일드카드(`*`) 지정을 지양하고 오직 최상위 래퍼와 직계 클래스를 대상으로 선별 지배 스타일을 부여한다.

# Diagram Rules

## 11. Diagram Simplicity

Use diagrams only when they improve understanding.

Preferred:
- flowchart
- request flow
- runtime lifecycle
- memory structure
- simple architecture

Avoid:
- highly connected graphs
- decorative diagrams
- excessive icons/colors

# PDF & Rendering Rules

## 12. Static Rendering Only

Slides must render perfectly in PDF export.

Strictly forbidden:
- `v-click`
- `v-clicks`
- `transition`
- overlay reveal systems
- hover-only explanations
- animation-dependent teaching

All information must be visible immediately.

# Required CSS Injection

## 13. Mandatory style.css Centralization

To ensure 100% clean structural separation and solid global override in Slidev compilation, **ALL custom CSS styling, typography definitions, and webfont loaders MUST be offloaded to `style.css` in the project root directory.**

The main file `slides.md` **MUST NOT** contain `<style>` tags at the end. 모든 스타일은 `style.css` 에 위임되어 전역적으로 지배 관리된다.

# AI Agent Execution Policy

## 14. Lecture Slide Priority Order

Priority order:

1. educational clarity
2. beginner readability
3. concept separation
4. code readability
5. PDF compatibility
6. visual consistency

## 15. Default Agent Behavior

Unless explicitly instructed otherwise:

Do not:
- add animations
- add decorative visuals
- increase information density
- introduce complex layouts
- prioritize aesthetics over comprehension

Always optimize toward:
- simpler explanations
- shorter slides
- clearer hierarchy
- smaller conceptual steps
- static rendering