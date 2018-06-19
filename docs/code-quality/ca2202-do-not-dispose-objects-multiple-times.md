---
title: 'CA2202: No aplicar Dispose a los objetos varias veces'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c7eb35e556e8edd6e840f2fbd6701e182895706
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920154"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: No aplicar Dispose a los objetos varias veces
|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|Identificador de comprobación|CA2202|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Implementación de un método contiene rutas de acceso de código que podrían provocar varias llamadas a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o a un equivalente de Dispose, como un método Close() en algunos tipos, en el mismo objeto.

## <a name="rule-description"></a>Descripción de la regla
 A que se haya implementado correctamente <xref:System.IDisposable.Dispose%2A> método puede llamarse varias veces sin producir una excepción. Sin embargo, esto no se garantiza y para evitar que se generen un <xref:System.ObjectDisposedException?displayProperty=fullName> no debería llamar a <xref:System.IDisposable.Dispose%2A> más de una vez en un objeto.

## <a name="related-rules"></a>Reglas relacionadas
 [CA2000: Desechar (Dispose) objetos antes de perder el ámbito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la implementación por lo que es independientemente de la ruta de acceso del código, <xref:System.IDisposable.Dispose%2A> se llama solo una vez para el objeto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Aunque <xref:System.IDisposable.Dispose%2A> para el objeto se conoce como con seguridad que se puede llamar varias veces, la implementación podría cambiar en el futuro.

## <a name="example"></a>Ejemplo
 Anidar `using` instrucciones (`Using` en Visual Basic) pueden producir infracciones de la advertencia CA2202. Si el recurso IDisposable de anidada interna `using` instrucción contiene el recurso de la externa `using` (instrucción), el `Dispose` método del recurso anidado libera el recurso incluido. Cuando se produce esta situación, el `Dispose` método externo `using` instrucción intenta disponer de su recurso por segunda vez.

 En el ejemplo siguiente, un <xref:System.IO.Stream> objeto que se crea en un externo utilizando la instrucción se haya liberado al final de la instrucción using interna en el método Dispose de la <xref:System.IO.StreamWriter> objeto que contiene el `stream` objeto. Al final de la externa `using` (instrucción), el `stream` se libera el objeto de una segunda vez. La segunda versión constituye una infracción de CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}

```

## <a name="example"></a>Ejemplo
 Para resolver este problema, use un `try` / `finally` bloque en lugar de la externa `using` instrucción. En el `finally` bloquear, asegúrese de que el `stream` del recurso no es null.

```
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
 <xref:System.IDisposable?displayProperty=fullName> [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)