---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/animations-debugging-css-effects/"}
---


# Анимации: проверка и изменение эффектов анимации CSS.  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Просматривайте и изменяйте анимацию с помощью панели «Анимация».

---

1.  [Откройте DevTools](https://developer.chrome.com/docs/devtools/open?hl=ru) и проверьте страницу, на которой использовался API View Transitions. Например, эта [демо-страница](https://simple-set-demos.glitch.me/) .
2.  В разделе **«Анимация»** **нажмите** .
3.  На странице вызовите анимацию. Панель **«Анимация»** захватывает его и сразу же приостанавливает. Теперь вы можете найти структуру `::view-transition` в DOM поверх элемента `<head>` .
    
    ![Редактирование CSS псевдоэлемента ::view-transition.](https://developer.chrome.com/static/docs/devtools/css/animations/image/view-transition-edit.png?hl=ru)
    
4.  В разделе **«Элементы»** > **«Стили»** измените CSS псевдоэлементов `::view-transition` .
    
5.  **Возобновите** анимацию и **воспроизведите** ее, чтобы увидеть результат.
    

Дополнительные сведения см. в [разделе Плавные и простые переходы с помощью API View Transitions](https://developer.chrome.com/docs/web-platform/view-transitions?hl=ru) . 