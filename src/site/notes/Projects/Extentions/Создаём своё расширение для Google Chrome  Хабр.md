---
{"dg-publish":true,"permalink":"/projects/extentions/sozdayom-svoyo-rasshirenie-dlya-google-chrome-habr/","tags":["расширение для chrome","разработка расширения chrome"]}
---


# Создаём своё расширение для Google Chrome / Хабр

> ## Excerpt
> На хабре уже есть несколько статей о создании расширений для хрома, поделюсь своим опытом, затронув основные вещи и места, в которых у меня возникли трудности. Ч...

---
На хабре уже есть несколько статей о создании расширений для хрома, поделюсь своим опытом, затронув основные вещи и места, в которых у меня возникли трудности.  
Что понадобится для создания расширения в двух словах:  
1) Базовые знания Javascript  
2) Базовые знания HTML  
3) 5$

Покажу создание расширения для хрома на примере своего, созданного для подсчета «потерянного времени» в интернете. То есть это расширение считает время, проведенное на сайтах с возможностью определения посещенных сайтов по категориям: полезное время, либо потерянное время.  
  
Итак, я начинаю создание расширения с создания папки самого расширения, в которую будем класть все создаваемые нами файлы. Назову её «losttime». Далее, я создаю файл manifest.json, выглядит он следующим образом:

**manifest.json**

```
 {
  "manifest_version": 2,
  "name": "Lost Time",
  "version": "1.0",
  
  "icons": {
    "128": ""
  },
  "content_scripts": [
    {
      "matches": [ "*://*/*" ],
      "js": [ "content.js" ]
    }
  ],
  "background": {
    "scripts": ["background.js"]
  },
  "permissions": [
    "http://losttime.su/*"
  ],

      "browser_action": {
        "default_title": "LostTime",
        "default_icon": "",
        "default_popup": "popup.html"
    }

}
```

Некоторые из строк должны быть интуитивно понятны, но что обязательно нужно знать:  
— Значение manifest\_version должно быть обязательно «2»;  
— В content\_scripts пишем, какой скрипт будет запускаться на всех страницах отдельно;  
— В background пишем общий скрипт(фоновый скрипт), который запускается при запуске браузера;  
— В permissions пишем адрес сайта, с которого будет браться информация.

