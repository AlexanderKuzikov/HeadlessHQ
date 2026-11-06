<p align="center">
  <a href="https://opencode.ai"><img alt="OpenCode" src="https://img.shields.io/badge/OpenCode-CLI%20%7C%20Desktop-5e6ad2?logoColor=white"></a>
  <a href="https://github.com/AlexanderKuzikov/HeadlessHQ"><img alt="Windows" src="https://img.shields.io/badge/Windows-11-0078D6?logo=windows&logoColor=white"></a>
  <a href="LICENSE"><img alt="License" src="https://img.shields.io/badge/License-Apache_2.0-blue.svg"></a>
</p>

<h1 align="center">HeadlessHQ</h1>
<p align="center">Штаб-автодиспетчер: headless-сессии OpenCode исполняют задания, штаб принимает по отчётам</p>

---

HeadlessHQ — автоматизация протокола Штаб. Штаб-сессия пишет задание файлом и сама запускает кодовую сессию через `opencode run`, та выполняет работу, пишет отчёт в тот же файл, штаб принимает и продолжает. Цикл выдачи и приёмки закрывается без человека.

Это надстройка, а не замена. Ручной Штаб (человек открывает сессию фразой-запуском) остаётся: он — запасной путь и режим для неоднозначных работ. Один и тот же файловый протокол обслуживает оба режима.

- **Файл как контракт** — обмен только через `docs/tasks/NNNN-*.md`, контекст сессии штабу не нужен
- **Deny-профиль** — безопасность unattended-запуска держится на запретах, а не на вопросах
- **Приёмка по фактам** — exit-код плюс отчёт с выводами команд, иначе разбор
- **Свой репо на сессию** — параллельность только между репозиториями, внутри — строго очередь

## Быстрый старт

```bash
git clone https://github.com/AlexanderKuzikov/HeadlessHQ.git
cd HeadlessHQ
# пока только документация, исполнение — по шагам docs/PLAN.md
```

## Документация

- [`docs/PROTOCOL.md`](docs/PROTOCOL.md) — протокол выдачи, запуска и приёмки
- [`docs/PLAN.md`](docs/PLAN.md) — шаги реализации
- [`docs/CONTEXT.md`](docs/CONTEXT.md) — состояние проекта
- [`docs/DECISIONS.md`](docs/DECISIONS.md) — архитектурные решения

## Стек

| Компонент | Технология |
|-----------|------------|
| Оркестрация | OpenCode CLI (`run`, `--agent`, `--auto`) |
| Наблюдение | OpenCode Desktop (общий стор сессий) |
| Скрипты | PowerShell 7, Windows 11 |

## Статус

**v0.0.0** — скелет репозитория и зафиксированный протокол. Исполнение — по шагам плана.

## Лицензия

[Apache-2.0](LICENSE) © Alexander Kuzikov
