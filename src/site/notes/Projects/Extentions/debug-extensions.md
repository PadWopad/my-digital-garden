---
{"dg-publish":true,"permalink":"/projects/extentions/debug-extensions/"}
---


# Отладка расширений  |  Chrome Extensions  |  Chrome for Developers

> ## Excerpt
> Инструкции по отладке расширений Chrome.

---
Расширения могут получить доступ к тем же [инструментам разработчика Chrome](https://developers.google.com/web/tools/chrome-devtools/?hl=ru) , что и веб-страницы. Чтобы стать экспертом в отладке расширений, вам необходимо знать, как находить журналы и ошибки различных компонентов расширения. В этом руководстве представлены основные методы отладки вашего расширения.

<iframe frameborder="0" allowfullscreen="" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" title="Debugging Chrome extensions #DevToolsTips" width="640" height="360" src="https://www.youtube.com/embed/Ta-YTDhiBIQ?origin=https%3A%2F%2Fdeveloper.chrome.com&amp;autoplay&amp;controls&amp;embed_domain&amp;enablejsapi=1&amp;end&amp;hl&amp;showinfo&amp;start&amp;video-id=Ta-YTDhiBIQ&amp;widgetid=1" id="widget2" data-gtm-yt-inspected-100007133_93="true" data-gtm-yt-inspected-183356566_95="true"></iframe>

## Прежде чем начать

В этом руководстве предполагается, что у вас есть базовый опыт веб-разработки. Мы рекомендуем прочитать [«Основы разработки»](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru) , чтобы ознакомиться с рабочим процессом разработки расширений. [Проектирование пользовательского интерфейса](https://developer.chrome.com/docs/extensions/develop/ui?hl=ru) дает вам представление об элементах пользовательского интерфейса, доступных в расширениях.

## Разорвать расширение

В этом руководстве будет поочередно сломан один компонент расширения, а затем продемонстрировано, как это исправить. Не забудьте исправить ошибки, обнаруженные в одном разделе, прежде чем переходить к следующему разделу. Начните с загрузки [примера Broken Color](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.broken-color) на GitHub.

### Отладка манифеста

Во-первых, давайте сломаем файл манифеста, изменив ключ `"version"` на `"versions"` :

манифест.json:

```
<span>{</span>
<span>  </span>"<span>na</span><span>me</span>"<span>:</span><span> </span>"<span>Broke</span><span>n</span><span> </span><span>Backgrou</span><span>n</span><span>d</span><span> </span><span>Color</span>"<span>,</span>
<span>  </span><s>"<span>versio</span><span>n</span>"<span>:</span><span> </span>"<span>1.0</span>"<span>,</span></s>
<span>  </span><strong>"<span>versio</span><span>ns</span>"<span>:</span><span> </span>"<span>1.0</span>"<span>,</span></strong>
<span>  </span>"<span>descrip</span><span>t</span><span>io</span><span>n</span>"<span>:</span><span> </span>"<span>Fix</span><span> </span><span>a</span><span>n</span><span> </span><span>Ex</span><span>tens</span><span>io</span><span>n</span><span>!</span>"<span>,</span>
<span>  </span><span>...</span>
<span>}</span>
```

Теперь попробуем [загрузить расширение локально](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=ru#load-unpacked) . Вы увидите диалоговое окно с ошибкой, указывающее на проблему:

```
Failed<span> </span>to<span> </span>load<span> </span>extension
Required<span> </span>value<span> </span>version<span> </span>is<span> </span>missing<span> </span>or<span> </span>invalid.<span> </span>It<span> </span>must<span> </span>be<span> </span>between<span> </span><span>1</span>-4<span> </span>dot-separated<span> </span>integers<span> </span>each<span> </span>between<span> </span><span>0</span><span> </span>and<span> </span><span>65536</span>.
Could<span> </span>not<span> </span>load<span> </span>manifest.
```

![Расширение с недопустимым ключом манифеста, вызывающее диалоговое окно с ошибкой при попытке загрузки.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/an-extension-an-invalid-9ab91f867f94c.png?hl=ru)

Диалоговое окно с ошибкой недопустимого ключа манифеста.

Если ключ манифеста недействителен, расширение не загружается, но Chrome подсказывает, как решить проблему.

Отмените это изменение и введите недопустимое разрешение, чтобы увидеть, что произойдет. Измените разрешение `"activeTab"` на `"activetab"` в нижнем регистре:

манифест.json:

```
<span>{</span>
<span>  </span><span>...</span>
<span>  </span><s>"<span>permissio</span><span>ns</span>"<span>:</span><span> </span><span>[</span>"<span>ac</span><span>t</span><span>iveTab</span>"<span>,</span><span> </span>"<span>scrip</span><span>t</span><span>i</span><span>n</span><span>g</span>"<span>,</span><span> </span>"<span>s</span><span>t</span><span>orage</span>"<span>],</span></s>
<span>  </span><strong>"<span>permissio</span><span>ns</span>"<span>:</span><span> </span><span>[</span>"<span>ac</span><span>t</span><span>ive</span><span>ta</span><span>b</span>"<span>,</span><span> </span>"<span>scrip</span><span>t</span><span>i</span><span>n</span><span>g</span>"<span>,</span><span> </span>"<span>s</span><span>t</span><span>orage</span>"<span>],</span></strong>
<span>  </span><span>...</span>
<span>}</span>
```

Сохраните расширение и попробуйте загрузить его еще раз. На этот раз он должен успешно загрузиться. На странице «Управление расширением» вы увидите три кнопки: **«Подробнее»** , **«Удалить»** и **«Ошибки»** . При возникновении ошибки надпись кнопки **«Ошибки»** становится красной. Нажмите кнопку **«Ошибки»** , чтобы увидеть следующую ошибку:

```
Permission<span> </span>'activetab'<span> </span>is<span> </span>unknown<span> </span>or<span> </span>URL<span> </span>pattern<span> </span>is<span> </span>malformed.
```

![При нажатии кнопки «Ошибка» отображается сообщение об ошибке.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/error-button-is-clicked-a7713a11553a.gif?hl=ru)

Находим сообщение об ошибке, нажав кнопку «Ошибки».

Прежде чем двигаться дальше, измените разрешение обратно, нажмите **«Очистить все»** в правом верхнем углу, чтобы очистить журналы, и перезагрузите расширение.

![Кнопка «Очистить все»](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/clear-button-2f67dd9230519.png?hl=ru)

Как очистить ошибки расширения.

### Отладка сервисного работника

#### Поиск журналов

Сервисный работник устанавливает цвет по умолчанию для хранилища и записывает его в консоль. Чтобы просмотреть этот журнал, откройте панель Chrome DevTools, выбрав синюю ссылку рядом с **пунктом «Проверить представления»** .

![Открытие DevTools для работника службы расширений.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/opening-devtools-the-ex-685e204e20773.png?hl=ru)

Сервисный работник регистрируется на панели Chrome DevTools.

#### Поиск ошибок

Давайте сломаем сервис-воркера, изменив `onInstalled` на `oninstalled` в нижнем регистре:

сервис-worker.js:

```
<span>// There's a typo in the line below;</span>
<span>// ❌ oninstalled should be ✅ onInstalled.</span>
<s><span>chrome</span><span>.</span><span>runtime</span><span>.</span><span>onInstalled</span><span>.</span><span>addListener</span><span>(()</span><span> </span><span>=</span>&gt;<span> </span><span>{</span><span> </span></s>
<strong><span>chrome</span><span>.</span><span>runtime</span><span>.</span><span>oninstalled</span><span>.</span><span>addListener</span><span>(()</span><span> </span><span>=</span>&gt;<span> </span><span>{</span><span> </span></strong>
<span>  </span><span>chrome</span><span>.</span><span>storage</span><span>.</span><span>sync</span><span>.</span><span>set</span><span>({</span><span> </span><span>color</span><span>:</span><span> </span>'<span>#</span><span>3</span><span>aa757</span>'<span> </span><span>},</span><span> </span><span>()</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>    </span><span>console</span><span>.</span><span>log</span><span>(</span>'<span>The</span><span> </span><span>background</span><span> </span><span>color</span><span> </span><span>is</span><span> </span><span>green</span><span>.');</span>
<span>  </span><span>});</span>
<span>});</span>
```

Обновите и нажмите **«Ошибки»** , чтобы просмотреть журнал ошибок. Первая ошибка сообщает о том, что сервисному работнику не удалось зарегистрироваться. Это означает, что во время инициализации что-то пошло не так:

```
Service<span> </span>worker<span> </span>registration<span> </span>failed.<span> </span>Status<span> </span>code:<span> </span><span>15</span>.
```

![Регистрация работника службы не удалась. Код состояния: 15 сообщение об ошибке](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/service-worker-registrati-9791df79120e6.png?hl=ru)

Сообщение об ошибке регистрации сервисного работника.

Фактическая ошибка возникает после:

```
Uncaught<span> </span>TypeError:<span> </span>Cannot<span> </span><span>read</span><span> </span>properties<span> </span>of<span> </span>undefined<span> </span><span>(</span>reading<span> </span>'addListener'<span>)</span>
```

![Uncaught TypeError: невозможно прочитать свойства неопределенного сообщения об ошибке](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/uncaught-typeerror-canno-45ae014961338.png?hl=ru)

Неперехваченное сообщение об ошибке типа.

Устраните обнаруженную нами ошибку, нажмите **«Очистить все»** в правом верхнем углу и перезагрузите расширение.

#### Проверьте статус сервисного работника

Вы можете определить, когда сервисный работник просыпается для выполнения задач, выполнив следующие действия:

1.  Скопируйте идентификатор расширения, расположенный над «Проверкой представлений».
    
    ![Идентификатор расширения на странице «Управление расширениями».](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/extension-id-the-extensi-1a615e29e13bb.png?hl=ru)
    
    Идентификатор расширения на странице «Управление расширениями».
    
2.  Откройте файл манифеста в браузере. Например: `text chrome-extension://YOUR_EXTENSION_ID/manifest.json`
3.  Осмотрите файл.
4.  Перейдите на панель **приложений** .
5.  Перейдите на панель **Service Workers** .

Чтобы протестировать свой код, запустите или остановите сервис-воркера, используя ссылки рядом с **статусом** .

[![Статус сервисного работника на панели приложения](https://developer.chrome.com/docs/extensions/get-started/tutorial/debug/image/start-stop-service-worker.png?auto=format&w=845&hl=ru)](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/start-stop-service-worker.png?hl=ru)

Статус сервисного работника на панели приложения. (Нажмите, чтобы увеличить изображение.)

Кроме того, если вы внесли изменения в код сервисного работника, вы можете нажать **«Обновить»** или **пропустить «Ожидание»** , чтобы немедленно применить изменения.

[![Статус сервисного работника на панели приложения](https://developer.chrome.com/docs/extensions/get-started/tutorial/debug/image/update-or-skipwaiting.png?auto=format&w=845&hl=ru)](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/update-or-skipwaiting.png?hl=ru)

Обновление сервис-воркера на панели приложения. (Нажмите, чтобы увеличить изображение.)

Теперь, когда расширение инициализируется правильно, давайте разобьем всплывающее окно, закомментировав выделенные строки ниже:

всплывающее окно.js:

```
<span>...</span>
<span>changeColorButton</span><span>.</span><span>addEventListener</span><span>(</span>'<span>click</span>'<span>,</span><span> </span><span>(</span><span>event</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>{</span>
<span>  </span><span>const</span><span> </span><span>color</span><span> </span><span>=</span><span> </span><span>event</span><span>.</span><span>target</span><span>.</span><span>value</span><span>;</span>

<span>  </span><span>// Query the active tab before injecting the content script</span>
<span>  </span><strong><span>chrome</span><span>.</span><span>tabs</span><span>.</span><span>query</span><span>({</span><span> </span><span>active</span><span>:</span><span> </span><span>true</span><span>,</span><span> </span><span>currentWindow</span><span>:</span><span> </span><span>true</span><span> </span><span>},</span><span> </span><span>(</span><span>tabs</span><span>)</span><span> </span><span>=</span>&gt;<span> </span><span>{</span><span> </span></strong>
<span>    </span><span>// Use the Scripting API to execute a script</span>
<span>    </span><span>chrome</span><span>.</span><span>scripting</span><span>.</span><span>executeScript</span><span>({</span>
<span>      </span><span>target</span><span>:</span><span> </span><span>{</span><span> </span><span>tabId</span><span>:</span><span> </span><span>tabs</span><span>[</span><span>0</span><span>].</span><span>id</span><span> </span><span>},</span>
<span>      </span><span>args</span><span>:</span><span> </span><span>[</span><span>color</span><span>],</span>
<span>      </span><span>func</span><span>:</span><span> </span><span>setColor</span>
<span>    </span><span>});</span>
<span> <strong> </strong></span><strong><span>});</span></strong>
<span>});</span>
```

Вернитесь на страницу управления расширениями. Кнопка **«Ошибки»** появится снова. Нажмите на нее, чтобы просмотреть новый журнал. Он показывает следующее сообщение об ошибке:

```
Uncaught ReferenceError: tabs is not defined
```

![На странице управления расширениями отображается всплывающая ошибка](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/extensions-management-pag-00a0f48a76239.png?hl=ru)

На странице управления расширениями отображается всплывающая ошибка.

Вы можете открыть DevTools всплывающего окна, проверив всплывающее окно.

![DevTools отображает всплывающую ошибку.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/devtools-displaying-popup-0ed24fd80361a.png?hl=ru)

DevTools отображает всплывающую ошибку.

Ошибка « `tabs is undefined` говорит о том, что расширение не знает, куда вставить скрипт содержимого. Исправьте это, вызвав [`tabs.query()`](https://developer.chrome.com/docs/extensions/reference/api/tabs?hl=ru#method-query) и выбрав активную вкладку.

Чтобы обновить код, нажмите кнопку **«Очистить все»** в правом верхнем углу, а затем перезагрузите расширение.

### Отладка сценариев контента

Теперь давайте сломаем скрипт содержимого, изменив переменную «color» на «colors»:

контент.js:

```
<span>...</span>
<span>function</span><span> </span><span>setColor</span><span>(</span><span>color</span><span>)</span><span> </span><span>{</span>
<span>  </span><span>// There's a typo in the line below;</span>
<span>  </span><span>// ❌ colors should be ✅ color.</span>
<span>  </span><s><span>document</span><span>.</span><span>body</span><span>.</span><span>style</span><span>.</span><span>backgroundColor</span><span> </span><span>=</span><span> </span><span>color</span><span>;</span></s>
<span>  </span><strong><span>document</span><span>.</span><span>body</span><span>.</span><span>style</span><span>.</span><span>backgroundColor</span><span> </span><span>=</span><span> </span><span>colors</span><span>;</span></strong>
<span>}</span><span>  </span>
```  

Обновите страницу, откройте всплывающее окно и щелкните зеленое поле. Ничего не происходит.

Если вы перейдете на страницу «Управление расширениями», кнопка **«Ошибки»** не появится. Это связано с тем, что на странице управления расширениями записываются только ошибки времени выполнения, `console.warning` и `console.error` .

[Скрипты контента](https://developer.chrome.com/docs/extensions/develop/concepts/content-scripts?hl=ru) выполняются внутри веб-сайта. Поэтому, чтобы найти эти ошибки, мы должны проверить веб-страницу, которую расширение пытается изменить:

```
Uncaught<span> </span>ReferenceError:<span> </span>colors<span> </span>is<span> </span>not<span> </span>defined
```

![Ошибка расширения отображается в консоли веб-страницы](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/extension-error-displayed-ca9d8c6c336b.png?hl=ru)

Ошибка расширения отображается в консоли веб-страницы.

Чтобы использовать DevTools из сценария содержимого, щелкните стрелку раскрывающегося списка **вверху** и выберите расширение.

![Uncaught ReferenceError: цвета не определены](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/uncaught-referenceerror-e5847be3a7de9.png?hl=ru)

Uncaught ReferenceError: цвета не определены.

Ошибка говорит, что `colors` не определены. Расширение не должно правильно передавать переменную. Исправьте внедренный скрипт, чтобы передать в код переменную цвета.

## Мониторинг сетевых запросов

Всплывающее окно часто выполняет все необходимые сетевые запросы еще до того, как даже самые быстрые разработчики смогут открыть DevTools. Чтобы просмотреть эти запросы, обновите панель сети. Он перезагружает всплывающее окно, не закрывая панель DevTools.

![Обновите панель сети, чтобы просмотреть всплывающие сетевые запросы.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/debug/image/refresh-inside-network-p-43993068e650e.gif?hl=ru)

Обновите панель сети, чтобы просмотреть всплывающие сетевые запросы.

## Объявить разрешения

Для некоторых API расширений требуются разрешения. Обратитесь к статье [о разрешениях](https://developer.chrome.com/docs/extensions/develop/concepts/declare-permissions?hl=ru) и [API Chrome](https://developer.chrome.com/docs/extensions/reference/api?hl=ru) , чтобы убедиться, что расширение запрашивает правильные разрешения в [манифесте](https://developer.chrome.com/docs/extensions/reference/manifest?hl=ru) .

  ```
<span>  </span><span>{</span>
<span>    </span>"<span>na</span><span>me</span>"<span>:</span><span> </span>"<span>Broke</span><span>n</span><span> </span><span>Backgrou</span><span>n</span><span>d</span><span> </span><span>Color</span>"<span>,</span>
<span>    </span><span>...</span>
<span>    </span>"<span>permissio</span><span>ns</span>"<span>:</span><span> </span><span>[</span>
<span>      </span>"<span>ac</span><span>t</span><span>iveTab</span>"<span>,</span>
<span>      </span>"<span>declara</span><span>t</span><span>iveCo</span><span>ntent</span>"<span>,</span>
<span>      </span>"<span>s</span><span>t</span><span>orage</span>"
<span>    </span><span>],</span>
<span>  </span><span>...</span>
<span>  </span><span>}</span>
```

## Дальнейшее чтение

Узнайте больше о [Chrome Devtools](https://developers.google.com/web/tools/chrome-devtools/?hl=ru) , прочитав документацию.
