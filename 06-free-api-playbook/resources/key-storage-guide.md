# API 키 안전 보관 가이드

## 핵심 원칙
- 키는 *비밀번호* 같음. 외부에 노출되면 *즉시 폐기 + 재발급*.
- *코드에 직접* 박지 않기 (특히 git에 올릴 코드).

## 추천 보관 방식 (학습자 OS 맞춤)

{{os:darwin}}
```bash
# 옵션 A: 셸 환경 변수 (영구)
echo 'export OPENAI_API_KEY="sk-..."' >> ~/.zshrc

# 옵션 B: 프로젝트 .env 파일 (프로젝트 한정)
cd ~/my-project
echo 'OPENAI_API_KEY="sk-..."' > .env
echo '.env' >> .gitignore  # git에 안 올라가도록 반드시
```
{{/os}}

{{os:win32}}
```powershell
# 옵션 A: 영구 환경 변수
[Environment]::SetEnvironmentVariable("OPENAI_API_KEY", "sk-...", "User")

# 옵션 B: 프로젝트 .env (그리고 .gitignore에 추가)
Set-Location $HOME\my-project
'OPENAI_API_KEY="sk-..."' | Out-File -FilePath .env -Encoding UTF8
'.env' | Add-Content -Path .gitignore
```
{{/os}}

## 절대 하지 말 것

- ❌ 키를 코드에 직접 — `api_key = "sk-..."`
- ❌ git에 커밋된 파일에 키 (`config.json`, `notebook.ipynb` 등)
- ❌ 메신저·이메일·디스코드에 평문 공유
- ❌ 스크린샷에 노출 (블로그 포스트 등)

## 노출됐을 때 대처

1. *즉시* 해당 키를 발급 페이지에서 *폐기*(revoke)
2. 새 키 발급
3. 기존 코드·파일에서 노출된 키 제거 + git history 정리 (`git filter-repo` 등)

## 비밀 관리 도구 (선택)

더 엄격한 환경:
- **1Password** — CLI 통합 가능
- **macOS Keychain** — 시스템 내장
- **Hashicorp Vault** — 팀·조직용
- **Doppler** — 멀티 환경 동기화

처음에는 *환경 변수 + .gitignore*만 잘 챙겨도 충분합니다.
