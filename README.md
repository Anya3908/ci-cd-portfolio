# CI/CD Portfolio — GitHub Actions

Портфолио учебных работ по CI/CD с публикацией артефактов: Docker-образы в **GHCR** и бинарники в **GitHub Releases**.

## 📊 Сводная таблица

| № | Работа | Артефакт | Триггер | Репозиторий | Actions | Результат |
|---|--------|----------|---------|-------------|---------|-----------|
| 1 | **Rust + GHCR** | Docker-образ | push `main` | [hello-rust](https://github.com/Anya3908/hello-rust) | [▶ Actions](https://github.com/Anya3908/hello-rust/actions) | [📦 Package](https://github.com/Anya3908?tab=packages) |
| 2 | **Go + GHCR** | Docker-образ | push `main` | [hello-go](https://github.com/Anya3908/hello-go) | [▶ Actions](https://github.com/Anya3908/hello-go/actions) | [📦 Package](https://github.com/Anya3908?tab=packages) |
| 3 | **Go + Releases** | 5 бинарников | push tag `v*` | [hello-go-releases](https://github.com/Anya3908/hello-go-releases) | [▶ Actions](https://github.com/Anya3908/hello-go-releases/actions) | [🏷 Releases](https://github.com/Anya3908/hello-go-releases/releases) |
| 4 | **Python + Releases** | 3 бинарника | push tag `v*` | [hello-python](https://github.com/Anya3908/hello-python) | [▶ Actions](https://github.com/Anya3908/hello-python/actions) | [🏷 Releases](https://github.com/Anya3908/hello-python/releases) |
| 5 | **C#/.NET + Releases** | 5 бинарников | push tag `v*` | [hello-dotnet](https://github.com/Anya3908/hello-dotnet) | [▶ Actions](https://github.com/Anya3908/hello-dotnet/actions) | [🏷 Releases](https://github.com/Anya3908/hello-dotnet/releases) |

## 🎯 Что в каждой работе

| Работа | Что собирается | Куда публикуется | Особенности |
|---|---|---|---|
| 1. Rust + GHCR | Docker-образ | GHCR | `cargo fmt`, `clippy`, `cargo test`, multi-stage Docker |
| 2. Go + GHCR | Docker-образ | GHCR | `gofmt`, `go vet`, `go test`, `CGO_ENABLED=0` |
| 3. Go + Releases | 5 бинарников | GitHub Releases | `GOOS`/`GOARCH`, matrix 5 платформ, `-ldflags -X` |
| 4. Python + Releases | 3 бинарника | GitHub Releases | PyInstaller `--onefile`, matrix 3 ОС, `ruff`, `pytest` |
| 5. C#/.NET + Releases | 5 бинарников | GitHub Releases | `dotnet format`, `xUnit`, `dotnet publish -r <RID>` |

## 🎓 Освоенные технологии

- **CI/CD:** GitHub Actions
- **Языки:** Rust, Go, Python, C#/.NET
- **Реестры:** GHCR (Docker-образы), GitHub Releases (бинарники)
- **Линтеры:** `cargo fmt`, `clippy`, `gofmt`, `go vet`, `ruff`, `dotnet format`
- **Тесты:** `cargo test`, `go test`, `pytest`, `xUnit`
- **Контейнеризация:** multi-stage Docker, `CGO_ENABLED=0`, `alpine`
- **Сборка бинарников:** `go build` (cross-compile), PyInstaller (per-OS), `dotnet publish -r <RID>` (cross-compile)
- **Матричные сборки:** 5 платформ (Go), 3 ОС (Python), 5 RID (.NET)
- **Версионирование:** `-ldflags -X` (Go), `__version__` (Python), `<Version>` в `.csproj` (.NET)
- **Публикация:** `docker/build-push-action`, `softprops/action-gh-release`

## 🔑 Ключевые отличия

### GHCR vs GitHub Releases

| Аспект | **GHCR** | **GitHub Releases** |
|---|---|---|
| Артефакт | Docker-образ | Бинарник |
| Триггер | push в `main` | push тега `v*` |
| Установка у пользователя | Docker обязателен | Не нужен |
| Размер | ~10-15 МБ | 1.5-70 МБ |
| Кому | DevOps, серверы | Конечные пользователи |

### Cross-compilation: Go vs Python vs .NET

| Язык | Cross-compile | Runner'ов в матрице |
|---|---|---|
| **Go** | ✅ Есть (`GOOS`/`GOARCH`) | **1** |
| **Python** | ❌ Нет (PyInstaller встраивает платформо-зависимый интерпретатор) | **3** |
| **.NET** | ✅ Есть (`-r <RID>`) | **1** |

## 📝 Автор

Учебные работы по CI/CD · 2026 · **Anya3908**