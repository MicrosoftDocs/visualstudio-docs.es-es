---
title: "Novedades de la generación de perfiles | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bf15a647c2dcd3f99afd476607fcdf48c2865a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Novedades de las herramientas de generación de perfiles en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
Las herramientas de diagnóstico incluyen nuevas visualizaciones para ayudarle a identificar problemas en la aplicación que se deben corregir. Las herramientas de diagnóstico ahora incluyen compatibilidad para aplicaciones de ASP.NET.

Para obtener más información, vea las [notas de la versión para [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).

Se ha agregado una pestaña **Resumen** a las herramientas que le ayudan a centrarse en áreas clave para el análisis de rendimiento. Esta pestaña muestra cuántos eventos se han producido, le permite tomar instantáneas del montón y le permite habilitar rápidamente la recopilación de datos de uso de CPU. Esta vista muestra cualquier evento de [Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) o de [Análisis de la interfaz de usuario](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis). Además, para Visual Studio Enterprise, esta vista también muestra los eventos de IntelliTrace.

![Pestaña Resumen de herramientas de diagnóstico de](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

La herramienta de uso de CPU tiene [nuevas visualizaciones](../profiling/Beginners-Guide-to-Performance-Profiling.md) para ayudarle a identificar las funciones que tienen más probabilidades de estar causando problemas de rendimiento. La nueva vista **Llamador y destinatario** que le permite investigar costos de las llamadas de funciones realizadas a y desde una función seleccionada.

![Herramientas de diagnóstico para la vista Llamador y destinatario](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")
  
## <a name="see-also"></a>Vea también  
 [Generación de perfiles en Visual Studio](../profiling/index.md)  
 [Guía de características de generación de perfiles](../profiling/profiling-feature-tour.md)