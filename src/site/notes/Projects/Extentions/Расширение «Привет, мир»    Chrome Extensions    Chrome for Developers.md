---
{"dg-publish":true,"permalink":"/projects/extentions/rasshirenie-privet-mir-chrome-extensions-chrome-for-developers/"}
---


# Расширение «Привет, мир»  |  Chrome Extensions  |  Chrome for Developers

> ## Excerpt
> Создайте свое первое расширение Hello World для Chrome.

---
Изучите основы разработки расширений Chrome, создав свое первое расширение Hello World.

## Обзор

Вы создадите пример «Hello World», загрузите расширение локально, найдёте журналы и изучите другие рекомендации.

## Привет, мир

Это расширение будет отображать «Hello Extensions», когда пользователь щелкнет значок расширения на панели инструментов.

![Привет, расширение](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/hello-extension-6e3eacba176d3.png?hl=ru)

Привет, всплывающее окно расширения

Начните с создания нового каталога для хранения файлов расширений. При желании вы можете скачать полный исходный код с [GitHub](https://github.com/GoogleChrome/chrome-extensions-samples/tree/main/functional-samples/tutorial.hello-world) .

Затем создайте в этом каталоге новый файл под названием `manifest.json` . Этот файл JSON описывает возможности и конфигурацию расширения. Например, большинство файлов манифеста содержат ключ `"action"` , который объявляет изображение, которое Chrome должен использовать в качестве значка действия расширения, и HTML-страницу, которая будет отображаться во всплывающем окне при нажатии значка действия расширения.

```
<span>{</span><span><br>&nbsp; </span><span>"manifest_version"</span><span>:</span><span> </span><span>3</span><span>,</span><span><br>&nbsp; </span><span>"name"</span><span>:</span><span> </span><span>"Hello Extensions"</span><span>,</span><span><br>&nbsp; </span><span>"description"</span><span>:</span><span> </span><span>"Base Level Extension"</span><span>,</span><span><br>&nbsp; </span><span>"version"</span><span>:</span><span> </span><span>"1.0"</span><span>,</span><span><br>&nbsp; </span><span>"action"</span><span>:</span><span> </span><span>{</span><span><br>&nbsp; &nbsp; </span><span>"default_popup"</span><span>:</span><span> </span><span>"hello.html"</span><span>,</span><span><br>&nbsp; &nbsp; </span><span>"default_icon"</span><span>:</span><span> </span><span>"hello_extensions.png"</span><span><br>&nbsp; </span><span>}</span><span><br></span><span>}</span><span><br></span>
```

[Загрузите значок](https://storage.googleapis.com/web-dev-uploads/image/WlD8wC6g8khYWPJUsQceQkhXSlv1/gmKIT88Ha1z8VBMJFOOH.png) в свой каталог и обязательно измените его имя, чтобы оно соответствовало тому, что указано в ключе `"default_icon"` .

Для всплывающего окна создайте файл `hello.html` и добавьте следующий код:

```
<span>&lt;html&gt;</span><span><br>&nbsp; </span><span>&lt;body&gt;</span><span><br>&nbsp; &nbsp; </span><span>&lt;h1&gt;</span><span>Hello Extensions</span><span>&lt;/h1&gt;</span><span><br>&nbsp; </span><span>&lt;/body&gt;</span><span><br></span><span>&lt;/html&gt;</span><span><br></span>
```

Расширение теперь отображает всплывающее окно при нажатии на значок действия расширения (значок на панели инструментов). Вы можете протестировать его в Chrome, загрузив локально. Убедитесь, что все файлы сохранены.

## Загрузите распакованное расширение

Чтобы загрузить распакованное расширение в режиме разработчика:

1.  Перейдите на страницу «Расширения», введя `chrome://extensions` на новой вкладке. (По замыслу URL-адреса `chrome://` не могут быть связаны.)
    -   Либо нажмите кнопку-головоломку меню «Расширения» и выберите **«Управление расширениями»** в нижней части меню.
    -   Или откройте меню Chrome, наведите указатель мыши на **«Дополнительные инструменты»** и выберите **«Расширения»** .
2.  Включите режим разработчика, щелкнув тумблер рядом с **режимом разработчика** .
3.  Нажмите кнопку **«Загрузить распакованное»** и выберите каталог расширения.
    
    ![Страница расширений](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/extensions-page-e0d64d89a6acf.png?hl=ru)
    
    Страница расширений (chrome://extensions)
    

Та-да! Расширение успешно установлено. Если в манифест не были включены значки расширений, для расширения будет создан общий значок.

## Закрепить расширение

По умолчанию, когда вы загружаете расширение локально, оно появляется в меню расширений ( ![Головоломка](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/puzzle-5416192fa9ae1.png?hl=ru) ). Закрепите расширение на панели инструментов, чтобы быстро получить доступ к нему во время разработки.

![Закрепление расширения](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/pinning-extension-215cb97773ab6.png?hl=ru)

Закрепление расширения

Нажмите значок действия расширения (значок на панели инструментов); вы должны увидеть всплывающее окно.

![привет, расширение мира](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/hello-world-extension-27a679d21340d.png?hl=ru)

Расширение «Привет, мир»

## Перезагрузить расширение

Вернитесь к коду и измените имя расширения на «Привет, расширения мира!» в манифесте.

```
<span>{</span><span><br>&nbsp; </span><span>"manifest_version"</span><span>:</span><span> </span><span>3</span><span>,</span><span><br>&nbsp; </span><span>"name"</span><span>:</span><span> </span><span>"Hello Extensions of the world!"</span><span>,</span><span><br>&nbsp; </span><span>...</span><span><br></span><span>}</span><span><br></span>
```

После сохранения файла, чтобы увидеть это изменение в браузере, вам также необходимо обновить расширение. Перейдите на страницу «Расширения» и щелкните значок обновления рядом с переключателем **включения** / **выключения** :

![Перезагрузить расширение](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/reload-extension-241cc5378fffb.png?hl=ru)

### Когда перезагрузить расширение

В следующей таблице показано, какие компоненты необходимо перезагрузить, чтобы увидеть изменения:

| Компонент расширения | Требуется перезагрузка расширения |
| --- | --- |
| Манифест | Да |
| Сервисный работник | Да |
| Скрипты контента | Да (плюс хост-страница) |
| Всплывающее окно | Нет |
| Страница параметров | Нет |
| Другие HTML-страницы расширений | Нет |

## Найдите журналы консоли и ошибки

### Журналы консоли

Во время разработки вы можете отлаживать свой код, обращаясь к журналам консоли браузера. В этом случае мы найдем журналы всплывающего окна. Начните с добавления тега сценария в `hello.html` .

```
<span>&lt;html&gt;</span><span><br>&nbsp; </span><span>&lt;body&gt;</span><span><br>&nbsp; &nbsp; </span><span>&lt;h1&gt;</span><span>Hello Extensions</span><span>&lt;/h1&gt;</span><span><br>&nbsp; &nbsp; </span><span>&lt;script</span><span> </span><span>src</span><span>=</span><span>"popup.js"</span><span>&gt;&lt;/script&gt;</span><span><br>&nbsp; </span><span>&lt;/body&gt;</span><span><br></span><span>&lt;/html&gt;</span><span><br></span>
```

Создайте файл `popup.js` и добавьте следующий код:

```
<span>console</span><span>.</span><span>log</span><span>(</span><span>"This is a popup!"</span><span>)</span><span><br></span>
```

Чтобы увидеть это сообщение в консоли:

1.  Откройте всплывающее окно.
2.  Щелкните правой кнопкой мыши всплывающее окно.
3.  Выберите **«Проверить»** .
    
    ![Проверка всплывающего окна.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/inspecting-popup-359e35efc3afb.png?hl=ru)
    
    Проверка всплывающего окна.
    
4.  В [DevTools](https://developer.chrome.com/docs/devtools?hl=ru) перейдите на панель **«Консоль»** .
    
    ![Панель кода DevTools](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/devtools-code-panel-71b4e1577c834.png?hl=ru)
    
    Проверка всплывающего окна
    

### Журналы ошибок

Теперь давайте сломаем расширение. Мы можем сделать это, удалив закрывающую кавычку в `popup.js` :

```
<span>console</span><span>.</span><span>log</span><span>(</span><span>"</span><span>This</span><span> is a popup</span><span>!)</span><span> </span><span>// ❌ broken code</span><span><br></span>
```

Перейдите на страницу «Расширения» и откройте всплывающее окно. Появится кнопка **«Ошибки»** .

![Страница расширений с кнопкой ошибки](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/extensions-page-error-bu-5c0c2b74fc8ee.png?hl=ru)

Нажмите кнопку **«Ошибки»** , чтобы узнать больше об ошибке:

![Подробности об ошибке расширения](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/extension-error-details-7784a142a2649.png?hl=ru)

Дополнительные сведения об отладке сервисного работника, страницы параметров и сценариев содержимого см. в [разделе Отладка расширений](https://developer.chrome.com/docs/extensions/get-started/tutorial/debug?hl=ru) .

## Структурируйте проект расширения

Существует много способов структурировать проект расширения; однако единственным обязательным условием является размещение файла манифеста.json в корневом каталоге расширения, как показано в следующем примере:

![Содержимое папки расширения: манифест.json, фон.js, папка сценариев, папка всплывающих окон и папка изображений.](https://developer.chrome.com/static/docs/extensions/get-started/tutorial/hello-world/image/the-contents-an-extensio-fc9e4690df76c.png?hl=ru)

## Используйте TypeScript

Если вы разрабатываете код с помощью [редактора кода](https://developer.mozilla.org/docs/Glossary/IDE) , такого как VSCode или Atom, вы можете использовать [chrome-types](https://www.npmjs.com/package/chrome-types) пакета npm, чтобы воспользоваться преимуществами автозаполнения для [Chrome API](https://developer.chrome.com/docs/extensions/reference?hl=ru) . Этот пакет npm обновляется автоматически при изменении исходного кода Chromium.

## 🚀 Готовы начать строить?

Выберите любое из следующих руководств, чтобы начать свой путь изучения расширений.
