---
{"dg-publish":true,"created":"2025-01-31T16:46:35 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-activetab?hl=ru","author":null,"permalink":"/projects/extentions/vnedrit-skripty-v-aktivnuyu-vkladku-chrome-extensions-chrome-for-developers/","dgPassFrontmatter":true}
---


# Внедрить скрипты в активную вкладку  |  Chrome Extensions  |  Chrome for Developers

> ## Excerpt
> Узнайте, как упростить стиль текущей страницы.

---
Упростите стиль текущей страницы, щелкнув значок расширения на панели инструментов.

## Обзор

В этом руководстве создается расширение, которое упрощает оформление страниц документации расширения Chrome и Интернет-магазина Chrome, чтобы их было легче читать.

В этом руководстве мы объясним, как сделать следующее:

-   Используйте работника службы расширения в качестве координатора событий.
-   Сохраняйте конфиденциальность пользователя с помощью разрешения `"activeTab"` .
-   Запускайте код, когда пользователь щелкает значок расширения на панели инструментов.
-   Вставляйте и удаляйте таблицу стилей с помощью API [сценариев](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru) .
-   Используйте сочетание клавиш для выполнения кода.

## Прежде чем начать

В этом руководстве предполагается, что у вас есть базовый опыт веб-разработки. Мы рекомендуем ознакомиться [с Hello World](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru) , чтобы познакомиться с рабочим процессом разработки расширений.

## Создайте расширение

Для начала создайте новый каталог с именем `focus-mode` , в котором будут храниться файлы расширения. При желании вы можете скачать полный исходный код с [GitHub](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.focus-mode) .

### Шаг 1. Добавьте данные и значки расширения.

Создайте файл с именем `manifest.json` и включите следующий код.

```
<span>{</span>
<span>  </span>"<span>ma</span><span>n</span><span>i</span><span>fest</span><span>_versio</span><span>n</span>"<span>:</span><span> </span><span>3</span><span>,</span>
<span>  </span>"<span>na</span><span>me</span>"<span>:</span><span> </span>"<span>Focus</span><span> </span><span>Mode</span>"<span>,</span>
<span>  </span>"<span>descrip</span><span>t</span><span>io</span><span>n</span>"<span>:</span><span> </span>"<span>E</span><span>na</span><span>ble</span><span> </span><span>f</span><span>ocus</span><span> </span><span>mode</span><span> </span><span>o</span><span>n</span><span> </span><span>Chrome's</span><span> </span><span>o</span><span>ff</span><span>icial</span><span> </span><span>Ex</span><span>tens</span><span>io</span><span>ns</span><span> </span><span>a</span><span>n</span><span>d</span><span> </span><span>Chrome</span><span> </span><span>Web</span><span> </span><span>S</span><span>t</span><span>ore</span><span> </span><span>docume</span><span>ntat</span><span>io</span><span>n</span><span>.</span>"<span>,</span>
<span>  </span>"<span>versio</span><span>n</span>"<span>:</span><span> </span>"<span>1.0</span>"<span>,</span>
<span>  </span>"<span>ico</span><span>ns</span>"<span>:</span><span> </span><span>{</span>
<span>    </span>"<span>16</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-16.</span><span>p</span><span>n</span><span>g</span>"<span>,</span>
<span>    </span>"<span>32</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-32.</span><span>p</span><span>n</span><span>g</span>"<span>,</span>
<span>    </span>"<span>48</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-48.</span><span>p</span><span>n</span><span>g</span>"<span>,</span>
<span>    </span>"<span>128</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-128.</span><span>p</span><span>n</span><span>g</span>"
<span>  </span><span>}</span>
<span>}</span>
```

