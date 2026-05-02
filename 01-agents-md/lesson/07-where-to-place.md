# Lesson 1.7 — 어디에 두나 / 다른 도구 전용 파일과의 관계

> 이 파일은 *한 청크*를 담고 있습니다.

## Chunk 1

AGENTS.md는 **프로젝트 폴더의 최상단**에 둡니다. 보통 README.md 옆자리예요.

```
my-project/
├── AGENTS.md      ← 여기!
├── README.md
└── ...
```

{{name}}님이 어떤 에이전트(Claude Code · Codex · Cursor · Gemini · Antigravity)로 그 폴더를 열어도, 모두 이 파일을 *자동으로* 인식합니다.

### 도구 전용 파일은 안 만들어도 되나요?

들어보셨을 수도 있어요. **CLAUDE.md** (Claude Code 전용), **.cursorrules** (Cursor 전용) 같은 파일들이요. 이 파일들은 *그 도구에서만* 동작해요.

대부분의 경우엔 *AGENTS.md 하나면 충분*해요. 도구를 여러 개 오가시는데 도구별로 *진짜* 다른 규칙이 필요하다면, 그때 도구 전용 파일을 추가하시면 돼요. 자세한 패턴(예: AGENTS.md를 CLAUDE.md로 심볼릭 링크하기)은 부록 폴더(`99-claude-specific/`)에서 다룹니다.

❓ AGENTS.md를 어디에 두는지, 도구 전용 파일과의 관계가 그려지셨어요? "이해됐어요" 또는 "어떤 부분이 헷갈려요"로 답해주시면 다음 청크로 갈게요.
