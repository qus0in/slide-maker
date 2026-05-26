---
theme: default
background: '#02343F'
class: text-center
highlighter: shiki
shikiConfig:
  themes:
    dark: one-dark-pro
    light: one-dark-pro
lineNumbers: true
drawings:
  persist: false
transition: none
title: Agentic Coding Environment
layout: cover
---

# Agentic Coding Environment

---
layout: default
---

## 학습 체크리스트 (1/2)

- [ ] 특정 벤더나 독점 모델에 종속되지 않는 에이전틱 코딩 도구의 필요성 이해
- [ ] OpenCode CLI 설치 및 로컬 터미널 환경에서의 정상 실행 확인
- [ ] OpenCode 기본 무료 모델의 사용 제한 및 프롬프트 보안 주의사항 인지

---
layout: default
---

## 학습 체크리스트 (2/2)

- [ ] Nvidia NIM(NVIDIA Inference Microservice)의 개념 및 무료 API 한도 파악
- [ ] Nvidia Developer 포털을 통한 가입 및 NIM API Key 발급 완료
- [ ] OpenCode에 NIM API Key를 연동하여 Nemotron 3 Super 외부 고성능 모델 적용
- [ ] 성능 분석 사이트 정보를 기반으로 작업에 맞는 최적의 LLM 탐색 및 변경

---
layout: default
---

## 에이전틱 유연성의 의의

> **에이전틱 유연성 (Agentic Flexibility)**
>
> 특정 벤더나 독점 모델에 종속되지 않고 다양한 LLM을 유연하게 교체하며 활용할 수 있는 역량

- **독점 모델 의존성 탈피**: Claude Code, Codex 등 특정 벤더 제품의 서비스 제약 극복
- **비용 및 성능 최적화**: 로컬 프라이빗 모델부터 상용 초고성능 모델까지 자유롭게 설계
- **기술 발전 속도 수용**: 나날이 변화하는 글로벌 LLM 생태계의 최신 모델을 즉각 연동

---
layout: default
---

## OpenCode 에이전트 CLI

> **오픈코드 (OpenCode)**
>
> 다양한 거대언어모델(LLM)을 연동하여 로컬 환경에서 개발을 보조하는 독립형 에이전틱 CLI 도구

- **높은 유연성**: 단일 서비스 벤더에 종속되지 않는 유연한 모델 교체 아키텍처 제공
- **로컬 개발 최적화**: 터미널 환경에 직접 통합되어 개발 작업 흐름의 맥락을 끊김 없이 보조
- **광범위한 확장성**: 상용 모델뿐만 아니라 다양한 오픈소스 및 로컬 추론 모델 연동 지원

---
layout: default
---

## OpenCode 기본 무료 모델

> **기본 무료 모델 (Built-in Free Model)**
>
> 외부 API 키 등록 없이도 에이전트 CLI 실행 즉시 제공되는 내장 추론 모델

- **별도 등록 불필요**: 복잡한 클라우드 결제나 계정 생성 없이 즉시 사용 가능한 상태 보장
- **무료 추론 한도**: 하루 최대 200회 분량의 에이전틱 코딩 요청 기회 제공
- **기본 탑재 엔진**: 효율적인 속도와 가벼운 성능을 갖춘 DeepSeek V4 Flash Free 지원

---
layout: default
---

## 무료 모델 사용 시 보안 주의사항

> **데이터 프라이버시 (Data Privacy)**
>
> 외부 API 연동 및 서비스 이용 시 소스코드나 개인정보 등의 민감 데이터가 무단 유출되거나 재학습되지 않도록 방지하는 보안 정책

- **프롬프트 데이터 재학습**: 기본 무료 모델에 제공된 입력 데이터는 AI 모델 재학습에 이용됨
- **민감 데이터 입력 주의**: API 키, 사내 핵심 소스코드, 개인정보 탑재 프롬프트 작성 제한
- **보안 권장 방향**: 독립된 서드파티 고성능 API Key를 활용하거나 보안 인프라 연동 필수

---
layout: default
---

