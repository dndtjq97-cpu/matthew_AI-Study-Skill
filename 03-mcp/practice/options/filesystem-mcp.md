# Option: filesystem MCP

## 한 줄 요약
이 MCP를 연결하면 에이전트가 *지정한 폴더*의 파일을 읽고 쓸 수 있어요.

## 사전 점검
- Node.js 18 이상 설치 (학습자 OS 맞춤 확인 명령)
- 연결할 폴더 *경로* 결정 ({{name}}님이 미리 정해주세요)
- 그 폴더에 *민감 데이터*가 없는지 확인 (안전상)

## 비용 안내
- MCP 자체 무료
- 에이전트가 폴더를 읽을 때 LLM 호출 비용은 별도 (보통 작음)

## 설치 명령 (학습자 OS 맞춤)

{{os:darwin}}
```bash
# filesystem MCP 서버 설치
npm install -g @modelcontextprotocol/server-filesystem

# 설치 확인
mcp-server-filesystem --version 2>&1 || echo "설치는 됐지만 직접 실행은 안 함"
```
{{/os}}

{{os:win32}}
```powershell
# filesystem MCP 서버 설치
npm install -g @modelcontextprotocol/server-filesystem

# 설치 확인
mcp-server-filesystem --version 2>&1
```
{{/os}}

## 에이전트에 등록

도구별 등록 위치는 부록 박스 참조 (도구마다 살짝 다름). 일반적으로 도구의 MCP 설정 파일에 다음을 추가:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "mcp-server-filesystem",
      "args": ["<연결할 폴더 경로>"]
    }
  }
}
```

## 첫 호출 안내

```
이제 에이전트한테 시켜보세요.

  👉 "내 [폴더 경로]에서 가장 최근에 수정된 파일 알려줘"

답이 나오면 그대로 붙여넣어 주세요.
```

## 자주 발생하는 에러

- **"command not found: mcp-server-filesystem"** — npm 글로벌 경로가 PATH에 없음. `npm config get prefix` 확인.
- **"Permission denied"** — 폴더 읽기 권한 부족. 다른 폴더 시도 또는 권한 확인.
- **에이전트가 인식 못함** — 도구 재시작 필요.

## 마무리 안내

방금 배운 패턴은 *다른 MCP*에도 동일해요. 설치 → 등록 → 재시작 → 호출. 다음 MCP를 추가할 때도 같은 흐름이에요.
