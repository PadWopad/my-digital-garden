---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/rabochaya-sreda-chrome-dev-tools-chrome-for-developers/"}
---


# Рабочая среда  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Ссылка на вкладку «Рабочая область».

---
![Настройки.](https://developer.chrome.com/static/docs/devtools/settings/workspace/image/settings-f86748ee39527.svg?hl=ru) [**Настройки**](https://developer.chrome.com/docs/devtools/settings?hl=ru#open) > [**Рабочая область**](https://developer.chrome.com/docs/devtools/workspaces?hl=ru) позволяет сохранять изменения, внесенные вами в DevTools, в исходный код, хранящийся на вашем компьютере.

Чтобы настроить рабочие пространства, откройте ![Настройки.](https://developer.chrome.com/static/docs/devtools/settings/workspace/image/settings-a41a15bc48fa5.svg?hl=ru) [Настройки](https://developer.chrome.com/docs/devtools/settings?hl=ru#open) > **Рабочая область** .

## Настройка исключений

**Шаблон исключения папок** — это глобальный шаблон RegEx по умолчанию, в котором перечислены общие и сторонние папки и типы файлов, которые DevTools исключает из рабочих областей, чтобы вы могли сосредоточиться только на своем коде. ![Шаблон исключения папки на вкладке «Рабочая область».](https://developer.chrome.com/static/docs/devtools/settings/workspace/image/folder-exclude-pattern-t-fce3770bb0868.png?hl=ru) Вы можете вручную добавлять в шаблон новые папки или типы файлов. Изменения шаблона вступают в силу после перезагрузки DevTools.

Чтобы изменить глобальный список исключенных папок и файлов по умолчанию, отредактируйте файл ![Настройки.](https://developer.chrome.com/static/docs/devtools/settings/workspace/image/settings-334dfa81d01e6.svg?hl=ru) **«Настройки** » > **«Рабочая область** » > «Текстовое поле **шаблона исключения папки** ».

## Управление рабочими пространствами

На вкладке **«Рабочая область»** перечислены папки, которые вы настроили как **рабочие области** , и для каждой папки подпапки, которые вы исключили вручную. ![Папка рабочей области с исключенными подпапками.](https://developer.chrome.com/static/docs/devtools/settings/workspace/image/a-workspace-folder-exclu-76e518d0e44f9.png?hl=ru) Изменения файлов в подпапках, перечисленных как исключенные, не сохраняются. Исключенные подпапки относятся к конкретному рабочему месту, а не глобально.

Чтобы добавить новую **рабочую область** :

1.  [Открыть настройки](https://developer.chrome.com/docs/devtools/settings?hl=ru#open) .
2.  На вкладке **«Рабочая область»** нажмите **«Добавить папку»** .
3.  Выберите папку с вашими исходниками.
4.  Нажмите **«Разрешить»** в приглашении вверху, чтобы разрешить DevTools вносить изменения в исходные коды. ![Запрос с запросом полного доступа к исходным кодам DevTools.](https://developer.chrome.com/static/docs/devtools/settings/workspace/image/the-prompt-requesting-ful-6bc9e108fd653.png?hl=ru)

Чтобы удалить рабочую область, нажмите ![Закрывать.](https://developer.chrome.com/static/docs/devtools/settings/workspace/image/close-d6dbbfe5bbe44.svg?hl=ru) рядом с соответствующей папкой.
