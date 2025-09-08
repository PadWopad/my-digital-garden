---
{"dg-publish":true,"created":"2025-01-31T16:45:29 (UTC +03:00)","tags":["google chrome extensions","javascript"],"source":"https://habr.com/ru/articles/165073/","author":"bozheville","permalink":"/proekty/extentions/pishem-rasshirenie-dlya-google-chrome-habr/","dgPassFrontmatter":true}
---


# Пишем расширение для google chrome / Хабр

> ## Excerpt
> Написать расширение для google chrome несложно. Но при написании первого раширения могут возникнуть (и возникают) вопросы. Большинство мануалов по написанию перв...

---
Написать расширение для google chrome несложно. Но при написании первого раширения могут возникнуть (и возникают) вопросы. Большинство мануалов по написанию первого расширения расчитаны на использования манифеста первой версии, поддержка которого в скором будущем прекратится.

В этой статье будет рассмотрено:

-   Как составлять манифест v.2
-   Как работать с удаленными ресурсами
-   Как работать с cookies
-   Как работать с local storage
-   Как работать с уведомлениями

  

#### Введение

К концу статьи у нас будет готово расширение-органайзер, в котором будет поле для добавления новой задачи, а так же список задач на текущий день. Обозначим все требования к органайзеру:

-   Должен иметь поле для добавления события (дата, время, событие)
-   Должен отображать все задачи на текущий день, отсортированные по времени
-   Все прошедшие события должен отображать зачеркнутыми
-   Должен иметь поле для ввода времени, за сколько надо показывать уведомление, а так же чекбокс разрешающий и запрещающий показывать уведомления
-   За указанное время до события должен отображать уведомление о приближающемся событии

  

#### Манифест

Начнем создавать расширение с самого начала, то есть с манифеста. Манифест – это тот самый файл, в котром прописываются все параметры расширения. Название, описание, версия, разрешение на доступ к сайтам, разрешение на использование кук, уведомлений, локального хранилища. В общем, манифест – это мозг расширения. Создаем файл manifest.json. Манифест – единственный файл, который должен иметь заранее предопределенное имя, все остальные файлы можно будет называть как угодно. В этом файле есть три обязательных поля:

**manifest.json**

```
{<br><span>“name”</span>:  <span>“Organizer</span> <span>extension”</span>,  <span>// Название расширения</span><br><span>“version”</span>: <span>“1</span><span>.0</span><span>”</span>,  <span>// Версия расширения.</span><br><span>“manifest_version”</span>: <span>2</span> <span>// Версия манифеста</span><br>}<br>
```

Тут есть пара правил:

-   Версия **манифеста** должна быть целочисленной, то есть должна писаться как 2, а не “2”.
-   Версия **расширения** должна быть строковой, но содержать только числа и точки, то есть “1.0” — хорошо, а 1.0 и “0.9 beta” — плохо.

С обязательными полями – все, перейдем к созданию всплывающего окна расширения. Для того, чтобы по нажатию на пиктограмму, открывалось окно, необходимо добавить в манифест поле “browser\_action”

**manifest.json**

```
{<br><span>…</span><br><span>"browser_action"</span>: {<br><span>"default_title"</span>: <span>"Open organizer"</span>, <span>// Заголовок. Его видно если навести курсор на иконку в браузере</span><br><span>"default_icon"</span>: <span>"icon_small.png"</span>, <span>// Путь к иконке расширения</span><br><span>"default_popup"</span>: <span>"popup.html"</span> <span>// Путь к странице с попапом</span><br>}<br>}<br>
```

Теперь создадим всплывающее окно. Это обычная html страница, которая может быть любого размера и цвета, никаких фокусов. Назовем файл “popup.html”. Создать этот файл мало – его надо указать в манифесте. Так мы и сделали: «default\_popup»: «popup.html».

**popup.html**

```
&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;title&gt;&lt;/title&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8"&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div&gt;It&nbsp;works!&lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;
```

  

#### Добавление расширения в браузер

