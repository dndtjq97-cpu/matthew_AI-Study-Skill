# Lesson 10.5 — 첫 워크플로우 — 노드 3~4개

> 이 파일은 *한 청크*를 담고 있습니다.

## Chunk 1

처음 워크플로우는 *가장 단순한 모양*이 좋아요. 노드 3~4개로 시작하세요.

가장 흔한 첫 패턴:
```
[Manual Trigger] → [Set] → [HTTP Request] → [Set]
```

- **Manual Trigger** — 버튼 눌러 시작
- **Set** — 변수에 값 넣기
- **HTTP Request** — 외부 API 호출
- **Set** — 결과 정리

이 4노드 패턴 하나만 만들 줄 알면, 거기에 *LLM 호출*이나 *데이터 처리*를 끼워넣어 무한히 확장돼요.

🛠 **미션** — 2번 청크에서 적은 본인 큰 작업을 *3~5단계로* 분해해주세요. 한 줄씩 적으셔도 OK.

> 💾 적어주신 단계는 자동 보관됩니다. (`draft.decomposed_steps`, `draft.first_workflow`)
