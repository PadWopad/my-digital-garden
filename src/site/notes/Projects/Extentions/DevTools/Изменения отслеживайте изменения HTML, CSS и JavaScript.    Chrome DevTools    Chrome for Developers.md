---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/izmeneniya-otslezhivajte-izmeneniya-html-css-i-java-script-chrome-dev-tools-chrome-for-developers/"}
---


# Изменения: отслеживайте изменения HTML, CSS и JavaScript.  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Отслеживайте изменения в HTML, CSS и JavaScript.

---
Используйте панель **«Изменения»** для отслеживания изменений кода, внесенных в DevTools.

## Обзор

С помощью панели **«Изменения»** отслеживайте изменения, которые вы вносите в:

-   HTML в [**источниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit) с включенными [локальными переопределениями](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides)
-   CSS в [**«Элементах»** > **«Стили**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) или [**источники»**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
-   JavaScript в [**исходниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)

На панели **«Изменения»** отображаются только изменения, внесенные вами в DevTools. Если вы перезагрузите DevTools или свою страницу, изменения исчезнут.

Чтобы DevTools сохранял изменения при загрузке страниц, выполните действия, описанные в разделе [Локальные переопределения](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides) .

Чтобы DevTools записывал изменения в ваши локальные источники, выполните действия, описанные в разделе [«Редактирование и сохранение файлов с помощью Workspaces»](https://developer.chrome.com/docs/devtools/workspaces?hl=ru) .

## Откройте панель «Изменения».

Чтобы открыть панель **«Изменения»** :

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
    
2.  Нажмите Command + Shift + P (Mac) или Control + Shift + P (Windows, Linux, ChromeOS), чтобы открыть **командное меню** .
    
3.  Начните вводить `changes` , выберите « **Показать изменения»** и нажмите Enter .
    
    ![Запустите команду «Показать изменения».](https://developer.chrome.com/static/docs/devtools/changes/image/run-show-changes-command-23263ba7e2577.png?hl=ru)
    

Либо в правом верхнем углу нажмите кнопку![](https://developer.chrome.com/static/docs/devtools/changes/image/N7wEDmtW9lnrSxPRupMa.svg?hl=ru) **Настраивайте и контролируйте DevTools** > **Дополнительные инструменты** > **Изменения** .

![Параметр «Изменения» находится в раскрывающемся списке «Дополнительные инструменты».](https://developer.chrome.com/static/docs/devtools/changes/image/more-tools-changes-f8b7202b524b.png?hl=ru)

По умолчанию DevTools отображает панель **«Изменения»** в нижней части окна DevTools, в **ящике** .

## Просмотр и понимание ваших изменений

Чтобы просмотреть изменения:

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
2.  Внесите изменения в исходники:
    
    -   HTML: сначала включите [локальные переопределения](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides) , затем внесите изменения в **источники.**
    -   CSS в [**«Элементах»** > **«Стили**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) или [**источники»**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
    -   JavaScript в [**исходниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
3.  [Откройте панель **«Изменения»**](https://developer.chrome.com/docs/devtools/changes?hl=ru#open-changes) и выберите файл в правой части панели.
    
4.  Обратите внимание на выходные `diff` , которые выделяют следующее:
    

![Выделенный диф на панели «Изменения»](https://developer.chrome.com/static/docs/devtools/changes/image/highlighted-diff-the-cha-5ac66c9170d43.png?hl=ru)

Панель **«Изменения»** автоматически печатает результаты `diff` , поэтому вам не придется прокручивать их по горизонтали, чтобы увидеть изменения в одной строке.

## Скопировать изменения CSS

Если вы внесли изменения в CSS в разделе [**«Элементы»** > **«Стили»**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) , вы можете скопировать их все одной кнопкой:

1.  [Откройте панель **«Изменения»**](https://developer.chrome.com/docs/devtools/changes?hl=ru#open-changes) и в правой части панели выберите файл CSS, в который вы внесли изменения.
    
    ![Копия.](https://developer.chrome.com/static/docs/devtools/changes/image/copy-e107336946db8.png?hl=ru)
    
2.  Нажмите кнопку ![Копия.](https://developer.chrome.com/static/docs/devtools/changes/image/copy-ec072678afe73.svg?hl=ru) Кнопка **«Копировать»** внизу **панели «Изменения»** .
    

## Отменить все изменения, внесенные в файл

Чтобы отменить изменения, внесенные в файл:

1.  В левой части панели **«Изменения»** выберите файл с изменениями, которые нужно отменить.
2.  На панели действий внизу нажмите ![Отменить](https://developer.chrome.com/static/docs/devtools/changes/image/undo-20a57d3c05e16.svg?hl=ru) **Отменить все изменения в текущем файле** .

![Кнопка возврата](https://developer.chrome.com/static/docs/devtools/changes/image/revert-button-becf5cafcf8bf.png?hl=ru)

,

![София Емельянова](https://web.dev/images/authors/sofiayem.jpg?hl=ru)

Используйте панель **«Изменения»** для отслеживания изменений кода, внесенных в DevTools.

## Обзор

С помощью панели **«Изменения»** отслеживайте изменения, которые вы вносите в:

-   HTML в [**источниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit) с включенными [локальными переопределениями](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides)
-   CSS в [**«Элементах»** > **«Стили**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) или [**источники»**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
-   JavaScript в [**исходниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)

На панели **«Изменения»** отображаются только изменения, внесенные вами в DevTools. Если вы перезагрузите DevTools или свою страницу, изменения исчезнут.

Чтобы DevTools сохранял изменения при загрузке страниц, выполните действия, описанные в разделе [Локальные переопределения](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides) .

Чтобы DevTools записывал изменения в ваши локальные источники, выполните действия, описанные в разделе [«Редактирование и сохранение файлов с помощью Workspaces»](https://developer.chrome.com/docs/devtools/workspaces?hl=ru) .

## Откройте панель «Изменения».

Чтобы открыть панель **«Изменения»** :

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
    
2.  Нажмите Command + Shift + P (Mac) или Control + Shift + P (Windows, Linux, ChromeOS), чтобы открыть **командное меню** .
    
3.  Начните вводить `changes` , выберите « **Показать изменения»** и нажмите Enter .
    
    ![Запустите команду «Показать изменения».](https://developer.chrome.com/static/docs/devtools/changes/image/run-show-changes-command-23263ba7e2577.png?hl=ru)
    

Либо в правом верхнем углу нажмите кнопку![](https://developer.chrome.com/static/docs/devtools/changes/image/N7wEDmtW9lnrSxPRupMa.svg?hl=ru) **Настраивайте и контролируйте DevTools** > **Дополнительные инструменты** > **Изменения** .

![Параметр «Изменения» находится в раскрывающемся списке «Дополнительные инструменты».](https://developer.chrome.com/static/docs/devtools/changes/image/more-tools-changes-f8b7202b524b.png?hl=ru)

По умолчанию DevTools отображает панель **«Изменения»** в нижней части окна DevTools, в **ящике** .

## Просмотр и понимание ваших изменений

Чтобы просмотреть изменения:

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
2.  Внесите изменения в исходники:
    
    -   HTML: сначала включите [локальные переопределения](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides) , затем внесите изменения в **источники.**
    -   CSS в [**«Элементах»** > **«Стили**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) или [**источники»**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
    -   JavaScript в [**исходниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
3.  [Откройте панель **«Изменения»**](https://developer.chrome.com/docs/devtools/changes?hl=ru#open-changes) и выберите файл в правой части панели.
    
4.  Обратите внимание на выходные `diff` , которые выделяют следующее:
    

![Выделенный диф на панели «Изменения»](https://developer.chrome.com/static/docs/devtools/changes/image/highlighted-diff-the-cha-5ac66c9170d43.png?hl=ru)

Панель **«Изменения»** автоматически печатает результаты `diff` , поэтому вам не придется прокручивать их по горизонтали, чтобы увидеть изменения в одной строке.

## Скопировать изменения CSS

Если вы внесли изменения в CSS в разделе [**«Элементы»** > **«Стили»**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) , вы можете скопировать их все одной кнопкой:

1.  [Откройте панель **«Изменения»**](https://developer.chrome.com/docs/devtools/changes?hl=ru#open-changes) и в правой части панели выберите файл CSS, в который вы внесли изменения.
    
    ![Копия.](https://developer.chrome.com/static/docs/devtools/changes/image/copy-e107336946db8.png?hl=ru)
    
2.  Нажмите кнопку ![Копия.](https://developer.chrome.com/static/docs/devtools/changes/image/copy-ec072678afe73.svg?hl=ru) Кнопка **«Копировать»** внизу **панели «Изменения»** .
    

## Отменить все изменения, внесенные в файл

Чтобы отменить изменения, внесенные в файл:

1.  В левой части панели **«Изменения»** выберите файл с изменениями, которые нужно отменить.
2.  На панели действий внизу нажмите ![Отменить](https://developer.chrome.com/static/docs/devtools/changes/image/undo-20a57d3c05e16.svg?hl=ru) **Отменить все изменения в текущем файле** .

![Кнопка возврата](https://developer.chrome.com/static/docs/devtools/changes/image/revert-button-becf5cafcf8bf.png?hl=ru)

,

![София Емельянова](https://web.dev/images/authors/sofiayem.jpg?hl=ru)

Используйте панель **«Изменения»** для отслеживания изменений кода, внесенных в DevTools.

## Обзор

С помощью панели **«Изменения»** отслеживайте изменения, которые вы вносите в:

-   HTML в [**источниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit) с включенными [локальными переопределениями](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides)
-   CSS в [**«Элементах»** > **«Стили**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) или [**источники»**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
-   JavaScript в [**исходниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)

На панели **«Изменения»** отображаются только изменения, внесенные вами в DevTools. Если вы перезагрузите DevTools или свою страницу, изменения исчезнут.

Чтобы DevTools сохранял изменения при загрузке страниц, выполните действия, описанные в разделе [Локальные переопределения](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides) .

Чтобы DevTools записывал изменения в ваши локальные источники, выполните действия, описанные в разделе [«Редактирование и сохранение файлов с помощью Workspaces»](https://developer.chrome.com/docs/devtools/workspaces?hl=ru) .

## Откройте панель «Изменения».

Чтобы открыть панель **«Изменения»** :

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
    
2.  Нажмите Command + Shift + P (Mac) или Control + Shift + P (Windows, Linux, ChromeOS), чтобы открыть **командное меню** .
    
3.  Начните вводить `changes` , выберите « **Показать изменения»** и нажмите Enter .
    
    ![Запустите команду «Показать изменения».](https://developer.chrome.com/static/docs/devtools/changes/image/run-show-changes-command-23263ba7e2577.png?hl=ru)
    

Либо в правом верхнем углу нажмите кнопку![](https://developer.chrome.com/static/docs/devtools/changes/image/N7wEDmtW9lnrSxPRupMa.svg?hl=ru) **Настраивайте и контролируйте DevTools** > **Дополнительные инструменты** > **Изменения** .

![Параметр «Изменения» находится в раскрывающемся списке «Дополнительные инструменты».](https://developer.chrome.com/static/docs/devtools/changes/image/more-tools-changes-f8b7202b524b.png?hl=ru)

По умолчанию DevTools отображает панель **«Изменения»** в нижней части окна DevTools, в **ящике** .

## Просмотр и понимание ваших изменений

Чтобы просмотреть изменения:

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
2.  Внесите изменения в исходники:
    
    -   HTML: сначала включите [локальные переопределения](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides) , затем внесите изменения в **источники.**
    -   CSS в [**«Элементах»** > **«Стили**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) или [**источники»**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
    -   JavaScript в [**исходниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
3.  [Откройте панель **«Изменения»**](https://developer.chrome.com/docs/devtools/changes?hl=ru#open-changes) и выберите файл в правой части панели.
    
4.  Обратите внимание на выходные `diff` , которые выделяют следующее:
    

![Выделенный диф на панели «Изменения»](https://developer.chrome.com/static/docs/devtools/changes/image/highlighted-diff-the-cha-5ac66c9170d43.png?hl=ru)

Панель **«Изменения»** автоматически печатает результаты `diff` , поэтому вам не придется прокручивать их по горизонтали, чтобы увидеть изменения в одной строке.

## Скопировать изменения CSS

Если вы внесли изменения в CSS в разделе [**«Элементы»** > **«Стили»**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) , вы можете скопировать их все одной кнопкой:

1.  [Откройте панель **«Изменения»**](https://developer.chrome.com/docs/devtools/changes?hl=ru#open-changes) и в правой части панели выберите файл CSS, в который вы внесли изменения.
    
    ![Копия.](https://developer.chrome.com/static/docs/devtools/changes/image/copy-e107336946db8.png?hl=ru)
    
2.  Нажмите кнопку ![Копия.](https://developer.chrome.com/static/docs/devtools/changes/image/copy-ec072678afe73.svg?hl=ru) Кнопка **«Копировать»** внизу **панели «Изменения»** .
    

## Отменить все изменения, внесенные в файл

Чтобы отменить изменения, внесенные в файл:

1.  В левой части панели **«Изменения»** выберите файл с изменениями, которые нужно отменить.
2.  На панели действий внизу нажмите ![Отменить](https://developer.chrome.com/static/docs/devtools/changes/image/undo-20a57d3c05e16.svg?hl=ru) **Отменить все изменения в текущем файле** .

![Кнопка возврата](https://developer.chrome.com/static/docs/devtools/changes/image/revert-button-becf5cafcf8bf.png?hl=ru)

,

![София Емельянова](https://web.dev/images/authors/sofiayem.jpg?hl=ru)

Используйте панель **«Изменения»** для отслеживания изменений кода, внесенных в DevTools.

## Обзор

С помощью панели **«Изменения»** отслеживайте изменения, которые вы вносите в:

-   HTML в [**источниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit) с включенными [локальными переопределениями](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides)
-   CSS в [**«Элементах»** > **«Стили**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) или [**источники»**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
-   JavaScript в [**исходниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)

На панели **«Изменения»** отображаются только изменения, внесенные вами в DevTools. Если вы перезагрузите DevTools или свою страницу, изменения исчезнут.

Чтобы DevTools сохранял изменения при загрузке страниц, выполните действия, описанные в разделе [Локальные переопределения](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides) .

Чтобы DevTools записывал изменения в ваши локальные источники, выполните действия, описанные в разделе [«Редактирование и сохранение файлов с помощью Workspaces»](https://developer.chrome.com/docs/devtools/workspaces?hl=ru) .

## Откройте панель «Изменения».

Чтобы открыть панель **«Изменения»** :

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
    
2.  Нажмите Command + Shift + P (Mac) или Control + Shift + P (Windows, Linux, ChromeOS), чтобы открыть **командное меню** .
    
3.  Начните вводить `changes` , выберите « **Показать изменения»** и нажмите Enter .
    
    ![Запустите команду «Показать изменения».](https://developer.chrome.com/static/docs/devtools/changes/image/run-show-changes-command-23263ba7e2577.png?hl=ru)
    

Либо в правом верхнем углу нажмите кнопку![](https://developer.chrome.com/static/docs/devtools/changes/image/N7wEDmtW9lnrSxPRupMa.svg?hl=ru) **Настраивайте и контролируйте DevTools** > **Дополнительные инструменты** > **Изменения** .

![Параметр «Изменения» находится в раскрывающемся списке «Дополнительные инструменты».](https://developer.chrome.com/static/docs/devtools/changes/image/more-tools-changes-f8b7202b524b.png?hl=ru)

По умолчанию DevTools отображает панель **«Изменения»** в нижней части окна DevTools, в **ящике** .

## Просмотр и понимание ваших изменений

Чтобы просмотреть изменения:

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
2.  Внесите изменения в исходники:
    
    -   HTML: сначала включите [локальные переопределения](https://developer.chrome.com/blog/new-in-devtools-65?hl=ru#overrides) , затем внесите изменения в **источники.**
    -   CSS в [**«Элементах»** > **«Стили**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) или [**источники»**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
    -   JavaScript в [**исходниках**](https://developer.chrome.com/docs/devtools/javascript/sources?hl=ru#edit)
3.  [Откройте панель **«Изменения»**](https://developer.chrome.com/docs/devtools/changes?hl=ru#open-changes) и выберите файл в правой части панели.
    
4.  Обратите внимание на выходные `diff` , которые выделяют следующее:
    

![Выделенный дифф на панели «Изменения»](https://developer.chrome.com/static/docs/devtools/changes/image/highlighted-diff-the-cha-5ac66c9170d43.png?hl=ru)

Панель **«Изменения»** автоматически печатает результаты `diff` , поэтому вам не придется прокручивать их по горизонтали, чтобы увидеть изменения в одной строке.

## Скопировать изменения CSS

Если вы внесли изменения в CSS в [разделе **«Элементы»** > **«Стили»**](https://developer.chrome.com/docs/devtools/css?hl=ru#declarations) , вы можете скопировать их все одной кнопкой:

1.  [Откройте панель **«Изменения»**](https://developer.chrome.com/docs/devtools/changes?hl=ru#open-changes) и в правой части панели выберите файл CSS, в который вы внесли изменения.
    
    ![Копия.](https://developer.chrome.com/static/docs/devtools/changes/image/copy-e107336946db8.png?hl=ru)
    
2.  Нажмите кнопку ![Копия.](https://developer.chrome.com/static/docs/devtools/changes/image/copy-ec072678afe73.svg?hl=ru) Кнопка **«Копировать»** внизу **панели «Изменения»** .
    

## Отменить все изменения, внесенные в файл

Чтобы отменить изменения, внесенные в файл:

1.  В левой части панели **«Изменения»** выберите файл с изменениями, которые нужно отменить.
2.  На панели действий внизу нажмите ![Отменить](https://developer.chrome.com/static/docs/devtools/changes/image/undo-20a57d3c05e16.svg?hl=ru) **Отменить все изменения в текущем файле** .

![Кнопка возврата](https://developer.chrome.com/static/docs/devtools/changes/image/revert-button-becf5cafcf8bf.png?hl=ru)
