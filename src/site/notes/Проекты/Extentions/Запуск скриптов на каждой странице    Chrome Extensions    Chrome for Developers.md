---
{"dg-publish":true,"created":"2025-01-31T16:46:27 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru","author":null,"permalink":"/proekty/extentions/zapusk-skriptov-na-kazhdoj-stranicze-chrome-extensions-chrome-for-developers/","dgPassFrontmatter":true}
---


# Запуск скриптов на каждой странице  |  Chrome Extensions  |  Chrome for Developers

> ## Excerpt
> Узнайте, как автоматически добавлять новые элементы на существующие веб-страницы.

---
Создайте свое первое расширение, которое вставляет новый элемент на страницу.

## Обзор

В этом руководстве создается расширение, которое добавляет ожидаемое время чтения к любому расширению Chrome и странице документации Интернет-магазина Chrome.

![Расширение времени чтения на странице приветствия расширения.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/scripts-on-every-tab/image/reading-extension-the-e-0070620f12665.png?hl=ru)

Расширение времени чтения на странице приветствия расширения.

В этом руководстве мы объясним следующие понятия:

-   Манифест расширения.
-   Какие размеры значков использует расширение.
-   Как внедрить код на страницы с помощью [контент-скриптов](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru) .
-   Как использовать шаблоны совпадений.
-   Разрешения на расширение.

## Прежде чем начать

В этом руководстве предполагается, что у вас есть базовый опыт веб-разработки. Мы рекомендуем ознакомиться с руководством [Hello world](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru) , чтобы познакомиться с рабочим процессом разработки расширений.

## Создайте расширение

Для начала создайте новый каталог с именем `reading-time` для хранения файлов расширения. При желании вы можете скачать полный исходный код с [GitHub](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.reading-time) .

### Шаг 1. Добавьте информацию о расширении.

Файл манифеста JSON — единственный обязательный файл. Он содержит важную информацию о расширении. Создайте файл `manifest.json` в _корне_ проекта и добавьте следующий код:

```
<span>{</span><span><br>&nbsp; </span><span>"manifest_version"</span><span>:</span><span> </span><span>3</span><span>,</span><span><br>&nbsp; </span><span>"name"</span><span>:</span><span> </span><span>"Reading time"</span><span>,</span><span><br>&nbsp; </span><span>"version"</span><span>:</span><span> </span><span>"1.0"</span><span>,</span><span><br>&nbsp; </span><span>"description"</span><span>:</span><span> </span><span>"Add the reading time to Chrome Extension documentation articles"</span><span><br></span><span>}</span><span><br></span>
```

