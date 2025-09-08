---
{"dg-publish":true,"created":"2025-01-31T17:56:30 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/devtools/console?hl=ru","author":"Kayce Basques","permalink":"/proekty/extentions/dev-tools/console-overview/","dgPassFrontmatter":true}
---


# Обзор консоли  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Консоль Chrome DevTools используется в основном для регистрации сообщений и запуска JavaScript

---

![Панель консоли рядом с домашней страницей DevTools.](https://developer.chrome.com/static/docs/devtools/console/image/the-console-panel-next-t-9c932aff8f795.png?hl=ru)

**Рисунок 2** . Панель консоли рядом с домашней страницей DevTools.

![Использование консоли для изменения заголовка страницы.](https://developer.chrome.com/static/docs/devtools/console/image/using-console-change-p-21db569361b85.png?hl=ru)

**Рисунок 3** . Использование консоли для изменения заголовка страницы.

Изменение страницы из консоли возможно, поскольку консоль имеет полный доступ к [`window`](https://developer.mozilla.org/docs/Web/API/Window) страницы. DevTools имеет несколько удобных функций, упрощающих проверку страницы. Например, предположим, что ваш JavaScript содержит функцию с `hideModal` . Запуск `debug(hideModal)` приостанавливает ваш код на первой строке `hideModal` при следующем вызове. Полный список служебных функций см. в [разделе «Справочник по API консольных утилит»](https://developer.chrome.com/docs/devtools/console/utilities?hl=ru#debug) .

Когда вы запускаете JavaScript, вам не нужно взаимодействовать со страницей. Вы можете использовать консоль, чтобы опробовать новый код, не связанный со страницей. Например, предположим, что вы только что узнали о встроенном методе JavaScript Array [`map()`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/map) и хотите поэкспериментировать с ним. Консоль — хорошее место, чтобы опробовать эту функцию.

См. [раздел «Начало работы с запуском JavaScript»](https://developer.chrome.com/docs/devtools/console/javascript?hl=ru) , чтобы получить практический опыт запуска JavaScript в консоли. 