Теперь пришло время проверить работоспособность нашего расширния. Для этого загрузим расширение в браузер. Открываем в хроме меню расширений. Ставим птицу на “Developer mode”.  
![](https://habrastorage.org/r/w1560/storage2/35b/309/bfd/35b309bfd62a78ac7c79ba8b9ff1f6f0.png)  
После этого появятся три кнопки. Нажимаем “Load unpacked extension...”. Выбираем папку с файлами расширения. После этого появится наше расширение. Если все правильно, то по нажатию на иконку – повится окно:  
![](https://habrastorage.org/r/w1560/storage2/05b/58a/369/05b58a3693b4df06238bac9dec09ceb3.png)

#### Подключение скриптов

Теперь можно приступить к интересному. Подключим два javascript файла. Первый – popup.js, второй – jquery. С первым проблем не возникнет, но jquery будем подключать не локальный, а удаленный, взятый по адресу [ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js](https://ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js). Проблемы возникнут от того, что по умолчанию расширение не имеет доступа к сторонним ресурсам. Чтобы получить доступ, надо его указать в манифесте. Доступ к чему-либо указывается в поле “permissions”. Так же, для удаленных скриптов и css надо указывать доступные удаленные ресурсы.

**manifest.json**

```
{<br><span>…</span><br><span>"permissions"</span>: [<br><span>"https://ajax.googleapis.com/*"</span><br>],<br><span>"content_security_policy"</span>: <span>"script-src 'self' https://ajax.googleapis.com; object-src 'self'"</span><br>}<br>
```

Теперь подключим эти скрипты в popup.html

**popup.html**

```
&lt;script src="https://ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js"&gt;&lt;/script&gt;
&lt;script src="popup.js"&gt;&lt;/script&gt;
```

  

#### Storage

При помощи storage в хроме можно хранить пользовательские данные. И именно в storage наше расширение и будет хранить грядущие события. На то есть две причины. Во-первых, данные, хранищиеся в storage можно синхронизировать, если залогиниться в браузере. А во-вторых, данные можно хранить не только в виде строки, как в cookies, а в любом виде, то есть можно хранить и массивы и объекты. Чтобы это заработало, откроем доступ к storage в манифесте.

**manifest.json**

```
{<br><span>...</span><br><span>"permissions"</span>: [<br>  <span>…</span><br>  <span>"storage"</span><br>]<br><span>...</span><br>}<br>
```

Теперь переделаем всплавающее окно. Во всплывающем окне будет поле с сегодняшней датой, три инпута для даты, времени и описания нового события, кнопка для добавления нового события, а так же список всех событий на сегодня.

**popup.html**

```
&lt;div id="container"&gt;
  &lt;div id="today_date"&gt;Date&lt;/div&gt;
  &lt;table class="table"&gt;
    &lt;tr&gt;
      &lt;td&gt;Дата&lt;/td&gt;
      &lt;td&gt;Время&lt;/td&gt;
      &lt;td&gt;Задача&lt;/td&gt;
    &lt;/tr&gt;
    &lt;tr&gt;
      &lt;td&gt;&lt;input type="text" id="new_date" value="" class="input_date" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;input type="text" id="new_time" value="" class="input_date" /&gt;&lt;/td&gt;
      &lt;td&gt;&lt;input type="text" id="new_task" value="" class="input_task" /&gt;&lt;/td&gt;
    &lt;/tr&gt;
  &lt;/table&gt;
  &lt;ul&gt;&lt;/ul&gt;
&lt;/div&gt;
```

И сразу же добавим отображение даты в блоке #today\_date.

**popup.js**

```
<span>$</span>(<span>function</span>(){<br>  <span>var</span> <span>today</span> <span>=</span> <span>new</span> <span>Date</span>();<br>  <span>$</span>(<span>"#today_date"</span>).<span>html</span>(<span>today</span>.<span>getDate</span>()<span>+</span><span>"."</span><span>+</span>(<span>parseInt</span>(<span>today</span>.<span>getMonth</span>())<span>+</span><span>1</span>)<span>+</span><span>"."</span> <span>+</span> <span>today</span>.<span>getFullYear</span>());<br>}<br>
```

Выглядеть должно так:  
![](https://habrastorage.org/r/w1560/storage2/a4c/d15/c0c/a4cd15c0c5746b9c5907c7a5566a5a6f.png)

Итак, при нажатии на кнопку “+” у нас должно добавляться событие. Вначале файла объявим глобальную переменную storage – объект для работы с storage, а так же глобальный массив tasks для хранения событий.

**popup.js**

```
<span>var</span> <span>storage</span> <span>=</span> <span>chrome</span>.<span>storage</span>.<span>sync</span>;<br><span>var</span> <span>tasks</span> <span>=</span> <span>new</span> <span>Array</span>();<br><span>$</span>(<span>function</span>(){<br>  <span>…</span><br>  <span>$</span>(<span>"#add_task"</span>).<span>click</span>(<span>function</span>(){<br>    <span>var</span> <span>new_task</span> <span>=</span> <span>new</span> <span>Object</span>();<br>    <span>new_task</span>.<span>date</span> <span>=</span> <span>validateField</span>(<span>$</span>(<span>"#new_date"</span>).<span>val</span>(), <span>"date"</span>);<br>    <span>new_task</span>.<span>time</span> <span>=</span> <span>validateField</span>(<span>$</span>(<span>"#new_time"</span>).<span>val</span>(), <span>"time"</span>);<br>    <span>new_task</span>.<span>task</span> <span>=</span> <span>$</span>(<span>"#new_task"</span>).<span>val</span>();<br>    <span>if</span>(<span>!</span><span>new_task</span>.<span>task</span> <span>||</span> <span>!</span><span>new_task</span>.<span>date</span> <span>||</span> <span>!</span><span>new_task</span>.<span>task</span>){<br>       <span>return</span> <span>false</span>;<br>    }<br>    <span>tasks</span>[<span>tasks</span>.<span>length</span>] <span>=</span> <span>new_task</span>;<br>    <span>storage</span>.<span>set</span>({<br>      <span>tasks</span>:<span>tasks</span><br>    });<br>  });<br>});<br>
```

Функция валидации проверяет, что дата записана в формате d.m.yyyy, а время в формате hh:mm, а так же, что в описании события не меньше трех символов.

**popup.js**

```
<span>var</span> <span>validateField</span> <span>=</span> <span>function</span>(<span>val</span>, <span>type</span>){<br>    <span>if</span>(<span>type</span> <span>==</span> <span>"date"</span>){<br>        <span>var</span> <span>date</span> <span>=</span> <span>val</span>.<span>split</span>(<span>"."</span>);<br>        <span>var</span> <span>year</span> <span>=</span> <span>new</span> <span>Date</span>();<br>        <span>year</span> <span>=</span> <span>year</span>.<span>getFullYear</span>();<br>        <span>if</span>(<span>date</span>.<span>length</span> <span>==</span> <span>3</span> <span>&amp;&amp;</span> <span>parseInt</span>(<span>date</span>[<span>0</span>]) <span>==</span> <span>date</span>[<span>0</span>] <span>&amp;&amp;</span> <span>date</span>[<span>0</span>] <span>&lt;=</span> <span>31</span> <span>&amp;&amp;</span> <span>parseInt</span>(<span>date</span>[<span>1</span>]) <span>==</span> <span>date</span>[<span>1</span>] <span>&amp;&amp;</span> <span>date</span>[<span>1</span>] <span>&lt;=</span> <span>12</span> <span>&amp;&amp;</span> <span>parseInt</span>(<span>date</span>[<span>2</span>]) <span>==</span> <span>date</span>[<span>2</span>] <span>&amp;&amp;</span> <span>date</span>[<span>2</span>] <span>&gt;=</span> <span>year</span>){<span>return</span> <span>val</span>;}<br>    } <span>else</span> <span>if</span>(<span>type</span> <span>==</span> <span>"time"</span>){<br>        <span>var</span> <span>time</span> <span>=</span> <span>val</span>.<span>split</span>(<span>":"</span>);<br>        <span>if</span>(<span>time</span>.<span>length</span> <span>==</span> <span>2</span> <span>&amp;&amp;</span> <span>parseInt</span>(<span>time</span>[<span>0</span>]) <span>==</span> <span>time</span>[<span>0</span>] <span>&amp;&amp;</span> <span>time</span>[<span>0</span>] <span>&lt;</span> <span>24</span> <span>&amp;&amp;</span> <span>parseInt</span>(<span>time</span>[<span>1</span>]) <span>==</span> <span>time</span>[<span>1</span>] <span>&amp;&amp;</span> <span>time</span>[<span>1</span>] <span>&lt;</span> <span>60</span>){<span>return</span> <span>val</span>;}<br>    } <span>else</span> <span>if</span>(<span>type</span> <span>==</span> <span>"task"</span> <span>&amp;&amp;</span> <span>type</span>.<span>length</span> <span>&gt;=</span> <span>3</span>){<br>        <span>return</span> <span>val</span>;<br>    }<br>    <span>return</span> <span>null</span>;<br>}<br>
```

С добавлением разобрались, переходим к получению событий на сегодня. Для этого надо получить все события из базы, выбираем из всех только сегодняшние события и сортируем их по времени по возрастанию.

**popup.js**

```
<span>$</span>(<span>function</span>(){<br>  <span>…</span><br>  <span>var</span> <span>now_hours</span> <span>=</span> <span>today</span>.<span>getHours</span>() <span>&lt;</span> <span>10</span> <span>?</span> <span>"0"</span> <span>+</span> <span>today</span>.<span>getHours</span>() :  <span>today</span>.<span>getHours</span>();<br>    <span>var</span> <span>now_minutes</span> <span>=</span> <span>today</span>.<span>getMinutes</span>() <span>&lt;</span> <span>10</span> <span>?</span> <span>"0"</span> <span>+</span> <span>today</span>.<span>getMinutes</span>() : <span>today</span>.<span>getMinutes</span>();<br>    <span>var</span> <span>now_time</span> <span>=</span> <span>now_hours</span> <span>+</span> <span>""</span> <span>+</span> <span>now_minutes</span>;<br>    <span>storage</span>.<span>get</span>(<span>"tasks"</span>,<span>function</span>(<span>items</span>){<br>        <span>if</span>(<span>items</span>.<span>tasks</span>){<br>            <span>tasks</span> <span>=</span> <span>items</span>.<span>tasks</span>;<br>            <span>var</span> <span>today_tasks</span> <span>=</span> <span>getTodayTasks</span>(<span>tasks</span>);<br>            <span>if</span>(<span>today_tasks</span>.<span>length</span> <span>&gt;</span><span>0</span>){<br>                <span>for</span>(<span>var</span> <span>i</span> <span>in</span> <span>today_tasks</span>){<br>                    <span>var</span> <span>this_time</span> <span>=</span> <span>today_tasks</span>[<span>i</span>].<span>time</span>.<span>replace</span>(<span>":"</span>, <span>""</span>);<br>                    <span>var</span> <span>add</span> <span>=</span> <span>this_time</span> <span>&gt;</span> <span>now_time</span> <span>?</span> <span>""</span> : <span>' class="done"'</span>;<br>                    <span>var</span> <span>add_html</span> <span>=</span> <span>'&lt;li'</span><span>+</span><span>add</span><span>+</span><span>'&gt;&lt;strong&gt;'</span><span>+</span><span>today_tasks</span>[<span>i</span>].<span>time</span><span>+</span><span>'&lt;/strong&gt; '</span><span>+</span><span>today_tasks</span>[<span>i</span>].<span>task</span><span>+</span><span>'&lt;/li&gt;'</span>;<br>                    <span>$</span>(<span>"ul"</span>).<span>append</span>(<span>add_html</span>);<br>                }<br>            }<br>        }<br>    });<br>  <span>…</span><br>});<br>
```

Функция getTodayTasks() возвращает из общего списка только события с сегодняшней датой.

**popup.js**

```
<span>var</span> <span>getTodayTasks</span> <span>=</span> <span>function</span>(<span>tasks</span>){<br>    <span>var</span> <span>today_tasks</span> <span>=</span> <span>new</span> <span>Array</span>();<br>    <span>var</span> <span>today</span> <span>=</span> <span>new</span> <span>Date</span>();<br>    <span>var</span> <span>today_date</span> <span>=</span> <span>today</span>.<span>getDate</span>()<span>+</span><span>"."</span><span>+</span>(<span>today</span>.<span>getMonth</span>() <span>+</span> <span>1</span> )<span>+</span> <span>"."</span> <span>+</span> <span>today</span>.<span>getFullYear</span>();<br>    <span>for</span>(<span>var</span> <span>i</span> <span>in</span> <span>tasks</span>){<br>        <span>if</span>(<span>tasks</span>[<span>i</span>].<span>date</span> <span>==</span> <span>today_date</span>){<br>            <span>today_tasks</span>[<span>today_tasks</span>.<span>length</span>] <span>=</span> <span>tasks</span>[<span>i</span>];<br>        }<br>    }<br>    <span>if</span>(<span>today_tasks</span>.<span>length</span> <span>&gt;</span> <span>0</span>){<br>        <span>today_tasks</span> <span>=</span> <span>sortTasks</span>(<span>today_tasks</span>);<br>    }<br>    <span>return</span> <span>today_tasks</span>;<br>}<br>
```

Функция sortTasks() сортирует события по возрастанию времени.

**popup.js**

```
<span>var</span> <span>sortTasks</span> <span>=</span> <span>function</span>(<span>tasks</span>){<br>    <span>if</span>(<span>tasks</span>.<span>length</span> <span>&gt;</span> <span>0</span>){<br>        <span>var</span> <span>swapped</span> <span>=</span> <span>true</span>;<br>        <span>while</span> (<span>swapped</span>) {<br>            <span>swapped</span> <span>=</span> <span>false</span>;<br>            <span>for</span> (<span>var</span> <span>i</span><span>=</span><span>0</span>; <span>i</span> <span>&lt;</span> <span>tasks</span>.<span>length</span><span>-</span><span>1</span>; <span>i</span><span>++</span>) {<br>                <span>var</span> <span>this_time</span> <span>=</span> <span>tasks</span>[<span>i</span>].<span>time</span>.<span>replace</span>(<span>":"</span>, <span>""</span>);<br>                <span>var</span> <span>next_time</span> <span>=</span> <span>tasks</span>[<span>i</span><span>+</span><span>1</span>].<span>time</span>.<span>replace</span>(<span>":"</span>, <span>""</span>);<br>                <span>if</span> (<span>this_time</span> <span>&gt;</span> <span>next_time</span>) {<br>                    <span>var</span> <span>temp</span> <span>=</span> <span>tasks</span>[<span>i</span>];<br>                    <span>tasks</span>[<span>i</span>] <span>=</span> <span>tasks</span>[<span>i</span><span>+</span><span>1</span>];<br>                    <span>tasks</span>[<span>i</span><span>+</span><span>1</span>] <span>=</span> <span>temp</span>;<br>                    <span>swapped</span> <span>=</span> <span>true</span>;<br>                }<br>            }<br>        }<br>    }<br>    <span>return</span> <span>tasks</span>;<br>}<br>
```

  

#### Уведомления

Пришло время настроить отображение уведомлений на экране. Добавим во всплывающее окно специальный чекбокс. Если этот чекбокс будет отмечен – уведомлениея будут показываться, если не будет отмечен – не будут. Так же добавим текстовый инпут. Цифра в этом инпуте будет показывать, за какое время до событя будет показываться уведомление. То есть если у нас событие назначено на 19:00, в этом текстовом инпуте будет 5, значит в 18:55 появится уведомление. Добавим в popup.html код с этими инпутами

**popup.html**

```
&lt;div&gt;
  &lt;input type="checkbox" id="show_notifications" checked="checked" /&gt;
  &lt;input type="text" id="when_to_notify" class="input_date" value="" /&gt; 
  Показывать уведомления
&lt;/div&gt;
```

![](https://habrastorage.org/r/w1560/storage2/8b5/296/bda/8b5296bda37776a49ea91d9e4a6e046f.png)

Теперь давайте разберемся с тем, как это будет работать. При нажатии на чекбокс, будет проверяться его атрибут checked, значение атрибута будет записываться в cookie “show\_notifications”. Перейдем к текстовому инпуту. По изменению его значения, новое значение будет валидироваться, если оно целочисленное и не больше 120, записываем новое значение в cookie “when\_to\_notify”.

Но для того, чтобы у нас это заработало, надо открыть доступ к cookies. Для этого заходим в manifest.json и добавляем в “permissions”

**manifest.json**

```
{<br><span>...</span><br><span>"permissions"</span>: [<br><span>…</span><br><span>“cookies”</span><br>]<br><span>...</span><br>}<br>
```

Теперь можно приступать к скрипту. Заходим в popup.js. Для начала установим первоначальные значения в инпутах. По-умолчанию чекбокс не отмечен, то есть уведомления не показываются, а время равно 0. При клике на чекбокс, будет меняться значение cookie “show\_notifications”. При изменении значения в тектовом поле, будет меняться значение cookie “when\_to\_notify”.

**popup.js**

```
<span>$</span>(<span>function</span>(){<br>    <span>setCheckbox</span>();<br>    <span>setWhenToNotify</span>(<span>getCookie</span>(<span>"when_to_notify"</span>));<br>    <span>...</span><br>    <span>$</span>(<span>"#show_notifications"</span>).<span>click</span>(<span>function</span>(){<br>        <span>setCookie</span>(<span>"show_notifications"</span>, <span>document</span>.<span>getElementById</span>(<span>"show_notifications"</span>).<span>checked</span>);<br>    });<br>    <span>$</span>(<span>"#when_to_notify"</span>).<span>change</span>(<span>function</span>(){<br>        <span>setWhenToNotify</span>(<span>$</span>(<span>this</span>).<span>val</span>());<br>    });<br>});<br>
```

Рассмотрим подробнее функции. Начнем с функций работы с cookies. В данном случае были взяты готовые функции с w3schools.com.

**popup.js**

```
<span>var</span> <span>setCookie</span> <span>=</span> <span>function</span>(<span>c_name</span>,<span>value</span>,<span>exdays</span>){<br>    <span>/*</span><br><span>     *Взято с http://www.w3schools.com/js/js_cookies.asp</span><br><span>     */</span><br>    <span>var</span> <span>exdate</span><span>=</span><span>new</span> <span>Date</span>();<br>    <span>exdate</span>.<span>setDate</span>(<span>exdate</span>.<span>getDate</span>() <span>+</span> <span>exdays</span>);<br>    <span>var</span> <span>c_value</span><span>=</span><span>escape</span>(<span>value</span>) <span>+</span> ((<span>exdays</span><span>==</span><span>null</span>) <span>?</span> <span>""</span> : <span>"; expires="</span><span>+</span><span>exdate</span>.<span>toUTCString</span>());<br>    <span>document</span>.<span>cookie</span><span>=</span><span>c_name</span> <span>+</span> <span>"="</span> <span>+</span> <span>c_value</span>;<br>}<br><br><span>var</span> <span>getCookie</span> <span>=</span> <span>function</span>(<span>c_name</span>){<span>Позвонить</span> <span>Васе</span> <span>П</span>.<br>    <span>/*</span><br><span>     *Взято с http://www.w3schools.com/js/js_cookies.asp</span><br><span>     */</span><br>    <span>var</span> <span>i</span>,<span>x</span>,<span>y</span>,<span>ARRcookies</span><span>=</span><span>document</span>.<span>cookie</span>.<span>split</span>(<span>";"</span>);<br>    <span>for</span> (<span>i</span><span>=</span><span>0</span>;<span>i</span><span>&lt;</span><span>ARRcookies</span>.<span>length</span>;<span>i</span><span>++</span>){<br>        <span>x</span><span>=</span><span>ARRcookies</span>[<span>i</span>].<span>substr</span>(<span>0</span>,<span>ARRcookies</span>[<span>i</span>].<span>indexOf</span>(<span>"="</span>));<br>        <span>y</span><span>=</span><span>ARRcookies</span>[<span>i</span>].<span>substr</span>(<span>ARRcookies</span>[<span>i</span>].<span>indexOf</span>(<span>"="</span>)<span>+</span><span>1</span>);<br>        <span>x</span><span>=</span><span>x</span>.<span>replace</span>(<span>/^\s+|\s+$/g</span>,<span>""</span>);<br>        <span>if</span> (<span>x</span><span>==</span><span>c_name</span>){<br>            <span>return</span> <span>unescape</span>(<span>y</span>);<br>        }<br>    }<br>}<br>
```

Разберемся с функцией setCheckbox(). Она получает cookie “show\_notifications” и проверяет, если полученное значение равно “true”(текстовое, да), то параметр checked у чекбокса true, иначе false.

**popup.js**

```
<span>var</span> <span>setCheckbox</span> <span>=</span> <span>function</span>(){<br>    <span>var</span> <span>val</span> <span>=</span> <span>getCookie</span>(<span>"show_notifications"</span>)<br>    <span>document</span>.<span>getElementById</span>(<span>'show_notifications'</span>).<span>checked</span> <span>=</span> ((<span>val</span> <span>==</span> <span>"true"</span>) <span>?</span> <span>true</span> : <span>false</span>);<br>}<br>
```

Теперь рассмотрим setWhenToNotify(). Она принимает новое значение таймера. Если это значение – целочисленное и не больше 120 минут, то в cookie “when\_to\_notify” устанавливается новое значение. Если переменная не прошла эту валидацию, то в инпут возвращается предыдущее значение из cookies “when\_to\_notify”.

**popup.js**

```
<span>var</span> <span>setWhenToNotify</span> <span>=</span> <span>function</span>(<span>val</span>){<br>    <span>var</span> <span>last_val</span> <span>=</span> <span>getCookie</span>(<span>"when_to_notify"</span>);<br>    <span>last_val</span> <span>=</span> <span>last_val</span> <span>!=</span> <span>"undefined"</span><span>?</span> <span>last_val</span>: <span>0</span>;<br>    <span>val</span> <span>=</span> (<span>parseInt</span>(<span>val</span>)<span>==</span><span>val</span> <span>&amp;&amp;</span> <span>val</span> <span>&lt;=</span><span>120</span>) <span>?</span> <span>val</span> : <span>last_val</span>;<br>    <span>setCookie</span>(<span>"when_to_notify"</span>, <span>val</span>);<br>    <span>$</span>(<span>"#when_to_notify"</span>).<span>val</span>(<span>val</span>);<br>}<br>
```

Перейдем к самим уведомлениям. Для этого откроем доступ к уведомлениям и подключим фоновый background.js. Нужно подключить именно фоновый файл, так как если уведомления вызывать из popup.js, то уведомления будут появляться только если открыто всплывающее окно.

**manifest.json**

```
{<br><span>...</span><br><span>"permissions"</span>: [<br>    <span>…</span><br>    <span>"notifications"</span><br>    ],<br><span>"background"</span>: { <span>"scripts"</span>: [<span>"background.js"</span>] },<br><span>"web_accessible_resources"</span>: [<span>"icon_small.png"</span>],<br><span>...</span><br>}<br>
```

Последняя строчка дает доступ к удаленному файлу. Дело в том, что картинка, которая отображается в уведомлении обязательно должна быть доступна расширению удаленно. В данном случае файл локальный, но доступ открывать все равно надо. Теперь возьмемся за background.js. Объявим переменную storage и пустой массив tasks. Далее раз в минуту скрипт будет получать список сегодняшних событий и получать из них список задач, которые должны произойти через указанное время. После этого для каждой такой задачи будет показано уведомление.

**background.js**

```
<span>var</span> <span>storage</span> <span>=</span> <span>chrome</span>.<span>storage</span>.<span>sync</span>;<br><span>var</span> <span>tasks</span> <span>=</span> <span>new</span> <span>Array</span>();<br><span>setInterval</span>(<span>function</span>() {<br>    <span>storage</span>.<span>get</span>(<span>"tasks"</span>,<span>function</span>(<span>items</span>){<br>        <span>if</span>(<span>items</span>.<span>tasks</span> <span>&amp;&amp;</span> <span>getCookie</span>(<span>"show_notifications"</span>) <span>==</span> <span>"true"</span>){<br>            <span>tasks</span> <span>=</span> <span>getTodayTasks</span>(<span>items</span>.<span>tasks</span>);<br>            <span>if</span>(<span>window</span>.<span>webkitNotifications</span>){<br>                <span>var</span> <span>texts</span> <span>=</span> <span>getNextTask</span>(<span>tasks</span>);<br>                <span>for</span>(<span>var</span> <span>i</span> <span>in</span> <span>texts</span>){<br>                    <span>show</span>(<span>texts</span>[<span>i</span>]);    <br>                }<br>            }<br>        }<br>    });<br>}, <span>60000</span>);<br>
```

Функции getTodayTasks() и getCookie() взяты из popup.js. Так что начнем разбор с функции getNextTask(). Функция сравнивает текущее время и время события, если оно равно тому значению, которое хранится в cookie “when\_to\_notify”, то в массив next дописывается строка из времени события и его описания. После проверки всех событий возвращет массив next.

**background.js**

```
<span>var</span> <span>getNextTask</span> <span>=</span> <span>function</span>(<span>tasks</span>){<br>    <span>var</span> <span>now</span> <span>=</span> <span>new</span> <span>Date</span>();<br>    <span>now</span> <span>=</span> <span>now</span>.<span>getTime</span>();<br>    <span>var</span> <span>next</span> <span>=</span> <span>new</span> <span>Array</span>();<br>    <span>for</span>(<span>var</span> <span>i</span> <span>in</span> <span>tasks</span>){<br>        <span>var</span> <span>date</span> <span>=</span> <span>tasks</span>[<span>i</span>].<span>date</span>.<span>split</span>(<span>"."</span>);<br>        <span>var</span> <span>time</span> <span>=</span> <span>tasks</span>[<span>i</span>].<span>time</span>.<span>split</span>(<span>":"</span>);<br>        <span>var</span> <span>task_date</span> <span>=</span> <span>new</span> <span>Date</span>(<span>parseInt</span>(<span>date</span>[<span>2</span>]), <span>parseInt</span>(<span>date</span>[<span>1</span>]<span>-</span><span>1</span>), <span>parseInt</span>(<span>date</span>[<span>0</span>]), <span>parseInt</span>(<span>time</span>[<span>0</span>]), <span>parseInt</span>(<span>time</span>[<span>1</span>]), <span>0</span>, <span>0</span>);<br>        <span>task_date</span> <span>=</span> <span>task_date</span>.<span>getTime</span>();<br>        <span>var</span> <span>delta</span> <span>=</span> <span>Math</span>.<span>round</span>((<span>task_date</span><span>-</span><span>now</span>)<span>/</span><span>60000</span>);<br>        <span>if</span>(<span>delta</span> <span>==</span> <span>getCookie</span>(<span>"when_to_notify"</span>)){<br>            <span>next</span>[<span>next</span>.<span>length</span>] <span>=</span> <span>tasks</span>[<span>i</span>].<span>time</span> <span>+</span> <span>" - "</span> <span>+</span> <span>tasks</span>[<span>i</span>].<span>task</span>;<br>        }<br>    }<br>    <span>return</span> <span>next</span>;<br>}<br>
```

Функция show() показывает уведомление с заданным текстом.

**background.js**

```
<span>var</span> <span>show</span> <span>=</span> <span>function</span>(<span>text</span>) {<br>    <span>var</span> <span>notification</span> <span>=</span> <span>window</span>.<span>webkitNotifications</span>.<span>createNotification</span>(<span>'icon_small.png'</span>,<span>'Есть дело'</span>, <span>text</span>);<br>    <span>notification</span>.<span>show</span>();    <br>}<br>
```

Результатом работы этого скрипта будет такое вот уведомление:  
![](http://habrastorage.org/r/w1560/storage2/825/747/da5/825747da550fff1941be095b56b3a153.png)

#### Послесловие

Как и обещано, в конце статьи у нас есть готовое расширение-органайзер для Google Chrome.  
Теперь добавим расширение в Chrome Web Store. Загружать надо расширение, запакованное в .zip-архив. Для начала заходим в Web Store. Для этого заходим в хроме на вкладку “Приложения” и нажимаем кнопку “Web Strore”  
![](http://habrastorage.org/r/w1560/storage2/c3f/33d/f42/c3f33df426d34d5725fb5b961e27af95.png)  
Теперь заходим в меню. Для этого нажимаем шестиренку и открываем “Developer dashboard”  
![](http://habrastorage.org/r/w1560/storage2/fb8/0aa/7a9/fb80aa7a97e76062d243d284d00e0726.png)  
Нажимаем большую кнопку “Add new item”. После этого надо будет выбрать zip-архив с расширением нажать “upload”  
![](http://habrastorage.org/r/w1560/storage2/764/145/5cb/7641455cbdbf6e6424f115be50327e8d.png)  
Далее надо заполнить небольшую форму с описанием расширения. Теперь есть выбор либо сохранить расширение в черновил либо опубликовать. Просто так опубликовать его не получится так как регистрация в Web Store стоит 5 $. Плату за регистрацию надо платить один раз для аккаунта, а не для каждого расширения. После оплаты появляется позможность опубликовать расширение, но и тут надо быть готовым к тому, что его будут валидировать несколько дней.

#### Полезные ссылки

Описание полей манифеста: [developer.chrome.com/trunk/extensions/manifest.html](http://developer.chrome.com/trunk/extensions/manifest.html)  
Работа с storage: [developer.chrome.com/trunk/extensions/storage.html](http://developer.chrome.com/trunk/extensions/storage.html)  
Информация по уведомлениям: [developer.chrome.com/extensions/notifications.html](http://developer.chrome.com/extensions/notifications.html)  
Исходники расширения: [github.com/bozheville/orginaizer\_extension](https://github.com/bozheville/orginaizer_extension)
