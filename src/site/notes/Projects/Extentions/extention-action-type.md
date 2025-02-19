---
{"dg-publish":true,"permalink":"/projects/extentions/extention-action-type/","dgPassFrontmatter":true}
---



## Различные типы действий расширений: `action`, `contextMenus`, `commands`

В Модуле 2 мы использовали `action` для создания иконки в панели инструментов и всплывающего окна. Однако, расширения могут взаимодействовать с пользователем и другими способами. Рассмотрим основные типы "действий":

*   **`action` (ранее `browser_action`):**
    *   **Описание:**  Добавляет иконку в панель инструментов браузера. При нажатии на иконку обычно открывается всплывающее окно (`default_popup`).
    *   **Использование:**  Для основных функций расширения, которые пользователь может вызвать в любой момент, независимо от текущей веб-страницы.
    *   **Пример:** Расширения-блокноты, менеджеры паролей, блокировщики рекламы, инструменты для продуктивности.
    *   **Пример кода в `manifest.json`:** (уже рассмотрено в теме 1)

*   **`contextMenus`:**
    *   **Описание:**  Добавляет пункты в контекстное меню (меню правой кнопки мыши), которое появляется при клике правой кнопкой мыши на веб-странице.
    *   **Использование:**  Для действий, которые зависят от контекста веб-страницы или выделенного текста.
    *   **Пример:** Расширение-переводчик выделенного текста (как в практическом задании Модуля 6), расширение для сохранения изображений, расширение для поиска выделенного текста в Google.
    *   **Пример кода в `manifest.json` и `background.js`:**

        **`manifest.json`:**

        ```json
        {
          "manifest_version": 3,
          "name": "Контекстное меню",
          "version": "1.0",
          "description": "Расширение, добавляющее пункт в контекстное меню.",
          "background": {
            "service_worker": "background.js"
          },
          "permissions": ["contextMenus"]
        }
        ```

        **`background.js`:**

        ```javascript
        chrome.contextMenus.create({
          id: "myContextMenu",
          title: "Действие из контекстного меню",
          contexts: ["page", "selection"] // Контексты: страница и выделенный текст
        });

        chrome.contextMenus.onClicked.addListener(function(info, tab) {
          if (info.menuItemId === "myContextMenu") {
            alert("Вы выбрали пункт контекстного меню!");
            console.log("Информация о клике:", info);
            console.log("Информация о вкладке:", tab);
          }
        });
        ```

    *   **Ссылка:** [chrome.contextMenus API](https://developer.chrome.com/docs/extensions/reference/contextMenus/)

*   **`commands`:**
    *   **Описание:**  Позволяет назначать горячие клавиши (сочетания клавиш) для выполнения определенных действий расширения.
    *   **Использование:**  Для быстрых действий, которые пользователь может вызвать с клавиатуры, не отрываясь от работы.
    *   **Пример:** Расширение для быстрого создания новой вкладки, расширение для переключения тем, расширение для копирования текущего URL.
    *   **Пример кода в `manifest.json` и `background.js`:**

        **`manifest.json`:**

        ```json
        {
          "manifest_version": 3,
          "name": "Горячие клавиши",
          "version": "1.0",
          "description": "Расширение с горячими клавишами.",
          "background": {
            "service_worker": "background.js"
          },
          "commands": {
            "toggle-feature": {
              "suggested_key": {
                "default": "Ctrl+Shift+X", // Горячая клавиша по умолчанию
                "mac": "Command+Shift+X" // Для macOS
              },
              "description": "Включить/выключить функцию расширения"
            }
          },
          "permissions": ["commands"]
        }
        ```

        **`background.js`:**

        ```javascript
        chrome.commands.onCommand.addListener(function(command) {
          if (command === "toggle-feature") {
            alert("Горячая клавиша 'Включить/выключить функцию расширения' нажата!");
            console.log("Команда:", command);
          }
        });
        ```

    *   **Ссылка:** [chrome.commands API](https://developer.chrome.com/docs/extensions/reference/commands/)

**Практическое задание:**

1.  Создайте расширение, которое добавляет пункт "Скопировать URL страницы" в контекстное меню.
2.  При выборе этого пункта, расширение должно копировать URL текущей страницы в буфер обмена.
    *   **Подсказка:** Используйте `chrome.contextMenus` API и [Clipboard API](https://developer.mozilla.org/en-US/docs/Web/API/Clipboard_API) (может потребоваться разрешение `"clipboardWrite"` в `manifest.json`).
3.  Создайте расширение, которое при нажатии горячей клавиши `Ctrl+Shift+Y` (или `Cmd+Shift+Y` на macOS) открывает новую вкладку с сайтом Google.
    *   **Подсказка:** Используйте `chrome.commands` API и `chrome.tabs.create` API.
