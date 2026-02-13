# 1. Если есть старый .venv - удали
deactivate
rm -rf .venv

# 2. Создай новое виртуальное окружение с Python 3.13 (рекомендуется для Panel)
python3.13 -m venv .venv
# ИЛИ если 3.13 не доступен:
python -m venv .venv

# 3. Активируй
source .venv/Scripts/activate  # Git Bash
# ИЛИ .venv\Scripts\activate  # CMD

# 4. Обнови pip
python -m pip install --upgrade pip

# if need. Очисти кэш pip
pip cache purge

# 5. Установи проект в режиме редактирования
pip install -e .

# 6. Установи dev зависимости
pip install -e ".[dev]"

# Проверь, какие политики применяются
pip debug --verbose | grep -i "policy"

# Проверь версию Windows и политики
systeminfo | findstr /B /C:"OS Name" /C:"OS Version"

# Проверь, доступен ли компилятор
gcc --version
cl --version

# 1. Проверь, что пакет установлен
pip list | grep zas