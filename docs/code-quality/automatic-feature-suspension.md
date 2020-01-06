---
title: Suspensión automática de la característica
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6910bae3d924202fad8995d6ccd53efe848ba50
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573305"
---
# <a name="automatic-feature-suspension"></a>Suspensión automática de la característica

Si la memoria disponible del sistema cae a 200 MB o menos, Visual Studio muestra el mensaje siguiente en el editor de código:

![Suspender el análisis de la solución completa de texto de alerta](../code-quality/media/fsa_alert.png)

Cuando Visual Studio detecta una condición de memoria insuficiente, suspende automáticamente determinadas características avanzadas que le ayuden a permanecer estable. Visual Studio sigue funcionando como antes, pero su rendimiento se degrada.

En una condición de memoria insuficiente, emprenden las acciones siguientes:

- Análisis de la solución completa para Visual C# y Visual Basic está deshabilitada.

- [Recolección de elementos](/dotnet/standard/garbage-collection/index) se deshabilita el modo de baja latencia (GC) para Visual C# y Visual Basic.

- Se vacían las memorias caché visuales Studio.

## <a name="improve-visual-studio-performance"></a>Mejorar el rendimiento de Visual Studio

Para sugerencias y trucos sobre cómo mejorar el rendimiento de Visual Studio cuando se trabaja con soluciones de gran tamaño o las condiciones de poca memoria, vea [consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Análisis de la solución completa suspendido

De forma predeterminada, análisis de la solución completa está habilitado para Visual Basic y deshabilitado para Visual C#. Sin embargo, en una condición de memoria insuficiente, análisis de la solución completa se deshabilita automáticamente para Visual Basic y Visual C#, independientemente de su configuración en el cuadro de diálogo Opciones. Sin embargo, puede volver a habilitar análisis de la solución completa eligiendo el **rehabilitar** botón en la información de la barra cuando aparezca, seleccionando la **Habilitar análisis de la solución completa** casilla de verificación en el cuadro de diálogo Opciones, o bien reiniciar Visual Studio. El cuadro de diálogo Opciones siempre muestra la solución completa actual configuración de análisis. Para obtener más información, consulte [Cómo: habilitar y deshabilitar el análisis de la solución completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC baja latencia deshabilitada

Para volver a habilitar el modo de latencia baja de GC, reinicie Visual Studio. De forma predeterminada, Visual Studio habilita el modo de latencia baja de GC cada vez que escribe para asegurarse de que lo que ha escrito no bloquea las operaciones de catálogo global. Sin embargo, si una condición de poca memoria hace que Visual Studio mostrar la advertencia suspensión automática, el modo de latencia baja de GC está deshabilitado para esa sesión. Volver a reiniciar Visual Studio permite que el comportamiento de GC de forma predeterminada. Para obtener más información, vea <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio las memorias caché vaciadas

Si continuar la sesión actual de desarrollo o reinicie Visual Studio, inmediatamente se vacían todas las cachés de Visual Studio, pero comienzan a llenar. Las memorias caché vaciadas incluyen las memorias caché de las siguientes características:

- Buscar todas las referencias

- Navegar a

- Agregar Using

Además, también se borran las memorias caché que se utiliza para operaciones internas de Visual Studio.

> [!NOTE]
> La advertencia de suspensión de la característica automática se produce solo una vez en una base de cada solución, no en cada sesión. Esto significa que si cambiar desde Visual Basic a Visual C# (o viceversa) y ejecutar en otra condición de poca memoria, posiblemente, puede obtener otra advertencia de suspensión de la característica automática.

## <a name="see-also"></a>Vea también

- [Cómo: Habilitar y deshabilitar el análisis completo de la solución](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Fundamentos de la recolección de elementos no utilizados](/dotnet/standard/garbage-collection/fundamentals)
- [Consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
