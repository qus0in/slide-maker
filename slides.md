---
theme: default
background: '#02343F'
class: text-center
highlighter: shiki
lineNumbers: true
drawings:
  persist: false
transition: slide-left
title: JavaScript 예외처리
layout: cover
---

# JavaScript 예외처리

---
layout: default
---

## 학습 체크리스트 (1/2)

- [ ] 에러 방어를 위한 `try-catch` 문의 기본 구조 및 작동 흐름 이해
- [ ] `catch(error)` 매개변수를 통한 에러 객체(`message`, `name`, `stack`) 활용
- [ ] `instanceof` 연산자 기반의 에러 유형별 분기 감지 및 커스텀 익셉션 패턴 적용
- [ ] 예외 조건 발생 시 `throw` 키워드를 이용한 강제 에러 발생 및 제어

---
layout: default
---

## 학습 체크리스트 (2/2)

- [ ] 상위 호출자로 에러 처리를 위임하는 `rethrow` 패턴의 이해 및 활용
- [ ] 예외 발생 여부와 무관하게 필수 실행되는 `finally` 블록의 Cleanup 원리 숙지
- [ ] `finally` 블록 내 `return` 선언 시 앞선 반환값을 덮어쓰는(Override) 동작 파악
- [ ] `try-catch-finally` 블록 레벨 스코프와 상위 `let` 공통 변수 설계 방식 파악

---
layout: default
---

## 예외 처리 (try-catch)

> **예외 처리 (try-catch)**
>
> 런타임 에러 발생 시 프로그램 즉각 종료를 방지하고 예외 대응용 대안 코드를 실행하는 제어 흐름 구조

<br>

* **에러 객체 매개변수**: `catch(err)`의 에러 객체는 `name`, `message`, `stack` 등의 속성 제공
* **매개변수 생략**: ES2019부터 catch 매개변수가 불필요하다면 `catch { ... }` 형태로 생략 가능
* **커스텀 에러 상속**: 내장 `Error` 클래스를 상속받아 커스텀 에러 클래스 정의 및 구분 처리 가능

---
layout: default
---

## 커스텀 에러 클래스 선언

```javascript
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = "ValidationError";
  }
}

function verifyUser(user) {
  if (!user.name) {
    throw new ValidationError("이름 누락!");
  }
}
```

---
layout: default
---

## 예외 감지 및 분기 처리

```javascript
try {
  const user = {}; // 이름 누락 상황
  verifyUser(user);
} catch (error) {
  if (error instanceof ValidationError) {
    console.error(`[검증 오류] ${error.message}`);
  } else {
    console.error(`[기타 오류] ${error.message}`);
  }
}
```

---
layout: default
---

## 에러 던지기 (throw)

> **에러 던지기 (throw)**
>
> 특정 예외 조건 감지 시 예외 발생을 알리기 위해 강제로 에러를 생성하여 던지는 키워드

<br>

* **에러 객체 던지기**: 관례 및 스택 추적 디버깅 정보를 위해 문자열 등이 아닌 `new Error()` 등의 객체를 던지는 것을 권장
* **호출 스택 전파**: `throw` 실행 시 현재 흐름이 즉시 중단되고 호출 스택을 거슬러 올라가며 가장 가까운 `catch` 블록을 탐색
* **rethrow 패턴**: 감지한 에러 중 감당할 수 없거나 상위 위임이 필요한 경우 상위 호출자에게 다시 에러를 던져 예외 처리를 위임

---
layout: default
---

## 예외 발생 및 위임(Rethrow)

```javascript
function loadConfig(configJson) {
  try {
    const config = JSON.parse(configJson);
    if (!config.apiUri) throw new SyntaxError("URI 누락!");
    return config;
  } catch (error) {
    if (error instanceof SyntaxError) {
      return { apiUri: "https://default-api.com" }; // 기본값 복구
    }
    throw error; // 처리 불가능한 에러는 상위로 위임 (Rethrow)
  }
}
```

---
layout: default
---

## 최상위 예외 감지 및 처리

```javascript
try {
  loadConfig("{ broken json... }"); // JSON 파싱 실패 오류 발생
} catch (err) {
  console.log("최상단 감지 에러:", err.message); // 상위 위임 확인
}
```

---
layout: default
---

## 마무리 블록 (finally)

> **마무리 블록 (finally)**
>
> 에러 발생 여부 및 return 실행 여부와 상관없이 제어 흐름의 가장 마지막에 무조건 실행되는 정리용 블록

<br>

* **클린업 코드**: 파일 닫기, 네트워크 연결 종료, 로딩 UI 비활성화 등 필수 실행되어야 하는 뒷정리 코드를 배치함
* **return 흐름 제어**: `try`나 `catch`에서 `return`이 먼저 실행되어도 함수의 반환 전에 `finally` 블록이 먼저 호출됨
* **return 덮어쓰기**: `finally` 내부에서 `return`을 선언하면 이전 블록의 `return` 값은 덮어씌워져(Override) 소멸함

---
layout: default
---

## finally 내 return 덮어쓰기

```javascript
function checkReturnFlow() {
  try {
    console.log("try 블록 진입");
    return "try 결과"; // 즉시 반환하지 않고 finally로 분기
  } finally {
    console.log("finally 블록 진입");
    return "finally가 최종 가로챈 결과!"; // 가로챔 발생
  }
}
```

---
layout: default
---

## return 덮어쓰기 결과 확인

```javascript
console.log(checkReturnFlow());
// 출력 결과:
// "try 블록 진입"
// "finally 블록 진입"
// "finally가 최종 가로챈 결과!"
```

---
layout: default
---

## 예외 처리와 블록 스코프

> **예외 처리와 블록 스코프 (Block Scope)**
>
> try, catch, finally 블록 스코프 내부의 const, let 변수가 외부 및 다른 블록에서 공유되지 않고 고립되는 스코프 구조

<br>

* **블록 레벨 변수**: `try` 블록 안에서 선언된 변수는 `catch`나 `finally` 블록 및 하위 스코프 외부에서 접근할 수 없음
* **공통 변수 설계**: 여러 블록에서 공유하거나 예외 처리 후에도 활용하려면 상위 스코프에서 `let`으로 먼저 공통 선언해야 함

---
layout: default
---

## 예외 처리 스코프 안티패턴

```javascript
function badScope() {
  try {
    const data = "민감한 데이터";
  } catch (err) {
    // console.log(data); // ReferenceError! (data 변수 참조 불가)
  }
}
```

---
layout: default
---

## 상위 스코프 공통 변수 설계

```javascript
function goodScope() {
  let data = null; // 상위 스코프에 let 선언 및 초기화
  
  try {
    data = "성공적으로 불러온 데이터";
  } catch (err) {
    console.error("오류 시점 데이터 참조:", data);
  }
  
  console.log("최종 결과:", data); // 외부 스코프에서 활용 가능
}
goodScope();
```
