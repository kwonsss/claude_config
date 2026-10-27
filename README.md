# claude_config

`~/.claude` 중 PC 간에 공유할 설정만 git 으로 관리한다.

## 추적 대상

- `CLAUDE.md` — 전역 지침
- `settings.json` — 권한, 모델, 플러그인(`enabledPlugins` / `extraKnownMarketplaces`)
- `skills/` — 직접 만든 스킬 (`skills/synced/` 는 claude.ai 에서 자동 동기화되므로 제외)
- `agents/`, `commands/` — 만들면 자동으로 추적됨

그 외(`.credentials.json`, `settings.local.json`, `projects/`, `sessions/`, `plugins/`, 캐시 등)는
`.gitignore` 의 화이트리스트 방식으로 전부 제외된다.
플러그인은 `settings.json` 의 설정만으로 새 PC 에서 자동 설치된다.

## 새 PC 설정

`~/.claude` 는 Claude Code 가 이미 만들어 두므로 clone 대신 init 후 체크아웃한다.

```bash
cd ~/.claude
git init -b main
git remote add origin git@github.com:kwonsss/claude_config.git   # SSH 가 안 되면 https://github.com/kwonsss/claude_config.git
git fetch origin
git reset --hard origin/main
git branch --set-upstream-to=origin/main main
```


## 변경 반영

```bash
cd ~/.claude && git add -A && git commit -m "..." && git push
```

다른 PC 에서는 `git pull`.
