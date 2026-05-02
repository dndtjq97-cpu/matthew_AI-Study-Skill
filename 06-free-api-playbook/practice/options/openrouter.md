# Option: OpenRouter

## 한 줄 요약
OpenRouter — 여러 모델을 한 곳에서 사용. *일부 무료 티어 모델*이 있어 시작 부담 적음.

## 사전 점검
- 이메일 주소 (또는 GitHub 계정)
- *무료 모델 한도*는 변동 가능. 가입 후 확인.

## 💰 비용 안내

```
OpenRouter는 *호출당 비용*이 모델별로 달라요. 무료 모델만 골라 쓰면
비용이 0이지만, 좋은 모델은 유료입니다.

  (1) 진행 (무료 모델 우선)
  (2) 스킵
  (3) 다른 옵션으로
```

## 가입 + 키 발급

1. openrouter.ai 접속 → 가입
2. "Keys" 메뉴 → "Create Key"
3. 키 발급 + 즉시 복사

## 키 안전 보관

{{os:darwin}}
```bash
echo 'export OPENROUTER_API_KEY="sk-or-..."' >> ~/.zshrc
source ~/.zshrc
```
{{/os}}

{{os:win32}}
```powershell
[Environment]::SetEnvironmentVariable("OPENROUTER_API_KEY", "sk-or-...", "User")
```
{{/os}}

## 무료 모델 골라 첫 호출

{{os:darwin}}
```bash
# 무료 모델 예시 (정책 변동 가능)
curl https://openrouter.ai/api/v1/chat/completions \
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "google/gemini-flash-1.5:free",
    "messages": [{"role": "user", "content": "안녕!"}]
  }'
```
{{/os}}

{{os:win32}}
```powershell
$body = @{
    model = "google/gemini-flash-1.5:free"
    messages = @(@{role="user"; content="안녕!"})
} | ConvertTo-Json -Depth 5

Invoke-RestMethod -Uri "https://openrouter.ai/api/v1/chat/completions" `
  -Method Post `
  -Headers @{
      "Authorization" = "Bearer $env:OPENROUTER_API_KEY"
      "Content-Type" = "application/json"
  } `
  -Body $body
```
{{/os}}

## 비용 추적

openrouter.ai → 대시보드에서 모델별 사용량·비용 확인. 모델 이름에 `:free` 붙은 것만 쓰면 비용 0.

## 자주 발생하는 에러

- **402 (Payment Required)** — 유료 모델인데 잔액 부족. 무료 모델로 변경.
- **404** — 모델 이름 오타. OpenRouter 모델 목록 페이지에서 정확한 이름 확인.
