# 부록 — 첫 routine 등록

> 이 파일은 *한 청크*를 담고 있습니다.

## Chunk 1

가장 단순한 첫 routine: **매일 오전 9시 NOTES.md 한 줄 정리**.

설정 흐름 (Claude Code):
1. `/routines` 명령으로 routine 메뉴 진입 (또는 settings.json에서 routines 항목)
2. 새 routine 추가:
   - 이름: `daily-notes-tidy`
   - 시간: `매일 09:00`
   - 작업 지시: "NOTES.md를 읽고 어제 항목을 한 줄 요약으로 압축해줘"
3. 활성화

> 정확한 명령은 Claude Code 버전에 따라 다를 수 있어요. `claude --help` 또는 공식 문서 확인.

🛠 **미션** — 본인 환경에 *어떤 routine 1개*가 도움 될까요? 한 줄로 적어주세요.

> 💾 답변은 자동 보관됩니다. (`draft.chosen_routine`)
