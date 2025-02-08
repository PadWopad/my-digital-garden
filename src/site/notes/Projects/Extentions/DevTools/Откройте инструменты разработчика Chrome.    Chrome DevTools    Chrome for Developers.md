---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/otkrojte-instrumenty-razrabotchika-chrome-chrome-dev-tools-chrome-for-developers/"}
---


# Откройте инструменты разработчика Chrome.  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Все способы открытия Chrome DevTools.

---
![Джеселин Йен](https://web.dev/images/authors/jecelynyeen.jpg?hl=ru)

![София Емельянова](https://web.dev/images/authors/sofiayem.jpg?hl=ru)

Есть много способов открыть Chrome DevTools. Выберите свой любимый способ из этого подробного справочника.

Вы можете получить доступ к DevTools с помощью пользовательского интерфейса Chrome или клавиатуры:

-   Из [раскрывающихся меню в Chrome](https://developer.chrome.com/docs/devtools/open?hl=ru#chrome-menu) .
-   С помощью специальных [ярлыков](https://developer.chrome.com/docs/devtools/open?hl=ru#shortcuts) , которые открывают **Elements** , **Console** или последнюю использованную вами панель.

Кроме того, узнайте, как [автоматически открывать DevTools для каждой новой вкладки](https://developer.chrome.com/docs/devtools/open?hl=ru#auto) .

Если вы предпочитаете пользовательский интерфейс, вы можете получить доступ к DevTools из раскрывающихся меню в Chrome.

### Откройте панель «Элементы», чтобы проверить DOM или CSS.

Чтобы проверить, щелкните правой кнопкой мыши элемент на странице и выберите **«Проверить»** .

![Параметр «Проверить» в раскрывающемся меню Chrome.](https://developer.chrome.com/static/docs/devtools/open/image/the-inspect-option-a-dro-e98bce489fabb.png?hl=ru)

DevTools открывает панель **«Элементы»** и выбирает элемент в дереве DOM. На панели **«Стили»** вы можете увидеть правила CSS, примененные к выбранному элементу.

![Элемент, выбранный на панели «Элементы».](https://developer.chrome.com/static/docs/devtools/open/image/an-element-selected-the-45e3ba473a721.png?hl=ru)

### Откройте последнюю панель, которую вы использовали, из главного меню Chrome.

Чтобы открыть последнюю панель DevTools, нажмите кнопку ![Трехточечное меню.](https://developer.chrome.com/static/docs/devtools/open/image/three-dot-menu-ee1d03807aa8f.svg?hl=ru) кнопку справа от адресной строки и выберите **«Дополнительные инструменты»** > **«Инструменты разработчика»** .

![Параметр «Инструменты разработчика» выбран в трехточечном меню.](https://developer.chrome.com/static/docs/devtools/open/image/the-developer-tools-optio-2d9d9b7c0ac96.png?hl=ru)

Альтернативно вы можете открыть последнюю панель с помощью ярлыка. Дополнительную информацию смотрите в следующем разделе.

## Открывайте панели с помощью ярлыков: «Элементы», «Консоль» или последнюю панель.

Если вы предпочитаете клавиатуру, нажмите сочетание клавиш в Chrome в зависимости от вашей операционной системы:

| ОС | Элементы | Консоль | Ваша последняя панель |
| --- | --- | --- | --- |
| Windows или Linux | Ctrl + Shift + **С** | Ctrl + Shift + **J** | F12  
Ctrl + Shift + **Я** |
| Мак | Cmd + Опция + **С** | Cmd + Опция + **J** | Фн + Ф12  
Cmd + Опция + **Я** |

Вот простой способ запомнить сочетания клавиш:

-   **C** означает CSS.
-   **J** для JavaScript.
-   **Я** обозначаю ваш выбор.

Ярлык **C** открывает панель **«Элементы»** в ![Осмотрите.](https://developer.chrome.com/static/docs/devtools/open/image/inspect-bd09fdef1b09d.png?hl=ru) режим инспектора. В этом режиме отображаются полезные всплывающие подсказки при наведении курсора на элементы на странице. Вы также можете щелкнуть любой элемент, чтобы просмотреть его CSS на панели **«Элементы»** > **«Стили»** .

![Панель «Элементы» в режиме инспектора с подсказкой.](https://developer.chrome.com/static/docs/devtools/open/image/the-elements-panel-inspe-6e5ff3c13f7a3.png?hl=ru)

Полный список сочетаний клавиш DevTools см. в [разделе «Сочетания клавиш»](https://developer.chrome.com/docs/devtools/shortcuts?hl=ru) .

## Автоматически открывать DevTools на каждой новой вкладке

Запустите Chrome из командной строки и передайте флаг `--auto-open-devtools-for-tabs` :

1.  Закройте любой запущенный экземпляр Chrome.
    
2.  Запустите ваш любимый терминал или приложение командной строки.
    
3.  В зависимости от вашей операционной системы выполните следующую команду:
    

-   МакОС:
    
    ```
    open<span> </span>-a<span> </span>"Google<span> </span>Chrome"<span> </span>--args<span> </span>--auto-open-devtools-for-tabs
    ```
    
-   Окна:
    
    ```
    start<span> </span>chrome<span> </span>--auto-open-devtools-for-tabs
    ```
    
-   Линукс:
    
    ```
    google-chrome<span> </span>--auto-open-devtools-for-tabs
    ```
    

DevTools будет автоматически открываться для каждой новой вкладки, пока вы не закроете Chrome.

## Что дальше?

Затем посмотрите следующее видео, чтобы узнать некоторые полезные сочетания клавиш и настройки для более быстрой навигации по DevTools.

Чтобы получить более практический опыт обучения, посмотрите [, как настроить DevTools](https://developer.chrome.com/docs/devtools/customize?hl=ru) .
