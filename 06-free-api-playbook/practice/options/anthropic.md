# Option: Anthropic Claude API

## 한 줄 요약
Anthropic Claude API — 신규 가입 시 일정 크레딧 제공 (변동 가능).

## 사전 점검
- 이메일 주소
- 카드 정보 *필요할 수 있음* (가입 페이지에서 확인)
- 변동 가능한 무료 정책 → 가입 전 *현재 정책*을 console.anthropic.com 에서 확인

## 💰 비용 안내

```
Anthropic 무료 크레딧은 정책에 따라 자주 바뀝니다. 현재 정책을 가입
페이지에서 직접 확인해주세요.

  (1) 진행할게요 (현재 정책 확인 후)
  (2) 스킵 — 다른 옵션으로
  (3) 다른 옵션 안내 받기 (Google AI Studio 등)
```

## 가입 + 키 발급 단계

1. console.anthropic.com 접속 → 회원가입 (이메일 + 비밀번호)
2. 대시보드 → "API Keys" 메뉴
3. "Create Key" 버튼 → 이름 짓기 → 키 발급
4. **키는 한 번만 보임**. 안전한 곳에 즉시 저장.

## 키 안전 보관 (학습자 OS 맞춤)

{{os:darwin}}
```bash
# .env 파일에 저장 (프로젝트 폴더 안)
echo 'ANTHROPIC_API_KEY="sk-ant-..."' >> ~/.env

# 또는 셸 설정에 영구 등록
echo 'export ANTHROPIC_API_KEY="sk-ant-..."' >> ~/.zshrc
source ~/.zshrc
```
{{/os}}

{{os:win32}}
```powershell
# 환경 변수 영구 등록
[Environment]::SetEnvironmentVariable("ANTHROPIC_API_KEY", "sk-ant-...", "User")

# 새 PowerShell 창에서 확인
$env:ANTHROPIC_API_KEY
```
{{/os}}

## 첫 호출 (curl)

{{os:darwin}}
```bash
curl https://api.anthropic.com/v1/messages \
  -H "x-api-key: $ANTHROPIC_API_KEY" \
  -H "anthropic-version: 2023-06-01" \
  -H "content-type: application/json" \
  -d '{
    "model": "claude-haiku-4-5",
    "max_tokens": 100,
    "messages": [{"role": "user", "content": "안녕!"}]
  }'
```
{{/os}}

{{os:win32}}
```powershell
$body = @{
    model = "claude-haiku-4-5"
    max_tokens = 100
    messages = @(@{role="user"; content="안녕!"})
} | ConvertTo-Json -Depth 5

Invoke-RestMethod -Uri "https://api.anthropic.com/v1/messages" `
  -Method Post `
  -Headers @{
      "x-api-key" = $env:ANTHROPIC_API_KEY
      "anthropic-version" = "2023-06-01"
      "content-type" = "application/json"
  } `
  -Body $body
```
{{/os}}

## 비용 추적

console.anthropic.com → "Usage" 메뉴에서 일일·월별 사용량 확인.

## 자주 발생하는 에러

- **401** — 키 잘못. 다시 확인.
- **rate_limit** — 한도 초과. 분당 제한 또는 일일 제한 도달.
