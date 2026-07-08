# SKILLS.md — 상황별 스킬 색인

> 계층 3: 과제 유형이 맞을 때만 발동하는 작업 습관(situational skill) 35종의 색인. 계층 1(추론 루프)·계층 2(응답 규율)가 모든 응답에 적용되는 것과 달리, 스킬은 해당 유형의 과제에서만 켜진다. 본문은 `../skills/`(KR/EN 팩 공유, 영문 원문).

## 출처와 발동
- 출처: fable-skills(adamentwistle/fable-skills, MIT). Fable이 경량 모델을 자기 작업 수준으로 끌어올리기 위해 쓴 엔지니어링 규율 35종. `../skills/`에 원문 무수정으로 벤더링(상세 `../skills/README.md`).
- 발동: S0(프레이밍)·S1(분해)에서 과제 유형을 아래 "언제 발동"과 각 스킬 frontmatter의 description에 대조해, 맞는 것만 내부 로드한다.
- 스킬도 내부 규율이다 — 출력에 스킬 이름·체크리스트·단계 라벨을 드러내지 않는다(INV-7).
- Claude Code에서는 `skills/`를 `.claude/skills/`로 복사하면 Skill 도구로도 발동할 수 있다.

## 적용면
| 기호 | 적용면 |
|---|---|
| ◎ | 대화+코딩 공통 — 파일·터미널 없이 대화만으로도 발동한다 |
| ○ | 코딩 중심 — 코드를 읽고 쓰는 과제에서 발동한다 |
| △ | 에이전트 세션 전용 — 파일·터미널·git 조작이 있는 세션에서만 의미가 있다 |

## 카탈로그 (35종)

하네스 대응 열의 Sn은 `phases/`의 단계, OM §n은 `OPERATING_MANUAL.md`의 절, INV-n은 `INVARIANTS.md`의 불변식. 대응이 없으면 —.

### 오리엔테이션·계획 (Orientation & planning)
| 스킬 | 적용면 | 언제 발동 | 하네스 대응 |
|---|---|---|---|
| codebase-orientation | ○ | 이 세션에서 처음 만지는 리포·모듈에 들어갈 때, 기존 아키텍처를 상대로 설계하기 전 | — |
| task-decomposition | ◎ | 3개 이상의 파일·단계에 걸치는 작업의 시작, 그리고 도중에 접근이 뒤집혔을 때 | S1·OM §2 |
| estimation-and-scoping | ◎ | 작업 크기를 산정할 때, 도중 범위가 폭증할 때, "간단 수정"이 구조 변경으로 드러날 때 | EFFORT·OM §3 |
| ambiguity-commit | ◎ | 요청의 해석이 여럿이거나 미지정 파라미터(어느 파일·환경, 얼마나 철저히, 어떤 형식)가 있을 때 | S0·OM §1 |
| question-vs-task | ◎ | 질문인지 수정 요청인지 갈리는 메시지 — 버그 서술, "왜 X가 되지", 생각 정리형 발화 | S0·OM §1 |

### 정확성·디버깅 (Correctness & debugging)
| 스킬 | 적용면 | 언제 발동 | 하네스 대응 |
|---|---|---|---|
| root-cause-debugging | ○ | 모든 버그·테스트 실패·회귀·간헐 오작동 — 수정을 제안하기 전, 그리고 첫 수정이 실패했을 때 | — |
| edge-case-sweep | ◎ | 정상 경로가 통과한 뒤, 함수·핸들러·파서·변환을 완료라고 선언하기 전 | S5(반증 시도의 코딩 구체화) |
| numerical-care | ◎ | 카운터 이상의 모든 산술 — 돈·퍼센트·평균·기간·집계·계산값 비교 | INV-9·OM §4 |
| concurrency-reasoning | ○ | 비동기 팬아웃, 스트림/SSE, 잡, 캐시, 타이밍 냄새가 나는 간헐 버그 | — |
| environment-first | ○ | 명령이 이유 없이 실패할 때, "실패할 리 없는" 테스트가 실패할 때, 동작이 읽고 있는 코드와 모순될 때 | — |
| stop-thrashing | ◎ | 같은 문제의 세 번째 실패, 같은 줄의 반복 수정, 추론이 아니라 추측으로 하는 시도 | S2(믿음 수정) |

### 보안·안전 (Security & safety)
| 스킬 | 적용면 | 언제 발동 | 하네스 대응 |
|---|---|---|---|
| security-reflexes | ○ | 사용자 입력·인증/인가·시크릿·경로·URL·서브프로세스·SQL·HTML 렌더링·외부 API를 만지는 모든 코드 | — |
| untrusted-content-guard | ◎ | 지시처럼 들리는 문구가 섞일 수 있는 외부·사용자 생성 콘텐츠를 처리할 때(프롬프트 인젝션 방어) | INV-6 |
| data-loss-guard | △ | 재생성이 어려운 상태를 부술 행동 직전 — rm·덮어쓰기·force-push·reset --hard·DROP·대량 삭제·프로세스 종료 | — |
| api-surface-care | ○ | 다른 코드가 의존하는 것을 고치기 전 — 공개 함수·엔드포인트·CLI 플래그·설정 형식·스키마 | — |

