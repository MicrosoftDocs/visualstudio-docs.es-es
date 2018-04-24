---
title: 'CA2213: Aplique Dispose a los campos a los que se pueda'
ms.date: 11/04/2016
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
ms.openlocfilehash: 914f4f14742bcac3de94a25a547767b714058b7c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
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
 Un tipo es responsable de la eliminación de todos sus recursos no administrados; Esto se logra mediante la implementación de <xref:System.IDisposable>. Esta regla comprueba si un tipo descartable `T` declara un campo `F` que es una instancia de un tipo descartable `FT`. Para cada campo `F`, la regla intenta buscar una llamada a `FT.Dispose`. La regla busca los métodos llamados por `T.Dispose`y un nivel inferior (los métodos llamados por los métodos llamados por `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a <xref:System.IDisposable.Dispose%2A> en los campos que son de tipos que implementan <xref:System.IDisposable> si usted es responsable de asignar y liberar los recursos no administrados mantenidos por el campo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si no es su responsabilidad para liberar los recursos mantenidos por el campo, o si la llamada a <xref:System.IDisposable.Dispose%2A> se produce en un nivel más profundo que realiza la llamada a las comprobaciones de la regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo `TypeA` que implementa <xref:System.IDisposable> (`FT` en la explicación anterior).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo `TypeB` que infringe esta regla declarando un campo `aFieldOfADisposableType` (`F` en la explicación anterior) como un tipo descartable (`TypeA`) y no llamando a <xref:System.IDisposable.Dispose%2A> en el campo. `TypeB` corresponde a `T` en la descripción anterior.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Vea también
 <xref:System.IDisposable?displayProperty=fullName> [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)