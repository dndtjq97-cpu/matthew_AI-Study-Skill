# 🎓 AI 에이전트 강의 패키지

> 비개발자도 본인만의 AI 에이전트 환경(=하네스)을 만들 수 있도록 만든 *대화형 강의 패키지*

이 패키지는 매튜의 강의를 학습자가 자기 페이스로 다시 학습하고 직접 실습할 수 있게 만든 **에이전트 비종속 SKILL.md 모음**입니다.
Claude Code · Codex CLI · Cursor · Gemini CLI · Antigravity 어디에서 열어도 동일한 흐름으로 동작합니다.

---

## 학습 흐름 — 한 줄로

> 0강(용어 안내) → 이론(청크 단위) → 가이드 실습(옵션 선택 + 함께 진행 + 에러 해결) → 진도 자동 저장 → 다음 강의

매 강의는 **한 청크씩** 게임처럼 진행됩니다. 학습자가 답해야 다음으로 넘어가요.
실습은 단순 미션이 아니라, **에이전트가 옆에 앉아 같이 해주는 가이드 모드**입니다.

---

## 트랙 구성

| 트랙 | 강의 수 | 학습자가 끝나면 할 수 있는 것 |
|---|---|---|
| 📖 **0강 — 시작 전 안내** (선택 권장) | 1강 | 비개발자 용어와 미리 가입할 곳을 10분 안에 익힘 |
| 🎓 **기초** (필수) | 7강 | 본인만의 *최소 동작 하네스* 구축 — AGENTS.md, 첫 스킬, MCP 연결, 프롬프트, 컨텍스트, 무료 API, 디버깅 |
| 🚀 **심화** (선택) | 7강 | 자동화·비용·멀티 에이전트까지 운영하는 *완성형 하네스* — 서브에이전트, 훅, 작업 분해, 도구 선택, 비용 관리, 로컬·프라이버시, 멀티에이전트 |
| 🎯 **캡스톤** | 1강 | 지금까지 배운 모든 것을 *본인 환경에 통합* |
| 🔌 **부록** (Claude 전용) | 5강 (각 5~15분) | Claude Code/Desktop/VS Code 확장 등 도구 특화 보강 |

기초 → 심화는 학습자가 직접 결정합니다. 기초만 듣고 나중에 돌아와도 진도가 그대로 남아 있어요.

---

## 첫 사용 방법

### 1) 패키지 폴더 받기
이 폴더 전체를 본인 컴퓨터 어디에든 두세요. (예: `~/Desktop/matthew_AI-Study-Skill`)

### 2) 본인이 쓰는 에이전트 도구로 폴더 열기
구체적인 명령은 [`INSTALL.md`](./INSTALL.md)를 참고하세요. (5개 에이전트 모두 안내)

### 3) 에이전트에게 시작 신호 주기

> 👉 "이 폴더의 README.md를 읽고 강의를 시작해줘."

처음이라면 **0강(prerequisites)부터 권장**됩니다. 익숙하시면 건너뛰셔도 OK.

---

## 첫 진입 시 — 학습자 프로필 생성

처음 시작하면 에이전트가 다음 3가지를 한 번만 묻습니다:

1. 이름·닉네임
2. 어떤 분야에서 에이전트를 활용하고 싶은지 (도메인)
3. 본인의 기술 수준

답변하면 OS·셸은 자동 감지하고 `_shared/learner-profile.json`을 생성합니다. 이후 0강 권장 안내가 떠요.

> 이 파일은 학습자 본인 컴퓨터에만 저장되며, 외부로 전송되지 않습니다.

---

## 메뉴 예시

```
👋 다시 오셨네요, 매튜님!

📖 [강의 시작 전]
  [0강] prerequisites          ✅ 수강완료

🎓 [기초 트랙]
  [1강] agents-md             ✅ 수강완료
  [2강] skills                ✅ 수강완료
  [3강] mcp                   ⏳ 진행중 (청크 4/8)        ← 이어서 듣기 추천
  [4강] prompt-engineering    🔒 미수강
  ...
```

자세한 동작은 [`_shared/menu-template.md`](./_shared/menu-template.md) 참조.

---

## 진도 표시 아이콘

| 아이콘 | 의미 |
|---|---|
| ✅ | 수강완료 (이론 + 실습 통과) |
| ⚠ | 수강완료지만 *실습 미이행* |
| ⏳ | 진행중 (현재 청크 표시) |
| ⏭ | 스킵됨 (수강완료 아님) |
| 🔒 | 미수강 |

---

## 패키지 구조