Эти ключи содержат основные метаданные расширения. Они контролируют, как расширение отображается на странице расширений и, после публикации, в Интернет-магазине Chrome. Чтобы углубиться, ознакомьтесь с ключами [`"name"`](https://developer.chrome.com/docs/extensions/reference/manifest/name?hl=ru) , [`"version"`](https://developer.chrome.com/docs/extensions/reference/manifest/version?hl=ru) и [`"description"`](https://developer.chrome.com/docs/extensions/reference/manifest/description?hl=ru) на странице обзора [манифеста](https://developer.chrome.com/docs/extensions/reference/manifest?hl=ru) .

💡 **Другие факты о манифесте расширения**

-   Он должен находиться в **корне** проекта.
-   Единственные необходимые ключи — это `"manifest_version"` , `"name"` и `"version"` .
-   Он поддерживает комментарии ( `//` ) во время разработки, но их необходимо удалить перед загрузкой кода в Интернет-магазин Chrome.

### Шаг 2. Предоставьте значки

Итак, зачем нужны иконки? Хотя [значки](https://developer.chrome.com/docs/extensions/reference/manifest/icons?hl=ru) не являются обязательными во время разработки, они необходимы, если вы планируете распространять свое расширение в Интернет-магазине Chrome. Они также появляются в других местах, например на странице управления расширениями.

Создайте папку `images` и поместите туда значки. Скачать иконки можно на [GitHub](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.reading-time/images) . Затем добавьте выделенный код в свой манифест для объявления значков:

```
<span>{</span><span><br>&nbsp; </span><span>"icons"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"16"</span><span>:</span><span> </span><span>"images/icon-16.png"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"32"</span><span>:</span><span> </span><span>"images/icon-32.png"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"48"</span><span>:</span><span> </span><span>"images/icon-48.png"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"128"</span><span>:</span><span> </span><span>"images/icon-128.png"</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

Мы рекомендуем использовать файлы PNG, но допускаются и другие форматы файлов, кроме файлов SVG.

💡 **Где отображаются значки разного размера?**

| Размер значка | Использование значков |
| --- | --- |
| 16x16 | Фавиконка на страницах расширения и в контекстном меню. |
| 32x32 | Компьютерам под управлением Windows часто требуется этот размер. |
| 48x48 | Отображается на странице «Расширения». |
| 128x128 | Отображается при установке и в Интернет-магазине Chrome. |

### Шаг 3. Объявите сценарий содержимого.

Расширения могут запускать сценарии, которые читают и изменяют содержимое страницы. Это так называемые _сценарии контента_ . Они живут в [изолированном мире](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru#isolated_world) , а это означает, что они могут вносить изменения в свою среду JavaScript, не вступая в конфликт со своей хост-страницей или сценариями содержимого других расширений.

Добавьте следующий код в `manifest.json` , чтобы зарегистрировать скрипт контента с именем `content.js` .

```
<span>{</span><span><br>&nbsp; </span><span>"content_scripts"</span><span>:</span><span> </span><span>[</span><span><br>&nbsp; &nbsp; </span><span>{</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"js"</span><span>:</span><span> </span><span>[</span><span>"scripts/content.js"</span><span>],</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"matches"</span><span>:</span><span> </span><span>[</span><span><br>&nbsp; &nbsp; &nbsp; &nbsp; </span><span>"https://developer.chrome.com/docs/extensions/*"</span><span>,</span><span><br>&nbsp; &nbsp; &nbsp; &nbsp; </span><span>"https://developer.chrome.com/docs/webstore/*"</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>]</span><span><br>&nbsp; &nbsp; </span><span>}</span><span><br>&nbsp; </span><span>]</span><span><br></span><span>}</span><span><br></span>
```

Поле `"matches"` может содержать один или несколько [шаблонов совпадений](https://developer.chrome.com/docs/extensions/develop/concepts/match-patterns?hl=ru) . Они позволяют браузеру определять, на какие сайты следует вставлять сценарии контента. Шаблоны совпадений состоят из трех частей: `<scheme>://<host><path>` . Они могут содержать символы « `*` ».

💡 **Отображает ли это расширение предупреждение о разрешении?**

Когда пользователь устанавливает расширение, браузер сообщает ему, что может делать расширение. Скрипты контента запрашивают разрешение на запуск на сайтах, соответствующих критериям шаблона соответствия.

В этом примере пользователь увидит следующее предупреждение о разрешении:

![Предупреждение о разрешении, которое пользователь увидит при установке расширения «Время чтения».](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/scripts-on-every-tab/image/permission-warning-user-af0cb023a0128.png?hl=ru)

Предупреждение о разрешении времени чтения.

Более подробно о разрешениях расширений см. [в разделе «Объявление разрешений и предупреждение пользователей»](https://developer.chrome.com/docs/extensions/develop/concepts/permission-warnings?hl=ru) .

### Шаг 4. Рассчитайте и укажите время чтения.

Сценарии содержимого могут использовать стандартную [объектную модель документа](https://developer.mozilla.org/docs/Web/API/Document_Object_Model) (DOM) для чтения и изменения содержимого страницы. Расширение сначала проверит, содержит ли страница элемент `<article>` . Затем он подсчитает все слова в этом элементе и создаст абзац, отображающий общее время чтения.

Создайте файл `content.js` внутри папки `scripts` и добавьте следующий код:

```
<span>const</span><span> article </span><span>=</span><span> document</span><span>.</span><span>querySelector</span><span>(</span><span>"article"</span><span>);</span><span><br><br></span><span>// `document.querySelector` may return null if the selector doesn't match anything.</span><span><br></span><span>if</span><span> </span><span>(</span><span>article</span><span>)</span><span> </span><span>{</span><span><br>&nbsp; </span><span>const</span><span> text </span><span>=</span><span> article</span><span>.</span><span>textContent</span><span>;</span><span><br>&nbsp; </span><span>const</span><span> wordMatchRegExp </span><span>=</span><span> </span><span>/[^\s]+/</span><span>g</span><span>;</span><span> </span><span>// Regular expression</span><span><br>&nbsp; </span><span>const</span><span> words </span><span>=</span><span> text</span><span>.</span><span>matchAll</span><span>(</span><span>wordMatchRegExp</span><span>);</span><span><br>&nbsp; </span><span>// matchAll returns an iterator, convert to array to get word count</span><span><br>&nbsp; </span><span>const</span><span> wordCount </span><span>=</span><span> </span><span>[...</span><span>words</span><span>].</span><span>length</span><span>;</span><span><br>&nbsp; </span><span>const</span><span> readingTime </span><span>=</span><span> </span><span>Math</span><span>.</span><span>round</span><span>(</span><span>wordCount </span><span>/</span><span> </span><span>200</span><span>);</span><span><br>&nbsp; </span><span>const</span><span> badge </span><span>=</span><span> document</span><span>.</span><span>createElement</span><span>(</span><span>"p"</span><span>);</span><span><br>&nbsp; </span><span>// Use the same styling as the publish information in an article's header</span><span><br>&nbsp; badge</span><span>.</span><span>classList</span><span>.</span><span>add</span><span>(</span><span>"color-secondary-text"</span><span>,</span><span> </span><span>"type--caption"</span><span>);</span><span><br>&nbsp; badge</span><span>.</span><span>textContent </span><span>=</span><span> </span><span>`⏱️</span><span> $</span><span>{</span><span>readingTime</span><span>}</span><span> min read</span><span>`;</span><span><br><br>&nbsp; </span><span>// Support for API reference docs</span><span><br>&nbsp; </span><span>const</span><span> heading </span><span>=</span><span> article</span><span>.</span><span>querySelector</span><span>(</span><span>"h1"</span><span>);</span><span><br>&nbsp; </span><span>// Support for article docs with date</span><span><br>&nbsp; </span><span>const</span><span> date </span><span>=</span><span> article</span><span>.</span><span>querySelector</span><span>(</span><span>"time"</span><span>)?.</span><span>parentNode</span><span>;</span><span><br><br>&nbsp; </span><span>(</span><span>date </span><span>??</span><span> heading</span><span>).</span><span>insertAdjacentElement</span><span>(</span><span>"afterend"</span><span>,</span><span> badge</span><span>);</span><span><br></span><span>}</span><span><br></span>
```

💡 **В этом коде использован интересный JavaScript**

-   [Регулярные выражения](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#writing_a_regular_expression_pattern) используются для подсчета только слов внутри элемента `<article>` .
-   [`insertAdjacentElement()`](https://developer.mozilla.org/docs/Web/API/Element/insertAdjacentElement) используется для вставки узла времени чтения после элемента.
-   Свойство [classList](https://developer.mozilla.org/docs/Web/API/Element/classList) используется для добавления имен классов CSS к атрибуту класса элемента.
-   [Необязательная цепочка,](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Optional_chaining) используемая для доступа к свойству объекта, которое может быть неопределенным или иметь значение NULL.
-   [Нулевое объединение](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator) возвращает `<heading>` , если `<date>` имеет значение NULL или не определено.

## Проверьте, что это работает

Убедитесь, что файловая структура вашего проекта выглядит следующим образом:

![Содержимое папки времени чтения: манифест.json, content.js в папке скриптов и папка изображений.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/scripts-on-every-tab/image/the-contents-the-reading-5777198253dc5.png?hl=ru)

### Загрузите расширение локально

Чтобы загрузить распакованное расширение в режиме разработчика, выполните действия, описанные в [разделе «Основы разработки»](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru#load-unpacked) .

### Откройте расширение или документацию Интернет-магазина Chrome.

Вот несколько страниц, которые вы можете открыть, чтобы увидеть, сколько времени займет чтение каждой статьи.

-   [Публикация в Интернет-магазине Chrome](https://developer.chrome.com/docs/webstore/publish?hl=ru)
-   [Понимание сценариев контента](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru)

Это должно выглядеть так:

![Время чтения на странице приветствия](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/scripts-on-every-tab/image/reading-running-the-wel-1d750346edcea.png?hl=ru)

Страница приветствия расширения с расширением «Время чтения»

## 🎯 Возможные улучшения

Основываясь на том, что вы узнали сегодня, попробуйте реализовать любое из следующих действий:

-   Добавьте еще один **шаблон соответствия** в файл манифеста.json для поддержки других страниц [разработчиков Chrome](https://developer.chrome.com/docs/?hl=ru) , например [Chrome DevTools](https://developer.chrome.com/docs/devtools/?hl=ru) или [Workbox](https://developer.chrome.com/docs/workbox?hl=ru) .
-   Добавьте новый скрипт контента, который рассчитывает время чтения, в любой из ваших любимых блогов или сайтов документации.

## Продолжайте строить

Поздравляем с завершением этого урока 🎉. Продолжайте развивать свои навыки, выполнив другие уроки из этой серии:

| Расширение | Что вы узнаете |
| --- | --- |
| [Режим фокусировки](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-activetab?hl=ru) | Чтобы запустить код на текущей странице после нажатия действия расширения. |
| [Менеджер вкладок](https://developer.chrome.com/docs/extensions/get-started/tutorial/popup-tabs-manager?hl=ru) | Создать всплывающее окно, управляющее вкладками браузера. |

## Продолжить изучение

Мы надеемся, что вам понравилось создавать это расширение Chrome, и мы рады продолжить обучение разработке Chrome. Мы рекомендуем следующий путь обучения:

-   [Руководство разработчика](https://developer.chrome.com/docs/extensions/develop?hl=ru) содержит десятки дополнительных ссылок на документацию, относящуюся к созданию расширенных расширений.
-   Расширения имеют доступ к мощным API, помимо тех, что доступны в открытой сети. [В документации по API Chrome](https://developer.chrome.com/docs/extensions/reference/api?hl=ru) описан каждый API.
