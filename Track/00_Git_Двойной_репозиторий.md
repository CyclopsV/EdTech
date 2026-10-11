# Шпаргалка: Git + зеркалирование на две платформы

**Аккаунты:**  
GitHub — `CyclopsV`  
GitVerse — `Cyclops`  
SSH-ключ (ed25519) добавлен на обе платформы.

**Проверка связи:**
```bash
ssh -T git@github.com
ssh -T git@gitverse.ru
```

**Локальный репозиторий:** `~/Desktop/DEV/EdTech`, ветка `main`, есть `.gitignore` (под Go).

**Конфигурация ремоутов:**
- `origin` = GitVerse — основное хранилище (fetch + два push-адреса).
- `github` = GitHub — зеркало.

```bash
git remote -v    # у origin: один fetch (gitverse) и два push (gitverse + github)
git branch -vv   # main отслеживает origin/main, то есть GitVerse
```

**Ежедневный цикл:**
```bash
git pull              # подтянуть изменения (из GitVerse)
git add .             # собрать изменения
git commit -m "..."   # зафиксировать
git push              # уходит СРАЗУ в GitVerse и GitHub
```

**Если нужно работать только с GitHub:** `git push github main` и `git pull github main`.

**Полезно помнить:**
- Хеши коммитов в обоих хранилищах совпадают — это одна история.
- Если push отклоняется (`rejected` / `non-fast-forward`) — сначала `git pull`, потом снова `git push`.
- Комментарии в конфигах и коде держим на русском.
