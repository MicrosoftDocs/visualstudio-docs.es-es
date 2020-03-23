---
title: Habilite & deshabilitar el análisis completo de soluciones para código administrado
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
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428192"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Cómo: Habilitar y deshabilitar el análisis completo de soluciones para código administrado

*El análisis completo* de la solución significa que el análisis de código examina todos los archivos de C o Visual Basic de la solución, independientemente de si están abiertos en el editor o no. De forma predeterminada, el análisis completo de la solución está *habilitado* para Visual Basic y *deshabilitado* para C.

Puede ser útil ver todos los problemas en todos los archivos, pero también puede ser una distracción. Ralentiza Visual Studio si la solución es muy grande o tiene muchos archivos. Para limitar el número de problemas mostrados y mejorar el rendimiento de Visual Studio, puede deshabilitar el análisis completo de la solución. Puede volver a habilitar fácilmente esta función si es necesario.

En la siguiente imagen, se habilita el análisis completo de la solución. Se muestran problemas del compilador y del análisis de código en todos los archivos de la solución, incluso si no están abiertos.

![Análisis completo de soluciones habilitado.](../code-quality/media/fsa_enabled.png)

La siguiente imagen muestra los resultados de la misma solución después de deshabilitar el análisis completo de la solución. Solo los errores del compilador y los problemas de análisis de código en los archivos de solución abiertos aparecen en la lista de errores.

![Análisis completo de la solución desactivado.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Alternar el análisis completo de la solución

1. Para abrir el cuadro de diálogo **Opciones,** en la barra de menús de Visual Studio, elija**Opciones** **de** > herramientas .

1. En el cuadro de diálogo **Opciones** , elija **Editor** > de**texto C o** **Basic** > **Advanced**.

1. Active la casilla **Habilitar análisis completo** de soluciones para habilitar el análisis completo de la solución o desactive la casilla para deshabilitarlo. Elija **OK** cuando haya terminado.

   ![Active la casilla de verificación Análisis completo de la solución.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Deshabilitar automáticamente el análisis completo de la solución

Si Visual Studio detecta que 200 MB o menos de memoria del sistema está disponible para él, deshabilita automáticamente el análisis completo de la solución (y algunas otras características) si está habilitado. Si esto ocurre, aparece una alerta que le informa de que Visual Studio ha deshabilitado algunas características. Un botón le permite volver a habilitar el análisis completo de la solución si lo desea.

![Texto de alerta que suspende el análisis completo de la solución](../code-quality/media/fsa_alert.png)
