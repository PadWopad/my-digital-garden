---
{"dg-publish":true,"permalink":"/projects/extentions/create-publish-extension-ai/","tags":["ai","learning","promptengineering","webdev","software","coding","development","engineering","inclusive","community"]}
---


# Как я создал и опубликовал расширение Chrome с помощью ИИ? - Сообщество DEV

> ## Excerpt
> In the beginning I was skeptical about the use of AI either to write articles or in coding. Because...

---
В начале я скептически относился к использованию ИИ как для написания статей, так и для кодирования. Потому что всякий раз, когда я использовал ИИ для создания статей, это было похоже на простое перефразирование существующих статей в сети.

Поэтому использование генеративного ИИ для меня ограничивалось обобщением и быстрым исследованием.

Но однажды я увидел видео об _**истории успеха Chrome Web Extension и разработчиках, зарабатывающих миллионы**_ .

Идея показалась мне настолько убедительной, что я захотел попробовать сделать ее.  
И когда я провел исследование, я узнал, что расширения Chrome Web Extensions создаются с использованием JavaScript, но я не был в этом так хорош.

Поэтому я изучил основы JavaScript, а также анатомию (структуру файлов и папок) веб-расширений Chrome.

Поскольку я просто хотел проверить идею создания расширения и опубликовать его в официальном интернет-магазине Chrome, я планировал использовать для его создания инструменты искусственного интеллекта.

