---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/obzor-css-opredelenie-potenczialnyh-uluchshenij-css-chrome-dev-tools-chrome-for-developers/"}
---


# Обзор CSS: определение потенциальных улучшений CSS  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Определите потенциальные улучшения CSS с помощью панели «Обзор CSS».

---
<iframe frameborder="0" allowfullscreen="" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" title="Identify potential CSS improvements with the CSS Overview panel #DevToolsTips" width="640" height="360" src="https://www.youtube.com/embed/OAP_Sr0zb5I?origin=https%3A%2F%2Fdeveloper.chrome.com&amp;autoplay&amp;controls&amp;embed_domain&amp;enablejsapi=1&amp;end&amp;hl&amp;showinfo&amp;start&amp;video-id=OAP_Sr0zb5I&amp;widgetid=1" id="widget2" data-gtm-yt-inspected-100007133_93="true" data-gtm-yt-inspected-183356566_95="true"></iframe>

Используйте панель **«Обзор CSS»** , чтобы лучше понять CSS вашей страницы и выявить потенциальные улучшения.

## Обзор

Панель **обзора CSS** создает отчет о статистике CSS вашего сайта. В этом отчете собраны данные обо всех вхождениях CSS и даже о неиспользуемых объявлениях. Панель **обзора CSS** помогает вам дополнительно исследовать случаи с помощью выделения страниц или прямой ссылки на затронутый код на панели **«Элементы»** .

Узнайте, как [запустить и повторно запустить отчет «Обзор CSS»](https://developer.chrome.com/docs/devtools/css-overview?hl=ru#run) , а также [ознакомьтесь с отчетом «Обзор CSS»](https://developer.chrome.com/docs/devtools/css-overview?hl=ru#report) .

## Откройте панель «Обзор CSS».

1.  Откройте любую веб-страницу, например [эту страницу](https://developer.chrome.com/discover?hl=ru) .
2.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
3.  Выбирать ![Более.](https://developer.chrome.com/static/docs/devtools/css-overview/image/more-08bc5a2f624ac.svg?hl=ru) **Настраивайте и контролируйте DevTools** > **Дополнительные инструменты** > **Обзор CSS** .
    
    ![Обзор CSS в меню.](https://developer.chrome.com/static/docs/devtools/css-overview/image/css-overview-the-menu-f3ef2aaf18e75.png?hl=ru)
    
    Либо используйте [меню команд](https://developer.chrome.com/docs/devtools/command-menu?hl=ru) , чтобы открыть панель **«Обзор CSS»** .
    
    ![Команда «Показать обзор CSS» в меню «Команды».](https://developer.chrome.com/static/docs/devtools/css-overview/image/show-css-overview-command-9e250260adc21.png?hl=ru)
    

## Запуск и повторный запуск отчета «Обзор CSS»

1.  Нажмите кнопку **«Захватить обзор»** , чтобы создать отчет «Обзор CSS» вашей страницы.
    
    ![Захват обзора CSS.](https://developer.chrome.com/static/docs/devtools/css-overview/image/capture-css-overview-8e5987ade03eb.png?hl=ru)
    
2.  Чтобы повторно запустить обзор CSS, нажмите кнопку ![Прозрачный.](https://developer.chrome.com/static/docs/devtools/css-overview/image/clear-5dab063f188a2.svg?hl=ru) **Очистите значок обзора** и повторите первый шаг.
    
    ![Четкий обзор.](https://developer.chrome.com/static/docs/devtools/css-overview/image/clear-overview-9027a6591e697.png?hl=ru)
    

## Понимание отчета «Обзор CSS»

Отчет состоит из пяти разделов:

1.  **Краткое описание обзора** . Общее описание CSS вашей страницы. ![Краткое описание.](https://developer.chrome.com/static/docs/devtools/css-overview/image/overview-summary-0926d3de96f52.png?hl=ru)
2.  **Цвета** . Все цвета на вашей странице. Цвета сгруппированы по типам, таким как цвета фона, цвета текста и т. д. В этом разделе также показаны тексты с проблемами низкой контрастности.
    
    ![Цвета.](https://developer.chrome.com/static/docs/devtools/css-overview/image/colors-4e9bcaf388448.png?hl=ru)
    
    Каждый цвет кликабельен. Например, предположим, что цвет границы `#DADCE0` не соответствует цветовой схеме вашего сайта. Чтобы получить список элементов, использующих этот цвет, щелкните цвет.
    
    ![Список элементов, использующих этот цвет.](https://developer.chrome.com/static/docs/devtools/css-overview/image/a-list-elements-use-co-366529686af6a.png?hl=ru)
    
    Чтобы выделить элемент на странице, наведите курсор на элемент в списке.
    
    ![Наведите указатель мыши на элемент, чтобы выделить его на странице.](https://developer.chrome.com/static/docs/devtools/css-overview/image/hover-an-element-highli-a3fbd448a6a28.png?hl=ru)
    
    Чтобы открыть элемент на панели **«Элементы»** , щелкните элемент в списке.
    
3.  **Информация о шрифте** . Все шрифты на вашей странице и их появление, сгруппированные по разным размерам, толщине шрифта и высоте строки. Как и в разделе **«Цвета»** , чтобы просмотреть список затронутых элементов, щелкните их вхождения.
    
    ![Информация о шрифте.](https://developer.chrome.com/static/docs/devtools/css-overview/image/font-info-5325e4e179895.png?hl=ru)
    
4.  **Неиспользуемые объявления** . Все стили, не имеющие эффекта, сгруппированы по причине.
    
    ![Неиспользуемые объявления.](https://developer.chrome.com/static/docs/devtools/css-overview/image/unused-declarations-ea01b8bc72572.png?hl=ru)
    
    Например, два приведенных выше объявления не используются, поскольку содержимое определяет высоту и ширину встроенного элемента. Чтобы просмотреть соответствующие элементы, щелкните вхождения.
    
5.  **Медиа запросы** . Все медиа-запросы, определенные на вашей странице, отсортированы по количеству вхождений в порядке убывания. Чтобы просмотреть список затронутых элементов, щелкните их вхождения.
    
    ![Медиа запросы.](https://developer.chrome.com/static/docs/devtools/css-overview/image/media-queries-4d2a940ed77e7.png?hl=ru)
