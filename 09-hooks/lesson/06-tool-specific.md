# Lesson 9.6 — 도구별 hook 설정 위치

> 이 파일은 *한 청크*를 담고 있습니다.

## Chunk 1

hook 설정 위치는 *도구마다 달라요*.

> 💡 **도구별 위치 (참고)**
>
> - Claude Code: `~/.claude/hooks/` 또는 settings의 hooks 섹션
> - Codex CLI: 도구 설정 파일 안 hook 항목
> - Cursor: `.cursor/hooks/` 또는 워크스페이스 설정
> - Gemini CLI: 확장(extension)에 정의
> - Antigravity: 워크스페이스 hooks 폴더
>
> 정확한 위치는 도구별 공식 문서 확인. 본인 도구에 hook 기능이 *없으면* 가이드 실습에서 *대체 방법*(예: git hook, 시스템 cron 등)을 안내드릴게요.

도구별 차이는 있어도 *트리거 + 액션* 모델은 같아요. 한 곳에서 익히면 다른 도구로 옮기기 쉽습니다.

❓ 본인 도구에 hook 기능이 있는지 짐작 가세요?
