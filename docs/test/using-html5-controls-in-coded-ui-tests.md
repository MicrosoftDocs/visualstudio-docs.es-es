---
title: Usar controles HTML5 en pruebas automatizadas de IU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: "17"
ms.author: douge
manager: douge
ms.openlocfilehash: 3e2e14748e27d965762b3245908382b278e6e132
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Usar controles HTML5 en pruebas de IU codificada
Las pruebas de IU codificadas proporcionan soporte para algunos de los controles HTML5 incluidos en Internet Explorer 9 o Internet Explorer 10.  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
> [!WARNING]
>  En versiones anteriores a Internet Explorer 10, era posible ejecutar pruebas de IU codificadas en un nivel de privilegios más alto en comparación con el del proceso de Internet Explorer. Al ejecutar pruebas de IU codificadas en Internet Explorer 10, tanto la prueba de IU codificada como el proceso de Internet Explorer deben estar en el mismo nivel de privilegios. Esto se debe a las características de AppContainer más seguras de Internet Explorer 10.  
  
> [!WARNING]
>  Si crea una prueba de IU codificada en Internet Explorer 10, podría no ejecutarse con Internet Explorer 9 o Internet Explorer 8. Esto se debe a que Internet Explorer 10 incluye controles HTML5, como audio, vídeo, barra de progreso y control deslizante. Internet Explorer 9 o Internet Explorer 8 no reconocen estos controles HTML5. Igualmente, la prueba de IU codificada mediante Internet Explorer 9 podría incluir algunos controles HTML5 que tampoco reconoce Internet Explorer 8.  
  
## <a name="supported-html5-controls"></a>Controles HTML5 compatibles  
 Las pruebas de IU codificadas admiten grabación, reproducción y validación de los controles HTML5 siguientes:  
  
-   [Control de audio](#UsingHTML5ControlsCodedUITestsAudio)  
  
-   [Control de vídeo](#UsingHTML5ControlsCodedUITestsVideo)  
  
-   [Control deslizante](#UsingHTML5ControlsCodedUITestsSlider)  
  
-   [Barra de progreso](#UsingHTML5ControlsCodedUITestsProgressBar)  
  
###  <a name="UsingHTML5ControlsCodedUITestsAudio"></a> Control de audio  
 **Control de audio:** las acciones en el control de audio de HTML5 se graban y se reproducen correctamente.  
  
 ![Control de audio de HTML5](../test/media/codedui_html5_audio.png "CodedUI_HTML5_Audio")  
  
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
>  La cantidad de tiempo para buscar y pausar puede ser significativa. Durante la reproducción, la prueba de IU codificada esperará hasta el momento especificado en `(TimeSpan)` antes de pausar el audio. Si por alguna circunstancia especial transcurre el tiempo especificado antes de que se alcance el comando Pausa, se iniciará una excepción.  
  
###  <a name="UsingHTML5ControlsCodedUITestsVideo"></a> Control de vídeo  
 **Control de vídeo:** las acciones en el control de vídeo de HTML5 se graban y se reproducen correctamente.  
  
 ![Control de vídeo de HTML5](../test/media/codedui_html5_video.png "CodedUI_HTML5_Video")  
  
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
>  Si rebobina o avanza rápidamente el vídeo mediante etiquetas -30s o +30s, se agregarán para buscar en el momento adecuado.  
  
###  <a name="UsingHTML5ControlsCodedUITestsSlider"></a> Control deslizante  
 **Control deslizante:** las acciones en el control deslizante de HTML5 se graban y se reproducen correctamente.  
  
 ![Control deslizante de HTML5](../test/media/codedui_html5_slider.png "CodedUI_HTML5_Slider")  
  
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
  
###  <a name="UsingHTML5ControlsCodedUITestsProgressbar"></a> Barra de progreso  
 **Control de barra de progreso:** la barra de progreso es un control con el que no se puede interactuar. Puede agregar aserciones en las propiedades `Value` y `Max` de este control.  
  
 ![Control de barra de progreso de HTML5](../test/media/codedui_html5_progressbar.png "CodedUI_HTML5_ProgressBar")  
  
## <a name="see-also"></a>Vea también  
 [Elementos HTML](http://go.microsoft.com/fwlink/?LinkID=232441)   
 [Usar UI Automation para probar el código](../test/use-ui-automation-to-test-your-code.md)   
 [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Personalizar la prueba automatizada de IU](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)   
 [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
