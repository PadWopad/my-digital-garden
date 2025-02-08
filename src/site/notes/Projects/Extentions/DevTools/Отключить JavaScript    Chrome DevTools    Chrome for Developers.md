---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/otklyuchit-java-script-chrome-dev-tools-chrome-for-developers/"}
---


# Отключить JavaScript  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Откройте командное меню и выполните команду «Отключить JavaScript».

---
![София Емельянова](https://web.dev/images/authors/sofiayem.jpg?hl=ru)

Чтобы увидеть, как веб-страница выглядит и ведет себя, когда JavaScript отключен:

1.  [Откройте Инструменты разработчика Chrome](https://developer.chrome.com/docs/devtools/open?hl=ru) .
2.  В зависимости от вашей операционной системы нажмите одну из следующих клавиш:
    
    -   В Windows или Linux: Control + Shift + P.
    -   В MacOS: Command + Shift + P.
    
    ![Командное меню.](https://developer.chrome.com/static/docs/devtools/javascript/disable/image/the-command-menu-6a5d68b955e31.png?hl=ru)
    
    Откроется **командное меню** .
    
3.  Начните вводить `javascript` , выберите **«Отключить JavaScript»** и нажмите Enter, чтобы запустить команду. JavaScript теперь отключен.
    
    ![Выбор «Отключить JavaScript» в меню команд.](https://developer.chrome.com/static/docs/devtools/javascript/disable/image/selecting-disable-javasc-78366e94532b5.png?hl=ru)
    

Чтобы напомнить вам, что JavaScript отключен, Chrome показывает соответствующее ![Отключен JavaScript.](https://developer.chrome.com/static/docs/devtools/javascript/disable/image/disabled-javascript-d2d171d8858c8.png?hl=ru) значок в адресной строке, и DevTools отображает предупреждение ![Предупреждение.](https://developer.chrome.com/static/docs/devtools/javascript/disable/image/warning-f5446d214a0a2.svg?hl=ru) значок рядом с **Источниками** .

![Значок в адресной строке и значок предупреждения рядом с источником в DevTools.](https://developer.chrome.com/static/docs/devtools/javascript/disable/image/an-icon-the-address-bar-d51fb4180a5e1.png?hl=ru)

JavaScript будет оставаться отключенным на этой вкладке, пока у вас открыты DevTools.

Возможно, вы захотите перезагрузить страницу, чтобы увидеть, зависит ли она от JavaScript во время загрузки и каким образом.

Альтернативно вы можете отключить JavaScript в ![Настройки.](https://developer.chrome.com/static/docs/devtools/javascript/disable/image/settings-682ede632e6b8.svg?hl=ru) [Настройки](https://developer.chrome.com/docs/devtools/settings?hl=ru#debugger) .

Чтобы снова включить JavaScript:

-   Снова откройте командное меню и выполните команду **«Включить JavaScript»** .
-   Закройте Инструменты разработчика.
