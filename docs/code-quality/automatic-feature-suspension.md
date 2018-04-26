---
title: Suspensión de la característica automática en Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: d75c02bf6b817d03492a15b1f827f94eaaf3e306
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="automatic-feature-suspension"></a>Suspensión de la característica automática

Si la memoria disponible del sistema cae a 200 MB o menos, Visual Studio muestra el mensaje siguiente en el editor de código:

![Suspender el análisis de la solución completa de texto de alerta](../code-quality/media/fsa_alert.png)

Cuando Visual Studio detecta una condición de memoria insuficiente, se suspende automáticamente determinadas características avanzadas que le ayuden a permanecer estable. Visual Studio continúa funcionando como antes, pero su rendimiento se degrada.

En una condición de memoria insuficiente, realicen las siguientes acciones:

- Análisis de la solución completa para Visual C# y Visual Basic está deshabilitado.

- [Colección de elementos no utilizados](/dotnet/standard/garbage-collection/index) modo de latencia baja (GC) para Visual C# y Visual Basic está deshabilitado.

- Se vacían las memorias caché visuales Studio.

## <a name="improve-visual-studio-performance"></a>Mejorar el rendimiento de Visual Studio

Para obtener sugerencias y trucos sobre cómo mejorar el rendimiento de Visual Studio cuando se trabaja con soluciones de gran tamaño o condiciones de memoria insuficiente, consulte [consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Análisis de la solución completa suspendido

De forma predeterminada, los análisis de la solución completa se habilita para Visual Basic y se deshabilita para Visual C#. Sin embargo, en una condición de memoria insuficiente, análisis de la solución completa se deshabilitan automáticamente para Visual Basic y Visual C#, independientemente de su configuración en el cuadro de diálogo de opciones. Sin embargo, puede volver a habilitar análisis de la solución completa eligiendo la **volver a habilitar** botón en la información de la barra cuando aparezca, seleccionando la **Habilitar análisis de la solución completa** casilla de verificación en el cuadro de diálogo Opciones, o reiniciar Visual Studio. El cuadro de diálogo de opciones siempre muestra la solución completa actual configuración de análisis. Para obtener más información, consulte [Cómo: habilitar y deshabilitar el análisis de la solución completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC baja latencia deshabilitada

Para volver a habilitar el modo de latencia baja de GC, reinicie Visual Studio. De forma predeterminada, Visual Studio habilita el modo de latencia baja de GC cada vez que se escribe para asegurarse de que su escritura no bloquea las operaciones de GC. Sin embargo, si una condición de memoria baja hace que Visual Studio mostrar la advertencia suspensión automática, se deshabilita el modo de latencia baja de GC para esa sesión. Vuelva a reiniciar Visual Studio permite que el comportamiento predeterminado de GC. Para obtener más información, consulta <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio las memorias caché vaciadas

Si sigues la sesión actual de desarrollo o al reiniciar Visual Studio, inmediatamente se vacían todas las cachés de Visual Studio, pero comienzan a rellenar. Las memorias caché vaciadas incluyen las memorias caché para las siguientes características:

- Buscar todas las referencias

- Navegar a

- Agregar Using

Además, también se borran las memorias caché que se utiliza para operaciones internas de Visual Studio.

> [!NOTE]
> La advertencia de suspensión de la característica automática se produce solo una vez en una base por solución, no en cada sesión. Esto significa que si se cambia de Visual Basic a Visual C# (o viceversa) y se ejecuta en otra condición de memoria insuficiente, posiblemente puede obtener otra advertencia de suspensión de la característica automática.

## <a name="see-also"></a>Vea también

- [Cómo: habilitar y deshabilitar el análisis de la solución completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Fundamentos de la recolección de elementos no utilizados](/dotnet/standard/garbage-collection/fundamentals)
- [Consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)