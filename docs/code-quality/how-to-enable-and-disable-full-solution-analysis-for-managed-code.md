---
title: Habilitar & deshabilitar el análisis completo de la solución para código administrado
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587516"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Cómo: habilitar y deshabilitar el análisis de la solución completa para código administrado

El análisis de la *solución completa* significa que el análisis de C# código examina todos los archivos o Visual Basic de la solución, con independencia de si están abiertos en el editor o no. De forma predeterminada, el análisis completo de la solución está *habilitado* para Visual Basic y *deshabilitado* para C#.

Puede ser útil Ver todos los problemas de todos los archivos, pero también puede resultar molesto. Ralentiza Visual Studio si la solución es muy grande o tiene muchos archivos. Para limitar el número de problemas que se muestran y mejorar el rendimiento de Visual Studio, puede deshabilitar el análisis completo de la solución. Puede volver a habilitar fácilmente esta característica si es necesario.

En la imagen siguiente, se habilita el análisis completo de la solución. Se muestran los problemas del compilador y el análisis de código en todos los archivos de la solución, aunque no estén abiertos.

![Análisis completo de la solución habilitada.](../code-quality/media/fsa_enabled.png)

En la imagen siguiente se muestran los resultados de la misma solución después de deshabilitar el análisis completo de la solución. En el Lista de errores solo aparecen los errores del compilador y los problemas de análisis de código en los archivos de la solución abierta.

![Análisis completo de la solución deshabilitado.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Alternancia del análisis de la solución completa

1. Para abrir el cuadro de diálogo **Opciones** , en la barra de menús de Visual Studio, elija **herramientas** > **Opciones**.

1. En el cuadro de diálogo **Opciones** , **Elija Editor** de **C#** texto > o **básico** > **avanzado**.

1. Active la casilla habilitar el análisis de la **solución completa** para habilitar el análisis completo de la solución o desactive la casilla para deshabilitarlo. Elija **Aceptar** cuando haya terminado.

   ![Active la casilla de verificación Análisis completo de la solución.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Deshabilitar automáticamente el análisis completo de la solución

Si Visual Studio detecta que 200 MB o menos de memoria del sistema está disponible, deshabilita automáticamente el análisis completo de la solución (y otras características) si está habilitada. Si esto ocurre, aparecerá una alerta que le informa de que Visual Studio ha deshabilitado algunas características. Un botón le permite volver A habilitar el análisis completo de la solución si lo desea.

![Suspender el análisis de la solución completa de texto de alerta](../code-quality/media/fsa_alert.png)