Чтобы узнать больше об этих ключах манифеста, ознакомьтесь с руководством «Запуск сценариев на каждой вкладке», в котором более подробно объясняются [метаданные](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru#step-1) и [значки](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru#step-2) расширения.

Создайте папку `images` и [загрузите в нее значки](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.focus-mode/images) .

### Шаг 2. Инициализируйте расширение.

Расширения могут отслеживать события браузера в фоновом режиме с помощью [сервис-воркера расширения](https://developer.chrome.com/docs/extensions/develop/concepts/service-workers?hl=ru) . Сервис-воркеры — это специальные среды JavaScript, которые обрабатывают события и завершают работу, когда они не нужны.

Начните с регистрации сервис-воркера в файле `manifest.json` :

```
<span>{</span>
<span>  </span><span>...</span>
<span>  </span>"<span>backgrou</span><span>n</span><span>d</span>"<span>:</span><span> </span><span>{</span>
<span>    </span>"<span>service_worker</span>"<span>:</span><span> </span>"<span>backgrou</span><span>n</span><span>d.js</span>"
<span>  </span><span>},</span>
<span>  </span><span>...</span>
<span>}</span>
```

Создайте файл с именем `background.js` и добавьте следующий код:

```
<span>chrome</span><span>.</span><span>runtime</span><span>.</span><span>onInstalled</span><span>.</span><span>addListener</span><span>(()</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>chrome</span><span>.</span><span>action</span><span>.</span><span>setBadgeText</span><span>({</span>
<span>    </span><span>text</span><span>:</span><span> </span>"<span>OFF</span>"<span>,</span>
<span>  </span><span>});</span>
<span>});</span>
```

Первое событие, которое будет прослушивать наш сервис-воркер, — это [`runtime.onInstalled()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=ru#event-onInstalled) . Этот метод позволяет расширению установить начальное состояние или выполнить некоторые задачи при установке. Расширения могут использовать [Storage API](https://developer.chrome.com/docs/extensions/reference/api/storage?hl=ru) и [IndexedDB](https://developer.mozilla.org/docs/Web/API/IndexedDB_API) для хранения состояния приложения. Однако в этом случае, поскольку мы обрабатываем только два состояния, мы будем использовать сам текст _значка действия_ , чтобы отслеживать, включено ли расширение или выключено.

### Шаг 3. Включите действие расширения.

_Действие расширения_ управляет значком расширения на панели инструментов. Поэтому всякий раз, когда пользователь щелкает значок расширения, он либо запускает некоторый код (как в этом примере), либо отображает всплывающее окно. Добавьте следующий код, чтобы объявить действие расширения в файле `manifest.json` :

```
<span>{</span>
<span>  </span><span>...</span>
<span>  </span>"<span>ac</span><span>t</span><span>io</span><span>n</span>"<span>:</span><span> </span><span>{</span>
<span>    </span>"<span>de</span><span>fault</span><span>_ico</span><span>n</span>"<span>:</span><span> </span><span>{</span>
<span>      </span>"<span>16</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-16.</span><span>p</span><span>n</span><span>g</span>"<span>,</span>
<span>      </span>"<span>32</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-32.</span><span>p</span><span>n</span><span>g</span>"<span>,</span>
<span>      </span>"<span>48</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-48.</span><span>p</span><span>n</span><span>g</span>"<span>,</span>
<span>      </span>"<span>128</span>"<span>:</span><span> </span>"<span>images/ico</span><span>n</span><span>-128.</span><span>p</span><span>n</span><span>g</span>"
<span>    </span><span>}</span>
<span>  </span><span>},</span>
<span>  </span><span>...</span>
<span>}</span>
```

#### Используйте разрешение activeTab для защиты конфиденциальности пользователя.

Разрешение [`activeTab`](https://developer.chrome.com/docs/extensions/develop/concepts/activeTab?hl=ru) предоставляет расширению _временную_ возможность выполнять код на активной вкладке. Это также обеспечивает доступ к [конфиденциальным свойствам](https://developer.chrome.com/docs/extensions/develop/concepts/activeTab?hl=ru#what-activeTab-allows) текущей вкладки.

Это разрешение включается, когда пользователь **_вызывает_** расширение. В этом случае пользователь вызывает расширение, щелкнув действие расширения.

💡 **Какие еще действия пользователя активируют разрешение activeTab в моем собственном расширении?**

-   Нажатие комбинации клавиш.
-   Выбор пункта контекстного меню.
-   Принятие предложения от омнибокса.
-   Открытие всплывающего окна расширения.

Разрешение `"activeTab"` позволяет пользователям _целенаправленно_ выбирать запуск расширения на соответствующей вкладке; таким образом, он защищает конфиденциальность пользователя. Еще одним преимуществом является то, что это не вызывает [предупреждения о разрешении](https://developer.chrome.com/docs/extensions/develop/concepts/permission-warnings?hl=ru#permissions_with_warnings) .

Чтобы использовать разрешение `"activeTab"` , добавьте его в массив разрешений манифеста:

```
<span>{</span>
<span>  </span><span>...</span>
<span>  </span>"<span>permissio</span><span>ns</span>"<span>:</span><span> </span><span>[</span>"<span>ac</span><span>t</span><span>iveTab</span>"<span>],</span>
<span>  </span><span>...</span>
<span>}</span>
```

### Шаг 4. Отслеживайте состояние текущей вкладки

После того, как пользователь нажмет действие расширения, расширение проверит, соответствует ли URL-адрес странице документации. Затем он проверит состояние текущей вкладки и установит следующее состояние. Добавьте следующий код в `background.js` :

```
<span>const</span><span> </span><span>extensions</span><span> </span><span>=</span><span> </span>'<span>https</span><span>:</span><span>//developer.chrome.com/docs/extensions';</span>
<span>const</span><span> </span><span>webstore</span><span> </span><span>=</span><span> </span>'<span>https</span><span>:</span><span>//developer.chrome.com/docs/webstore';</span>

<span>chrome</span><span>.</span><span>action</span><span>.</span><span>onClicked</span><span>.</span><span>addListener</span><span>(</span><span>async</span><span> </span><span>(</span><span>tab</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>if</span><span> </span><span>(</span><span>tab</span><span>.</span><span>url</span><span>.</span><span>startsWith</span><span>(</span><span>extensions</span><span>)</span><span> </span><span>||</span><span> </span><span>tab</span><span>.</span><span>url</span><span>.</span><span>startsWith</span><span>(</span><span>webstore</span><span>))</span><span> </span><span>{</span>
<span>    </span><span>// Retrieve the action badge to check if the extension is 'ON' or 'OFF</span>'
<span>    </span><span>const</span><span> </span><span>prevState</span><span> </span><span>=</span><span> </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>action</span><span>.</span><span>getBadgeText</span><span>({</span><span> </span><span>tabId</span><span>:</span><span> </span><span>tab</span><span>.</span><span>id</span><span> </span><span>});</span>
<span>    </span><span>// Next state will always be the opposite</span>
<span>    </span><span>const</span><span> </span><span>nextState</span><span> </span><span>=</span><span> </span><span>prevState</span><span> </span><span>===</span><span> </span>'<span>ON</span>'<span> </span><span>?</span><span> </span>'<span>OFF</span>'<span> </span><span>:</span><span> </span>'<span>ON</span>'<span>;</span>

<span>    </span><span>// Set the action badge to the next state</span>
<span>    </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>action</span><span>.</span><span>setBadgeText</span><span>({</span>
<span>      </span><span>tabId</span><span>:</span><span> </span><span>tab</span><span>.</span><span>id</span><span>,</span>
<span>      </span><span>text</span><span>:</span><span> </span><span>nextState</span><span>,</span>
<span>    </span><span>});</span>
<span>  </span><span>}</span>
<span>});</span>
```

### Шаг 5. Добавьте или удалите таблицу стилей.

Теперь пришло время изменить макет страницы. Создайте файл с именем `focus-mode.css` и включите следующий код:

```
<span>*</span><span> </span><span>{</span>
<span>  </span><span>display</span><span>:</span><span> </span><span>none</span><span> </span><span>!</span><span>important</span><span>;</span>
<span>}</span>

<span>html</span><span>,</span>
<span>body</span><span>,</span>
<span>*:</span><span>has</span><span>(</span><span>article</span><span>),</span>
<span>article</span><span>,</span>
<span>article</span><span> </span><span>*</span><span> </span><span>{</span>
<span>  </span><span>display</span><span>:</span><span> </span><span>revert</span><span> </span><span>!</span><span>important</span><span>;</span>
<span>}</span>

<span>[</span><span>role</span><span>=</span>'<span>navigation</span>'<span>]</span><span> </span><span>{</span>
<span>  </span><span>display</span><span>:</span><span> </span><span>none</span><span> </span><span>!</span><span>important</span><span>;</span>
<span>}</span>

<span>article</span><span> </span><span>{</span>
<span>  </span><span>margin</span><span>:</span><span> </span><span>auto</span><span>;</span>
<span>  </span><span>max</span><span>-</span><span>width</span><span>:</span><span> </span><span>700</span><span>px</span><span>;</span>
<span>}</span>
```

Вставьте или удалите таблицу стилей с помощью API [сценариев](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru) . Начните с объявления разрешения `"scripting"` в манифесте:

```
<span>{</span>
<span>  </span><span>...</span>
<span>  </span>"<span>permissio</span><span>ns</span>"<span>:</span><span> </span><span>[</span>"<span>ac</span><span>t</span><span>iveTab</span>"<span>,</span><span> </span>"<span>scrip</span><span>t</span><span>i</span><span>n</span><span>g</span>"<span>],</span>
<span>  </span><span>...</span>
<span>}</span>
```

Наконец, в `background.js` добавьте следующий код, чтобы изменить макет страницы:

  ```
<span>  </span><span>...</span>
<span>    </span><span>if</span><span> </span><span>(</span><span>nextState</span><span> </span><span>===</span><span> </span>"<span>ON</span>"<span>)</span><span> </span><span>{</span>
<span>      </span><span>// Insert the CSS file when the user turns the extension on</span>
<span>      </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>scripting</span><span>.</span><span>insertCSS</span><span>({</span>
<span>        </span><span>files</span><span>:</span><span> </span><span>[</span>"<span>focus</span><span>-</span><span>mode</span><span>.</span><span>css</span>"<span>],</span>
<span>        </span><span>target</span><span>:</span><span> </span><span>{</span><span> </span><span>tabId</span><span>:</span><span> </span><span>tab</span><span>.</span><span>id</span><span> </span><span>},</span>
<span>      </span><span>});</span>
<span>    </span><span>}</span><span> </span><span>else</span><span> </span><span>if</span><span> </span><span>(</span><span>nextState</span><span> </span><span>===</span><span> </span>"<span>OFF</span>"<span>)</span><span> </span><span>{</span>
<span>      </span><span>// Remove the CSS file when the user turns the extension off</span>
<span>      </span><span>await</span><span> </span><span>chrome</span><span>.</span><span>scripting</span><span>.</span><span>removeCSS</span><span>({</span>
<span>        </span><span>files</span><span>:</span><span> </span><span>[</span>"<span>focus</span><span>-</span><span>mode</span><span>.</span><span>css</span>"<span>],</span>
<span>        </span><span>target</span><span>:</span><span> </span><span>{</span><span> </span><span>tabId</span><span>:</span><span> </span><span>tab</span><span>.</span><span>id</span><span> </span><span>},</span>
<span>      </span><span>});</span>
<span>    </span><span>}</span>
<span>  </span><span>}</span>
<span>});</span>
```

💡 **Могу ли я использовать API сценариев для внедрения кода вместо таблицы стилей?**

Да. Вы можете использовать [`scripting.executeScript()`](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru#injected-code) для внедрения JavaScript.

### _Необязательно: назначьте сочетание клавиш_

Просто ради интереса добавьте ярлык, чтобы упростить включение или отключение режима фокусировки. Добавьте ключ `"commands"` в манифест.

```
<span>{</span>
<span>  </span><span>...</span>
<span>  </span>"<span>comma</span><span>n</span><span>ds</span>"<span>:</span><span> </span><span>{</span>
<span>    </span>"<span>_execu</span><span>te</span><span>_ac</span><span>t</span><span>io</span><span>n</span>"<span>:</span><span> </span><span>{</span>
<span>      </span>"<span>sugges</span><span>te</span><span>d_key</span>"<span>:</span><span> </span><span>{</span>
<span>        </span>"<span>de</span><span>fault</span>"<span>:</span><span> </span>"<span>C</span><span>trl</span><span>+B</span>"<span>,</span>
<span>        </span>"<span>mac</span>"<span>:</span><span> </span>"<span>Comma</span><span>n</span><span>d+B</span>"
<span>      </span><span>}</span>
<span>    </span><span>}</span>
<span>  </span><span>}</span>
<span>}</span>
```

Клавиша `"_execute_action"` запускает тот же код, что и событие `action.onClicked()` , поэтому дополнительный код не требуется.

## Проверьте, что это работает

Убедитесь, что файловая структура вашего проекта выглядит следующим образом:

![Содержимое папки режима фокуса: манифест.json, фон.js, focus-mode.css и папка изображений.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/scripts-activetab/image/the-contents-the-focus-m-6e0ec866ea578.png?hl=ru)

### Загрузите расширение локально

Чтобы загрузить распакованное расширение в режиме разработчика, выполните действия, описанные в разделе [Hello World](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru#load-unpacked) .

### Протестируйте расширение на странице документации.

Сначала откройте любую из следующих страниц:

-   [Добро пожаловать в документацию по расширениям Chrome](https://developer.chrome.com/docs/extensions?hl=ru)
-   [Публикация в Интернет-магазине Chrome](https://developer.chrome.com/docs/webstore/publish?hl=ru)
-   [API сценариев](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=ru)

Затем нажмите действие расширения. Если вы настроили [сочетание клавиш](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-activetab?hl=ru#step-6) , вы можете проверить его, нажав `Ctrl + B` или `Cmd + B` .

Отсюда следует исходить:

![Расширение режима фокусировки ВЫКЛ.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/scripts-activetab/image/focus-mode-extension-off-dc8f9326aa92b.png?hl=ru)

Расширение режима фокусировки отключено

На это:

![Расширение режима фокусировки включено](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/scripts-activetab/image/focus-mode-extension-on-c248a59b498ea.png?hl=ru)

Расширение режима фокусировки включено

## 🎯 Возможные улучшения

Основываясь на том, что вы узнали сегодня, попробуйте выполнить любое из следующих действий:

-   Улучшите таблицу стилей CSS.
-   Назначьте другое сочетание клавиш.
-   Измените макет вашего любимого блога или сайта документации.

## Продолжайте строить.

Поздравляем с завершением этого урока 🎉. Продолжайте совершенствовать свои навыки, выполнив другие уроки из этой серии:

| Расширение | Что вы узнаете |
| --- | --- |
| [Время чтения](https://developer.chrome.com/docs/extensions/get-started/tutorial/scripts-on-every-tab?hl=ru) | Автоматическая вставка элемента в определенный набор страниц. |
| [Менеджер вкладок](https://developer.chrome.com/docs/extensions/get-started/tutorial/popup-tabs-manager?hl=ru) | Создать всплывающее окно, управляющее вкладками браузера. |

## Продолжить изучение

Мы надеемся, что вам понравилось создавать это расширение Chrome, и мы рады продолжить ваше обучение разработке расширений. Мы рекомендуем следующие пути обучения:

-   [Руководство разработчика](https://developer.chrome.com/docs/extensions/develop?hl=ru) содержит десятки дополнительных ссылок на документацию, относящуюся к созданию расширенных расширений.
-   Расширения имеют доступ к мощным API, помимо тех, которые доступны в открытой сети. [В документации по API Chrome](https://developer.chrome.com/docs/extensions/reference/api?hl=ru) описан каждый API.
