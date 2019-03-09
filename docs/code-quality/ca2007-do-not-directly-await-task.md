---
title: 'CA2007: No espera una tarea directamente'
ms.date: 03/08/2019
ms.topic: reference
f1_keywords:
- CA2007
- DoNotDirectlyAwaitATaskAnalyzer
helpviewer_keywords:
- CA2007
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: 8e94b67d1924e2144f658cd6bcd5989751efdb85
ms.sourcegitcommit: 1024f336dcd8e8a4c50b9a9ad8ec85b6e70073a8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2019
ms.locfileid: "57699684"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: No espera una tarea directamente

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|Identificador de comprobación|CA2007|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un método asincrónico [espera](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> directamente.

## <a name="rule-description"></a>Descripción de la regla

Cuando un método asincrónico espera una <xref:System.Threading.Tasks.Task> directamente, se produce la continuación en el mismo subproceso que creó la tarea. Este comportamiento puede ser costoso en términos de rendimiento y puede provocar un interbloqueo en el subproceso de interfaz de usuario. Considere la posibilidad de llamar a <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> para señalar su intención de continuación.

Esta regla se introdujo con [analizadores de FxCop](install-fxcop-analyzers.md) y no existe en "legacy" (análisis de código estático) FxCop.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir las infracciones, llame a <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> en la espera <xref:System.Threading.Tasks.Task>. Puede pasar `true` o `false` para el `continueOnCapturedContext` parámetro.

- Una llamada a `ConfigureAwait(true)` en la tarea tiene el mismo comportamiento que no explícitamente una llamada a <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>. Al llamar explícitamente a este método, está indicándole que los lectores intencionadamente desea realizar la continuación en el contexto de sincronización originales.

- Llamar a `ConfigureAwait(false)` en la tarea para programar continuaciones al grupo de subprocesos, lo que evita un interbloqueo en el subproceso de interfaz de usuario. Pasar `false` es una buena opción para las bibliotecas de independiente de la aplicación.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Puede suprimir esta advertencia si sabe que el consumidor no es una aplicación de interfaz gráfica de usuario o si el consumidor no tiene un <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Ejemplo

El fragmento de código siguiente genera la advertencia:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Para corregir la infracción, llame a <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> en la espera <xref:System.Threading.Tasks.Task>:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="see-also"></a>Vea también

- [¿Espera una tarea con ConfigureAwait (false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Instalar analizadores de FxCop en Visual Studio](install-fxcop-analyzers.md)