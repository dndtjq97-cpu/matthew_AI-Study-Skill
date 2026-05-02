# Option: memory MCP

## 한 줄 요약
대화가 끝나도 *기억*을 보관해서, 다음 대화에서 *이어가게* 해주는 MCP예요.

## 사전 점검
- Node.js 18 이상
- 디스크 공간 100MB 이내 (메모리 저장용)

## 비용 안내
- MCP 자체 무료
- 메모리 데이터를 LLM에 전달할 때 토큰 비용 발생

## 설치 명령 (학습자 OS 맞춤)

{{os:darwin}}
```bash
# memory MCP 서버 설치
npm install -g @modelcontextprotocol/server-memory
```
{{/os}}

{{os:win32}}
```powershell
npm install -g @modelcontextprotocol/server-memory
```
{{/os}}

## 에이전트에 등록

```json
{
  "mcpServers": {
    "memory": {
      "command": "mcp-server-memory"
    }
  }
}
```

## 첫 호출 안내

```
이제 에이전트한테 시켜보세요.

  👉 "방금 우리 대화의 핵심을 메모리에 저장해줘"

저장이 잘 됐다는 답이 오면, 새 대화 창에서:

  👉 "메모리에 저장된 내용 알려줘"

이전 대화 내용이 나오면 ✅ 통과예요.
```

## 자주 발생하는 에러

- **저장은 되는데 다음 대화에서 안 보임** — 도구 재시작 후 메모리 폴더가 같은지 확인.
- **메모리가 너무 커짐** — 주기적으로 오래된 항목 정리.

## 마무리 안내

memory MCP는 *장기 프로젝트*에 특히 유용해요. 한 번 정한 결정·맥락이 매번 잊히지 않아요.
