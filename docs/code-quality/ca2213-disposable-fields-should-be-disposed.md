---
title: 'CA2213: Los campos descartables deben ser descartables'
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 675206bb58e27110af79c46b1d61e9489f7661f2
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766083"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Los campos descartables deben ser descartables

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|Identificador de comprobación|CA2213|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa

Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> declara campos que son de tipos que también implementan. <xref:System.IDisposable> El <xref:System.IDisposable.Dispose%2A> método del tipo declarativo no llama <xref:System.IDisposable.Dispose%2A> al método del campo.

## <a name="rule-description"></a>Descripción de la regla

Un tipo es responsable de la eliminación de todos sus recursos no administrados. La regla CA2213 comprueba si un tipo descartable (es decir, uno que implementa <xref:System.IDisposable>) `T` declara un campo `F` que es una instancia de un tipo `FT`descartable. Para cada campo `F` que tiene asignado un objeto creado localmente dentro de los métodos o inicializadores del tipo `T`contenedor, la regla intenta buscar una llamada a `FT.Dispose`. La regla busca los métodos a los `T.Dispose` que llama y un nivel inferior (es decir, los métodos llamados por los métodos `T.Dispose`llamados por).

> [!NOTE]
> Aparte de los [casos especiales](#special-cases), la regla CA2213 se activa solo para los campos a los que se ha asignado un objeto descartable creado localmente dentro de los métodos e inicializadores del tipo contenedor. Si el objeto se crea o se asigna fuera del `T`tipo, la regla no se activa. Esto reduce el ruido en los casos en los que el tipo contenedor no posee la responsabilidad de desechar el objeto.

### <a name="special-cases"></a>Casos especiales

La regla CA2213 también se puede activar para los campos de los siguientes tipos incluso si el objeto que se asigna no se crea localmente:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Pasar un objeto de uno de estos tipos a un constructor y, a continuación, asignarlo a un campo indica una *transferencia de propiedad de Dispose* al tipo recién construido. Es decir, el tipo recién construido ahora es responsable de desechar el objeto. Si no se desecha el objeto, se produce una infracción de CA2213.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, <xref:System.IDisposable.Dispose%2A> llame a en los campos que son de <xref:System.IDisposable>tipos que implementan.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si:

- El tipo marcado no es responsable de liberar el recurso mantenido por el campo (es decir, el tipo no tiene la *propiedad Dispose*)
- La llamada a <xref:System.IDisposable.Dispose%2A> se produce en un nivel de llamada más profundo que las comprobaciones de la regla

## <a name="example"></a>Ejemplo

En el fragmento de código siguiente `TypeA` se muestra un <xref:System.IDisposable>tipo que implementa.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

En el fragmento de código siguiente `TypeB` se muestra un tipo que infringe la regla CA2213 al `aFieldOfADisposableType` declarar un campo como un`TypeA`tipo descartable <xref:System.IDisposable.Dispose%2A> () y no llamar a en el campo.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

Para corregir la infracción, `Dispose()` llame a en el campo descartable:

```csharp
protected virtual void Dispose(bool disposing)
{
   if (!disposed)
   {
      // Dispose of resources held by this instance.
      aFieldOfADisposableType.Dispose();

      disposed = true;

      // Suppress finalization of this disposed instance.
      if (disposing)
      {
          GC.SuppressFinalize(this);
      }
   }
}
```

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)