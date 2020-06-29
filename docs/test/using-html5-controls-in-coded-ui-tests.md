---
title: Usar controles HTML5 en pruebas de IU codificada
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 3519d1cc030c69880bcc047b4b4123785c4fb8b2
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289344"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Usar controles HTML5 en pruebas automatizadas de IU

Las pruebas de IU codificadas proporcionan soporte para algunos de los controles HTML5 incluidos en Internet Explorer 9 o Internet Explorer 10.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requisitos**

- Visual Studio Enterprise

> [!WARNING]
> En versiones anteriores a Internet Explorer 10, era posible ejecutar pruebas de IU codificadas en un nivel de privilegios más alto en comparación con el del proceso de Internet Explorer. Al ejecutar pruebas de IU codificadas en Internet Explorer 10, tanto la prueba de IU codificada como el proceso de Internet Explorer deben estar en el mismo nivel de privilegios. Esto se debe a las características de AppContainer más seguras de Internet Explorer 10.

> [!WARNING]
> Si crea una prueba de IU codificada en Internet Explorer 10, podría no ejecutarse con Internet Explorer 9 o Internet Explorer 8. Esto se debe a que Internet Explorer 10 incluye controles HTML5, como audio, vídeo, barra de progreso y control deslizante. Internet Explorer 9 o Internet Explorer 8 no reconocen estos controles HTML5. Igualmente, la prueba de IU codificada mediante Internet Explorer 9 podría incluir algunos controles HTML5 que tampoco reconoce Internet Explorer 8.

## <a name="audio-control"></a>Control de audio

**Control Audio**: Las acciones del control Audio de HTML5 se graban y se reproducen correctamente.

![Control Audio de HTML5](../test/media/codedui_html5_audio.png)

|Acción|Grabando|Código generado|
|-|---------------|-|
|**Reproducir audio**<br /><br /> Directamente desde el control, o bien desde el menú contextual del control.|Reproducir el audio \<name> a partir de 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Buscar un momento concreto en el audio**|Buscar el audio \<name> en 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Pausar audio**<br /><br /> Directamente desde el control, o bien desde el menú contextual del control.|Pausar el audio \<name> en 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Silenciar audio**<br /><br /> Directamente desde el control, o bien desde el menú contextual del control.|Silenciar el audio \<name>|HtmlAudio.Mute()|
|**Reactivar audio**<br /><br /> Directamente desde el control, o bien desde el menú contextual del control.|Reactivar el audio \<name>|HtmlAudio.Unmute()|
|**Cambiar el volumen del audio**|Establecer el volumen del audio \<name> en el 79 %|HtmlAudio.SetVolume(float)|

Vea [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) para obtener una lista de propiedades en las que puede agregar una aserción.

**Propiedades de búsqueda**: Las propiedades de búsqueda de `HtmlAudio` son `Id`, `Name` y `Title`.

**Propiedades del filtro**: Las propiedades del filtro de `HtmlAudio` son `Src`, `Class`, `ControlDefinition` y `TagInstance`.

> [!NOTE]
> La cantidad de tiempo para buscar y pausar puede ser significativa. Durante la reproducción, la prueba de IU codificada esperará hasta el momento especificado en `(TimeSpan)` antes de pausar el audio. Si por alguna circunstancia especial transcurre el tiempo especificado antes de que se alcance el comando Pausa, se iniciará una excepción.

## <a name="video-control"></a>Control de vídeo
**Control Vídeo**: Las acciones del control Vídeo de HTML5 se graban y se reproducen correctamente.

![Control Video de HTML5](../test/media/codedui_html5_video.png)

|Acción|Grabando|Código generado|
|-|---------------|-|
|**Reproducir vídeo**<br /><br /> Directamente desde el control, o bien desde el menú contextual del control.|Reproducir el vídeo \<name> a partir de 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Buscar un momento concreto en el vídeo**|Buscar el vídeo \<name> en 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Pausar vídeo**<br /><br /> Directamente desde el control, o bien desde el menú contextual del control.|Pausar el vídeo \<name> en 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Silenciar vídeo**<br /><br /> Directamente desde el control, o bien desde el menú contextual del control.|Silenciar el audio del vídeo \<name>|HtmlVideo.Mute()|
|**Reactivar audio del vídeo**<br /><br /> Directamente desde el control, o bien desde el menú contextual del control.|Reactivar el audio del vídeo \<name>|HtmlVideo.Unmute()|
|**Cambiar el volumen del vídeo**|Establecer el volumen del vídeo \<name> en el 79 %||

Vea [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) para obtener una lista de propiedades en las que puede agregar una aserción.

**Propiedades de búsqueda**: Las propiedades de búsqueda de `HtmlVideo` son `Id`, `Name` y `Title`.

**Propiedades del filtro**: Las propiedades del filtro de `HtmlVideo` son `Src`, `Poster`, `Class`, `ControlDefinition` y `TagInstance`.

> [!NOTE]
> Si rebobina o avanza rápidamente el vídeo mediante etiquetas -30s o +30s, se agregarán para buscar en el momento adecuado.

## <a name="progressbar"></a>ProgressBar
**ProgressBar (control)** : ProgressBar no es un control con el que se pueda interactuar. Puede agregar aserciones en las propiedades `Value` y `Max` de este control. Para obtener más información, vea [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![Control ProgressBar de HTML5](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Vea también

- [HTML elements](https://developer.mozilla.org/docs/Web/HTML/Element) (Elementos HTML)
- [Usar la automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
- [Crear pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md)
- [Configuraciones y plataformas compatibles con las pruebas automatizadas de IU y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
