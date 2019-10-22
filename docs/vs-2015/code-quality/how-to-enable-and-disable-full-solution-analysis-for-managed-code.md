---
title: 'Cómo: habilitar y deshabilitar el análisis de la solución completa para código administrado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646289"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Cómo: habilitar y deshabilitar el análisis de la solución completa para código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Este tema solo se aplica a Visual Studio 2015 Update 3 RC y versiones posteriores.

 El *análisis completo* de la solución es una característica de Visual Studio que le permite elegir si ve problemas de análisis de código C# solo en archivos visuales o Visual Basic abiertos en la solución, o en archivos C# Visual Basic visuales abiertos y cerrados en el solución.

 Aunque ser capaz de ver todos los problemas de todos los archivos es útil, puede resultar molesto e incluso ralentizar Visual Studio si la solución es muy grande o tiene muchos archivos.  Para limitar el número de problemas que se muestran y mejorar el rendimiento de Visual Studio, puede deshabilitar el análisis completo de la solución. Puede volver a habilitar fácilmente esta característica si lo desea.

#### <a name="to-toggle-full-solution-analysis"></a>Para alternar el análisis completo de la solución

1. En el menú principal de Visual Studio, elija **herramientas** &#124; **Opciones** para ver el cuadro de diálogo **Opciones** .

2. En el cuadro de diálogo **Opciones** , **Elija editor** &#124; **C#** de texto o **básico** &#124; **avanzado**.

3. Active la casilla habilitar el análisis de la **solución completa** para habilitar el análisis completo de la solución o desactive la casilla para deshabilitarlo. Elija el botón **Aceptar** cuando haya terminado.

     ![Active la casilla de verificación Análisis completo de la solución.](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Resultados de habilitar y deshabilitar el análisis completo de la solución
 En la siguiente captura de pantalla, puede ver los resultados cuando se habilita el análisis completo de la solución. Aparecen todos los errores y los problemas de análisis de código en *todos* los archivos de la solución, independientemente de si los archivos están abiertos o no.

 ![Análisis completo de la solución habilitada.](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 En la captura de pantalla siguiente se muestran los resultados de la misma solución después de deshabilitar el análisis completo de la solución. En el Lista de errores solo aparecen los errores y los problemas de análisis de código en los archivos de la solución abierta.

 ![Análisis completo de la solución deshabilitado.](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Deshabilitar automáticamente el análisis completo de la solución
 Si Visual Studio detecta que 200 MB o menos memoria del sistema está disponible, deshabilita automáticamente el análisis completo de la solución (así como otras características) si está habilitado. Si esto ocurre, aparecerá una alerta que le informa de esto. Un botón le permite volver a habilitar el análisis completo de la solución si desea hacerlo.

 ![Texto de alerta que suspende el análisis completo de la solución](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>Detalles adicionales
 De forma predeterminada, el análisis completo de la solución está habilitado para C#Visual Basic y deshabilitado para visual.

 Visual Studio Update 3 RC incluye un motor mejorado de diagnóstico de analizador de código v2 que reduce significativamente el uso de memoria y reduce el tiempo de CPU al estado de inactividad, incluso si está habilitado el análisis completo de la solución.
