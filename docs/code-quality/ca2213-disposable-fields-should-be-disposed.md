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
ms.openlocfilehash: b38157fcc23561b47a919151aa78a71f98b3909b
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804996"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Los campos descartables deben ser descartables

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|Identificador de comprobación|CA2213|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> declara campos que son de tipos que también implementan <xref:System.IDisposable>. El <xref:System.IDisposable.Dispose%2A> no se llama al método del campo el <xref:System.IDisposable.Dispose%2A> método del tipo declarativo.

## <a name="rule-description"></a>Descripción de la regla

Un tipo es responsable de eliminar todos sus recursos no administrados. Regla CA2213 comprueba para ver si un tipo desechable (es decir, uno que implementa <xref:System.IDisposable>) `T` declara un campo `F` que es una instancia de un tipo desechable `FT`. Para cada campo `F` que ha asignado un objeto creado localmente dentro de los métodos o inicializadores del tipo contenedor `T`, la regla intenta buscar una llamada a `FT.Dispose`. La regla busca los métodos llamados por `T.Dispose` y un nivel inferior (es decir, los métodos llamados por los métodos llamados por `T.Dispose`).

> [!NOTE]
> No sea el [casos especiales](#special-cases), se desencadena CA2213 solo para los campos que se asignan a un objeto descartable creado localmente dentro de los métodos del tipo contenedor y los inicializadores de regla. Si el objeto se crea o asigna fuera de tipo `T`, no se activa la regla. Esto reduce el ruido de los casos donde el tipo contenedor no tiene la responsabilidad de desechar el objeto.

### <a name="special-cases"></a>Casos especiales

CA2213 regla también pueden activar para los campos de los siguientes tipos, incluso si no se crea el objeto que se les asigna localmente:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Pasar un objeto de uno de estos tipos a un constructor y, a continuación, asignarlo a un campo indican un *dispose de transferencia de la propiedad* para el tipo construido recientemente. Es decir, el tipo construido recién ahora es responsable de desechar el objeto. Si no se desecha el objeto, se produce una infracción de CA2213.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, llame a <xref:System.IDisposable.Dispose%2A> en los campos que son de tipos que implementan <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si:

- El tipo marcado no es responsable de liberar los recursos mantenidos por el campo (es decir, no tiene el tipo *dispose propiedad*)
- La llamada a <xref:System.IDisposable.Dispose%2A> se produce en un nivel más profundo que realiza la llamada a las comprobaciones de regla

## <a name="example"></a>Ejemplo

El fragmento de código siguiente muestra un tipo `TypeA` que implementa <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

El fragmento de código siguiente muestra un tipo `TypeB` que infringe la regla CA2213 declarando un campo `aFieldOfADisposableType` como un tipo desechable (`TypeA`) y no se llama a <xref:System.IDisposable.Dispose%2A> en el campo.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)