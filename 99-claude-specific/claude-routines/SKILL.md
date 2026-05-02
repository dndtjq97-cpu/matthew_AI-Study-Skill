---
name: appendix-claude-routines
description: Claude 전용 부록 — Claude Code의 Routines (정기 자동 작업) 기능을 10분 안에 익힌다. cron 스타일로 주기적 작업을 등록하는 첫 routine 1개 시연. 9강(hooks)이 *이벤트 기반*이라면 routines는 *시간 기반*. 사용자가 "Claude routines", "정기 작업", "매일 자동", "주간 자동", "스케줄링" 같은 표현을 쓰거나, 캡스톤 종료 후 부록을 둘러볼 때 사용. 본 강의가 아닌 *짧은 부록 안내*.
---

# 부록 — Claude Routines

> 10분 안에 routines 개념 + 첫 routine 등록까지.

## 0. 시작하기 전에
공통 프로토콜(`_shared/teaching-protocol.md` 등)을 따름.

## 1. 진입 시 행동
1. 학습자 프로필 확인.
2. `progress["appendix-claude-routines"].status` 분기.
3. 첫 인사: "Claude Code의 Routines를 10분 안에 봐드릴게요."
4. lesson 1~3개 진행. 헤더 `📘 [부록 · 청크 X/Y]`.

## 2. lesson 흐름
- `lesson/01-what-is-routine.md` — Routines란? 9강 hooks와의 차이
- `lesson/02-first-routine.md` — 첫 routine 등록 (예: 매일 9시 NOTES 정리)
- `lesson/03-deactivate-debug.md` — 비활성화·디버깅

## 3. draft 키
- `chosen_routine` — 첫 등록할 routine 한 줄

## 4. 종료 시 행동
1. 진도 갱신 (`status = "completed"`)
2. "다른 부록 더 보시겠어요?" 안내

## 5. 강의 작성자 메타
- **트랙**: 부록 (Claude 전용)
- **선행**: 9강 (hooks, 권장)
- **분량**: ~10분
- **외부 자료**: Claude Code (필수)

## 6. 빠른 자기 점검
- [ ] 한 청크만, 끝에 ❓/🛠/🔀
- [ ] 진도 갱신
