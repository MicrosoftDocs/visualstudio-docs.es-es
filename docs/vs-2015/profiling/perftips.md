---
title: Sugerencias de rendimiento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa56b6731e359db486a111194a710069d41a2f1b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295872"
---
# <a name="perftips"></a>Sugerencias de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los *PerfTips* del depurador de Visual Studio y las **Herramientas de diagnóstico** integradas del depurador le ayudan a supervisar y analizar el rendimiento de la aplicación durante la depuración.  
  
 Aunque las herramientas de diagnóstico integradas del depurador son una excelente manera de conocer los problemas de rendimiento durante el desarrollo, el depurador puede afectar de manera significativa al rendimiento de la aplicación. Para recopilar datos de rendimiento más precisos, considere la posibilidad de usar también las herramientas de diagnóstico de Visual Studio que se ejecutan fuera del depurador como parte de las investigaciones de rendimiento. See [Run profiling tools without debugging](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
## <a name="perftips"></a>Sugerencias de rendimiento  
 Cuando el depurador detiene la ejecución en un punto de interrupción o en una operación de ejecución paso a paso, el tiempo transcurrido entre la interrupción y el punto de interrupción anterior aparece como una sugerencia en la ventana del editor. Para obtener más información, vea [PerfTips: Performance Information at-a-glance while Debugging with Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).  
  
 ![PerfTip](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Ventana Herramientas de diagnóstico  
 Los puntos de interrupción y datos de tiempo asociados se registran en la ventana Herramientas de diagnóstico.  
  
 En el gráfico siguiente se muestra la ventana de Herramientas de diagnóstico en Visual Studio 2015 Update 1:  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
- La escala de tiempo **Eventos de interrupción** marca los puntos de interrupción que se alcanzaron en la sesión de depuración. Haga clic en un evento para seleccionarlo en la lista de detalles del **Depurador** .  
  
- El gráfico **Uso de CPU** muestra el cambio en el uso de CPU en todos los núcleos de procesador en la sesión de depuración.  
  
- La lista **Eventos** del panel de detalles **Depurador** incluye elementos para cada evento de interrupción.  
  
- La columna **Duración** de un evento de interrupción muestra el tiempo transcurrido entre el evento y el punto de interrupción anterior.  
  
## <a name="turn-perftips-on-or-off"></a>Activar o desactivar las sugerencias de rendimiento  
 Para habilitar o deshabilitar las sugerencias de rendimiento:  
  
1. En el menú **Depurar** , elija **Opciones**.  
  
2. Active o desactive **Mostrar la sugerencia de rendimiento transcurrida durante la depuración**.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Activar o desactivar la ventana Herramientas de diagnóstico  
 Para habilitar o deshabilitar la ventana Herramientas de diagnóstico:  
  
1. En el menú **Depurar** , elija **Opciones**.  
  
2. Active o desactive **Habilitar herramientas de diagnóstico durante la depuración**.
