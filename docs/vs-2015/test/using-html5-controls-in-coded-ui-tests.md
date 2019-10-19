---
title: Usar controles HTML5 en pruebas automatizadas de IU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 029b547102863f4798ad261deb678c4d98596916
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657200"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Usar controles HTML5 en pruebas de IU codificada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las pruebas de IU codificadas proporcionan soporte para algunos de los controles HTML5 incluidos en Internet Explorer 9 o Internet Explorer 10.

 **Requisitos**

- Visual Studio Enterprise

> [!WARNING]
> En versiones anteriores a Internet Explorer 10, era posible ejecutar pruebas de IU codificadas en un nivel de privilegios más alto en comparación con el del proceso de Internet Explorer. Al ejecutar pruebas de IU codificadas en Internet Explorer 10, tanto la prueba de IU codificada como el proceso de Internet Explorer deben estar en el mismo nivel de privilegios. Esto se debe a las características de AppContainer más seguras de Internet Explorer 10.

> [!WARNING]
> Si crea una prueba de IU codificada en Internet Explorer 10, podría no ejecutarse con Internet Explorer 9 o Internet Explorer 8. Esto se debe a que Internet Explorer 10 incluye controles HTML5, como audio, vídeo, barra de progreso y control deslizante. Internet Explorer 9 o Internet Explorer 8 no reconocen estos controles HTML5. Igualmente, la prueba de IU codificada mediante Internet Explorer 9 podría incluir algunos controles HTML5 que tampoco reconoce Internet Explorer 8.

## <a name="supported-html5-controls"></a>Controles HTML5 compatibles
 Las pruebas de IU codificadas admiten grabación, reproducción y validación de los controles HTML5 siguientes:

- [Control de audio](#audio-control)

- [Control de vídeo](#video-control)

- [Control deslizante](#slider)

- [Barra de progreso](#progressbar)

### <a name="audio-control"></a>Control de audio
 **Control de audio:** las acciones en el control de audio de HTML5 se graban y se reproducen correctamente.

 ![Control Audio de HTML5](../test/media/codedui-html5-audio.png)

|Acción|Grabando|Código generado|
|------------|---------------|--------------------|
|**Reproducir audio**<br /><br /> Directamente desde el control o desde el menú contextual de los controles.|Reproducir el audio \<nombre> a partir de 00:00:00|HtmlAudio.Play(TimeSpan)|
|**Buscar un momento concreto en el audio**|Buscar el audio \<nombre> en 00:01:48|HtmlAudio.Seek(TimeSpan)|
|**Pausar audio**<br /><br /> Directamente desde el control o desde el menú contextual de los controles.|Pausar el audio \<nombre> en 00:01:53|HtmlAudio.Pause(TimeSpan)|
|**Silenciar audio**<br /><br /> Directamente desde el control o desde el menú contextual de los controles.|Silenciar el audio \<nombre>|HtmlAudio.Mute()|
|**Reactivar audio**<br /><br /> Directamente desde el control o desde el menú contextual de los controles.|Reactivar el audio \<nombre>|HtmlAudio.Unmute()|
|**Cambiar el volumen del audio**|Establecer el volumen del audio \<nombre> al 79 %|HtmlAudio.SetVolume(float)|

 Las propiedades siguientes están disponibles para HtmlAudio, y puede agregar una aserción en todas ellas:

```
string AutoPlay
string Controls
string CurrentSrc
string CurrentTime
string CurrentTimeAsString
string Duration
string DurationAsString
string Ended
string Loop
string Muted
string Paused
string PlaybackRate
string ReadyState
string Seeking
string Src
string Volume
```

 **Propiedades de búsqueda:** las propiedades de búsqueda de `HtmlAudio` son `Id`, `Name` y `Title`.

 **Propiedades del filtro:** las propiedades del filtro de `HtmlAudio` son `Src`, `Class`, `ControlDefinition` y `TagInstance`.

> [!NOTE]
> La cantidad de tiempo para buscar y pausar puede ser significativa. Durante la reproducción, la prueba de IU codificada esperará hasta el momento especificado en `(TimeSpan)` antes de pausar el audio. Si por alguna circunstancia especial transcurre el tiempo especificado antes de que se alcance el comando Pausa, se iniciará una excepción.

### <a name="video-control"></a>Control de vídeo
 **Control de vídeo:** las acciones en el control de vídeo de HTML5 se graban y se reproducen correctamente.

 ![Control Video de HTML5](../test/media/codedui-html5-video.png)

|Acción|Grabando|Código generado|
|------------|---------------|--------------------|
|**Reproducir vídeo**<br /><br /> Directamente desde el control o desde el menú contextual de los controles.|Reproducir el vídeo \<nombre> a partir de 00:00:00|HtmlVideo.Play(TimeSpan)|
|**Buscar un momento concreto en el vídeo**|Buscar el vídeo \<nombre> en 00:01:48|HtmlVideo.Seek(TimeSpan)|
|**Pausar vídeo**<br /><br /> Directamente desde el control o desde el menú contextual de los controles.|Pausar el vídeo \<nombre> en 00:01:53|HtmlVideo.Pause(TimeSpan)|
|**Silenciar vídeo**<br /><br /> Directamente desde el control o desde el menú contextual de los controles.|Silenciar el vídeo \<nombre>|HtmlVideo.Mute()|
|**Reactivar audio del vídeo**<br /><br /> Directamente desde el control o desde el menú contextual de los controles.|Reactivar el audio del vídeo \<nombre>|HtmlVideo.Unmute()|
|**Cambiar el volumen del vídeo**|Establecer el volumen del vídeo \<nombre> al 79 %||

 Todas las propiedades de HtmlAudio están disponibles para HtmlVideo. También están disponibles las tres propiedades siguientes. Se puede agregar una aserción en todas ellas.

```
string Poster
string VideoHeight
string VideoWidth

```

 **Propiedades de búsqueda:** las propiedades de búsqueda de `HtmlVideo` son `Id`, `Name` y `Title`.

 **Propiedades del filtro:** las propiedades del filtro de `HtmlVideo` son `Src`, `Poster`, `Class`, `ControlDefinition` y `TagInstance`.

> [!NOTE]
> Si rebobina o avanza rápidamente el vídeo mediante etiquetas -30s o +30s, se agregarán para buscar en el momento adecuado.

### <a name="slider"></a>Slider
 **Control deslizante:** las acciones en el control deslizante de HTML5 se graban y se reproducen correctamente.

 ![Control Slider de HTML5](../test/media/codedui-html5-slider.png)

|Acción|Grabando|Código generado|
|------------|---------------|--------------------|
|**Establecer una posición en el control deslizante**|Establecer la posición en \<x> en el control deslizante \<nombre>|HtmlSlider.ValueAsNumber=\<x>|

 Las propiedades siguientes están disponibles para HtmlSlider, y puede agregar una aserción en todas ellas:

```
string Disabled
string Max
string Min
string Required
string Step
string ValueAsNumber
```

### <a name="progressbar"></a>ProgressBar
 **Control ProgressBar:** la barra de progreso es un control con el que no se puede interactuar. Puede agregar aserciones en las propiedades `Value` y `Max` de este control.

 ![Control ProgressBar de HTML5](../test/media/codedui-html5-progressbar.png)

## <a name="see-also"></a>Vea también

- [HTML Elements](https://www.w3schools.com/HTML/html_elements.asp) (Elementos HTML)
- [Usar Automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
- [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Personalizar la prueba de IU codificada](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)
- [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
