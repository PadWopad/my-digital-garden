---
{"dg-publish":true,"permalink":"/projects/extentions/analyze-tradingview-charts/"}
---


# Analyze tradingview.com charts with Chrome extension, N8N and OpenAI | n8n workflow template

## Связанные статьи
- [Pet-проект расширения для Chrome: как я вырастил аудиторию](Projects/Extentions/pet-project-chrome-extension.md) - Полезный опыт по продвижению расширения Chrome
- [Как я создал и опубликовал расширение Chrome с помощью ИИ](Projects/Extentions/create-publish-extension-ai.md) - Еще один пример использования ИИ в расширениях
- [Дорабатываем чужие сайты: Как написать расширение для Chrome с помощью ChatGPT](Projects/Extentions/customize-sites-chatgpt.md) - Про интеграцию с внешними сервисами
- [make-extension-10min](Projects/Extentions/make-extension-10min.md) - Базовое руководство по созданию расширений

> ## Excerpt
> This flow is supported by a Chrome plugin created with Cursor AI.

The idea was to create a Chrome plugin and a backend service in N8N to do chart analytics wit

---
Опубликовано 1 месяц назад

### Категории

### Описание шаблона

Этот процесс поддерживается плагином Chrome, созданным с помощью Cursor AI.

Идея заключалась в создании плагина Chrome и **бэкэнд-сервиса** в N8N для аналитики диаграмм с помощью OpenAI. Это хороший пример того, как отправить скриншот из браузера в N8N.

**Для кого это?**  
Разработчики N8N, которые хотят узнать об использовании плагина Chrome, веб-хука N8N и OpenAI.

**Какие возможности он предоставляет?**  
Этот пример открывает целый ряд подключенных расширений Chrome N8N, которые могут анализировать скриншоты с помощью OpenAI.

**Что делает этот рабочий процесс?**  
Рабочий процесс содержит:

-   триггер веб-хука
-   узел OpenAI с GPT-4O-MINI и выбранным **Analyze Image**
-   узел ответа для отправки обратно текста, созданного после анализа снимка экрана.