### 변경 규율 (Change discipline)
| 스킬 | 적용면 | 언제 발동 | 하네스 대응 |
|---|---|---|---|
| surgical-refactoring | ○ | 3곳 이상에 걸친 개명, 시그니처·타입 개편, 코드 이동, 코드베이스 전반의 패턴 교체 | — |
| dependency-changes | ○ | 패키지 매니페스트를 만지기 전, 보안 권고가 떴을 때, 버전 불일치 오류가 났을 때 | — |
| data-migration-safety | ○ | 스키마 변경, 저장된 JSON 형태 변경, 백필, 영속 필드·API 필드의 개명·삭제 | — |

### 테스트·검증 (Testing & verification)
| 스킬 | 적용면 | 언제 발동 | 하네스 대응 |
|---|---|---|---|
| test-design | ○ | 테스트를 쓸 때, 수정에 회귀 커버리지를 붙일 때, 기존 테스트가 무엇을 지키는지 판정할 때 | S5(반증 시도의 코딩 구체화) |
| verify-ui-visually | △ | 컴포넌트·스타일·레이아웃·템플릿·차트·이메일·생성 문서/이미지를 바꾼 뒤 | — |
| workmanship | ○ | 코드 변경·조사·사용자가 근거로 행동할 최종 보고가 있는 모든 과제 — 코딩 과제의 상시 후보 | INV-3·OM §6·§7 |

### 성능·운영 (Performance & operations)
| 스킬 | 적용면 | 언제 발동 | 하네스 대응 |
|---|---|---|---|
| performance-investigation | ○ | 모든 "빠르게 해줘", 지연·메모리 조사, 감으로 캐시·메모이제이션을 넣기 전 | — |
| perf-sanity | ○ | 크기를 모르는 데이터 위의 루프, 루프 안의 DB 접근, 요청 경로 위의 모든 것 | — |
| incident-diagnosis | △ | 프로덕션이 지금 죽어 있을 때, 재시작·재배포·삭제를 첫수로 두기 전 | — |

### 커뮤니케이션 (Communication)
| 스킬 | 적용면 | 언제 발동 | 하네스 대응 |
|---|---|---|---|
| calibrated-recommendation | ◎ | "뭘 써야 하나", "최선의 방법은", "A냐 B냐", 설계 선택을 제안할 때 | INV-10·OM §5 |
| explain-at-the-right-level | ◎ | 모든 설명형 질문 — "어떻게 작동하나", "왜 이러나", "차이가 뭔가", "짚어 달라" | — |
| error-message-quality | ○ | throw/raise·로그 문장·검증 메시지·CLI/API 오류 응답을 쓸 때 | — |
| escalate-vs-decide | ◎ | 작업 중 불확실할 때, "할까요?"라고 묻고 싶을 때, 파괴적·대외적·범위 변경 행동 전 | — |
| generalize-the-correction | ◎ | 사용자가 오류를 지적하거나, 접근을 거부하거나, 작업 방식의 선호를 밝히는 순간 | RUNBOOK 성장 원칙 |

### 작업 습관·위생 (Working style & hygiene)
| 스킬 | 적용면 | 언제 발동 | 하네스 대응 |
|---|---|---|---|
| git-hygiene | △ | 커밋·브랜치를 만질 때, 되돌릴 지점이 필요할 만큼 큰 변경의 시작 | — |
| leave-no-mess | △ | 서버를 띄웠거나 스크래치 파일·디버그 출력·의도한 diff 밖의 상태 변경을 남긴 과제의 끝 | — |
| context-checkpoint | △ | 30분을 넘기거나 다수 파일에 걸칠 과제의 시작, 그리고 국면이 바뀔 때마다 | — |
| subagent-fanout | △ | 다수 파일·디렉터리를 훑어야 할 때, 독립 조사 여럿을 병렬로 돌릴 수 있을 때, 원시 도구 출력이 작업 컨텍스트를 침수시킬 때 | — |
| cross-platform-care | ○ | 셸 스크립트·CI 단계·경로 조작·파일 I/O, 남이 실행할 설치 안내를 쓸 때 | — |

### LLM 애플리케이션 코드 (LLM application code)
| 스킬 | 적용면 | 언제 발동 | 하네스 대응 |
|---|---|---|---|
| llm-app-code | ○ | 에이전트 루프, 도구 정의, 프롬프트·모델 변경 — LLM API를 호출하는 모든 코드 | INV-6(전이 인젝션) |

## 주의 — 스킬 본문 안의 교차참조
일부 스킬 본문이 참조하는 이름(see …)은 업스트림에서 통합·개명되기 전의 이름이다. 원문은 벤더링 원칙상 수정하지 않는다 — 다음 매핑으로 읽는다.

| 본문에 등장하는 이름 | 실제 스킬 |
|---|---|
| ground-before-edit · honest-report · self-review-diff · verify-before-done · pre-done-review · read-what-came-back | workmanship |
| search-existing-patterns | codebase-orientation |
| scope-discipline | estimation-and-scoping · surgical-refactoring §5 |
| security-reflex | security-reflexes |
| root-cause-debug | root-cause-debugging |
