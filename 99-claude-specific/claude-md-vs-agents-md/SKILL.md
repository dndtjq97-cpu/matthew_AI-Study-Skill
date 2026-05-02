---
name: appendix-claude-md-vs-agents-md
description: Claude 전용 부록 — AGENTS.md(공통)와 CLAUDE.md(Claude Code 전용)의 차이를 5분 안에 이해하고, 둘 중 어느 것을 만들지 또는 심볼릭 링크로 둘 다 지원할지 결정한다. 사용자가 "CLAUDE.md vs AGENTS.md", "둘 다 만들어야 해", "심볼릭 링크", "Claude Code에서 AGENTS.md 안 읽어요", "claude.md 차이" 같은 표현을 쓰거나, 캡스톤 종료 후 부록을 둘러볼 때 사용. 본 강의(15강)가 아닌 *짧은 부록 안내*라는 점이 핵심.
---

# 부록 — AGENTS.md vs CLAUDE.md

> 5분 안에 차이·관계 + 심볼릭 링크 패턴을 익힙니다.

## 0. 시작하기 전에
공통 프로토콜(`_shared/teaching-protocol.md` 등)을 따르되, 부록이라 *간소*하게 진행합니다.

## 1. 진입 시 행동
1. 학습자 프로필 확인.
2. `progress["appendix-claude-md-vs-agents-md"].status` 분기.
3. 첫 인사: "Claude Code를 쓰시면 도움이 될 짧은 부록이에요. 5분이면 끝나요."
4. lesson 1~2개 진행. 헤더 `📘 [부록 · 청크 X/Y]`.

## 2. lesson 흐름
- `lesson/01-difference.md` — AGENTS.md와 CLAUDE.md의 핵심 차이
- `lesson/02-symlink-pattern.md` — 둘 다 지원하는 심볼릭 링크 패턴

## 3. 가이드 실습 (선택)
부록은 *간소*해서 별도 가이드 실습은 두지 않음. 학습자가 *심볼릭 링크 한 줄*만 적용하면 충분.

## 4. 종료 시 행동
1. 진도 갱신 (`status = "completed"`)
2. "다른 부록 더 보시겠어요?" 안내

## 5. 강의 작성자 메타
- **트랙**: 부록 (Claude 전용)
- **선행**: 1강 (AGENTS.md), 캡스톤(권장)
- **분량**: ~5분
- **외부 자료**: Claude Code (선택)

## 6. 빠른 자기 점검
- [ ] `📘 [부록 · 청크 X/Y]` 헤더
- [ ] 한 청크만, 끝에 ❓/🛠/🔀
- [ ] 도구명 노출 X (본문에서 — 부록 자체는 Claude 전용이라 *안내성 언급*은 OK)
- [ ] 진도 갱신