![n8n_tradingview.png](https://n8niostorageaccount.blob.core.windows.net/n8nio-strapi-blobs-prod/assets/n8n_tradingview_a48bd0e82a.png)  
![хром.png](https://n8niostorageaccount.blob.core.windows.net/n8nio-strapi-blobs-prod/assets/chrome_5818940e8f.png)

Все это необходимо для взаимодействия с расширением Chrome, созданным с помощью Cursor AI.

Идея заключается в том, чтобы посетить графики криптовалют [tradingview.com](http://tradingview.com/) , нажать на плагин Chrome и получить аналитику по показанному графику на понятном языке. Это управляется потоком N8N.

Благодаря новым возможностям анализа изображений OpenAI это открывает целый мир возможностей.

**Требования/настройка**

-   API-ключ OpenAI
-   Курсор AI установлен
-   Расширение Chrome. [Скачать](https://things.io/wp-content/uploads/2024/12/chrome_screenshot.zip)
-   Код N8N JSON. [Скачать](https://things.io/wp-content/uploads/2024/12/chrome_extension_backend_with_AI.json)

**Как настроить его под свои нужды?**  
Расширение Chrome и поток N8N можно адаптировать для использования на других веб-сайтах. Вы можете рассмотреть:

-   анализировать финансовый экран и задавать вопросы по отображаемым данным
-   анализ других диаграмм
-   расширение рабочего процесса N8N с помощью других узлов ИИ

Благодаря ИИ и аналитике изображений у вас нет ограничений, а в некоторых случаях это избавляет вас от необходимости создавать сложные интеграции API.

[Загрузить расширение Chrome](https://things.io/wp-content/uploads/2024/12/chrome_screenshot.zip)

### Поделиться шаблоном

## Больше шаблонов финансовых рабочих процессов

[

### Действия по выполнению следующих шагов вашей встречи с использованием стенограмм и искусственного интеллекта

](https://n8n.io/workflows/2328-actioning-your-meeting-next-steps-using-transcripts-and-ai/)

Этот рабочий процесс n8n демонстрирует, как можно обобщать и автоматизировать действия после встречи из видеотрансляций, загруженных в AI Agent. Экономьте время между встречами, позволяя AI выполнять рутинные задачи по организации последующих встреч и приглашений. Как это работает Этот рабочий процесс сканирует календарь для клиентских или командных встреч, которые проводились онлайн. \* Будут предприняты попытки извлечь все записанные транскрипты, которые затем отправляются AI Agent. AI Agent обобщает и определяет, требуются ли какие-либо последующие встречи. Если они найдены, Agent использует свой инструмент Calendar для создания события на время, дату и место для следующей встречи, а также добавит известных участников. Требования Google Calendar и возможность извлекать транскрипты встреч (для этого действия существует специальное разрешение OAuth!) Учетная запись OpenAI для доступа к LLM. Настройка рабочего процесса Этот пример регистрирует только последующие встречи, но может быть расширен для создания отчетов или отправки электронных писем.

![джимлеук](https://gravatar.com/avatar/4ab99e51473df76838beeaac908747f7928c625f869794815cabe34016967d51?r=pg&d=retro&size=200)

Джимлеук

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### Извлечение данных счетов-фактур с помощью LlamaParse и OpenAI

](https://n8n.io/workflows/2320-invoice-data-extraction-with-llamaparse-and-openai/)

Этот рабочий процесс n8n автоматизирует процесс анализа и извлечения данных из счетов-фактур PDF. С помощью этого рабочего процесса бухгалтеры и финансисты могут добиться огромной экономии времени и средств в своих плотных графиках. Читайте блог: https://blog.n8n.io/how-to-extract-data-from-pdf-to-excel-spreadsheet-advance-parsing-with-n8n-io-and-llamaparse/ Как это работает Этот рабочий процесс будет отслеживать входящие электронные письма от поставщиков. Он будет загружать прикрепленные PDF-файлы и обрабатывать их с помощью стороннего сервиса под названием LlamaParse. LlamaParse специально разработан для обработки и преобразования сложных структур данных PDF, таких как таблицы, в Markdown. Markdown легко обрабатывается для моделей LLM, поэтому извлечение данных нашим агентом ИИ более точное и надежное. Рабочий процесс экспортирует извлеченные данные из агента ИИ в Google Таблицы после завершения работы. Требования Критерии триггера электронной почты должны быть настроены для захвата электронных писем с вложениями. Перед использованием этого рабочего процесса необходимо создать метку gmail «синхронизированный счет». Учетная запись LlamaIndex.ai для использования службы LlamaParse. Учетная запись OpenAI для использования GPT для работы ИИ. Google Таблицы для сохранения выходных данных процесса извлечения данных, хотя их можно заменить на любые другие нужные вам. Настройка этого рабочего процесса Этот рабочий процесс использует Gmail и Google Таблицы, но их можно легко заменить на эквивалентные службы, такие как Outlook и Excel. Не используете Excel? Просто перенаправьте выходные данные агента ИИ в выбранное вами бухгалтерское программное обеспечение.

![джимлеук](https://gravatar.com/avatar/4ab99e51473df76838beeaac908747f7928c625f869794815cabe34016967d51?r=pg&d=retro&size=200)

Джимлеук

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### Извлекайте расходы из электронных писем и добавляйте в Google Таблицы

](https://n8n.io/workflows/1466-extract-expenses-from-emails-and-add-to-google-sheets/)

Этот рабочий процесс проверит почтовый ящик на наличие новых писем, и если тема содержит Expenses или Recipe, он отправит вложение в Mindee для обработки, а затем обновит таблицу Google значениями. Чтобы использовать этот узел, вам нужно будет настроить узел Email Read на использование учетных данных вашего почтового ящика и настроить узлы Mindee и Google Sheets на использование ваших учетных данных.

![jon-n8n](https://gravatar.com/avatar/5240094f838126182ceefb50ca4a3cf75cc7dc0808efd4b9920d792e41bfc45e?r=pg&d=retro&size=200)

Джонатан

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### Создайте помощника по работе с финансовыми документами с помощью Qdrant и Mistral.ai

](https://n8n.io/workflows/2335-build-a-financial-documents-assistant-using-qdrant-and-mistralai/)

Этот рабочий процесс n8n демонстрирует, как управлять вашим векторным хранилищем Qdrant, когда необходимо синхронизировать его с локальными файлами. Он охватывает создание, обновление и удаление записей векторного хранилища, гарантируя, что наш помощник чат-бота никогда не устареет и не будет вводить в заблуждение. Отказ от ответственности Этот рабочий процесс зависит от локальных файлов, доступ к которым осуществляется через локальную файловую систему, и поэтому в настоящее время будет работать только в версии n8n с собственным хостингом. Можно изменить этот рабочий процесс для работы в облаке n8n, заменив локальный триггер файла и узлы чтения файлов. Как это работает Локальный каталог, в который загружаются банковские выписки, отслеживается с помощью локального триггера файла. Триггер отслеживает события создания, изменения и удаления файла. Когда файл создается, его содержимое загружается в векторное хранилище. Когда файл обновляется, его предыдущие записи заменяются. Когда файл удаляется, соответствующие записи также удаляются из векторного хранилища. Простой чат-бот вопросов и ответов настроен для ответа на любые вопросы о банковских выписках в системе. Требования Версия n8n с собственным хостингом. Некоторые узлы, используемые в этом рабочем процессе, работают только с локальной файловой системой. Экземпляр Qdrant для хранения записей. Настройка рабочего процесса Этот рабочий процесс также может работать с удаленными данными. Попробуйте интегрировать бухгалтерское или CRM-программное обеспечение для создания управляемой системы для расчета заработной платы, счетов-фактур и многого другого. Хотите полностью локальный подход? Доступна версия этого рабочего процесса, которая использует Ollama. Вы можете загрузить этот шаблон здесь: https://drive.google.com/file/d/189F1fNOiw6naNSlSwnyLVEm\_Ho\_IFfdM/view?usp=sharing

![джимлеук](https://gravatar.com/avatar/4ab99e51473df76838beeaac908747f7928c625f869794815cabe34016967d51?r=pg&d=retro&size=200)

Джимлеук

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### Транскрибация банковских выписок в Markdown с помощью Gemini Vision AI

](https://n8n.io/workflows/2421-transcribing-bank-statements-to-markdown-using-gemini-vision-ai/)

Этот рабочий процесс n8n демонстрирует подход к разбору банковских выписок в формате PDF с помощью мультимодальных LLM в качестве альтернативы традиционному OCR. Это позволяет извлекать данные из документа гораздо точнее, особенно когда речь идет о таблицах и сложных макетах. Мультимодальный анализ лучше традиционного OCR, потому что: Он снижает сложность и накладные расходы, избегая необходимости предварительной обработки документа в текстовый формат, такой как markdown, перед передачей в LLM. Он обрабатывает нестандартные форматы PDF, которые могут давать искаженный вывод при традиционном преобразовании текста OCR. Это на порядок дешевле, чем премиальные модели OCR, которые по-прежнему требуют очистки и форматирования после обработки. LLM могут форматировать в любую схему или язык по вашему желанию! Как это работает Вы можете использовать пример банковской выписки, созданный специально для этого рабочего процесса, здесь: https://drive.google.com/file/d/1wS9U7MQDthj57CvEcqG\_Llkr-ek6RqGA/view?usp=sharing Банковская выписка в формате PDF импортируется через Google Диск. Для этой демонстрации я создал фиктивную банковскую выписку, которая включает в себя сложные табличные макеты из 5 столбцов. Обычно OCR не может правильно выровнять столбцы и ошибочно принимает некоторые депозиты за снятие средств. Поскольку мультимодальные LLM не принимают PDF-файлы напрямую, нам придется преобразовать PDF в серию изображений. Мы можем добиться этого с помощью такого инструмента, как Stirling PDF. Stirling PDF является самостоятельным, что удобно для конфиденциальных данных, таких как банковские выписки. Stirling PDF вернет наш PDF в виде серии JPG-файлов (по одному на каждую страницу) в сжатом файле. Мы можем использовать узел распаковки n8n для извлечения изображений и обеспечения их упорядоченности с помощью узла сортировки. Затем мы изменим размер каждой страницы с помощью узла редактирования изображения, чтобы обеспечить правильный баланс между пределами разрешения и скоростью обработки. Затем каждое измененное изображение страницы передается в базовый узел LLM, который будет использовать наш мультимодальный LLM по выбору - Gemini 1.5 Pro. В параметрах узла LLM мы добавим «пользовательское сообщение» типа binary (data), которое является способом добавления наших данных изображения в качестве входных данных. Наш запрос даст указание мультимодальному LLM транскрибировать каждую страницу в markdown. Обратите внимание, что вам не нужно этого делать — вы можете просто запросить точки данных для извлечения напрямую! Наша цель для этого шаблона — продемонстрировать способность LLM точно читать страницу. Наконец, с нашей версией markdown всех страниц мы можем передать это другому узлу LLM для извлечения необходимых данных, таких как позиции депозитных строк. Требования API Google Gemini для мультимодального LLM. Доступ к Google Drive для хранения документов. Экземпляр Stirling PDF для преобразования PDF в изображение Настройка рабочего процесса На момент написания статьи Gemini 1.5 Pro является наиболее точным в анализе текстовых документов с относительно низкой стоимостью. Однако, если вы не используете Google Gemini, вы можете переключиться на другие мультимодальные LLM, такие как OpenAI GPT или Antrophic Claude. Если вам не нужна разметка, то можно просто спросить, что именно нужно извлечь, прямо в приглашении LLM, и это сэкономит несколько дополнительных шагов.Не собираетесь анализировать банковские выписки в ближайшее время? Этот шаблон также подходит для счетов-фактур, инвентарных списков, контрактов, юридических документов и т. д.

![джимлеук](https://gravatar.com/avatar/4ab99e51473df76838beeaac908747f7928c625f869794815cabe34016967d51?r=pg&d=retro&size=200)

Джимлеук

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### Технический аналитик ИИ-агент, использующий LLM Vision

](https://n8n.io/workflows/2569-technical-analyst-ai-agent-using-llm-vision/)

Цель рабочего процесса: Цель этого рабочего процесса — создать агента технического анализа на базе ИИ, способного анализировать финансовые графики, в частности, для криптовалют, таких как биткоин или акции. Этот агент предоставляет пользователям информацию о рыночных тенденциях, движении цен и технических индикаторах для принятия обоснованных торговых решений. Как это работает: Агент использует модель Sonnet от Anthropic для LLM Он интегрируется с графиками TradingView через API chart-img.com для создания и загрузки финансовых графиков. Агент анализирует график с помощью возможностей зрения ИИ, исследуя модели свечей, ценовые тенденции и технические индикаторы, такие как индекс относительной силы (RSI) и индекс направленного движения (DMI). Он предоставляет подробный анализ графика, включая уровни поддержки и сопротивления, рыночные тенденции и анализ объема. Агент генерирует визуальное представление анализа, отображая свечи, объем, RSI и DMI. Пошаговая настройка: Создайте бесплатный ключ API от chart-img.com Установите биржу для тикера (по умолчанию NYSE) Учебник

![дерекчынса](https://gravatar.com/avatar/1d8dbb30401a76425734d4319abbaa38548b7572064ca080740bbfe60324772a?r=pg&d=retro&size=200)

Дерек Чунг

![](https://n8n.io/_nuxt/image/c4683e.svg)

## Больше шаблонов рабочих процессов ИИ

[

### Чат агента ИИ

](https://n8n.io/workflows/1954-ai-agent-chat/)

Этот рабочий процесс использует языковые модели OpenAI и SerpAPI для создания отзывчивого, интеллектуального диалогового агента. Он оснащен ручными триггерами чата и возможностями буфера памяти для обеспечения бесперебойного взаимодействия. Для использования этого шаблона вам необходимо использовать n8n версии 1.50.0 или более поздней.

![n8n-команда](https://gravatar.com/avatar/b3d1a47322f05a8be3d2e7bad6a80c29161bd58b91e4762cbb3ac25e5d0db5a8?r=pg&d=retro&size=200)

Команда n8n

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### Собирайте и обобщайте веб-страницы с помощью ИИ

](https://n8n.io/workflows/1951-scrape-and-summarize-webpages-with-ai/)

Этот рабочий процесс объединяет функции веб-скрейпинга и обработки естественного языка. Он использует парсинг HTML для извлечения ссылок, HTTP-запросы для извлечения контента эссе и резюмирование на основе ИИ с использованием GPT-4o. Это прекрасный пример сквозной автоматизированной задачи, которая не только эффективна, но и обеспечивает реальную ценность, резюмируя ценный контент. Обратите внимание, что для использования этого шаблона вам необходимо использовать n8n версии 1.50.0 или более поздней.

![n8n-команда](https://gravatar.com/avatar/b3d1a47322f05a8be3d2e7bad6a80c29161bd58b91e4762cbb3ac25e5d0db5a8?r=pg&d=retro&size=200)

Команда n8n

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### Агент ИИ, который может сканировать веб-страницы

](https://n8n.io/workflows/2006-ai-agent-that-can-scrape-webpages/)

⚙️🛠️🚀🤖🦾 This template is a PoC of a ReAct AI Agent capable of fetching random pages (not only Wikipedia or Google search results). On the top part there's a manual chat node connected to a LangChain ReAct Agent. The agent has access to a workflow tool for getting page content. The page content extraction starts with converting query parameters into a JSON object. There are 3 pre-defined parameters: url\*\* – an address of the page to fetch method\*\* = full / simplified maxlimit\*\* - maximum length for the final page. For longer pages an error message is returned back to the agent Page content fetching is a multistep process: An HTTP Request mode tries to get the page content. If the page content was successfuly retrieved, a series of post-processing begin: Extract HTML BODY; content Remove all unnecessary tags to recude the page size Further eliminate external URLs and IMG scr values (based on the method query parameter) Remaining HTML is converted to Markdown, thus recuding the page lengh even more while preserving the basic page structure The remaining content is sent back to an Agent if it's not too long (maxlimit = 70000 by default, see CONFIG node). NB: You can isolate the HTTP Request part into a separate workflow. Check the Workflow Tool description, it guides the agent to provide a query string with several parameters instead of a JSON object. Please reach out to Eduard is you need further assistance with you n8n workflows and automations! Note that to use this template, you need to be on n8n version 1.19.4 or later.

![эдуард](https://gravatar.com/avatar/a551e67c6fe7affd5f882a527dee154bb6c3ac90cf878326accb3fb3ec77c8a6?r=pg&d=retro&size=200)

Eduard

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### Telegram AI Chatbot

](https://n8n.io/workflows/1934-telegram-ai-chatbot/)

The workflow starts by listening for messages from Telegram users. The message is then processed, and based on its content, different actions are taken. If it's a regular chat message, the workflow generates a response using the OpenAI API and sends it back to the user. If it's a command to create an image, the workflow generates an image using the OpenAI API and sends the image to the user. If the command is unsupported, an error message is sent. Throughout the workflow, there are additional nodes for displaying notes and simulating typing actions.

![эдуард](https://gravatar.com/avatar/a551e67c6fe7affd5f882a527dee154bb6c3ac90cf878326accb3fb3ec77c8a6?r=pg&d=retro&size=200)

Eduard

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### OpenAI GPT-3: Company Enrichment from website content

](https://n8n.io/workflows/1862-openai-gpt-3-company-enrichment-from-website-content/)

Enrich your company lists with OpenAI GPT-3 ↓ You'll get valuable information such as: Market (B2B or B2C) Industry Target Audience Value Proposition This will help you to: add more personalization to your outreach make informed decisions about which accounts to target I've made the process easy with an n8n workflow. Here is what it does: Retrieve website URLs from Google Sheets Extract the content for each website Analyze it with GPT-3 Update Google Sheets with GPT-3 data

![лемпир](https://gravatar.com/avatar/b0a32f127a6ad690cd4ee808cb4d1b59d3b5e53410181d54f91d10c0027ebb43?r=pg&d=retro&size=200)

Lucas Perret

![](https://n8n.io/_nuxt/image/c4683e.svg)

[

### Ask questions about a PDF using AI

](https://n8n.io/workflows/1960-ask-questions-about-a-pdf-using-ai/)

Рабочий процесс сначала заполняет индекс Pinecone векторами из технического документа Bitcoin. Затем он ждет ручного сообщения чата. При получении сообщение чата преобразуется в вектор и сравнивается с векторами в Pinecone. Наиболее похожие векторы извлекаются и передаются в OpenAI для генерации ответа чата. Обратите внимание, что для использования этого шаблона вам необходимо использовать n8n версии 1.19.4 или более поздней.

![davidn8n](https://gravatar.com/avatar/4cda9c7c1c24fdb61896cac588296d1dad03655a439ab71ef34f4c62c0ba8524?r=pg&d=retro&size=200)

Дэвид Робертс

![](https://n8n.io/_nuxt/image/c4683e.svg)

Реализуйте сложные процессы быстрее с помощью n8n

![красный значок](https://n8n.io/_nuxt/image/83b330.png) ![желтый значок](https://n8n.io/_nuxt/image/1e8ec1.png)
