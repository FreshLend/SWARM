# SWARM **RU** | [EN](README.EN.md)

**Scalable Workspace & Application Runtime for Modules**

SWARM - это модульное десктопное приложение на Python (PySide6), представляющее собой платформу для разработки и интеграции независимых модулей. Оно позволяет строить сложные системы из изолированных компонентов, которые работают в едином интерфейсе.

Вместо монолитного кода вы пишете изолированный модуль, помещаете его в папку `modules/`, и он автоматически появляется в интерфейсе программы.

## Особенности
*   **Hot Reload:** Разработка модулей без перезапуска приложения. Изменили код - нажали «Применить» в меню - модуль обновился.
*   **Разрешение зависимостей:** Если один модуль требует другой, ядро загрузит их в правильном порядке и проверит совместимость версий.
*   **Шина событий (Event Bus):** Модули общаются друг с другом через `api.call()` и `api.event`, не имея жестких связей.
*   **Готовый UI из коробки:** Встроенная тема, адаптивная сетка, локализация (i18n) и менеджер модулей.
*   **Свои иконки:** Используйте встроенные SVG-иконки или просто поместите файл `icon.svg` в папку модуля.

## Быстрый старт

```bash
git clone https://github.com/FreshLend/SWARM.git
cd SWARM
pip install -r requirements.txt
python main.py
```

> **Кастомизация:** Чтобы изменить название, логотип (ASCII-арт) и иконку приложения, отредактируйте файл `core/brand.py`.

## Как написать свой модуль

Создайте папку `modules/example/`. Внутри должно быть два файла:

**1. `metadata.json`**
```json
{
  "name": "Example Module",
  "version": "1.0.0",
  "author": "Your Name",
  "description": "My first SWARM module.",
  "icon_name": "module"
}
```

**2. `module.py`**
```python
from PySide6.QtWidgets import QLabel
from core.base_module import BaseModule

class ExampleModule(BaseModule):
    def create_widget(self):
        return QLabel("Привет, SWARM!")
```

Готово. Запустите SWARM (или нажмите «Модули» -> «Применить»), и ваш модуль появится в меню.

## Встроенные иконки
Вам не обязательно рисовать иконку. В `metadata.json` можно указать `icon_name` из встроенного набора:
`module`, `play`, `globe`, `settings`, `code`, `database`, `info`.

## Экосистема
На базе SWARM уже создан проект [O.N.Y.X.](https://github.com/FreshLend/O.N.Y.X.) (инструмент для сетевого анализа). Форкните SWARM и создайте свою платформу.

## Лицензия
MIT License.