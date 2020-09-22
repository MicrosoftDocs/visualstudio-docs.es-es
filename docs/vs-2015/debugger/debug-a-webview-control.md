---
title: Depurar un control WebView | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f2da5b3122bd97fcbef0db7124049372c21983f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842974"
---
# <a name="debug-a-webview-control"></a>Depurar un control WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Para inspeccionar y depurar controles `WebView` en una aplicación de Windows en tiempo de ejecución, puede configurar Visual Studio de modo que adjunte el depurador de script al iniciar la aplicación. A partir de Visual Studio 2013 Update 2, tiene dos formas de interactuar con los controles `WebView` mediante el depurador:  
  
- Abrir el [Explorador DOM](../debugger/quickstart-debug-html-and-css.md) de una instancia `WebView`, inspeccionar los elementos DOM, investigar los problemas de estilo CSS y probar los cambios presentados de forma dinámica de los estilos.  
  
- Seleccionar la página web o `iFrame` mostrado en la instancia `WebView` como destino en la ventana [Consola JavaScript](../debugger/javascript-console-commands.md) e interactuar con la página web mediante los comandos de la consola. La consola ofrece acceso al contexto de ejecución de script actual.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Adjuntar el depurador (C#, Visual Basic, C++)  
  
1. En Visual Studio, agregue un control `WebView` a la aplicación de Windows en tiempo de ejecución.  
  
2. En el Explorador de soluciones, abra las propiedades del proyecto al elegir **Propiedades** en el menú contextual del proyecto.  
  
3. Elija **Depurar**. En la lista **Proceso de aplicación**, elija **Script**.  
  
     ![Adjuntar el depurador de scripts](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4. Opta En el caso de las versiones no Express de Visual Studio, deshabilite la depuración Just-in-Time (JIT) eligiendo **herramientas**, **Opciones**, **depuración**, **Just-in-Time**y deshabilitando la depuración JIT para el script.  
  
    > [!NOTE]
    > Al deshabilitar la depuración JIT, puede ocultar los cuadros de diálogo de las excepciones no controladas que se producen en algunas páginas web. En Visual Studio Express, la depuración JIT siempre está deshabilitada.  
  
5. Presiona F5 para iniciar la depuración.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Usar el Explorador DOM para inspeccionar y depurar un control WebView  
  
1. (C#, Visual Basic, C++) Adjunte el depurador de script a la aplicación. Consulte la primera sección para obtener instrucciones.  
  
2. Si aún no lo ha hecho, agregue un control `WebView` a la aplicación y presione F5 para iniciar la depuración.  
  
3. Vaya a la página que contiene el control o controles `Webview`.  
  
4. Abra la ventana del Explorador DOM del control `WebView` al elegir **Depurar**, **Ventanas**, **Explorador DOM** y después elija la dirección URL del `WebView` que quiera inspeccionar.  
  
     ![Abrir el Explorador DOM](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     El Explorador DOM asociado al control `WebView` aparece como una nueva pestaña en Visual Studio.  
  
5. Vea y modifique los elementos DOM dinámicos y los estilos CSS, tal como se describe en [Depuración de estilos CSS mediante el Explorador DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Usar la ventana Consola JavaScript para inspeccionar y depurar un control WebView  
  
1. (C#, Visual Basic, C++) Adjunte el depurador de script a la aplicación. Consulte la primera sección para obtener instrucciones.  
  
2. Si aún no lo ha hecho, agregue un control `WebView` a la aplicación y presione F5 para iniciar la depuración.  
  
3. Abra la ventana Consola JavaScript del control `WebView` al elegir **Depurar**, **Ventanas**, **Consola JavaScript**.  
  
     Aparece la ventana Consola JavaScript.  
  
4. Vaya a la página que contiene el control o controles `Webview`.  
  
5. En la ventana Consola, seleccione la página web o un `iFrame` mostrado por el control `WebView` en la lista **Destino**.  
  
     ![Selección de destino en la ventana de la Consola JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    > Con la consola, puede interactuar con un único `WebView`, `iFrame`, contrato de participación o trabajo web a la vez. Cada elemento necesita una instancia independiente del host de plataforma web (WWAHost.exe). Puede interactuar con un host a la vez.  
  
6. Visualice y modifique variables en la aplicación o use comandos de la consola, tal como se describe en [Inicio rápido: Depuración de JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) y [Comandos de la Consola JavaScript](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Consulte también  
 [Inicio rápido: depuración de HTML y CSS](../debugger/quickstart-debug-html-and-css.md)
