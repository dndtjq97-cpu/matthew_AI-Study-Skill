# 부록 — 심볼릭 링크 패턴 (둘 다 지원)

> 이 파일은 *한 청크*를 담고 있습니다.

## Chunk 1

여러 도구를 쓰는데 *AGENTS.md와 CLAUDE.md 내용이 같다면* 심볼릭 링크로 *한 파일 두 이름*을 만들 수 있어요.

{{os:darwin}}
```bash
# 프로젝트 폴더에서
cd ~/my-project

# AGENTS.md를 CLAUDE.md로 심볼릭 링크
ln -s AGENTS.md CLAUDE.md

# 확인
ls -la CLAUDE.md
```
{{/os}}

{{os:win32}}
```powershell
cd $HOME\my-project

# 심볼릭 링크 (관리자 권한 필요할 수 있음)
New-Item -ItemType SymbolicLink -Path CLAUDE.md -Target AGENTS.md

# 확인
Get-Item CLAUDE.md
```
{{/os}}

이렇게 하면 AGENTS.md를 *수정하면* CLAUDE.md도 자동으로 같은 내용. 두 파일을 따로 관리할 필요 없어요.

✅ **이 부록 끝!** 짧지만 중요한 패턴이에요. 다른 부록 더 보시겠어요?
