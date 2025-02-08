---
{"dg-publish":true,"created":"2025-01-31T16:47:17 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru","author":null,"permalink":"/projects/extentions/chrome-declarative-net-request-api-chrome-for-developers/","dgPassFrontmatter":true}
---


# chrome.declarativeNetRequest  |  API  |  Chrome for Developers

> ## Excerpt
> Manifest V3

---
[Skip to main content](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#main-content)

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

API `chrome.declarativeNetRequest` используется для блокировки или изменения сетевых запросов путем указания декларативных правил. Это позволяет расширениям изменять сетевые запросы, не перехватывая их и не просматривая их содержимое, обеспечивая тем самым большую конфиденциальность.

## Разрешения

`declarativeNetRequest`  
`declarativeNetRequestWithHostAccess`  

Разрешения « `declarativeNetRequest` » и « `declarativeNetRequestWithHostAccess` » предоставляют одинаковые возможности. Разница между ними заключается в том, когда разрешения запрашиваются или предоставляются.

`"declarativeNetRequest"`

Вызывает предупреждение о разрешении во время установки, но обеспечивает неявный доступ к `allow` , `allowAllRequests` и правилам `block` . Используйте это, когда это возможно, чтобы избежать необходимости запрашивать полный доступ к хостам.

`"declarativeNetRequestFeedback"`

Включает функции отладки для [распакованных расширений](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru#load-unpacked) , в частности [`getMatchedRules()`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#method-getMatchedRules) и [`onRuleMatchedDebug`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#event-onRuleMatchedDebug) .

`"declarativeNetRequestWithHostAccess"`

Предупреждение о разрешении не отображается во время установки, но вы должны запросить разрешения хоста, прежде чем сможете выполнять какие-либо действия на хосте. Это подходит, если вы хотите использовать декларативные правила сетевых запросов в расширении, которое уже имеет разрешения хоста, без создания дополнительных предупреждений.

## Доступность

## Манифест

В дополнение к разрешениям, описанным ранее, некоторые типы наборов правил, в частности статические наборы правил, требуют объявления ключа манифеста `"declarative_net_request"` , который должен представлять собой словарь с единственным ключом под названием `"rule_resources"` . Этот ключ представляет собой массив, содержащий словари типа `Ruleset` , как показано ниже. (Обратите внимание, что имя «Набор правил» не отображается в JSON манифеста, поскольку это просто массив.) [Статические наборы правил](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#rules) объясняются позже в этом документе.

```
<span>{</span><span><br>&nbsp; </span><span>"name"</span><span>:</span><span> </span><span>"My extension"</span><span>,</span><span><br>&nbsp; </span><span>...</span><span><br><br>&nbsp; </span><span>"declarative_net_request"</span><span> </span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"rule_resources"</span><span> </span><span>:</span><span> </span><span>[{</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"id"</span><span>:</span><span> </span><span>"ruleset_1"</span><span>,</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"enabled"</span><span>:</span><span> </span><span>true</span><span>,</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"path"</span><span>:</span><span> </span><span>"rules_1.json"</span><span><br>&nbsp; &nbsp; </span><span>},</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"id"</span><span>:</span><span> </span><span>"ruleset_2"</span><span>,</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"enabled"</span><span>:</span><span> </span><span>false</span><span>,</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"path"</span><span>:</span><span> </span><span>"rules_2.json"</span><span><br>&nbsp; &nbsp; </span><span>}]</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>"permissions"</span><span>:</span><span> </span><span>[</span><span><br>&nbsp; &nbsp; </span><span>"declarativeNetRequest"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"declarativeNetRequestFeedback"</span><span>,</span><span><br>&nbsp; </span><span>],</span><span><br>&nbsp; </span><span>"host_permissions"</span><span>:</span><span> </span><span>[</span><span><br>&nbsp; &nbsp; </span><span>"http://www.blogger.com/*"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"http://*.google.com/*"</span><span><br>&nbsp; </span><span>],</span><span><br>&nbsp; </span><span>...</span><span><br></span><span>}</span><span><br></span>
```

## Правила и наборы правил

Чтобы использовать этот API, укажите один или несколько наборов правил. Набор правил содержит массив правил. Одно правило выполняет одно из следующих действий:

-   Заблокируйте сетевой запрос.
-   Обновите схему (с http на https).
-   Предотвратите блокировку запроса, отменив все соответствующие заблокированные правила.
-   Перенаправить сетевой запрос.
-   Измените заголовки запроса или ответа.

Существует три типа наборов правил, управление которыми несколько отличается.

Динамический

Сохраняются во всех сеансах браузера и обновлениях расширений и управляются с помощью JavaScript, пока расширение используется.

Сессия

Очищается при закрытии браузера и установке новой версии расширения. Правила сеанса управляются с помощью JavaScript, пока используется расширение.

Статический

Упаковывается, устанавливается и обновляется при установке или обновлении расширения. Статические правила хранятся в файлах правил в формате JSON и перечислены в файле манифеста.

### Динамические и сеансовые наборы правил

Динамические и сеансовые наборы правил управляются с помощью JavaScript, пока используется расширение.

-   Динамические правила сохраняются во всех сеансах браузера и обновлениях расширений.
-   Правила сеанса очищаются при закрытии браузера и установке новой версии расширения.

Каждый из этих типов наборов правил существует только по одному. Расширение может добавлять или удалять правила динамически, вызывая [`updateDynamicRules()`](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest?hl=ru#method-updateDynamicRules) и [`updateSessionRules()`](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest?hl=ru#method-updateSessionRules) , при условии, что ограничения правил не превышены. Информацию об ограничениях правил см. в [разделе Ограничения правил](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#limits) . Вы можете увидеть [пример этого](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#update-dynamic-rule-examples) в [примерах кода](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#code-examples) .

### Статические наборы правил

В отличие от динамических правил и правил сеанса, статические правила упаковываются, устанавливаются и обновляются при установке или обновлении расширения. Они хранятся в файлах правил в формате JSON, которые указываются расширению с помощью ключей `"declarative_net_request"` и `"rule_resources"` [, как описано выше](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#manifest) , а также в одном или нескольких словарях [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest?hl=ru#type-Ruleset) . Словарь `Ruleset` содержит путь к файлу правил, идентификатор набора правил, содержащегося в файле, а также сведения о том, включен или отключен этот набор правил. Последние два важны при программном включении или отключении набора правил.

```
<span>{</span><span><br>&nbsp; </span><span>...</span><span><br>&nbsp; </span><span>"declarative_net_request"</span><span> </span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"rule_resources"</span><span> </span><span>:</span><span> </span><span>[{</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"id"</span><span>:</span><span> </span><span>"ruleset_1"</span><span>,</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"enabled"</span><span>:</span><span> </span><span>true</span><span>,</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"path"</span><span>:</span><span> </span><span>"rules_1.json"</span><span><br>&nbsp; &nbsp; </span><span>},</span><span><br>&nbsp; &nbsp; </span><span>...</span><span><br>&nbsp; &nbsp; </span><span>]</span><span><br>&nbsp; </span><span>}</span><span><br>&nbsp; </span><span>...</span><span><br></span><span>}</span><span><br></span>
```

Чтобы протестировать файлы правил, [загрузите распакованное расширение](https://developer.chrome.com/docs/extensions/mv3/getstarted/development-basics?hl=ru#load-unpacked) . Ошибки и предупреждения о недопустимых статических правилах отображаются только для распакованных расширений. Недопустимые статические правила в упакованных расширениях игнорируются.

## Ускоренная проверка

Изменения в статических наборах правил могут подлежать ускоренному рассмотрению. См. [ускоренную проверку допустимых изменений](https://developer.chrome.com/docs/webstore/expedited-review?hl=ru) .

## Включение и отключение статических правил и наборов правил

Как отдельные статические правила, так и полные статические наборы правил могут быть включены или отключены во время выполнения.

Набор включенных статических правил и наборов правил сохраняется во всех сеансах браузера. Ни один из них не сохраняется при обновлении расширений, а это означает, что после обновления доступны только те правила, которые вы решили оставить в своих файлах правил.

По соображениям производительности также существуют ограничения на количество правил и наборов правил, которые можно включить одновременно. Вызовите [`getAvailableStaticRuleCount()`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#method-getAvailableStaticRuleCount) чтобы проверить количество дополнительных правил, которые можно включить. Информацию об ограничениях правил см. в [разделе Ограничения правил](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#limits) .

Чтобы включить или отключить статические _правила_ , вызовите [`updateStaticRules()`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#method-updateStaticRules) . Этот метод принимает объект [`UpdateStaticRulesOptions`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-UpdateStaticRulesOptions) , который содержит массивы идентификаторов правил для включения или отключения. Идентификаторы определяются с использованием ключа `"id"` словаря `Ruleset` . Максимальный лимит отключенных статических правил — 5000.

Чтобы включить или отключить статические _наборы правил_ , вызовите [`updateEnabledRulesets()`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#method-updateEnabledRulesets) . Этот метод принимает объект [`UpdateRulesetOptions`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-UpdateRulesetOptions) , который содержит массивы идентификаторов наборов правил для включения или отключения. Идентификаторы определяются с использованием ключа `"id"` словаря `Ruleset` .

## Правила сборки

Независимо от типа правило начинается с четырех полей, как показано ниже. Хотя ключи `"id"` и `"priority"` принимают числовые значения, клавиши [`"action"`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-Rule-action) и [`"condition"`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-Rule-condition) могут обеспечивать несколько условий блокировки и перенаправления. Следующее правило блокирует все запросы сценариев, исходящие от `"foo.com"` к любому URL-адресу с `"abc"` в качестве подстроки.

```
<span>{</span><span><br>&nbsp; </span><span>"id"</span><span> </span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"priority"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"action"</span><span> </span><span>:</span><span> </span><span>{</span><span> </span><span>"type"</span><span> </span><span>:</span><span> </span><span>"block"</span><span> </span><span>},</span><span><br>&nbsp; </span><span>"condition"</span><span> </span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"urlFilter"</span><span> </span><span>:</span><span> </span><span>"abc"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"initiatorDomains"</span><span> </span><span>:</span><span> </span><span>[</span><span>"foo.com"</span><span>],</span><span><br>&nbsp; &nbsp; </span><span>"resourceTypes"</span><span> </span><span>:</span><span> </span><span>[</span><span>"script"</span><span>]</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

## Соответствие URL-адресов

Декларативный сетевой запрос предоставляет возможность сопоставлять URL-адреса с помощью синтаксиса сопоставления с образцом или регулярных выражений.

### Синтаксис URL-фильтра

Ключ `"condition"` правила позволяет использовать ключ `"urlFilter"` для воздействия на URL-адреса в указанном домене. Вы создаете шаблоны, используя [токены сопоставления шаблонов](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest?hl=ru#property-RuleCondition-urlFilter) . Вот несколько примеров.

| `**urlFilter**` | Матчи | Не соответствует |
| --- | --- | --- |
| `"abc"` | https://abcd.com  
https://example.com/abcd | https://ab.com |
| `"abc*d"` | https://abcd.com  
https://example.com/abcxyzd | https://abc.com |
| `"||a.example.com"` | https://a.example.com/  
https://baexample.com/xyz  
https://a.example.company | https://example.com/ |
| `"|https*"` | https://example.com | http://example.com/  
http://https.com |
| `"example*^123|"` | https://example.com/123  
http://abc.com/example?123 | https://example.com/1234  
https://abc.com/example0123 |

### Регулярные выражения

Условия также могут использовать регулярные выражения. См. ключ [`"regexFilter"`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-RuleCondition-regexFilter) . Чтобы узнать об ограничениях, применимых к этим условиям, см. [Правила, использующие регулярные выражения](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#regex-rules) .

### Напишите хорошие условия URL

Будьте осторожны при написании правил, чтобы они всегда соответствовали всему домену. В противном случае ваше правило может сработать в непредвиденных ситуациях. Например, при использовании синтаксиса сопоставления с образцом:

-   `google.com` неправильно соответствует `https://example.com/?param=google.com`
-   `||google.com` неправильно соответствует `https://google.company`
-   `https://www.google.com` неправильно соответствует `https://example.com/?param=https://www.google.com`

Рассмотрите возможность использования:

-   `||google.com/` , который соответствует всем путям и всем поддоменам.
-   `|https://www.google.com/` который соответствует всем путям и не содержит поддоменов.

Аналогичным образом используйте символы `^` и `/` для привязки регулярного выражения. Например, `^https:\/\/www\.google\.com\/` соответствует любому пути на https://www.google.com.

## Оценка правил

Правила DNR применяются браузером на различных этапах жизненного цикла сетевого запроса.

### Перед запросом

Прежде чем запрос будет сделан, расширение может заблокировать или перенаправить его (включая обновление схемы с HTTP на HTTPS) с помощью соответствующего правила.

Для каждого расширения браузер определяет список правил соответствия. Правила с `modifyHeaders` сюда не включены, поскольку они будут обработаны позже. Кроме того, правила с условием `responseHeaders` будут рассмотрены позже (когда будут доступны заголовки ответов) и не включены.

Затем для каждого расширения Chrome выбирает не более одного кандидата на каждый запрос. Chrome находит подходящее правило, упорядочивая все соответствующие правила по приоритету. Правила с одинаковым приоритетом упорядочены по действию ( `allow` `allowAllRequests` > `block` > `upgradeScheme` > `redirect` ).

Если кандидатом является `allow` `allowAllRequests` , или кадр, в котором выполняется запрос, ранее соответствовал `allowAllRequests` с более высоким или равным приоритетом из этого расширения, запрос считается «разрешенным», и расширение не окажет никакого влияния на запрос.

Если более одного расширения хотят заблокировать или перенаправить этот запрос, выбирается одно действие. Chrome делает это, сортируя правила в `block` порядка > `redirect` `upgradeScheme` > `allow` `allowAllRequests` . Если два правила относятся к одному типу, Chrome выбирает правило из последнего установленного расширения.

Прежде чем Chrome отправит заголовки запроса на сервер, заголовки обновляются на основе соответствующих правил `modifyHeaders` .

В рамках одного расширения Chrome создает список модификаций, которые необходимо выполнить, находя все соответствующие правила `modifyHeaders` . Как и раньше, включаются только те правила, которые имеют более высокий приоритет, чем любые соответствующие `allow` `allowAllRequests` .

Эти правила применяются Chrome в таком порядке, что правила из недавно установленного расширения всегда оцениваются перед правилами из более старого расширения. Кроме того, правила с более высоким приоритетом из одного расширения всегда применяются раньше правил с более низким приоритетом из того же расширения. Примечательно, что даже среди расширений:

-   Если правило добавляется к заголовку, то правила с более низким приоритетом могут добавляться только к этому заголовку. Операции установки и удаления не допускаются.
-   Если правило устанавливает заголовок, то к этому заголовку могут добавляться только правила с более низким приоритетом из того же расширения. Никакие другие модификации не допускаются.
-   Если правило удаляет заголовок, то правила с более низким приоритетом не смогут в дальнейшем изменять заголовок.

### Как только будет получен ответ

После получения заголовков ответа Chrome оценивает правила с условием `responseHeaders` .

После сортировки этих правил по `action` и `priority` и исключения всех правил, ставших избыточными из-за соответствующего правила `allow` или `allowAllRequests` (это происходит идентично шагам, описанным в разделе «Перед запросом»), Chrome может заблокировать или перенаправить запрос от имени расширения.

Обратите внимание: если запрос дошел до этого этапа, он уже отправлен на сервер, и сервер получил данные, такие как тело запроса. Правило блокировки или перенаправления с условием заголовков ответа по-прежнему будет работать, но не сможет фактически заблокировать или перенаправить запрос.

В случае правила блокировки это обрабатывается страницей, которая отправила запрос, получая заблокированный ответ, и Chrome досрочно завершает запрос. В случае правила перенаправления Chrome отправляет новый запрос на перенаправленный URL-адрес. Обязательно подумайте, соответствуют ли эти действия ожиданиям конфиденциальности вашего расширения.

Если запрос не заблокирован или не перенаправлен, Chrome применяет все правила `modifyHeaders` . Применение изменений к заголовкам ответов работает так же, как описано в разделе «Перед отправкой заголовков запроса». Применение изменений к заголовкам запроса ничего не дает, поскольку запрос уже был сделан.

## Безопасные правила

Безопасные правила определяются как правила с `block` , `allow` , `allowAllRequests` `upgradeScheme` . На эти правила распространяется увеличенная [квота](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#dynamic-rules) динамических правил.

## Ограничения правил

Загрузка и оценка правил в браузере приводит к увеличению производительности, поэтому при использовании API применяются некоторые ограничения. Ограничения зависят от типа используемого вами правила.

### Статические правила

Статические правила — это правила, указанные в файлах правил, объявленных в файле манифеста. Расширение может указать до 100 статических [наборов правил](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) как часть ключа манифеста `"rule_resources"` , но одновременно можно включить только 50 из этих наборов правил. Последний называется [`MAX_NUMBER_OF_ENABLED_STATIC_RULESETS`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-MAX_NUMBER_OF_ENABLED_STATIC_RULESETS) . В совокупности эти наборы правил гарантируют не менее 30 000 правил. Это называется [`GUARANTEED_MINIMUM_STATIC_RULES`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-GUARANTEED_MINIMUM_STATIC_RULES) .

Количество правил, доступных после этого, зависит от того, сколько правил включено всеми расширениями, установленными в браузере пользователя. Вы можете найти это число во время выполнения, вызвав [`getAvailableStaticRuleCount()`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#method-getAvailableStaticRuleCount) . [Пример этого](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#update-static-rulesets) вы можете увидеть в разделе [«Примеры кода»](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#code-examples) .

### Правила сеанса

Расширение может иметь до 5000 правил сеанса. Это отображается как [`MAX_NUMBER_OF_SESSION_RULES`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-MAX_NUMBER_OF_SESSION_RULES) .

До Chrome 120 существовало ограничение в 5000 комбинированных динамических и сеансовых правил.

### Динамические правила

Расширение может иметь не менее 5000 динамических правил. Это отображается как [`MAX_NUMBER_OF_UNSAFE_DYNAMIC_RULES`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-MAX_NUMBER_OF_UNSAFE_DYNAMIC_RULES) .

Начиная с Chrome 121, для [безопасных](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#safe_rules) динамических правил доступен более высокий лимит в 30 000, представленный как [`MAX_NUMBER_OF_DYNAMIC_RULES`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-MAX_NUMBER_OF_DYNAMIC_RULES) . Любые небезопасные правила, добавленные в пределах лимита в 5000, также будут учитываться в этом лимите.

До Chrome 120 существовало ограничение в 5000 комбинированных динамических и сеансовых правил.

### Правила, использующие регулярные выражения

Все типы правил могут использовать регулярные выражения; однако общее количество правил регулярных выражений каждого типа не может превышать 1000. Это называется [MAX\_NUMBER\_OF\_REGEX\_RULES](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-MAX_NUMBER_OF_REGEX_RULES) .

Кроме того, каждое правило после компиляции должно занимать менее 2 КБ. Это примерно коррелирует со сложностью правила. Если вы попытаетесь загрузить правило, превышающее этот предел, вы увидите предупреждение, подобное следующему, и правило будет проигнорировано.

```
<span>rules_1</span><span>.</span><span>json</span><span>:</span><span> </span><span>Rule</span><span> </span><span>with</span><span> id </span><span>1</span><span> specified a more complex regex than allowed<br></span><span>as</span><span> part of the </span><span>"regexFilter"</span><span> key</span><span>.</span><span><br></span>
```

## Взаимодействие с работниками сервиса

declarativeNetRequest применяется только к запросам, достигающим сетевого стека. Сюда входят ответы из кэша HTTP, но могут не включаться ответы, проходящие через обработчик `onfetch` сервисного работника. declarativeNetRequest не повлияет на ответы, сгенерированные сервисным работником или полученные из `CacheStorage` , но повлияет на вызовы `fetch()` сделанные в сервисном работнике.

## Доступные веб-ресурсы

Правило declarativeNetRequest не может перенаправлять запрос общедоступного ресурса на ресурс, который недоступен через Интернет. Это вызывает ошибку. Это верно, даже если указанный доступный веб-ресурс принадлежит расширению перенаправления. Чтобы объявить ресурсы для declarativeNetRequest, используйте массив [`"web_accessible_resources"`](https://developer.chrome.com/docs/extensions/mv3/manifest/web_accessible_resources?hl=ru) манифеста.

Операция добавления поддерживается только для следующих заголовков: `accept` , `accept-encoding` , `accept-language` , `access-control-request-headers` , `cache-control` , `connection` , `content-language` , `cookie` , `forwarded` , `if-match` , `if-none-match` , `keep-alive` , `range` , `te` , `trailer` , `transfer-encoding` , `upgrade` , `user-agent` , `via` , `want-digest` , `x-forwarded-for` .

## Примеры

### Примеры кода

#### Обновить динамические правила

В следующем примере показано, как вызвать `updateDynamicRules()` . Процедура `updateSessionRules()` такая же.

```
<span>// Get arrays containing new and old rules</span><span><br></span><span>const</span><span> newRules </span><span>=</span><span> await getNewRules</span><span>();</span><span><br></span><span>const</span><span> oldRules </span><span>=</span><span> await chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>getDynamicRules</span><span>();</span><span><br></span><span>const</span><span> oldRuleIds </span><span>=</span><span> oldRules</span><span>.</span><span>map</span><span>(</span><span>rule </span><span>=&gt;</span><span> rule</span><span>.</span><span>id</span><span>);</span><span><br><br></span><span>// Use the arrays to update the dynamic rules</span><span><br>await chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>updateDynamicRules</span><span>({</span><span><br>&nbsp; removeRuleIds</span><span>:</span><span> oldRuleIds</span><span>,</span><span><br>&nbsp; addRules</span><span>:</span><span> newRules<br></span><span>});</span><span><br></span>
```

#### Обновить статические наборы правил

В следующем примере показано, как включать и отключать наборы правил, учитывая количество доступных и максимальное количество включенных статических наборов правил. Это следует сделать, когда количество необходимых статических правил превышает разрешенное количество. Чтобы это работало, некоторые из ваших наборов правил должны быть установлены, а некоторые отключены (в файле манифеста `"Enabled"` установлено значение `false` ).

```
<span>async </span><span>function</span><span> updateStaticRules</span><span>(</span><span>enableRulesetIds</span><span>,</span><span> disableCandidateIds</span><span>)</span><span> </span><span>{</span><span><br>&nbsp; </span><span>// Create the options structure for the call to updateEnabledRulesets()</span><span><br>&nbsp; let options </span><span>=</span><span> </span><span>{</span><span> enableRulesetIds</span><span>:</span><span> enableRulesetIds </span><span>}</span><span><br>&nbsp; </span><span>// Get the number of enabled static rules</span><span><br>&nbsp; </span><span>const</span><span> enabledStaticCount </span><span>=</span><span> await chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>getEnabledRulesets</span><span>();</span><span><br>&nbsp; </span><span>// Compare rule counts to determine if anything needs to be disabled so that</span><span><br>&nbsp; </span><span>// new rules can be enabled</span><span><br>&nbsp; </span><span>const</span><span> proposedCount </span><span>=</span><span> enableRulesetIds</span><span>.</span><span>length</span><span>;</span><span><br>&nbsp; </span><span>if</span><span> </span><span>(</span><span>enabledStaticCount </span><span>+</span><span> proposedCount </span><span>&gt;</span><span> chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>MAX_NUMBER_OF_ENABLED_STATIC_RULESETS</span><span>)</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; options</span><span>.</span><span>disableRulesetIds </span><span>=</span><span> disableCandidateIds<br>&nbsp; </span><span>}</span><span><br>&nbsp; </span><span>// Update the enabled static rules</span><span><br>&nbsp; await chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>updateEnabledRulesets</span><span>(</span><span>options</span><span>);</span><span><br></span><span>}</span><span><br></span>
```

### Примеры правил

Следующие примеры иллюстрируют, как Chrome определяет приоритет правил в расширении. При их просмотре вам может потребоваться открыть правила [расстановки приоритетов](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#implementation-matching-algorithm) в отдельном окне.

#### Ключ «приоритета»

Эти примеры требуют [разрешения хоста](https://developer.chrome.com/docs/extensions/mv3/declare_permissions?hl=ru) для `*://*.example.com/*` .

Чтобы определить приоритет конкретного URL-адреса, посмотрите на ключ `"priority"` (определенный разработчиком), ключ `"action"` и ключ `"urlFilter"` . Эти примеры относятся к примерному файлу правил, показанному под ними.

Переход на https://google.com

Этот URL-адрес распространяется на два правила: правила с идентификаторами 1 и 4. Правило с идентификатором 1 применяется, поскольку действия `"block"` имеют более высокий приоритет, чем действия `"redirect"` . Остальные правила не применяются, поскольку они предназначены для более длинных URL-адресов.

Переход на https://google.com/1234.

Из-за более длинного URL-адреса теперь применяется правило с идентификатором 2 в дополнение к правилам с идентификаторами 1 и 4. Правило с идентификатором 2 применяется, поскольку `"allow"` имеет более высокий приоритет, чем `"block"` и `"redirect"` .

Переход на https://google.com/12345.

Все четыре правила соответствуют этому URL. Правило с идентификатором 3 применяется, поскольку его приоритет, определенный разработчиком, является наивысшим в группе.

```
<span>[</span><span><br>&nbsp; </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"id"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"priority"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span> </span><span>"type"</span><span>:</span><span> </span><span>"block"</span><span> </span><span>},</span><span><br>&nbsp; &nbsp; </span><span>"condition"</span><span>:</span><span> </span><span>{</span><span>"urlFilter"</span><span>:</span><span> </span><span>"||google.com/"</span><span>,</span><span> </span><span>"resourceTypes"</span><span>:</span><span> </span><span>[</span><span>"main_frame"</span><span>]</span><span> </span><span>}</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"id"</span><span>:</span><span> </span><span>2</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"priority"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span> </span><span>"type"</span><span>:</span><span> </span><span>"allow"</span><span> </span><span>},</span><span><br>&nbsp; &nbsp; </span><span>"condition"</span><span>:</span><span> </span><span>{</span><span> </span><span>"urlFilter"</span><span>:</span><span> </span><span>"||google.com/123"</span><span>,</span><span> </span><span>"resourceTypes"</span><span>:</span><span> </span><span>[</span><span>"main_frame"</span><span>]</span><span> </span><span>}</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"id"</span><span>:</span><span> </span><span>3</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"priority"</span><span>:</span><span> </span><span>2</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span> </span><span>"type"</span><span>:</span><span> </span><span>"block"</span><span> </span><span>},</span><span><br>&nbsp; &nbsp; </span><span>"condition"</span><span>:</span><span> </span><span>{</span><span> </span><span>"urlFilter"</span><span>:</span><span> </span><span>"||google.com/12345"</span><span>,</span><span> </span><span>"resourceTypes"</span><span>:</span><span> </span><span>[</span><span>"main_frame"</span><span>]</span><span> </span><span>}</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"id"</span><span>:</span><span> </span><span>4</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"priority"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span> </span><span>"type"</span><span>:</span><span> </span><span>"redirect"</span><span>,</span><span> </span><span>"redirect"</span><span>:</span><span> </span><span>{</span><span> </span><span>"url"</span><span>:</span><span> </span><span>"https://example.com"</span><span> </span><span>}</span><span> </span><span>},</span><span><br>&nbsp; &nbsp; </span><span>"condition"</span><span>:</span><span> </span><span>{</span><span> </span><span>"urlFilter"</span><span>:</span><span> </span><span>"||google.com/"</span><span>,</span><span> </span><span>"resourceTypes"</span><span>:</span><span> </span><span>[</span><span>"main_frame"</span><span>]</span><span> </span><span>}</span><span><br>&nbsp; </span><span>},</span><span><br></span><span>]</span><span><br></span>
```

#### Перенаправления

В приведенном ниже примере требуется [разрешение хоста](https://developer.chrome.com/docs/extensions/mv3/declare_permissions?hl=ru) для `*://*.example.com/*` .

В следующем примере показано, как перенаправить запрос с сайта example.com на страницу внутри самого расширения. Путь расширения `/a.jpg` преобразуется в `chrome-extension://EXTENSION_ID/a.jpg` , где `EXTENSION_ID` — это идентификатор вашего расширения. Чтобы это работало, манифест должен объявить `/a.jpg` как [ресурс, доступный через Интернет](https://developer.chrome.com/docs/extensions/mv3/manifest/web_accessible_resources?hl=ru) .

```
<span>{</span><span><br>&nbsp; </span><span>"id"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"priority"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span> </span><span>"type"</span><span>:</span><span> </span><span>"redirect"</span><span>,</span><span> </span><span>"redirect"</span><span>:</span><span> </span><span>{</span><span> </span><span>"extensionPath"</span><span>:</span><span> </span><span>"/a.jpg"</span><span> </span><span>}</span><span> </span><span>},</span><span><br>&nbsp; </span><span>"condition"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"urlFilter"</span><span>:</span><span> </span><span>"||https://www.example.com/"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"resourceTypes"</span><span>:</span><span> </span><span>[</span><span>"main_frame"</span><span>]</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

Ниже используется ключ `"transform"` для перенаправления на поддомен example.com. Он использует привязку доменного имени («||») для перехвата запросов по любой схеме от example.com. Ключ `"scheme"` в `"transform"` указывает, что при перенаправлении на поддомен всегда будет использоваться «https».

```
<span>{</span><span><br>&nbsp; </span><span>"id"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"priority"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"type"</span><span>:</span><span> </span><span>"redirect"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"redirect"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"transform"</span><span>:</span><span> </span><span>{</span><span> </span><span>"scheme"</span><span>:</span><span> </span><span>"https"</span><span>,</span><span> </span><span>"host"</span><span>:</span><span> </span><span>"new.example.com"</span><span> </span><span>}</span><span><br>&nbsp; &nbsp; </span><span>}</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>"condition"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"urlFilter"</span><span>:</span><span> </span><span>"||example.com/"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"resourceTypes"</span><span>:</span><span> </span><span>[</span><span>"main_frame"</span><span>]</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

В следующем примере регулярные выражения используются для перенаправления с `https://www.abc.xyz.com/path` на `https://abc.xyz.com/path` . Обратите внимание, что в ключе `"regexFilter"` точки экранируются и что группа захвата выбирает либо «abc», либо «def». Ключ `"regexSubstitution"` указывает первое возвращаемое совпадение регулярного выражения с помощью «\\1». В этом случае «abc» извлекается из перенаправленного URL-адреса и помещается в подстановку.

```
<span>{</span><span><br>&nbsp; </span><span>"id"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"priority"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"type"</span><span>:</span><span> </span><span>"redirect"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"redirect"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"regexSubstitution"</span><span>:</span><span> </span><span>"https://\\1.xyz.com/"</span><span><br>&nbsp; &nbsp; </span><span>}</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>"condition"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"regexFilter"</span><span>:</span><span> </span><span>"^https://www\\.(abc|def)\\.xyz\\.com/"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"resourceTypes"</span><span>:</span><span> </span><span>[</span><span><br>&nbsp; &nbsp; &nbsp; </span><span>"main_frame"</span><span><br>&nbsp; &nbsp; </span><span>]</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

В следующем примере удаляются все файлы cookie как из основного кадра, так и из всех подкадров.

```
<span>{</span><span><br>&nbsp; </span><span>"id"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"priority"</span><span>:</span><span> </span><span>1</span><span>,</span><span><br>&nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"type"</span><span>:</span><span> </span><span>"modifyHeaders"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"requestHeaders"</span><span>:</span><span> </span><span>[{</span><span> </span><span>"header"</span><span>:</span><span> </span><span>"cookie"</span><span>,</span><span> </span><span>"operation"</span><span>:</span><span> </span><span>"remove"</span><span> </span><span>}]</span><span><br>&nbsp; </span><span>},</span><span><br>&nbsp; </span><span>"condition"</span><span>:</span><span> </span><span>{</span><span> </span><span>"resourceTypes"</span><span>:</span><span> </span><span>[</span><span>"main_frame"</span><span>,</span><span> </span><span>"sub_frame"</span><span>]</span><span> </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

## Типы

### DomainType

Здесь указывается, является ли запрос первой или третьей стороной по отношению к кадру, в котором он был создан. Запрос считается первичным, если он имеет тот же домен (eTLD+1), что и кадр, в котором возник запрос.

#### Перечисление

"первая вечеринка"  
Сетевой запрос является первой стороной кадра, в котором он был создан.

"третья сторона"  
Сетевой запрос является третьей стороной по отношению к кадру, в котором он был создан.

### ExtensionActionOptions

#### Характеристики

-   displayActionCountAsBadgeText
    
    логическое значение необязательно
    
    Следует ли автоматически отображать количество действий для страницы в виде текста значка расширения. Это предпочтение сохраняется во всех сеансах.
    
-   tabUpdate
    
    [TabActionCountUpdate](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-TabActionCountUpdate) необязательно.
    
    Подробная информация о том, как следует настроить количество действий на вкладке.
    

### GetDisabledRuleIdsOptions

#### Характеристики

-   Идентификатор набора правил
    
    нить
    
    Идентификатор, соответствующий статическому [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) .
    

### GetRulesFilter

#### Характеристики

-   идентификаторы правил
    
    номер\[\] необязательно
    
    Если указано, включаются только правила с совпадающими идентификаторами.
    

#### Характеристики

-   Если указано, это условие не выполняется, если заголовок существует, но его значение содержит хотя бы один элемент в этом списке. Здесь используется тот же синтаксис шаблона соответствия, что и `values` .
    
-   Название заголовка. Это условие соответствует имени, только если не указаны ни `values` , ни `excludedValues` .
    
-   Если указано, это условие соответствует, если значение заголовка соответствует хотя бы одному шаблону в этом списке. Это поддерживает сопоставление значений заголовков без учета регистра, а также следующие конструкции:
    
    **'\*'** : Соответствует любому количеству символов.
    
    **'?'** : Соответствует нулю или одному символу(ам).
    
    '\*' и '?' можно экранировать обратной косой чертой, например, '\\\*' и '\\?'
    

Здесь описаны возможные операции для правила «modifyHeaders».

#### Перечисление

"добавить"  
Добавляет новую запись для указанного заголовка. Эта операция не поддерживается для заголовков запросов.

"набор"  
Устанавливает новое значение для указанного заголовка, удаляя все существующие заголовки с тем же именем.

"удалять"  
Удаляет все записи для указанного заголовка.

### IsRegexSupportedResult

#### Характеристики

-   isSupported
    
    логическое значение
    
-   причина
    
    [UnsupportedRegexReason](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-UnsupportedRegexReason) необязательно
    
    Указывает причину, по которой регулярное выражение не поддерживается. Предоставляется только в том случае, если `isSupported` имеет значение false.
    

### MatchedRule

#### Характеристики

-   идентификатор правила
    
    число
    
    Идентификатор соответствующего правила.
    
-   Идентификатор набора правил
    
    нить
    
    Идентификатор [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) , которому принадлежит это правило. Для правила, происходящего из набора динамических правил, это значение будет равно [`DYNAMIC_RULESET_ID`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-DYNAMIC_RULESET_ID) .
    

### MatchedRuleInfo

#### Характеристики

-   идентификатор табуляции
    
    число
    
    tabId вкладки, из которой поступил запрос, если вкладка все еще активна. Остальное -1.
    
-   Время соответствия правилу. Временные метки будут соответствовать соглашению Javascript для времени, то есть количеству миллисекунд с начала эпохи.
    

### MatchedRuleInfoDebug

#### Характеристики

-   Подробная информация о запросе, для которого было сопоставлено правило.
    

### MatchedRulesFilter

#### Характеристики

-   минтиместамп
    
    номер необязательно
    
    Если указано, соответствует правилам только после указанной отметки времени.
    
-   идентификатор табуляции
    
    номер необязательно
    
    Если указано, соответствует только правилам для данной вкладки. Соответствует правилам, не связанным ни с одной активной вкладкой, если установлено значение -1.
    

#### Характеристики

-   Имя заголовка, который нужно изменить.
    
-   Операция, выполняемая над заголовком.
    
-   Новое значение для заголовка. Должен быть указан для операций `append` и `set` .
    

### QueryKeyValue

#### Характеристики

-   replaceOnly
    
    логическое значение необязательно
    
    Если это правда, ключ запроса заменяется, только если он уже существует. В противном случае ключ также добавляется, если он отсутствует. По умолчанию ложь.
    

### QueryTransform

#### Характеристики

-   аддонзаменепарамс
    
    [QueryKeyValue](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-QueryKeyValue) \[\] необязательно
    
    Список пар ключ-значение запроса, которые необходимо добавить или заменить.
    
-   удалитьПарамс
    
    строка\[\] необязательно
    
    Список ключей запроса, которые необходимо удалить.
    

### Redirect

#### Характеристики

-   путь расширения
    
    строка необязательна
    
    Путь относительно каталога расширения. Должно начинаться с '/'.
    
-   регулярное выражениеЗамена
    
    строка необязательна
    
    Шаблон подстановки для правил, определяющих `regexFilter` . Первое совпадение `regexFilter` в URL-адресе будет заменено этим шаблоном. В `regexSubstitution` цифры с обратной косой чертой (от \\1 до \\9) могут использоваться для вставки соответствующих групп захвата. \\0 относится ко всему совпадающему тексту.
    
-   трансформировать
    
    [URLTransform](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-URLTransform) необязательно
    
    Преобразования URL-адресов, которые необходимо выполнить.
    
-   URL-адрес перенаправления. Перенаправления на URL-адреса JavaScript не разрешены.
    

### RegexOptions

#### Характеристики

-   isCaseSensitive
    
    логическое значение необязательно
    
    Является ли указанное `regex` выражение чувствительным к регистру. По умолчанию верно.
    
-   регулярное выражение
    
    нить
    
    Регулярное выражение для проверки.
    
-   требуется захват
    
    логическое значение необязательно
    
    Требуется ли захват указанного `regex` . Захват требуется только для правил перенаправления, которые определяют действие `regexSubstition` . По умолчанию — ложь.
    

### RequestDetails

#### Характеристики

-   идентификатор документа
    
    строка необязательна
    
    Уникальный идентификатор документа фрейма, если этот запрос относится к фрейму.
    
-   Жизненный цикл документа фрейма, если этот запрос относится к фрейму.
    
-   идентификатор кадра
    
    число
    
    Значение 0 указывает, что запрос происходит в основном кадре; положительное значение указывает идентификатор подкадра, в котором происходит запрос. Если загружен документ (под)кадра ( `type` — `main_frame` или `sub_frame` ), `frameId` указывает идентификатор этого кадра, а не идентификатор внешнего кадра. Идентификаторы кадров уникальны в пределах вкладки.
    
-   Тип кадра, если это запрос на кадр.
    
-   инициатор
    
    строка необязательна
    
    Источник, из которого был инициирован запрос. Это не меняется при перенаправлении. Если это непрозрачное происхождение, будет использоваться строка «null».
    
-   Стандартный метод HTTP.
    
-   родительскийDocumentId
    
    строка необязательна
    
    Уникальный идентификатор родительского документа фрейма, если этот запрос относится к фрейму и имеет родительский элемент.
    
-   родительскийFrameId
    
    число
    
    Идентификатор кадра, который заключает в себе кадр, отправивший запрос. Установите значение -1, если родительский фрейм не существует.
    
-   идентификатор запроса
    
    нить
    
    Идентификатор запроса. Идентификаторы запросов уникальны в рамках сеанса браузера.
    
-   идентификатор табуляции
    
    число
    
    Идентификатор вкладки, в которой происходит запрос. Установите значение -1, если запрос не связан с вкладкой.
    
-   Тип ресурса запроса.
    
-   URL-адрес запроса.
    

### RequestMethod

Здесь описывается метод HTTP-запроса сетевого запроса.

#### Перечисление

"соединять"  

"удалить"  

"получать"  

"голова"  

"параметры"  

"пластырь"  

"почта"  

"помещать"  

"другой"  

### ResourceType

Это описывает тип ресурса сетевого запроса.

#### Перечисление

"основной\_фрейм"  

"под\_кадр"  

"таблица стилей"  

"сценарий"  

"изображение"  

"шрифт"  

"объект"  

"xmlhttprequest"  

"пинг"  

"csp\_report"  

"СМИ"  

"веб-сокет"  

"вебтранспорт"  

"паутина"  

"другой"  

### Rule

#### Характеристики

-   Действие, которое необходимо предпринять, если это правило соответствует.
    
-   Условие, при котором срабатывает это правило.
    
-   Идентификатор, который однозначно идентифицирует правило. Обязательный и должен быть >= 1.
    
-   приоритет
    
    номер необязательно
    
    Приоритет правила. По умолчанию — 1. Если указано, должно быть >= 1.
    

### RuleAction

#### Характеристики

-   перенаправить
    
    [Перенаправление](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Redirect) необязательно
    
    Описывает, как должно выполняться перенаправление. Действует только для правил перенаправления.
    
-   [ModifyHeaderInfo](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-ModifyHeaderInfo) \[\] необязательно
    
    Заголовки запроса, которые необходимо изменить для запроса. Допустимо только в том случае, если RuleActionType имеет значение «modifyHeaders».
    
-   [ModifyHeaderInfo](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-ModifyHeaderInfo) \[\] необязательно
    
    Заголовки ответов, которые необходимо изменить для запроса. Допустимо только в том случае, если RuleActionType имеет значение «modifyHeaders».
    
-   Тип действия, которое необходимо выполнить.
    

### RuleActionType

Описывает тип действия, которое необходимо предпринять, если заданное RuleCondition соответствует.

#### Перечисление

"блокировать"  
Заблокируйте сетевой запрос.

"перенаправление"  
Перенаправить сетевой запрос.

"позволять"  
Разрешите сетевой запрос. Запрос не будет перехвачен, если существует разрешающее правило, соответствующее ему.

"схема обновления"  
Обновите схему URL-адреса сетевого запроса на https, если запрос http или ftp.

"изменить заголовки"  
Измените заголовки запроса/ответа из сетевого запроса.

"разрешитьВсе запросы"  
Разрешить все запросы в иерархии кадров, включая сам запрос кадра.

### RuleCondition

#### Характеристики

-   тип домена
    
    [Тип домена](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-DomainType) необязательно
    
    Указывает, является ли сетевой запрос собственным или сторонним по отношению к домену, из которого он исходит. Если этот параметр опущен, все запросы принимаются.
    
-   домены
    
    строка\[\] необязательно
    
    Устарело с версии Chrome 101.
    
    Вместо этого используйте [`initiatorDomains`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-RuleCondition-initiatorDomains)
    
    Правило будет соответствовать только сетевым запросам, исходящим из списка `domains` .
    
-   исключенные домены
    
    строка\[\] необязательно
    
    Устарело с версии Chrome 101.
    
    Вместо этого используйте [`excludedInitiatorDomains`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-RuleCondition-excludedInitiatorDomains) .
    
    Правило не будет соответствовать сетевым запросам, исходящим из списка `excludedDomains` .
    
-   исключенные инициатордомены
    
    строка\[\] необязательно
    
    Правило не будет соответствовать сетевым запросам, исходящим из списка `excludedInitiatorDomains` . Если список пуст или опущен, домены не исключаются. Это имеет приоритет над `initiatorDomains` .
    
    Примечания:
    
    -   Также разрешены субдомены, такие как «a.example.com».
    -   Записи должны состоять только из символов ASCII.
    -   Используйте кодировку punycode для интернационализированных доменов.
    -   Это соответствует инициатору запроса, а не URL-адресу запроса.
    -   Субдомены перечисленных доменов также исключены.
-   исключенный запросдомены
    
    строка\[\] необязательно
    
    Правило не будет соответствовать сетевым запросам, если домены соответствуют одному из списка `excludedRequestDomains` . Если список пуст или опущен, домены не исключаются. Это имеет приоритет над `requestDomains` .
    
    Примечания:
    
    -   Также разрешены субдомены, такие как «a.example.com».
    -   Записи должны состоять только из символов ASCII.
    -   Используйте кодировку punycode для интернационализированных доменов.
    -   Субдомены перечисленных доменов также исключены.
-   исключенные методы запроса
    
    [RequestMethod](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-RequestMethod) \[\] необязательный
    
    Список методов запроса, которым правило не соответствует. Должен быть указан только один из `requestMethods` и `excludedRequestMethods` . Если ни один из них не указан, сопоставляются все методы запроса.
    
-   исключенныересаурцетипес
    
    [ТипРесурса](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-ResourceType) \[\] необязательно
    
    Список типов ресурсов, которым не будет соответствовать правило. Должен быть указан только один из `resourceTypes` и `excludedResourceTypes` . Если ни один из них не указан, блокируются все типы ресурсов, кроме «main\_frame».
    
-   [HeaderInfo](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-HeaderInfo) \[\] необязательно
    
    Правило не соответствует, если запрос соответствует какому-либо условию заголовка ответа в этом списке (если указано). Если указаны оба `excludedResponseHeaders` и `responseHeaders` , то свойство `excludedResponseHeaders` имеет приоритет.
    
-   исключенныеTabIds
    
    номер\[\] необязательно
    
    Список [`tabs.Tab.id`](https://developer.chrome.com/docs/extensions/reference/tabs/?hl=ru#property-Tab-id) , которым правило не должно соответствовать. Идентификатор [`tabs.TAB_ID_NONE`](https://developer.chrome.com/docs/extensions/reference/tabs/?hl=ru#property-TAB_ID_NONE) исключает запросы, исходящие не от вкладки. Поддерживается только для правил на уровне сеанса.
    
-   домены инициатора
    
    строка\[\] необязательно
    
    Правило будет соответствовать только сетевым запросам, исходящим из списка `initiatorDomains` . Если список опущен, правило применяется к запросам со всех доменов. Пустой список не допускается.
    
    Примечания:
    
    -   Также разрешены субдомены, такие как «a.example.com».
    -   Записи должны состоять только из символов ASCII.
    -   Используйте кодировку punycode для интернационализированных доменов.
    -   Это соответствует инициатору запроса, а не URL-адресу запроса.
    -   Субдомены перечисленных доменов также совпадают.
-   isUrlFilterCaseSensitive
    
    логическое значение необязательно
    
    Учитывает ли `urlFilter` или `regexFilter` (в зависимости от того, что указано) регистр. По умолчанию — ложь.
    
-   регулярное выражениеФильтр
    
    строка необязательна
    
    Регулярное выражение для сопоставления с URL-адресом сетевого запроса. Это соответствует [синтаксису RE2](https://github.com/google/re2/wiki/Syntax) .
    
    Примечание. Можно указать только один из `urlFilter` или `regexFilter` .
    
    Примечание. `regexFilter` должен состоять только из символов ASCII. Это сопоставляется с URL-адресом, в котором хост закодирован в формате punycode (в случае интернационализированных доменов), а любые другие символы, отличные от ascii, имеют URL-адрес, закодированный в utf-8.
    
-   запросДомены
    
    строка\[\] необязательно
    
    Правило будет соответствовать сетевым запросам только в том случае, если домен соответствует одному из списка `requestDomains` . Если список опущен, правило применяется к запросам со всех доменов. Пустой список не допускается.
    
    Примечания:
    
    -   Также разрешены субдомены, такие как «a.example.com».
    -   Записи должны состоять только из символов ASCII.
    -   Используйте кодировку punycode для интернационализированных доменов.
    -   Субдомены перечисленных доменов также совпадают.
-   Методы запроса
    
    [RequestMethod](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-RequestMethod) \[\] необязательный
    
    Список методов HTTP-запросов, которым может соответствовать правило. Пустой список не допускается.
    
    Примечание. Указание условия правила `requestMethods` также будет исключать запросы, отличные от HTTP, тогда как указание `excludedRequestMethods` — нет.
    
-   типы ресурсов
    
    [ТипРесурса](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-ResourceType) \[\] необязательно
    
    Список типов ресурсов, которым может соответствовать правило. Пустой список не допускается.
    
    Примечание. Это значение должно быть указано для `allowAllRequests` и может включать только типы ресурсов `sub_frame` и `main_frame` .
    
-   [HeaderInfo](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-HeaderInfo) \[\] необязательно
    
    Правило соответствует, если запрос соответствует какому-либо условию заголовка ответа в этом списке (если указано).
    
-   tabIds
    
    номер\[\] необязательно
    
    Список [`tabs.Tab.id`](https://developer.chrome.com/docs/extensions/reference/tabs/?hl=ru#property-Tab-id) , которым должно соответствовать правило. Идентификатор [`tabs.TAB_ID_NONE`](https://developer.chrome.com/docs/extensions/reference/tabs/?hl=ru#property-TAB_ID_NONE) соответствует запросам, исходящим не от вкладки. Пустой список не допускается. Поддерживается только для правил на уровне сеанса.
    
-   urlFilter
    
    строка необязательна
    
    Шаблон, который сопоставляется с URL-адресом сетевого запроса. Поддерживаемые конструкции:
    
    **'\*'** : Подстановочный знак: соответствует любому количеству символов.
    
    **'|'** : Левый/правый якорь: если используется на любом конце шаблона, указывает начало/конец URL соответственно.
    
    **'||'** : Доменное имя якорь: если используется в начале шаблона, указывает начало (суб) домена URL.
    
    **'^'** : Символ сепаратора: это соответствует чему -либо, кроме буквы, цифры или одной из следующих: `_` , `-` , `.` , или `%` . Это также соответствует концу URL.
    
    Поэтому `urlFilter` состоит из следующих частей: (Необязательно якорь влево/доменное имя) + шаблон + (необязательный правый якорь).
    
    Если опущены, все URL -адреса соответствуют. Пустая строка не разрешена.
    
    Шаблон, начиная с `||*` не допускается. Используйте `*` вместо этого.
    
    Примечание: может быть указана только один из `urlFilter` или `regexFilter` .
    
    Примечание. `urlFilter` должен состоять только из символов ASCII. Это соответствует URL-адресу, в котором хост кодируется в формате Punycode (в случае интернационализированных доменов), а любые другие не ASCII-символы кодируются URL в UTF-8. Например, когда URL-адрес запроса составляет http: //abc.rf? Q = f, `urlFilter` будет сопоставлен с URL http: //abc.xn--p1ai/? Q =%d1%84.
    

### Ruleset

#### Характеристики

-   включено
    
    логическое значение
    
    Будет ли набор правил включена по умолчанию.
    
-   Непустые строки однозначно идентифицируя набор правил. Идентификаторы, начиная с '\_', зарезервированы для внутреннего использования.
    
-   Путь к набору правил JSON относительно каталога расширения.
    

### RulesMatchedDetails

#### Характеристики

-   Правила, соответствующие данному фильтру.
    

### TabActionCountUpdate

#### Характеристики

-   Сумма, чтобы увеличить количество действий вкладки. Отрицательные значения уменьшат счет.
    
-   Вкладка, для которой можно обновить количество действий.
    

### TestMatchOutcomeResult

#### Характеристики

-   Matchedrules
    
    [MatchedRule](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-MatchedRule) \[\]
    
    Правила (если таковые имеются), которые соответствуют гипотетическому запросу.
    

### TestMatchRequestDetails

#### Характеристики

-   инициатор
    
    Строка необязательно
    
    URL инициатора (если есть) для гипотетического запроса.
    
-   метод
    
    [RequestMethod](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-RequestMethod) необязательно
    
    Стандартный метод HTTP гипотетического запроса. По умолчанию «получить» для HTTP-запросов и игнорируется для не HTTP-запросов.
    
-   Заголовки, предоставленные гипотетическим ответом, если запрос не заблокирован или перенаправлен до его отправки. Представлен как объект, который отображает имя заголовка в список строковых значений. Если не указано, гипотетический ответ будет возвращать пустые заголовки ответа, которые могут соответствовать правилам, которые соответствуют небыванию заголовков. Например `{"content-type": ["text/html; charset=utf-8", "multipart/form-data"]}`
    
-   табид
    
    номер необязательно
    
    Идентификатор вкладки, в которой происходит гипотетический запрос. Не нужно соответствовать реальному идентификатору вкладки. По умолчанию -1, что означает, что запрос не связан с вкладкой.
    
-   Тип ресурса гипотетического запроса.
    
-   URL гипотетического запроса.
    

### UnsupportedRegexReason

Описывает причину, по которой данное регулярное выражение не поддерживается.

#### Перевозить

"Синтаксиртор"  
Регулярное выражение является синтаксически неверным или использует функции, недоступные в [синтаксисе RE2](https://github.com/google/re2/wiki/Syntax) .

"MemoryLimitexeded"  
Регулярное выражение превышает предел памяти.

### UpdateRuleOptions

#### Характеристики

-   addrules
    
    [Правило](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Rule) \[\] необязательно
    
    Правила добавить.
    
-   Removeruleids
    
    номер \[\] необязательно
    
    Идентификаторы правил для удаления. Любые неверные идентификаторы будут игнорированы.
    

### UpdateRulesetOptions

#### Характеристики

-   Divablorulesetids
    
    string \[\] необязательно
    
    Набор идентификаторов, соответствующий статическому [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) , который должен быть отключен.
    
-   eNablerulesTids
    
    string \[\] необязательно
    
    Набор идентификаторов, соответствующий статическому [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) , который должен быть включен.
    

### UpdateStaticRulesOptions

#### Характеристики

-   Distableruleids
    
    номер \[\] необязательно
    
    Набор идентификаторов, соответствующих правилам на [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) , чтобы отключить.
    
-   Enableruleids
    
    номер \[\] необязательно
    
    Набор идентификаторов, соответствующих правилам на [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) для включения.
    
-   Идентификатор, соответствующий статическому [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) .
    

### URLTransform

#### Характеристики

-   фрагмент
    
    Строка необязательно
    
    Новый фрагмент для запроса. Должен быть либо пустым, и в этом случае существующий фрагмент очищается; или начинаться с '#'.
    
-   хозяин
    
    Строка необязательно
    
    Новый хост для запроса.
    
-   пароль
    
    Строка необязательно
    
    Новый пароль для запроса.
    
-   путь
    
    Строка необязательно
    
    Новый путь для запроса. Если пуст, существующий путь очищается.
    
-   порт
    
    Строка необязательно
    
    Новый порт для запроса. Если пуст, существующий порт очищается.
    
-   запрос
    
    Строка необязательно
    
    Новый запрос для запроса. Должен быть либо пустым, и в этом случае существующий запрос очищается; Или начать с '?'.
    
-   QueryTransform
    
    [QueryTransform](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-QueryTransform) необязательно
    
    Добавьте, удалите или замените пары значений клавиш запроса.
    
-   схема
    
    Строка необязательно
    
    Новая схема для запроса. Разрешенными значениями являются «http», «https», «ftp» и «chrome-extension».
    
-   имя пользователя
    
    Строка необязательно
    
    Новое имя пользователя для запроса.
    

## Характеристики

### DYNAMIC\_RULESET\_ID

Идентификатор набора правил для динамических правил, добавленных расширением.

### GETMATCHEDRULES\_QUOTA\_INTERVAL

Временный интервал, в котором могут быть сделаны вызовы `MAX_GETMATCHEDRULES_CALLS_PER_INTERVAL getMatchedRules` , указаны в минуты. Дополнительные вызовы сразу не будут сбой и установят [`runtime.lastError`](https://developer.chrome.com/docs/extensions/reference/runtime/?hl=ru#property-lastError) . LasterRor. ПРИМЕЧАНИЕ. Вызовы `getMatchedRules` , связанные с жестом пользователя, освобождены от квоты.

### GUARANTEED\_MINIMUM\_STATIC\_RULES

Минимальное количество статических правил гарантированно продление на его включенных статических наборах правил. Любые правила выше этого предела будут учитываться в отношении [глобального ограничения статического правила](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest/?hl=ru#global-static-rule-limit) .

### MAX\_GETMATCHEDRULES\_CALLS\_PER\_INTERVAL

Количество раз, когда `getMatchedRules` можно вызывать в течение периода `GETMATCHEDRULES_QUOTA_INTERVAL` .

### MAX\_NUMBER\_OF\_DYNAMIC\_RULES

Максимальное количество динамических правил, которые может добавить расширение.

### MAX\_NUMBER\_OF\_ENABLED\_STATIC\_RULESETS

Максимальное количество статических `Rulesets` которые расширение может включить в любое время.

### MAX\_NUMBER\_OF\_REGEX\_RULES

Максимальное количество правил регулярного выражения, которые может добавить расширение. Этот предел оценивается отдельно для набора динамических правил и указанных в файле ресурсов правил.

### MAX\_NUMBER\_OF\_SESSION\_RULES

Максимальное количество правил сферы сеанса, которые может добавить расширение.

### MAX\_NUMBER\_OF\_STATIC\_RULESETS

Максимальное количество статических `Rulesets` расширение может указать как часть манифестного ключа `"rule_resources"` .

### MAX\_NUMBER\_OF\_UNSAFE\_DYNAMIC\_RULES

Максимальное количество «небезопасных» динамических правил, которые может добавить расширение.

### MAX\_NUMBER\_OF\_UNSAFE\_SESSION\_RULES

Максимальное количество «небезопасных» сессионных правил, которые может добавить расширение.

### SESSION\_RULESET\_ID

Идентификатор набора правил для правил с сеансом, добавленным расширением.

## Методы

### getAvailableStaticRuleCount()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>getAvailableStaticRuleCount</span><span>(</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Возвращает количество статических правил, которые может включить расширение до достижения [глобального ограничения статического правила](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest/?hl=ru#global-static-rule-limit) .

#### Параметры

-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>(</span><span>count</span><span>:</span><span> number</span><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### getDisabledRuleIds()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>getDisabledRuleIds</span><span>(</span><span><br>&nbsp; options</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-GetDisabledRuleIdsOptions"><span>GetDisabledRuleIdsOptions</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Возвращает список статических правил в данном [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) , которые в настоящее время отключены.

#### Параметры

-   Определяет набор правил для запроса.
    
-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>(</span><span>disabledRuleIds</span><span>:</span><span> number</span><span>[])</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### getDynamicRules()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>getDynamicRules</span><span>(</span><span><br>&nbsp; filter</span><span>?:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-GetRulesFilter"><span>GetRulesFilter</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Возвращает текущий набор динамических правил для расширения. Абоненты могут необязательно отфильтровать список извлеченных правил, указав `filter` .

#### Параметры

-   фильтр
    
    [GetRulesFilter](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-GetRulesFilter) необязательно
    
    Объект для фильтрации списка извлеченных правил.
    
-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>(</span><span>rules</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Rule"><span>Rule</span></a><span>[])</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### getEnabledRulesets()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>getEnabledRulesets</span><span>(</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Возвращает идентификаторы для текущего набора включенных статических наборов правил.

#### Параметры

-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>(</span><span>rulesetIds</span><span>:</span><span> </span><span>string</span><span>[])</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### getMatchedRules()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>getMatchedRules</span><span>(</span><span><br>&nbsp; filter</span><span>?:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-MatchedRulesFilter"><span>MatchedRulesFilter</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Возвращает все правила, соответствующие расширению. Абоненты могут необязательно отфильтровать список соответствующих правил, указав `filter` . Этот метод доступен только для расширений с разрешением `"declarativeNetRequestFeedback"` или с разрешением `"activeTab"` , предоставленным для `tabId` , указанного в `filter` . ПРИМЕЧАНИЕ. Правила, не связанные с активным документом, который соответствовал более пяти минутам назад, не будут возвращены.

#### Параметры

-   фильтр
    
    [MatchedRulesfilter](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-MatchedRulesFilter) необязательно
    
    Объект для фильтрации списка соответствующих правил.
    
-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>(</span><span>details</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-RulesMatchedDetails"><span>RulesMatchedDetails</span></a><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещание < [правила MatchedDetails](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-RulesMatchedDetails) >
    
    Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### getSessionRules()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>getSessionRules</span><span>(</span><span><br>&nbsp; filter</span><span>?:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-GetRulesFilter"><span>GetRulesFilter</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Возвращает текущий набор правил сферы сеанса для расширения. Абоненты могут необязательно отфильтровать список извлеченных правил, указав `filter` .

#### Параметры

-   фильтр
    
    [GetRulesFilter](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-GetRulesFilter) необязательно
    
    Объект для фильтрации списка извлеченных правил.
    
-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>(</span><span>rules</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Rule"><span>Rule</span></a><span>[])</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### isRegexSupported()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>isRegexSupported</span><span>(</span><span><br>&nbsp; regexOptions</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-RegexOptions"><span>RegexOptions</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Проверяет, если данное регулярное выражение будет поддерживаться как условие правила `regexFilter` .

#### Параметры

-   Регулярное выражение для проверки.
    
-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>(</span><span>result</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-IsRegexSupportedResult"><span>IsRegexSupportedResult</span></a><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### setExtensionActionOptions()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>setExtensionActionOptions</span><span>(</span><span><br>&nbsp; options</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-ExtensionActionOptions"><span>ExtensionActionOptions</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Настройка, если количество действий для вкладок должно отображаться в качестве текста значка действия расширения и предоставляет способ увеличить количество действий.

#### Параметры

-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### testMatchOutcome()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>testMatchOutcome</span><span>(</span><span><br>&nbsp; request</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-TestMatchRequestDetails"><span>TestMatchRequestDetails</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Проверяет, что какое -либо из правил DeclarativenetRequest в продлении соответствует гипотетическому запросу. Примечание. Доступно только для распакованных расширений, так как это предназначено только для развития расширения.

#### Параметры

-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>(</span><span>result</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-TestMatchOutcomeResult"><span>TestMatchOutcomeResult</span></a><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### updateDynamicRules()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>updateDynamicRules</span><span>(</span><span><br>&nbsp; options</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-UpdateRuleOptions"><span>UpdateRuleOptions</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Изменяет текущий набор динамических правил для расширения. Правила с идентификаторами, перечисленными в `options.removeRuleIds` сначала удаляются, а затем добавляются правила, приведенные в `options.addRules` . Примечания:

-   Это обновление происходит как одна атомная операция: либо добавляются и удаляются все указанные правила, либо возвращается ошибка.
-   Эти правила сохраняются между сеансами браузера и по обновлениям расширения.
-   Статические правила, указанные как часть пакета расширения, не могут быть удалены с использованием этой функции.
-   [`MAX_NUMBER_OF_DYNAMIC_RULES`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-MAX_NUMBER_OF_DYNAMIC_RULES) - это максимальное количество динамических правил, которые может добавить расширение. Количество [небезопасных правил](https://developer.chrome.com/docs/extensions/reference/declarativeNetRequest/?hl=ru#safe_rules) не должно превышать [`MAX_NUMBER_OF_UNSAFE_DYNAMIC_RULES`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-MAX_NUMBER_OF_UNSAFE_DYNAMIC_RULES) .

#### Параметры

-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### updateEnabledRulesets()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>updateEnabledRulesets</span><span>(</span><span><br>&nbsp; options</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-UpdateRulesetOptions"><span>UpdateRulesetOptions</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Обновляет набор включенных статических наборов правил для расширения. Наборы правил с идентификаторами, перечисленными в `options.disableRulesetIds` , сначала удаляются, а затем добавляются наборы правил, перечисленные в `options.enableRulesetIds` . Обратите внимание, что набор включенных статических наборов правил сохраняется в разных сеансах, но не по обновлениям расширения, то есть ключ Manifest `rule_resources` будет определять набор включенных статических наборов правил при каждом обновлении расширения.

#### Параметры

-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### updateSessionRules()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>updateSessionRules</span><span>(</span><span><br>&nbsp; options</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-UpdateRuleOptions"><span>UpdateRuleOptions</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Изменяет текущий набор правил сферы сеанса для расширения. Правила с идентификаторами, перечисленными в `options.removeRuleIds` сначала удаляются, а затем добавляются правила, приведенные в `options.addRules` . Примечания:

-   Это обновление происходит как одна атомная операция: либо добавляются и удаляются все указанные правила, либо возвращается ошибка.
-   Эти правила не сохраняются в разных сессиях и поддерживаются в памяти.
-   [`MAX_NUMBER_OF_SESSION_RULES`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#property-MAX_NUMBER_OF_SESSION_RULES) - это максимальное количество правил сеанса, которое может добавить расширение.

#### Параметры

-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

### updateStaticRules()

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>updateStaticRules</span><span>(</span><span><br>&nbsp; options</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-UpdateStaticRulesOptions"><span>UpdateStaticRulesOptions</span></a><span>,</span><span><br>&nbsp; callback</span><span>?:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Отключает и позволяет отдельным статическим правилам на [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) . Изменения в правилах, принадлежащих к сбору [`Ruleset`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-Ruleset) отключения, вступят в силу в следующий раз, когда он станет включенным.

#### Параметры

-   перезвонить
    
    функция необязательно
    
    Параметр `callback` выглядит как:
    
    ```
    <span>()</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

#### Возврат

-   Обещания поддерживаются в Manifest V3 и позже, но обратные вызовы предоставляются для обратной совместимости. Вы не можете использовать оба на одном и том же вызове функции. Обещание решается с тем же типом, который передается обратном вызове.
    

## События

### onRuleMatchedDebug

```
<span>chrome</span><span>.</span><span>declarativeNetRequest</span><span>.</span><span>onRuleMatchedDebug</span><span>.</span><span>addListener</span><span>(</span><span><br>&nbsp; callback</span><span>:</span><span> </span><span>function</span><span>,</span><span><br></span><span>)</span>
```

Уволен, когда правило сопоставлено с запросом. Доступно только для распакованных расширений с разрешением `"declarativeNetRequestFeedback"` поскольку это предназначено для использования только для целей отладки.

#### Параметры

-   Параметр `callback` выглядит как:
    
    ```
    <span>(</span><span>info</span><span>:</span><span> </span><a href="https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru#type-MatchedRuleInfoDebug"><span>MatchedRuleInfoDebug</span></a><span>)</span><span> </span><span>=&gt;</span><span> </span><span>void</span>
    ```
    

Если не указано иное, контент на этой странице предоставляется по [лицензии Creative Commons "С указанием авторства 4.0"](https://creativecommons.org/licenses/by/4.0/), а примеры кода – по [лицензии Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0). Подробнее об этом написано в [правилах сайта](https://developers.google.com/site-policies?hl=ru). Java – это зарегистрированный товарный знак корпорации Oracle и ее аффилированных лиц.

Последнее обновление: 2025-01-08 UTC.
