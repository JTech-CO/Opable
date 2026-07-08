# Opable

> **Claude Opus 4.8의 답변을 Fable 5에 최대한 가깝게 — 모델을 바꾸는 게 아니라 Fable의 작업 방식을 이식하는 응답 발현 하네스.**

[English](README.md) · [한국어](README-KR.md)

## 1. 소개 (Introduction)

Opable(구 *Opus 4.8 Plus*)은 Claude Opus 4.8용 지침 하네스입니다. 답 뒤의 추론만 강화하며, 출력 스타일은 네이티브 그대로 — 관측 가능한 차이는 품질뿐입니다. 모델의 능력 천장을 올리는 것이 아니라, 그 천장 중 실제로 끌려 나오는 양(발현)을 극대화합니다.

**주요 기능**
- **계층 1 — 추론 루프**: 응답마다 내부 6단계(프레이밍→분해→심층 추론→초안→그라운딩→점검), 전부 출력 비노출 (`phases/`, `EFFORT.md`).
- **계층 2 — 응답 규율**: 유출된 Fable 5의 답변 방식을 명문화한 Operating Manual 정본 + 불변식 10종 + 발신 전 6항목 점검 (`OPERATING_MANUAL.md`, `INVARIANTS.md`, `gates/`).
- **계층 3 — 상황별 스킬**: 과제 유형이 맞을 때만 발동하는 fable-skills 35종(유형별 시니어 작업 습관) (`skills/`, 색인은 `SKILLS.md`).
- **네이티브 출력**: 단계 라벨·체크리스트·강제 템플릿 없음 — 사용자는 더 좋은 답을 볼 뿐, 다른 포맷을 보지 않습니다.

## 2. 기술 스택 (Tech Stack)

- **대상 모델**: Claude Opus 4.8
- **형식**: 순수 Markdown 지침 팩 — `KR/`·`EN/`(각 23파일, 동일 내용) + 공유 `skills/`
- **배포면**: claude.ai Project / Claude Code / API 시스템 프롬프트
- **소스**: 기존 하네스 골격 + Operating Manual + [fable-skills](https://github.com/adamentwistle/fable-skills) (MIT)

## 3. 설치 및 실행 (Quick Start)

**요구 사항**: Claude Opus 4.8 사용 환경 (claude.ai, Claude Code 또는 API)

1. **설치 (Install)**
   ```bash
   git clone https://github.com/JTech-CO/Opus-4.8-Plus.git
   cd Opus-4.8-Plus
   ```

2. **도입 (Adopt)** — 배포면을 선택합니다
   - **claude.ai Project**: `KR/CLAUDE.md`(또는 `EN/CLAUDE.md`)를 Project 지침에 붙이고, 나머지 팩 파일을 Project 지식에 업로드합니다.
   - **Claude Code**: 한 팩의 내용물을 레포 루트에 복사해 `CLAUDE.md`가 루트에 오게 합니다. (선택) `skills/`를 `.claude/skills/`로 복사하면 Skill 도구로도 발동합니다.
   - **API**: `CLAUDE.md`(필요하면 `OPERATING_MANUAL.md`까지)를 system 프롬프트에 넣습니다.

3. **조정 (Tune)**
   프로젝트 고유 불변식을 `INVARIANTS.md`에 추가하고, 기본 추론 깊이를 `EFFORT.md`에서 확인합니다.

## 4. 폴더 구조 (Structure)

```text
Opus-4.8-Plus/
├── KR/                      # 국문 팩 (23파일)
│   ├── CLAUDE.md            # 자동 로드 계약 (세 계층을 묶음)
│   ├── OPERATING_MANUAL.md  # 응답 규율 정본 (계층 2)
│   ├── HARNESS.md / INVARIANTS.md / SKILLS.md / EFFORT.md / RUNBOOK.md …
│   ├── phases/              # 내부 추론 6단계 (계층 1)
│   ├── gates/               # 발신 전 점검 기준
│   └── decisions/           # 설계 결정 기록 (ADR)
├── EN/                      # 영문 팩 (동일 구성)
├── skills/                  # fable-skills 35종 벤더링 (계층 3, MIT)
└── Operating Manual.md      # 병합 전 원문 보존본
```

심화 배경(천장 vs 발현, 설계 결정)은 각 팩의 `README.md`와 `decisions/`에 있습니다.

## 5. 정보 (Info)

- **License**: MIT
- **Attribution**: [fable-skills](https://github.com/adamentwistle/fable-skills) (MIT, 원문 무수정 벤더링). Operating Manual은 유출된 Fable 5의 답변 방식을 명문화한 문서 기반.
- **Contact**: [JTech-CO](https://github.com/JTech-CO) — 이슈·PR 환영
