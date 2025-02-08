---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/obzor-konsoli-chrome-dev-tools-chrome-for-developers/"}
---


# Обзор консоли  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Консоль Chrome DevTools используется в основном для регистрации сообщений и запуска JavaScript.

---
На этой странице объясняется, как консоль Chrome DevTools упрощает разработку веб-страниц. Консоль имеет два основных применения: [просмотр зарегистрированных сообщений](https://developer.chrome.com/docs/devtools/console?hl=ru#view) и [запуск JavaScript](https://developer.chrome.com/docs/devtools/console?hl=ru#javascript) .

<iframe frameborder="0" allowfullscreen="" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" title="YouTube video player" width="640" height="360" src="https://www.youtube.com/embed/76U0gtuV9AY?origin=https%3A%2F%2Fdeveloper.chrome.com&amp;autoplay&amp;controls&amp;embed_domain&amp;enablejsapi=1&amp;end&amp;hl&amp;showinfo&amp;start&amp;video-id=76U0gtuV9AY&amp;widgetid=1" id="widget2" data-gtm-yt-inspected-100007133_93="true" data-gtm-yt-inspected-183356566_95="true"></iframe>

## Просмотр зарегистрированных сообщений

Веб-разработчики часто регистрируют сообщения в консоли, чтобы убедиться, что их JavaScript работает должным образом. Чтобы зарегистрировать сообщение, вы вставляете в свой JavaScript выражение типа `console.log('Hello, Console!')` . Когда браузер выполняет ваш JavaScript и видит подобное выражение, он знает, что он должен записать сообщение в консоль. Например, предположим, что вы пишете HTML и JavaScript для страницы:

```
&lt;!doctype html&gt;
&lt;html&gt;
&nbsp; &lt;head&gt;
&nbsp; &nbsp; &lt;title&gt;Console Demo&lt;/title&gt;
&nbsp; &lt;/head&gt;
&nbsp; &lt;body&gt;
&nbsp; &nbsp; &lt;h1&gt;Hello, World!&lt;/h1&gt;
&nbsp; &nbsp; &lt;script&gt;
&nbsp; &nbsp; &nbsp; console.log('Loading!');
&nbsp; &nbsp; &nbsp; const h1 = document.querySelector('h1');
&nbsp; &nbsp; &nbsp; console.log(h1.textContent);
&nbsp; &nbsp; &nbsp; console.assert(document.querySelector('h2'), 'h2 not found!');
&nbsp; &nbsp; &nbsp; const artists = [
&nbsp; &nbsp; &nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; first: 'René',
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; last: 'Magritte'
&nbsp; &nbsp; &nbsp; &nbsp; },
&nbsp; &nbsp; &nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; first: 'Chaim',
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; last: 'Soutine'
&nbsp; &nbsp; &nbsp; &nbsp; },
&nbsp; &nbsp; &nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; first: 'Henri',
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; last: 'Matisse'
&nbsp; &nbsp; &nbsp; &nbsp; }
&nbsp; &nbsp; &nbsp; ];
&nbsp; &nbsp; &nbsp; console.table(artists);
&nbsp; &nbsp; &nbsp; setTimeout(() =&gt; {
&nbsp; &nbsp; &nbsp; &nbsp; h1.textContent = 'Hello, Console!';
&nbsp; &nbsp; &nbsp; &nbsp; console.log(h1.textContent);
&nbsp; &nbsp; &nbsp; }, 3000);
&nbsp; &nbsp; &lt;/script&gt;
&nbsp; &lt;/body&gt;
&lt;/html&gt;
```

**На рис. 1** показано, как выглядит консоль после загрузки страницы и ожидания в течение 3 секунд. Попытайтесь выяснить, какие строки кода заставили браузер регистрировать сообщения.

![Панель Консоли.](https://developer.chrome.com/static/docs/devtools/console/image/the-console-panel-dc4828392d194.png?hl=ru)

**Рисунок 1** . Панель Консоли.

Веб-разработчики регистрируют сообщения по двум основным причинам:

-   Убедиться, что код выполняется в правильном порядке.
-   Проверка значений переменных в определенный момент времени.

См. [раздел «Начало работы с ведением журнала сообщений»](https://developer.chrome.com/docs/devtools/console/log?hl=ru) , чтобы получить практический опыт ведения журнала. См. [Справочник по консольному API](https://developer.chrome.com/docs/devtools/console/api?hl=ru) , чтобы просмотреть полный список `console` методов. Основное различие между методами заключается в том, как они отображают регистрируемые данные.

## Запуск JavaScript

Консоль также является [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) . Вы можете запустить JavaScript в консоли, чтобы взаимодействовать с проверяемой страницей. Например, **на рис. 2** показана консоль рядом с домашней страницей DevTools, а **на рис. 3** показана та же страница после использования консоли для изменения заголовка страницы.

![Панель консоли рядом с домашней страницей DevTools.](https://developer.chrome.com/static/docs/devtools/console/image/the-console-panel-next-t-9c932aff8f795.png?hl=ru)

**Рисунок 2** . Панель консоли рядом с домашней страницей DevTools.

![Использование консоли для изменения заголовка страницы.](https://developer.chrome.com/static/docs/devtools/console/image/using-console-change-p-21db569361b85.png?hl=ru)

**Рисунок 3** . Использование консоли для изменения заголовка страницы.

Изменение страницы из консоли возможно, поскольку консоль имеет полный доступ к [`window`](https://developer.mozilla.org/docs/Web/API/Window) страницы. DevTools имеет несколько удобных функций, упрощающих проверку страницы. Например, предположим, что ваш JavaScript содержит функцию с `hideModal` . Запуск `debug(hideModal)` приостанавливает ваш код на первой строке `hideModal` при следующем вызове. Полный список служебных функций см. в [разделе «Справочник по API консольных утилит»](https://developer.chrome.com/docs/devtools/console/utilities?hl=ru#debug) .

Когда вы запускаете JavaScript, вам не нужно взаимодействовать со страницей. Вы можете использовать консоль, чтобы опробовать новый код, не связанный со страницей. Например, предположим, что вы только что узнали о встроенном методе JavaScript Array [`map()`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array/map) и хотите поэкспериментировать с ним. Консоль — хорошее место, чтобы опробовать эту функцию.

См. [раздел «Начало работы с запуском JavaScript»](https://developer.chrome.com/docs/devtools/console/javascript?hl=ru) , чтобы получить практический опыт запуска JavaScript в консоли.
