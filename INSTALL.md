# 🛠 INSTALL — 에이전트별 설치/연동 가이드

이 패키지를 학습자 본인의 에이전트에서 인식시키는 방법입니다.

> ⚠ 도구별 정확한 명령은 *현재 시점*에서 확인된 *권장 패턴*입니다.
> 도구 업데이트로 명령이 바뀔 수 있으니, 의심되면 각 도구 공식 문서를 먼저 확인해 주세요.

---

## 공통 — 어떤 에이전트든 적용되는 흐름

세 가지 방식 중 학습자 환경에 맞는 것을 고르세요.

### 방식 A — 패키지 폴더에서 에이전트 실행 (가장 간단, 추천)
패키지 폴더로 이동한 뒤, 그 안에서 에이전트를 띄우면 폴더 내 SKILL.md들을 자동 인식합니다.

### 방식 B — 글로벌 스킬 폴더에 복사·링크
도구별 글로벌 스킬 디렉토리(`~/.claude/skills/` 등)에 패키지 폴더를 *심볼릭 링크*하거나 복사하면, 어떤 작업 폴더에서 에이전트를 켜도 강의가 잡힙니다.

### 방식 C — 워크스페이스 스킬 폴더 사용 (Antigravity 등)
프로젝트 안에 `.agents/skills/` 같은 폴더를 두고 거기에 패키지를 넣는 방식.

---

## 1. Claude Code

### 방식 A — 패키지 폴더에서 실행 (추천)

**Mac**
```bash
# 패키지 폴더로 이동
cd ~/Desktop/matthew_AI-Study-Skill

# Claude Code 실행
claude
```

**Windows (PowerShell)**
```powershell
# 패키지 폴더로 이동
cd $HOME\Desktop\matthew_AI-Study-Skill

# Claude Code 실행
claude
```

폴더 안의 `README.md`와 각 SKILL.md를 Claude Code가 자동 참조합니다.

### 방식 B — 글로벌 스킬 폴더 (선택)

**Mac**
```bash
# 글로벌 스킬 폴더로 심볼릭 링크
mkdir -p ~/.claude/skills
ln -s ~/Desktop/matthew_AI-Study-Skill ~/.claude/skills/matthew-lecture
```

이후 어떤 폴더에서 `claude` 실행해도 강의가 인식됩니다.

> 자세한 사용법은 [Claude Code 공식 문서](https://docs.claude.com/en/docs/claude-code) 참조.

---

## 2. OpenAI Codex CLI / App

### 방식 A — 패키지 폴더에서 실행

**Mac**
```bash
# 패키지 폴더로 이동
cd ~/Desktop/matthew_AI-Study-Skill

# Codex CLI 실행
codex
```

**Windows**
```powershell
cd $HOME\Desktop\matthew_AI-Study-Skill
codex
```

> 학습자가 시작 신호만 주면 됩니다: "이 폴더의 README.md를 읽고 강의를 시작해줘."
> 자세한 사용법은 [Codex CLI 공식 문서](https://github.com/openai/codex) 참조.

---

## 3. Cursor

### 방식 A — 패키지 폴더를 Cursor에서 열기

1. Cursor 실행 → `File > Open Folder` → 패키지 폴더 선택
2. Cursor 채팅 창에 다음 입력:

```
이 워크스페이스의 README.md를 읽고 강의를 시작해줘.
```

### 방식 B — 플러그인 마켓플레이스 (선택, Superpowers 사용 시)
이 패키지는 자체로 동작하지만, 학습자가 더 풍부한 스킬 생태계를 원하면 Superpowers 플러그인 설치도 가능합니다:

```
/add-plugin superpowers
```

> 자세한 사용법은 [Cursor 공식 문서](https://cursor.com/docs) 참조.

---

## 4. Gemini CLI

### 방식 A — 패키지 폴더에서 실행

**Mac**
```bash
# 패키지 폴더로 이동
cd ~/Desktop/matthew_AI-Study-Skill

# Gemini CLI 실행
gemini
```

**Windows**
```powershell
cd $HOME\Desktop\matthew_AI-Study-Skill
gemini
```

### Superpowers 확장 설치 (선택)
강의 02-skills 실습에서 Superpowers `writing-skills`를 사용합니다. 패키지 안의 `_vendor/`에 동봉본이 들어가지만, 글로벌로 쓰고 싶으면:

```bash
gemini extensions install https://github.com/obra/superpowers
```

> 자세한 사용법은 [Gemini CLI 공식 문서](https://github.com/google-gemini/gemini-cli) 참조.

---

## 5. Antigravity

Antigravity는 SKILL.md 표준을 정식으로 지원합니다. 두 가지 경로가 있어요.

### 방식 A — 워크스페이스 스킬 (프로젝트 전용)

```
<패키지 폴더>/.agents/skills/
```

이 위치에 SKILL.md들이 인식되도록 하려면, 패키지 안에 직접 `.agents/skills/` 폴더를 만들고 각 강의 폴더를 그 안으로 옮기거나 심볼릭 링크해야 할 수 있어요.

> 단, 이 패키지는 학습 자료이므로 *방식 B(글로벌)* 가 더 자연스럽습니다.

### 방식 B — 글로벌 스킬 (시스템 전체) — 추천

**Mac**
```bash
# Antigravity 글로벌 스킬 폴더 만들기
mkdir -p ~/.gemini/antigravity/skills

# 패키지를 심볼릭 링크
ln -s ~/Desktop/matthew_AI-Study-Skill ~/.gemini/antigravity/skills/matthew-lecture
```

**Windows**
```powershell
# 폴더 만들기
New-Item -ItemType Directory -Force -Path "$HOME\.gemini\antigravity\skills"

# 심볼릭 링크 (관리자 권한 필요할 수 있음)
New-Item -ItemType SymbolicLink `
  -Path "$HOME\.gemini\antigravity\skills\matthew-lecture" `
  -Target "$HOME\Desktop\matthew_AI-Study-Skill"
```

이후 Antigravity를 어떤 프로젝트에서 열어도 강의 SKILL.md가 자동 인식됩니다.

> 자세한 사용법은 [Antigravity 공식 문서](https://antigravity.google/docs/skills) 참조.

---

## 시작 신호 — 모든 도구 공통

설치를 마치고 에이전트를 띄운 뒤, 다음 한 줄을 입력하면 강의가 시작됩니다.

```
이 폴더의 README.md를 읽고 강의를 시작해줘.
```

또는 특정 강의 직접 호출:

```
01-agents-md 강의 시작
```

---

## 트러블슈팅

### "에이전트가 SKILL.md를 인식 못해요"
- 패키지 폴더 안에서 에이전트를 켰는지 확인
- 또는 글로벌 스킬 폴더에 심볼릭 링크가 잘 걸렸는지 확인 (Mac: `ls -la ~/.claude/skills/`)
- Antigravity의 경우 `~/.gemini/antigravity/skills/` 경로 확인

### "심볼릭 링크 생성이 안 돼요" (Windows)
- PowerShell을 *관리자 권한*으로 실행
- 또는 *복사*로 대체: `Copy-Item -Recurse <패키지 경로> <글로벌 경로>`

### "여러 도구를 동시에 쓰고 싶어요"
- 가능합니다. 도구마다 글로벌 스킬 폴더가 달라서 *각각* 심볼릭 링크 걸어두면 됩니다.

---

## 다음 단계

설치가 끝나면 [`README.md`](./README.md)로 돌아가 *첫 사용 방법* 섹션부터 시작하세요.
