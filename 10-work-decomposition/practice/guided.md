# Practice — 가이드 실습 (10강 작업 분해 + n8n)

> `_shared/guided-practice-protocol.md`의 7단계 + **n8n 설치 + LLM 노드 무료/유료/스킵 분기**.

## 0. 진입 직전 (draft 정리)

이론에서 적은 `big_task` / `decomposed_steps` / `dependencies` / `first_workflow` / `llm_node_choice`를 정리해 보여줌.

## 1. 옵션 제시 (2개 인라인)

```
어떻게 진행하시겠어요?

  (1) {{name}}님 본인 작업으로 워크플로우 만들기 (가장 추천)
  (2) 가상 사례 — 예: "주간 리포트 자동 생성"

번호로 답해주세요.
```

## 2. 공통 흐름

### 2-1. Docker 설치 점검 (학습자 OS 맞춤)

{{os:darwin}}
```bash
# Docker 설치 확인
docker --version 2>&1 || echo "Docker 미설치 — Docker Desktop 설치 필요"
```
{{/os}}

{{os:win32}}
```powershell
docker --version 2>&1
```
{{/os}}

미설치 시 Docker Desktop 다운로드 페이지로 안내. *5~10분 소요*.

### 2-2. n8n 설치 + 첫 실행

{{os:darwin}}
```bash
# n8n Docker 이미지 다운로드 + 실행
docker run -d --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n
```
{{/os}}

{{os:win32}}
```powershell
docker run -d --name n8n -p 5678:5678 -v ${HOME}/.n8n:/home/node/.n8n n8nio/n8n
```
{{/os}}

브라우저에서 `http://localhost:5678` 접속 → 첫 화면.

### 2-3. 첫 워크플로우 만들기 (노드 3~4개)

학습자에게 안내:
1. "+ Add first step" 클릭 → Manual Trigger 선택
2. Set 노드 추가 → 변수 설정
3. (선택) HTTP Request 노드로 외부 데이터 가져오기
4. (선택) LLM 노드 추가 (다음 단계)

### 2-4. LLM 노드 추가 (학습자 `llm_node_choice`에 따라 분기)

**무료 옵션**:
```
HTTP Request 노드를 추가해서 다음 URL을 호출하세요.

  - Google AI Studio: https://generativelanguage.googleapis.com/...
  - OpenRouter (무료 모델): https://openrouter.ai/api/...

키는 6강에서 발급받은 것을 환경 변수로 설정해두면 됩니다.
```

**유료 옵션**:
```
유료 키 사용 시 호출당 비용 발생. 진행하시겠어요?
  (1) 진행
  (2) 무료 옵션으로 전환
  (3) LLM 노드 빼기 (스킵)
```

**스킵 옵션**:
```
LLM 노드 없이 워크플로우만 완성합니다. Set 노드와 HTTP Request만으로도
가치 있는 자동화가 가능해요.
```

### 2-5. 실행 + 결과 확인
- "Execute Workflow" 버튼 클릭
- 각 노드의 *초록불* 확인
- 마지막 노드 데이터 점검

## 3. 검증 기준

| 항목 | 통과 기준 |
|---|---|
| n8n 컨테이너 *정상 실행* | ✅ |
| 워크플로우가 노드 3~4개 *연결* | ✅ |
| 1회 *실행 성공* (LLM 노드 스킵해도 OK) | ✅ |

3개 중 *2개 이상* 통과 시 ✅.

## 4. 트러블슈팅

- Docker 미설치 → Docker Desktop 설치 안내 (10분 소요)
- 포트 5678 충돌 → `-p 8080:5678`처럼 다른 포트 사용
- n8n UI 안 뜸 → `docker logs n8n`으로 로그 확인
- LLM 호출 실패 → 키 환경 변수 점검

## 5. 마무리

### 진도 갱신
- 통과: `status = "completed"`, `practice_status = "done"`

### 다음 강의 안내

```
🎉 10강 완주! 시각적 워크플로우의 힘을 직접 보셨어요.

다음 강의로 가시겠어요?
  (1) 11강(tool-selection) — 도구 선택 사고법
  (2) 메뉴로
  (3) 종료
```
