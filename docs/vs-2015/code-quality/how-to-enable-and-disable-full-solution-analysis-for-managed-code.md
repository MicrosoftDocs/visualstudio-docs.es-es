---
title: Filtrar Habilitar y deshabilitar el análisis de la solución completa para código administrado | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b9efdb5ea3e7ccbee9aefb724e847db6a37c2a0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987211"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Filtrar Habilitar y deshabilitar el análisis de la solución completa para código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  En este tema se aplica solo a Visual Studio 2015 Update 3 RC y versiones posteriores.  
  
 *Completa el análisis de la solución* es una característica de Visual Studio que le permite elegir si ve que los problemas de análisis de código solo en archivos abiertos de Visual C# o Visual Basic en la solución o en archivos de Visual C# o Visual Basic abiertos y cerrados en su solución.  
  
 Aunque resulta útil poder ver todos los problemas en todos los archivos, puede ser confuso y ralentizan incluso a Visual Studio si la solución es muy grande o tiene una gran cantidad de archivos.  Para limitar el número de problemas que se muestran y mejorar el rendimiento de Visual Studio, puede deshabilitar el análisis de la solución completa. Fácilmente puede volver a habilitar esta característica si desea.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Para activar o desactivar el análisis de la solución completa  
  
1.  En el menú principal de Visual Studio, elija **herramientas** &#124; **opciones** para ver el **opciones** cuadro de diálogo.  
  
2.  En el **opciones** diálogo cuadro, elija **Editor de texto** &#124; **C#** o **básica** &#124; **avanzadas**.  
  
3.  Seleccione el **Habilitar análisis de la solución completa** casilla de verificación para habilitar el análisis de la solución completa, o desactive la casilla para deshabilitarla. Elija la **Aceptar** cuando haya terminado.  
  
     ![Habilitar la casilla de verificación de análisis de solución completa. ](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Resultados de la habilitación y deshabilitación de análisis de la solución completa  
 En la siguiente captura de pantalla, puede ver los resultados cuando se habilita el análisis de la solución completa. Todos los errores y problemas de análisis de código en *todas* de los archivos de la solución aparecen, independientemente de si los archivos están abiertos.  
  
 ![Análisis de la solución completa habilitada. ](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 Captura de pantalla siguiente muestra los resultados de la misma solución después de deshabilitar el análisis de la solución completa. Solo los errores y problemas de análisis de código en abren solución archivos aparecen en la lista de errores.  
  
 ![Análisis de la solución completa deshabilitado. ](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Deshabilitar automáticamente el análisis de la solución completa  
 Si Visual Studio detecta que 200MB o menos de memoria del sistema está disponible en él, deshabilita automáticamente análisis completo de la solución (así como algunas otras características) si está habilitado. Si esto ocurre, aparece una alerta que le informa de este. Un botón le permite volver a habilitar el análisis de la solución completa si desea hacerlo.  
  
 ![Suspender el análisis de la solución completa de texto de alerta](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Detalles adicionales  
 De forma predeterminada, análisis de la solución completa está habilitado para Visual Basic y deshabilitado para Visual C#.  
  
 Visual Studio Update 3 RC incluye un motor de diagnóstico v2 de analizador de código mejorada que reduce el uso de memoria significativamente y reduce el tiempo de CPU en inactividad, incluso si está habilitado el análisis de la solución completa.
