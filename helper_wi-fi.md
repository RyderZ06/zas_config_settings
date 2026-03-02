# WI‑FI
```bash
sudo iw dev wlan0 scan | grep SSID   # сканировать Wi‑Fi сети
iwconfig wlan0                       # статус беспроводного интерфейса
rfkill list                          # проверить блокировку Wi‑Fi/радио
sudo ip link set wlan0 up            # включить интерфейс Wi‑Fi
sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf   # запустить wpa_supplicant
sudo dhclient wlan0                  # получить IP по DHCP
ping -c 4 1.1.1.1                    # проверить связь (Cloudflare DNS)
curl ifconfig.me                     # показать внешний IP
nslookup google.com                  # проверить DNS
sudo killall -9 wpa_supplicant       # принудительно остановить wpa_supplicant
sudo systemctl restart networking    # перезапустить сетевой стек
journalctl -u wpa_supplicant -n 30   # последние 30 логов wpa_supplicant
wpa_passphrase "SSID" "пароль" >> /etc/wpa_supplicant.conf   # безопасно добавить Wi‑Fi‑сеть
cp /etc/wpa_supplicant.conf ~/wifi_backup.conf   # резервная копия конфига Wi‑Fi
tar -czvf configs_backup.tar.gz ~/.config/i3/   # бэкап настроек i3
```

# СЕТЬ ДОПОЛНИТЕЛЬНО
```bash
curl -O URL                         # скачать файл по URL
wget --continue URL                 # продолжить прерванную загрузку
ssh user@host -p 2222               # SSH с нестандартным портом
scp file.txt user@host:/path        # скопировать по SSH
ps aux | grep process               # найти процесс по имени
kill -9 PID                         # жёстко завершить процесс
sudo fdisk -l                       # список разделов диска
sudo mount /dev/sda1 /mnt           # вручную смонтировать раздел
```

# WI‑FI: подключение вручную (antiX Linux)
## 📡 Общая диагностика
```bash
iwconfig wlan0                 # статус и режим подключения Wi‑Fi
sudo wpa_cli status             # статус wpa_supplicant
ip a show wlan0                 # посмотреть, есть ли IP у интерфейса
ping 8.8.8.8                    # проверить базовую связь
sudo iwlist wlan0 scan | grep ESSID   # показать доступные Wi‑Fi сети
```
## 📝 Новая сеть в конфиге
```bash
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf   # отредактировать список сетей
```

## 🔹 1. Включить и разблокировать Wi‑Fi
```bash
sudo ip link set wlan0 up       # включить интерфейс
sudo rfkill unblock wifi        # разблокировать Wi‑Fi (если было заблокировано)
```

## 🔹 2. Поиск доступных сетей (опционально)
```bash
sudo iwlist wlan0 scan | grep ESSID   # показать доступные сети
```

## 🔹 3. Подключение к уже настроенной сети
```bash
sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf   # запустить wpa_supplicant в фоне
```

## 🔹 4. Получить IP‑адрес
```bash
sudo dhclient wlan0             # получить IP по DHCP
```

## 🔹 5. Проверка интернета и DNS
```bash
ping -c 4 8.8.8.8              # проверить связь с интернетом
ping -c 4 google.com           # проверить работу DNS
```

## 🔹 6. Отключение Wi‑Fi
```bash
sudo killall wpa_supplicant     # остановить подключение
sudo ip link set wlan0 down     # выключить интерфейс
```

## 💡 Полезные команды‑заготовки
```bash
ip a                            # список всех интерфейсов и их IP
iwconfig wlan0                  # детали Wi‑Fi интерфейса
sudo wpa_cli status             # текущий статус wpa_supplicant

# ⚠️ Важные нюансы (пример конфига)
# sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
#
# должен содержать:
#
# ctrl_interface_group=0
# ctrl_interface=/run/wpa_supplicant
# ap_scan=1
# update_config=1
#
# network={
#     ssid="MTS_GPON_F6F6"
#     psk="GTA4GN74"
#     key_mgmt=WPA-PSK
#     priority=1
# }
#
# сохранить: Ctrl+O → Enter → Ctrl+X
```

## 🎯 Пример полного цикла (подключиться → проверить → отключиться)
```bash
sudo ip link set wlan0 up
sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
sudo dhclient wlan0             # подключение завершено

ping -c 4 google.com            # проверка интернета

sudo killall wpa_supplicant     # отключить Wi‑Fi
sudo ip link set wlan0 down
```
