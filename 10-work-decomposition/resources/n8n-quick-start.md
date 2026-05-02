# n8n 빠른 시작 가이드

## Docker로 n8n 띄우기 (학습자 OS 맞춤)

{{os:darwin}}
```bash
# 첫 실행 (-d는 백그라운드 실행)
docker run -d --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n

# 확인
docker ps | grep n8n

# 브라우저에서 접속
open http://localhost:5678
```
{{/os}}

{{os:win32}}
```powershell
docker run -d --name n8n -p 5678:5678 -v ${HOME}/.n8n:/home/node/.n8n n8nio/n8n

# 확인
docker ps | Select-String n8n

# 브라우저에서 접속
Start-Process http://localhost:5678
```
{{/os}}

## 자주 쓰는 명령

| 작업 | 명령 |
|---|---|
| 중지 | `docker stop n8n` |
| 재시작 | `docker start n8n` |
| 로그 보기 | `docker logs n8n` |
| 완전 삭제 | `docker rm -f n8n` |

## 첫 워크플로우 권장 노드

1. **Manual Trigger** — 버튼 한 번으로 시작
2. **Set** — 변수 정의 (입력 데이터)
3. **HTTP Request** — 외부 API 호출 또는 LLM
4. **Set** 또는 **Edit Fields** — 결과 정리

이 4단계면 거의 모든 자동화의 *시작점*이 됩니다.

## LLM 노드 무료 옵션 가이드

### Google AI Studio (Gemini)
```
URL: https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent
헤더: ?key={GOOGLE_API_KEY}
바디: {"contents": [{"parts":[{"text": "{{$json.input}}"}]}]}
```

### OpenRouter (무료 모델)
```
URL: https://openrouter.ai/api/v1/chat/completions
헤더: Authorization: Bearer {OPENROUTER_API_KEY}
바디:
{
  "model": "google/gemini-flash-1.5:free",
  "messages": [{"role": "user", "content": "{{$json.input}}"}]
}
```

## 자주 발생하는 에러

| 에러 | 원인·해결 |
|---|---|
| 포트 충돌 (5678) | 다른 포트로: `-p 8080:5678` |
| n8n UI 안 뜸 | `docker logs n8n`으로 시작 로그 확인 |
| 워크플로우 실행 안 됨 | 각 노드를 *개별*로 클릭해서 데이터 확인 |
| LLM 호출 401/403 | API 키 환경 변수 점검 |

## 워크플로우 저장 위치

`~/.n8n/` 폴더에 저장됨. 컨테이너 재시작해도 데이터 보존.
