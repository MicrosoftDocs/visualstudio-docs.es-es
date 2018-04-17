---
title: "' S New para que el depurador de Visual Studio de 2017 | Documentos de Microsoft"
ms.custom: ''
ms.date: 03/07/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0bcd44da88279f042469356a97bce7f369e1190
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>' S New para que el depurador en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

El depurador incluye estas nuevas características:

- Nuevo en 15,5, el **depurador instantánea** toma una instantánea de las aplicaciones de producción cuando se ejecuta código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

    La colección de instantáneas está disponible para las siguientes aplicaciones web que se ejecutan en Azure App Service:

    * Aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
    * Aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.

    Para obtener más información, consulte [depurar aplicaciones ASP.NET en directo con el depurador de instantánea](../debugger/debug-live-azure-applications.md).

- Nuevo en 15,5 en Visual Studio Enterprise, **IntelliTrace paso-back** automáticamente toma una instantánea de la aplicación en cada punto de interrupción y el depurador de evento de paso. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

    Para poder navegar y ver las instantáneas, use los botones **Retroceder paso a paso** y **Avanzar paso a paso** en la barra de herramientas de depuración. Estos botones permiten navegar por los eventos que aparecen en la pestaña **Eventos** en la ventana **Herramientas de diagnóstico**.

    ![Paso hacia atrás y hacia delante botones](../debugger/media/intellitrace-step-back-icons-description.png  "botones paso hacia atrás y hacia delante")

    Para más información, consulte la página [Visualización de instantáneas mediante step-back de IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md).

- El **aplicación auxiliar de excepciones** reemplaza el Asistente de excepciones y aparece en un cuadro de diálogo no modal donde se produjo el error. El **aplicación auxiliar de excepciones** proporciona un acceso más rápido a las excepciones internas, el análisis adicional por el depurador (si está disponible) y un acceso inmediato a la **configuración de excepciones** para la excepción. También se puede arrastrar la aplicación auxiliar de excepciones a una vista flotante si está bloqueando algo que necesita ver.

    Por ejemplo, un **NullReferenceException** ahora muestra la variable que tiene la referencia nula (información adicional).

    ![Aplicación auxiliar de excepciones del depurador](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Para obtener más información, vea la publicación del blog [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Usar la nueva aplicación auxiliar de excepciones en Visual Studio).

- Ahora puede ejecutar una línea de código mientras está en pausa en el depurador seleccionando la **ejecutar aquí** icono de flecha verde (para que aparezca el icono al mantener el mouse sobre una línea de código). Esto elimina la necesidad de establecer puntos de interrupción temporales.

    ![Depurador de ejecutarse, haga clic en](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

- Puede establecer condiciones en las excepciones producidas en el **configuración de excepciones** cuadro de diálogo (puede hacerlo mediante el uso de la **Editar condición** icono en el cuadro de diálogo de configuración de excepciones o mediante el menú contextual en el excepción.) Entre las condiciones actualmente compatibles se incluyen los nombres de módulo para incluir o excluir de la excepción.

    ![Las condiciones de una excepción](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Asociar al proceso de cuadro de diálogo incluye una nueva característica de búsqueda que puede ayudarle a identificar rápidamente el proceso que necesita para conectar a.

    ![Búsqueda en asociar al proceso](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch") 

Para obtener más información sobre estas nuevas características, consulte la [notas de versión [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)