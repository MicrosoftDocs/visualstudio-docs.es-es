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
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 976e676cda09d50e34acb88a12551b1531595888
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508384"
---
# <a name="automatic-feature-suspension"></a>Suspensión automática de la característica

Si la memoria disponible del sistema se encuentra en 200 MB o menos, Visual Studio muestra el siguiente mensaje en el editor de código:

![Texto de alerta que suspende el análisis completo de la solución](../code-quality/media/fsa_alert.png)

Cuando Visual Studio detecta una condición de memoria insuficiente, suspende automáticamente ciertas características avanzadas para ayudarlo a permanecer estable. Visual Studio continúa funcionando como antes, pero su rendimiento está degradado.

En una condición de memoria insuficiente, se realizan las siguientes acciones:

- El análisis de código activo para Visual C# y Visual Basic se reduce al ámbito mínimo.

- La [recolección de elementos no utilizados](/dotnet/standard/garbage-collection/index) (GC) el modo de baja latencia para Visual C# y Visual Basic está deshabilitado.

- Las memorias caché de Visual Studio se vacían.

## <a name="improve-visual-studio-performance"></a>Mejorar el rendimiento de Visual Studio

Para obtener sugerencias y trucos sobre cómo mejorar el rendimiento de Visual Studio cuando se trabaja con soluciones de gran tamaño o condiciones de memoria insuficiente, vea [consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>El análisis de código activo se reduce a un ámbito mínimo

De forma predeterminada, el análisis de código activo se ejecuta para proyectos y documentos abiertos. Puede personalizar este ámbito de análisis para que se reduzca al documento actual o aumente a toda la solución. Para obtener más información, vea [Cómo: Configurar el ámbito del análisis activo para el código administrado](./configure-live-code-analysis-scope-managed-code.md). En una condición de memoria insuficiente, Visual Studio fuerza que el ámbito de análisis activo se reduzca al documento actual. Sin embargo, puede volver a habilitar el ámbito de análisis preferido eligiendo el botón **volver a habilitar** en la barra de información cuando aparezca o reiniciando Visual Studio. En el cuadro de diálogo Opciones siempre se muestra la configuración actual del ámbito de análisis de código activo.

## <a name="gc-low-latency-disabled"></a>Baja latencia de GC deshabilitada

Para volver a habilitar el modo de baja latencia de GC, reinicie Visual Studio. De forma predeterminada, Visual Studio habilita el modo de baja latencia de GC siempre que se escribe para asegurarse de que su escritura no bloquea las operaciones de GC. Sin embargo, si una condición de memoria insuficiente hace que Visual Studio muestre la advertencia de suspensión automática, el modo de latencia baja de GC está deshabilitado para esa sesión. Al reiniciar Visual Studio, se vuelve a habilitar el comportamiento predeterminado de GC. Para obtener más información, vea <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Memorias caché de Visual Studio vacías

Si continúa con la sesión de desarrollo actual o reinicia Visual Studio, todas las memorias caché de Visual Studio se vaciarán inmediatamente, pero comenzarán a rellenarse. Las memorias caché vacías incluyen memorias caché para las siguientes características:

- Buscar todas las referencias

- Navegar a

- Agregar usando

Además, también se borran las memorias caché utilizadas para las operaciones internas de Visual Studio.

> [!NOTE]
> La advertencia de suspensión automática de características se produce solo una vez por solución, no por sesión. Esto significa que si cambia de Visual Basic a Visual C# (o viceversa) y se ejecuta en otra condición de memoria insuficiente, es posible que pueda obtener otra advertencia de suspensión automática de características.

## <a name="see-also"></a>Vea también

- [Cómo: configurar el ámbito de análisis de código activo para código administrado](./configure-live-code-analysis-scope-managed-code.md)
- [Fundamentos de la recolección de elementos no utilizados](/dotnet/standard/garbage-collection/fundamentals)
- [Consideraciones de rendimiento para soluciones de gran tamaño](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)
