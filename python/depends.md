# 1. Установите pre-commit (уже есть в dev зависимостях)
pip install pre-commit

# 2. Установите хуки в ваш .git
pre-commit install

# 3. (Опционально) Запустите на всех файлах разово
pre-commit run --all-files