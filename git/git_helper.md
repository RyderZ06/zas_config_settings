# Шпаргалка: Полное удаление файла/папки из Git и GitHub
*Полная очистка локальной папки/файла из Git истории и GitHub репозитория (без установки доп. инструментов).*

✅ Предварительные условия:  

- Приватный репозиторий
- Единственный разработчик

Сделайте бэкап!

🚀 Шаги по очистке
1. Перейти в orphan-ветку (удалить историю)  
bash  
`cd /путь/к/репозиторию`  
`git checkout --orphan new-main`  
`git rm -rf .`  
`git commit --allow-empty -m "Initial empty commit"`  
`git branch -D master`    # или main  
`git branch -m master`  

2. Принудительно перезаписать GitHub  
bash  
`git push origin master --force`

3. Разорвать связь с удалённым репозиторием  
bash  
`git remote remove origin`  
`git remote -v`  # проверка — список пустой  

4. Полная локальная очистка  
bash  
`rm -rf .git`      # удалить Git историю  
`rm -rf *`         # удалить все файлы  
`cd ..`            # выйти из папки  
`rm -rf имя_папки` # удалить пустую папку  

🗑️ Дополнительно: Удалить репозиторий на GitHub  
GitHub → Repository → Settings

Danger Zone → Delete this repository

Введите название → Подтвердить

⚠️ ВАЖНЫЕ замечания  
text  
✅ Работает на Windows (MINGW64/Git Bash), Linux  
✅ Не требует установки git-filter-repo/BFG  
✅ Перезаписывает ВСЮ историю коммитов  
❌ НЕ используйте для общих/публичных репозиториев!  
❌ Предупредите коллег перед --force push  
Готово! Репозиторий чист как новенький ✨