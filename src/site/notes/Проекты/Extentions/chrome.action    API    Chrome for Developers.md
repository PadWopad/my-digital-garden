---
{"dg-publish":true,"created":"2025-01-31T16:47:33 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru","author":null,"permalink":"/proekty/extentions/chrome-action-api-chrome-for-developers/","dgPassFrontmatter":true}
---


# chrome.action  |  API  |  Chrome for Developers

> ## Excerpt
> Manifest V3

---
[Skip to main content](https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#main-content)

 [![Chrome for Developers](https://www.gstatic.com/devrel-devsite/prod/v0f39da1ecc369fa6a1c816bfa5d8f549228499e733c9bd8becc473543aa6caa2/chrome/images/lockup.svg)](https://developer.chrome.com/)

-   Manifest V3
    
-   [➡ Manifest V2](https://developer.chrome.com/docs/extensions/mv2/reference)
-   [accessibilityFeatures](https://developer.chrome.com/docs/extensions/reference/api/accessibilityFeatures)
-   [action](https://developer.chrome.com/docs/extensions/reference/api/action)
-   [alarms](https://developer.chrome.com/docs/extensions/reference/api/alarms)
-   [audio](https://developer.chrome.com/docs/extensions/reference/api/audio)
-   [bookmarks](https://developer.chrome.com/docs/extensions/reference/api/bookmarks)
-   [browsingData](https://developer.chrome.com/docs/extensions/reference/api/browsingData)
-   [certificateProvider](https://developer.chrome.com/docs/extensions/reference/api/certificateProvider)
-   [commands](https://developer.chrome.com/docs/extensions/reference/api/commands)
-   [contentSettings](https://developer.chrome.com/docs/extensions/reference/api/contentSettings)
-   [contextMenus](https://developer.chrome.com/docs/extensions/reference/api/contextMenus)
-   [cookies](https://developer.chrome.com/docs/extensions/reference/api/cookies)
-   [debugger](https://developer.chrome.com/docs/extensions/reference/api/debugger)
-   [declarativeContent](https://developer.chrome.com/docs/extensions/reference/api/declarativeContent)
-   [declarativeNetRequest](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest)
-   [desktopCapture](https://developer.chrome.com/docs/extensions/reference/api/desktopCapture)
-   [devtools.inspectedWindow](https://developer.chrome.com/docs/extensions/reference/api/devtools/inspectedWindow)
-   [devtools.network](https://developer.chrome.com/docs/extensions/reference/api/devtools/network)
-   [devtools.panels](https://developer.chrome.com/docs/extensions/reference/api/devtools/panels)
-   [devtools.performance](https://developer.chrome.com/docs/extensions/reference/api/devtools/performance)
-   [devtools.recorder](https://developer.chrome.com/docs/extensions/reference/api/devtools/recorder)
-   [dns](https://developer.chrome.com/docs/extensions/reference/api/dns)
-   [documentScan](https://developer.chrome.com/docs/extensions/reference/api/documentScan)
-   [dom](https://developer.chrome.com/docs/extensions/reference/api/dom)
-   [downloads](https://developer.chrome.com/docs/extensions/reference/api/downloads)
-   [enterprise.deviceAttributes](https://developer.chrome.com/docs/extensions/reference/api/enterprise/deviceAttributes)
-   [enterprise.hardwarePlatform](https://developer.chrome.com/docs/extensions/reference/api/enterprise/hardwarePlatform)
-   [enterprise.networkingAttributes](https://developer.chrome.com/docs/extensions/reference/api/enterprise/networkingAttributes)
-   [enterprise.platformKeys](https://developer.chrome.com/docs/extensions/reference/api/enterprise/platformKeys)
-   [events](https://developer.chrome.com/docs/extensions/reference/api/events)
-   [extension](https://developer.chrome.com/docs/extensions/reference/api/extension)
-   [extensionTypes](https://developer.chrome.com/docs/extensions/reference/api/extensionTypes)
-   [fileBrowserHandler](https://developer.chrome.com/docs/extensions/reference/api/fileBrowserHandler)
-   [fileSystemProvider](https://developer.chrome.com/docs/extensions/reference/api/fileSystemProvider)
-   [fontSettings](https://developer.chrome.com/docs/extensions/reference/api/fontSettings)
-   [gcm](https://developer.chrome.com/docs/extensions/reference/api/gcm)
-   [history](https://developer.chrome.com/docs/extensions/reference/api/history)
-   [i18n](https://developer.chrome.com/docs/extensions/reference/api/i18n)
-   [identity](https://developer.chrome.com/docs/extensions/reference/api/identity)
-   [idle](https://developer.chrome.com/docs/extensions/reference/api/idle)
-   [input.ime](https://developer.chrome.com/docs/extensions/reference/api/input/ime)
-   [instanceID](https://developer.chrome.com/docs/extensions/reference/api/instanceID)
-   [loginState](https://developer.chrome.com/docs/extensions/reference/api/loginState)
-   [management](https://developer.chrome.com/docs/extensions/reference/api/management)
-   [notifications](https://developer.chrome.com/docs/extensions/reference/api/notifications)
-   [offscreen](https://developer.chrome.com/docs/extensions/reference/api/offscreen)
-   [omnibox](https://developer.chrome.com/docs/extensions/reference/api/omnibox)
-   [pageCapture](https://developer.chrome.com/docs/extensions/reference/api/pageCapture)
-   [permissions](https://developer.chrome.com/docs/extensions/reference/api/permissions)
-   [platformKeys](https://developer.chrome.com/docs/extensions/reference/api/platformKeys)
-   [power](https://developer.chrome.com/docs/extensions/reference/api/power)
-   [printerProvider](https://developer.chrome.com/docs/extensions/reference/api/printerProvider)
-   [printing](https://developer.chrome.com/docs/extensions/reference/api/printing)
-   [printingMetrics](https://developer.chrome.com/docs/extensions/reference/api/printingMetrics)
-   [privacy](https://developer.chrome.com/docs/extensions/reference/api/privacy)
-   [processes](https://developer.chrome.com/docs/extensions/reference/api/processes)
-   [proxy](https://developer.chrome.com/docs/extensions/reference/api/proxy)
-   [readingList](https://developer.chrome.com/docs/extensions/reference/api/readingList)
-   [runtime](https://developer.chrome.com/docs/extensions/reference/api/runtime)
-   [scripting](https://developer.chrome.com/docs/extensions/reference/api/scripting)
-   [search](https://developer.chrome.com/docs/extensions/reference/api/search)
-   [sessions](https://developer.chrome.com/docs/extensions/reference/api/sessions)
-   [sidePanel](https://developer.chrome.com/docs/extensions/reference/api/sidePanel)
-   [storage](https://developer.chrome.com/docs/extensions/reference/api/storage)
-   [system.cpu](https://developer.chrome.com/docs/extensions/reference/api/system/cpu)
-   [system.display](https://developer.chrome.com/docs/extensions/reference/api/system/display)
-   [system.memory](https://developer.chrome.com/docs/extensions/reference/api/system/memory)
-   [system.storage](https://developer.chrome.com/docs/extensions/reference/api/system/storage)
-   [systemLog](https://developer.chrome.com/docs/extensions/reference/api/systemLog)
-   [tabCapture](https://developer.chrome.com/docs/extensions/reference/api/tabCapture)
-   [tabGroups](https://developer.chrome.com/docs/extensions/reference/api/tabGroups)
-   [tabs](https://developer.chrome.com/docs/extensions/reference/api/tabs)
-   [topSites](https://developer.chrome.com/docs/extensions/reference/api/topSites)
-   [tts](https://developer.chrome.com/docs/extensions/reference/api/tts)
-   [ttsEngine](https://developer.chrome.com/docs/extensions/reference/api/ttsEngine)
-   [types](https://developer.chrome.com/docs/extensions/reference/api/types)
-   [userScripts](https://developer.chrome.com/docs/extensions/reference/api/userScripts)
-   [vpnProvider](https://developer.chrome.com/docs/extensions/reference/api/vpnProvider)
-   [wallpaper](https://developer.chrome.com/docs/extensions/reference/api/wallpaper)
-   [webAuthenticationProxy](https://developer.chrome.com/docs/extensions/reference/api/webAuthenticationProxy)
-   [webNavigation](https://developer.chrome.com/docs/extensions/reference/api/webNavigation)
-   [webRequest](https://developer.chrome.com/docs/extensions/reference/api/webRequest)
-   [windows](https://developer.chrome.com/docs/extensions/reference/api/windows)

bookmark\_border Оптимизируйте свои подборки Сохраняйте и классифицируйте контент в соответствии со своими настройками.

Используйте API `chrome.action` для управления значком расширения на панели инструментов Google Chrome.

Значки действий отображаются на панели инструментов браузера рядом с [омнибоксом](https://en.wiktionary.org/wiki/omnibox) . После установки они появляются в меню расширений (значок кусочка головоломки). Пользователи могут закрепить значок вашего расширения на панели инструментов.

## Доступность

## Манифест

Для использования этого API [в манифесте](https://developer.chrome.com/docs/extensions/mv3/manifest?hl=ru) необходимо объявить следующие ключи.

`"action"`  

Чтобы использовать API `chrome.action` , укажите значение `"manifest_version"` `3` и включите ключ `"action"` в [файл манифеста](https://developer.chrome.com/docs/extensions/reference/manifest?hl=ru) .

```
<span>{</span><span><br>&nbsp; </span><span>"name"</span><span>:</span><span> </span><span>"Action Extension"</span><span>,</span><span><br>&nbsp; </span><span>...</span><span><br>&nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"default_icon"</span><span>:</span><span> </span><span>{</span><span> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</span><span>//</span><span> optional<br>&nbsp; &nbsp; &nbsp; </span><span>"16"</span><span>:</span><span> </span><span>"images/icon16.png"</span><span>,</span><span> &nbsp; </span><span>//</span><span> optional<br>&nbsp; &nbsp; &nbsp; </span><span>"24"</span><span>:</span><span> </span><span>"images/icon24.png"</span><span>,</span><span> &nbsp; </span><span>//</span><span> optional<br>&nbsp; &nbsp; &nbsp; </span><span>"32"</span><span>:</span><span> </span><span>"images/icon32.png"</span><span> &nbsp; &nbsp;</span><span>//</span><span> optional<br>&nbsp; &nbsp; </span><span>},</span><span><br>&nbsp; &nbsp; </span><span>"default_title"</span><span>:</span><span> </span><span>"Click Me"</span><span>,</span><span> &nbsp; </span><span>//</span><span> optional</span><span>,</span><span> shown in tooltip<br>&nbsp; &nbsp; </span><span>"default_popup"</span><span>:</span><span> </span><span>"popup.html"</span><span> &nbsp;</span><span>//</span><span> optional<br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>...</span><span><br></span><span>}</span><span><br></span>
```

Клавиша `"action"` (вместе с ее дочерними элементами) не является обязательной. Если оно не включено, ваше расширение по-прежнему отображается на панели инструментов, обеспечивая доступ к меню расширения. По этой причине мы рекомендуем всегда включать как минимум клавиши `"action"` и `"default_icon"` .

## Концепции и использование

### Части пользовательского интерфейса

#### Икона

Значок является основным изображением на панели инструментов вашего расширения и задается ключом `"default_icon"` в ключе `"action"` вашего манифеста. Значки должны иметь ширину и высоту 16 аппаратно-независимых пикселей (DIP).

Ключ `"default_icon"` представляет собой словарь размеров путей к изображениям. Chrome использует эти значки, чтобы выбрать масштаб изображения. Если точное совпадение не найдено, Chrome выбирает наиболее близкий из доступных и масштабирует его в соответствии с изображением, что может повлиять на качество изображения.

Поскольку устройства с менее распространенными коэффициентами масштабирования, такими как 1,5x или 1,2x, становятся все более распространенными, мы рекомендуем вам предоставлять значки разных размеров. Это также защитит ваше расширение от возможных изменений размера отображения значков в будущем. Однако, если указан только один размер, ключу `"default_icon"` также можно задать строку с путем к одному значку вместо словаря.

Вы также можете вызвать `action.setIcon()` чтобы программно установить значок вашего расширения, указав другой путь к изображению или предоставив динамически создаваемый значок с помощью [HTML-элемента холста](https://developer.mozilla.org/docs/Web/API/HTMLCanvasElement) или, если установка выполняется из работника службы расширений, [внеэкранного API холста](https://developer.mozilla.org/docs/Web/API/OffscreenCanvas) .

```
<span>const</span><span> canvas </span><span>=</span><span> </span><span>new</span><span> </span><span>OffscreenCanvas</span><span>(</span><span>16</span><span>,</span><span> </span><span>16</span><span>);</span><span><br></span><span>const</span><span> context </span><span>=</span><span> canvas</span><span>.</span><span>getContext</span><span>(</span><span>'2d'</span><span>);</span><span><br>context</span><span>.</span><span>clearRect</span><span>(</span><span>0</span><span>,</span><span> </span><span>0</span><span>,</span><span> </span><span>16</span><span>,</span><span> </span><span>16</span><span>);</span><span><br>context</span><span>.</span><span>fillStyle </span><span>=</span><span> </span><span>'#00FF00'</span><span>;</span><span> &nbsp;</span><span>// Green</span><span><br>context</span><span>.</span><span>fillRect</span><span>(</span><span>0</span><span>,</span><span> </span><span>0</span><span>,</span><span> </span><span>16</span><span>,</span><span> </span><span>16</span><span>);</span><span><br></span><span>const</span><span> imageData </span><span>=</span><span> context</span><span>.</span><span>getImageData</span><span>(</span><span>0</span><span>,</span><span> </span><span>0</span><span>,</span><span> </span><span>16</span><span>,</span><span> </span><span>16</span><span>);</span><span><br>chrome</span><span>.</span><span>action</span><span>.</span><span>setIcon</span><span>({</span><span>imageData</span><span>:</span><span> imageData</span><span>},</span><span> </span><span>()</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span> </span><span>/* ... */</span><span> </span><span>});</span><span><br></span>
```

Для упакованных расширений (установленных из файла .crx) изображения могут быть в большинстве форматов, которые может отображать механизм рендеринга Blink, включая PNG, JPEG, BMP, ICO и другие. SVG не поддерживается. Распакованные расширения должны использовать изображения PNG.

#### Подсказка (заголовок)

Всплывающая подсказка или заголовок появляется, когда пользователь наводит указатель мыши на значок расширения на панели инструментов. Он также включается в доступный текст, произносимый программами чтения с экрана, когда кнопка получает фокус.

Подсказка по умолчанию задается с использованием поля `"default_title"` клавиши `"action"` в `manifest.json` . Вы также можете установить его программно, вызвав `action.setTitle()` .

#### Значок

Действия могут дополнительно отображать «значок» — небольшой текст, наложенный поверх значка. Это позволяет обновить действие для отображения небольшого объема информации о состоянии расширения, например счетчика. Значок имеет текстовую часть и цвет фона. Поскольку пространство ограничено, мы рекомендуем использовать в тексте значка четыре или менее символов.

Чтобы создать значок, установите его программно, вызвав `action.setBadgeBackgroundColor()` и `action.setBadgeText()` . В манифесте нет настройки значка по умолчанию. Значения цвета значка могут быть либо массивом из четырех целых чисел от 0 до 255, которые составляют цвет значка RGBA, либо строкой со значением [цвета CSS](https://developer.mozilla.org/docs/Web/CSS/color) .

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>setBadgeBackgroundColor</span><span>(</span><span><br>&nbsp; </span><span>{</span><span>color</span><span>:</span><span> </span><span>[</span><span>0</span><span>,</span><span> </span><span>255</span><span>,</span><span> </span><span>0</span><span>,</span><span> </span><span>0</span><span>]},</span><span> &nbsp;</span><span>// Green</span><span><br>&nbsp; </span><span>()</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span> </span><span>/* ... */</span><span> </span><span>},</span><span><br></span><span>);</span><span><br><br>chrome</span><span>.</span><span>action</span><span>.</span><span>setBadgeBackgroundColor</span><span>(</span><span><br>&nbsp; </span><span>{</span><span>color</span><span>:</span><span> </span><span>'#00FF00'</span><span>},</span><span> &nbsp;</span><span>// Also green</span><span><br>&nbsp; </span><span>()</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span> </span><span>/* ... */</span><span> </span><span>},</span><span><br></span><span>);</span><span><br><br>chrome</span><span>.</span><span>action</span><span>.</span><span>setBadgeBackgroundColor</span><span>(</span><span><br>&nbsp; </span><span>{</span><span>color</span><span>:</span><span> </span><span>'green'</span><span>},</span><span> &nbsp;</span><span>// Also, also green</span><span><br>&nbsp; </span><span>()</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span> </span><span>/* ... */</span><span> </span><span>},</span><span><br></span><span>);</span><span><br></span>
```

Всплывающее окно действия отображается, когда пользователь нажимает кнопку действия расширения на панели инструментов. Всплывающее окно может содержать любое HTML-содержимое, которое вам нравится, и его размер будет автоматически изменен в соответствии с его содержимым. Размер всплывающего окна должен находиться в диапазоне от 25x25 до 800x600 пикселей.

Всплывающее окно изначально задается свойством `"default_popup"` в ключе `"action"` в файле `manifest.json` . Если это свойство присутствует, оно должно указывать на относительный путь в каталоге расширения. Его также можно динамически обновлять, чтобы он указывал на другой относительный путь, используя метод `action.setPopup()` .

## Варианты использования

### Состояние на вкладке

Действия расширения могут иметь разные состояния для каждой вкладки. Чтобы установить значение для отдельной вкладки, используйте свойство `tabId` в методах настройки API `action` . Например, чтобы установить текст значка для определенной вкладки, сделайте следующее:

```
<span>function</span><span> getTabId</span><span>()</span><span> </span><span>{</span><span> </span><span>/* ... */</span><span>}</span><span><br></span><span>function</span><span> getTabBadge</span><span>()</span><span> </span><span>{</span><span> </span><span>/* ... */</span><span>}</span><span><br><br>chrome</span><span>.</span><span>action</span><span>.</span><span>setBadgeText</span><span>(</span><span><br>&nbsp; </span><span>{</span><span><br>&nbsp; &nbsp; text</span><span>:</span><span> getTabBadge</span><span>(</span><span>tabId</span><span>),</span><span><br>&nbsp; &nbsp; tabId</span><span>:</span><span> getTabId</span><span>(),</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>()</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span> </span><span>...</span><span> </span><span>}</span><span><br></span><span>);</span><span><br></span>
```

Если свойство `tabId` опущено, этот параметр рассматривается как глобальный. Настройки, относящиеся к вкладкам, имеют приоритет над глобальными настройками.

### Включенное состояние

По умолчанию действия панели инструментов включены (кликабельны) на каждой вкладке. Вы можете контролировать это с помощью методов `action.enable()` и `action.disable()` . Это влияет только на то, будет ли всплывающее окно (если оно есть) или событие `action.onClicked` отправлено на ваше расширение; это не влияет на присутствие действия на панели инструментов.

## Примеры

В следующих примерах показаны некоторые распространенные способы использования действий в расширениях. Чтобы попробовать этот API, установите [пример Action API](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/api-samples/action) из репозитория [chrome-extension-samples](https://github.com/GoogleChrome/chrome-extensions-samples) .

Обычно расширение отображает всплывающее окно, когда пользователь щелкает действие расширения. Чтобы реализовать это в своем собственном расширении, объявите всплывающее окно в `manifest.json` и укажите содержимое, которое Chrome должен отображать во всплывающем окне.

```
<span>//</span><span> manifest</span><span>.</span><span>json<br></span><span>{</span><span><br>&nbsp; </span><span>"name"</span><span>:</span><span> </span><span>"Action popup demo"</span><span>,</span><span><br>&nbsp; </span><span>"version"</span><span>:</span><span> </span><span>"1.0"</span><span>,</span><span><br>&nbsp; </span><span>"manifest_version"</span><span>:</span><span> </span><span>3</span><span>,</span><span><br>&nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"default_title"</span><span>:</span><span> </span><span>"Click to view a popup"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"default_popup"</span><span>:</span><span> </span><span>"popup.html"</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

```
<span>&lt;!-- popup.html --&gt;</span><span><br></span><span>&lt;!DOCTYPE html&gt;</span><span><br></span><span>&lt;html&gt;</span><span><br></span><span>&lt;head&gt;</span><span><br>&nbsp; </span><span>&lt;style&gt;</span><span><br>&nbsp; &nbsp; html </span><span>{</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>min-height</span><span>:</span><span> </span><span>5em</span><span>;</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>min-width</span><span>:</span><span> </span><span>10em</span><span>;</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>background</span><span>:</span><span> salmon</span><span>;</span><span><br>&nbsp; &nbsp; </span><span>}</span><span><br>&nbsp; </span><span>&lt;/style&gt;</span><span><br></span><span>&lt;/head&gt;</span><span><br></span><span>&lt;body&gt;</span><span><br>&nbsp; </span><span>&lt;p&gt;</span><span>Hello, world!</span><span>&lt;/p&gt;</span><span><br></span><span>&lt;/body&gt;</span><span><br></span><span>&lt;/html&gt;</span><span><br></span>
```

### Внедрить скрипт контента при клике

Распространенным шаблоном для расширений является раскрытие своей основной функции с помощью действия расширения. Следующий пример демонстрирует эту закономерность. Когда пользователь нажимает на действие, расширение вставляет сценарий содержимого на текущую страницу. Затем сценарий содержимого отображает предупреждение, чтобы убедиться, что все работает должным образом.

```
<span>//</span><span> manifest</span><span>.</span><span>json<br></span><span>{</span><span><br>&nbsp; </span><span>"name"</span><span>:</span><span> </span><span>"Action script injection demo"</span><span>,</span><span><br>&nbsp; </span><span>"version"</span><span>:</span><span> </span><span>"1.0"</span><span>,</span><span><br>&nbsp; </span><span>"manifest_version"</span><span>:</span><span> </span><span>3</span><span>,</span><span><br>&nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"default_title"</span><span>:</span><span> </span><span>"Click to show an alert"</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>"permissions"</span><span>:</span><span> </span><span>[</span><span>"activeTab"</span><span>,</span><span> </span><span>"scripting"</span><span>],</span><span><br>&nbsp; </span><span>"background"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"service_worker"</span><span>:</span><span> </span><span>"background.js"</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

```
<span>// background.js</span><span><br>chrome</span><span>.</span><span>action</span><span>.</span><span>onClicked</span><span>.</span><span>addListener</span><span>((</span><span>tab</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; chrome</span><span>.</span><span>scripting</span><span>.</span><span>executeScript</span><span>({</span><span><br>&nbsp; &nbsp; target</span><span>:</span><span> </span><span>{</span><span>tabId</span><span>:</span><span> tab</span><span>.</span><span>id</span><span>},</span><span><br>&nbsp; &nbsp; files</span><span>:</span><span> </span><span>[</span><span>'content.js'</span><span>]</span><span><br>&nbsp; </span><span>});</span><span><br></span><span>});</span><span><br></span>
```

```
<span>// content.js</span><span><br>alert</span><span>(</span><span>'Hello, world!'</span><span>);</span><span><br></span>
```

### Эмулируйте действия с помощью declarativeContent

В этом примере показано, как фоновая логика расширения может (а) отключить действие по умолчанию и (б) использовать [declarativeContent](https://developer.chrome.com/docs/extensions/reference/api/declarativeContent?hl=ru) для включения действия на определенных сайтах.

```
<span>// service-worker.js</span><span><br><br></span><span>// Wrap in an onInstalled callback to avoid unnecessary work</span><span><br></span><span>// every time the service worker is run</span><span><br>chrome</span><span>.</span><span>runtime</span><span>.</span><span>onInstalled</span><span>.</span><span>addListener</span><span>(()</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; </span><span>// Page actions are disabled by default and enabled on select tabs</span><span><br>&nbsp; chrome</span><span>.</span><span>action</span><span>.</span><span>disable</span><span>();</span><span><br><br>&nbsp; </span><span>// Clear all rules to ensure only our expected rules are set</span><span><br>&nbsp; chrome</span><span>.</span><span>declarativeContent</span><span>.</span><span>onPageChanged</span><span>.</span><span>removeRules</span><span>(</span><span>undefined</span><span>,</span><span> </span><span>()</span><span> </span><span>=&gt;</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>// Declare a rule to enable the action on example.com pages</span><span><br>&nbsp; &nbsp; let exampleRule </span><span>=</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; &nbsp; conditions</span><span>:</span><span> </span><span>[</span><span><br>&nbsp; &nbsp; &nbsp; &nbsp; </span><span>new</span><span> chrome</span><span>.</span><span>declarativeContent</span><span>.</span><span>PageStateMatcher</span><span>({</span><span><br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pageUrl</span><span>:</span><span> </span><span>{</span><span>hostSuffix</span><span>:</span><span> </span><span>'.example.com'</span><span>},</span><span><br>&nbsp; &nbsp; &nbsp; &nbsp; </span><span>})</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>],</span><span><br>&nbsp; &nbsp; &nbsp; actions</span><span>:</span><span> </span><span>[</span><span>new</span><span> chrome</span><span>.</span><span>declarativeContent</span><span>.</span><span>ShowAction</span><span>()],</span><span><br>&nbsp; &nbsp; </span><span>};</span><span><br><br>&nbsp; &nbsp; </span><span>// Finally, apply our new array of rules</span><span><br>&nbsp; &nbsp; let rules </span><span>=</span><span> </span><span>[</span><span>exampleRule</span><span>];</span><span><br>&nbsp; &nbsp; chrome</span><span>.</span><span>declarativeContent</span><span>.</span><span>onPageChanged</span><span>.</span><span>addRules</span><span>(</span><span>rules</span><span>);</span><span><br>&nbsp; </span><span>});</span><span><br></span><span>});</span><span><br></span>
```

## Типы

#### Характеристики

-   Идентификатор окна, в котором открывается всплывающее окно действия. По умолчанию используется активное в данный момент окно, если не указано.
    

### TabDetails

#### Характеристики

-   идентификатор табуляции
    
    номер необязательно
    
    Идентификатор вкладки, для которой требуется запросить состояние. Если вкладка не указана, возвращается состояние, не зависящее от вкладки.
    

### UserSettings

Коллекция пользовательских настроек, относящихся к действию расширения.

#### Характеристики

-   isOnToolbar
    
    логическое значение
    
    Виден ли значок действия расширения на панели инструментов верхнего уровня окон браузера (т. е. было ли расширение «закреплено» пользователем).
    

### UserSettingsChange

#### Характеристики

-   isOnToolbar
    
    логическое значение необязательно
    
    Виден ли значок действия расширения на панели инструментов верхнего уровня окон браузера (т. е. было ли расширение «закреплено» пользователем).
    

## Методы

### disable()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>disable</span><span>(</span><span><br>&nbsp; tabId</span><span>?:</span><span> number</span><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Отключает действие для вкладки.

#### Параметры

-   идентификатор табуляции
    
    номер необязательно
    
    Идентификатор вкладки, для которой вы хотите изменить действие.
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### enable()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>enable</span><span>(</span><span><br>&nbsp; tabId</span><span>?:</span><span> number</span><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Включает действие для вкладки. По умолчанию действия включены.

#### Параметры

-   идентификатор табуляции
    
    номер необязательно
    
    Идентификатор вкладки, для которой вы хотите изменить действие.
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### getBadgeBackgroundColor()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>getBadgeBackgroundColor</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-TabDetails"><span>TabDetails</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Получает цвет фона действия.

#### Параметры

-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>result</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/browserAction/?hl=ru#type-ColorArray"><span>ColorArray</span></a><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### getBadgeText()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>getBadgeText</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-TabDetails"><span>TabDetails</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Получает текст значка действия. Если вкладка не указана, возвращается текст значка, не относящийся к вкладке. Если [displayActionCountAsBadgeText](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest/?hl=ru#setExtensionActionOptions) включен, будет возвращен текст-заполнитель, если не присутствует разрешение [declarativeNetRequestFeedback](https://developer.chrome.com/docs/extensions/develop/concepts/declare-permissions?hl=ru#declarativeNetRequestFeedback) или не предоставлен текст значка для конкретной вкладки.

#### Параметры

-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>result</span><span>:</span><span> </span><span>string</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### getBadgeTextColor()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>getBadgeTextColor</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-TabDetails"><span>TabDetails</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Получает цвет текста действия.

#### Параметры

-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>result</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/browserAction/?hl=ru#type-ColorArray"><span>ColorArray</span></a><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>getPopup</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-TabDetails"><span>TabDetails</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Получает HTML-документ, установленный в качестве всплывающего окна для этого действия.

#### Параметры

-   Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>result</span><span>:</span><span> </span><span>string</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### getTitle()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>getTitle</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-TabDetails"><span>TabDetails</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Получает название действия.

#### Параметры

-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>result</span><span>:</span><span> </span><span>string</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### getUserSettings()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>getUserSettings</span><span>(</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Возвращает заданные пользователем настройки, относящиеся к действию расширения.

#### Параметры

-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>userSettings</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-UserSettings"><span>UserSettings</span></a><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    
    -   пользовательские настройки
        
    

#### Возврат

-   Обещание < [Настройки пользователя](https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-UserSettings) >
    
    Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### isEnabled()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>isEnabled</span><span>(</span><span><br>&nbsp; tabId</span><span>?:</span><span> number</span><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Указывает, включено ли действие расширения для вкладки (или глобально, если `tabId` не указан). Действия, включенные с использованием только [`declarativeContent`](https://developer.chrome.com/docs/extensions/reference/declarativeContent/?hl=ru) всегда возвращают значение false.

#### Параметры

-   идентификатор табуляции
    
    номер необязательно
    
    Идентификатор вкладки, для которой вы хотите проверить включенный статус.
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>isEnabled</span><span>:</span><span> </span><span>boolean</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    
    -   isEnabled
        
        логическое значение
        
        True, если действие расширения включено.
        
    

#### Возврат

-   Обещание <логическое значение>
    
    Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>openPopup</span><span>(</span><span><br>&nbsp; options</span><span>?:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-OpenPopupOptions"><span>OpenPopupOptions</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Открывает всплывающее окно расширения. В версиях Chrome 118 и Chrome 126 это доступно только для расширений, установленных политикой.

#### Параметры

-   [OpenPopupOptions](https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-OpenPopupOptions) необязательно
    
    Указывает параметры открытия всплывающего окна.
    
-   Параметр `callback` выглядит так:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### setBadgeBackgroundColor()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>setBadgeBackgroundColor</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><span>object</span><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Устанавливает цвет фона для значка.

#### Параметры

-   -   Массив из четырех целых чисел в диапазоне \[0,255\], составляющих цвет значка RGBA. Например, непрозрачный красный — это `[255, 0, 0, 255]` . Также может быть строкой со значением CSS, где непрозрачный красный — `#FF0000` или `#F00` .
        
    -   идентификатор табуляции
        
        номер необязательно
        
        Ограничивает изменение моментом выбора определенной вкладки. Автоматически сбрасывается при закрытии вкладки.
        
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### setBadgeText()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>setBadgeText</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><span>object</span><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Устанавливает текст значка для действия. Значок отображается поверх значка.

#### Параметры

-   -   идентификатор табуляции
        
        номер необязательно
        
        Ограничивает изменение моментом выбора определенной вкладки. Автоматически сбрасывается при закрытии вкладки.
        
    -   текст
        
        строка необязательна
        
        Можно передать любое количество символов, но в пространстве поместится только около четырех. Если передается пустая строка ( `''` ), текст значка очищается. Если указан `tabId` и `text` имеет значение NULL, текст указанной вкладки очищается и по умолчанию используется текст глобального значка.
        
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### setBadgeTextColor()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>setBadgeTextColor</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><span>object</span><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Устанавливает цвет текста для значка.

#### Параметры

-   -   Массив из четырех целых чисел в диапазоне \[0,255\], составляющих цвет значка RGBA. Например, непрозрачный красный — это `[255, 0, 0, 255]` . Также может быть строкой со значением CSS, где непрозрачный красный цвет — `#FF0000` или `#F00` . Если вы не установите это значение, будет автоматически выбран цвет, который будет контрастировать с цветом фона значка, поэтому текст будет виден. Цвета со значениями альфа, равными 0, не будут установлены и вернут ошибку.
        
    -   идентификатор табуляции
        
        номер необязательно
        
        Ограничивает изменение моментом выбора определенной вкладки. Автоматически сбрасывается при закрытии вкладки.
        
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### setIcon()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>setIcon</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><span>object</span><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Устанавливает значок для действия. Значок можно указать либо как путь к файлу изображения, либо как данные пикселей из элемента холста, либо как словарь любого из них. Необходимо указать либо **путь** , либо свойство **imageData** .

#### Параметры

-   -   данные изображения
        
        Данные изображения | объект необязательный
        
        Либо объект ImageData, либо словарь {size -> ImageData}, представляющий устанавливаемый значок. Если значок указан как словарь, фактическое изображение, которое будет использоваться, выбирается в зависимости от плотности пикселей экрана. Если количество пикселей изображения, помещающихся в одну единицу экранного пространства, равно `scale` , то будет выбрано изображение с размером `scale` \* n, где n — размер значка в пользовательском интерфейсе. Необходимо указать хотя бы одно изображение. Обратите внимание, что 'details.imageData = foo' эквивалентно 'details.imageData = {'16': foo}'
        
    -   путь
        
        строка | объект необязательный
        
        Либо относительный путь к изображению, либо словарь {размер → относительный путь к изображению}, указывающий на устанавливаемый значок. Если значок указан как словарь, фактическое изображение, которое будет использоваться, выбирается в зависимости от плотности пикселей экрана. Если количество пикселей изображения, помещающихся в одну единицу экранного пространства, равно `scale` , то будет выбрано изображение с размером `scale` \* n, где n — размер значка в пользовательском интерфейсе. Необходимо указать хотя бы одно изображение. Обратите внимание, что 'details.path = foo' эквивалентен 'details.path = {'16': foo}'.
        
    -   идентификатор табуляции
        
        номер необязательно
        
        Ограничивает изменение моментом выбора определенной вкладки. Автоматически сбрасывается при закрытии вкладки.
        
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>setPopup</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><span>object</span><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Устанавливает HTML-документ, который будет открываться во всплывающем окне, когда пользователь щелкает значок действия.

#### Параметры

-   -   Относительный путь к HTML-файлу, который будет отображаться во всплывающем окне. Если установлена пустая строка ( `''` ), всплывающее окно не отображается.
        
    -   Ограничивает изменение моментом выбора определенной вкладки. Автоматически сбрасывается при закрытии вкладки.
        
    
-   Параметр `callback` выглядит так:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### setTitle()

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>setTitle</span><span>(</span><span><br>&nbsp; details</span><span>:</span><span> </span><span>object</span><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Устанавливает название действия. Это отображается во всплывающей подсказке.

#### Параметры

-   -   идентификатор табуляции
        
        номер необязательно
        
        Ограничивает изменение моментом выбора определенной вкладки. Автоматически сбрасывается при закрытии вкладки.
        
    -   Строка, которую действие должно отображать при наведении курсора мыши.
        
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

## События

### onClicked

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>onClicked</span><span>.</span><span>addListener</span><span>(</span><span><br>&nbsp; callback</span><span>:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Запускается при нажатии значка действия. Это событие не сработает, если у действия есть всплывающее окно.

#### Параметры

-   Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>tab</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/tabs/?hl=ru#type-Tab"><span>tabs</span><span>.</span><span>Tab</span></a><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

### onUserSettingsChanged

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>onUserSettingsChanged</span><span>.</span><span>addListener</span><span>(</span><span><br>&nbsp; callback</span><span>:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Вызывается, когда изменяются заданные пользователем настройки, относящиеся к действию расширения.

#### Параметры

-   Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>change</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru#type-UserSettingsChange"><span>UserSettingsChange</span></a><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

Если не указано иное, контент на этой странице предоставляется по [лицензии Creative Commons "С указанием авторства 4.0"](https://creativecommons.org/licenses/by/4.0/), а примеры кода – по [лицензии Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0). Подробнее об этом написано в [правилах сайта](https://developers.google.com/site-policies?hl=ru). Java – это зарегистрированный товарный знак корпорации Oracle и ее аффилированных лиц.

Последнее обновление: 2025-01-05 UTC.
