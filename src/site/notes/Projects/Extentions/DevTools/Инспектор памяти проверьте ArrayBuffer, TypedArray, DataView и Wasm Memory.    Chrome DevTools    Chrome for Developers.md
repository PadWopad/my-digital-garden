---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/inspektor-pamyati-proverte-array-buffer-typed-array-data-view-i-wasm-memory-chrome-dev-tools-chrome-for-developers/"}
---


# Инспектор памяти: проверьте ArrayBuffer, TypedArray, DataView и Wasm Memory.  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Используйте инспектор памяти для проверки ArrayBuffer, TypedArray или DataView в JavaScript, а также WebAssembly.Memory of C++ Васм-приложения.

---
![София Емельянова](https://web.dev/images/authors/sofiayem.jpg?hl=ru)

Используйте **инспектор памяти** для проверки памяти `ArrayBuffer` , `TypedArray` и `DataView` в JavaScript, а также `WebAssembly.Memory` приложений Wasm, написанных на C++.

## Обзор

**Инспектор памяти** упорядочивает содержимое памяти и помогает быстро перемещаться по большим массивам. Вы можете просмотреть значения ASCII содержимого памяти непосредственно рядом с байтами и выбрать другой порядок байтов. Используйте **инспектор памяти** во время отладки веб-приложения, чтобы повысить эффективность рабочего процесса.

## Откройте инспектор памяти

Открыть **инспектор памяти** можно несколькими способами.

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
2.  Нажмите **«Дополнительные параметры».** ![Более](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/more-0d3265891c0d3.png?hl=ru) > **Дополнительные инструменты** > **Инспектор памяти** . ![Меню инспектора памяти](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/memory-inspector-menu-59bf7cfcb0055.png?hl=ru)

### Открыть во время отладки

1.  Откройте страницу с помощью JavaScript `ArrayBuffer` . Мы будем использовать [эту демонстрационную страницу](http://memory-inspector.glitch.me/demo-js.html) .
2.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
3.  Откройте файл **demo-js.js** на панели **«Источники»** , установите точку останова в строке 18.
4.  Обновите страницу.
5.  Разверните раздел **Область** на правой панели **Отладчика** .
6.  Вы можете открыть **инспектор памяти** :
    
    -   **Из значка** . Нажав на значок рядом со свойством `buffer` , или
    -   **Из контекстного меню** . Щелкните правой кнопкой мыши свойство `buffer` и выберите **«Показать на панели инспектора памяти»** .
    
    ![Показать на панели инспектора памяти](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/reveal-memory-inspector-c768cdcb79abf.png?hl=ru)
    

### Осмотрите несколько объектов

1.  Вы также можете проверить [DataView](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/DataView) или [TypedArray](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/TypedArray) . Например, `b2` — это `TypedArray` . Чтобы проверить это, щелкните правой кнопкой мыши свойство `b2` и выберите **«Показать на панели инспектора памяти»** (значка для `TypedArray` или `DataView` пока нет).
2.  В **Инспекторе памяти** откроется новая вкладка. Обратите внимание, что вы можете проверять несколько объектов одновременно. ![Новая вкладка в инспекторе памяти.](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/new-tab-the-memory-inspe-a4d6eda41779c.png?hl=ru)

## Инспектор памяти

![Инспектор памяти](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/the-memory-inspector-70f7e3e68c1c9.jpg?hl=ru)

**Инспектор памяти** состоит из 3 основных областей:

### Панель навигации

![Панель навигации](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/navigation-bar-7c8f5070b8dac.jpg?hl=ru)

1.  **Ввод адреса** показывает текущий адрес байта в шестнадцатеричном формате. Вы можете ввести новое значение, чтобы перейти к новому месту в буфере памяти. Например, попробуйте ввести `0x00000008` .
2.  Буферы памяти могут быть длиннее страницы. Вместо прокрутки вы можете использовать **левую** и **правую** кнопку для навигации.
3.  Кнопки слева позволяют осуществлять навигацию **вперед/назад** .
4.  По умолчанию буфер автоматически обновляется при шаге. В противном случае кнопка **обновления** дает вам возможность обновить память и обновить ее содержимое.

### Буфер памяти

![Буфер памяти](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/memory-buffer-a7d31525c1a55.jpg?hl=ru)

1.  Слева **адрес** отображается в шестнадцатеричном формате.
2.  **Память** также отображается в шестнадцатеричном формате, где каждый байт разделен пробелом. Текущий выбранный байт выделяется. Вы можете нажать на байт или перемещаться с помощью клавиатуры (влево, вправо, вверх, вниз).
3.  **Представление памяти в формате ASCII** показано справа. Подсветка показывает значение, соответствующее выбранным битам в байте. Как и в случае с памятью, вы можете нажимать на байт или перемещаться с помощью клавиатуры (влево, вправо, вверх, вниз).

### Инспектор значений

![Инспектор значений](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/value-inspector-5c0c254c78f07.jpg?hl=ru)

1.  На верхней панели инструментов имеется кнопка для переключения между **прямым и прямым порядком байтов** и открытия **настроек** . Откройте **настройки** , чтобы выбрать, какие типы значений они хотят видеть по умолчанию в инспекторе. ![кнопка на панели инструментов](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/toolbar-button-54ea370aa3da2.png?hl=ru)
2.  В основной области отображаются все **интерпретации значений** в соответствии с **настройками** . По умолчанию показаны все.
3.  **Кодировка** кликабельна. Вы можете переключаться между dec, hex, Oct для целых чисел и sci, dec для чисел с плавающей запятой. ![Переключатель кодирования](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/encoding-switch-f6cf904c7c193.png?hl=ru)

## Проверка памяти

Давайте вместе проверим память.

1.  Выполните следующие действия, чтобы [начать](https://developer.chrome.com/docs/devtools/memory-inspector?hl=ru#open-debug) отладку.
2.  Измените адрес на `0x00000027` во **входном адресе** . ![ввод адреса](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/address-input-418b7229e3036.png?hl=ru)
3.  Обратите внимание **на представление ASCII** и **интерпретацию значений** . На данный момент все значения пусты.
4.  Обратите внимание на синюю кнопку **Перейти к адресу** рядом с `Pointer 32-bit` и `Pointer 64-bit` . Вы можете нажать на нее, чтобы перейти по адресу. Кнопки неактивны и недоступны для нажатия, если адреса недействительны. ![Кнопка перехода к адресу](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/jump-address-button-d67529b88b035.png?hl=ru)
5.  Нажмите **«Возобновить выполнение сценария»** , чтобы выполнить код. ![Возобновить выполнение скрипта](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/resume-script-execution-335bab3a6b807.png?hl=ru)
6.  Обратите внимание **, что представление ASCII** теперь обновлено. Все **интерпретации значений** также обновляются. ![Все интерпретации значений обновлены.](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/all-value-interpretations-7031b3861113f.png?hl=ru)
7.  Давайте настроим **инспектор значений** так, чтобы он отображал только **числа с плавающей запятой** . Нажмите кнопку **настроек** и отметьте только **Float 32-bit** и **Float 64-bit** . ![настройки для настройки инспектора значений](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/settings-customize-value-b0cab734b0874.png?hl=ru)
8.  Давайте изменим кодировку с `dec` на `sci` . Обратите внимание, что представления значений соответствующим образом обновляются. ![Измените кодировку.](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/change-encoding-6485e8149b9a6.png?hl=ru)
9.  Попробуйте перемещаться по буферу памяти с помощью клавиатуры или панели навигации. Повторите шаг 4, чтобы наблюдать за изменением значений.

## Проверка памяти WebAssembly

Объект `WebAssembly.Memory` представляет собой `ArrayBuffer` , содержащий необработанные байты памяти объекта. Панель **«Инспектор памяти»** позволяет проверять такие объекты в приложениях Wasm, написанных на C++.

Чтобы в полной мере воспользоваться преимуществами проверки `WebAssembly.Memory` :

-   Используйте Chrome 107 или более позднюю версию. Проверьте свою версию на `chrome://version/` .
-   Установите расширение [поддержки C/C++ DevTools (DWARF)](https://chrome.google.com/webstore/detail/cc%20%20-devtools-support-dwa/pdcpmagijalfljmkmjngeonclgbbannb?hl=ru) . Это плагин для отладки приложений C/C++ WebAssembly с использованием отладочной информации DWARF.

Чтобы проверить `WebAssembly.Memory` объекта:

1.  [Откройте DevTools](https://developer.chrome.com/docs/devtools/open?hl=ru) на [этой демонстрационной странице](https://memory-inspector.glitch.me/demo-cpp.html) .
2.  На панели **«Источники»** откройте `demo-cpp.cc` и [установите точку останова](https://developer.chrome.com/docs/devtools/javascript/breakpoints?hl=ru#loc) в функции `main()` в строке 15: `x[i] = n - i - 1;` .
3.  Перезагрузите страницу, чтобы запустить приложение. Отладчик приостанавливает работу в точке останова.
4.  На панели **«Отладчик»** разверните **«Область»** > **«Локальный»** .
5.  Нажмите кнопку ![Показать в инспекторе памяти.](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/reveal-memory-inspector-c77ee60001d05.png?hl=ru) значок рядом с массивом `x: int[10]` .
    
    Либо щелкните массив правой кнопкой мыши и выберите **«Показать на панели инспектора памяти»** .
    

![Массив x открыт в инспекторе памяти.](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/the-x-array-opened-memor-0d0231bd45de.png?hl=ru)

Чтобы прекратить выделение памяти объекта, на панели **«Инспектор памяти»** наведите указатель мыши на значок объекта и нажмите кнопку `x` .

![Перестаньте выделять память объекта.](https://developer.chrome.com/static/docs/devtools/memory-inspector/image/stop-highlighting-object-3b446e810ccbd.png?hl=ru)

Чтобы узнать больше, см.:

-   [Расширение инспектора памяти для отладки C/C++](https://developer.chrome.com/blog/memory-inspector-extended-cpp?hl=ru)
-   [Отладка WebAssembly современными инструментами](https://developer.chrome.com/blog/wasm-debugging-2020?hl=ru) .
