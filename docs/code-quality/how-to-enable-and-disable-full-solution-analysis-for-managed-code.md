---
title: Procedimiento Habilitar y deshabilitar el análisis de la solución completa para código administrado
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: dbd4cf06a5d51a668acc5c980e7e93a94f2992f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816477"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procedimiento Habilitar y deshabilitar el análisis de la solución completa para código administrado

*Completa el análisis de la solución* es una característica de Visual Studio que le permite ver los problemas de análisis de código solo en abierto Visual C# o los archivos de Visual Basic en la solución, o también en los archivos de código que se cierran. De forma predeterminada, es el análisis de la solución completa *habilitado* para Visual Basic, y *deshabilitado* Visual C#.

Puede ser útil ver todos los problemas en todos los archivos, pero también puede ser confuso. Ralentiza Visual Studio si la solución es muy grande o tiene muchos archivos. Para limitar el número de problemas que se muestran y mejorar el rendimiento de Visual Studio, puede deshabilitar el análisis de la solución completa. Fácilmente puede volver a habilitar esta característica si es necesario.

## <a name="to-toggle-full-solution-analysis"></a>Para activar o desactivar el análisis de la solución completa

1. Para abrir el **opciones** cuadro de diálogo, en la barra de menús de Visual Studio elija **herramientas** > **opciones**.

1. En el **opciones** diálogo cuadro, elija **Editor de texto**  >  **C#** o **básica**  >  **Avanzada**.

1. Seleccione el **Habilitar análisis de la solución completa** casilla de verificación para habilitar el análisis de la solución completa, o desactive la casilla para deshabilitarla. Elija **Aceptar** cuando haya terminado.

    ![Habilitar la casilla de verificación de análisis de solución completa.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Resultados de la habilitación y deshabilitación de análisis de la solución completa

En la siguiente captura de pantalla, puede ver los resultados cuando se habilita el análisis de la solución completa. Todos los errores y problemas de análisis de código en *todas* de los archivos de la solución aparecen, independientemente de si los archivos están abiertos.

![Análisis de la solución completa habilitada.](../code-quality/media/fsa_enabled.png)

Captura de pantalla siguiente muestra los resultados de la misma solución después de deshabilitar el análisis de la solución completa. Solo los errores y problemas de análisis de código en archivos de solución abierta aparecen en la **lista de errores**.

![Análisis de la solución completa deshabilitado.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Deshabilitar automáticamente el análisis de la solución completa

Si Visual Studio detecta que 200 MB o menos de memoria del sistema está disponible en él, deshabilita automáticamente análisis completo de la solución (y algunas otras características) si está habilitado. Si esto ocurre, aparece una alerta que le informa de que Visual Studio ha deshabilitado algunas características. Un botón le permite volver a habilitar el análisis de la solución completa si desea.

![Suspender el análisis de la solución completa de texto de alerta](../code-quality/media/fsa_alert.png)