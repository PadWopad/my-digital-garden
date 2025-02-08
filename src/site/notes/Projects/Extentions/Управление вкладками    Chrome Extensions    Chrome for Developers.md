---
{"dg-publish":true,"created":"2025-01-31T16:46:42 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/extensions/get-started/tutorial/popup-tabs-manager?hl=ru","author":null,"permalink":"/projects/extentions/upravlenie-vkladkami-chrome-extensions-chrome-for-developers/","dgPassFrontmatter":true}
---


# Управление вкладками  |  Chrome Extensions  |  Chrome for Developers

> ## Excerpt
> Узнайте, как программно организовывать вкладки с помощью групп вкладок.

---
Создайте свой первый менеджер вкладок.

## Обзор

В этом руководстве создается менеджер вкладок для организации вкладок расширения Chrome и документации Интернет-магазина Chrome.

![Всплывающее окно расширения «Диспетчер вкладок»](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/popup-tabs-manager/image/tabs-manager-extension-po-725ac725aaa4d.png?hl=ru)

Расширение «Диспетчер вкладок»

В этом руководстве мы объясним, как сделать следующее:

-   Создайте всплывающее окно расширения с помощью [Action](https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru) API.
-   Запрос определенных вкладок с помощью API [вкладок](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=ru) .
-   Сохраняйте конфиденциальность пользователей за счет узких разрешений хоста.
-   Измените фокус вкладки.
-   Переместите вкладки в одно окно и сгруппируйте их.
-   Переименуйте группы вкладок с помощью API [TabGroups](https://developer.chrome.com/docs/extensions/reference/api/tabGroups?hl=ru) .

## Прежде чем начать

В этом руководстве предполагается, что у вас есть базовый опыт веб-разработки. Мы рекомендуем ознакомиться [с Hello World](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru) , чтобы познакомиться с рабочим процессом разработки расширений.

## Создайте расширение

Для начала создайте новый каталог под названием `tabs-manager` для хранения файлов расширения. При желании вы можете скачать полный исходный код на [GitHub](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.tabs-manager) .

### Шаг 1. Добавьте данные и значки расширения.

Создайте файл с именем `manifest.json` и добавьте следующий код:

```
<span>{</span>
<span>  </span>"<span>ma</span><span>n</span><span>i</span><span>fest</span><span>_versio</span><span>n</span>"<span>:</span><span> </span><span>3</span><span>,</span>
<span>  </span>"<span>na</span><span>me</span>"<span>:</span><span> </span>"<span>Tab</span><span> </span><span>Ma</span><span>na</span><span>ger</span><span> </span><span>f</span><span>or</span><span> </span><span>Chrome</span><span> </span><span>Dev</span><span> </span><span>Docs</span>"<span>,</span>
<span>  </span>"<span>versio</span><span>n</span>"<span>:</span><span> </span>"<span>1.0</span>"<span>,</span>
<span>  </span>"<span>ico</span><span>ns</span>"<span>:</span><span> </span><span>{</span>
<span>    </span>"<span>16</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-16.</span><span>p</span><span>n</span><span>g</span>"<span>,</span>
<span>    </span>"<span>32</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-32.</span><span>p</span><span>n</span><span>g</span>"<span>,</span>
<span>    </span>"<span>48</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-48.</span><span>p</span><span>n</span><span>g</span>"<span>,</span>
<span>    </span>"<span>128</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-128.</span><span>p</span><span>n</span><span>g</span>"
<span>  </span><span>}</span>
<span>}</span>
```

Чтобы узнать больше об этих ключах манифеста, ознакомьтесь с руководством по времени чтения, в котором более подробно объясняются [метаданные](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru#step-1) и [значки](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru#step-2) расширения.

Создайте папку `images` и [загрузите в нее значки](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.tabs-manager/images) .

### Шаг 2. Создайте и стилизуйте всплывающее окно.

[Action](https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru) API управляет действием расширения (значок на панели инструментов). Когда пользователь нажимает на действие расширения, оно либо запускает некоторый код, либо открывает всплывающее окно, как в этом случае. Начните с объявления всплывающего окна в `manifest.json` :

```
<span>{</span>
<span>  </span>"<span>ac</span><span>t</span><span>io</span><span>n</span>"<span>:</span><span> </span><span>{</span>
<span>    </span>"<span>de</span><span>fault</span><span>_popup</span>"<span>:</span><span> </span>"<span>popup.h</span><span>t</span><span>ml</span>"
<span>  </span><span>}</span>
<span>}</span>
```

Всплывающее окно похоже на веб-страницу, за одним исключением: оно не может запускать встроенный JavaScript. Создайте файл `popup.html` и добавьте следующий код:

```
&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
  &lt;head&gt;
    &lt;meta charset="UTF-8" /&gt;
    &lt;meta http-equiv="X-UA-Compatible" content="IE=edge" /&gt;
    &lt;meta name="viewport" content="width=device-width, initial-scale=1.0" /&gt;
    &lt;link rel="stylesheet" href="./popup.css" /&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;template id="li_template"&gt;
      &lt;li&gt;
        &lt;a&gt;
          &lt;h3 class="title"&gt;Tab Title&lt;/h3&gt;
          &lt;p class="pathname"&gt;Tab Pathname&lt;/p&gt;
        &lt;/a&gt;
      &lt;/li&gt;
    &lt;/template&gt;

    &lt;h1&gt;Google Dev Docs&lt;/h1&gt;
    &lt;button&gt;Group Tabs&lt;/button&gt;
    &lt;ul&gt;&lt;/ul&gt;

    &lt;script src="./popup.js" type="module"&gt;&lt;/script&gt;
  &lt;/body&gt;
&lt;/html&gt;
```

Далее вы настроите всплывающее окно. Создайте файл `popup.css` и добавьте следующий код:

```
<span>body</span><span> </span><span>{</span>
<span>  </span><span>width</span><span>:</span><span> </span><span>20</span><span>rem</span><span>;</span>
<span>}</span>

<span>ul</span><span> </span><span>{</span>
<span>  </span><span>list-style-type</span><span>:</span><span> </span><span>none</span><span>;</span>
<span>  </span><span>padding-inline-start</span><span>:</span><span> </span><span>0</span><span>;</span>
<span>  </span><span>margin</span><span>:</span><span> </span><span>1</span><span>rem</span><span> </span><span>0</span><span>;</span>
<span>}</span>

<span>li</span><span> </span><span>{</span>
<span>  </span><span>padding</span><span>:</span><span> </span><span>0.25</span><span>rem</span><span>;</span>
<span>}</span>
<span>li</span><span>:</span><span>nth-child</span><span>(</span><span>odd</span><span>)</span><span> </span><span>{</span>
<span>  </span><span>background</span><span>:</span><span> </span><span>#808080</span><span>30</span><span>;</span>
<span>}</span>
<span>li</span><span>:</span><span>nth-child</span><span>(</span><span>even</span><span>)</span><span> </span><span>{</span>
<span>  </span><span>background</span><span>:</span><span> </span><span>#ffffff</span><span>;</span>
<span>}</span>

<span>h3</span><span>,</span>
<span>p</span><span> </span><span>{</span>
<span>  </span><span>margin</span><span>:</span><span> </span><span>0</span><span>;</span>
<span>}</span>
```

### Шаг 3. Управление вкладками

[API вкладок](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=ru) позволяет расширению создавать, запрашивать, изменять и переупорядочивать вкладки в браузере.

#### Запросить разрешение

Многие методы API вкладок можно использовать без запроса какого-либо разрешения. Однако нам нужен доступ к `title` и `URL` вкладок; эти конфиденциальные свойства требуют разрешения. Мы могли бы запросить разрешение `"tabs"` , но это дало бы доступ к конфиденциальным свойствам **всех** вкладок. Поскольку мы управляем только вкладками определенного сайта, мы запрашиваем узкие разрешения хоста.

Узкие [разрешения хоста](https://developer.chrome.com/docs/extensions/develop/concepts/match-patterns?hl=ru) позволяют нам защищать конфиденциальность пользователей, предоставляя повышенные разрешения **определенным сайтам** . Это предоставит доступ к свойствам `title` и `URL` , а также к дополнительным возможностям. Добавьте выделенный код в файл `manifest.json` :

```
{
  "host_permissions": [
    "https://developer.chrome.com/*"
  ]
}
```

💡 **Каковы основные различия между разрешениями вкладок и разрешениями хоста?**

Как разрешение `"tabs"` , так и разрешения хоста имеют недостатки.

Разрешение `"tabs"` предоставляет расширению возможность читать конфиденциальные данные на всех вкладках. Со временем эта информация может быть использована для сбора истории просмотров пользователя. Таким образом, если вы запросите это разрешение, Chrome во время установки отобразит следующее предупреждающее сообщение:

![Диалоговое окно с предупреждением о разрешении вкладок](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/popup-tabs-manager/image/tabs-permission-warning-d-5c3b40c0c500e.png?hl=ru)

Разрешения хоста позволяют расширению читать и запрашивать конфиденциальные свойства соответствующей вкладки, а также внедрять сценарии на эти вкладки. Во время установки пользователи увидят следующее предупреждающее сообщение:

![Диалоговое окно с предупреждением о разрешении хоста](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/popup-tabs-manager/image/host-permission-warning-d-9ec55817f55d.png?hl=ru)

Эти предупреждения могут вызвать тревогу у пользователей. Для более удобного подключения мы рекомендуем реализовать [дополнительные разрешения](https://developer.chrome.com/docs/extensions/reference/api/permissions?hl=ru) .

#### Запросить вкладки

Вы можете получить вкладки с определенных URL-адресов, используя метод `tabs.query()` . Создайте файл `popup.js` и добавьте следующий код:

```
<span>const</span><span> </span><span>tabs</span><span> </span><span>=</span><span> </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>tabs</span><span>.</span><span>query</span><span>({</span>
<span>  </span><span>url</span><span>:</span><span> </span><span>[</span>
<span>    </span>"<span>https</span><span>:</span><span>//developer.chrome.com/docs/webstore/*",</span>
<span>    </span>"<span>https</span><span>:</span><span>//developer.chrome.com/docs/extensions/*",</span>
<span>  </span><span>]</span>
<span>});</span>
```

💡 **Могу ли я использовать API Chrome прямо во всплывающем окне?**

Всплывающее окно и другие страницы расширений могут вызывать любой [API Chrome](https://developer.chrome.com/docs/extensions/reference?hl=ru) , поскольку они обслуживаются из схемы Chrome. Например `chrome-extension://EXTENSION_ID/popup.html` .

#### Сосредоточьтесь на вкладке

Во-первых, расширение сортирует имена вкладок (заголовки содержащихся HTML-страниц) в алфавитном порядке. Затем, когда щелкнут элемент списка, он сосредоточится на этой вкладке с помощью `tabs.update()` и выведет окно на передний план с помощью `windows.update()` . Добавьте следующий код в файл `popup.js` :

```
<span>...</span>
<span>const</span><span> </span><span>collator</span><span> </span><span>=</span><span> </span><span>new</span><span> </span><span>Intl</span><span>.</span><span>Collator</span><span>();</span>
<span>tabs</span><span>.</span><span>sort</span><span>((</span><span>a</span><span>,</span><span> </span><span>b</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>collator</span><span>.</span><span>compare</span><span>(</span><span>a</span><span>.</span><span>title</span><span>,</span><span> </span><span>b</span><span>.</span><span>title</span><span>));</span>

<span>const</span><span> </span><span>template</span><span> </span><span>=</span><span> </span><span>document</span><span>.</span><span>getElementById</span><span>(</span>"<span>li_template</span>"<span>);</span>
<span>const</span><span> </span><span>elements</span><span> </span><span>=</span><span> </span><span>new</span><span> </span><span>Set</span><span>();</span>
<span>for</span><span> </span><span>(</span><span>const</span><span> </span><span>tab</span><span> </span><span>of</span><span> </span><span>tabs</span><span>)</span><span> </span><span>{</span>
<span>  </span><span>const</span><span> </span><span>element</span><span> </span><span>=</span><span> </span><span>template</span><span>.</span><span>content</span><span>.</span><span>firstElementChild</span><span>.</span><span>cloneNode</span><span>(</span><span>true</span><span>);</span>

<span>  </span><span>const</span><span> </span><span>title</span><span> </span><span>=</span><span> </span><span>tab</span><span>.</span><span>title</span><span>.</span><span>split</span><span>(</span>"<span>-</span>"<span>)[</span><span>0</span><span>].</span><span>trim</span><span>();</span>
<span>  </span><span>const</span><span> </span><span>pathname</span><span> </span><span>=</span><span> </span><span>new</span><span> </span><span>URL</span><span>(</span><span>tab</span><span>.</span><span>url</span><span>).</span><span>pathname</span><span>.</span><span>slice</span><span>(</span>"<span>/docs".length);</span>

<span>  </span><span>element</span><span>.</span><span>querySelector</span><span>(".</span><span>title</span>"<span>).</span><span>textContent</span><span> </span><span>=</span><span> </span><span>title</span><span>;</span>
<span>  </span><span>element</span><span>.</span><span>querySelector</span><span>(".</span><span>pathname</span>"<span>).</span><span>textContent</span><span> </span><span>=</span><span> </span><span>pathname</span><span>;</span>
<span>  </span><span>element</span><span>.</span><span>querySelector</span><span>(</span>"<span>a</span>"<span>).</span><span>addEventListener</span><span>(</span>"<span>click</span>"<span>,</span><span> </span><span>async</span><span> </span><span>()</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>    </span><span>// need to focus window as well as the active tab</span>
<span>    </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>tabs</span><span>.</span><span>update</span><span>(</span><span>tab</span><span>.</span><span>id</span><span>,</span><span> </span><span>{</span><span> </span><span>active</span><span>:</span><span> </span><span>true</span><span> </span><span>});</span>
<span>    </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>windows</span><span>.</span><span>update</span><span>(</span><span>tab</span><span>.</span><span>windowId</span><span>,</span><span> </span><span>{</span><span> </span><span>focused</span><span>:</span><span> </span><span>true</span><span> </span><span>});</span>
<span>  </span><span>});</span>

<span>  </span><span>elements</span><span>.</span><span>add</span><span>(</span><span>element</span><span>);</span>
<span>}</span>
<span>document</span><span>.</span><span>querySelector</span><span>(</span>"<span>ul</span>"<span>).</span><span>append</span><span>(...</span><span>elements</span><span>);</span>
<span>...</span>
```

💡 **В этом коде использован интересный JavaScript**

-   [Средство сортировки](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Intl/Collator) используется для сортировки массива вкладок по предпочитаемому пользователем языку.
-   [Тег шаблона](https://web.dev/webcomponents-template/?hl=ru) , используемый для определения элемента HTML, который можно клонировать вместо использования `document.createElement()` для создания каждого элемента.
-   [Конструктор URL-адресов](https://developer.mozilla.org/docs/Web/API/URL/URL) , используемый для создания и анализа URL-адресов.
-   [Синтаксис Spread,](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_syntax) используемый для преобразования набора элементов в аргументы при вызове `append()` .

#### Сгруппируйте вкладки

API [TabGroups](https://developer.chrome.com/docs/extensions/reference/api/tabGroups?hl=ru) позволяет расширению присваивать имя группе и выбирать цвет фона. Добавьте разрешение `"tabGroups"` в манифест, добавив выделенный код:

```
{
  "permissions": [
    "tabGroups"
  ]
}
```

В `popup.js` добавьте следующий код, чтобы создать кнопку, которая будет группировать все вкладки с помощью [`tabs.group()`](https://developer.chrome.com/docs/extensions/reference/api/tabGroups?hl=ru) и перемещать их в текущее окно.

```
<span>const</span><span> </span><span>button</span><span> </span><span>=</span><span> </span><span>document</span><span>.</span><span>querySelector</span><span>(</span>"<span>button</span>"<span>);</span>
<span>button</span><span>.</span><span>addEventListener</span><span>(</span>"<span>click</span>"<span>,</span><span> </span><span>async</span><span> </span><span>()</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>const</span><span> </span><span>tabIds</span><span> </span><span>=</span><span> </span><span>tabs</span><span>.</span><span>map</span><span>(({</span><span> </span><span>id</span><span> </span><span>})</span><span> </span><span>=</span>&gt;<span> </span><span>id</span><span>);</span>
<span>  </span><span>if</span><span> </span><span>(</span><span>tabIds</span><span>.</span><span>length</span><span>)</span><span> </span><span>{</span>
<span>    </span><span>const</span><span> </span><span>group</span><span> </span><span>=</span><span> </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>tabs</span><span>.</span><span>group</span><span>({</span><span> </span><span>tabIds</span><span> </span><span>});</span>
<span>    </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>tabGroups</span><span>.</span><span>update</span><span>(</span><span>group</span><span>,</span><span> </span><span>{</span><span> </span><span>title</span><span>:</span><span> </span>"<span>DOCS</span>"<span> </span><span>});</span>
<span>  </span><span>}</span>
<span>});</span>
```

## Проверьте, работает ли это

Убедитесь, что файловая структура вашего проекта соответствует следующему дереву каталогов:

![Содержимое папки менеджера вкладок: манифест.json, popup.js, popup.css, popup.html и папка images.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/popup-tabs-manager/image/the-contents-the-tabs-ma-c08bbca1828a9.png?hl=ru)

### Загрузите расширение локально

Чтобы загрузить распакованное расширение в режиме разработчика, выполните действия, описанные в разделе [Hello World](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru#load-unpacked) .

### Откройте несколько страниц документации

Откройте следующие документы в разных окнах:

-   [Проектирование пользовательского интерфейса](https://developer.chrome.com/docs/extensions/develop/ui?hl=ru)
-   [Обнаружение в Интернет-магазине Chrome](https://developer.chrome.com/docs/webstore/discovery?hl=ru)
-   [Обзор разработки расширений](https://developer.chrome.com/docs/extensions/develop?hl=ru)
-   [Формат файла манифеста](https://developer.chrome.com/docs/extensions/reference/manifest?hl=ru)
-   [Публикация в Интернет-магазине Chrome](https://developer.chrome.com/docs/webstore/publish?hl=ru)

Нажмите всплывающее окно. Это должно выглядеть так:

![Всплывающее окно расширения «Диспетчер вкладок»](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/popup-tabs-manager/image/tabs-manager-extension-po-f958d72e1a9ae.png?hl=ru)

Всплывающее окно расширения «Диспетчер вкладок»

Нажмите кнопку «Группировать вкладки». Это должно выглядеть так:

![Менеджер вкладок Сгруппированные вкладки](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/popup-tabs-manager/image/tabs-manager-grouped-tabs-65bdf282bdf98.png?hl=ru)

Сгруппированные вкладки с помощью расширения Tabs Manager.

## 🎯 Возможные улучшения

Основываясь на том, что вы узнали сегодня, попробуйте реализовать любое из следующих действий:

-   Настройте таблицу стилей всплывающего окна.
-   Измените цвет и заголовок группы вкладок.
-   Управляйте вкладками другого сайта документации.
-   Добавьте поддержку разгруппировки сгруппированных вкладок.

## Продолжайте строить!

Поздравляем с завершением этого урока 🎉. Продолжайте развивать свои навыки, выполнив другие уроки из этой серии:

| Расширение | Что вы узнаете |
| --- | --- |
| [Время чтения](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru) | Автоматическая вставка элемента на каждую страницу. |
| [Режим фокусировки](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-activetab?hl=ru) | Чтобы запустить код на текущей странице после нажатия на действие расширения. |

## Продолжить изучение

Мы надеемся, что вам понравилось создавать это расширение Chrome, и мы рады продолжить обучение разработке Chrome. Мы рекомендуем следующий путь обучения:

-   [Руководство разработчика](https://developer.chrome.com/docs/extensions/develop?hl=ru) содержит десятки дополнительных ссылок на документацию, относящуюся к созданию расширенных расширений.
-   Расширения имеют доступ к мощным API, помимо тех, что доступны в открытой сети. [В документации по API Chrome](https://developer.chrome.com/docs/extensions/reference?hl=ru) описан каждый API.
