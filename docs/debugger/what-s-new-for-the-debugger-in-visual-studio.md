---
title: Novedades del depurador de Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
ms.date: 01/22/2018
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
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 9c6f2eb4be56be8cf5e25c3238a91819df3bc574
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901408"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Novedades del depurador de Visual Studio 2017

El depurador incluye estas nuevas características:

- Novedades de la versión 15.5, el **Snapshot Debugger** toma una instantánea de sus aplicaciones en producción cuando se ejecuta el código que le interesen. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

    La colección de instantáneas está disponible para las siguientes aplicaciones web que se ejecutan en Azure App Service:

  * Aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
  * Aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.

    Para obtener más información, vea [Depurar aplicaciones de ASP.NET Azure activas con el depurador de instantáneas](../debugger/debug-live-azure-applications.md).

- Novedades de la versión 15.5 de Visual Studio Enterprise solo, **step-back de IntelliTrace** automáticamente toma una instantánea de la aplicación en cada punto de interrupción y el depurador de evento de paso. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

    Para poder navegar y ver las instantáneas, use los botones **Retroceder paso a paso** y **Avanzar paso a paso** en la barra de herramientas de depuración. Estos botones permiten navegar por los eventos que aparecen en la pestaña **Eventos** en la ventana **Herramientas de diagnóstico**.

    ![Botones Retroceder paso a paso y Avanzar paso a paso](../debugger/media/intellitrace-step-back-icons-description.png  "Step Backward and Forward buttons")

    Para obtener más información, vea la página [Inspeccionar el estado de aplicación anterior mediante step-back de IntelliTrace en Visual Studio](../debugger/view-historical-application-state.md).

- El **aplicación auxiliar de excepciones** reemplaza el Asistente de excepciones y aparece en un cuadro de diálogo no modal donde se produjo el error. El **aplicación auxiliar de excepciones** proporciona un acceso más rápido a las excepciones internas, análisis adicionales por el depurador (si está disponible) y acceso inmediato a la **configuración de excepciones** para la excepción. También se pueden arrastrar a la aplicación auxiliar de excepciones a una vista flotante si está bloqueando algo que necesita para ver.

    Por ejemplo, un **NullReferenceException** muestra ahora la variable que tiene la referencia nula (información adicional).

    ![Aplicación auxiliar de excepciones del depurador](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Para obtener más información, vea la publicación del blog [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Usar el nuevo asistente de excepciones en Visual Studio).

- Ahora puede ejecutar en una línea de código mientras está en pausa en el depurador seleccionando el **ejecutar hasta aquí** icono de flecha verde (verá el icono al mantener el mouse sobre una línea de código). Esto elimina la necesidad de establecer puntos de interrupción temporales.

    ![Depurador de ejecución, haga clic en](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Puede establecer condiciones en las excepciones en el **configuración de excepciones** cuadro de diálogo (puede hacerlo mediante el uso de la **Editar condición** icono en el cuadro de diálogo Configuración de excepciones o mediante el menú contextual en el excepción.) Las condiciones admitidas actualmente incluyen los nombres de módulo para incluir o excluir de la excepción.

    ![Las condiciones de una excepción](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Adjuntar al cuadro de diálogo incluye una nueva característica de búsqueda que puede ayudarle a identificar rápidamente el proceso que se debe adjuntar a proceso.

    ![Búsqueda en asociar al proceso](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Para obtener más información sobre estas nuevas características, consulte el [notas de la versión [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.md)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)