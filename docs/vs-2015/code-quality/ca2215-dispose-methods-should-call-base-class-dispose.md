---
title: 'CA2215: los métodos Dispose deben llamar a Dispose de clase base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4197c2faaf4aa23db930a9019538592326a84116
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534386"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|Identificador de comprobación|CA2215|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> hereda de un tipo que también implementa <xref:System.IDisposable> . El <xref:System.IDisposable.Dispose%2A> método del tipo de herencia no llama al <xref:System.IDisposable.Dispose%2A> método del tipo primario.

## <a name="rule-description"></a>Descripción de la regla
 Si un tipo hereda de un tipo descartable, debe llamar al <xref:System.IDisposable.Dispose%2A> método del tipo base desde su propio <xref:System.IDisposable.Dispose%2A> método. Llamar al método de tipo base Dispose garantiza que se liberen los recursos creados por el tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a `base` .<xref:System.IDisposable.Dispose%2A> en el <xref:System.IDisposable.Dispose%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si la llamada a `base` .<xref:System.IDisposable.Dispose%2A> se produce en un nivel de llamada más profundo que las comprobaciones de la regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo `TypeA` que implementa <xref:System.IDisposable> .

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo `TypeB` que hereda de Type `TypeA` y llama correctamente a su <xref:System.IDisposable.Dispose%2A> método.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.IDisposable?displayProperty=fullName> [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
