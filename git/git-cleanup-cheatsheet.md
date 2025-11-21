# Шпаргалка: Как удалить большие файлы из истории Git и сбросить репозиторий

## 1. Найти большие файлы в истории

git rev-list --objects --all |
git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
sed -n 's/^blob //p' |
sort -n -k2 |
cut -c 1-12,41- |
numfmt --to=iec-i --suffix=B --padding=7 --field=2

- Запиши пути к подозрительно большим файлам для следующего шага.

## 2. Удалить большие файлы из истории (нужен [`git-filter-repo`](https://github.com/newren/git-filter-repo))

git filter-repo --path путь/к/файлу1 --invert-paths

- Для нескольких файлов:  

git filter-repo --invert-paths --path путь/к/файлу1 --path путь/к/файлу2

- Укажи точные пути к файлам из предыдущего шага.

## 3. (Радикально) — Начать с новой истории
> Используй, если не важно сохранить историю. Репозиторий сохранит только актуальные файлы, большие удалятся навсегда.

git checkout --orphan latest_branch  
git add -A  
git commit -m "Initial commit with current files"  
git branch -D main  
git branch -m main  
git push -f origin main

## 4. Добавлять файлы поэтапно
- Добавляй и коммить только нужные файлы:

git add путь/к/нужному_файлу  
git commit -m "Добавлен нужный файл"  
git push origin main

## 5. Настройка .gitignore
- Добавляй в `.gitignore` то, что не стоит коммитить:

*.zip  
movie/  
photo/  
archive/

## 6. Важно!
- Для файлов >100MB используй [Git LFS](https://git-lfs.github.com/)
- После переписывания истории всегда ПРИНУДИТЕЛЬНО пушь изменения:

git push -f origin main

- Предупреди коллег: историю нужно обновить вручную!

---

**Если не знаешь, какие папки удалять, всегда делай поиск крупных файлов (см. шаг 1).**

> Используй эту шпаргалку при ошибках с большими файлами или если потребуется очистить историю Git от мусора.







