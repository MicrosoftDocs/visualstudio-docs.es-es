---
title: "Novedades de la generación de perfiles | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 77e7ce26df70e41e2328442454fe78c7a663f1f3
ms.openlocfilehash: f93c61e084378cd702ea8f190e1661c03bbc9c51
ms.lasthandoff: 03/08/2017

---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Novedades de las herramientas de generación de perfiles en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
Las herramientas de diagnóstico incluyen nuevas visualizaciones para ayudarle a identificar problemas en la aplicación que se deben corregir. Las herramientas de diagnóstico ahora incluyen compatibilidad para aplicaciones de ASP.NET.

Para obtener más información, consulte las [Notas de la versión de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]] (https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).

Se ha agregado una pestaña **Resumen** a las herramientas que le ayudan a centrarse en áreas clave para el análisis de rendimiento. Esta pestaña muestra cuántos eventos se han producido, le permite tomar instantáneas del montón y le permite habilitar rápidamente la recopilación de datos de uso de CPU. Esta vista muestra cualquier evento de [Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) o de [Análisis de la interfaz de usuario](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis). Además, para Visual Studio Enterprise, esta vista también muestra los eventos de IntelliTrace.

![Pestaña Resumen de herramientas de diagnóstico de](~/docs/profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

La herramienta de uso de CPU tiene [nuevas visualizaciones](../profiling/Beginners-Guide-to-Performance-Profiling.md) para ayudarle a identificar las funciones que tienen más probabilidades de estar causando problemas de rendimiento. La nueva vista **Llamador y destinatario** que le permite investigar costos de las llamadas de funciones realizadas a y desde una función seleccionada.

![Herramientas de diagnóstico para la vista Llamador y destinatario](~/docs/profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")
  
## <a name="see-also"></a>Vea también  
 [Herramientas de generación de perfiles](../profiling/profiling-tools.md)
