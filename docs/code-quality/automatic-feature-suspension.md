---
title: Suspensión automática de la característica
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd399d78ac43085d89958ba358954f9e6cefe521
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606535"
---
# <a name="automatic-feature-suspension"></a>Suspensión automática de la característica

Si la memoria disponible del sistema se encuentra en 200 MB o menos, Visual Studio muestra el siguiente mensaje en el editor de código:

![Texto de alerta que suspende el análisis completo de la solución](../code-quality/media/fsa_alert.png)

Cuando Visual Studio detecta una condición de memoria insuficiente, suspende automáticamente ciertas características avanzadas para ayudarlo a permanecer estable. Visual Studio continúa funcionando como antes, pero su rendimiento está degradado.

En una condición de memoria insuficiente, se realizan las siguientes acciones:

- El análisis completo de la C# solución para Visual y Visual Basic está deshabilitado.

- La [recolección de elementos no utilizados](/dotnet/standard/garbage-collection/index) (GC) el modo C# de baja latencia para objetos visuales y Visual Basic está deshabilitado.

- Las memorias caché de Visual Studio se vacían.

## <a name="improve-visual-studio-performance"></a>Mejorar el rendimiento de Visual Studio

Para obtener sugerencias y trucos sobre cómo mejorar el rendimiento de Visual Studio cuando se trabaja con soluciones de gran tamaño o condiciones de memoria insuficiente, vea [consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Análisis completo de la solución suspendido

De forma predeterminada, el análisis completo de la solución está habilitado para C#Visual Basic y deshabilitado para visual. Sin embargo, en una condición de memoria insuficiente, el análisis completo de la solución se deshabilita C#automáticamente para Visual Basic y visual, independientemente de su configuración en el cuadro de diálogo Opciones. Sin embargo, puede volver a habilitar el análisis completo de la solución eligiendo el botón **volver a habilitar** en la barra de información cuando aparezca; para ello, active la casilla habilitar el análisis de la **solución completa** en el cuadro de diálogo Opciones o reinicie Visual Studio. En el cuadro de diálogo Opciones siempre se muestra la configuración actual de análisis de la solución completa. Para obtener más información, vea [Cómo: habilitar y deshabilitar el análisis completo de la solución](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Baja latencia de GC deshabilitada

Para volver a habilitar el modo de baja latencia de GC, reinicie Visual Studio. De forma predeterminada, Visual Studio habilita el modo de baja latencia de GC siempre que se escribe para asegurarse de que su escritura no bloquea las operaciones de GC. Sin embargo, si una condición de memoria insuficiente hace que Visual Studio muestre la advertencia de suspensión automática, el modo de latencia baja de GC está deshabilitado para esa sesión. Al reiniciar Visual Studio, se vuelve a habilitar el comportamiento predeterminado de GC. Para obtener más información, vea <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Memorias caché de Visual Studio vacías

Si continúa con la sesión de desarrollo actual o reinicia Visual Studio, todas las memorias caché de Visual Studio se vaciarán inmediatamente, pero comenzarán a rellenarse. Las memorias caché vacías incluyen memorias caché para las siguientes características:

- Buscar todas las referencias

- Navegar a

- Agregar usando

Además, también se borran las memorias caché utilizadas para las operaciones internas de Visual Studio.

> [!NOTE]
> La advertencia de suspensión automática de características se produce solo una vez por solución, no por sesión. Esto significa que si cambia de Visual Basic a visual C# (o viceversa) y se ejecuta en otra condición de memoria insuficiente, puede obtener otra advertencia de suspensión automática de características.

## <a name="see-also"></a>Vea también

- [Cómo: Habilitar y deshabilitar el análisis completo de la solución](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Fundamentos de la recolección de elementos no utilizados](/dotnet/standard/garbage-collection/fundamentals)
- [Consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
