---
name: git
description: Git workflow and commit conventions including interactive rebase, squashing, force-pushing safety, and semantic commit splitting.
---

# Git Commit Conventions & Workflow

본 문서는 프로젝트의 코드 변경 이력을 명확히 하고, 협업과 코드 리뷰의 효율성을 극대화하기 위해 준수해야 하는 Git 커밋 컨벤션과 워크플로우 지침이다.

---

## 1. 의미론적 커밋 분리 (Semantic Commit Splitting)

커밋은 변경 사항의 최소 의미 단위(Atomic Commit)로 나누어야 한다. 서로 다른 성격의 작업(예: 기능 개발과 가이드 문서 수정)을 하나의 커밋으로 결합하는 것을 지양한다.

- **원칙**: 하나의 커밋은 단 하나의 논리적 변경 사항만 담는다.
- **구분 사례**:
  - 교안 본문(`slides.md`) 작성/수정과 에이전트 행동 지침(`AGENTS.md`)의 변경은 성격이 다르므로 개별 커밋으로 분리한다.
  - 리팩토링과 새로운 기능 구현은 커밋을 분리한다.

---

## 2. Git 커밋 메시지 컨벤션 (Commit Message Convention)

프로젝트의 커밋 메시지는 **영어 카테고리(Type/Scope)와 한글 메시지(Subject)의 조합을 의무화**한다. 접두사는 영어로 변경 사항의 종류를 드러내고, 본문 메시지는 명확한 한글로 작성하여 협업 생산성을 높인다.

### 2.1 커밋 메시지 규칙 및 구조

- **구조**: `영어카테고리(영어스코프) : 한글메시지` (콜론 `:` 앞뒤에 공백을 주어 가독성을 확보한다)
- **메시지 한글 작성 의무**: 콜론 뒤의 핵심 메시지(Subject)는 **반드시 한글**로 작성해야 한다. 영문 작성을 엄격히 금지한다.

```
<type>(<scope>) : <한글 메시지>
```

- **Good**: `feat(slides) : 자바스크립트 예외 처리 슬라이드 제작`
- **Bad**: `feat(slides) : create JavaScript exception handling slides` (한글 메시지 의무 위반)

### 2.2 커밋 타입 (Types)
- `feat` : 새로운 기능 추가 (예: 새로운 교안 슬라이드 작성)
- `fix` : 버그 수정
- `docs` : 문서 변경 (예: `AGENTS.md` 수정, `README.md` 수정)
- `style` : 코드 스타일 조율 (코드 자체의 로직 변경 없는 포맷팅 등)
- `refactor` : 코드 리팩토링
- `test` : 테스트 코드 추가 및 수정
- `chore` : 빌드 설정 및 패키지 매니저 등 기타 작업

---

## 3. 대화형 리베이스 및 스쿼시 적극 활용 (Interactive Rebase & Squash)

커밋 이력을 정갈하게 유지하기 위해 원격 저장소에 병합(Merge)하거나 리뷰를 요청하기 전에 **대화형 리베이스(Interactive Rebase)**를 적극적으로 활용한다.

- **커밋 수정 및 결합**: `git rebase -i HEAD~N` 또는 특정 커밋 해시를 활용해 자잘한 피드백 반영 커밋들을 하나로 합치거나(`squash`), 잘못 작성된 커밋 메시지를 변경(`reword`)하고, 필요한 경우 커밋을 쪼갠다(`edit`).
- **히스토리 정리**: 의미 없이 반복되는 `fix: typo` 또는 `test` 같은 지저분한 커밋들은 메인 기능 커밋에 스쿼시(Squash)하여 히스토리를 정돈한다.

---

## 4. 안전한 강제 푸시 (`--force-with-lease`) 적용

리베이스나 커밋 분리 등으로 인해 로컬 커밋 히스토리가 변경되어 원격 저장소와 불일치가 발생할 경우, 일반적인 `git push`는 거절된다. 이 경우 강제 푸시를 수행해야 하나, 절대 `-f` 또는 `--force`를 남발하지 않는다.

- **원칙**: 반드시 **`git push --force-with-lease`** 옵션을 사용한다.
- **이유**: `--force-with-lease`는 내가 마지막으로 인지한 원격 저장소의 상태와 실제 원격 저장소의 상태를 비교하여, 내가 모르는 다른 사람의 새로운 커밋이 원격에 업로드되어 있다면 강제 푸시를 거절하여 다른 사람의 코드가 덮어씌워져 유실되는 대참사를 원천 방지한다.
