# 부록 — AGENTS.md와 CLAUDE.md의 차이

> 이 파일은 *한 청크*를 담고 있습니다.

## Chunk 1

두 파일의 핵심 차이는 *누가 읽는가*예요.

| 파일 | 누가 읽나 | 어디에 둬야 하나 |
|---|---|---|
| **AGENTS.md** | Claude Code · Codex · Cursor · Gemini · Antigravity *모두* | 프로젝트 폴더 최상단 |
| **CLAUDE.md** | **Claude Code 전용** | 같은 위치 (또는 `~/.claude/CLAUDE.md` 글로벌) |

AGENTS.md는 *표준 파일*이라 모든 도구가 인식해요. CLAUDE.md는 *Claude Code만* 우선 인식합니다.

대부분의 경우 **AGENTS.md 한 장이면 충분**해요. 다만 *Claude Code에서만 다르게 동작하길* 원할 때 CLAUDE.md를 추가합니다.

❓ 본인이 *여러 도구*를 함께 쓰시는 환경인가요? 한 도구만 쓰시면 어떤 거예요?
