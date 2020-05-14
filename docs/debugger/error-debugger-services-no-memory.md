---
title: Servicios del depurador que se quedan sin memoria | Microsoft Docs
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737840"
---
# <a name="debugger-services-running-out-of-memory"></a>Servicios del depurador que se quedan sin memoria
El servicio de depuración se quedó sin memoria y causó la finalización de la sesión de depuración.

## <a name="to-investigate-this-error-on-windows"></a>Para investigar este error en Windows
- Puede comprobar el gráfico de memoria del proceso en la ventana **Herramientas de diagnóstico** para ver si la aplicación de destino está experimentando un gran crecimiento en la memoria. Si es así, use la herramienta **Uso de la memoria** para diagnosticar cuál es el problema subyacente; vea [Analizar el uso de memoria](../profiling/memory-usage.md).

- Si la aplicación de destino no parece estar consumiendo mucha memoria, use la ventana **Administrador de tareas** para consultar el uso de la memoria de Visual Studio (devenv.exe), el proceso de trabajo (msvsmon.exe) o VS Code (vsdbg.exe/vsdbg-ui.exe), para determinar si se trata de un problema del depurador. Si el proceso que se está quedando sin memoria es devenv.exe, considere la posibilidad de reducir el número de extensiones de Visual Studio en ejecución.

## <a name="see-also"></a>Vea también
- [Entrada de blog: Análisis de la CPU y la memoria durante la depuración](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Acerca de la administración de memoria](/windows/win32/memory/about-memory-management)
