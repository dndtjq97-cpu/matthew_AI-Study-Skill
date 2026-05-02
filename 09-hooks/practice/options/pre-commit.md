# Option: 커밋 전 hook (pre-commit)

## 한 줄 요약
git 커밋을 *시도할 때* 자동으로 검사가 발사돼요. 통과해야 커밋 진행.

## 흔한 액션 예시
- 코드 포맷팅 검사
- 비밀번호·키 노출 점검
- 테스트 실행 (빠른 것만)

## 사전 점검
- git 저장소 안에서 작업 중
- pre-commit 도구 설치 (`pip install pre-commit` 등)

## hook 정의 예시

`.pre-commit-config.yaml` 파일에:

```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.5.0
    hooks:
      - id: detect-private-key  # 비밀 키 노출 감지
      - id: trailing-whitespace
      - id: end-of-file-fixer
```

## 등록 + 발사 테스트

{{os:darwin}}
```bash
# pre-commit 설치 (한 번만)
pip install pre-commit

# 저장소에 hook 등록
pre-commit install

# 모든 파일에 한 번 시범 실행
pre-commit run --all-files
```
{{/os}}

{{os:win32}}
```powershell
pip install pre-commit
pre-commit install
pre-commit run --all-files
```
{{/os}}

## 발사 테스트

1. 작은 파일 수정
2. `git add .` → `git commit -m "test"`
3. hook이 발사되는지 확인 (검사 결과가 보임)

## 자주 발생하는 에러
- "pre-commit not found" → PATH 점검
- 검사 통과해도 커밋 안 됨 → `git commit --no-verify`로 hook 우회 (응급용, 평소엔 X)

## 마무리 안내

같은 패턴으로 *push 전 hook*도 만들 수 있어요. push 전엔 더 무거운 검사(테스트 전체 등)를 둘 수 있어요.
