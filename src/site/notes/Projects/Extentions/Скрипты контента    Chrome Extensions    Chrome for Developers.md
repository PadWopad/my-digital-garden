---
{"dg-publish":true,"permalink":"/projects/extentions/skripty-kontenta-chrome-extensions-chrome-for-developers/"}
---


# Скрипты контента  |  Chrome Extensions  |  Chrome for Developers

> ## Excerpt
> Объяснение сценариев контента и способов их использования в расширении Chrome.

---
Сценарии контента — это файлы, которые запускаются в контексте веб-страниц. Используя стандартную [объектную модель документа](https://developer.mozilla.org/docs/Web/API/Document_Object_Model) (DOM), они могут считывать сведения о веб-страницах, которые посещает браузер, вносить в них изменения и передавать информацию своему родительскому расширению.

## Понимание возможностей скрипта контента

Скрипты контента могут напрямую обращаться к следующим API расширений:

-   [`dom`](https://developer.chrome.com/docs/extensions/reference/api/dom?hl=ru)
-   [`i18n`](https://developer.chrome.com/docs/extensions/reference/api/i18n?hl=ru)
-   [`storage`](https://developer.chrome.com/docs/extensions/reference/api/storage?hl=ru)
-   [`runtime.connect()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#method-connect)
-   [`runtime.getManifest()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#method-getManifest)
-   [`runtime.getURL()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#method-getURL)
-   [`runtime.id`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#property-id)
-   [`runtime.onConnect`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#event-onConnect)
-   [`runtime.onMessage`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#event-onMessage)
-   [`runtime.sendMessage()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#method-sendMessage)

Сценарии контента не могут напрямую обращаться к другим API. Но они могут получить к ним доступ косвенно, [обмениваясь сообщениями](https://developer.chrome.com/docs/extensions/develop/concepts/messaging?hl=ru) с другими частями вашего расширения.

Вы также можете получить доступ к другим файлам в вашем расширении из сценария содержимого, используя API, такие как `fetch()` . Для этого вам необходимо объявить их как [ресурсы, доступные через Интернет](https://developer.chrome.com/docs/extensions/reference/manifest/web-accessible-resources?hl=ru) . Обратите внимание, что при этом ресурсы также становятся доступными для любых собственных или сторонних сценариев, работающих на том же сайте.

## Работа в изолированных мирах

Скрипты контента живут в изолированном мире, что позволяет скрипту контента вносить изменения в свою среду JavaScript, не вступая в конфликт со скриптами контента страницы или других расширений.

Расширение может работать на веб-странице с кодом, подобным следующему примеру.

веб-страница.html

```
&lt;html&gt;
  &lt;button id="mybutton"&gt;click me&lt;/button&gt;
  &lt;script&gt;
    var greeting = "hello, ";
    var button = document.getElementById("mybutton");
    button.person_name = "Bob";
    button.addEventListener(
        "click", () =&gt; alert(greeting + button.person_name + "."), false);
  &lt;/script&gt;
&lt;/html&gt;
```

Это расширение может внедрить следующий сценарий содержимого, используя один из методов, описанных в разделе [«Внедрение сценариев»](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru#functionality) .

контент-script.js

```
<span>var</span><span> </span><span>greeting</span><span> </span><span>=</span><span> </span><span>"hola, "</span><span>;</span>
<span>var</span><span> </span><span>button</span><span> </span><span>=</span><span> </span><span>document</span><span>.</span><span>getElementById</span><span>(</span><span>"mybutton"</span><span>);</span>
<span>button</span><span>.</span><span>person_name</span><span> </span><span>=</span><span> </span><span>"Roberto"</span><span>;</span>
<span>button</span><span>.</span><span>addEventListener</span><span>(</span>
<span>    </span><span>"click"</span><span>,</span><span> </span><span>()</span><span> </span><span>=</span>&gt;<span> </span><span>alert</span><span>(</span><span>greeting</span><span> </span><span>+</span><span> </span><span>button</span><span>.</span><span>person_name</span><span> </span><span>+</span><span> </span><span>"."</span><span>),</span><span> </span><span>false</span><span>);</span>
```

Благодаря этому изменению оба оповещения появляются последовательно при нажатии кнопки.

## Внедрить скрипты

Сценарии содержимого могут быть [объявлены статически](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru#static-declarative) , [объявлены динамически](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru#dynamic-declarative) или [внедрены программно](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru#programmatic) .

### Внедрить статические объявления

Используйте объявления сценариев статического содержимого в файле манифеста.json для сценариев, которые должны автоматически запускаться на хорошо известном наборе страниц.

Статически объявленные скрипты регистрируются в манифесте под ключом `"content_scripts"` . Они могут включать файлы JavaScript, файлы CSS или и то, и другое. Все сценарии автозапуска содержимого должны указывать [шаблоны соответствия](https://developer.chrome.com/docs/extensions/develop/concepts/match-patterns?hl=ru) .

манифест.json

```
{
 "name": "My extension",
 ...
 "content_scripts": [
   {
     "matches": ["https://*.nytimes.com/*"],
     "css": ["my-styles.css"],
     "js": ["content-script.js"]
   }
 ],
 ...
}

```

| Имя | Тип | Описание |
| --- | --- | --- |
| `matches` | массив строк | _Необходимый._ Указывает, на какие страницы будет внедрен этот скрипт содержимого. Подробную информацию о синтаксисе этих строк см. в разделе [«Шаблоны сопоставления»](https://developer.chrome.com/docs/extensions/develop/concepts/match-patterns?hl=ru) , а также [«Шаблоны сопоставления и шаблоны»](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru#matchAndGlob) для получения информации о том, как исключить URL-адреса. |
| `css` | массив строк | _Необязательный._ Список файлов CSS, которые будут вставлены в соответствующие страницы. Они вводятся в том порядке, в котором они появляются в этом массиве, до того, как будет создан или отображен какой-либо DOM для страницы. |
| `js` | массив строк | _Необязательный._ Список файлов JavaScript, которые будут внедрены на соответствующие страницы. Файлы внедряются в том порядке, в котором они появляются в этом массиве. Каждая строка в этом списке должна содержать относительный путь к ресурсу в корневом каталоге расширения. Ведущие косые черты (\`/\`) автоматически обрезаются. |
| `run_at` | [RunAt](https://developer.chrome.com/docs/extensions/reference/api/extensionTypes?hl=ru#type-RunAt) | _Необязательный._ Указывает, когда сценарий следует внедрить на страницу. По умолчанию — `document_idle` . |
| `match_about_blank` | логическое значение | _Необязательный._ Должен ли сценарий внедриться в кадр `about:blank` , где родительский или открывающий кадр соответствует одному из шаблонов, объявленных в `matches` . По умолчанию ложь. |
| `match_origin_as_fallback` | логическое значение | _Необязательный._ Должен ли сценарий внедряться в кадры, созданные соответствующим источником, но URL-адрес или источник которых могут не соответствовать шаблону напрямую. К ним относятся кадры с различными схемами, например `about:` , `data:` , `blob:` и `filesystem:` . См. также [Вставка в связанные кадры](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru#injecting-in-related-frames) . |
| `world` | [ИсполнениеМир](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru#type-ExecutionWorld) | _Необязательный._ Мир JavaScript, в котором выполняется скрипт. По умолчанию `ISOLATED` . См. также [Работа в изолированных мирах](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru#isolated_world) . |

### Внедрить динамические объявления

Сценарии динамического содержимого полезны, когда шаблоны совпадений для сценариев содержимого недостаточно известны или когда сценарии содержимого не всегда следует внедрять на известных хостах.

Динамические объявления, представленные в Chrome 96, аналогичны [статическим объявлениям](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru#static-declarative) , но объект сценария содержимого регистрируется в Chrome с использованием методов в [пространстве имен `chrome.scripting`](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru) а не в [манифесте.json](https://developer.chrome.com/docs/extensions/reference/manifest?hl=ru) . API сценариев также позволяет разработчикам расширений:

-   [Зарегистрируйте](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru#method-registerContentScripts) сценарии контента.
-   [Получите список](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru#method-getRegisteredContentScripts) зарегистрированных сценариев контента.
-   [Обновите](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru#method-updateContentScripts) список зарегистрированных сценариев контента.
-   [Удалите](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru#method-unregisterContentScripts) скрипты зарегистрированного контента.

Как и статические объявления, динамические объявления могут включать файлы JavaScript, файлы CSS или и то, и другое.

сервис-worker.js

```
<span>chrome</span><span>.</span><span>scripting</span>
<span>  </span><span>.</span><span>registerContentScripts</span><span>([{</span>
<span>    </span><span>id</span><span>:</span><span> </span><span>"session-script"</span><span>,</span>
<span>    </span><span>js</span><span>:</span><span> </span><span>[</span><span>"content.js"</span><span>],</span>
<span>    </span><span>persistAcrossSessions</span><span>:</span><span> </span><span>false</span><span>,</span>
<span>    </span><span>matches</span><span>:</span><span> </span><span>[</span><span>"*://example.com/*"</span><span>],</span>
<span>    </span><span>runAt</span><span>:</span><span> </span><span>"document_start"</span><span>,</span>
<span>  </span><span>}])</span>
<span>  </span><span>.</span><span>then</span><span>(()</span><span> </span><span>=</span>&gt;<span> </span><span>console</span><span>.</span><span>log</span><span>(</span><span>"registration complete"</span><span>))</span>
<span>  </span><span>.</span><span>catch</span><span>((</span><span>err</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>console</span><span>.</span><span>warn</span><span>(</span><span>"unexpected error"</span><span>,</span><span> </span><span>err</span><span>))</span>
```

сервис-worker.js

```
<span>chrome</span><span>.</span><span>scripting</span>
<span>  </span><span>.</span><span>updateContentScripts</span><span>([{</span>
<span>    </span><span>id</span><span>:</span><span> </span><span>"session-script"</span><span>,</span>
<span>    </span><span>excludeMatches</span><span>:</span><span> </span><span>[</span><span>"*://admin.example.com/*"</span><span>],</span>
<span>  </span><span>}])</span>
<span>  </span><span>.</span><span>then</span><span>(()</span><span> </span><span>=</span>&gt;<span> </span><span>console</span><span>.</span><span>log</span><span>(</span><span>"registration updated"</span><span>));</span>
```

сервис-worker.js

```
<span>chrome</span><span>.</span><span>scripting</span>
<span>  </span><span>.</span><span>getRegisteredContentScripts</span><span>()</span>
<span>  </span><span>.</span><span>then</span><span>(</span><span>scripts</span><span> </span><span>=</span>&gt;<span> </span><span>console</span><span>.</span><span>log</span><span>(</span><span>"registered content scripts"</span><span>,</span><span> </span><span>scripts</span><span>));</span>
```

сервис-worker.js

```
<span>chrome</span><span>.</span><span>scripting</span>
<span>  </span><span>.</span><span>unregisterContentScripts</span><span>({</span><span> </span><span>ids</span><span>:</span><span> </span><span>[</span><span>"session-script"</span><span>]</span><span> </span><span>})</span>
<span>  </span><span>.</span><span>then</span><span>(()</span><span> </span><span>=</span>&gt;<span> </span><span>console</span><span>.</span><span>log</span><span>(</span><span>"un-registration complete"</span><span>));</span>
```

### Внедрить программно

Используйте программное внедрение для сценариев контента, которые необходимо запускать в ответ на события или в определенных случаях.

Чтобы программно внедрить сценарий содержимого, вашему расширению необходимы [разрешения хоста](https://developer.chrome.com/docs/extensions/reference/permissions?hl=ru) для страницы, в которую оно пытается внедрить сценарии. Разрешения хоста можно предоставить, запросив их как часть манифеста вашего расширения, или временно используя [`"activeTab"`](https://developer.chrome.com/docs/extensions/develop/concepts/activeTab?hl=ru) .

Ниже приведены различные версии расширения на основе activeTab.

манифест.json:

```
{
  "name": "My extension",
  ...
  "permissions": [
    "activeTab",
    "scripting"
  ],
  "background": {
    "service_worker": "background.js"
  },
  "action": {
    "default_title": "Action Button"
  }
}
```

Сценарии содержимого можно внедрить в виде файлов.

контент-script.js

```

<span>document</span><span>.</span><span>body</span><span>.</span><span>style</span><span>.</span><span>backgroundColor</span><span> </span><span>=</span><span> </span><span>"orange"</span><span>;</span>
```

сервис-worker.js:

```
<span>chrome</span><span>.</span><span>action</span><span>.</span><span>onClicked</span><span>.</span><span>addListener</span><span>((</span><span>tab</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>chrome</span><span>.</span><span>scripting</span><span>.</span><span>executeScript</span><span>({</span>
<span>    </span><span>target</span><span>:</span><span> </span><span>{</span><span> </span><span>tabId</span><span>:</span><span> </span><span>tab</span><span>.</span><span>id</span><span> </span><span>},</span>
<span>    </span><span>files</span><span>:</span><span> </span><span>[</span><span>"content-script.js"</span><span>]</span>
<span>  </span><span>});</span>
<span>});</span>
```

Или тело функции можно внедрить и выполнить как сценарий содержимого.

сервис-worker.js:

```
<span>function</span><span> </span><span>injectedFunction</span><span>()</span><span> </span><span>{</span>
<span>  </span><span>document</span><span>.</span><span>body</span><span>.</span><span>style</span><span>.</span><span>backgroundColor</span><span> </span><span>=</span><span> </span><span>"orange"</span><span>;</span>
<span>}</span>

<span>chrome</span><span>.</span><span>action</span><span>.</span><span>onClicked</span><span>.</span><span>addListener</span><span>((</span><span>tab</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>chrome</span><span>.</span><span>scripting</span><span>.</span><span>executeScript</span><span>({</span>
<span>    </span><span>target</span><span> </span><span>:</span><span> </span><span>{</span><span>tabId</span><span> </span><span>:</span><span> </span><span>tab</span><span>.</span><span>id</span><span>},</span>
<span>    </span><span>func</span><span> </span><span>:</span><span> </span><span>injectedFunction</span><span>,</span>
<span>  </span><span>});</span>
<span>});</span>
```

Имейте в виду, что внедренная функция является копией функции, указанной в вызове `chrome.scripting.executeScript()` , а не самой исходной функции. В результате тело функции должно быть автономным; ссылки на переменные вне функции приведут к тому, что сценарий содержимого выдаст ошибку [`ReferenceError`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/ReferenceError) .

При внедрении в качестве функции вы также можете передавать ей аргументы.

сервис-worker.js

```
<span>function</span><span> </span><span>injectedFunction</span><span>(</span><span>color</span><span>)</span><span> </span><span>{</span>
<span>  </span><span>document</span><span>.</span><span>body</span><span>.</span><span>style</span><span>.</span><span>backgroundColor</span><span> </span><span>=</span><span> </span><span>color</span><span>;</span>
<span>}</span>

<span>chrome</span><span>.</span><span>action</span><span>.</span><span>onClicked</span><span>.</span><span>addListener</span><span>((</span><span>tab</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>chrome</span><span>.</span><span>scripting</span><span>.</span><span>executeScript</span><span>({</span>
<span>    </span><span>target</span><span> </span><span>:</span><span> </span><span>{</span><span>tabId</span><span> </span><span>:</span><span> </span><span>tab</span><span>.</span><span>id</span><span>},</span>
<span>    </span><span>func</span><span> </span><span>:</span><span> </span><span>injectedFunction</span><span>,</span>
<span>    </span><span>args</span><span> </span><span>:</span><span> </span><span>[</span><span> </span><span>"orange"</span><span> </span><span>],</span>
<span>  </span><span>});</span>
<span>});</span>
```

### Исключить совпадения и глобусы

Чтобы настроить указанное соответствие страниц, включите следующие поля в декларативную регистрацию.

| Имя | Тип | Описание |
| --- | --- | --- |
| `exclude_matches` | массив строк | _Необязательный._ Исключает страницы, в которые в противном случае был бы внедрен этот сценарий содержимого. Подробную информацию о синтаксисе этих строк см. в разделе [«Шаблоны совпадений»](https://developer.chrome.com/docs/extensions/develop/concepts/match-patterns?hl=ru) . |
| `include_globs` | массив строк | _Необязательный._ Применяется после `matches` , чтобы включать только те URL-адреса, которые также соответствуют этому шаблону. Это предназначено для эмуляции ключевого слова [`@include`](https://wiki.greasespot.net/Metadata_Block#.40include) Greasemonkey. |
| `exclude_globs` | массив строк | _Необязательный._ Применяется после `matches` , чтобы исключить URL-адреса, соответствующие этому шаблону. Предназначен для эмуляции ключевого слова [`@exclude`](https://wiki.greasespot.net/Metadata_Block#.40exclude) Greasemonkey. |

Сценарий содержимого будет внедрен на страницу, если выполняются оба следующих условия:

-   Его URL-адрес соответствует любому шаблону `matches` и любому шаблону `include_globs` .
-   URL-адрес также не соответствует шаблону `exclude_matches` или `exclude_globs` . Поскольку свойство `matches` является обязательным, `exclude_matches` , `include_globs` и `exclude_globs` можно использовать только для ограничения того, какие страницы будут затронуты.

Следующее расширение вводит сценарий содержимого в `https://www.nytimes.com/health` но не в `https://www.nytimes.com/business` .

манифест.json

```
{
  "name": "My extension",
  ...
  "content_scripts": [
    {
      "matches": ["https://*.nytimes.com/*"],
      "exclude_matches": ["*://*/*business*"],
      "js": ["contentScript.js"]
    }
  ],
  ...
}
```

сервис-worker.js

```
<span>chrome</span><span>.</span><span>scripting</span><span>.</span><span>registerContentScripts</span><span>([{</span>
<span>  </span><span>id</span><span> </span><span>:</span><span> </span><span>"test"</span><span>,</span>
<span>  </span><span>matches</span><span> </span><span>:</span><span> </span><span>[</span><span> </span><span>"https://*.nytimes.com/*"</span><span> </span><span>],</span>
<span>  </span><span>excludeMatches</span><span> </span><span>:</span><span> </span><span>[</span><span> </span><span>"*://*/*business*"</span><span> </span><span>],</span>
<span>  </span><span>js</span><span> </span><span>:</span><span> </span><span>[</span><span> </span><span>"contentScript.js"</span><span> </span><span>],</span>
<span>}]);</span>
```

Свойства Glob имеют другой, более гибкий синтаксис, чем [шаблоны сопоставления](https://developer.chrome.com/docs/extensions/develop/concepts/match-patterns?hl=ru) . Допустимыми glob-строками являются URL-адреса, которые могут содержать подстановочные знаки и звездочки. Звездочка ( `*` ) соответствует любой строке любой длины, включая пустую строку, а знак вопроса ( `?` ) соответствует любому одиночному символу.

Например, glob `https://???.example.com/foo/\*` соответствует любому из следующих значений:

-   `https://www.example.com/foo/bar`
-   `https://the.example.com/foo/`

Однако он _не_ соответствует следующему:

-   `https://my.example.com/foo/bar`
-   `https://example.com/foo/`
-   `https://www.example.com/foo`

Это расширение внедряет скрипт контента в `https://www.nytimes.com/arts/index.html` и `https://www.nytimes.com/jobs/index.htm*` , но не в `https://www.nytimes.com/sports/index.html` :

манифест.json

```
{
  "name": "My extension",
  ...
  "content_scripts": [
    {
      "matches": ["https://*.nytimes.com/*"],
      "include_globs": ["*nytimes.com/???s/*"],
      "js": ["contentScript.js"]
    }
  ],
  ...
}
```

Это расширение встраивает сценарий содержимого в `https://history.nytimes.com` и `https://.nytimes.com/history` , но не в `https://science.nytimes.com` или `https://www.nytimes.com/science` :

манифест.json

```
{
  "name": "My extension",
  ...
  "content_scripts": [
    {
      "matches": ["https://*.nytimes.com/*"],
      "exclude_globs": ["*science*"],
      "js": ["contentScript.js"]
    }
  ],
  ...
}
```

Для достижения правильной области действия можно включить один, все или некоторые из них.

манифест.json

```
{
  "name": "My extension",
  ...
  "content_scripts": [
    {
      "matches": ["https://*.nytimes.com/*"],
      "exclude_matches": ["*://*/*business*"],
      "include_globs": ["*nytimes.com/???s/*"],
      "exclude_globs": ["*science*"],
      "js": ["contentScript.js"]
    }
  ],
  ...
}
```

### Время выполнения

Поле `run_at` определяет, когда файлы JavaScript внедряются на веб-страницу. Предпочтительным значением по умолчанию является `"document_idle"` . Другие возможные значения см. в типе [RunAt](https://developer.chrome.com/docs/extensions/reference/api/extensionTypes?hl=ru#type-RunAt) .

манифест.json

```
{
  "name": "My extension",
  ...
  "content_scripts": [
    {
      "matches": ["https://*.nytimes.com/*"],
      "run_at": "document_idle",
      "js": ["contentScript.js"]
    }
  ],
  ...
}
```

сервис-worker.js

```
<span>chrome</span><span>.</span><span>scripting</span><span>.</span><span>registerContentScripts</span><span>([{</span>
<span>  </span><span>id</span><span> </span><span>:</span><span> </span><span>"test"</span><span>,</span>
<span>  </span><span>matches</span><span> </span><span>:</span><span> </span><span>[</span><span> </span><span>"https://*.nytimes.com/*"</span><span> </span><span>],</span>
<span>  </span><span>runAt</span><span> </span><span>:</span><span> </span><span>"document_idle"</span><span>,</span>
<span>  </span><span>js</span><span> </span><span>:</span><span> </span><span>[</span><span> </span><span>"contentScript.js"</span><span> </span><span>],</span>
<span>}]);</span>
```

| Имя | Тип | Описание |
| --- | --- | --- |
| `document_idle` | нить | _Предпочтительно._ Используйте `"document_idle"` когда это возможно.
Браузер выбирает время для внедрения скриптов между `"document_end"` и сразу после срабатывания события [`window.onload`](https://developer.mozilla.org/docs/Web/API/Window/load_event) . Точный момент внедрения зависит от того, насколько сложен документ и сколько времени занимает его загрузка, и оптимизирован для скорости загрузки страницы.

Сценариям содержимого, работающим в `"document_idle"` не нужно прослушивать событие `window.onload` , они гарантированно запустятся после завершения DOM. Если сценарий обязательно должен быть запущен после `window.onload` , расширение может проверить, запущена ли уже `onload` используя свойство [`document.readyState`](https://developer.mozilla.org/docs/Web/API/Document/readyState) .

 |
| `document_start` | нить | Скрипты вводятся после любых файлов из `css` , но до создания любого другого DOM или запуска любого другого скрипта. |
| `document_end` | нить | Скрипты внедряются сразу после завершения DOM, но до загрузки подресурсов, таких как изображения и фреймы. |

### Укажите рамки

Для сценариев декларативного содержимого, указанных в манифесте, поле [`"all_frames"`](https://developer.chrome.com/docs/extensions/reference/manifest/content-scripts?hl=ru#frames) позволяет расширению указать, следует ли вставлять файлы JavaScript и CSS во все кадры, соответствующие указанным требованиям URL-адреса, или только в самый верхний кадр на вкладке:

манифест.json

```
{
  "name": "My extension",
  ...
  "content_scripts": [
    {
      "matches": ["https://*.nytimes.com/*"],
      "all_frames": true,
      "js": ["contentScript.js"]
    }
  ],
  ...
}
```

При программной регистрации сценариев содержимого с помощью [`chrome.scripting.registerContentScripts(...)`](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru#type-RegisteredContentScript) параметр [`allFrames`](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru#properties_4) можно использовать, чтобы указать, следует ли вставлять сценарий содержимого во все кадры, соответствующие указанным требованиям URL-адреса, или только в самый верхний кадр на вкладке. Это можно использовать только с tabId и нельзя использовать, если указаны FrameIds или DocumentIds:

сервис-worker.js

```
<span>chrome</span><span>.</span><span>scripting</span><span>.</span><span>registerContentScripts</span><span>([{</span>
<span>  </span><span>id:</span><span> </span><span>"test"</span><span>,</span>
<span>  </span><span>matches</span><span> </span><span>:</span><span> </span><span>[</span><span> </span><span>"https://*.nytimes.com/*"</span><span> </span><span>],</span>
<span>  </span><span>allFrames</span><span> </span><span>:</span><span> </span><span>true</span><span>,</span>
<span>  </span><span>js</span><span> </span><span>:</span><span> </span><span>[</span><span> </span><span>"contentScript.js"</span><span> </span><span>],</span>
<span>}]);</span>
```

Расширения могут захотеть запускать сценарии в кадрах, которые связаны с совпадающим кадром, но сами не совпадают. Обычным сценарием в этом случае являются фреймы с URL-адресами, которые были созданы совпадающим фреймом, но чьи URL-адреса сами по себе не соответствуют шаблонам, указанным в сценарии.

Это тот случай, когда расширение хочет внедрить в кадры URL-адреса, имеющие схемы `about:` , `data:` , `blob:` и `filesystem:` :. В этих случаях URL-адрес не будет соответствовать шаблону сценария содержимого (а в случае `about:` и `data:` вообще не включайте родительский URL-адрес или источник в URL-адрес, как в `about:blank` или `data:text/html,<html>Hello, World!</html>` ). Однако эти кадры по-прежнему можно связать с создающим кадром.

Для внедрения в эти кадры расширения могут указать свойство `"match_origin_as_fallback"` в спецификации сценария содержимого в манифесте.

манифест.json

```
<span>{</span>
<span>  </span><span>"name"</span><span>:</span><span> </span><span>"My extension"</span><span>,</span>
<span>  </span><span>...</span>
<span>  </span><span>"content_scripts"</span><span>:</span><span> </span><span>[</span>
<span>    </span><span>{</span>
<span>      </span><span>"matches"</span><span>:</span><span> </span><span>[</span><span>"https://*.google.com/*"</span><span>],</span>
<span>      </span><span>"match_origin_as_fallback"</span><span>:</span><span> </span><span>true</span><span>,</span>
<span>      </span><span>"js"</span><span>:</span><span> </span><span>[</span><span>"contentScript.js"</span><span>]</span>
<span>    </span><span>}</span>
<span>  </span><span>],</span>
<span>  </span><span>...</span>
<span>}</span>
```

Если указано значение `true` , Chrome будет проверять происхождение инициатора кадра, чтобы определить, соответствует ли кадр, а не URL-адрес самого кадра. Обратите внимание, что это также может отличаться от _источника_ целевого кадра (например, `data:` URL-адреса имеют нулевое происхождение).

Инициатором кадра является кадр, который создал или перемещался по целевому кадру. Хотя обычно это прямой родительский элемент или средство открытия, это может и не быть (как в случае с фреймом, перемещающимся по iframe внутри iframe).

Поскольку при этом сравнивается _источник_ кадра-инициатора, кадр-инициатор может находиться на любом пути от этого источника. Чтобы прояснить этот вывод, Chrome требует, чтобы все сценарии содержимого, для которых для параметра `"match_origin_as_fallback"` установлено значение `true` , также указывали путь `*` .

Если указаны оба `"match_origin_as_fallback"` и `"match_about_blank"` , приоритет имеет `"match_origin_as_fallback"` .

## Связь со страницей встраивания

Хотя среды выполнения сценариев контента и страниц, на которых они размещены, изолированы друг от друга, они имеют общий доступ к DOM страницы. Если страница желает взаимодействовать со сценарием содержимого или с расширением через сценарий содержимого, она должна делать это через общий DOM.

Пример можно реализовать с помощью [`window.postMessage()`](https://developer.mozilla.org/docs/Web/API/Window/postMessage) :

контент-script.js

```
<span>var</span><span> </span><span>port</span><span> </span><span>=</span><span> </span><span>chrome</span><span>.</span><span>runtime</span><span>.</span><span>connect</span><span>();</span>

<span>window</span><span>.</span><span>addEventListener</span><span>(</span><span>"message"</span><span>,</span><span> </span><span>(</span><span>event</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>// We only accept messages from ourselves</span>
<span>  </span><span>if</span><span> </span><span>(</span><span>event</span><span>.</span><span>source</span><span> </span><span>!==</span><span> </span><span>window</span><span>)</span><span> </span><span>{</span>
<span>    </span><span>return</span><span>;</span>
<span>  </span><span>}</span>

<span>  </span><span>if</span><span> </span><span>(</span><span>event</span><span>.</span><span>data</span><span>.</span><span>type</span><span> &amp;&amp; </span><span>(</span><span>event</span><span>.</span><span>data</span><span>.</span><span>type</span><span> </span><span>===</span><span> </span><span>"FROM_PAGE"</span><span>))</span><span> </span><span>{</span>
<span>    </span><span>console</span><span>.</span><span>log</span><span>(</span><span>"Content script received: "</span><span> </span><span>+</span><span> </span><span>event</span><span>.</span><span>data</span><span>.</span><span>text</span><span>);</span>
<span>    </span><span>port</span><span>.</span><span>postMessage</span><span>(</span><span>event</span><span>.</span><span>data</span><span>.</span><span>text</span><span>);</span>
<span>  </span><span>}</span>
<span>},</span><span> </span><span>false</span><span>);</span>
```

пример.js

```
<span>document</span><span>.</span><span>getElementById</span><span>(</span><span>"theButton"</span><span>).</span><span>addEventListener</span><span>(</span><span>"click"</span><span>,</span><span> </span><span>()</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>window</span><span>.</span><span>postMessage</span><span>(</span>
<span>      </span><span>{</span><span>type</span><span> </span><span>:</span><span> </span><span>"FROM_PAGE"</span><span>,</span><span> </span><span>text</span><span> </span><span>:</span><span> </span><span>"Hello from the webpage!"</span><span>},</span><span> </span><span>"*"</span><span>);</span>
<span>},</span><span> </span><span>false</span><span>);</span>
```

Страница без расширения, example.html, отправляет сообщения самому себе. Это сообщение перехватывается и проверяется сценарием содержимого, а затем отправляется в процесс расширения. Таким образом, страница устанавливает канал связи с процессом расширения. Обратное возможно с помощью аналогичных средств.

## Доступ к файлам расширений

Чтобы получить доступ к файлу расширения из сценария содержимого, вы можете вызвать [`chrome.runtime.getURL()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#method-getURL) , чтобы получить _абсолютный URL-адрес_ вашего ресурса расширения, как показано в следующем примере ( `content.js` ):

контент-script.js

```
<span>let</span><span> </span><span>image</span><span> </span><span>=</span><span> </span><span>chrome</span><span>.</span><span>runtime</span><span>.</span><span>getURL</span><span>(</span><span>"images/my_image.png"</span><span>)</span>
```

Чтобы использовать шрифты или изображения в файле CSS, вы можете использовать [`@@extension_id`](https://developer.chrome.com/docs/extensions/reference/api/i18n?hl=ru#overview-predefined) для создания URL-адреса, как показано в следующем примере ( `content.css` ):

контент.css

```
<span>body</span><span> </span><span>{</span>
<span> </span><span>background-image</span><span>:</span><span>url</span><span>(</span><span>'chrome-extension://__MSG_@@extension_id__/background.png'</span><span>);</span>
<span>}</span>

<span>@</span><span>font-face</span><span> </span><span>{</span>
<span> </span><span>font-family</span><span>:</span><span> </span><span>'Stint Ultra Expanded'</span><span>;</span>
<span> </span><span>font-style</span><span>:</span><span> </span><span>normal</span><span>;</span>
<span> </span><span>font-weight</span><span>:</span><span> </span><span>400</span><span>;</span>
<span> </span><span>src</span><span>:</span><span> </span><span>url</span><span>(</span><span>'chrome-extension://__MSG_@@extension_id__/fonts/Stint Ultra Expanded.woff'</span><span>)</span><span> </span><span>format</span><span>(</span><span>'woff'</span><span>);</span>
<span>}</span>
```

Все ресурсы должны быть объявлены как [доступные через Интернет ресурсы](https://developer.chrome.com/docs/extensions/reference/manifest/web-accessible-resources?hl=ru) в файле `manifest.json` :

манифест.json

```
<span>{</span>
<span> </span><span>...</span>
<span> </span><span>"web_accessible_resources"</span><span>:</span><span> </span><span>[</span>
<span>   </span><span>{</span>
<span>     </span><span>"resources"</span><span>:</span><span> </span><span>[</span><span> </span><span>"images/*.png"</span><span> </span><span>],</span>
<span>     </span><span>"matches"</span><span>:</span><span> </span><span>[</span><span> </span><span>"https://example.com/*"</span><span> </span><span>]</span>
<span>   </span><span>},</span>
<span>   </span><span>{</span>
<span>     </span><span>"resources"</span><span>:</span><span> </span><span>[</span><span> </span><span>"fonts/*.woff"</span><span> </span><span>],</span>
<span>     </span><span>"matches"</span><span>:</span><span> </span><span>[</span><span> </span><span>"https://example.com/*"</span><span> </span><span>]</span>
<span>   </span><span>}</span>
<span> </span><span>],</span>
<span> </span><span>...</span>
<span>}</span>
```

## Оставайтесь в безопасности

Хотя изолированные миры обеспечивают уровень защиты, использование сценариев содержимого может создать уязвимости в расширении и веб-странице. Если сценарий контента получает контент с отдельного веб-сайта, например, путем вызова `fetch()` , будьте осторожны, чтобы отфильтровать контент от атак [с использованием межсайтовых сценариев](https://en.wikipedia.org/wiki/Cross-site_scripting) перед его внедрением. Общайтесь только через HTTPS, чтобы избежать атак [«человек посередине»](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) .

Обязательно отфильтруйте вредоносные веб-страницы. Например, следующие шаблоны опасны и запрещены в Манифесте V3:

Не

контент-script.js

```
<span>const</span><span> </span><span>data</span><span> </span><span>=</span><span> </span><span>document</span><span>.</span><span>getElementById</span><span>(</span><span>"json-data"</span><span>);</span>
<span>// WARNING! Might be evaluating an evil script!</span>
<span>const</span><span> </span><span>parsed</span><span> </span><span>=</span><span> </span><span>eval</span><span>(</span><span>"("</span><span> </span><span>+</span><span> </span><span>data</span><span> </span><span>+</span><span> </span><span>")"</span><span>);</span>
```

Не

контент-script.js

```
<span>const</span><span> </span><span>elmt_id</span><span> </span><span>=</span><span> </span><span>...</span>
<span>// WARNING! elmt_id might be '); ... evil script ... //'!</span>
<span>window</span><span>.</span><span>setTimeout</span><span>(</span><span>"animate("</span><span> </span><span>+</span><span> </span><span>elmt_id</span><span> </span><span>+</span><span> </span><span>")"</span><span>,</span><span> </span><span>200</span><span>);</span>
```

Вместо этого отдайте предпочтение более безопасным API, которые не запускают сценарии:

Делать

контент-script.js

```
<span>const</span><span> </span><span>data</span><span> </span><span>=</span><span> </span><span>document</span><span>.</span><span>getElementById</span><span>(</span><span>"json-data"</span><span>)</span>
<span>// JSON.parse does not evaluate the attacker's scripts.</span>
<span>const</span><span> </span><span>parsed</span><span> </span><span>=</span><span> </span><span>JSON</span><span>.</span><span>parse</span><span>(</span><span>data</span><span>);</span>
```

Делать

контент-script.js

```
<span>const</span><span> </span><span>elmt_id</span><span> </span><span>=</span><span> </span><span>...</span>
<span>// The closure form of setTimeout does not evaluate scripts.</span>
<span>window</span><span>.</span><span>setTimeout</span><span>(()</span><span> </span><span>=&gt;</span><span> </span><span>animate</span><span>(</span><span>elmt_id</span><span>),</span><span> </span><span>200</span><span>);</span>
```
