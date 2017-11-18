---
title: "Cómo: habilitar y deshabilitar el análisis de la solución completa para código administrado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 94cda949a713a773e5586e5b1ef284c6ba54839c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Cómo: habilitar y deshabilitar el análisis de la solución completa para código administrado
> [!NOTE]
>  En este tema se aplica solo a Visual Studio 2015 Update 3 RC y versiones posteriores.  
  
 *Completa el análisis de la solución* es una característica de Visual Studio que le permite elegir si ver los problemas de análisis de código solo en archivos abiertos de Visual C# o Visual Basic en la solución o en archivos de Visual C# o Visual Basic abiertos y cerrados en la solución.  
  
 Aunque es útil poder ver todos los problemas en todos los archivos, puede ser molesto y ralentizar incluso a Visual Studio si la solución es muy grande o tiene una gran cantidad de archivos.  Para limitar el número de problemas que se muestra y mejorar el rendimiento de Visual Studio, puede deshabilitar el análisis de la solución completa. Fácilmente puede volver a habilitar esta característica si desea.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Para activar o desactivar el análisis de la solución completa  
  
1.  En el menú principal en Visual Studio, elija **herramientas** &#124; **Opciones** para ver el **opciones** cuadro de diálogo.  
  
2.  En el **opciones** diálogo cuadro, elija **Editor de texto** &#124; **C#** o **básica** &#124; **Avanzadas**.  
  
3.  Seleccione el **Habilitar análisis de la solución completa** casilla de verificación para habilitar el análisis de la solución completa, o desactive la casilla para deshabilitarlo. Elija la **Aceptar** botón cuando haya terminado.  
  
     ![Habilitar la casilla de verificación de análisis de la solución completa. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Resultados de habilitar y deshabilitar el análisis de la solución completa  
 En la siguiente captura de pantalla, puede ver los resultados cuando se habilita el análisis de la solución completa. Todos los errores y problemas de análisis de código en *todos los* de los archivos de la solución aparecen, independientemente de si los archivos están abiertos.  
  
 ![Análisis de la solución completa habilitada. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")  
  
 Captura de pantalla siguiente muestra los resultados de la misma solución después de deshabilitar el análisis de la solución completa. Solo los errores y problemas de análisis de código en abren solución archivos aparecen en la lista de errores.  
  
 ![Análisis de la solución completa deshabilitado. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Deshabilitar automáticamente el análisis de la solución completa  
 Si Visual Studio detecta que 200MB o menos de memoria del sistema está disponible en él, deshabilita automáticamente análisis de la solución completa (así como otras características) si está habilitado. Si esto ocurre, aparece una alerta que le informa de este. Un botón le permite volver a habilitar el análisis de la solución completa si desea hacerlo.  
  
 ![Texto de alerta suspender el análisis de la solución completa](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Detalles adicionales  
 De forma predeterminada, los análisis de la solución completa se habilita para Visual Basic y se deshabilita para Visual C#.  
  
 Visual Studio Update 3 RC incluye un motor de diagnóstico v2 del analizador de código mejorada que reduce el uso de memoria significativamente y disminuye el tiempo de CPU inactiva, incluso si está habilitado el análisis de la solución completa.