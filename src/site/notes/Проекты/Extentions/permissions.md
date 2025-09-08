---
{"dg-publish":true,"created":"2025-01-31T16:43:12 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/extensions/reference/permissions-list?hl=ru","author":null,"permalink":"/proekty/extentions/permissions/","dgPassFrontmatter":true}
---


# Разрешения  |  Permissions  |  Chrome for Developers

> ## Excerpt
> Список разрешений и предупреждений пользователей, доступных на платформе расширений.

---
[Skip to main content](https://developer.chrome.com/docs/extensions/reference/permissions-list?hl=ru#main-content)

 [![Chrome for Developers](https://www.gstatic.com/devrel-devsite/prod/v0f39da1ecc369fa6a1c816bfa5d8f549228499e733c9bd8becc473543aa6caa2/chrome/images/lockup.svg)](https://developer.chrome.com/)

## Разрешения

bookmark\_border Оптимизируйте свои подборки Сохраняйте и классифицируйте контент в соответствии со своими настройками.

Чтобы получить доступ к большинству API и функций расширений, вы должны объявить разрешения в [манифесте](https://developer.chrome.com/docs/extensions/reference/manifest?hl=ru) вашего расширения. Некоторые разрешения вызывают предупреждения, которые пользователи должны разрешить, чтобы продолжить использование расширения.

Дополнительные сведения о том, как работают разрешения, см. в [разделе Объявление разрешений](https://developer.chrome.com/docs/extensions/develop/concepts/declare-permissions?hl=ru) . Рекомендации по использованию разрешений с предупреждениями см. в разделе [Рекомендации по предупреждениям о разрешениях](https://developer.chrome.com/docs/extensions/develop/concepts/permission-warnings?hl=ru) .

Ниже приведен список всех доступных разрешений и всех предупреждений, вызванных конкретными разрешениями.

`"accessibilityFeatures.modify"`

Позволяет расширениям изменять состояния функций специальных возможностей при использовании API `chrome.accessibilityFeatures` .  
Отображается предупреждение: _измените настройки специальных возможностей._

`"accessibilityFeatures.read"`

Позволяет расширениям считывать состояния доступности при использовании API `chrome.accessibilityFeatures` .  
Отображается предупреждение: _прочтите настройки специальных возможностей._

`"activeTab"`

Предоставляет временный доступ к активной вкладке с помощью жеста пользователя. Подробности см. в [`activeTab`](https://developer.chrome.com/docs/extensions/develop/concepts/activeTab?hl=ru) .

`"alarms"`

Предоставляет доступ к API [`chrome.alarms`](https://developer.chrome.com/docs/extensions/reference/api/alarms?hl=ru) .

`"audio"`

Предоставляет доступ к API [`chrome.audio`](https://developer.chrome.com/docs/extensions/reference/api/audio?hl=ru) .

`"background"`

Заставляет Chrome запускаться раньше (как только пользователь входит в свой компьютер, прежде чем он запустит Chrome) и позже закрываться (даже после закрытия последнего окна, пока пользователь явно не выйдет из Chrome).

`"bookmarks"`

Предоставляет доступ к API [`chrome.bookmarks`](https://developer.chrome.com/docs/extensions/reference/api/bookmarks?hl=ru) .  
Отображается предупреждение: _Прочтите и измените свои закладки._

`"browsingData"`

Предоставляет доступ к API [`chrome.browsingData`](https://developer.chrome.com/docs/extensions/reference/api/browsingData?hl=ru) .

`"certificateProvider"`

Предоставляет доступ к API [`chrome.certificateProvider`](https://developer.chrome.com/docs/extensions/reference/api/certificateProvider?hl=ru) .

`"clipboardRead"`

Позволяет расширению вставлять элементы из буфера обмена с помощью [API буфера обмена](https://developer.mozilla.org/docs/Web/API/Clipboard_API) веб-платформы.  
Отображается предупреждение: _прочтите данные, которые вы копируете и вставляете._

`"clipboardWrite"`

Позволяет расширению вырезать и копировать элементы в буфер обмена с помощью [API буфера обмена](https://developer.mozilla.org/docs/Web/API/Clipboard_API) веб-платформы.  
Отображается предупреждение: _измените данные, которые вы копируете и вставляете._

`"contentSettings"`

Предоставляет доступ к API [`chrome.contentSettings`](https://developer.chrome.com/docs/extensions/reference/api/contentSettings?hl=ru) .  
Отображается предупреждение: _измените настройки, которые контролируют доступ веб-сайтов к таким функциям, как файлы cookie, JavaScript, плагины, геолокация, микрофон, камера и т. д._

`"contextMenus"`

Предоставляет доступ к API [`chrome.contextMenus`](https://developer.chrome.com/docs/extensions/reference/api/contextMenus?hl=ru) .

`"cookies"`

Предоставляет доступ к API [`chrome.cookies`](https://developer.chrome.com/docs/extensions/reference/api/cookies?hl=ru) .

`"debugger"`

Предоставляет доступ к API [`chrome.debugger`](https://developer.chrome.com/docs/extensions/reference/api/debugger?hl=ru) .  
Отображаются предупреждения:  

-   _Получите доступ к серверной части отладчика страниц._
-   _Прочитайте и измените все свои данные на всех сайтах._

`"declarativeContent"`

Предоставляет доступ к API [`chrome.declarativeContent`](https://developer.chrome.com/docs/extensions/reference/api/declarativeContent?hl=ru) .

`"declarativeNetRequest"`

Предоставляет доступ к API [`chrome.declarativeNetRequest`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru) .  
Отображается предупреждение: _заблокируйте содержимое на любой странице._

`"declarativeNetRequestWithHostAccess"`

Предоставляет доступ к API [`chrome.declarativeNetRequest`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru) , но требует разрешений хоста для всех действий.

`"declarativeNetRequestFeedback"`

Дает разрешение на запись ошибок и предупреждений в консоль DevTools при использовании API [`chrome.declarativeNetRequest`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru) . Это разрешение предназначено для использования с распакованными расширениями и игнорируется для расширений, установленных из Интернет-магазина Chrome.  
Отображается предупреждение: _прочтите историю просмотров._

`"dns"`

Предоставляет доступ к API `chrome.dns` .

`"desktopCapture"`

Предоставляет доступ к API [`chrome.desktopCapture`](https://developer.chrome.com/docs/extensions/reference/api/desktopCapture?hl=ru) .  
Отображается предупреждение: _Захват содержимого экрана._

`"documentScan"`

Предоставляет доступ к API [`chrome.documentScan`](https://developer.chrome.com/docs/extensions/reference/api/documentScan?hl=ru) .

`"downloads"`

Предоставляет доступ к API [`chrome.downloads`](https://developer.chrome.com/docs/extensions/reference/api/downloads?hl=ru) .  
Отображается предупреждение: _Управляйте загрузками._

`"downloads.open"`

Позволяет использовать [`chrome.downloads.open()`](https://developer.chrome.com/docs/extensions/reference/api/downloads?hl=ru#method-open) .  
Отображается предупреждение: _Управляйте загрузками._

`"downloads.ui"`

Позволяет использовать [`chrome.downloads.setUiOptions()`](https://developer.chrome.com/docs/extensions/reference/api/downloads?hl=ru#method-setUiOptions) .  
Отображается предупреждение: _Управляйте загрузками._

`"enterprise.deviceAttributes"`

Предоставляет доступ к API [`chrome.enterprise.deviceAttributes`](https://developer.chrome.com/docs/extensions/reference/api/enterprise/deviceAttributes?hl=ru) .

`"enterprise.hardwarePlatform"`

Предоставляет доступ к API [`chrome.enterprise.hardwarePlatform`](https://developer.chrome.com/docs/extensions/reference/api/enterprise/hardwarePlatform?hl=ru) .

`"enterprise.networkingAttributes"`

Предоставляет доступ к API [`chrome.enterprise.networkingAttributes`](https://developer.chrome.com/docs/extensions/reference/api/enterprise/networkingAttributes?hl=ru) .

`"enterprise.platformKeys"`

Предоставляет доступ к API [`chrome.enterprise.platformKeys`](https://developer.chrome.com/docs/extensions/reference/api/enterprise/platformKeys?hl=ru) .

`"favicon"`

Предоставляет доступ к API [Favicon](https://developer.chrome.com/docs/extensions/how-to/ui/favicons?hl=ru) .  
Отображается предупреждение: _прочтите значки веб-сайтов, которые вы посещаете._

`"fileBrowserHandler"`

Предоставляет доступ к API [`chrome.fileBrowserHandler`](https://developer.chrome.com/docs/extensions/reference/api/fileBrowserHandler?hl=ru) .

`"fileSystemProvider"`

Предоставляет доступ к API [`chrome.fileSystemProvider`](https://developer.chrome.com/docs/extensions/reference/api/fileSystemProvider?hl=ru) .

`"fontSettings"`

Предоставляет доступ к API [`chrome.fontSettings`](https://developer.chrome.com/docs/extensions/reference/api/fontSettings?hl=ru) .

`"gcm"`

Предоставляет доступ к API [`chrome.gcm`](https://developer.chrome.com/docs/extensions/reference/api/gcm?hl=ru) и [`chrome.instanceID`](https://developer.chrome.com/docs/extensions/reference/api/instanceID?hl=ru) .

`"geolocation"`

Позволяет расширению использовать API геолокации, не запрашивая разрешения у пользователя.  
Отображается предупреждение: _Определите свое физическое местоположение._

`"history"`

Предоставляет доступ к API [`chrome.history`](https://developer.chrome.com/docs/extensions/reference/api/history?hl=ru) .  
Отображается предупреждение: _прочитайте и измените историю просмотров на всех устройствах, на которых выполнен вход._

`"identity"`

Предоставляет доступ к API [`chrome.identity`](https://developer.chrome.com/docs/extensions/reference/api/identity?hl=ru) .  
Отображается предупреждение: _знайте свой адрес электронной почты._

`"identity.email"`

Предоставляет доступ к адресу электронной почты пользователя через API [`chrome.identity`](https://developer.chrome.com/docs/extensions/reference/api/identity?hl=ru) .  
Отображается предупреждение: _знайте свой адрес электронной почты._

`"idle"`

Предоставляет доступ к API [`chrome.idle`](https://developer.chrome.com/docs/extensions/reference/api/idle?hl=ru) .

`"loginState"`

Предоставляет доступ к API [`chrome.loginState`](https://developer.chrome.com/docs/extensions/reference/api/loginState?hl=ru) .

`"management"`

Предоставляет доступ к API [`chrome.management`](https://developer.chrome.com/docs/extensions/reference/api/management?hl=ru) .  
Отображается предупреждение: _Управляйте своими приложениями, расширениями и темами._

`"nativeMessaging"`

Предоставляет доступ к [собственному API обмена сообщениями](https://developer.chrome.com/docs/extensions/develop/concepts/native-messaging?hl=ru) .  
Отображается предупреждение: _Общайтесь с совместимыми собственными приложениями._

`"notifications"`

Предоставляет доступ к API [`chrome.notifications`](https://developer.chrome.com/docs/extensions/reference/api/notifications?hl=ru) .  
Отображается предупреждение: _отображение уведомлений._

`"offscreen"`

Предоставляет доступ к API [`chrome.offscreen`](https://developer.chrome.com/docs/extensions/reference/api/offscreen?hl=ru) .

`"pageCapture"`

Предоставляет доступ к API [`chrome.pageCapture`](https://developer.chrome.com/docs/extensions/reference/api/pageCapture?hl=ru) .  
Отображается предупреждение: _прочтите и измените все свои данные на всех веб-сайтах._

`"platformKeys"`

Предоставляет доступ к API [`chrome.platformKeys`](https://developer.chrome.com/docs/extensions/reference/api/platformKeys?hl=ru) .

`"power"`

Предоставляет доступ к API [`chrome.power`](https://developer.chrome.com/docs/extensions/reference/api/power?hl=ru) .

`"printerProvider"`

Предоставляет доступ к API [`chrome.printerProvider`](https://developer.chrome.com/docs/extensions/reference/api/printerProvider?hl=ru) .

`"printing"`

Предоставляет доступ к API [`chrome.printing`](https://developer.chrome.com/docs/extensions/reference/api/printing?hl=ru) .

`"printingMetrics"`

Предоставляет доступ к API [`chrome.printingMetrics`](https://developer.chrome.com/docs/extensions/reference/api/printingMetrics?hl=ru) .

`"privacy"`

Предоставляет доступ к API [`chrome.privacy`](https://developer.chrome.com/docs/extensions/reference/api/privacy?hl=ru) .  
Отображается предупреждение: _измените настройки конфиденциальности._

`"processes"`

Предоставляет доступ к API [`chrome.processes`](https://developer.chrome.com/?hl=ru) .

`"proxy"`

Предоставляет доступ к API [`chrome.proxy`](https://developer.chrome.com/docs/extensions/reference/api/proxy?hl=ru) .  
Отображается предупреждение: _прочтите и измените все свои данные на всех веб-сайтах._

`"readingList"`

Предоставляет доступ к API [`chrome.readingList`](https://developer.chrome.com/docs/extensions/reference/api/readingList?hl=ru) .  
Отображается предупреждение: _Прочтите и измените записи в списке чтения._

`"runtime"`

Предоставляет доступ к [`runtime.connectNative()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#method-connectNative) и [`runtime.sendNativeMessage()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#method-sendNativeMessage) . Для всех других функций пространства имен среды `runtime` разрешение не требуется.

`"scripting"`

Предоставляет доступ к API [`chrome.scripting`](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru) .

`"search"`

Предоставляет доступ к API [`chrome.search`](https://developer.chrome.com/docs/extensions/reference/api/search?hl=ru) .

`"sessions"`

Предоставляет доступ к API [`chrome.sessions`](https://developer.chrome.com/docs/extensions/reference/api/sessions?hl=ru) .  
Отображаются предупреждения:  

-   При использовании с разрешением `"history"` : _чтение и изменение истории просмотров на всех устройствах, на которых вы вошли в систему._
-   При использовании с разрешением `"tabs"` : _прочитайте историю просмотров на всех устройствах, на которых выполнен вход._

`"sidePanel"`

Предоставляет доступ к API [`chrome.sidePanel`](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru) .

`"storage"`

Предоставляет доступ к API [`chrome.storage`](https://developer.chrome.com/docs/extensions/reference/api/storage?hl=ru) .

`"system.cpu"`

Предоставляет доступ к API [`chrome.system.cpu`](https://developer.chrome.com/docs/extensions/reference/api/system/cpu?hl=ru) .

`"system.display"`

Предоставляет доступ к API [`chrome.system.display`](https://developer.chrome.com/docs/extensions/reference/api/system/display?hl=ru) .

`"system.memory"`

Предоставляет доступ к API [`chrome.system.memory`](https://developer.chrome.com/docs/extensions/reference/api/system/memory?hl=ru) .

`"system.storage"`

Предоставляет доступ к API [`chrome.system.storage`](https://developer.chrome.com/docs/extensions/reference/api/system/storage?hl=ru) .  
Отображается предупреждение: _Определите и извлеките устройства хранения данных._

`"tabCapture"`

Предоставляет доступ к API [`chrome.tabCapture`](https://developer.chrome.com/docs/extensions/reference/api/tabCapture?hl=ru) .  
Отображается предупреждение: _прочтите и измените все свои данные на всех веб-сайтах._

`"tabGroups"`

Предоставляет доступ к API [`chrome.tabGroups`](https://developer.chrome.com/docs/extensions/reference/api/tabGroups?hl=ru) .  
Отображается предупреждение: _просмотр групп вкладок и управление ими._

`"tabs"`

Предоставляет доступ к привилегированным полям объектов Tab, используемых несколькими API, включая [`chrome.tabs`](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=ru) и [`chrome.windows`](https://developer.chrome.com/docs/extensions/reference/api/windows?hl=ru) . Обычно вам не нужно объявлять это разрешение для использования этих API.  
Отображается предупреждение: _прочтите историю просмотров._

`"topSites"`

Предоставляет доступ к API [`chrome.topSites`](https://developer.chrome.com/docs/extensions/reference/api/topSites?hl=ru) .  
Отображается предупреждение: _прочтите список наиболее часто посещаемых вами веб-сайтов._

`"tts"`

Предоставляет доступ к API [`chrome.tts`](https://developer.chrome.com/docs/extensions/reference/api/tts?hl=ru) .

`"ttsEngine"`

Предоставляет доступ к API [`chrome.ttsEngine`](https://developer.chrome.com/docs/extensions/reference/api/ttsEngine?hl=ru) .  
Отображается предупреждение: _прочитайте весь текст, произнесенный с использованием синтезированной речи._

`"unlimitedStorage"`

Предоставляет неограниченную квоту для [`chrome.storage.local`](https://developer.chrome.com/docs/extensions/reference/api/storage?hl=ru#property-local) , [`IndexedDB`](https://developer.mozilla.org/docs/Web/API/IndexedDB_API) , [`Cache Storage`](https://developer.mozilla.org/docs/Web/API/Cache) и [`Origin Private File System`](https://web.dev/origin-private-file-system/?hl=ru) . Дополнительную информацию см. в разделе [Хранение и файлы cookie](https://developer.chrome.com/docs/extensions/develop/concepts/storage-and-cookies?hl=ru) .

`"vpnProvider"`

Предоставляет доступ к API [`chrome.vpnProvider`](https://developer.chrome.com/docs/extensions/reference/api/vpnProvider?hl=ru) .

`"wallpaper"`

Предоставляет доступ к API [`chrome.wallpaper`](https://developer.chrome.com/docs/extensions/reference/api/wallpaper?hl=ru) .

`"webAuthenticationProxy"`

Предоставляет доступ к API [`chrome.webAuthenticationProxy`](https://developer.chrome.com/docs/extensions/reference/api/webAuthenticationProxy?hl=ru) .  
Отображается предупреждение: _прочтите и измените все свои данные на всех веб-сайтах._

`"webNavigation"`

Предоставляет доступ к API [`chrome.webNavigation`](https://developer.chrome.com/docs/extensions/reference/api/webNavigation?hl=ru) .  
Отображается предупреждение: _прочтите историю просмотров._

`"webRequest"`

Предоставляет доступ к API [`chrome.webRequest`](https://developer.chrome.com/docs/extensions/reference/api/webRequest?hl=ru) .

`"webRequestBlocking"`

Позволяет использовать API [`chrome.webRequest`](https://developer.chrome.com/docs/extensions/reference/api/webRequest?hl=ru#permissions) для блокировки.

Если не указано иное, контент на этой странице предоставляется по [лицензии Creative Commons "С указанием авторства 4.0"](https://creativecommons.org/licenses/by/4.0/), а примеры кода – по [лицензии Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0). Подробнее об этом написано в [правилах сайта](https://developers.google.com/site-policies?hl=ru). Java – это зарегистрированный товарный знак корпорации Oracle и ее аффилированных лиц.

Последнее обновление: 2024-02-06 UTC.
