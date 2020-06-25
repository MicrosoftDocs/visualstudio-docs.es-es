---
title: advertencias de confiabilidad
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3449723394f603b4b726fa8ebf2258e2c8f4c46c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283390"
---
# <a name="reliability-warnings"></a>Advertencias de confiabilidad

Las advertencias de confiabilidad admiten la confiabilidad de bibliotecas y aplicaciones, como la memoria y el uso de subprocesos correctos. Las reglas de confiabilidad incluyen:

|Regla|Descripción|
|----------|-----------------|
|[CA2000: Desechar objetos antes de perder el ámbito](../code-quality/ca2000.md)|Dado que podría producirse un evento excepcional que evitaría que el finalizador de un objeto se ejecutase, el objeto debe estar disponible en su lugar antes de que todas las referencias a él estén fuera del ámbito.|
|[CA2001: Evitar llamar a métodos problemáticos](../code-quality/ca2001.md)|Un miembro llama a un método potencialmente peligroso o problemático.|
|[CA2002: No bloquear objetos con identidad débil](../code-quality/ca2002.md)|Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación. Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto.|
|[CA2003: No tratar fibras como subprocesos](../code-quality/ca2003.md)|Un subproceso administrado se trata como un subproceso de Win32.|
|[CA2004: Quitar las llamadas a GC.KeepAlive](../code-quality/ca2004.md)|Si va a realizar la conversión al uso de SafeHandle, quite todas las llamadas a GC. KeepAlive (objeto). En este caso, las clases no deben tener que llamar a GC. KeepAlive, suponiendo que no tienen un finalizador, sino que se basan en SafeHandle para finalizar el identificador de sistema operativo.|
|[CA2006: Utilizar SafeHandle para encapsular recursos nativos](../code-quality/ca2006.md)|El uso de IntPtr en código administrado podría indicar un posible problema para la seguridad y la confiabilidad. Todos los usos de IntPtr se deben revisar para determinar si se necesita utilizar en su lugar SafeHandle o una tecnología similar.|
|[CA2007: No esperar una tarea directamente](../code-quality/ca2007.md)|Un método asincrónico [espera](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> directamente.|
|[CA2009: No llame a ToImmutableCollection en un valor ImmutableCollection](../code-quality/ca2009.md)|`ToImmutable`se llamó innecesariamente al método en una colección inmutable desde el <xref:System.Collections.Immutable> espacio de nombres.|
|[CA2011: No asignar la propiedad dentro de su establecedor](../code-quality/ca2011.md) | Se asignó accidentalmente un valor a una propiedad dentro de su propio [descriptor de acceso set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
|[CA2012: usar ValueTasks correctamente](../code-quality/ca2012.md) | Los ValueTasks devueltos de las invocaciones de miembro están diseñados para esperarse directamente.  Los intentos de consumir un ValueTask varias veces o de tener acceso directamente a uno de los resultados antes de que se sepa que se han completado pueden producir una excepción o daños.  Omitir tal ValueTask es probable que se trate de un error funcional y puede degradar el rendimiento. |
|[CA2013: no usar ReferenceEquals con tipos de valor](../code-quality/ca2013.md) | Al comparar valores mediante <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , si objA y objB son tipos de valor, se les aplica la conversión boxing antes de que se pasen al <xref:System.Object.ReferenceEquals%2A> método. Esto significa que, aunque objA y objB representen la misma instancia de un tipo de valor, el <xref:System.Object.ReferenceEquals%2A> método devuelve false. |
|[CA2014: no use stackalloc en los bucles.](../code-quality/ca2014.md) | El espacio de pila asignado por stackalloc solo se libera al final de la invocación del método actual.  Su uso en un bucle puede dar lugar a un crecimiento de pila sin enlazar y a condiciones de desbordamiento de pila eventuales. |
|[CA2015: no definir finalizadores para los tipos derivados de MemoryManager &lt; T&gt;](../code-quality/ca2015.md) | Agregar un finalizador a un tipo derivado de <xref:System.Buffers.MemoryManager%601> puede permitir que la memoria se libere mientras esté siendo utilizada por <xref:System.Span%601> . |
