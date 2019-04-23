---
title: Suspensión de la característica automática | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c2e6db11220c2cc7f14bc2f0f05912e7855646c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045987"
---
# <a name="automatic-feature-suspension"></a>Suspensión automática de la característica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Si la memoria disponible del sistema cae a 200MB o menos, Visual Studio muestra el mensaje siguiente en el editor de código.

 ![Suspender el análisis de la solución completa de texto de alerta](../code-quality/media/fsa-alert.png "FSA_Alert")

 Cuando Visual Studio detecta una condición de memoria insuficiente, suspende automáticamente determinadas características avanzadas que le ayuden a permanecer estable. Cuando esta avanzada aparece la advertencia de suspensión de característica, Visual Studio seguirán funcionando como antes, pero se degradará ligeramente su rendimiento.

 En una condición de memoria insuficiente, ocurre lo siguiente:

- Análisis de la solución completa para Visual C# y Visual Basic está deshabilitada.

- [Recolección de elementos](http://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) se deshabilitan el modo de baja latencia (GC) para Visual C# y Visual Basic.

- Se vacían las memorias caché visuales Studio.

## <a name="improve-visual-studio-performance"></a>Mejorar el rendimiento de Visual Studio
 Para sugerencias y trucos sobre cómo mejorar el rendimiento de Visual Studio cuando se trabaja con soluciones de gran tamaño o las condiciones de poca memoria, vea [consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Análisis de la solución completa suspendido
 De forma predeterminada, análisis de la solución completa está habilitado para Visual Basic y deshabilitado para Visual C#. Sin embargo, en una condición de memoria insuficiente, análisis de la solución completa se deshabilita automáticamente para Visual Basic y Visual C#, independientemente de su configuración en el cuadro de diálogo Opciones. Sin embargo, puede volver a habilitar análisis de la solución completa eligiendo el **rehabilitar** botón en la información de la barra cuando aparezca, seleccionando la **Habilitar análisis de la solución completa** casilla de verificación en el cuadro de diálogo Opciones, o bien reiniciar Visual Studio. El cuadro de diálogo Opciones siempre muestra la solución completa actual configuración de análisis. Para obtener más información, vea [Cómo: Habilitar y deshabilitar el análisis de la solución completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC baja latencia deshabilitada
 Para volver a habilitar el modo de latencia baja de GC, reinicie Visual Studio.  De forma predeterminada, Visual Studio habilita el modo de latencia baja de GC cada vez que escribe para asegurarse de que lo que ha escrito no bloquea las operaciones de catálogo global. Sin embargo, si una condición de poca memoria hace que Visual Studio mostrar la advertencia suspensión automática, el modo de latencia baja de GC está deshabilitado para esa sesión. Reiniciar Visual Studio se rehabilitar el comportamiento de GC de forma predeterminada. Para obtener más información, consulta <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio las memorias caché vaciadas

Todas las cachés de Visual Studio se vacían inmediatamente, pero se iniciará volver a rellenar si continuar la sesión actual de desarrollo o reinicie Visual Studio. Las memorias caché vaciadas incluyen las memorias caché de las siguientes características.

- Buscar todas las referencias

- Navegar a

- Agregar Using

Además, también se borran las memorias caché que se utiliza para operaciones internas de Visual Studio.

> [!NOTE]
> La advertencia de suspensión de la característica automática se produce solo una vez en una base de cada solución, no en cada sesión. Esto significa que si cambiar desde Visual Basic a Visual C# (o viceversa) y ejecutar en otra condición de poca memoria, posiblemente, puede obtener otra advertencia de suspensión de la característica automática.

## <a name="see-also"></a>Vea también

- [Cómo: Habilitar y deshabilitar el análisis de la solución completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Fundamentos de la recolección de elementos no utilizados](http://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)