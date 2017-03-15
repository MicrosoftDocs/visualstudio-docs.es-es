---
title: Sugerencias de rendimiento | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 6
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
ms.sourcegitcommit: 65bceca75b87aaf187926ebbed1a54ce4f0e8eec
ms.openlocfilehash: db7c9121beea3b6a27a435680dfe01cbc8cba8b6
ms.lasthandoff: 02/22/2017

---
# <a name="perftips"></a>Sugerencias de rendimiento
Los *PerfTips* del depurador de Visual Studio y las **Herramientas de diagnóstico** integradas del depurador le ayudan a supervisar y analizar el rendimiento de la aplicación durante la depuración.  
  
 Aunque las herramientas de diagnóstico integradas del depurador son una excelente manera de conocer los problemas de rendimiento durante el desarrollo, el depurador puede afectar de manera significativa al rendimiento de la aplicación. Para recopilar datos de rendimiento más precisos, considere la posibilidad de usar también las herramientas de diagnóstico de Visual Studio que se ejecutan fuera del depurador como parte de las investigaciones de rendimiento. Consulte [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).  
  
## <a name="perftips"></a>Sugerencias de rendimiento  
 Cuando el depurador detiene la ejecución en un punto de interrupción o en una operación de ejecución paso a paso, el tiempo transcurrido entre la interrupción y el punto de interrupción anterior aparece como una sugerencia en la ventana del editor. Para obtener más información, vea [PerfTips: Performance Information at-a-glance while Debugging with Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx).  
  
 ![Sugerencia de rendimiento](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Ventana Herramientas de diagnóstico  
 Los puntos de interrupción y datos de tiempo asociados se registran en la ventana Herramientas de diagnóstico.  
  
 En el gráfico siguiente se muestra la ventana de Herramientas de diagnóstico en Visual Studio 2015 Update 1:  
  
 ![DiagnosticTools Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
-   La escala de tiempo **Eventos de interrupción** marca los puntos de interrupción que se alcanzaron en la sesión de depuración. Haga clic en un evento para seleccionarlo en la lista de detalles del **Depurador** .  
  
-   El gráfico **Uso de CPU** muestra el cambio en el uso de CPU en todos los núcleos de procesador en la sesión de depuración.  
  
-   La lista **Eventos** del panel de detalles **Depurador** incluye elementos para cada evento de interrupción.  
  
-   La columna **Duración** de un evento de interrupción muestra el tiempo transcurrido entre el evento y el punto de interrupción anterior.  
  
## <a name="turn-perftips-on-or-off"></a>Activar o desactivar las sugerencias de rendimiento  
 Para habilitar o deshabilitar las sugerencias de rendimiento:  
  
1.  En el menú **Depurar** , elija **Opciones**.  
  
2.  Active o desactive **Mostrar la sugerencia de rendimiento transcurrida durante la depuración**.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Activar o desactivar la ventana Herramientas de diagnóstico  
 Para habilitar o deshabilitar la ventana Herramientas de diagnóstico:  
  
1.  En el menú **Depurar** , elija **Opciones**.  
  
2.  Active o desactive **Habilitar herramientas de diagnóstico durante la depuración**.
