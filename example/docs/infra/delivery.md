# Сборка и выкатка

### PIPE-main — Проверка и деплой из main
status: implemented

- trigger: push в `main`
- where: GitHub Actions `.github/workflows/main.yml`
- steps: `wk check --strict` → тесты обоих сервисов → `nix build` → `nixos-rebuild switch` на ENV-prod
- rollback: `nixos-rebuild switch --rollback`
