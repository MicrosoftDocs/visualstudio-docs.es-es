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
ms.openlocfilehash: cf07c997f933e6aacf3eff29ae204ecd0bedb036
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233075"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: No esperar una tarea directamente

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|Identificador de comprobación|CA2007|
|Categoría|Microsoft.Reliability|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un método asincrónico [espera](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> directamente.

## <a name="rule-description"></a>Descripción de la regla

Cuando un método asincrónico espera <xref:System.Threading.Tasks.Task> directamente, la continuación se produce en el mismo subproceso que creó la tarea. Este comportamiento puede ser costoso en términos de rendimiento y puede dar lugar a un interbloqueo en el subproceso de la interfaz de usuario. Considere la <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> posibilidad de llamar a para señalar su intención de continuación.

Esta regla se presentó con los [analizadores de FxCop](install-fxcop-analyzers.md) y no existe en el análisis de FxCop heredado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir las infracciones <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> , llame a en <xref:System.Threading.Tasks.Task>el Await. Puede pasar `true` o `false` para el `continueOnCapturedContext` parámetro.

- Llamar `ConfigureAwait(true)` a en la tarea tiene el mismo comportamiento que no llamar <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>explícitamente a. Al llamar explícitamente a este método, está permitiendo a los lectores saber que desea realizar la continuación en el contexto de sincronización original.

- Llame `ConfigureAwait(false)` a en la tarea para programar continuaciones en el grupo de subprocesos, evitando así un interbloqueo en el subproceso de la interfaz de usuario. Pasar `false` es una buena opción para las bibliotecas independientes de la aplicación.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Puede suprimir esta advertencia si sabe que el consumidor no es una aplicación de interfaz gráfica de usuario (GUI) o si el consumidor no tiene un <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Ejemplo

El siguiente fragmento de código genera la ADVERTENCIA:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Para corregir la infracción, <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> llame a en <xref:System.Threading.Tasks.Task>Await:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="configurability"></a>Configurabilidad

Puede configurar si desea excluir métodos asincrónicos que no devuelven un valor de esta regla. Para excluir estos tipos de métodos, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

También puede configurar los tipos de ensamblado de salida a los que aplicar esta regla. Por ejemplo, para aplicar esta regla solo al código que produce una aplicación de consola o una biblioteca vinculada dinámicamente (es decir, no una aplicación de interfaz de usuario), agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="see-also"></a>Vea también

- [¿Debo esperar una tarea con ConfigureAwait (false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Instalar analizadores de FxCop en Visual Studio](install-fxcop-analyzers.md)