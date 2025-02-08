---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/zapusk-komand-v-menyu-komand-chrome-dev-tools-chrome-for-developers/"}
---


# Запуск команд в меню команд  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Руководство о том, как открыть командное меню, запускать команды, открывать файлы, просматривать другие действия и многое другое.

---
![София Емельянова](https://web.dev/images/authors/sofiayem.jpg?hl=ru)

**Меню команд** обеспечивает быстрый способ навигации по пользовательскому интерфейсу Chrome DevTools и выполнения общих задач, таких как [отключение JavaScript](https://developer.chrome.com/docs/devtools/javascript/disable?hl=ru) . Возможно, вы знакомы с похожей функцией в Visual Studio Code, называемой « [Палитра команд»](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette) , которая послужила первоначальным источником вдохновения для **меню команд** .

![Командное меню.](https://developer.chrome.com/static/docs/devtools/command-menu/image/the-command-menu-548e4aa6667da.png?hl=ru)

## Откройте командное меню

Чтобы открыть **командное меню** :

-   Нажмите Control + Shift + P (Windows/Linux) или Command + Shift + P (Mac).
-   Нажмите ![Настраивайте и управляйте DevTools.](https://developer.chrome.com/static/docs/devtools/command-menu/image/customize-control-devtoo-e0e773bec2e98.svg?hl=ru) **Настройте DevTools и управляйте ими** , а затем выберите **команду «Выполнить»** .

![Команда запуска.](https://developer.chrome.com/static/docs/devtools/command-menu/image/run-command-28db4161e1508.png?hl=ru)

## Открыть файлы

Если вы используете рабочий процесс, описанный в разделе [«Открытие командного меню»](https://developer.chrome.com/docs/devtools/command-menu?hl=ru#open) , **командное меню** открывается с добавленным в текстовом поле `Run >` .

Вместо этого, чтобы открыть файл, удалите символ `>` и начните вводить имя файла.

![Открыть.](https://developer.chrome.com/static/docs/devtools/command-menu/image/open-1dc1318d2f71a.png?hl=ru)

`Run` добавляет изменения к `Open` , а DevTools вместо этого ищет соответствующие файлы.

Альтернативно вы можете сразу перейти в меню **«Открыть файл»** одним из следующих способов:

-   Нажмите Control + P (Windows/Linux) или Command + P (Mac).
-   Нажмите ![Настраивайте и управляйте DevTools.](https://developer.chrome.com/static/docs/devtools/command-menu/image/customize-control-devtoo-3be146374e7c1.svg?hl=ru) **Настройте DevTools и управляйте ими** , а затем выберите **«Открыть файл»** .

### Открыть файлы из списка игнорируемых

По умолчанию DevTools скрывает файлы известных третьих лиц. Чтобы открывать такие файлы из меню, отключите параметр [«Скрыть источники из игнорируемого списка»](https://developer.chrome.com/docs/devtools/javascript/reference?hl=ru#hide-ignore-listed) на панели **«Источники»** .

## Делать скриншоты области

**Меню команд** позволяет делать снимки экрана вашего веб-сайта, подобно инструменту «Ножницы».

Чтобы сделать снимок экрана области, выполните следующие действия:

1.  [Откройте командное меню](https://developer.chrome.com/docs/devtools/command-menu?hl=ru#open) .
2.  Введите «скриншот».
3.  Выберите **«Снимок экрана области»** .
4.  Перетащите, чтобы выбрать любое место на странице, чтобы захватить его. ![Перетащите, чтобы сделать снимок экрана области.](https://developer.chrome.com/static/docs/devtools/command-menu/image/area-screenshot.gif?hl=ru)

Дополнительные способы создания снимков экрана с помощью DevTools см. [в разделе «4 способа создания снимков экрана с помощью DevTools»](https://developer.chrome.com/blog/devtools-tips-33?hl=ru) .

## Посмотреть другие доступные действия

Чтобы просмотреть другие действия, доступные в **командном меню** , удалите символ `>` и введите `?` .

![Другие действия.](https://developer.chrome.com/static/docs/devtools/command-menu/image/other-actions-804629b2411fa.png?hl=ru)
