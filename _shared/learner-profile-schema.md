# Learner Profile Schema — 학습자 프로필 명세

이 문서는 학습자 프로필 파일(`_shared/learner-profile.json`)의 *구조*와 *갱신 규칙*을 정의합니다.

> ⚠️ 강의 패키지의 콘텐츠는 매튜의 저작권으로 보호됩니다 (All Rights Reserved). 학습자 프로필 파일(`learner-profile.json`)은 학습자 본인의 데이터이며 외부에 업로드되지 않습니다.

---

## 1. 파일 위치

- 경로: `_shared/learner-profile.json` (강의 패키지 폴더 내부)
- 첫 진입 시 빈 템플릿 `learner-profile.template.json`을 복사·채워서 생성

---

## 2. 스키마

```json
{
  "name": "string",
  "os": "darwin | win32 | linux",
  "shell": "zsh | bash | pwsh | cmd | fish",
  "level": "non-developer | developer | mixed",
  "domain": "string (자유 입력, 예: '1인 콘텐츠 크리에이터')",
  "track": "basic | advanced | capstone | none",
  "progress": {
    "<skill-id>": {
      "status": "not_started | in_progress | completed | skipped",
      "current_chunk": 0,
      "total_chunks": 0,
      "practice_status": "not_started | in_progress | done | not_done",
      "completed_at": "YYYY-MM-DD | null",
      "last_visited_at": "YYYY-MM-DD",
      "draft": { /* 자유 형식. 각 강의가 자체 키를 SKILL.md에 정의해 사용 */ }
    }
  },
  "track_decisions": {
    "advanced_decision": "pending | yes | no"
  },
  "created_at": "YYYY-MM-DD",
  "updated_at": "YYYY-MM-DD"
}
```

### `<skill-id>` 명명
폴더명을 그대로 사용합니다. 예: `01-agents-md`, `08-subagents`, `15-build-your-own-harness`.

### 필드별 의미

| 필드 | 설명 |
|---|---|
| `name` | 학습자가 입력한 이름·닉네임 (인사말 개인화) |
| `os` | 운영체제. 첫 진입 시 자동 감지 (Bash `uname` 또는 Node `process.platform`) |
| `shell` | 셸. 자동 감지(`echo $SHELL` 등) 또는 학습자 입력 |
| `level` | 학습자 자가 응답 |
| `domain` | 학습자가 자유롭게 입력한 도메인. lesson 동적 예시 생성 시 참조 |
| `track` | 현재 트랙. 첫 진입 시 `none`, 기초 시작 시 `basic`, 캡스톤 진입 시 `capstone` |
| `progress` | 스킬별 진도 상태 (Object) |
| `progress[skill_id].draft` | 학습자가 미션·실습 중 적은 산출물 임시 저장. 자유 형식 객체. 각 강의가 SKILL.md에 사용 키를 명세 |
| `track_decisions.advanced_decision` | 기초 종료 후 심화 진입 여부 결정 상태 |
| `created_at` / `updated_at` | ISO-8601 짧은 형식 |

---

## 3. 첫 진입 시 자동 감지 흐름

학습자가 패키지를 처음 열 때, 루트 README의 진입 스킬이 다음을 수행합니다:

1. `_shared/learner-profile.json`이 존재하는지 확인
2. 존재하지 않으면:
   - **자동 감지** (한 번만):
     - `os`: 셸 명령으로 감지 — Mac=`darwin`, Windows=`win32`
     - `shell`: `echo $SHELL` 또는 `$env:PSVersionTable` 등
   - **학습자에게 입력 요청** (3가지만):
     - 이름
     - 도메인 (자유 입력)
     - 기술 수준 (1=비개발자 / 2=개발자 / 3=어중간)
3. 위 값으로 프로필을 생성하고 저장

> 두 번째 진입부터는 프로필이 이미 있으므로 메뉴로 바로 진입.

---

## 4. 갱신 규칙

다음 이벤트에서 `progress` 또는 관련 필드를 갱신합니다:

| 이벤트 | 갱신 대상 |
|---|---|
| 스킬 첫 진입 | `progress[skill_id].status = "in_progress"`, `current_chunk = 1`, `last_visited_at` |
| 청크 통과 | `current_chunk += 1` |
| lesson 마지막 청크 통과 | `status = "completed"`, `completed_at` |
| 실습 미션 시작 | `practice_status = "in_progress"` |
| 실습 미션 합격 | `practice_status = "done"` |
| "넘어가" — 청크 | `current_chunk += 1` (status 그대로) |
| "넘어가" — lesson | `status = "skipped"` |
| "넘어가" — 실습 | `practice_status = "not_done"` |
| 기초 트랙 마지막 스킬 완료 | `track_decisions.advanced_decision = "pending"` 후 학습자에게 분기 묻기 |
| 학습자가 "심화 시작" | `track = "advanced"`, `advanced_decision = "yes"` |
| 학습자가 "기초 종료" | `advanced_decision = "no"` |
| 학습자가 미션 답변 제출 | 강의가 정의한 `progress[skill_id].draft.<key>`에 저장 |
| 학습자가 답변 수정 | 같은 키 덮어쓰기 |
| 가이드 실습 진입 시 | `draft` 전체를 학습자에게 정리해 보여줌 (실제 결과물 작성에 활용) |
| 학습자가 강의 "리셋" | 해당 강의의 `progress[skill_id].draft = {}` 비우기 |

매 갱신 시 `updated_at`도 같이 오늘 날짜로 변경.

### `draft` 필드 설계 — 강의별 키 명세

`draft`는 자유 형식 객체이며, 각 강의가 *자신이 사용할 키 이름*을 SKILL.md에 명세합니다. 예 (`01-agents-md`):

```json
"draft": {
  "overview": "한 단락의 프로젝트 개요 (청크 4 답변)",
  "rules": ["규칙1", "규칙2", "규칙3"],
  "commands": "자주 쓰는 명령 (청크 6 답변 일부)",
  "cautions": "주의사항 (청크 6 답변 일부)"
}
```

저장된 데이터는 가이드 실습 진입 시 학습자에게 정리되어 보여지고, 실제 결과물(예: AGENTS.md) 작성에 그대로 활용됩니다. 학습자가 다시 적을 필요가 없습니다.

---

## 5. 갱신 방법 (구현 가이드라인)

각 SKILL.md는 *프로필 갱신을 직접 명령*하지 않고, 다음 표준 형태의 지시문을 본문에 포함합니다:

> "청크 통과 시: `_shared/learner-profile.json`을 읽어 `progress["<skill-id>"].current_chunk`을 +1, `updated_at`을 오늘 날짜로 갱신해주세요."

에이전트는 이 지시문을 읽고 파일 입출력을 수행합니다. (Claude Code/Codex/Cursor/Gemini/Antigravity 모두 파일 읽기/쓰기 가능)

---

## 6. 충돌·복구

- 파일 손상 시: 학습자에게 "프로필이 손상되어 새로 만들어야 합니다" 알림 → 백업(`learner-profile.backup.json`) 시도 → 새로 생성
- 동시성: 강의 중 한 에이전트만 동시에 실행되는 것을 가정. 동시 갱신은 고려하지 않음.

---

## 7. 프라이버시

- 이 파일은 학습자 본인 컴퓨터에만 저장됨
- 외부 전송 X
- 패키지 깃 저장소가 만들어진다면 `learner-profile.json`은 `.gitignore`에 추가
