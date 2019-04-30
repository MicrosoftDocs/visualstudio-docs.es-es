---
title: 'CA2007: No esperar una tarea directamente'
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
ms.openlocfilehash: bf3e13697f39f7d0f531549d4c018b9f42872596
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545233"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: No esperar una tarea directamente

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

## <a name="configurability"></a>Capacidad de configuración

Puede configurar si desea excluir los métodos asincrónicos que no devuelven un valor de esta regla. Para excluir estos tipos de métodos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

También puede configurar qué tipos de ensamblado al que aplicar esta regla de salida. Por ejemplo, para esta regla solo se aplican al código que genera una aplicación de consola o una biblioteca de vínculos dinámicos (es decir, no una interfaz de usuario aplicación), agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="see-also"></a>Vea también

- [¿Espera una tarea con ConfigureAwait (false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Instalar analizadores de FxCop en Visual Studio](install-fxcop-analyzers.md)