---
{"dg-publish":true,"permalink":"/projects/extentions/dev-tools/web-audio-prosmotr-pokazatelej-api-web-audio-chrome-dev-tools-chrome-for-developers/"}
---


# WebAudio: просмотр показателей API WebAudio.  |  Chrome DevTools  |  Chrome for Developers

> ## Excerpt
> Просмотр показателей API WebAudio на панели WebAudio.

---
Используйте панель **WebAudio** для просмотра показателей [API WebAudio](https://developer.mozilla.org/docs/Web/API/Web_Audio_API) .

## Обзор

На панели **WebAudio** отображаются показатели производительности [AudioContext](https://developer.mozilla.org/docs/Web/API/AudioContext) для веб-сайтов, использующих API WebAudio.

## Откройте панель WebAudio.

Чтобы открыть панель **WebAudio** :

1.  [Откройте Инструменты разработчика](https://developer.chrome.com/docs/devtools/open?hl=ru) .
2.  Откройте **командное меню,** нажав:
    -   macOS: Command + Shift + P
    -   Windows, Linux, ChromeOS: Control + Shift + P. ![Командное меню с](https://developer.chrome.com/static/docs/devtools/webaudio/image/command-menu-webaudio.png?hl=ru)
3.  Начните вводить `WebAudio` , выберите « **Показать WebAudio»** и нажмите Enter . DevTools отображает панель **WebAudio** в нижней части окна DevTools.

Либо в правом верхнем углу выберите **Дополнительные параметры** > **Дополнительные инструменты** > **WebAudio** .

![Панель WebAudio в DevTools](https://developer.chrome.com/static/docs/devtools/webaudio/image/devtools-webaudio.png?hl=ru)

## Просмотр показателей AudioContext

На панели действий в верхней части панели **WebAudio** выберите AudioContext, чтобы просмотреть следующие показатели:

-   **Состояние** : указывает состояние текущего аудиоконтекста. Может быть `closed` , `running` или `suspended` .
-   **Частота дискретизации** (Гц): частота дискретизации в секунду, сообщенная из AudioContext, преобразованная в герцы.
-   **Размер буфера обратного вызова** (кадры): размер буфера обратного вызова, указанный в [примерах кадров](https://developer.mozilla.org/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#audio_buffers_frames_samples_and_channels) , предоставляемый базовой системой.
-   **Макс. выходные каналы** (ch): максимальное количество аудиоканалов, доступных на текущем устройстве вывода звука.

И в строке состояния внизу:

-   **Текущее время** (с): текущая временная метка в секундах, сообщаемая из AudioContext.
-   **Интервал обратного вызова** (мс): средневзвешенная разница времени между обратными вызовами.
-   **Мощность рендеринга** (в процентах): процент, показывающий, как работает средство рендеринга веб-аудио в рамках заданного бюджета рендеринга.

Чтобы собрать мусор, нажмите соответствующую кнопку на панели действий.
