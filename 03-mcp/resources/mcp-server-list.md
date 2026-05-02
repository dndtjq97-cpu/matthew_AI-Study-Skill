# 자주 쓰이는 MCP 목록

> 정책·패키지 이름은 자주 바뀝니다. 가입·설치 전 *공식 저장소*에서 최신 정보 확인.

## 무료·공식 MCP

| MCP | 용도 | 패키지 (npm 또는 pypi) |
|---|---|---|
| filesystem | 폴더 안 파일 읽기·쓰기 | `@modelcontextprotocol/server-filesystem` |
| memory | 장기 메모리 보관 | `@modelcontextprotocol/server-memory` |
| github | GitHub 이슈·PR 조회 | `@modelcontextprotocol/server-github` |
| sqlite | 작은 DB 조회 | `@modelcontextprotocol/server-sqlite` |
| fetch | 웹 페이지 가져오기 | `@modelcontextprotocol/server-fetch` |
| postgres | Postgres DB 조회 | `@modelcontextprotocol/server-postgres` |

## 외부 API 연결 MCP

다음은 *외부 API의 요금*이 별도로 적용될 수 있어요.

- Brave Search MCP — 검색 API
- Google Drive MCP — 구글 드라이브 (인증 필요)
- Slack MCP — 슬랙 메시지 (워크스페이스 권한 필요)

## 안전 점검 체크리스트

새 MCP 추가 전:
- [ ] 공식 저장소(`@modelcontextprotocol/...` 또는 잘 알려진 회사)에서 받았나?
- [ ] 권한 범위가 *최소 필요*만 되어 있나?
- [ ] 민감 폴더·자료에 접근하지 않게 *경로 제한*했나?

## 더 알아보기

- 공식 MCP 저장소: github.com/modelcontextprotocol
- 커뮤니티 목록: 검색 시 항상 *별·최근 업데이트* 확인