Итак, я написал свою первую подсказку (инструкцию) на [Gemini](https://gemini.google.com/) (ИИ от Google), и она написала код, но когда я попробовал, он не сработал. Я попробовал несколько вариантов, но ни один не сработал. Поэтому я отдохнул пару дней, не написав код для расширения.

Просто я хотел создать расширение, которое отображало бы список предстоящих 5 фестивалей с оставшимся количеством дней. Первый должен быть большего размера шрифта, а остальные меньшего размера шрифта.

Через пару дней я захотел дать ему последний шанс и написал подсказку.  
И Gemini сгенерировал код, который, когда я попробовал, сработал. Затем я опубликовал его в Chrome Web Store, и он называется **[«Nepali Festivals Tracker»](https://chromewebstore.google.com/detail/nepali-festivals-tracker/pgfagekhabgbdgbdbenghjdcleeoiajm)** . Вы можете попробовать его.

## [](https://dev.to/vijaythapa/how-i-created-published-a-chrome-extension-with-ai-46op#using-ai-to-write-code)Использование ИИ для написания кода

Для создания этого расширения Chrome «Festivals Tracker» я использовал Gemini от Google, который бесплатен и доступен всем.  
И вот как я использовал его для создания работающего расширения Chrome за несколько минут.

> Но если вы новичок в создании расширений Chrome, JavaScript и HTML/CSS, то я сначала рекомендую вам посмотреть несколько видео по ним. Особенно понимание структуры файлов и папок для создания расширения Chrome.

Я предполагаю, что вы знакомы с HTML/CSS, JavaScript и разработкой веб-расширений Chrome.

### [](https://dev.to/vijaythapa/how-i-created-published-a-chrome-extension-with-ai-46op#the-prompt)Подсказка

Вот подсказка, которую я дал gemini для создания веб-расширения Chrome.

[![Запрос на создание расширения Chrome с помощью Gemini](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fq3zqc8zp8ehje1pqar2p.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fq3zqc8zp8ehje1pqar2p.png)

### [](https://dev.to/vijaythapa/how-i-created-published-a-chrome-extension-with-ai-46op#generated-code)Сгенерированный код

В соответствии со структурой файла расширения Chrome Web Extension были сгенерированы следующие коды.

**1\. Файл манифеста (manifest.json)**  
Этот файл определяет базовую структуру и разрешения для расширения.

[![Файл Manifest.json, созданный Gemini для расширения Chrome](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F15oe7ahhnk5exa6b9vbg.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F15oe7ahhnk5exa6b9vbg.png)

**2\. Всплывающее HTML-окно (popup.html)**  
Этот HTML-файл будет отображать информацию о фестивале.

[![Файл Popup.html, созданный расширением Gemini для Chrome](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fbukamfpqzttot0fea07n.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fbukamfpqzttot0fea07n.png)

**3\. Всплывающий JavaScript (popup.js)**  
Этот файл JavaScript будет обрабатывать логику отслеживания фестивалей.

[![Файл Popup.js, созданный Gemini для расширения Chrome](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fifgq0ct8jv0cz0jl9rgs.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fifgq0ct8jv0cz0jl9rgs.png)

**4\. Фоновый скрипт (background.js)**  
Этот скрипт работает в фоновом режиме и может выполнять такие задачи, как периодическая проверка обновлений.  
Поскольку мое расширение было простым, ему не нужно было работать в фоновом режиме.

### [](https://dev.to/vijaythapa/how-i-created-published-a-chrome-extension-with-ai-46op#testing-locally)Тестирование локально

После того, как код сгенерирован, вы можете протестировать его локально, чтобы проверить, работает он или нет. Для этого вам нужно открыть браузер Chrome на вашем компьютере и включить «Режим разработчика», затем загрузить папку, содержащую все файлы кода.

Вы можете следовать инструкциям ниже.

1.  Создайте новую папку для расширения Chrome.
2.  Поместите все файлы (manifest.json, popup.html, popup.js и background.js) в эту папку.
3.  Загрузите расширение в Chrome, перейдя по адресу chrome://extensions/, включив «Режим разработчика» и нажав «Загрузить распакованное».

После тестирования я обнаружил, что расширение работает так, как мне хотелось, поэтому на следующем этапе я попытался сделать его более красивым, добавив немного CSS (как и любое другое веб-приложение).  
И, конечно же, я попросил Gemini сделать это, так как я хотел, чтобы этот проект был выполнен ИИ и протестировал его возможности. К моему удивлению, он добавил CSS и сделал пользовательский интерфейс современным и красивым. Вот окончательный дизайн после того, как я добавил в него несколько настроек.

[![Финальный дизайн расширения Chrome для трекера непальских фестивалей](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F2vngka67smlhkcniaesn.png)](https://media2.dev.to/dynamic/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F2vngka67smlhkcniaesn.png)

После того, как я остался доволен дизайном расширения, мне захотелось развить его и проверить, можно ли опубликовать его в официальном интернет-магазине Chrome или нет.

Поэтому я создал учетную запись разработчика Chrome, заплатив единовременный взнос в размере 5 долларов США, и отправил ее в Магазин.

И через пару часов он был принят, и теперь он доступен в официальном интернет-магазине Chrome, где любой желающий может попробовать его БЕСПЛАТНО.

## [](https://dev.to/vijaythapa/how-i-created-published-a-chrome-extension-with-ai-46op#now-create-your-own)Теперь создайте свой собственный

> Существуют сотни племен и групп со своими уникальными праздниками, которые могут не быть указаны в официальном национальном календаре.

И такие приложения (расширения) могут быть полезны для распространения информации среди людей по всему миру или просто для отслеживания вашего фестиваля, когда вы находитесь вдали от дома.

**_Возможно, этот фестиваль не важен для всех, но для меньшинств это символ их идентичности._**

А приложения/расширения, такие как Festivals Tracker, могут стать шагом на пути к сохранению идентичности (культуры, традиций и фестивалей).

Итак, я поделился всей информацией и доказал, что это возможно, теперь ваша очередь попробовать сделать что-то полезное с помощью ИИ.

Но если вам нужен только исходный код и вы хотите опубликовать свое собственное расширение, то [КЛИКНИТЕ ЗДЕСЬ](https://www.patreon.com/vijaythapa/shop/festivals-tracker-chrome-extension-896929)  
_(Скидка на январь. Код - **3525C** )_

Наконец-то я почувствовал, что ИИ может стать помощником, о котором вы даже не думали, что он вам нужен.

Если вы можете дать четкую подсказку (инструкции), это может помочь вам выполнить любые задачи быстрее. Это может быть полезно для генерации идей, исследования и создания MVP как можно быстрее.

Итак, **будьте хороши в подсказках, и ИИ станет для вас лучшим помощником** .

## Связанные статьи
- [Дорабатываем чужие сайты: Как написать расширение для Chrome с помощью ChatGPT](Projects/Extentions/customize-sites-chatgpt.md) - Другой подход к созданию с помощью ИИ
- [Pet-проект расширения для Chrome](Projects/Extentions/pet-project-chrome-extension.md) - Опыт создания и продвижения
- [chrome-store-seo-tips](chrome-store-seo-tips.md) - Продвижение расширения
