# Создай новую структуру
mkdir -p src/zas_jupyternb

# Перемести существующие модули (измени пути под твою реальную структуру!)
mv src/dashboard src/zas_jupyternb/ 2>/dev/null || echo "dashboard not in src"
mv src/data_processing src/zas_jupyternb/ 2>/dev/null || echo "data_processing not in src"
mv src/utils src/zas_jupyternb/ 2>/dev/null || echo "utils not in src"

# Создай __init__.py в корне пакета
touch src/zas_jupyternb/__init__.py

# Создай cli.py (временный, чтобы установка прошла)
cat > src/zas_jupyternb/cli.py << 'EOF'
"""Command line interface for zas_jupyternb."""
def pipeline():
    """Run full pipeline."""
    print("ZAS Pipeline")
EOF

# Проверь структуру
tree src -L 2