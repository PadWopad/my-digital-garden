---
{"dg-publish":true,"created":"2025-01-31T16:47:25 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru","author":null,"permalink":"/proekty/extentions/chrome-side-panel-api-chrome-for-developers/","dgPassFrontmatter":true}
---


# chrome.sidePanel  |  API  |  Chrome for Developers

> ## Excerpt
> Используйте API chrome.sidePanel для размещения контента на боковой панели браузера рядом с основным содержимым веб-страницы.

---
Используйте API `chrome.sidePanel` для размещения контента на боковой панели браузера рядом с основным содержимым веб-страницы.

## Разрешения

`sidePanel`  

Чтобы использовать API боковой панели, добавьте разрешение `"sidePanel"` в файл [манифеста](https://developer.chrome.com/docs/extensions/reference/manifest?hl=ru) расширения:

манифест.json:

```
<span>{</span>
<span>  </span>"<span>na</span><span>me</span>"<span>:</span><span> </span>"<span>My</span><span> </span><span>side</span><span> </span><span>pa</span><span>nel</span><span> </span><span>ex</span><span>tens</span><span>io</span><span>n</span>"<span>,</span>
<span>  </span><span>...</span>
<span>  </span>"<span>permissio</span><span>ns</span>"<span>:</span><span> </span><span>[</span>
<span>    </span>"<span>sidePa</span><span>nel</span>"
<span>  </span><span>]</span>
<span>}</span>
```

## Доступность

## Концепции и использование

API боковой панели позволяет расширениям отображать собственный пользовательский интерфейс на боковой панели, обеспечивая постоянное взаимодействие, дополняющее путешествие пользователя в Интернете.

![Выпадающее меню боковой панели](https://developer.chrome.com/static/docs/extensions/reference/api/sidePanel/images/example-side-panel.png?hl=ru)

Пользовательский интерфейс боковой панели браузера Chrome.

Некоторые функции включают в себя:

-   Боковая панель остается открытой при переходе между вкладками (если это разрешено).
-   Он может быть доступен только на определенных сайтах.
-   В качестве страницы расширения боковые панели имеют доступ ко всем API Chrome.
-   В настройках Chrome пользователи могут указать, на какой стороне должна отображаться панель.

### Варианты использования

В следующих разделах демонстрируются некоторые распространенные случаи использования API боковой панели. Полные [примеры расширений](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#examples) см. в разделе «Примеры расширений».

#### Отображать одну и ту же боковую панель на каждом сайте

Боковую панель можно изначально настроить с помощью свойства `"default_path"` в ключе `"side_panel"` манифеста, чтобы отображать одну и ту же боковую панель на каждом сайте. Это должно указывать на относительный путь в каталоге расширения.

манифест.json:

```
<span>{</span>
<span>  </span>"<span>na</span><span>me</span>"<span>:</span><span> </span>"<span>My</span><span> </span><span>side</span><span> </span><span>pa</span><span>nel</span><span> </span><span>ex</span><span>tens</span><span>io</span><span>n</span>"<span>,</span>
<span>  </span><span>...</span>
<span>  </span>"<span>side_pa</span><span>nel</span>"<span>:</span><span> </span><span>{</span>
<span>    </span>"<span>de</span><span>fault</span><span>_pa</span><span>t</span><span>h</span>"<span>:</span><span> </span>"<span>sidepa</span><span>nel</span><span>.h</span><span>t</span><span>ml</span>"
<span>  </span><span>}</span>
<span>  </span><span>...</span>
<span>}</span>
```

боковая панель.html:

```
&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;title&gt;My Sidepanel&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;h1&gt;All sites sidepanel extension&lt;/h1&gt;
    &lt;p&gt;This side panel is enabled on all sites&lt;/p&gt;
  &lt;/body&gt;
&lt;/html&gt;
```

#### Включить боковую панель на определенном сайте

Расширение может использовать [`sidepanel.setOptions()`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#method-setOptions) чтобы включить боковую панель на определенной вкладке. В этом примере используется [`chrome.tabs.onUpdated()`](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=ru#event-onUpdated) для прослушивания любых обновлений, вносимых на вкладку. Он проверяет, является ли URL-адрес [www.google.com](https://www.google.com/?hl=ru) , и включает боковую панель. В противном случае он отключает его.

сервис-worker.js:

```
<span>const</span><span> </span><span>GOOGLE_ORIGIN</span><span> </span><span>=</span><span> </span>'<span>https</span><span>:</span><span>//www.google.com';</span>

<span>chrome</span><span>.</span><span>tabs</span><span>.</span><span>onUpdated</span><span>.</span><span>addListener</span><span>(</span><span>async</span><span> </span><span>(</span><span>tabId</span><span>,</span><span> </span><span>info</span><span>,</span><span> </span><span>tab</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>if</span><span> </span><span>(</span><span>!</span><span>tab</span><span>.</span><span>url</span><span>)</span><span> </span><span>return</span><span>;</span>
<span>  </span><span>const</span><span> </span><span>url</span><span> </span><span>=</span><span> </span><span>new</span><span> </span><span>URL</span><span>(</span><span>tab</span><span>.</span><span>url</span><span>);</span>
<span>  </span><span>// Enables the side panel on google.com</span>
<span>  </span><span>if</span><span> </span><span>(</span><span>url</span><span>.</span><span>origin</span><span> </span><span>===</span><span> </span><span>GOOGLE_ORIGIN</span><span>)</span><span> </span><span>{</span>
<span>    </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>setOptions</span><span>({</span>
<span>      </span><span>tabId</span><span>,</span>
<span>      </span><span>path</span><span>:</span><span> </span>'<span>sidepanel</span><span>.</span><span>html</span>'<span>,</span>
<span>      </span><span>enabled</span><span>:</span><span> </span><span>true</span>
<span>    </span><span>});</span>
<span>  </span><span>}</span><span> </span><span>else</span><span> </span><span>{</span>
<span>    </span><span>// Disables the side panel on all other sites</span>
<span>    </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>setOptions</span><span>({</span>
<span>      </span><span>tabId</span><span>,</span>
<span>      </span><span>enabled</span><span>:</span><span> </span><span>false</span>
<span>    </span><span>});</span>
<span>  </span><span>}</span>
<span>});</span>
```

Когда пользователь временно переключается на вкладку, где боковая панель не включена, боковая панель будет скрыта. Он автоматически отобразится снова, когда пользователь перейдет на вкладку, где он был открыт ранее.

Когда пользователь переходит на сайт, где боковая панель не включена, боковая панель закроется, и расширение не будет отображаться в раскрывающемся меню боковой панели.

Полный пример см. в примере [боковой панели для вкладок](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/cookbook.sidepanel-site-specific) .

#### Откройте боковую панель, щелкнув значок на панели инструментов.

Разработчики могут разрешить пользователям открывать боковую панель, когда они щелкают значок панели действий с помощью [`sidePanel.setPanelBehavior()`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#method-setPanelBehavior) . Сначала объявите ключ `"action"` в манифесте:

манифест.json:

```
{
  "name": "My side panel extension",
  ...
  "action": {
    "default_title": "Click to open panel"
  },
  ...
}
```

Теперь добавьте этот код к предыдущему примеру:

сервис-worker.js:

```
<span>const</span><span> </span><span>GOOGLE_ORIGIN</span><span> </span><span>=</span><span> </span>'<span>https</span><span>:</span><span>//www.google.com';</span>

<span>// Allows users to open the side panel by clicking on the action toolbar icon</span>
<span>chrome</span><span>.</span><span>sidePanel</span>
<span>  </span><span>.</span><span>setPanelBehavior</span><span>({</span><span> </span><span>openPanelOnActionClick</span><span>:</span><span> </span><span>true</span><span> </span><span>})</span>
<span>  </span><span>.</span><span>catch</span><span>((</span><span>error</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>console</span><span>.</span><span>error</span><span>(</span><span>error</span><span>));</span>
<span>...</span>
```

#### Программно открыть боковую панель при взаимодействии с пользователем

В Chrome 116 представлен [`sidePanel.open()`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#method-open) . Он позволяет расширениям открывать боковую панель с помощью жеста пользователя расширения, например [щелчка по значку действия](https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru) . Или взаимодействие пользователя на странице расширения или [скрипте контента](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru) , например нажатие кнопки. Полную демонстрацию см. в примере расширения [Open Side Panel](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/cookbook.sidepanel-open) .

Следующий код показывает, как открыть глобальную боковую панель в текущем окне, когда пользователь щелкает контекстное меню. При использовании [`sidePanel.open()`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#method-open) вы должны выбрать контекст, в котором он должен открываться. Используйте [`windowId`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#property-OpenOptions-windowId) , чтобы открыть глобальную боковую панель. Альтернативно, установите [`tabId`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#property-OpenOptions-tabId) , чтобы боковая панель открывалась только на определенной вкладке.

сервис-worker.js:

```
<span>chrome</span><span>.</span><span>runtime</span><span>.</span><span>onInstalled</span><span>.</span><span>addListener</span><span>(()</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>chrome</span><span>.</span><span>contextMenus</span><span>.</span><span>create</span><span>(</span><span>{</span>
<span>    </span><span>id</span><span>:</span><span> </span>'<span>openSidePanel</span>'<span>,</span>
<span>    </span><span>title</span><span>:</span><span> </span>'<span>Open</span><span> </span><span>side</span><span> </span><span>panel</span>'<span>,</span>
<span>    </span><span>contexts</span><span>:</span><span> </span><span>[</span>'<span>all</span>'<span>]</span>
<span>  </span><span>}</span><span>);</span>
<span>}</span><span>);</span>

<span>chrome</span><span>.</span><span>contextMenus</span><span>.</span><span>onClicked</span><span>.</span><span>addListener</span><span>((</span><span>info</span><span>,</span><span> </span><span>tab</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>if</span><span> </span><span>(</span><span>info</span><span>.</span><span>menuItemId</span><span> </span><span>===</span><span> </span>'<span>openSidePanel</span>'<span>)</span><span> </span><span>{</span>
<span>    </span><span>//</span><span> </span><span>This</span><span> </span><span>will</span><span> </span><span>open</span><span> </span><span>the</span><span> </span><span>panel</span><span> </span><span>in</span><span> </span><span>all</span><span> </span><span>the</span><span> </span><span>pages</span><span> </span><span>on</span><span> </span><span>the</span><span> </span><span>current</span><span> </span><span>window</span><span>.</span>
<span>    </span><span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>open</span><span>(</span><span>{</span><span> </span><span>windowId</span><span>:</span><span> </span><span>tab</span><span>.</span><span>windowId</span><span> </span><span>}</span><span>);</span>
<span>  </span><span>}</span>
<span>}</span><span>);</span>
```

#### Переключиться на другую панель

Расширения могут использовать [`sidepanel.getOptions()`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#method-getOptions) для получения текущей боковой панели. В следующем примере устанавливается боковая панель приветствия в [`runtime.onInstalled()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#event-onInstalled) . Затем, когда пользователь переходит на другую вкладку, она заменяется основной боковой панелью.

сервис-worker.js:

```
<span>const</span><span> </span><span>welcomePage</span><span> </span><span>=</span><span> </span>'<span>sidepanels</span><span>/</span><span>welcome</span><span>-</span><span>sp</span><span>.</span><span>html</span>'<span>;</span>
<span>const</span><span> </span><span>mainPage</span><span> </span><span>=</span><span> </span>'<span>sidepanels</span><span>/</span><span>main</span><span>-</span><span>sp</span><span>.</span><span>html</span>'<span>;</span>

<span>chrome</span><span>.</span><span>runtime</span><span>.</span><span>onInstalled</span><span>.</span><span>addListener</span><span>(()</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>setOptions</span><span>({</span><span> </span><span>path</span><span>:</span><span> </span><span>welcomePage</span><span> </span><span>});</span>
<span>  </span><span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>setPanelBehavior</span><span>({</span><span> </span><span>openPanelOnActionClick</span><span>:</span><span> </span><span>true</span><span> </span><span>});</span>
<span>});</span>

<span>chrome</span><span>.</span><span>tabs</span><span>.</span><span>onActivated</span><span>.</span><span>addListener</span><span>(</span><span>async</span><span> </span><span>({</span><span> </span><span>tabId</span><span> </span><span>})</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>const</span><span> </span><span>{</span><span> </span><span>path</span><span> </span><span>}</span><span> </span><span>=</span><span> </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>getOptions</span><span>({</span><span> </span><span>tabId</span><span> </span><span>});</span>
<span>  </span><span>if</span><span> </span><span>(</span><span>path</span><span> </span><span>===</span><span> </span><span>welcomePage</span><span>)</span><span> </span><span>{</span>
<span>    </span><span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>setOptions</span><span>({</span><span> </span><span>path</span><span>:</span><span> </span><span>mainPage</span><span> </span><span>});</span>
<span>  </span><span>}</span>
<span>});</span>
```

Полный код см. в образце [«Несколько боковых панелей»](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/cookbook.sidepanel-multiple) .

### Пользовательский интерфейс боковой панели

Сначала пользователи увидят встроенные боковые панели Chrome. На каждой боковой панели в меню боковой панели отображается значок расширения. Если значки не включены, будет отображаться значок-заполнитель с первой буквой имени расширения.

#### Откройте боковую панель

Чтобы разрешить пользователям открывать боковую панель, используйте значок действия в сочетании с [`sidePanel.setPanelBehavior()`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#open-action-icon) . Альтернативно, вызовите [`sidePanel.open()`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#user-interaction) после взаимодействия с пользователем, например:

-   [Щелчок действия](https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru)
-   [Сочетание клавиш](https://developer.chrome.com/docs/extensions/reference/api/commands?hl=ru)
-   [Контекстное меню](https://developer.chrome.com/docs/extensions/reference/api/contextMenus?hl=ru)
-   [Жест пользователя](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#user-interaction) на странице расширения или скрипте контента.

#### Закрепите боковую панель

![Значок закрепления в пользовательском интерфейсе на боковой панели.](https://developer.chrome.com/static/docs/extensions/reference/api/sidePanel/images/side-panel-pin.png?hl=ru)

Значок закрепления в пользовательском интерфейсе на боковой панели.

На панели инструментов боковой панели отображается значок булавки, когда боковая панель открыта. При нажатии на значок закрепляется значок действия вашего расширения. Нажатие на закрепленный значок действия приведет к выполнению действия по умолчанию для вашего значка действия и откроет боковую панель только в том случае, если это было явно настроено.

## Примеры

Для получения дополнительных демонстраций расширений API боковой панели изучите любое из следующих расширений:

-   [Боковая панель словаря](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/sample.sidepanel-dictionary) .
-   [Глобальная боковая панель](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/cookbook.sidepanel-global) .
-   [Несколько боковых панелей](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/cookbook.sidepanel-multiple) .
-   [Откройте боковую панель](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/cookbook.sidepanel-open) .
-   [Боковая панель для конкретного сайта](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/cookbook.sidepanel-site-specific) .

## Типы

### GetPanelOptions

#### Характеристики

-   идентификатор табуляции
    
    номер необязательно
    
    Если указано, будут возвращены параметры боковой панели для данной вкладки. В противном случае возвращаются параметры боковой панели по умолчанию (используются для любой вкладки, не имеющей определенных настроек).
    

### OpenOptions

#### Характеристики

-   идентификатор табуляции
    
    номер необязательно
    
    Вкладка, в которой открывается боковая панель. Если соответствующая вкладка имеет боковую панель для конкретной вкладки, панель будет открыта только для этой вкладки. Если панель для конкретной вкладки отсутствует, глобальная панель будет открыта на указанной вкладке и на любых других вкладках без открытой в данный момент панели для конкретной вкладки. Это переопределит любую активную в данный момент боковую панель (глобальную или для конкретной вкладки) на соответствующей вкладке. Необходимо указать хотя бы одно из значений this или `windowId` .
    
-   идентификатор окна
    
    номер необязательно
    
    Окно, в котором открывается боковая панель. Это применимо только в том случае, если расширение имеет глобальную (не зависящую от вкладок) боковую панель или также указан `tabId` . Это переопределит любую активную в данный момент глобальную боковую панель, которую пользователь открыл в данном окне. Должен быть указан хотя бы один из значений this или `tabId` .
    

### PanelBehavior

#### Характеристики

-   опенпанельонактионклик
    
    логическое значение необязательно
    
    Будет ли щелчок по значку расширения включать отображение записи о расширении на боковой панели. По умолчанию ложь.
    

### PanelOptions

#### Характеристики

-   включено
    
    логическое значение необязательно
    
    Должна ли быть включена боковая панель. Это необязательно. Значение по умолчанию — true.
    
-   путь
    
    строка необязательна
    
    Путь к используемому HTML-файлу боковой панели. Это должен быть локальный ресурс в пакете расширения.
    
-   идентификатор табуляции
    
    номер необязательно
    
    Если указано, параметры боковой панели будут применяться только к вкладке с этим идентификатором. Если они опущены, эти параметры задают поведение по умолчанию (используется для любой вкладки, не имеющей определенных настроек). Примечание. Если для этого tabId и tabId по умолчанию задан один и тот же путь, то панель для этого tabId будет другим экземпляром, чем панель для tabId по умолчанию.
    

### SidePanel

#### Характеристики

-   Путь, указанный разработчиком для отображения боковой панели.
    

## Методы

### getOptions()

```
<span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>getOptions</span><span>(</span><br>&nbsp;&nbsp;<span>options</span><span>:</span>&nbsp;<a href="https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#type-GetPanelOptions"><span>GetPanelOptions</span></a><span>,</span><br>&nbsp;&nbsp;<span>callback?</span><span>:</span>&nbsp;<span>function</span><span>,<br>)</span>
```

Возвращает конфигурацию активной панели.

#### Параметры

-   Указывает контекст, для которого возвращается конфигурация.
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>options</span><span>:</span>&nbsp;<a href="https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#type-PanelOptions"><span>PanelOptions</span></a><span>)&nbsp;=&gt;</span>&nbsp;<span>void</span>
    ```
    

#### Возврат

-   Обещание< [Параметры панели](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#type-PanelOptions) >
    
    Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### getPanelBehavior()

```
<span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>getPanelBehavior</span><span>(</span><br>&nbsp;&nbsp;<span>callback?</span><span>:</span>&nbsp;<span>function</span><span>,<br>)</span>
```

Возвращает текущее поведение боковой панели расширения.

#### Параметры

-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>(</span><span>behavior</span><span>:</span>&nbsp;<a href="https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#type-PanelBehavior"><span>PanelBehavior</span></a><span>)&nbsp;=&gt;</span>&nbsp;<span>void</span>
    ```
    

#### Возврат

-   Обещание < [PanelBehavior](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#type-PanelBehavior) >
    
    Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### open()

```
<span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>open</span><span>(</span><br>&nbsp;&nbsp;<span>options</span><span>:</span>&nbsp;<a href="https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#type-OpenOptions"><span>OpenOptions</span></a><span>,</span><br>&nbsp;&nbsp;<span>callback?</span><span>:</span>&nbsp;<span>function</span><span>,<br>)</span>
```

Открывает боковую панель расширения. Это может быть вызвано только в ответ на действие пользователя.

#### Параметры

-   Указывает контекст, в котором открывается боковая панель.
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()&nbsp;=&gt;</span>&nbsp;<span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### setOptions()

```
<span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>setOptions</span><span>(</span><br>&nbsp;&nbsp;<span>options</span><span>:</span>&nbsp;<a href="https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#type-PanelOptions"><span>PanelOptions</span></a><span>,</span><br>&nbsp;&nbsp;<span>callback?</span><span>:</span>&nbsp;<span>function</span><span>,<br>)</span>
```

Настраивает боковую панель.

#### Параметры

-   Параметры конфигурации, применимые к панели.
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()&nbsp;=&gt;</span>&nbsp;<span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
    

### setPanelBehavior()

```
<span>chrome</span><span>.</span><span>sidePanel</span><span>.</span><span>setPanelBehavior</span><span>(</span><br>&nbsp;&nbsp;<span>behavior</span><span>:</span>&nbsp;<a href="https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru#type-PanelBehavior"><span>PanelBehavior</span></a><span>,</span><br>&nbsp;&nbsp;<span>callback?</span><span>:</span>&nbsp;<span>function</span><span>,<br>)</span>
```

Настраивает поведение боковой панели расширения. Это операция по переустановке.

#### Параметры

-   Новое поведение, которое необходимо установить.
    
-   перезвонить
    
    функция необязательна
    
    Параметр `callback` выглядит так:
    
    ```
    <span>()&nbsp;=&gt;</span>&nbsp;<span>void</span>
    ```
    

#### Возврат

-   Промисы поддерживаются в Манифесте V3 и более поздних версиях, но обратные вызовы предусмотрены для обратной совместимости. Вы не можете использовать оба при одном вызове функции. Промис разрешается с тем же типом, который передается в обратный вызов.
