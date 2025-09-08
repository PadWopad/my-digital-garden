---
{"dg-publish":true,"created":"2025-01-31T17:56:26 (UTC +03:00)","tags":[],"source":"https://developer.chrome.com/docs/devtools/css?hl=ru","author":"Kayce Basques","permalink":"/proekty/extentions/dev-tools/css-editing/","dgPassFrontmatter":true}
---


# Просмотр и изменение CSS  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Узнайте, как использовать Chrome DevTools для просмотра и изменения CSS страницы.

---

Измените мою маржу!

2.  Чтобы увидеть **блочную модель** , нажмите кнопку ![Показать боковую панель.](https://developer.chrome.com/static/docs/devtools/css/image/show-sidebar-bf915ed20021b.png?hl=ru) **Показывать кнопку боковой панели** на панели действий на вкладке **«Стили»** .
    
3.  На диаграмме **«Блоковая модель»** на вкладке **«Стили»** наведите указатель мыши на **отступы** . Заполнение элемента выделяется в окне просмотра. ![Заполнение элемента.](https://developer.chrome.com/static/docs/devtools/css/image/elements-padding-42cdfef833fcf.png?hl=ru)
    
4.  Дважды щелкните левое поле в **блочной модели** . В настоящее время элемент не имеет полей, поэтому `margin-left` имеет значение `-` .
    
5.  Введите `100` и нажмите Enter . ![Изменение левого поля элемента.](https://developer.chrome.com/static/docs/devtools/css/image/changing-elements-left-7aa96916ac40d.png?hl=ru)

В **блочной модели** по умолчанию используются пиксели, но она также принимает и другие значения, например `25%` или `10vw` . 