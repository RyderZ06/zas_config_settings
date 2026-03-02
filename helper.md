# 1. ТЕРМИНАЛ
```bash
Ctrl+Alt+T                    # Открыть roxterm
roxterm                       # Запуск вручную
x-terminal-emulator           # Универсальный вызов
pwd # print working directory (shows your current location)
ls -la # lists directory for a detailed view including hidden files
ps # displays information about current running processes (ps aux)
free -h # Displays memory usage
df -h # Disk free; show disk space usage in human-readable format
top # Provides a real-time, dynamic view of running system processes
uname -a # Display system information, often used with -a for all details
```

# ФАЙЛЫ И ДИРЕКТОРИИ
```bash
find /path -name "*.txt"            # найти файлы по имени
locate filename                     # быстрый поиск (предварительно updatedb)
grep -r "текст" /path               # рекурсивный поиск по содержимому
tree -L 2                           # дерево каталогов (2 уровня)
cp -rv dir1/ dir2/                  # копировать с прогрессом
rsync -ah --progress src/ dst/      # синхронизировать с прогрессом
mv -i file1 file2                   # переименовать с подтверждением
rm -rI dir/                         # удалить с подтверждением
chmod +x script.sh                  # сделать файл исполняемым
nano file.txt                       # простой редактор
micro file.txt                      # продвинутый редактор (если установлен)
cat file1 file2 > combined          # объединить файлы
less /var/log/syslog                # читать лог с прокруткой
```

# ПАКЕТЫ (Debian/antix)
```bash
sudo apt update               # Список пакетов
sudo apt list --upgradable    # Что обновить
sudo apt dist-upgrade         # Установить
sudo apt autoremove           # Очистка
sudo apt autoremove && sudo apt autoclean # Очистка
sudo reboot # Перезагрузитесь
apt search keyword                  # поиск пакета
sudo apt install package            # установить пакет
sudo apt remove --purge package     # полное удаление с конфигами
sudo apt autoremove                 # убрать ненужные зависимости
sudo dpkg -i package.deb            # ручная установка .deb
sudo apt --fix-broken install       # починить сломанные зависимости
apt changelog package               # история изменений пакета
```



# 3. IceWM HOTKEYS (zzz-icewm)
```bash
Ctrl+Esc      # Меню приложений
icewm --restart # Перезапуск WM
```

# Пять вещей которые должны быть под рукой в машине
1. Аптечка
2. Стеклобой и стропорез
3. Перчовый болончик струйный
4. Ключ на 10, для скидывания клем
5. Светоотражающий жилет


# I3WM
```bash
startx ~/.xinitrc i3                # запустить i3 с кастомным конфигом
mod+Enter                           # новый терминал
mod+Shift+q                         # закрыть текущее окно
mod+d                               # запуск rofi / меню
mod+[1-9]                           # переключение рабочих столов
i3-msg restart                      # перезагрузить конфиг i3
mod+Shift+r                         # перезагрузить i3 без перезапуска сессии
mod+Shift+space                     # перевести окно в плавающий режим
i3-msg move workspace 2             # переместить окно на 2‑й workspace
```

# МОНИТОРИНГ СИСТЕМЫ
```bash
htop                                # интерактивный мониторинг процессов
free -h                             # свободная память
df -h                               # использование диска
iostat -xz 1                        # нагруженность дисков
nethogs                             # трафик по процессам
ps aux --sort=-%mem                 # процессы по памяти
pstree -p                           # дерево процессов
lsof -i :80                         # кто слушает порт 80?
iftop                               # трафик в реальном времени
ss -tulnp                           # все открытые порты с PID
vnstat -l                           # статистика трафика
bmon                                # графический мониторинг трафика
dmesg -T | grep -i error            # ошибки ядра
journalctl -p 3 -xb                 # критические системные ошибки
```
