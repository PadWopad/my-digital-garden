---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/web-authn-emulyacziya-autentifikatorov-chrome-dev-tools-chrome-for-developers/"}
---


# WebAuthn: эмуляция аутентификаторов  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Эмуляция аутентификаторов и отладка WebAuthn в Chrome DevTools.

---
![Джеселин Йен](https://web.dev/images/authors/jecelynyeen.jpg?hl=ru)

![София Емельянова](https://web.dev/images/authors/sofiayem.jpg?hl=ru)

Используйте панель **WebAuthn** для создания и взаимодействия с программными виртуальными аутентификаторами.

## Обзор

Панель **WebAuthn** позволяет добавлять, переименовывать и удалять средства аутентификации. Зарегистрируйте учетные данные, которые аналогичны пользователям, в аутентификаторе и отслеживайте **идентификаторы** , **дескрипторы пользователей** и **количество подписей** во время тестирования.

## Откройте панель WebAuthn

1.  Посетите страницу, использующую WebAuthn, например нашу [демонстрационную страницу](https://try-webauthn.appspot.com/?hl=ru) (войдите в систему, чтобы получить доступ к странице).
2.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
3.  Откройте **командное меню,** нажав:
    -   macOS: Command + Shift + P
    -   Windows, Linux, ChromeOS: Control + Shift + P.
4.  Начните вводить `webauthn` , выберите **«Показать WebAuthn»** и нажмите Enter .

Либо в правом верхнем углу нажмите **«Дополнительные параметры».** ![Более](https://developer.chrome.com/static/docs/devtools/webauthn/image/more-3775331e721da.png?hl=ru) > **Дополнительные инструменты** > **WebAuthn** , чтобы открыть панель **WebAuthn** .

![Панель WebAuthn](https://developer.chrome.com/static/docs/devtools/webauthn/image/webauthn-tab-78a1bc6540bc9.png?hl=ru)

## Включите среду виртуальной аутентификации

1.  На панели **WebAuthn** установите флажок check\_box **Включить виртуальную среду аутентификации** .
2.  После включения появится раздел **«Новый аутентификатор»** .

![Включить среду виртуальной аутентификации](https://developer.chrome.com/static/docs/devtools/webauthn/image/enable-virtual-authentica-683cd60113652.png?hl=ru)

## Добавить виртуальный аутентификатор

Чтобы добавить новый виртуальный аутентификатор:

1.  В разделе **Новый аутентификатор** настройте следующие параметры:
    
    1.  [**Протокол**](https://w3c.github.io/webauthn/) : `ctap2` (протокол клиент-аутентификатор) или `u2f` (универсальный 2-й фактор)
    2.  [**Транспорт**](https://w3c.github.io/webauthn/#dom-publickeycredentialdescriptor-transports) : `usb` , `nfc` , `ble` или `internal`
    3.  [**Поддерживает резидентные ключи**](https://w3c.github.io/webauthn/#dom-authenticatorselectioncriteria-requireresidentkey)
    4.  [**Поддерживает проверку пользователя**](https://w3c.github.io/webauthn/#enumdef-userverificationrequirement)
    5.  [**Поддерживает большие BLOB-объекты**](https://fidoalliance.org/specs/fido-v2.1-ps-20210615/fido-client-to-authenticator-protocol-v2.1-ps-20210615.html#sctn-largeBlobKey-extension) , доступно только для протокола `ctap2` с поддержкой резидентных ключей.
    
    Например:
    
    ![Добавление нового виртуального аутентификатора.](https://developer.chrome.com/static/docs/devtools/webauthn/image/adding-new-virtual-authe-b2810f60698f6.png?hl=ru)
    
2.  Нажмите кнопку **Добавить** .
    
3.  Теперь вы можете увидеть раздел с вашим недавно созданным аутентификатором. ![Аутентификатор](https://developer.chrome.com/static/docs/devtools/webauthn/image/authenticator-ed9154a945eaf.png?hl=ru)
    

Раздел **«Аутентификатор»** включает таблицу **учетных данных** . Таблица пуста, пока учетные данные не будут зарегистрированы в аутентификаторе.

![Нет учетных данных](https://developer.chrome.com/static/docs/devtools/webauthn/image/no-credentials-0b8720f65d127.png?hl=ru)

### Зарегистрируйте новые учетные данные

Чтобы зарегистрировать новые учетные данные, вам необходимо иметь веб-страницу, использующую WebAuthn, например, нашу [демонстрационную страницу](https://try-webauthn.appspot.com/?hl=ru) .

1.  На демонстрационной странице нажмите **Зарегистрировать новые учетные данные** .
2.  Новые учетные данные теперь добавляются в таблицу **«Учетные данные»** на панели WebAuthn.

![Просмотр учетных данных](https://developer.chrome.com/static/docs/devtools/webauthn/image/view-credentials-058608b2a1ad5.png?hl=ru)

На демонстрационной странице вы можете нажать кнопку **«Аутентификация»** несколько раз. Обратите внимание на таблицу **учетных данных** . **Количество знаков** учетных данных соответственно увеличится.

### Экспорт и удаление учетных данных

Вы можете экспортировать или удалить учетные данные, нажав кнопки **«Экспорт»** или **«Удалить»** .

![Экспортировать или удалить учетные данные](https://developer.chrome.com/static/docs/devtools/webauthn/image/export-remove-credentia-961c317ba160b.png?hl=ru)

## Переименование аутентификатора

1.  Чтобы переименовать аутентификатор, нажмите кнопку **«Изменить»** рядом с именем аутентификатора.
2.  Отредактируйте имя, затем нажмите **Enter,** чтобы сохранить изменения.

![Переименование аутентификатора](https://developer.chrome.com/static/docs/devtools/webauthn/image/rename-authenticator-680d847c2a7ba.png?hl=ru)

## Активировать аутентификатор

Вновь созданный аутентификатор активируется автоматически. DevTools поддерживает только один активный виртуальный аутентификатор в любой момент времени.

Чтобы деактивировать аутентификацию, удалите текущий активный аутентификатор.

Чтобы активировать аутентификатор, выберите его переключатель **«Активный** ».

![Установить активный аутентификатор](https://developer.chrome.com/static/docs/devtools/webauthn/image/set-active-authenticator-678d8cbd9fdcd.png?hl=ru)

## Удаление виртуального аутентификатора

Чтобы удалить виртуальный аутентификатор, нажмите его кнопку **«Удалить»** .

![Удалить аутентификатор](https://developer.chrome.com/static/docs/devtools/webauthn/image/remove-authenticator-c30d855c11e5e.png?hl=ru)
