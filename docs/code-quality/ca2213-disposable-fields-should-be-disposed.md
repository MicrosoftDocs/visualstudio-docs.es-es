---
title: 'CA2213: Los campos descartables deben ser descartables'
ms.date: 11/05/2018
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
ms.openlocfilehash: 1fff209c9a432b78ce27e9c344c1afd29e93d57f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935542"
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

Un tipo es responsable de eliminar todos sus recursos no administrados. Regla CA2213 comprueba para ver si un tipo desechable (es decir, uno que implementa <xref:System.IDisposable>) `T` declara un campo `F` que es una instancia de un tipo desechable `FT`. Para cada campo `F` que ha asignado un objeto creado localmente dentro de los métodos o inicializadores del tipo contenedor `T`, la regla intenta buscar una llamada a `FT.Dispose`. La regla busca los métodos llamados por `T.Dispose` y un nivel inferior (es decir, los métodos llamados por los métodos llamados por `FT.Dispose`).

> [!NOTE]
> CA2213 regla se desencadena únicamente para los campos que están asignados a un objeto descartable creado localmente dentro de los métodos del tipo contenedor y los inicializadores. Si el objeto se crea o asigna fuera de tipo `T`, no se activa la regla. Esto reduce el ruido de los casos donde el tipo contenedor no tiene la responsabilidad de desechar el objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, llame a <xref:System.IDisposable.Dispose%2A> en los campos que son de tipos que implementan <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si usted no es responsable de liberar los recursos mantenidos por el campo, o si la llamada a <xref:System.IDisposable.Dispose%2A> se produce en un nivel más profundo que realiza la llamada a las comprobaciones de la regla.

## <a name="example"></a>Ejemplo

El fragmento de código siguiente muestra un tipo `TypeA` que implementa <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

El fragmento de código siguiente muestra un tipo `TypeB` que infringe la regla CA2213 declarando un campo `aFieldOfADisposableType` como un tipo desechable (`TypeA`) y no se llama a <xref:System.IDisposable.Dispose%2A> en el campo.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)