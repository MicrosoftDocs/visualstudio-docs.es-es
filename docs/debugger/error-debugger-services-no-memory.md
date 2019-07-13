---
title: Servicios que se está quedando sin memoria del depurador | Microsoft Docs
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
ms.openlocfilehash: 05664ffd056f69215e6fb00d6d49a59382a3692f
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "67854022"
---
# <a name="debugger-services-running-out-of-memory"></a>Servicios que se está quedando sin memoria del depurador
Los servicios de depuración se quedó sin memoria y ha provocado la finalización de la sesión de depuración.

## <a name="to-investigate-this-error-on-windows"></a>Para investigar este error en Windows
- Puede comprobar el gráfico de memoria de proceso el **herramientas de diagnóstico** ventana para ver si la aplicación de destino está experimentando un enorme crecimiento en la memoria. Si es así, use el **uso de memoria** herramienta para diagnosticar lo que es el problema subyacente, vea [analizar el uso de memoria](../profiling/memory-usage.md).

- Si la aplicación de destino no parece estar consumiendo demasiada memoria, use el **el Administrador de tareas** ventana para comprobar el uso de memoria de Visual Studio (devenv.exe), el proceso de trabajo (msvsmon.exe), o de VS Code (vsdbg.exe/vsdbg-ui.exe) para determinar si se trata de un problema de depurador. Si el proceso que se está quedando sin memoria es devenv.exe, considere la posibilidad de reducir el número de extensiones de Visual Studio que se ejecutan.

## <a name="see-also"></a>Vea también
- [Entrada de blog: Analizar la CPU y memoria durante la depuración](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Acerca de la administración de memoria](/windows/win32/memory/about-memory-management)
