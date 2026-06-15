# 교육 기획 및 교수 설계 원칙 (Pedagogical Principles)

## 1.1 슬라이드당 단일 개념 원칙 (One Concept Per Slide)
- 각 슬라이드는 오직 **하나의 핵심 개념**만을 다룬다.
- **Good:** 변수 선언, `this` 키워드 동작, 프로토타입 공유 메서드 등 독립된 주제.
- **Bad:** 여러 개념의 혼용 또는 전체 단원의 서머리를 한 슬라이드에 우겨넣는 구성.
- 복잡하거나 조밀한 개념은 압축하려 하지 말고 **공격적인 슬라이드 분할**을 수행한다.

## 1.2 초심자 지향 가독성 (Beginner-Friendly Language)
- 학습자가 컴퓨터 과학(CS) 전문 용어에 익숙하지 않다고 가정한다.
- 어려운 추상화나 사양(Spec) 중심 설명은 지양하고, 점진적으로 용어를 학습시킨다.
- **Preferred:** "함수가 생성될 때 주변 변수를 기억하여 나중에도 접근 가능한 특성"
- **Avoid:** "자바스크립트의 Lexical Environment 기반 Execution Context의 외부 바인딩 참조 구조..."

## 1.3 직관 우선 설계 (Explanation Before Detail)
- 강의 자료의 전달 순서는 항상 다음 흐름을 따른다:
  1. **직관 (Intuition):** 비유 및 실생활 접근
  2. **간단한 예제 (Simple Example):** 코드 형태
  3. **공식 용어 (Terminology):** 공식 학술 명칭
  4. **심화 동작 (Mechanics):** 메모리 및 구동 방식
  5. **예외 처리 / 경계 조건 (Edge Cases)**
- 절대로 복잡한 정의나 명세(Spec) 내부 규격부터 설명하지 않는다.

## 1.4 점진적 코드 확장 (Progressive Code Expansion)
- 예제 코드는 한 번에 완성형 코드를 제시하기보다 점진적으로 추가 확장한다.
- **Preferred:** 기본 예제 제공 $\rightarrow$ 조금 더 확장된 예제 $\rightarrow$ 실무 활용 $\rightarrow$ 특수한 엣지 케이스 처리 순서로 단계적으로 공개.
