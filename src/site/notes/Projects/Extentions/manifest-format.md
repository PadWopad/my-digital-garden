---
{"dg-publish":true,"permalink":"/projects/extentions/manifest-format/"}
---


# Формат файла манифеста  |  Manifest  |  Chrome for Developers

> ## Excerpt
> Обзор свойств файла манифеста.json расширения Chrome.

---
[Skip to main content](https://developer.chrome.com/docs/extensions/reference/manifest?hl=ru#main-content)

 [![Chrome for Developers](https://www.gstatic.com/devrel-devsite/prod/v0f39da1ecc369fa6a1c816bfa5d8f549228499e733c9bd8becc473543aa6caa2/chrome/images/lockup.svg)](https://developer.chrome.com/)

-   [Формат файла манифеста](https://developer.chrome.com/docs/extensions/reference/manifest)
-   [Общие модули](https://developer.chrome.com/docs/extensions/reference/manifest/shared-modules)
-   [Переопределение настроек Chrome](https://developer.chrome.com/docs/extensions/reference/manifest/chrome-settings-override)

-   [author](https://developer.chrome.com/docs/extensions/reference/manifest/author)
-   [задний план](https://developer.chrome.com/docs/extensions/reference/manifest/background)
-   [контент\_скрипты](https://developer.chrome.com/docs/extensions/reference/manifest/content-scripts)
-   [cross\_origin\_embedder\_policy](https://developer.chrome.com/docs/extensions/reference/manifest/cross-origin-embedder-policy)
-   [content\_security\_policy](https://developer.chrome.com/docs/extensions/reference/manifest/content-security-policy)
-   [cross\_origin\_opener\_policy](https://developer.chrome.com/docs/extensions/reference/manifest/cross-origin-opener-policy)
-   [Описание](https://developer.chrome.com/docs/extensions/reference/manifest/description)
-   [default\_locale](https://developer.chrome.com/docs/extensions/reference/manifest/default-locale)
-   [event\_rules](https://developer.chrome.com/docs/extensions/reference/manifest/event-rules)
-   [внешне\_подключаемый](https://developer.chrome.com/docs/extensions/reference/manifest/externally-connectable)
-   [file\_handlers](https://developer.chrome.com/docs/extensions/reference/manifest/file-handlers)
-   [URL-адрес домашней страницы](https://developer.chrome.com/docs/extensions/reference/manifest/homepage-url)
-   [инкогнито](https://developer.chrome.com/docs/extensions/reference/manifest/incognito)
-   [значки](https://developer.chrome.com/docs/extensions/reference/manifest/icons)
-   [входные\_компоненты](https://developer.chrome.com/docs/extensions/reference/manifest/input-components)
-   [ключ](https://developer.chrome.com/docs/extensions/reference/manifest/key)
-   [манифест\_версия](https://developer.chrome.com/docs/extensions/reference/manifest/manifest-version)
-   [минимальная\_хром\_версия](https://developer.chrome.com/docs/extensions/reference/manifest/minimum-chrome-version)
-   [Название](https://developer.chrome.com/docs/extensions/reference/manifest/name)
-   [oauth2](https://developer.chrome.com/docs/extensions/reference/manifest/oauth2)
-   [требования](https://developer.chrome.com/docs/extensions/reference/manifest/requirements)
-   [песочница](https://developer.chrome.com/docs/extensions/reference/manifest/sandbox)
-   [короткое имя](https://developer.chrome.com/docs/extensions/reference/manifest/short-name)
-   [хранилище](https://developer.chrome.com/docs/extensions/reference/manifest/storage)
-   [пробные\_токены,пробные\_токены](https://developer.chrome.com/docs/extensions/reference/manifest/trial_tokens)
-   [версия](https://developer.chrome.com/docs/extensions/reference/manifest/version)
-   [web\_accessible\_resources](https://developer.chrome.com/docs/extensions/reference/manifest/web-accessible-resources)

## Формат файла манифеста

bookmark\_border Оптимизируйте свои подборки Сохраняйте и классифицируйте контент в соответствии со своими настройками.

Каждое расширение должно иметь файл `manifest.json` в корневом каталоге, в котором перечислена важная информация о структуре и поведении этого расширения. На этой странице объясняется структура манифестов расширений и функции, которые они могут включать.

## Примеры

В следующих примерах манифестов показана базовая структура манифеста и некоторые часто используемые функции в качестве отправной точки для создания собственного манифеста:

## Ключи манифеста

Ниже приведен список всех поддерживаемых ключей манифеста.

### Ключи, необходимые для платформы расширений

`"manifest_version"`

Целое число, указывающее версию формата файла манифеста, используемого вашим расширением. Единственное поддерживаемое значение — `3` .

`"name"`

Строка, идентифицирующая расширение в [Интернет-магазине Chrome](https://chrome.google.com/webstore?hl=ru) , диалоговом окне установки и на странице расширений Chrome пользователя ( `chrome://extensions` ). Максимальная длина — 75 символов. Информацию об использовании имен, зависящих от локали, см. в разделе [Интернационализация](https://developer.chrome.com/docs/extensions/reference/api/i18n?hl=ru) .

`"version"`

Строка, идентифицирующая номер версии расширения. Информацию о форматировании номера версии см. в [разделе Версия](https://developer.chrome.com/docs/extensions/reference/manifest/version?hl=ru) .

### Ключи, необходимые для Интернет-магазина Chrome

`"description"`

Строка, описывающая расширение как в Интернет-магазине Chrome, так и на странице управления расширениями пользователя. Максимальная длина — 132 символа. Информацию о локализации описаний см. в разделе [Интернационализация](https://developer.chrome.com/docs/extensions/reference/api/i18n?hl=ru) .

`"icons"`

Один или несколько значков, обозначающих ваше расширение. Информацию о передовом опыте см. в [разделе Значки](https://developer.chrome.com/docs/extensions/reference/manifest/icons?hl=ru) .

### Дополнительные ключи

`"action"`

Определяет внешний вид и поведение значка расширения на панели инструментов Google. Дополнительную информацию см. в [`chrome.action`](https://developer.chrome.com/docs/extensions/reference/api/action?hl=ru) .

`"author"`

Указывает адрес электронной почты учетной записи, которая использовалась для создания расширения.

`"background"`

Указывает файл JavaScript, содержащий сервис-воркер расширения, который действует как обработчик событий. Дополнительные сведения см. [в разделе О работниках службы расширения](https://developer.chrome.com/docs/extensions/develop/concepts/service-workers?hl=ru) .

`"chrome_settings_overrides"`

Определяет переопределения для выбранных настроек Chrome. Дополнительную информацию см. в [разделе «Переопределение настроек Chrome»](https://developer.chrome.com/docs/extensions/reference/manifest/chrome-settings-override?hl=ru) .

`"chrome_url_overrides"`

Определяет переопределения для страниц Chrome по умолчанию. Дополнительную информацию см. [в разделе Переопределение страниц Chrome](https://developer.chrome.com/docs/extensions/develop/ui/override-chrome-pages?hl=ru) .

`"commands"`

Определяет сочетания клавиш внутри расширения. Дополнительную информацию см. в [разделе chrome.commands](https://developer.chrome.com/docs/extensions/reference/api/commands?hl=ru) .

`"content_scripts"`

Указывает файлы JavaScript или CSS, которые будут использоваться, когда пользователь открывает определенные веб-страницы. Дополнительные сведения см. в [разделе Сценарии содержимого](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru) .

`"content_security_policy"`

Определяет ограничения на сценарии, стили и другие ресурсы, которые может использовать расширение. Дополнительную информацию см. в [разделе Политика безопасности контента](https://developer.chrome.com/docs/extensions/reference/manifest/content-security-policy?hl=ru) .

`"cross_origin_embedder_policy"`

Указывает значение HTTP-заголовка Cross-Origin-Embedder-Policy, который настраивает внедрение ресурсов из разных источников на страницу расширения.

`"cross_origin_opener_policy"`

Указывает значение для HTTP-заголовка Cross-Origin-Opener-Policy, которое позволяет гарантировать, что страница расширения верхнего уровня не использует общую группу контекста просмотра с документами из разных источников.

`"declarative_net_request"`

Определяет статические правила для API [declarativeNetRequest](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest?hl=ru) , которые позволяют блокировать и изменять сетевые запросы.

`"default_locale"`

Строка, определяющая язык по умолчанию для расширения, поддерживающего несколько локалей. Примеры включают «en» и «pt\_BR». Этот ключ необходим в локализованных расширениях и не должен использоваться в нелокализованных расширениях. Для получения дополнительной информации см. [Интернационализация](https://developer.chrome.com/docs/extensions/reference/api/i18n?hl=ru) .

`"devtools_page"`

Определяет страницы, использующие API [DevTools](https://developer.chrome.com/docs/extensions/how-to/devtools/extend-devtools?hl=ru) .

`"export"`

Позволяет экспортировать ресурсы из расширения. Для получения дополнительной информации см. [Экспорт](https://developer.chrome.com/docs/extensions/reference/manifest/shared-modules?hl=ru#export) .

`"externally_connectable"`

Указывает, какие другие страницы и расширения могут подключаться к вашим расширениям. Для получения дополнительной информации см. [`"externally_connectable"`](https://developer.chrome.com/docs/extensions/reference/manifest/externally-connectable?hl=ru) .

`"homepage_url"`

Строка, определяющая URL-адрес домашней страницы расширения. Если это значение не определено, домашней страницей по умолчанию будет страница Интернет-магазина Chrome расширения. Это поле особенно полезно, если вы [размещаете расширение](https://developer.chrome.com/docs/extensions/how-to/distribute/host-extensions?hl=ru) на своем сайте.

`"host_permissions"`

Перечисляет веб-страницы, с которыми вашему расширению разрешено взаимодействовать, определяемые с использованием шаблонов соответствия URL-адресов. Разрешение пользователя для этих сайтов запрашивается во время установки. Дополнительную информацию см. в [разделе Разрешения хоста](https://developer.chrome.com/docs/extensions/develop/concepts/declare-permissions?hl=ru) .

`"import"`

Позволяет импортировать ресурсы в расширение. Дополнительную информацию см. в [разделе Импорт](https://developer.chrome.com/docs/extensions/reference/manifest/shared-modules?hl=ru#import) .

`"incognito"`

Определяет, как расширение ведет себя в режиме инкогнито. Поддерживаемые значения: `"spanning"` , `"split"` и `"not_allowed"` . Дополнительную информацию см. в [разделе Инкогнито](https://developer.chrome.com/docs/extensions/reference/manifest/incognito?hl=ru) .

`"key"`

Указывает идентификатор вашего расширения для различных вариантов использования при разработке. Для получения дополнительной информации см. [Ключ](https://developer.chrome.com/docs/extensions/reference/manifest/key?hl=ru) .

`"minimum_chrome_version"`

Определяет самую старую версию Chrome, в которой можно установить ваше расширение. Значение должно быть подстрокой существующей строки версии браузера Chrome, например `"107"` или `"107.0.5304.87"` . Пользователи версий Chrome старше минимальной версии видят предупреждение «Несовместимо» в Интернет-магазине Chrome и не могут установить ваше расширение. Если вы добавите это к существующему расширению, пользователи Chrome с более старой версией не будут получать автоматические обновления вашего расширения. Сюда входят бизнес-пользователи в [эфемерном](https://support.google.com/chrome/a/answer/3538894?hl=ru) режиме.

`"oauth2"`

Позволяет использовать идентификатор безопасности OAuth 2.0. Значением этого ключа должен быть объект со свойствами `"client_id"` и `"scopes"` . Подробности см. [в руководстве по OAuth 2.0](https://developer.chrome.com/docs/extensions/how-to/integrate/oauth?hl=ru) .

`"omnibox"`

Позволяет расширению регистрировать ключевое слово в адресной строке Chrome. Для получения дополнительной информации см. [Омнибокс](https://developer.chrome.com/docs/extensions/reference/api/omnibox?hl=ru) .

`"optional_host_permissions"`

Объявляет дополнительные [разрешения хоста](https://developer.chrome.com/docs/extensions/develop/concepts/declare-permissions?hl=ru) для вашего расширения.

`"optional_permissions"`

Объявляет [дополнительные разрешения](https://developer.chrome.com/docs/extensions/reference/api/permissions?hl=ru#step-2-declare-optional-permissions-in-the-manifest) для вашего расширения.

`"options_page"`

Указывает путь к файлу options.html, который расширение будет использовать в качестве страницы параметров. Дополнительные сведения см. в [разделе Предоставление пользователям возможностей](https://developer.chrome.com/docs/extensions/develop/ui/options-page?hl=ru) .

`"options_ui"`

Указывает путь к HTML-файлу, который позволяет пользователю изменять параметры расширения на странице расширений Chrome. Дополнительную информацию см. в [разделе Встроенные параметры](https://developer.chrome.com/docs/extensions/develop/ui/options-page?hl=ru#embedded_options) .

`"permissions"`

Позволяет использовать определенные API расширений. См. [«Разрешения»](https://developer.chrome.com/docs/extensions/reference/permissions?hl=ru) для общего объяснения. На справочных страницах отдельных API перечислены необходимые им разрешения.

`"requirements"`

Перечисляет технологии, необходимые для использования расширения. Список поддерживаемых требований см. в разделе [Требования](https://developer.chrome.com/docs/extensions/reference/manifest/requirements?hl=ru) .

`"sandbox"`

Определяет набор страниц расширений, у которых нет доступа к API расширений или прямого доступа к страницам, не изолированным в изолированной программной среде. Дополнительные сведения см. в [разделе Песочница](https://developer.chrome.com/docs/extensions/reference/manifest/sandbox?hl=ru) .

`"short_name"`

Строка, содержащая сокращенную версию имени расширения, которая будет использоваться, когда пространство символов ограничено. Максимальная длина — 12 символов. Если это значение не определено, вместо этого отображается усеченная версия ключа «имя».

`"side_panel"`

Идентифицирует HTML-файл для отображения в [боковой панели](https://developer.chrome.com/docs/extensions/reference/api/sidePanel?hl=ru) .

`"storage"`

Объявляет схему JSON для [управляемой области хранения](https://developer.chrome.com/docs/extensions/reference/storage?hl=ru#property-managed) . Дополнительную информацию см. в [разделе Манифест областей хранения](https://developer.chrome.com/docs/extensions/reference/manifest/storage?hl=ru) .

`"tts_engine"`

Регистрирует расширение как механизм преобразования текста в речь. Для получения дополнительной информации см. API [ttsEngine](https://developer.chrome.com/docs/extensions/reference/api/ttsEngine?hl=ru) .

`"update_url"`

Строка, содержащая URL-адрес страницы обновлений расширения. Используйте этот ключ, если вы [размещаете свое расширение](https://developer.chrome.com/docs/extensions/how-to/distribute/host-extensions?hl=ru) за пределами Интернет-магазина Chrome.

`"version_name"`

Строка, описывающая версию расширения. Примеры включают `"1.0 beta"` и `"build rc2"` . Если это значение не указано, вместо этого на странице управления расширением отображается значение «версия».

`"web_accessible_resources"`

Определяет файлы внутри расширения, к которым могут получить доступ веб-страницы или другие расширения. Для получения дополнительной информации см. [Доступные веб-ресурсы](https://developer.chrome.com/docs/extensions/reference/manifest/web-accessible-resources?hl=ru) .

### Дополнительные ключи ChromeOS

`"file_browser_handlers"`

Предоставляет доступ к API [`fileBrowserHandler`](https://developer.chrome.com/docs/extensions/reference/api/fileBrowserHandler?hl=ru) , который позволяет расширениям получать доступ к файловому браузеру ChromeOS.

`"file_handlers"`

Указывает типы файлов, которые будут обрабатываться расширениями ChromeOS. Для получения дополнительной информации см. [`file_handlers`](https://developer.chrome.com/docs/extensions/reference/manifest/file-handlers?hl=ru) .

`"file_system_provider_capabilities"`

Предоставляет доступ к API [`fileSystemProvider`](https://developer.chrome.com/docs/extensions/reference/api/fileSystemProvider?hl=ru) , который позволяет расширениям создавать файловые системы, которые может использовать ChromeOS.

`"input_components"`

Позволяет использовать API редактора метода ввода. Для получения дополнительной информации см. [`input_components`](https://developer.chrome.com/docs/extensions/reference/manifest/input-components?hl=ru) .

Если не указано иное, контент на этой странице предоставляется по [лицензии Creative Commons "С указанием авторства 4.0"](https://creativecommons.org/licenses/by/4.0/), а примеры кода – по [лицензии Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0). Подробнее об этом написано в [правилах сайта](https://developers.google.com/site-policies?hl=ru). Java – это зарегистрированный товарный знак корпорации Oracle и ее аффилированных лиц.

Последнее обновление: 2012-09-18 UTC.
