---
title: Suspensión automática de características | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1dddc235131322a61cdb0106d866b138040d8c18
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508241"
---
# <a name="automatic-feature-suspension"></a>Suspensión automática de la característica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Si la memoria disponible del sistema se encuentra en 200 MB o menos, Visual Studio muestra el siguiente mensaje en el editor de código.

 ![Texto de alerta que suspende el análisis completo de la solución](../code-quality/media/fsa-alert.png "FSA_Alert")

 Cuando Visual Studio detecta una condición de memoria insuficiente, suspende automáticamente ciertas características avanzadas para ayudarlo a permanecer estable. Cuando se muestra esta advertencia de suspensión de características avanzadas, Visual Studio continuará funcionando como antes, pero su rendimiento se degradará ligeramente.

 En una condición de memoria insuficiente, ocurre lo siguiente:

- El análisis completo de la solución para Visual C# y Visual Basic está deshabilitado.

- La [recolección de elementos no utilizados](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) (GC) el modo de baja latencia para Visual C# y Visual Basic están deshabilitados.

- Las memorias caché de Visual Studio se vacían.

## <a name="improve-visual-studio-performance"></a>Mejorar el rendimiento de Visual Studio
 Para obtener sugerencias y trucos sobre cómo mejorar el rendimiento de Visual Studio cuando se trabaja con soluciones de gran tamaño o condiciones de memoria insuficiente, vea [consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

## <a name="full-solution-analysis-suspended"></a>Análisis completo de la solución suspendido
 De forma predeterminada, el análisis completo de la solución está habilitado para Visual Basic y deshabilitado para Visual C#. Sin embargo, en una condición de memoria insuficiente, el análisis completo de la solución se deshabilita automáticamente para Visual Basic y Visual C#, independientemente de su configuración en el cuadro de diálogo Opciones. Sin embargo, puede volver a habilitar el análisis completo de la solución eligiendo el botón **volver a habilitar** en la barra de información cuando aparezca; para ello, active la casilla habilitar el análisis de la **solución completa** en el cuadro de diálogo Opciones o reinicie Visual Studio. En el cuadro de diálogo Opciones siempre se muestra la configuración actual de análisis de la solución completa. Para obtener más información, vea [Cómo: habilitar y deshabilitar el análisis completo de la solución](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Baja latencia de GC deshabilitada
 Para volver a habilitar el modo de baja latencia de GC, reinicie Visual Studio.  De forma predeterminada, Visual Studio habilita el modo de baja latencia de GC siempre que se escribe para asegurarse de que su escritura no bloquea las operaciones de GC. Sin embargo, si una condición de memoria insuficiente hace que Visual Studio muestre la advertencia de suspensión automática, el modo de latencia baja de GC está deshabilitado para esa sesión. Al reiniciar Visual Studio, se volverá a habilitar el comportamiento predeterminado de GC. Para obtener más información, vea <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Memorias caché de Visual Studio vacías

Todas las memorias caché de Visual Studio se vacían inmediatamente, pero comenzarán a rellenarse si continúa con la sesión de desarrollo actual o reinicia Visual Studio. Las memorias caché vacías incluyen memorias caché para las siguientes características.

- Buscar todas las referencias

- Navegar a

- Agregar usando

Además, también se borran las memorias caché utilizadas para las operaciones internas de Visual Studio.

> [!NOTE]
> La advertencia de suspensión automática de características se produce solo una vez por solución, no por sesión. Esto significa que si cambia de Visual Basic a Visual C# (o viceversa) y se ejecuta en otra condición de memoria insuficiente, es posible que pueda obtener otra advertencia de suspensión automática de características.

## <a name="see-also"></a>Vea también

- [Cómo: Habilitar y deshabilitar el análisis completo de la solución](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Fundamentos de la recolección de elementos no utilizados](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)