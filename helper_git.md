# GIT
```bash
git init                            # инициализация репозитория в папке
git config --global user.name "Имя"      # имя автора коммитов
git config --global user.email "mail"    # email автора
git config --global init.defaultBranch main   # дефолтная ветка — main
git remote add origin git@github.com:User/repo.git   # привязать удалённый репозиторий
git remote -v                       # показать удалённые
git clone git@github.com:User/repo.git   # клонировать репозиторий
git status                          # что изменилось
git add .                           # добавить всё в индекс
git add имя_файла                   # добавить один файл
git restore имя_файла               # отменить изменения в файле
git rm имя_файла                    # удалить файл и внести в индекс
git commit -m "Текст коммита"       # зафиксировать изменения
git commit --amend                  # подправить последний коммит
git pull origin main                # забрать изменения с GitHub
git pull                            # если отслеживающая ветка настроена
git push origin main                # отправить изменения на GitHub
git push                            # если отслеживающая ветка настроена
git push --force origin main        # перезаписать ветку (осторожно!)
git branch                          # показать локальные ветки
git branch -a                       # показать все ветки (лок+remote)
git branch новая_ветка              # создать ветку
git checkout новая_ветка            # перейти в ветку
git checkout -b новая_ветка         # создать и сразу перейти
git branch -m старо ново            # переименовать текущую ветку
git branch --set-upstream-to=origin/main   # связать локальную main с origin/main
git branch -d имя_ветки             # удалить локальную ветку
git push --delete origin имя_ветки  # удалить ветку на GitHub
git log --oneline                   # короткий журнал коммитов
git log --oneline --graph           # ветки и коммиты как граф
git branch -vv                      # ветки + с какой удалённой связаны
git reset --hard HEAD               # откатить все изменения до последнего коммита
git reset --soft HEAD~1             # вернуть последний коммит в индекс
git clean -fd                       # удалить неотслеживаемые файлы и папки
```
