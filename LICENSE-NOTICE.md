# 📜 LICENSE NOTICE

이 문서는 *AI 에이전트 강의 패키지*의 배포·사용 조건과, 패키지 안에 동봉된 외부 자료의 라이선스 고지를 담고 있습니다.

---

## 1. 본 패키지 (강의 자료)

### 저작권
© 2026 매튜 (Matthew). 모든 권리 유보 (All Rights Reserved).

### 배포 정책
- **현재 비공개입니다.** 외부 공개·재배포·상업적 사용은 허락 없이 금지됩니다.
- 강의에 직접 참여한 학습자에게만 개인 학습 목적으로 제공됩니다.
- 공개 정책이 향후 바뀔 수 있으며, 그때는 별도 공지가 있을 예정입니다.

### 학습자 산출물
- 학습자가 강의를 따라 만든 결과물(AGENTS.md, SKILL.md, 코드 등)은 *학습자 본인의 소유*입니다.
- 본인 프로젝트·블로그·회사 업무에 자유롭게 사용·배포할 수 있습니다.
- 다만 *강의 자료 자체*(이 패키지의 lesson 텍스트, 가이드 문서 등)는 본인 산출물에 그대로 복사해 재배포할 수 없습니다.

### 학습자 프로필 데이터
- `_shared/learner-profile.json`은 *학습자 본인 컴퓨터*에만 저장됩니다.
- 외부로 전송되지 않습니다.
- 패키지를 깃 저장소로 관리한다면 `.gitignore`에 추가해 주세요.

---

## 2. 동봉된 외부 자료

### 2-1. Anthropic skill-creator (동봉됨)

이 패키지는 학습자가 02-skills 강의에서 *직접 SKILL.md를 만드는 실습*을 할 수 있도록, Anthropic의 `skill-creator` 스킬을 *변경 없이 그대로* `_vendor/anthropic-skill-creator/`에 동봉했습니다.

**라이선스: Apache License 2.0**

- 라이선스 전문: `_vendor/anthropic-skill-creator/LICENSE.txt` (201줄)
- NOTICE: `_vendor/anthropic-skill-creator/NOTICE.md` (출처·동봉 이유·변경 사항)

**출처**: Anthropic의 Claude skills 번들 (`anthropics/skills` 또는 Claude Code 자체 번들의 일부)

**변경 사항**: 없음. 원본을 그대로 복사했습니다.

**고지 의무 이행**:
- ✅ `LICENSE.txt` 동봉
- ✅ `NOTICE.md` 동봉 (출처·라이선스·변경 사항·동봉 일자 명시)
- 재배포 시: 위 두 파일 보존 의무

**다른 에이전트 호환성**: skill-creator는 표준 SKILL.md 형식이라 Claude Code · Codex CLI · Cursor · Gemini CLI · Antigravity 어디서든 호출 가능합니다. 다만 일부 자동화 기능(eval/benchmark)은 Claude 환경에 최적화되어 있어, 02-skills 강의에서는 *vibe 모드*(평가 생략)만 안내합니다.

### 2-2. Superpowers writing-skills (검토 후 채택 안 함)

처음에는 [Superpowers writing-skills (MIT)](https://github.com/obra/superpowers)을 동봉 후보로 검토했으나, 다음 이유로 채택하지 않았습니다:

- 다른 superpowers 스킬(예: `test-driven-development`)에 대한 강한 의존성
- TDD 기반의 엄격한 톤이 비개발자 학습자에게 부담
- skill-creator의 "vibe with me" 모드가 강의 의도에 더 부합

이 결정은 향후 변경될 수 있습니다.

### 2-3. 강의 본문에서 참조되는 외부 자료

각 강의 lesson에서 외부 도구·문서·이미지를 *참조*할 수 있습니다 (Anthropic Claude 문서, MCP 공식 spec, Antigravity docs 등). 이 경우 본문에 출처 링크를 명시하며, 해당 자료의 저작권은 각 원저작자에게 있습니다.

---

## 3. 면책

- 이 패키지는 *교육 목적*으로 제공됩니다.
- 학습자가 외부 API·서비스를 사용해 발생하는 비용·데이터·결과에 대해 강의 작성자는 책임지지 않습니다.
- 강의 진행 중 비용 발생 가능성이 있는 실습은 *사전 안내*되며, 학습자는 자유롭게 스킵할 수 있습니다.

---

## 4. 변경 이력

- 2026-05-02: 패키지 골격 생성, 비공개 정책 명시.
- 2026-05-02: 동봉 외부 자료를 **Anthropic skill-creator (Apache 2.0)** 로 결정. (Superpowers writing-skills MIT 동봉 계획은 채택하지 않음.)

---

## 5. 문의

이 라이선스나 사용 권한 관련 문의는 강의 작성자에게 직접 연락해 주세요.
