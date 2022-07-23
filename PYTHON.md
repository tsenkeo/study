# Виртульное окружение python

**Создать виртульное окружение:**  

    python -m venv .venv
    
**Активировать виртуальное окружение:*

    .venv\Scripts\activate.bat

**Деактивировать:**

    .venv\Scripts\deactivate.bat

**Для Linux:**

    source .venv/bin/activate

**После активации виртуального окружения любые пакеты, установленные с помощью pip, будут сохраняться в папке .venv**

**Обновить pip перед установкой пакетов:**

    python -m pip install --upgrade pip
