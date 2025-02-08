---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/obzor-paneli-istochniki-chrome-dev-tools-chrome-for-developers/"}
---


# Обзор панели «Источники»  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Просматривайте и редактируйте файлы, создавайте фрагменты, отлаживайте JavaScript и настраивайте рабочие области на панели «Источники» Chrome DevTools.

---
![София Емельянова](https://web.dev/images/authors/sofiayem.jpg?hl=ru)

Используйте панель « **Источники** Chrome DevTools», чтобы:

-   [Просмотр файлов](https://developer.chrome.com/docs/devtools/sources?hl=ru#files) .
-   [Отредактируйте CSS и JavaScript](https://developer.chrome.com/docs/devtools/sources?hl=ru#edit) .
-   [Создавайте и сохраняйте **фрагменты** JavaScript](https://developer.chrome.com/docs/devtools/sources?hl=ru#snippets) , которые можно запускать на любой странице. **Сниппеты** похожи на букмарклеты.
-   [Отладка JavaScript](https://developer.chrome.com/docs/devtools/sources?hl=ru#debug) .
-   [Настройте рабочую область](https://developer.chrome.com/docs/devtools/sources?hl=ru#workspace) , чтобы изменения, внесенные вами в DevTools, сохранялись в коде вашей файловой системы.

## Просмотр файлов

Используйте панель **«Страница»** , чтобы просмотреть все ресурсы, загруженные страницей.

![Панель «Страница».](https://developer.chrome.com/static/docs/devtools/sources/image/the-page-pane-49968ac6336d8.png?hl=ru)

Как организована панель **«Страница»** :

-   Верхний уровень, такой как `top` на скриншоте выше, представляет собой [HTML-фрейм](https://www.w3.org/TR/html401/present/frames.html) . Вы найдете `top` на каждой странице, которую вы посещаете. `top` представляет собой основной фрейм документа.
-   Второй уровень, например, `developers.google.com` на скриншоте выше, представляет собой [источник](https://html.spec.whatwg.org/multipage/origin.html#origin) .
-   Третий уровень, четвертый уровень и т. д. представляют каталоги и ресурсы, загруженные из этого источника. Например, на скриншоте выше полный путь к ресурсу `devsite-googler-button` — `developers.google.com/_static/19aa27122b/css/devsite-googler-button` .

Щелкните файл на панели **«Страница»** , чтобы просмотреть его содержимое на панели **«Редактор»** . Вы можете просмотреть любой тип файла. Для изображений вы видите предварительный просмотр изображения.

![Просмотр файла на панели редактора.](https://developer.chrome.com/static/docs/devtools/sources/image/viewing-file-the-editor-a7b15a0d4e7d5.png?hl=ru)

## Редактировать CSS и JavaScript

Используйте панель **«Редактор»** для редактирования CSS и JavaScript. DevTools обновляет страницу для запуска нового кода.

**Редактор** также помогает вам отлаживать. Например, он подчеркивает и показывает встроенные всплывающие подсказки рядом с синтаксическими ошибками и другими проблемами, такими как неудачные операторы CSS `@import` и `url()` , а также атрибуты HTML `href` с недопустимыми URL-адресами.

![Встроенная подсказка об ошибке синтаксиса.](https://developer.chrome.com/static/docs/devtools/sources/image/an-inline-syntax-error-to-cb1195595eebb.png?hl=ru)

Если вы отредактируете `background-color` элемента, вы увидите, что изменение вступит в силу немедленно.

![Редактирование CSS на панели редактора.](https://developer.chrome.com/static/docs/devtools/sources/image/editing-css-the-editor-p-b6f00591b7d8e.gif?hl=ru)

Чтобы изменения JavaScript вступили в силу, нажмите Command + S (Mac) или Control + S (Windows, Linux). DevTools не перезапускает скрипт, поэтому вступают в силу только те изменения JavaScript, которые вы вносите внутри функций. Например, обратите внимание, что `console.log('A')` не запускается, тогда как `console.log('B')` работает.

![Редактирование JavaScript на панели редактора.](https://developer.chrome.com/static/docs/devtools/sources/image/editing-javascript-the-e-d989a1a5c3704.gif?hl=ru)

Если бы DevTools повторно запустил весь скрипт после внесения изменений, то текст `A` был бы записан в **консоль** .

DevTools стирает изменения CSS и JavaScript при перезагрузке страницы. См. [раздел «Настройка рабочей области»](https://developer.chrome.com/docs/devtools/sources?hl=ru#workspace) , чтобы узнать, как сохранить изменения в файловой системе.

## Создание, сохранение и запуск фрагментов

Сниппеты — это скрипты, которые можно запускать на любой странице. Представьте, что вы неоднократно вводите следующий код в **Консоль** , чтобы вставить библиотеку jQuery на страницу, чтобы вы могли запускать команды jQuery из **Консоли** :

```
<span>let</span><span> </span><span>script</span><span> </span><span>=</span><span> </span><span>document</span><span>.</span><span>createElement</span><span>(</span>'<span>script</span>'<span>);</span>
<span>script</span><span>.</span><span>src</span><span> </span><span>=</span><span> </span>'<span>https</span><span>:</span><span>//code.jquery.com/jquery-3.2.1.min.js';</span>
<span>script</span><span>.</span><span>crossOrigin</span><span> </span><span>=</span><span> </span>'<span>anonymous</span>'<span>;</span>
<span>script</span><span>.</span><span>integrity</span><span> </span><span>=</span><span> </span>'<span>sha256</span><span>-</span><span>hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4</span><span>=</span>'<span>;</span>
<span>document</span><span>.</span><span>head</span><span>.</span><span>appendChild</span><span>(</span><span>script</span><span>);</span>
```

Вместо этого вы можете сохранить этот код во **фрагменте** и запускать его парой нажатий кнопок в любое время, когда он вам понадобится. DevTools сохраняет **фрагмент** в вашей файловой системе. Например, изучите **фрагмент** , который вставляет библиотеку jQuery на страницу.

![Фрагмент, который вставляет библиотеку jQuery на страницу.](https://developer.chrome.com/static/docs/devtools/sources/image/a-snippet-inserts-jquer-699d1e95396d5.png?hl=ru)

Чтобы запустить **фрагмент** :

-   Откройте файл на панели **«Фрагменты»** и нажмите « **Выполнить»** . ![Кнопка «Выполнить».](https://developer.chrome.com/static/docs/devtools/sources/image/the-run-button-bca877bd0432d.svg?hl=ru) на панели действий внизу.
-   Откройте [**командное меню**](https://developer.chrome.com/docs/devtools/command-menu?hl=ru) , удалите символ `>` , введите `!` , введите имя **фрагмента** и нажмите Enter.

Дополнительную информацию см. [в разделе «Запуск фрагментов кода с любой страницы»](https://developer.chrome.com/docs/devtools/javascript/snippets?hl=ru) .

## Отладка JavaScript

Вместо того, чтобы использовать `console.log()` для определения того, где ваш JavaScript работает не так, рассмотрите возможность использования инструментов отладки Chrome DevTools. Общая идея состоит в том, чтобы установить точку останова, которая является намеренным местом остановки в вашем коде, а затем пошагово выполнять ваш код, по одной строке за раз.

![Пауза в точке останова.](https://developer.chrome.com/static/docs/devtools/sources/image/pausing-a-breakpoint-b05705f84cde.png?hl=ru)

По мере выполнения кода вы можете просматривать и изменять значения всех определенных в данный момент свойств и переменных, запускать JavaScript в **консоли** и многое другое.

См. [раздел «Начало работы с отладкой JavaScript»](https://developer.chrome.com/docs/devtools/javascript?hl=ru) , чтобы изучить основы отладки в DevTools.

### Сосредоточьтесь только на своем коде

Chrome DevTools позволяет вам сосредоточиться только на написанном вами коде, отфильтровывая шум, создаваемый платформами и инструментами сборки, которые вы используете при создании веб-приложений.

Чтобы предоставить вам современные возможности веб-отладки, DevTools делает следующее:

-   **Разделяет созданный и развернутый код** . Чтобы помочь вам быстрее найти код, [панель **«Источники»** отделяет созданный вами код](https://developer.chrome.com/docs/devtools/javascript/reference?hl=ru#group-authored-and-deployed) от связанного и минимизированного кода.
-   **Игнорирует известный сторонний код** :
    -   [Панель **«Источники»** скрывает такие источники](https://developer.chrome.com/docs/devtools/javascript/reference?hl=ru#hide-ignore-listed) из дерева файлов на панели **«Страница»** .
    -   [**Консоль** скрывает такие кадры из трассировки стека](https://developer.chrome.com/docs/devtools/console/reference?hl=ru#show-third-party) .
    -   [Меню **«Открыть файл»** скрывает такие файлы из результатов поиска](https://developer.chrome.com/docs/devtools/command-menu?hl=ru#open-ignore-listed-files) .

Кроме того, если это поддерживается платформами, [**стек вызовов** в отладчике](https://developer.chrome.com/docs/devtools/javascript/reference?hl=ru#async-frames) и [трассировки стека в **консоли**](https://developer.chrome.com/docs/devtools/console/reference?hl=ru#async-stack-traces) отображают полную историю асинхронных операций.

Чтобы узнать больше, см.:

-   [Современная веб-отладка в Chrome DevTools](https://developer.chrome.com/blog/devtools-modern-web-debugging?hl=ru)
-   [Практический пример: улучшение угловой отладки с помощью DevTools](https://developer.chrome.com/blog/devtools-better-angular-debugging?hl=ru)

## Настройте рабочее пространство

По умолчанию, когда вы редактируете файл на панели **«Источники»** , эти изменения теряются при перезагрузке страницы. **Рабочие области** позволяют сохранять изменения, внесенные в DevTools, в файловую систему. По сути, это позволяет вам использовать DevTools в качестве редактора кода.

Чтобы начать, ознакомьтесь с [разделом «Редактирование файлов с помощью рабочих пространств»](https://developer.chrome.com/docs/devtools/workspaces?hl=ru) .