```
matthew_AI-Study-Skill/
├── README.md                       ← (이 문서)
├── INSTALL.md                      ← 에이전트별 설치/연동 방법
├── LICENSE-NOTICE.md               ← 비공개 + 동봉 라이선스 고지
├── LESSONS_PLAN.md                 ← 13개 강의 결정 이력
├── LESSONS_PLAN_APPENDIX.md        ← 부록 5개 결정 이력
│
├── _shared/                        ← 모든 강의가 따르는 공통 규칙
│   ├── teaching-protocol.md
│   ├── guided-practice-protocol.md
│   ├── learner-profile-schema.md
│   ├── learner-profile.template.json
│   ├── style-guide.md
│   └── menu-template.md
│
├── _vendor/                        ← 외부 동봉 (Apache 2.0 고지 동반)
│   └── anthropic-skill-creator/    ← 02-skills 실습용 (skill-creator + LICENSE + NOTICE)
│
├── 00-prerequisites/               ← 📖 강의 시작 전 안내 (10분, 선택 권장)
│   ├── lesson/01-terms.md          ← 비개발자 용어 사전
│   ├── lesson/02-signups.md        ← 미리 가입할 곳
│   └── resources/glossary.md       ← 용어 사전 (전체 강의 참조)
│
├── 01-agents-md/ ~ 07-debugging/   ← 🎓 기초 트랙 7개
├── 08-subagents/ ~ 14-multi-agent-design/  ← 🚀 심화 트랙 7개
├── 15-build-your-own-harness/      ← 🎯 캡스톤
│
└── 99-claude-specific/             ← 🔌 Claude 전용 부록
    ├── README.md
    ├── claude-md-vs-agents-md/     ← AGENTS.md vs CLAUDE.md (~5분)
    ├── claude-routines/            ← 정기 자동 작업 (~10분)
    ├── claude-remote-control/      ← 원격 제어 (~10분)
    ├── claude-desktop-multisession/ ← 다중 세션 (~5분)
    └── claude-vscode-extension/    ← VS Code 확장 (~10~15분)
```

각 강의 폴더 내부 구조:
```
NN-skill-name/
├── SKILL.md
├── lesson/         ← 이론 (청크 파일들)
├── practice/       ← 가이드 실습
│   ├── guided.md
│   └── options/    ← 학습자 선택지별 (옵션 ≥3개일 때)
└── resources/      ← 템플릿·체크리스트 등
```

---

## 에이전트가 따라야 할 진입 프로토콜

> ⚙ **에이전트용 지시 — 학습자가 이 README를 보여주거나 "강의 시작"을 입력하면 다음을 수행하세요.**
>
> 1. `_shared/learner-profile.json` 존재 확인.
> 2. 없으면 → `_shared/learner-profile-schema.md`의 첫 진입 흐름. 프로필 생성 후 **0강 권장**.
> 3. 있으면 → `_shared/menu-template.md`의 두 번째 이후 메뉴 출력.
> 4. 학습자가 강의 번호·이름 입력 → 해당 폴더의 `SKILL.md` 호출.
> 5. 모든 응답은 `_shared/style-guide.md`의 톤(친근한 존댓말).
> 6. 이론은 `_shared/teaching-protocol.md`(청크 단위), 실습은 `_shared/guided-practice-protocol.md`(7단계).
> 7. 학습자가 모르는 단어 만나면 `00-prerequisites/resources/glossary.md`로 안내.

---

## 비용 안내

이 강의 패키지 자체는 비용이 없습니다. 다만 일부 실습은 외부 API(유료 가능)를 사용해요.

- 비용 발생 가능성 있는 실습은 시작 전에 *반드시* 안내됩니다.
- 부담되면 **자유롭게 스킵 가능**합니다 (⚠ 실습 미이행으로 표시되지만 다음 강의는 진행).
- 13강에서 *비용 없는 로컬 LLM 옵션*도 다룹니다.

---

## 라이선스 / 외부 공유

이 패키지는 **비공개**입니다. 자세한 내용은 [`LICENSE-NOTICE.md`](./LICENSE-NOTICE.md) 참조.

동봉된 외부 자료: Anthropic skill-creator (Apache 2.0)

학습자 본인이 만든 결과물(AGENTS.md, 스킬 등)은 학습자 소유입니다.

---

## 도움이 필요하시면

- 강의 중 모르는 단어: `00-prerequisites/resources/glossary.md`
- 강의 중 막히는 부분: 에이전트에게 "잠깐, 이 부분 더 설명해주세요"
- 패키지 자체의 버그·개선 요청: 강의 작성자에게 직접 전달
