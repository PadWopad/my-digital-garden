---
{"dg-publish":true,"created":"2025-01-31T16:47:02 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/extensions/get-started/tutorial/service-worker-events?hl=ru","author":null,"permalink":"/proekty/extentions/obrabotka-sobytij-s-pomoshhyu-servisnyh-rabotnikov-chrome-extensions-chrome-for-developers/","dgPassFrontmatter":true}
---


# Обработка событий с помощью сервисных работников  |  Chrome Extensions  |  Chrome for Developers

> ## Excerpt
> Узнайте, как создавать и отлаживать работника службы расширений.

---
Учебное пособие, в котором рассматриваются концепции рабочих служб расширения.

## Обзор

В этом руководстве представлены сведения о работниках службы расширений Chrome. В рамках этого руководства вы создадите расширение, которое позволит пользователям быстро переходить на справочные страницы API Chrome с помощью омнибокса. Вы узнаете, как:

-   Зарегистрируйте своего сервис-воркера и импортируйте модули.
-   Отладьте работника службы расширений.
-   Управляйте состоянием и обрабатывайте события.
-   Запускайте периодические события.
-   Общайтесь с помощью сценариев контента.

## Прежде чем начать

В этом руководстве предполагается, что у вас есть базовый опыт веб-разработки. Мы рекомендуем просмотреть [Extensions 101](https://developer.chrome.com/docs/extensions/get-started?hl=ru) и [Hello World](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru) , чтобы получить представление о разработке расширений.

## Создайте расширение

Начните с создания нового каталога под названием `quick-api-reference` для хранения файлов расширений или загрузите исходный код из нашего репозитория [образцов GitHub](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.quick-api-reference) .

### Шаг 1. Зарегистрируйте сервисного работника

Создайте файл [манифеста](https://developer.chrome.com/docs/extensions/reference/manifest?hl=ru) в корне проекта и добавьте следующий код:

манифест.json:

```
<span>{</span><span><br>&nbsp; </span><span>"manifest_version"</span><span>:</span><span> </span><span>3</span><span>,</span><span><br>&nbsp; </span><span>"name"</span><span>:</span><span> </span><span>"Open extension API reference"</span><span>,</span><span><br>&nbsp; </span><span>"version"</span><span>:</span><span> </span><span>"1.0.0"</span><span>,</span><span><br>&nbsp; </span><span>"icons"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"16"</span><span>:</span><span> </span><span>"images/icon-16.png"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"128"</span><span>:</span><span> </span><span>"images/icon-128.png"</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>"background"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"service_worker"</span><span>:</span><span> </span><span>"service-worker.js"</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

Расширения регистрируют своего сервис-воркера в манифесте, который принимает только один файл JavaScript. Нет необходимости вызывать `navigator.serviceWorker.register()` , как на веб-странице.

Создайте папку `images` и [загрузите в нее значки](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.quick-api-reference/images) .

Ознакомьтесь с первыми шагами руководства «Время чтения», чтобы узнать больше о [метаданных](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru#step-1) и [значках](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru#step-2) расширения в манифесте.

### Шаг 2. Импортируйте несколько модулей Service Worker.

Наш сервис-воркер реализует две функции. Для большей удобства сопровождения мы реализуем каждую функцию в отдельном модуле. Во-первых, нам нужно объявить сервис-воркера как [ES-модуль](https://web.dev/es-modules-in-sw/?hl=ru) в нашем манифесте, что позволит нам импортировать модули в наш сервис-воркер:

манифест.json:

```
<span>{</span><span><br>&nbsp;</span><span>"background"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"service_worker"</span><span>:</span><span> </span><span>"service-worker.js"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"type"</span><span>:</span><span> </span><span>"module"</span><span><br>&nbsp; </span><span>},</span><span><br></span><span>}</span><span><br></span>
```

Создайте файл `service-worker.js` и импортируйте два модуля:

```
<span>import</span><span> </span><span>'./sw-omnibox.js'</span><span>;</span><span><br></span><span>import</span><span> </span><span>'./sw-tips.js'</span><span>;</span><span><br></span>
```

Создайте эти файлы и добавьте к каждому журнал консоли.

sw-omnibox.js:

```
<span>console</span><span>.</span><span>log</span><span>(</span><span>"sw-omnibox.js"</span><span>);</span><span><br></span>
```

sw-tips.js:

```
<span>console</span><span>.</span><span>log</span><span>(</span><span>"sw-tips.js"</span><span>);</span><span><br></span>
```

См. [раздел Импорт сценариев](https://developer.chrome.com/docs/extensions/develop/concepts/service-workers/basics?hl=ru#import-scripts) , чтобы узнать о других способах импорта нескольких файлов в сервис-воркера.

### Необязательно: отладка сервис-воркера

Я объясню, как найти журналы сервисного работника и узнать, когда он завершился. Сначала следуйте инструкциям по [загрузке распакованного расширения](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru#load-unpacked) .

Через 30 секунд вы увидите надпись «Service Worker (inactive)», что означает, что Service Worker завершил работу. Нажмите ссылку «служебный работник (неактивный)», чтобы проверить ее. Следующая анимация показывает это.

Вы заметили, что проверка сервисника разбудила его? Открытие сервисного работника в инструментах разработчика сохранит его активным. Чтобы убедиться, что ваше расширение работает правильно после завершения работы вашего сервис-воркера, не забудьте закрыть DevTools.

Теперь сломайте расширение, чтобы узнать, где искать ошибки. Один из способов сделать это — удалить «.js» из импорта `'./sw-omnibox.js'` в файле `service-worker.js` . Chrome не сможет зарегистрировать сервисного работника.

Вернитесь на chrome://extensions и обновите расширение. Вы увидите две ошибки:

```
<span>Service</span><span> worker registration failed</span><span>.</span><span> </span><span>Status</span><span> code</span><span>:</span><span> </span><span>3.</span><span><br><br></span><span>An</span><span> unknown error occurred </span><span>when</span><span> fetching the script</span><span>.</span><span><br></span>
```

Дополнительные способы отладки работника службы расширений см. в [разделе «Отладка расширений»](https://developer.chrome.com/docs/extensions/get-started/tutorial/debug?hl=ru#debug_bg) .

### Шаг 4. Инициализируйте состояние

Chrome отключит сервис-воркеры, если они не нужны. Мы используем API [`chrome.storage`](https://developer.chrome.com/docs/extensions/reference/api/storage?hl=ru) для сохранения состояния во время сеансов сервис-воркера. Для доступа к хранилищу нам нужно запросить разрешение в манифесте:

манифест.json:

```
<span>{</span><span><br>&nbsp; </span><span>...</span><span><br>&nbsp; </span><span>"permissions"</span><span>:</span><span> </span><span>[</span><span>"storage"</span><span>],</span><span><br></span><span>}</span><span><br></span>
```

Сначала сохраните предложения по умолчанию в хранилище. Мы можем инициализировать состояние при первой установке расширения, прослушивая событие [`runtime.onInstalled()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#event-onInstalled) :

sw-omnibox.js:

```
<span>...</span><span><br></span><span>// Save default API suggestions</span><span><br>chrome</span><span>.</span><span>runtime</span><span>.</span><span>onInstalled</span><span>.</span><span>addListener</span><span>(({</span><span> reason </span><span>})</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; </span><span>if</span><span> </span><span>(</span><span>reason </span><span>===</span><span> </span><span>'install'</span><span>)</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; chrome</span><span>.</span><span>storage</span><span>.</span><span>local</span><span>.</span><span>set</span><span>({</span><span><br>&nbsp; &nbsp; &nbsp; apiSuggestions</span><span>:</span><span> </span><span>[</span><span>'tabs'</span><span>,</span><span> </span><span>'storage'</span><span>,</span><span> </span><span>'scripting'</span><span>]</span><span><br>&nbsp; &nbsp; </span><span>});</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>});</span><span><br></span>
```

Сервисные работники не имеют прямого доступа к [объекту окна](https://developer.mozilla.org/docs/Web/API/Window) и поэтому не могут использовать [`window.localStorage`](https://developer.mozilla.org/docs/Web/API/Window/localStorage) для хранения значений. Кроме того, сервис-воркеры — это недолговечная среда выполнения; они неоднократно завершаются в течение сеанса браузера пользователя, что делает их несовместимыми с глобальными переменными. Вместо этого используйте [`chrome.storage.local`](https://developer.chrome.com/docs/extensions/reference/api/storage?hl=ru#property-local) , который хранит данные на локальном компьютере.

См. [раздел «Сохранение данных вместо использования глобальных переменных»,](https://developer.chrome.com/docs/extensions/develop/concepts/service-workers/lifecycle?hl=ru#persist-data) чтобы узнать о других вариантах хранения для работников служб расширения.

### Шаг 5. Зарегистрируйте свои мероприятия

Все прослушиватели событий должны быть статически зарегистрированы в глобальной области действия сервис-воркера. Другими словами, прослушиватели событий не должны быть вложены в асинхронные функции. Таким образом, Chrome может гарантировать восстановление всех обработчиков событий в случае перезагрузки сервисного работника.

В этом примере мы собираемся использовать API [`chrome.omnibox`](https://developer.chrome.com/docs/extensions/reference/api/omnibox?hl=ru) , но сначала мы должны объявить триггер ключевого слова omnibox в манифесте:

манифест.json:

```
<span>{</span><span><br>&nbsp; </span><span>...</span><span><br>&nbsp; </span><span>"minimum_chrome_version"</span><span>:</span><span> </span><span>"102"</span><span>,</span><span><br>&nbsp; </span><span>"omnibox"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"keyword"</span><span>:</span><span> </span><span>"api"</span><span><br>&nbsp; </span><span>},</span><span><br></span><span>}</span><span><br></span>
```

Теперь зарегистрируйте прослушиватели событий омнибокса на верхнем уровне скрипта. Когда пользователь вводит ключевое слово омнибокса ( `api` ) в адресную строку, а затем табуляцию или пробел, Chrome отображает список предложений на основе ключевых слов в хранилище. За заполнение этих предложений отвечает событие [`onInputChanged()`](https://developer.chrome.com/docs/extensions/reference/api/omnibox?hl=ru#event-onInputChanged) , которое принимает текущий пользовательский ввод и объект [`suggestResult`](https://developer.chrome.com/docs/extensions/reference/api/omnibox?hl=ru#type-SuggestResult) .

sw-omnibox.js:

```
<span>...</span><span><br></span><span>const</span><span> URL_CHROME_EXTENSIONS_DOC </span><span>=</span><span><br>&nbsp; </span><span>'https://developer.chrome.com/docs/extensions/reference/'</span><span>;</span><span><br></span><span>const</span><span> NUMBER_OF_PREVIOUS_SEARCHES </span><span>=</span><span> </span><span>4</span><span>;</span><span><br><br></span><span>// Display the suggestions after user starts typing</span><span><br>chrome</span><span>.</span><span>omnibox</span><span>.</span><span>onInputChanged</span><span>.</span><span>addListener</span><span>(</span><span>async </span><span>(</span><span>input</span><span>,</span><span> suggest</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; await chrome</span><span>.</span><span>omnibox</span><span>.</span><span>setDefaultSuggestion</span><span>({</span><span><br>&nbsp; &nbsp; description</span><span>:</span><span> </span><span>'Enter a Chrome API or choose from past searches'</span><span><br>&nbsp; </span><span>});</span><span><br>&nbsp; </span><span>const</span><span> </span><span>{</span><span> apiSuggestions </span><span>}</span><span> </span><span>=</span><span> await chrome</span><span>.</span><span>storage</span><span>.</span><span>local</span><span>.</span><span>get</span><span>(</span><span>'apiSuggestions'</span><span>);</span><span><br>&nbsp; </span><span>const</span><span> suggestions </span><span>=</span><span> apiSuggestions</span><span>.</span><span>map</span><span>((</span><span>api</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>return</span><span> </span><span>{</span><span> content</span><span>:</span><span> api</span><span>,</span><span> description</span><span>:</span><span> </span><span>`</span><span>Open</span><span> chrome</span><span>.</span><span>$</span><span>{</span><span>api</span><span>}</span><span> API</span><span>`</span><span> </span><span>};</span><span><br>&nbsp; </span><span>});</span><span><br>&nbsp; suggest</span><span>(</span><span>suggestions</span><span>);</span><span><br></span><span>});</span><span><br></span>
```

После того, как пользователь выберет предложение, [`onInputEntered()`](https://developer.chrome.com/docs/extensions/reference/api/omnibox?hl=ru#event-onInputEntered) откроет соответствующую справочную страницу Chrome API.

sw-omnibox.js:

```
<span>...</span><span><br></span><span>// Open the reference page of the chosen API</span><span><br>chrome</span><span>.</span><span>omnibox</span><span>.</span><span>onInputEntered</span><span>.</span><span>addListener</span><span>((</span><span>input</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; chrome</span><span>.</span><span>tabs</span><span>.</span><span>create</span><span>({</span><span> url</span><span>:</span><span> URL_CHROME_EXTENSIONS_DOC </span><span>+</span><span> input </span><span>});</span><span><br>&nbsp; </span><span>// Save the latest keyword</span><span><br>&nbsp; updateHistory</span><span>(</span><span>input</span><span>);</span><span><br></span><span>});</span><span><br></span>
```

Функция `updateHistory()` принимает входные данные омнибокса и сохраняет их в [`storage.local`](https://developer.chrome.com/docs/extensions/reference/api/storage?hl=ru) . Таким образом, самый последний поисковый запрос можно будет использовать позже в качестве предложения омнибокса.

sw-omnibox.js:

```
<span>...</span><span><br>async </span><span>function</span><span> updateHistory</span><span>(</span><span>input</span><span>)</span><span> </span><span>{</span><span><br>&nbsp; </span><span>const</span><span> </span><span>{</span><span> apiSuggestions </span><span>}</span><span> </span><span>=</span><span> await chrome</span><span>.</span><span>storage</span><span>.</span><span>local</span><span>.</span><span>get</span><span>(</span><span>'apiSuggestions'</span><span>);</span><span><br>&nbsp; apiSuggestions</span><span>.</span><span>unshift</span><span>(</span><span>input</span><span>);</span><span><br>&nbsp; apiSuggestions</span><span>.</span><span>splice</span><span>(</span><span>NUMBER_OF_PREVIOUS_SEARCHES</span><span>);</span><span><br>&nbsp; </span><span>return</span><span> chrome</span><span>.</span><span>storage</span><span>.</span><span>local</span><span>.</span><span>set</span><span>({</span><span> apiSuggestions </span><span>});</span><span><br></span><span>}</span><span><br></span>
```

### Шаг 6. Настройте повторяющееся событие

Методы `setTimeout()` или `setInterval()` обычно используются для выполнения отложенных или периодических задач. Однако эти API могут дать сбой, поскольку планировщик отменит таймеры при завершении работы сервис-воркера. Вместо этого расширения могут использовать API [`chrome.alarms`](https://developer.chrome.com/docs/extensions/reference/api/alarms?hl=ru) .

Начните с запроса разрешения `"alarms"` в манифесте. Кроме того, чтобы получить советы по расширению из удаленного расположения, вам необходимо запросить [разрешение хоста](https://developer.chrome.com/docs/extensions/develop/concepts/match-patterns?hl=ru) :

манифест.json:

```
<span>{</span><span><br>&nbsp; </span><span>...</span><span><br>&nbsp; </span><s><span>"permissions"</span><span>:</span><span> </span><span>[</span><span>"storage"</span><span>],</span></s><span><br>&nbsp; </span><strong><span>"permissions"</span><span>:</span><span> </span><span>[</span><span>"storage"</span><span>,</span><span> </span><span>"alarms"</span><span>],</span></strong><span><br>&nbsp; </span><span>"host_permissions"</span><span>:</span><span> </span><span>[</span><span>"https://extension-tips.glitch.me/*"</span><span>],</span><span><br></span><span>}</span><span><br></span>
```

Расширение получит все советы, выберет один случайным образом и сохранит его в хранилище. Мы создадим сигнал тревоги, который будет срабатывать один раз в день для обновления подсказки. Сигналы тревоги не сохраняются при закрытии Chrome. Поэтому нам нужно проверить, существует ли сигнал тревоги, и создать его, если его нет.

sw-tips.js:

```
<span>// Fetch tip &amp; save in storage</span><span><br></span><span>const</span><span> updateTip </span><span>=</span><span> async </span><span>()</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; </span><span>const</span><span> response </span><span>=</span><span> await fetch</span><span>(</span><span>'https://extension-tips.glitch.me/tips.json'</span><span>);</span><span><br>&nbsp; </span><span>const</span><span> tips </span><span>=</span><span> await response</span><span>.</span><span>json</span><span>();</span><span><br>&nbsp; </span><span>const</span><span> randomIndex </span><span>=</span><span> </span><span>Math</span><span>.</span><span>floor</span><span>(</span><span>Math</span><span>.</span><span>random</span><span>()</span><span> </span><span>*</span><span> tips</span><span>.</span><span>length</span><span>);</span><span><br>&nbsp; </span><span>return</span><span> chrome</span><span>.</span><span>storage</span><span>.</span><span>local</span><span>.</span><span>set</span><span>({</span><span> tip</span><span>:</span><span> tips</span><span>[</span><span>randomIndex</span><span>]</span><span> </span><span>});</span><span><br></span><span>};</span><span><br><br></span><span>const</span><span> ALARM_NAME </span><span>=</span><span> </span><span>'tip'</span><span>;</span><span><br><br></span><span>// Check if alarm exists to avoid resetting the timer.</span><span><br></span><span>// The alarm might be removed when the browser session restarts.</span><span><br>async </span><span>function</span><span> createAlarm</span><span>()</span><span> </span><span>{</span><span><br>&nbsp; </span><span>const</span><span> alarm </span><span>=</span><span> await chrome</span><span>.</span><span>alarms</span><span>.</span><span>get</span><span>(</span><span>ALARM_NAME</span><span>);</span><span><br>&nbsp; </span><span>if</span><span> </span><span>(</span><span>typeof</span><span> alarm </span><span>===</span><span> </span><span>'undefined'</span><span>)</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; chrome</span><span>.</span><span>alarms</span><span>.</span><span>create</span><span>(</span><span>ALARM_NAME</span><span>,</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; &nbsp; delayInMinutes</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; &nbsp; &nbsp; periodInMinutes</span><span>:</span><span> </span><span>1440</span><span><br>&nbsp; &nbsp; </span><span>});</span><span><br>&nbsp; &nbsp; updateTip</span><span>();</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br><br>createAlarm</span><span>();</span><span><br><br></span><span>// Update tip once a day</span><span><br>chrome</span><span>.</span><span>alarms</span><span>.</span><span>onAlarm</span><span>.</span><span>addListener</span><span>(</span><span>updateTip</span><span>);</span><span><br></span>
```

### Шаг 7: Общайтесь с другими контекстами

Расширения используют [сценарии содержимого](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru) для чтения и изменения содержимого страницы. Когда пользователь посещает справочную страницу API Chrome, сценарий содержимого расширения обновит страницу с советом дня. Он [отправляет сообщение](https://developer.chrome.com/docs/extensions/develop/concepts/messaging?hl=ru) с запросом совета дня от сервисного работника.

Начните с объявления сценария содержимого в манифесте и добавьте шаблон соответствия, соответствующий справочной документации [API Chrome](https://developer.chrome.com/docs/extensions/reference?hl=ru) .

манифест.json:

```
<span>{</span><span><br>&nbsp; </span><span>...</span><span><br>&nbsp; </span><span>"content_scripts"</span><span>:</span><span> </span><span>[</span><span><br>&nbsp; &nbsp; </span><span>{</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"matches"</span><span>:</span><span> </span><span>[</span><span>"https://developer.chrome.com/docs/extensions/reference/*"</span><span>],</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"js"</span><span>:</span><span> </span><span>[</span><span>"content.js"</span><span>]</span><span><br>&nbsp; &nbsp; </span><span>}</span><span><br>&nbsp; </span><span>]</span><span><br></span><span>}</span><span><br><br></span>
```

Создайте новый файл содержимого. Следующий код отправляет сообщение работнику службы с запросом подсказки. Затем добавляет кнопку, которая откроет всплывающее окно с подсказкой о расширении. Этот код использует новую веб-платформу [Popover API](https://developer.mozilla.org/docs/Web/API/Popover_API) .

контент.js:

```
<span>(</span><span>async </span><span>()</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; </span><span>// Sends a message to the service worker and receives a tip in response</span><span><br>&nbsp; </span><span>const</span><span> </span><span>{</span><span> tip </span><span>}</span><span> </span><span>=</span><span> await chrome</span><span>.</span><span>runtime</span><span>.</span><span>sendMessage</span><span>({</span><span> greeting</span><span>:</span><span> </span><span>'tip'</span><span> </span><span>});</span><span><br><br>&nbsp; </span><span>const</span><span> nav </span><span>=</span><span> document</span><span>.</span><span>querySelector</span><span>(</span><span>'.upper-tabs &gt; nav'</span><span>);</span><span><br>&nbsp; <br>&nbsp; </span><span>const</span><span> tipWidget </span><span>=</span><span> createDomElement</span><span>(`</span><span><br>&nbsp; &nbsp; </span><span>&lt;</span><span>button type</span><span>=</span><span>"button"</span><span> popovertarget</span><span>=</span><span>"tip-popover"</span><span> popovertargetaction</span><span>=</span><span>"show"</span><span> style</span><span>=</span><span>"padding: 0 12px; height: 36px;"</span><span>&gt;</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>&lt;</span><span>span style</span><span>=</span><span>"display: block; font: var(--devsite-link-font,500 14px/20px var(--devsite-primary-font-family));"</span><span>&gt;</span><span>Tip</span><span>&lt;</span><span>/span&gt;<br>&nbsp; &nbsp; &lt;/</span><span>button</span><span>&gt;</span><span><br>&nbsp; </span><span>`);</span><span><br><br>&nbsp; </span><span>const</span><span> popover </span><span>=</span><span> createDomElement</span><span>(</span><span><br>&nbsp; &nbsp; </span><span>`&lt;</span><span>div id</span><span>=</span><span>'tip-popover'</span><span> popover style</span><span>=</span><span>"margin: auto;"</span><span>&gt;</span><span>$</span><span>{</span><span>tip</span><span>}&lt;/</span><span>div</span><span>&gt;`</span><span><br>&nbsp; </span><span>);</span><span><br><br>&nbsp; document</span><span>.</span><span>body</span><span>.</span><span>append</span><span>(</span><span>popover</span><span>);</span><span><br>&nbsp; nav</span><span>.</span><span>append</span><span>(</span><span>tipWidget</span><span>);</span><span><br></span><span>})();</span><span><br><br></span><span>function</span><span> createDomElement</span><span>(</span><span>html</span><span>)</span><span> </span><span>{</span><span><br>&nbsp; </span><span>const</span><span> dom </span><span>=</span><span> </span><span>new</span><span> </span><span>DOMParser</span><span>().</span><span>parseFromString</span><span>(</span><span>html</span><span>,</span><span> </span><span>'text/html'</span><span>);</span><span><br>&nbsp; </span><span>return</span><span> dom</span><span>.</span><span>body</span><span>.</span><span>firstElementChild</span><span>;</span><span><br></span><span>}</span><span><br></span>
```

Последний шаг — добавить в наш сервис-воркер обработчик сообщений, который отправляет ответ на сценарий содержимого с ежедневным советом.

sw-tips.js:

```
<span>...</span><span><br></span><span>// Send tip to content script via messaging</span><span><br>chrome</span><span>.</span><span>runtime</span><span>.</span><span>onMessage</span><span>.</span><span>addListener</span><span>((</span><span>message</span><span>,</span><span> sender</span><span>,</span><span> sendResponse</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; </span><span>if</span><span> </span><span>(</span><span>message</span><span>.</span><span>greeting </span><span>===</span><span> </span><span>'tip'</span><span>)</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; chrome</span><span>.</span><span>storage</span><span>.</span><span>local</span><span>.</span><span>get</span><span>(</span><span>'tip'</span><span>).</span><span>then</span><span>(</span><span>sendResponse</span><span>);</span><span><br>&nbsp; &nbsp; </span><span>return</span><span> </span><span>true</span><span>;</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>});</span><span><br></span>
```

## Проверьте, работает ли это

Убедитесь, что файловая структура вашего проекта выглядит следующим образом:

![Содержимое папки расширения: папка images, манифест.json, service-worker.js, sw-omnibox.js, sw-tips.js и content.js.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/service-worker-events/image/the-contents-the-extensi-5487192c01cef.png?hl=ru)

### Загрузите расширение локально

Чтобы загрузить распакованное расширение в режиме разработчика, выполните действия, описанные в разделе [Hello world](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru#load-unpacked) .

### Открыть справочную страницу

1.  Введите ключевое слово «api» в адресную строку браузера.
2.  Нажмите «Tab» или «Пробел».
3.  Введите полное имя API.
    -   ИЛИ выберите из списка прошлых поисков
4.  Откроется новая страница со справочной страницей API Chrome.

Это должно выглядеть так:

![Краткий справочник по API, открывающий справочник по API среды выполнения.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/service-worker-events/image/quick-api-reference-openi-5041b3b640769.gif?hl=ru)

Расширение Quick API, открывающее API среды выполнения.

### Откройте совет дня

Нажмите кнопку «Совет», расположенную на панели навигации, чтобы открыть подсказку о расширении.

![Открыть ежедневный совет в](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/service-worker-events/image/open-daily-tip-676249a78de8e.gif?hl=ru)

Расширение быстрого API, открывающее совет дня.

## 🎯 Возможные улучшения

Основываясь на том, что вы узнали сегодня, попробуйте выполнить любое из следующих действий:

-   Изучите другой способ реализации предложений омнибокса.
-   Создайте собственное модальное окно для отображения подсказки расширения.
-   Откройте дополнительную страницу со справочными страницами API веб-расширений MDN.

## Продолжайте строить!

Поздравляем с завершением этого урока 🎉. Продолжайте совершенствовать свои навыки, выполнив другие руководства для начинающих:

| Расширение | Что вы узнаете |
| --- | --- |
| [Время чтения](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru) | Автоматическая вставка элемента в определенный набор страниц. |
| [Менеджер вкладок](https://developer.chrome.com/docs/extensions/get-started/tutorial/popup-tabs-manager?hl=ru) | Создать всплывающее окно, управляющее вкладками браузера. |
| [Режим фокусировки](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-activetab?hl=ru) | Чтобы запустить код на текущей странице после нажатия на действие расширения. |

## Продолжить изучение

Чтобы продолжить обучение сотрудников службы расширения, мы рекомендуем изучить следующие статьи:

-   [О работниках службы распространения знаний](https://developer.chrome.com/docs/extensions/develop/concepts/service-workers?hl=ru) .
-   [Жизненный цикл работника службы расширения](https://developer.chrome.com/docs/extensions/develop/concepts/service-workers/lifecycle?hl=ru) .
-   [События в сервисных работниках](https://developer.chrome.com/docs/extensions/develop/concepts/service-workers/events?hl=ru)
