# Option: Google AI Studio (Gemini)

## 한 줄 요약
Google Gemini API — 일일 한도까지 *무료* (변동 가능, 카드 정보 *없이* 시작 가능한 경우 많음).

## 사전 점검
- Google 계정 (Gmail 등)
- 카드 정보 *없이도* 시작 가능 (정책 확인)

## 💰 비용 안내

```
Google AI Studio는 무료 한도가 가장 너그러운 편이에요. 다만 정책은
자주 바뀌고, 무료 한도 안에서도 일정 사용량 이상은 데이터가 *학습*에
사용될 수 있어요. 가입 페이지에서 *프라이버시 정책* 확인 후 진행.

  (1) 진행할게요
  (2) 스킵
  (3) Anthropic으로 전환
```

## 가입 + 키 발급

1. aistudio.google.com 접속 → Google 계정으로 로그인
2. "Get API Key" 버튼
3. 새 프로젝트 생성 또는 기존 선택
4. 키 발급 → **즉시 복사**

## 키 안전 보관

{{os:darwin}}
```bash
echo 'export GOOGLE_API_KEY="AIza..."' >> ~/.zshrc
source ~/.zshrc
```
{{/os}}

{{os:win32}}
```powershell
[Environment]::SetEnvironmentVariable("GOOGLE_API_KEY", "AIza...", "User")
```
{{/os}}

## 첫 호출

{{os:darwin}}
```bash
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=$GOOGLE_API_KEY" \
  -H 'Content-Type: application/json' \
  -d '{
    "contents": [{"parts":[{"text": "안녕!"}]}]
  }'
```
{{/os}}

{{os:win32}}
```powershell
$body = @{
    contents = @(@{parts = @(@{text = "안녕!"})})
} | ConvertTo-Json -Depth 5

Invoke-RestMethod -Uri "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=$env:GOOGLE_API_KEY" `
  -Method Post `
  -Headers @{"Content-Type"="application/json"} `
  -Body $body
```
{{/os}}

## 비용 추적

aistudio.google.com → 사용량 대시보드. 무료 한도까지는 비용 없음.

## 자주 발생하는 에러

- **400** — 요청 형식 오류. JSON 점검.
- **403** — 키 권한 부족 또는 만료.
- **429** — 분당 한도 초과 (RPM 제한).
