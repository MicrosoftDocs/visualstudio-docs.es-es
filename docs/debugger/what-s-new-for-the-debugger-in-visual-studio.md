---
title: Novedades del depurador de Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
description: Vea las nuevas característica de la versión 15.5 del depurador. Se incluyen instantáneas del código seleccionado de las aplicaciones en producción y la característica Retroceder de IntelliTrace.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: bac5c7021146a0b9bc66e98e7de334bdbf05a7b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883953"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Novedades del depurador de Visual Studio 2017

El depurador incluye estas nuevas características:

- Novedad de la versión 15.5: el **Depurador de instantáneas** toma una instantánea de las aplicaciones en producción cuando se ejecuta el código que le interesa. Para indicar al depurador que tome una instantánea, establezca puntos de acoplamiento y puntos de registro en el código. El depurador le permite ver exactamente qué salió mal, sin afectar el tráfico de la aplicación de producción. El Depurador de instantáneas puede permitirle disminuir considerablemente el tiempo que tarda en resolver los problemas que se producen en los entornos de producción.

    La colección de instantáneas está disponible para las siguientes aplicaciones web que se ejecutan en Azure App Service:

  * Aplicaciones ASP.NET que se ejecutan en .NET Framework 4.6.1 o versiones posteriores.
  * Aplicaciones ASP.NET Core que se ejecutan en .NET Core 2.0 o posteriores en Windows.

    Para obtener más información, vea [Depurar aplicaciones de ASP.NET Azure activas con el depurador de instantáneas](../debugger/debug-live-azure-applications.md).

- Novedad de la versión 15.5 solo en Visual Studio Enterprise: la característica **Retroceder de IntelliTrace** toma automáticamente una instantánea de la aplicación en cada punto de interrupción y evento de paso del depurador. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

    Para poder navegar y ver las instantáneas, use los botones **Retroceder paso a paso** y **Avanzar paso a paso** en la barra de herramientas de depuración. Estos botones permiten navegar por los eventos que aparecen en la pestaña **Eventos** en la ventana **Herramientas de diagnóstico**.

    ![Botones Retroceder paso a paso y Avanzar paso a paso](../debugger/media/intellitrace-step-back-icons-description.png  "Botones Retroceder paso a paso y Avanzar paso a paso")

    Para obtener más información, vea la página [Inspeccionar el estado de aplicación anterior mediante step-back de IntelliTrace en Visual Studio](view-historical-application-state.md).

- La **Aplicación auxiliar de excepciones** reemplaza al Asistente de excepciones y aparece en un cuadro de diálogo no modal en el que se produjo el error. La **Aplicación auxiliar de excepciones** proporciona un acceso más rápido a cualquier excepción interna, un análisis adicional por parte del depurador (si está disponible) y el acceso inmediato a la **configuración de excepciones** para la excepción. También se puede arrastrar la Aplicación auxiliar de excepciones a una vista flotante si está bloqueando algo que necesite ver.

    Por ejemplo, **NullReferenceException** ahora muestra la variable que tiene la referencia nula (información adicional).

    ![Aplicación auxiliar de excepciones del depurador](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Para obtener más información, vea la publicación del blog [Using the New Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) (Usar el nuevo asistente de excepciones en Visual Studio).

- Ahora puede ejecutar una línea de código mientras se encuentra en pausa en el depurador; para ello, seleccione el icono de flecha verde **Ejecutar hasta aquí** (verá el icono mientras mantiene el puntero sobre una línea de código). Esto elimina la necesidad de establecer puntos de interrupción temporales.

    ![Ejecución hasta hacer clic del depurador](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Puede establecer condiciones en las excepciones en el cuadro de diálogo **Configuración de excepciones** (puede hacerlo mediante el icono **Editar condición** del cuadro de diálogo Configuración de excepciones o mediante el menú contextual en la excepción). Las condiciones admitidas actualmente incluyen los nombres de los módulos que se van a incluir o excluir para la excepción.

    ![Condiciones para una excepción](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- El cuadro de diálogo Asociar al proceso incluye una nueva característica de búsqueda que puede ayudarle a identificar con mayor rapidez el proceso al que debe asociarse.

    ![Buscar en Asociar al proceso](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Para más información sobre estas nuevas características, consulte las [notas de la versión de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)