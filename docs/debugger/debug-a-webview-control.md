---
title: Depuración de un control WebView (UWP) | Microsoft Docs
description: Obtenga información sobre cómo inspeccionar y depurar los controles WebView que se usan en una aplicación Windows Runtime. Puede usar el Explorador DOM y la ventana Consola de JavaScript.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 5439f9f253126e159df5dd9ea58bad04c3f6c649
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560556"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Depuración de un control WebView en una aplicación para UWP

 Para inspeccionar y depurar controles `WebView` en una aplicación de Windows en tiempo de ejecución, puede configurar Visual Studio de modo que adjunte el depurador de script al iniciar la aplicación. Tiene dos maneras de interactuar con los controles de `WebView` con el depurador:

- Abrir el [Explorador DOM](../debugger/quickstart-debug-html-and-css.md) de una instancia `WebView`, inspeccionar los elementos DOM, investigar los problemas de estilo CSS y probar los cambios presentados de forma dinámica de los estilos.

- Seleccionar la página web o `iFrame` mostrado en la instancia `WebView` como destino en la ventana [Consola JavaScript](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true) e interactuar con la página web mediante los comandos de la consola. La consola ofrece acceso al contexto de ejecución de script actual.

### <a name="attach-the-debugger-c-visual-basic-c"></a>Adjuntar el depurador (C#, Visual Basic, C++)

1. En Visual Studio, agregue un control `WebView` a la aplicación de Windows en tiempo de ejecución.

2. En el Explorador de soluciones, abra las propiedades del proyecto al elegir **Propiedades** en el menú contextual del proyecto.

3. Elija **Depurar**. En la lista **Proceso de aplicación**, elija **Script**.

     ![Adjuntar el depurador de scripts](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4. (Opcional) En las versiones de Visual Studio que no sean Express, deshabilite la depuración justo a tiempo (JIT) eligiendo **Herramientas, Opciones, Depuración, Just-In-Time** y deshabilitando a continuación la depuración JIT para Script.

    > [!NOTE]
    > Al deshabilitar la depuración JIT, puede ocultar los cuadros de diálogo de las excepciones no controladas que se producen en algunas páginas web. En Visual Studio Express, la depuración JIT siempre está deshabilitada.

5. Presiona F5 para iniciar la depuración.

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Usar el Explorador DOM para inspeccionar y depurar un control WebView

1. (C#, Visual Basic, C++) Adjunte el depurador de script a la aplicación. Consulte la primera sección para obtener instrucciones.

2. Si aún no lo ha hecho, agregue un control `WebView` a la aplicación y presione F5 para iniciar la depuración.

3. Vaya a la página que contiene el control o controles `Webview`.

4. Abra la ventana del Explorador DOM del control `WebView` al elegir **Depurar**, **Ventanas**, **Explorador DOM** y después elija la dirección URL del `WebView` que quiera inspeccionar.

     ![Abrir el Explorador DOM](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     El Explorador DOM asociado al control `WebView` aparece como una nueva pestaña en Visual Studio.

5. Vea y modifique los elementos DOM dinámicos y los estilos CSS, tal como se describe en [Depuración de estilos CSS mediante el Explorador DOM](quickstart-debug-html-and-css.md).

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Usar la ventana Consola JavaScript para inspeccionar y depurar un control WebView

1. (C#, Visual Basic, C++) Adjunte el depurador de script a la aplicación. Consulte la primera sección para obtener instrucciones.

2. Si aún no lo ha hecho, agregue un control `WebView` a la aplicación y presione F5 para iniciar la depuración.

3. Abra la ventana Consola JavaScript del control `WebView` al elegir **Depurar**, **Ventanas**, **Consola JavaScript**.

     Aparece la ventana Consola JavaScript.

4. Vaya a la página que contiene el control o controles `Webview`.

5. En la ventana Consola, seleccione la página web o un `iFrame` mostrado por el control `WebView` en la lista **Destino**.

     ![Selección de destino en la ventana de la Consola JavaScript](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    > Con la consola, puede interactuar con un único `WebView`, `iFrame`, contrato de participación o trabajo web a la vez. Cada elemento necesita una instancia independiente del host de plataforma web (WWAHost.exe). Puede interactuar con un host a la vez.

6. Visualice y modifique variables en la aplicación o use comandos de la consola, tal como se describe en [Inicio rápido: Depuración de JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) y [Comandos de la Consola JavaScript](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true).

## <a name="see-also"></a>Vea también

- [Inicio rápido: depuración de HTML y CSS](../debugger/quickstart-debug-html-and-css.md)