---
{"dg-publish":true,"permalink":"/projects/extentions/vis-ui-builders-ext/","dgPassFrontmatter":true}
---


## Визуальные No-Code UI Билдеры с экспортом для расширений: Создание интерфейсов Popup и Options Pages без кода, готовых к интеграции

Создание пользовательского интерфейса (UI) для всплывающих окон (`popup.html`) и страниц настроек (`options.html`) расширений может быть упрощено с помощью визуальных no-code UI билдеров, которые позволяют создавать интерфейсы drag-and-drop и экспортировать готовый HTML, CSS и JavaScript код, который можно напрямую интегрировать в расширение.

**Актуальные No-Code UI Билдеры с возможностью экспорта HTML/CSS/JS для расширений:**

*   **[TeleportHQ](https://teleporthq.io/)**:
    *   **Описание:**  Мощная no-code платформа для создания веб-приложений и UI компонентов. Предлагает drag-and-drop интерфейс, компоненты UI, стилизацию, и возможность экспорта чистого, семантического HTML, CSS и React/Vue/Angular код. Бесплатный тарифный план с ограничениями.
    *   **Преимущества для расширений:**  Создание сложных и красивых UI для всплывающих окон и страниц настроек визуально. Экспорт чистого кода, который легко интегрировать в расширение. Поддержка React, Vue, Angular (если вы планируете использовать фреймворки в расширении в будущем).
    *   **Ограничения:**  Бесплатный тариф ограничен. Может потребоваться время на освоение всех возможностей платформы.
    *   **Ссылка:** [TeleportHQ](https://teleporthq.io/)

*   **[Plasmic](https://www.plasmic.app/)**:
    *   **Описание:**  Визуальный билдер страниц и компонентов для React, Vue, Angular и HTML.  Drag-and-drop интерфейс, компоненты, стилизация, интеграция с CMS и API. Бесплатный тарифный план для личного использования.
    *   **Преимущества для расширений:**  Создание интерактивных и динамических UI для расширений. Экспорт HTML, CSS и React/Vue/Angular код.  Мощные возможности для создания сложных интерфейсов.
    *   **Ограничения:**  Ориентирован на React, Vue, Angular (хотя есть экспорт и в HTML). Бесплатный тариф ограничен.
    *   **Ссылка:** [Plasmic](https://www.plasmic.app/)

*   **[Builder.io](https://www.builder.io/)**:
    *   **Описание:**  Визуальный редактор страниц и headless CMS. Drag-and-drop, компоненты, стилизация, A/B тестирование, интеграция с разными платформами. Бесплатный тарифный план для личного использования.
    *   **Преимущества для расширений:**  Быстрое создание лендингов и страниц настроек для расширений. Экспорт HTML, CSS и React код.  Хорошо подходит для создания маркетинговых страниц для расширений.
    *   **Ограничения:**  Больше ориентирован на создание веб-страниц, чем UI компонентов для расширений. Бесплатный тариф ограничен.
    *   **Ссылка:** [Builder.io](https://www.builder.io/)

*   **[Webflow](https://webflow.com/)**:
    *   **Описание:**  Мощная no-code платформа для создания веб-сайтов. Drag-and-drop, CMS, анимации, хостинг. Бесплатный тарифный план для ознакомления.
    *   **Преимущества для расширений:**  Создание профессионально выглядящих веб-страниц и UI компонентов. Экспорт чистого HTML, CSS и JavaScript кода.  Широкие возможности стилизации и анимации.
    *   **Ограничения:**  Больше ориентирован на создание полноценных веб-сайтов, чем UI для расширений. Экспорт кода доступен только на платных тарифах (но можно использовать бесплатный тариф для дизайна и скопировать код элементов через DevTools, хотя это менее удобно).
    *   **Ссылка:** [Webflow](https://webflow.com/)

**Как использовать No-Code UI билдер для создания `popup.html`:**

1.  Выберите UI билдер:  Выберите один из предложенных билдеров (например, TeleportHQ или Plasmic). Зарегистрируйтесь (обычно есть бесплатные тарифы).
2.  Создайте проект:  Создайте новый проект в выбранном билдере.
3.  Визуально создайте UI:  Используйте drag-and-drop интерфейс, добавляйте компоненты (кнопки, текст, изображения, поля ввода и т.д.), стилизуйте их, настраивайте расположение.
4.  Экспортируйте HTML/CSS/JS код:  Найдите опцию экспорта кода (обычно "Export code", "Download code" или аналогичную). Выберите опцию экспорта в HTML/CSS/JS (или HTML, CSS, JS по отдельности). Скачайте ZIP-архив или скопируйте код.
5.  Интегрируйте код в расширение:
    *   Создайте файл `popup.html` (или `options.html`) в папке вашего расширения.
    *   Вставьте скопированный HTML код в `popup.html`.
    *   Если билдер экспортировал CSS и JavaScript файлы, скопируйте их в папку расширения и подключите к `popup.html` (через `<link>` для CSS и `<script>` для JS).  Или, если CSS стили встроены в HTML (в `<style>` тегах), оставьте их как есть.

**Практическое задание:**

6.  Выберите TeleportHQ или Plasmic. Зарегистрируйтесь и ознакомьтесь с интерфейсом.
7.  Визуально создайте всплывающее окно для расширения "Синий Фон" (из предыдущего задания). Добавьте кнопку "Сделать синим", стилизуйте окно.
8.  Экспортируйте HTML и CSS код из UI билдера.
9.  Создайте `popup.html` и `popup.css` в папке расширения "Синий Фон". Вставьте экспортированный HTML в `popup.html`, CSS в `popup.css`. Подключите `popup.css` к `popup.html`.
10.  Убедитесь, что `popup.js` (код смены фона) по-прежнему подключен к `popup.html` и работает.
11.  Загрузите и протестируйте обновленное расширение с визуально созданным всплывающим окном.
