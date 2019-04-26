---
title: Sugerencias de rendimiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0713ae13038991ec65dcbebe350c9085f7d6a94a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797945"
---
# <a name="perftips"></a>Sugerencias de rendimiento
Los *PerfTips* del depurador de Visual Studio y las **Herramientas de diagnóstico** integradas del depurador le ayudan a supervisar y analizar el rendimiento de la aplicación durante la depuración.

 Aunque las herramientas de diagnóstico integradas del depurador son una excelente manera de conocer los problemas de rendimiento durante el desarrollo, el depurador puede afectar de manera significativa al rendimiento de la aplicación. Para recopilar datos de rendimiento más precisos, considere la posibilidad de usar también las herramientas de diagnóstico de Visual Studio que se ejecutan fuera del depurador como parte de las investigaciones de rendimiento. Vea [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>Sugerencias de rendimiento
 Cuando el depurador detiene la ejecución en un punto de interrupción o en una operación de ejecución paso a paso, el tiempo transcurrido entre la interrupción y el punto de interrupción anterior aparece como una sugerencia en la ventana del editor. Para obtener más información, vea [PerfTips: Información de rendimiento de un solo vistazo mientras se realiza la depuración con Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

 ![Sugerencia de rendimiento](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Ventana Herramientas de diagnóstico
 Los puntos de interrupción y datos de tiempo asociados se registran en la ventana **Herramientas de diagnóstico**.

 En el gráfico siguiente se muestra la ventana de **Herramientas de diagnóstico** en Visual Studio 2015 Update 1:

 ![DiagnosticTools Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

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

## <a name="see-also"></a>Vea también
- [Generación de perfiles en Visual Studio](../profiling/index.md)
- [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)
