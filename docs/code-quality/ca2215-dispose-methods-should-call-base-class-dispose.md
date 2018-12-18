---
title: 'CA2215: Los métodos Dispose deben llamar a Dispose de clase base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11359e021d5c297c0782bf95fe35997b0a1b5be5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548418"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Los métodos Dispose deben llamar a Dispose de clase base

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|Identificador de comprobación|CA2215|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> hereda de un tipo que también implementa <xref:System.IDisposable>. El <xref:System.IDisposable.Dispose%2A> método del tipo heredado no llama a la <xref:System.IDisposable.Dispose%2A> método del tipo primario.

## <a name="rule-description"></a>Descripción de la regla
 Si un tipo hereda de un tipo desechable, debe llamar a la <xref:System.IDisposable.Dispose%2A> método del tipo base desde dentro de su propio <xref:System.IDisposable.Dispose%2A> método. Una llamada al método del tipo base Dispose garantiza que se liberen los recursos creados por el tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a `base`.<xref:System.IDisposable.Dispose%2A> en su <xref:System.IDisposable.Dispose%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si la llamada a `base`.<xref:System.IDisposable.Dispose%2A> se produce en un nivel más profundo que realiza la llamada a las comprobaciones de la regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo `TypeA` que implementa <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo `TypeB` que hereda del tipo `TypeA` y llama correctamente a su <xref:System.IDisposable.Dispose%2A> método.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable?displayProperty=fullName>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)