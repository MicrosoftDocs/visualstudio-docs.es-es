---
title: Depurar un control WebView | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb004576546fd028b97fa3ebb2b68ad8f4ee2f3a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189846"
---
# <a name="debug-a-webview-control"></a>Depurar un control WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Para inspeccionar y depurar controles `WebView` en una aplicación de Windows Runtime, puede configurar Visual Studio de modo que adjunte el depurador de script al iniciar la aplicación. A partir de Visual Studio 2013 Update 2, tiene dos formas de interactuar con los controles `WebView` mediante el depurador:  
  
-   Abra el [explorador DOM](../debugger/quickstart-debug-html-and-css.md) para un `WebView` de instancia, inspeccionar los elementos DOM, investigar los problemas de estilo CSS y probar cambios presentados de forma dinámica en los estilos.  
  
-   Seleccione la página Web o `iFrame` muestra en el `WebView` instancia como un destino en el [consola JavaScript](../debugger/javascript-console-commands.md) ventana y después podrá interactuar con la página Web mediante comandos de la consola. La consola ofrece acceso al contexto de ejecución de script actual.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Adjuntar el depurador (C#, Visual Basic, C++)  
  
1.  En Visual Studio, agregue un control `WebView` a la aplicación de Windows Runtime.  
  
2.  En el Explorador de soluciones, abra las propiedades del proyecto eligiendo **propiedades** en el menú contextual del proyecto.  
  
3.  Elija **depurar**. En el **proceso de la aplicación** elija **Script**.  
  
     ![Asociar el depurador de script](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Opcional) En las versiones que no son Express de Visual Studio, deshabilitar la depuración just-in-time (JIT) eligiendo **herramientas**, **opciones**, **depuración**, **Just-In-Time**, y, a continuación, deshabilitar JIT depuración de Script.  
  
    > [!NOTE]
    >  Al deshabilitar la depuración JIT, puede ocultar los cuadros de diálogo de las excepciones no controladas que se producen en algunas páginas web. En Visual Studio Express, la depuración JIT siempre está deshabilitada.  
  
5.  Presione F5 para iniciar la depuración.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Usar el Explorador DOM para inspeccionar y depurar un control WebView  
  
1.  (C#, Visual Basic, C++) Adjunte el depurador de script a la aplicación. Consulte la primera sección para obtener instrucciones.  
  
2.  Si aún no lo ha hecho, agregue un control `WebView` a la aplicación y presione F5 para iniciar la depuración.  
  
3.  Vaya a la página que contiene el control o controles `Webview`.  
  
4.  Abra la ventana del explorador DOM para el `WebView` control eligiendo **depurar**, **Windows**, **explorador DOM**y, a continuación, elija la dirección URL de la `WebView` que ¿desea inspeccionar.  
  
     ![Abrir el explorador DOM](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     El Explorador DOM asociado al control `WebView` aparece como una nueva pestaña en Visual Studio.  
  
5.  Ver y modificar elementos DOM activos y estilos CSS, como se describe en [estilos CSS depurar mediante el explorador DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Usar la ventana Consola JavaScript para inspeccionar y depurar un control WebView  
  
1.  (C#, Visual Basic, C++) Adjunte el depurador de script a la aplicación. Consulte la primera sección para obtener instrucciones.  
  
2.  Si aún no lo ha hecho, agregue un control `WebView` a la aplicación y presione F5 para iniciar la depuración.  
  
3.  Abra la ventana Consola JavaScript para la `WebView` control eligiendo **depurar**, **Windows**, **consola JavaScript**.  
  
     Aparece la ventana Consola JavaScript.  
  
4.  Vaya a la página que contiene el control o controles `Webview`.  
  
5.  En la ventana de consola, seleccione la página Web o un `iFrame` mostrado por el `WebView` en controlar la **destino** lista.  
  
     ![Destino de selección en la ventana de consola JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Con la consola, puede interactuar con un único `WebView`, `iFrame`, contrato de participación o trabajo web a la vez. Cada elemento necesita una instancia independiente del host de plataforma web (WWAHost.exe). Puede interactuar con un host a la vez.  
  
6.  Ver y modificar las variables de la aplicación o usar los comandos de consola, como se describe en [inicio rápido: depurar JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) y [JavaScript Console commands](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Vea también  
 [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md)



