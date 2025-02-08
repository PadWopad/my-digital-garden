---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/chernyj-spisok-chrome-dev-tools-chrome-for-developers/"}
---


# Черный список  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Игнорировать ссылку на вкладку «Список».

---
![Настройки.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/settings-5712f3ab4684e.svg?hl=ru) [**«Настройки»**](https://developer.chrome.com/docs/devtools/settings?hl=ru#open) > **«Список игнорирования»** позволяют настроить список сценариев, которые игнорирует [отладчик](https://developer.chrome.com/docs/devtools/javascript?hl=ru) .

Чтобы включить или отключить все списки игнорирования для отладчика:

1.  [Открыть настройки](https://developer.chrome.com/docs/devtools/settings?hl=ru#open) .
2.  На вкладке **«Список игнорируемых»** установите или снимите флажок ![Настройки.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/settings-e2cd1395d457e.svg?hl=ru) **Настройки** > ![Флажок.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/checkbox-1897b60b022f.svg?hl=ru) **Включите «Игнорировать листинг»** . Это основной переключатель для всех возможностей списка игнорируемых пользователей.

![Установите флажок Включить игнорирование списка.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/enable-ignore-listing.png?hl=ru)

Включив список игнорирования, вы можете дополнительно настроить список игнорируемых сценариев.

## Игнорировать сценарии расширений Chrome

При использовании панели **«Источники»** в Chrome DevTools для [пошагового выполнения кода](https://developer.chrome.com/docs/devtools/javascript?hl=ru#code-stepping) иногда вы делаете паузу на незнакомом коде. Вероятно, вы остановились на коде одного из установленных вами расширений Chrome.

В ![Настройки.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/settings-ef4769dc014f3.svg?hl=ru) **Настройки** > **Список игнорирования** , включите две галочки:

![Настройки DevTools для игнорирования кода расширений.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/settings-devtools-ignore-81f83fc1283ee.png?hl=ru)

## Игнорировать известные сторонние скрипты

Чтобы отладчик пропускал известные сторонние скрипты, установите флажок ![Настройки.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/settings-9b63358e85a12.svg?hl=ru) **Настройки** > **Список игнорирования** > ![Флажок.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/checkbox-7007fbd43b88d.svg?hl=ru) **Автоматически добавлять известные сторонние скрипты в список игнорирования** .

DevTools добавляет сторонние скрипты в список игнорирования на основе свойства [ignoreList](https://developer.chrome.com/articles/x-google-ignore-list?hl=ru) в исходных картах. Платформы и сборщики должны предоставлять эту информацию.

Например, такие платформы, как Angular и Nuxt, поддерживают эту функцию.

## Игнорировать пользовательский список скриптов

По умолчанию **отладчик** игнорирует сценарии из `/node_modules/` и `/bower_components/` . Чтобы игнорировать дополнительный одиночный сценарий или пользовательский шаблон сценариев:

1.  Проверять ![Настройки.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/settings-fe10fff820da1.svg?hl=ru) **Настройки** > **Список игнорирования** > ![Флажок.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/checkbox-7a88c0555bda2.svg?hl=ru) **Включите «Игнорировать листинг»** .
2.  В разделе **«Пользовательские правила исключения»** нажмите **«Добавить шаблон»** . ![Добавление пользовательского шаблона в список игнорирования.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/adding-custom-pattern.png?hl=ru)
3.  Укажите имя сценария или регулярное выражение имен сценариев, которые следует игнорировать.
4.  Нажмите **«Добавить»** , чтобы сохранить изменения.

## Управление собственным списком игнорируемых скриптов

Чтобы включить или отключить игнорирование определенного сценария или шаблона имен сценариев, в ![Настройки.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/settings-8c3e4ef931a9f.svg?hl=ru) **Настройки** > **Список игнорирования** > **Пользовательские правила исключения** , установите или очистите флажок ![Флажок.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/checkbox-4a6f533ccad58.svg?hl=ru) флажок рядом со сценарием или шаблоном.

![Пользовательский список игнорирования с включенными именами шаблонов или сценариев.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/a-custom-ignore-list-a-p-fdb1b69a60ee9.png?hl=ru)

Чтобы отредактировать или удалить сценарий или шаблон имен сценариев, нажмите кнопку ![Редактировать.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/edit-d25d9730bde2.svg?hl=ru) или ![Удалить.](https://developer.chrome.com/static/docs/devtools/settings/ignore-list/image/delete-8c3239e3e9006.svg?hl=ru) кнопки, которые появляются при наведении.
