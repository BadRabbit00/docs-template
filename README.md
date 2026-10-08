# docs-kit — справочная документация проекта как источник правды

Что внутри:

| путь | что это |
|---|---|
| `docs/` | пустой скелет: скопируй в корень репозитория и заполняй |
| `docs/_meta/ids.md` | система ID: все префиксы и в каком файле каждый определяется |
| `docs/_meta/format.md` | формат карточек и таблиц, единая система типов для всех языков, бюджет строк |
| `docs/_meta/workflow.md` | процесс «сначала документ, потом код», маркеры `doc:` в коде, как читать |
| `docs/_meta/checklist.md` | чеклист «что вообще бывает в проекте» — по нему ничего не забудешь |
| `wk docs check` | встроенная проверка документации + генерация `_meta/registry.md`; Python в проекте не нужен |
| `docs/components/_template/` | шаблон папки компонента — копируй как `components/<имя>/` |
| `docs/decisions/ADR-0000-template.md` | шаблон архитектурного решения |
| `example/` | заполненный пример: 2 сервиса (Go + Python), БД, события, модель, код с маркерами |
| `AGENTS-snippet.md` | блок для `AGENTS.md` / `CLAUDE.md` / инструкций агента |

Быстрый старт:

```
cp -r docs-kit/docs ./docs
cp -r docs/components/_template docs/components/<имя-компонента>
wk docs check
```

Посмотреть, как выглядит готовое: `example/docs/INDEX.md`, затем `example/docs/_meta/registry.md`
(из каталога `example/` запусти `wk docs check`).

Для проекта нужен `.wiki-project.yaml`, создаваемый `wk init`. Единый гейт —
`wk check`, в CI — `wk check --strict`: документация и актуальность политик.
Для старого проекта `wk docs upgrade` удаляет прежний `docs/_meta/check.py`.
Реестр `_meta/registry.md` остаётся генерируемым файлом, который коммитится.
