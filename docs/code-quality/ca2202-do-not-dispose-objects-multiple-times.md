---
title: 'CA2202: No usar Dispose varias veces en objetos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d65e9466a57e28b8e0322fc45401fb6e2333aaf7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012269"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: No usar Dispose varias veces en objetos

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|Identificador de comprobación|CA2202|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Implementación de un método contiene rutas de acceso del código que podrían provocar varias llamadas a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o un equivalente de Dispose, como un método Close() en algunos tipos, en el mismo objeto.

## <a name="rule-description"></a>Descripción de la regla

Una correcta ejecución <xref:System.IDisposable.Dispose%2A> método puede llamarse varias veces sin producir una excepción. Sin embargo, esto no está garantizado y para evitar que se generen un <xref:System.ObjectDisposedException?displayProperty=fullName> no debe llamar a <xref:System.IDisposable.Dispose%2A> más de una vez en un objeto.

## <a name="related-rules"></a>Reglas relacionadas

- [CA2000: Eliminar objetos antes de perder el ámbito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie la implementación hasta que independientemente de la ruta de acceso del código, <xref:System.IDisposable.Dispose%2A> se llama solo una vez para el objeto.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. Incluso si <xref:System.IDisposable.Dispose%2A> para el objeto se sabe que se puede llamar varias veces, la implementación podría cambiar en el futuro.

## <a name="example"></a>Ejemplo

Anidar `using` instrucciones (`Using` en Visual Basic) pueden producir infracciones de la advertencia CA2202. Si el recurso IDisposable de anidada interna `using` instrucción contiene el recurso de la exterior `using` instrucción, el `Dispose` método del recurso anidado libera el recurso contenido. Cuando se produce esta situación, el `Dispose` método externo `using` instrucción intenta disponer de su recurso por segunda vez.

En el ejemplo siguiente, un <xref:System.IO.Stream> objeto que se crea en un exterior usando la instrucción se libera al final de la instrucción using interna en el método Dispose de la <xref:System.IO.StreamWriter> objeto que contiene el `stream` objeto. Al final de la exterior `using` instrucción, el `stream` objeto se libere una segunda vez. La segunda versión es una infracción de CA2202.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Ejemplo

Para resolver este problema, use un `try` / `finally` bloquear en lugar de la exterior `using` instrucción. En el `finally` bloquear, asegúrese de que el `stream` del recurso no es null.

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)