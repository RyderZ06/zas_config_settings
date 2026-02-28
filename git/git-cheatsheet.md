# GIT-CHEATSHEET
# Git-шпаргалка для работы в Antix/Linux
# Репозитории: zas_docs, zas_config_settings, zas_* (личные)


1. Базовые команды для рабочего репозитория

```bash
# посмотреть состояние
git status

# добавить все изменения
git add .

# сделать коммит
git commit -m "Описание изменений"

# забрать изменения с GitHub
git pull origin main

# отправить изменения на GitHub
git push origin main
```
2. Переименовать ветку master → main

Если ветка называется master, а хочешь сделать main:

```bash
# 1. посмотреть, где сейчас
git branch

# 2. переименовать локально
git branch -m master main

# 3. связать с origin/main
git branch --set-upstream-to=origin/main

# 4. убедиться, что всё чисто
git branch -vv
```
Если хочешь, можешь после этого удалить master на удалённом репозитории:

```bash
git push --delete origin master
```
3. Исправить проблему «Your configuration specifies to merge with the ref 'refs/heads/master'»

Если git pull ругается на master, но на GitHub уже есть только main:

```bash
# 1. убедиться, что локально нет master
git branch -a

# 2. если есть master, переименовать в main
git branch -m master main

# 3. явно связать main с origin/main
git branch --set-upstream-to=origin/main

# 4. проверить, что всё ок
git branch -vv
```
4. Почистить .git/config от дублей

Открываем:

```bash
nano .git/config
```
В секции:

```text
[branch "main"]
```
оставить только:

```text
[branch "main"]
        remote = origin
        merge = refs/heads/main

и удалить:

    второй блок [branch "main"],

    merge = refs/heads/master,

    лишние дубли merge = refs/heads/main.
```
5. Когда нужно сделать git pull и git push

    Перед git add (если давно не синхронизировался):

```bash
git pull origin main
```
После git commit:

```bash
git push origin main
```
Если ты один работаешь в репозитории, можно использовать сокращённо:

```bash
git pull
git push
```
6. Жизненный цикл правки в файлах

Вот типичная последовательность:

```bash
# 1. открываем файлы и редактируем

# 2. проверяем, что изменилось
git status

# 3. добавляем изменения
git add .

# 4. делаем коммит
git commit -m "Что именно я изменил"

# 5. пушим в GitHub
git push origin main
```
7. Полезные проверочные команды

```bash
# что именно делает текущая ветка
git branch -vv

# полный список веток (локальные и удалённые)
git branch -a

# если что‑то пошло не так — что тут
git status
```

1. Инициализация и базовые настройки

```bash
git init                          # инициализация репозитория в папке
git config --global user.name "Имя"      # установить имя автора
git config --global user.email "mail"    # установить email автора
git config --global init.defaultBranch main   # дефолтная ветка — main
```
2. Работа с удалённым репозиторием (GitHub)

```bash
git remote add origin git@github.com:User/repo.git   # привязать GitHub
git remote -v                     # посмотреть привязанные удалённые
git clone git@github.com:User/repo.git  # клонировать репозиторий
```
3. Цикл правок (локально)

```bash
git status                       # что изменилось
git add .                        # добавить всё в индекс
git add имя_файла                # добавить только один файл
git restore имя_файла            # отменить изменения в файле
git rm имя_файла                 # удалить файл и добавить в индекс
git commit -m "Текст коммита"    # зафиксировать изменения
git commit --amend               # подправить последний коммит
```
4. Синхронизация с GitHub

```bash
git pull origin main             # забрать изменения с GitHub
git pull                         # если отслеживающая ветка настроена
git push origin main             # отправить изменения на GitHub
git push                         # если отслеживающая ветка настроена
git push --force origin main     # перезаписать GitHub (осторожно!)
```
5. Ветки (branches)

```bash
git branch                       # показать локальные ветки
git branch -a                    # показать все (локальные и удалённые)
git branch новая_ветка           # создать ветку
git checkout новая_ветка         # перейти в ветку
git checkout -b новая_ветка      # создать и сразу перейти
git branch -m старо ново         # переименовать текущую ветку
git branch --set-upstream-to=origin/main   # связать локальную с origin/main
git branch -d имя_ветки          # удалить локальную ветку
git push --delete origin имя_ветки # удалить ветку на GitHub
```
6. Быстрая проверка состояния

```bash
git log --oneline                # короткий журнал коммитов
git log --oneline --graph        # ветки и коммиты в виде графа
git branch -vv                   # ветки + с какой удалённой связаны
git status                       # что изменено, что добавлено, что не в Git
```
7. Восстановление (если что‑то пошло не так)

```bash
git reset --hard HEAD            # откатить все изменения до последнего коммита
git reset --soft HEAD~1          # вернуть последний коммит в индекс
git clean -fd                    # удалить неотслеживаемые файлы и папки
```