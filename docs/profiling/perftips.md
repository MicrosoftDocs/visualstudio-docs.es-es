---
title: Sugerencias de rendimiento | Microsoft Docs
description: Obtenga información sobre cómo usar las sugerencias de rendimiento y las Herramientas de diagnóstico integradas del depurador de Visual Studio para supervisar y analizar el rendimiento de la aplicación durante la depuración.
ms.date: 9/11/2020
ms.topic: how-to
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 73d6558264bb51f011d8f04b5a3096e95702c49b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892351"
---
# <a name="perftips"></a>Sugerencias de rendimiento

Los *PerfTips* del depurador de Visual Studio y las **Herramientas de diagnóstico** integradas del depurador le ayudan a supervisar y analizar el rendimiento de la aplicación durante la depuración.

Aunque las herramientas de diagnóstico integradas del depurador son una excelente manera de conocer los problemas de rendimiento durante el desarrollo, el depurador puede afectar de manera significativa al rendimiento de la aplicación. Para recopilar datos de rendimiento más precisos, considere la posibilidad de usar las herramientas del Generador de perfiles de rendimiento como parte adicional de las investigaciones de rendimiento. Vea [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>Sugerencias de rendimiento

Cuando el depurador detiene la ejecución en un punto de interrupción o en una operación de ejecución paso a paso, el tiempo transcurrido entre la interrupción y el punto de interrupción anterior aparece como una sugerencia en la ventana del editor. Para obtener más información, vea [PerfTips: Información de rendimiento de un solo vistazo mientras se realiza la depuración con Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Ventana Herramientas de diagnóstico

Los puntos de interrupción y datos de tiempo asociados se registran en la ventana **Herramientas de diagnóstico**.

En la ilustración siguiente se muestra la ventana **Herramientas de diagnóstico**.

![Captura de pantalla de la ventana Herramientas de diagnóstico en el depurador de Visual Studio, en la que se muestra la escala de tiempo y los gráficos del uso de memoria y de CPU.](../profiling/media/diagnostictools-update1.png)

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

- [Generación de perfiles en Visual Studio](../profiling/index.yml)
- [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)