## OpenCode 설치 및 실행 절차

- **설명**: 로컬 터미널 환경에 OpenCode CLI를 간편하게 세팅하고 구동하는 과정입니다.
- **절차 안내**:
  1. CLI 설치 스크립트를 다운로드하여 셸 환경에 환경 변수 및 실행 파일 등록
  2. 터미널 환경에서 `opencode` 명령어를 수행하여 대화형 셸 활성화
  3. 에이전트 대화 창 내부에서 `/models` 명령어를 실행하여 사용 가능한 모델 목록 탐색
  4. 기본 탑재된 `DeepSeek V4 Flash Free` 모델을 선택하여 구동 준비 완료

---
layout: default
---

## OpenCode CLI 설치 및 에이전트 구동

```sh
# 1. 설치 스크립트 실행 및 터미널 환경 연동
curl -fsSL https://opencode.ai/install | bash

# 2. OpenCode 에이전트 실행
opencode
```

---
layout: default
---

## OpenCode 핵심 제어 명령어

- **설명**: OpenCode CLI 세션 내에서 에이전트를 조작하고 설정을 변경하는 핵심 명령체계입니다.
- **슬래시 명령어**:
  * `/models`: 에이전트에 적용할 로컬 및 글로벌 LLM 추론 모델 선택 화면 호출
  * `/connect`: Nvidia NIM 등 외부 고성능 AI 플랫폼의 API 키 연동 인터페이스 진입
  * `/quit` 또는 `/exit`: 에이전틱 인터랙션 세션을 정상 종료하고 로컬 터미널로 복귀

---
layout: default
---

## Nvidia NIM 추론 마이크로서비스

> **엔비디아 님 (Nvidia NIM)**
>
> 최적화된 AI 모델들을 클라우드 및 에지 환경에서 즉각 추론할 수 있도록 패키징한 컨테이너화된 마이크로서비스

- **추론 최적화**: NVIDIA 인프라를 바탕으로 극대화된 연산 속도와 낮은 지연 시간 보장
- **무료 API 혜택**: 개발자 계정 가입 시 분당 40회(RPM 40) 외 일일 사용량에 실질적 제한 없음
- **높은 활용성**: 코딩 에이전트의 정밀한 모델 지원 외에도 타 에이전트 프레임워크 연계 가능

---
layout: default
---

## Developer 포털 가입 및 API Key 발급

- **설명**: 고성능 NIM 모델 사용을 위해 Nvidia API Key를 발급받는 보안 연동 절차입니다.
- **진행 단계**:
  1. [Nvidia Developer 로그인](https://developer.nvidia.com/login) 페이지 접속 및 계정 가입
  2. 이메일 인증 절차를 통과한 후 [Nvidia build](https://build.nvidia.com/explore/discover) 접속
  3. 모바일 문자 인증을 거쳐 고유한 NVIDIA Cloud Account 생성 작업 마무리
  4. 대시보드에서 `Generate Key` 버튼을 클릭한 뒤 생성된 `nvapi-...` 고유 API Key 복사

---
layout: default
---

## Nvidia NIM API Key 연동 및 모델 선택

```sh
# 1. 에이전트 터미널 진입
opencode

# 2. 연동 명령어 실행 후 Nvidia 선택 및 발급된 Key 입력
/connect

# 3. 고성능 Nemotron 3 Super 모델을 선택하여 교체 완료
```

---
layout: default
---

## 최적의 LLM 탐색과 실시간 모델 변경

- **설명**: 작업의 난이도와 에이전트 응답성에 맞춰 실시간으로 최적의 인텔리전스를 매칭합니다.
- **고려 사항**:
  * **Artificial Analysis 정보**: 성능 분석 벤치마크 사이트를 참조하여 객관적 품질 검증
  * **체감 성능과 레이턴시**: 단순 벤치마크 점수 외에 실제 에이전트 구동 지연 시간 조율
  * **유동적인 모델 변경**: `/model` 명령어를 통해 개발 도중 언제든지 다른 고성능 모델로 스위칭
