---
title: Suspensión automática de la característica
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431246"
---
# <a name="automatic-feature-suspension"></a>Suspensión automática de la característica

Si la memoria del sistema disponible cae a 200 MB o menos, Visual Studio muestra el siguiente mensaje en el editor de código:

![Texto de alerta que suspende el análisis completo de la solución](../code-quality/media/fsa_alert.png)

Cuando Visual Studio detecta una condición de memoria baja, suspende automáticamente ciertas características avanzadas para ayudar a que se mantenga estable. Visual Studio sigue funcionando como antes, pero su rendimiento se degrada.

En una condición de memoria baja, se llevan a cabo las siguientes acciones:

- El análisis de código en vivo para Visual C. y Visual Basic se reduce a un ámbito mínimo.

- El modo de baja latencia de la [recolección](/dotnet/standard/garbage-collection/index) de elementos no utilizados (GC) para Visual C- y Visual Basic está deshabilitado.

- Las cachés de Visual Studio se vacían.

## <a name="improve-visual-studio-performance"></a>Mejorar el rendimiento de Visual Studio

Para obtener sugerencias y trucos sobre cómo mejorar el rendimiento de Visual Studio cuando se trata de soluciones grandes o condiciones de poca memoria, vea Consideraciones de rendimiento [para soluciones grandes.](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>El análisis de código en vivo se reduce a un ámbito mínimo

De forma predeterminada, el análisis de código activo se ejecuta para documentos y proyectos abiertos. Puede personalizar este ámbito de análisis para que se reduzca al documento actual o se aumente a toda la solución. Para obtener más información, vea [Cómo: Configurar el ámbito](./configure-live-code-analysis-scope-managed-code.md)de análisis de código en vivo para código administrado . En una condición de memoria baja, Visual Studio fuerza el ámbito de análisis en vivo que se va a reducir al documento actual. Sin embargo, puede volver a habilitar el ámbito de análisis preferido eligiendo el botón **Volver a habilitar** en la barra de información cuando aparezca o reiniciando Visual Studio. El cuadro de diálogo Opciones siempre muestra la configuración actual del ámbito de análisis de código en vivo.

## <a name="gc-low-latency-disabled"></a>GC de baja latencia desactivada

Para volver a habilitar el modo de baja latencia de GC, reinicie Visual Studio. De forma predeterminada, Visual Studio habilita el modo de baja latencia de GC cada vez que escribe para asegurarse de que la escritura no bloquea ninguna operación de GC. Sin embargo, si una condición de memoria baja hace que Visual Studio muestre la advertencia de suspensión automática, el modo de baja latencia de GC está deshabilitado para esa sesión. Reiniciar Visual Studio vuelve a habilitar el comportamiento de GC predeterminado. Para más información, consulte <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Cachés de Visual Studio vaciadas

Si continúa la sesión de desarrollo actual o reinicia Visual Studio, todas las cachés de Visual Studio se vacían inmediatamente, pero comienzan a volver a rellenarse. Las memorias caché vaciadas incluyen cachés para las siguientes características:

- Buscar todas las referencias

- Navegar a

- Añadir usando

Además, las memorias caché utilizadas para las operaciones internas de Visual Studio también se borran.

> [!NOTE]
> La advertencia de suspensión de característica automática se produce solo una vez por solución, no por sesión. Esto significa que si cambia de Visual Basic a Visual C ( o viceversa) y se ejecuta en otra condición de memoria baja, es posible que obtenga otra advertencia de suspensión de característica automática.

## <a name="see-also"></a>Consulte también

- [Cómo: Configurar el ámbito de análisis de código en vivo para el código administrado](./configure-live-code-analysis-scope-managed-code.md)
- [Fundamentos de la recolección de elementos no utilizados](/dotnet/standard/garbage-collection/fundamentals)
- [Consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