Все, что буду использовать я, не обязательно использовать Вам, если вам это по логике просто не нужно. [Подробнее о манифесте](https://developer.chrome.com/extensions/manifest.html).

То самое окошко, которое Вы можете видеть по клику на иконку расширения — это страница: popup.html.

![](https://habrastorage.org/r/w780q1/getpro/habr/post_images/2eb/942/02a/2eb94202ab82e4302d71541baf336348.jpg)

Она у меня выглядит следующим образом:

**popup.html**

```
&lt;!doctype html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;title&gt;Потерянное время LostTime&lt;/title&gt;
    &lt;script src="jquery.js" type="text/javascript"&gt;&lt;/script&gt; &lt;!-- Подключаю jquery --&gt;
&lt;link href="css.css" rel="stylesheet" type="text/css"/&gt;&lt;!-- Подключаю стили--&gt;
  &lt;/head&gt;
  &lt;body&gt;
  &lt;div id="options"&gt;&lt;!-- меню --&gt;
&lt;a  href="/popup.html"&gt;&lt;img class='img' src="" Title = "Короткая статистика за сегодня"&gt;&lt;/a&gt;
&lt;a href="/options.html"&gt;&lt;img class='img' src="images/options.png" Title="Настройки программы"&gt;&lt;/a&gt;
&lt;a href="/stat.html"&gt;&lt;img class='img' src="images/stat.png" Title="Подробная статистика о посещаемости"&gt;&lt;/a&gt;
&lt;/div&gt;
&lt;div id="dannie"&gt;&lt;/div&gt; &lt;!-- в этот блок буду загружать данные, которые будут показываться пользователю--&gt;
    &lt;script src="popup.js"&gt;&lt;/script&gt;&lt;!-- скрипт, выполняющийся при нажатии на иконку расширения--&gt;
  &lt;/body&gt;
&lt;/html&gt;
```

Чтобы было понятнее, описание кода вставил в самом HTML. Меню я организую просто: на картинку ставлю внутреннюю ссылку расширения.

Раз уж начал про popup.html, то расскажу сразу и о popup.js

Выглядит он у меня весьма просто:

**popup.js**

```
<span>var</span> <span>xhr</span> <span>=</span> <span>new</span> <span>XMLHttpRequest</span>();<br><span>xhr</span>.<span>open</span>(<span>"GET"</span>, <span>"http://losttime.su/?tmpl=login&amp;token="</span><span>+</span><span>localStorage</span>[<span>'lostlogin'</span>], <span>true</span>); <span>// тут происходит ГЕТ запрос на указанную страницу</span><br><span>xhr</span>.<span>onreadystatechange</span> <span>=</span> <span>function</span>() {<br>  <span>if</span> (<span>xhr</span>.<span>readyState</span> <span>==</span> <span>4</span>) <span>// если всё прошло хорошо, выполняем, что в скобках</span><br>  {<br><span>var</span> <span>dannie</span> <span>=</span> <span>document</span>.<span>getElementById</span>(<span>'dannie'</span>);<br><span>dannie</span>.<span>innerHTML</span> <span>=</span> <span>xhr</span>.<span>responseText</span>; <span>// добавляем в блок с id=dannie  полученный код</span><br>  }<br>}<br><span>xhr</span>.<span>send</span>();<br>
```

Описание кода также вставил.

Именно описанная выше конструкция позволяет вытащить и вывести содержание с Вашего, а может и не с Вашего сайта. Но, что важно знать:  
— В файле манифеста обязательно в поле permissions пишем адрес сайта, с которого будет браться информация.  
— Файл popup.js связан с фоновым скриптом background.js, т.к. данные, занесенные в локальное хранилище на background.js, видны и на popup.js.

Перед тем, как рассмотреть файл фонового скрипта background.js, рассмотрим файл скрипта, который запускается на каждой странице отдельно: content.js

У меня он выглядит так:

**content.js**

```
<span>function</span> <span>onBlur</span>() { <span>// окно теряет фокус</span><br><span>chrome</span>.<span>runtime</span>.<span>sendMessage</span>({<span>site</span>:<span>sait</span>,<span>time</span>:<span>localStorage</span>[<span>sait</span>]}); <span>// отправка сообщения на background.js</span><br><span>localStorage</span>[<span>sait</span>] <span>=</span> <span>'0'</span>;<br>}<br>    <span>window</span>.<span>onblur</span> <span>=</span> <span>onBlur</span>; <span>// если окно теряет фокус</span><br><span>function</span> <span>sec</span>() <span>//выполняется каждую секунду</span><br>{ <br>  <span>if</span>(<span>document</span>.<span>webkitVisibilityState</span> <span>==</span> <span>'visible'</span>)<span>//если страница активна</span><br>    {<br>   <span>localStorage</span>[<span>sait</span>] <span>=</span>  <span>parseInt</span>(<span>localStorage</span>[<span>sait</span>],<span>10</span>) <span>+</span><span>1</span>; <span>// обновляем данные о сайте в локальном хранилище</span><br>    }<br>} <br><span>var</span> <span>sait</span><span>=</span><span>location</span>.<span>hostname</span>; <span>// на каком сайте находится скрипт</span><br><span>localStorage</span>[<span>sait</span>] <span>=</span> <span>'0'</span>;<br><span>setInterval</span>(<span>sec</span>, <span>1000</span>);<span>// запускать функцию каждую секунду</span><br><br>
```

Наиболее интересный момент из моего скрипта, я считаю, должен быть:  
`chrome.runtime.sendMessage({site:sait,time:localStorage[sait]});`  
Тут происходит отправка сообщения background скрипту, а именно две переменные: site:sait — содержит адрес сайта, на котором скрипт  
time:localStorage\[sait\] — количество времени, проведенное на этом скрипте.

Далее, рассмотрим фоновый скрипт background.js, где и происходит приём данных, а точнее рассмотрим саму функцию приёма данных.

**background.js**

```
<span>chrome</span>.<span>runtime</span>.<span>onMessage</span>.<span>addListener</span>(<br>  <span>function</span>(<span>request</span>, <span>sender</span>, <span>sendResponse</span>) {<br><span>var</span> <span>a</span> <span>=</span> <span>request</span>.<span>site</span>; <span>// данные о сайте</span><br><span>var</span> <span>b</span> <span>=</span> <span>request</span>.<span>time</span>; <span>// данные о проведенном времени</span><br><span>// тут делаем с этими данными что хотим.</span><br>  });<br>
```

Вот, собственно, и она. Разбирать подробно ничего не стану, т.к. это в принципе и не нужно. Достаточно знать наглядный пример, чтобы осуществить задуманное. Если в скрипте background.js добавить какие-либо данные в локальное хранилище( а также куки, web sql), то эти же данные можно будет использовать и в popup.js скрипте.

Вот собственно всё, что я хотел поведать о создании расширения, но я затрону еще один момент, в котором у меня возникли трудности.

На странице настроек мне необходимо было организовать перетаскивание сайтов в разные колонки.

![](https://habrastorage.org/r/w780q1/getpro/habr/post_images/6e3/132/f21/6e3132f2190d273419e1eda223d09277.jpg)

Т.к. данные вставляются посредством InnerHtml, то данная возможность просто так не появится. Вот, что пришлось организовать:

```
<span>$</span>(<span>'#dannie'</span>).<span>on</span>(<span>'mouseover'</span>, <span>'.sait'</span>, <span>function</span>( ) {<br><span>$</span>(<span>this</span>).<span>css</span>({'border':<span>'3px solid #ffffff'</span>});<br>});<br><span>$</span>(<span>'#dannie'</span>).<span>on</span>(<span>'mouseout'</span>, <span>'.sait'</span>, <span>function</span>( ) {<br><span>$</span>(<span>this</span>).<span>css</span>({'border':<span>'3px solid black'</span>});<br>});<br><span>$</span>(<span>'#dannie'</span>).<span>on</span>(<span>'mousedown'</span>, <span>'.sait'</span>, <span>function</span>( ) {<br><span>$</span>(<span>this</span>).<span>css</span>({'border':<span>'3px solid black'</span>});<br>});<br><br><span>$</span>(<span>'#dannie'</span>).<span>on</span>(<span>'mouseover'</span>, <span>'.sait'</span>, <span>function</span>( ) {<br>  <span>$</span>(<span>'.sait'</span>).<span>draggable</span>({ <br><span>helper</span>:<span>'clone'</span><br>});  <br>});<br>
```

вместо привычного:

```
<span>$</span>(<span>'.sait'</span>).<span>mouseover</span>(<span>function</span>(){<br><span>$</span>(<span>'#'</span><span>+</span><span>this</span>.<span>id</span>).<span>css</span>({'border':<span>'3px solid #ffffff'</span>});<br>});<br><span>$</span>(<span>'.sait'</span>).<span>mouseout</span>(<span>function</span>(){<br><span>$</span>(<span>'#'</span><span>+</span><span>this</span>.<span>id</span>).<span>css</span>({'border':<span>'3px solid black'</span>});<br>});<br><span>$</span>(<span>'.sait'</span>).<span>mousedown</span>(<span>function</span>(){<br><span>$</span>(<span>'#'</span><span>+</span><span>this</span>.<span>id</span>).<span>css</span>({'border':<span>'0px solid black'</span>});<br>});<br><span>$</span>(<span>'.sait'</span>).<span>draggable</span>(<br>{ <br><span>helper</span>:<span>'clone'</span>,<br>});<br>
```

Думаю, объяснять не нужно. Почитать подробнее можете по [ссылке](http://jquery.page2page.ru/index.php5/On)

**Тестирование расширения**

Заходим в Настройки — Инструменты — Расширения, жмем на «Загрузить распакованное расширение»

**Публикация расширения**  
Заходим на [страницу](https://chrome.google.com/webstore/developer/dashboard?authuser=1) оплачиваем 5$, публикуем.  
Я не останавливаюсь на моментах, с которыми у меня не возникли трудности. А трудности возникли при оплате карточкой:  
— В моём случае должен быть подключен 3д пароль.  
Если Вам при оплате пишет ошибку, звоните своему банку и узнавайте. Мне за минуту помогли и всё гуд.

**Источники:**  
[Документация](https://developer.chrome.com/extensions/overview.html)  
[Об отправке сообщений](http://developer.chrome.com/apps/app_lifecycle.html)  
[О манифесте](https://developer.chrome.com/extensions/manifest.html)  
[Форум javascript](http://javascript.ru/forum/)

А также само [расиширние![](https://habrastorage.org/r/w1560/getpro/habr/post_images/ae7/da0/daa/ae7da0daa725de6cef3e2773912d18a5.png)](https://chrome.google.com/webstore/detail/lost-time/hnndadmkdppcpfbnabmpngoebedefokh).

Спасибо за прочтение. Всем удачи.
