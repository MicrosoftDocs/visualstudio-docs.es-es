---
title: 'CA2213: Aplique Dispose a los campos a los que se pueda'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 143a094375871bf8073999f89d7fac5d6df01b4f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551865"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Aplique Dispose a los campos a los que se pueda

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|Identificador de comprobación|CA2213|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> declara campos que son de tipos que también implementan <xref:System.IDisposable>. El <xref:System.IDisposable.Dispose%2A> no se llama al método del campo el <xref:System.IDisposable.Dispose%2A> método del tipo declarativo.

## <a name="rule-description"></a>Descripción de la regla
 Un tipo es responsable de eliminar todos sus recursos no administrados; Esto se logra implementando <xref:System.IDisposable>. Esta regla comprueba si un tipo desechable `T` declara un campo `F` que es una instancia de un tipo desechable `FT`. Para cada campo `F`, la regla intenta buscar una llamada a `FT.Dispose`. La regla busca los métodos llamados por `T.Dispose`y un nivel inferior (los métodos llamados por los métodos llamados por `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a <xref:System.IDisposable.Dispose%2A> en los campos que son de tipos que implementan <xref:System.IDisposable> si usted es responsable de asignar y liberar los recursos no administrados mantenidos por el campo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si no es su responsabilidad para liberar los recursos mantenidos por el campo, o si la llamada a <xref:System.IDisposable.Dispose%2A> se produce en un nivel más profundo que realiza la llamada a las comprobaciones de la regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo `TypeA` que implementa <xref:System.IDisposable> (`FT` en la explicación anterior).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo `TypeB` que infringe esta regla declarando un campo `aFieldOfADisposableType` (`F` en la explicación anterior) como un tipo desechable (`TypeA`) y no se llama a <xref:System.IDisposable.Dispose%2A> en el campo. `TypeB` corresponde a `T` en la explicación anterior.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)