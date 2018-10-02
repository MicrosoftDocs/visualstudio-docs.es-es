---
title: 'CA2215: Los métodos Dispose deben llamar al método dispose de clase base | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bacd16fa8c58fcbe6646e1b7c5f2a26fad8e4ce3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591194"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Los métodos Dispose deben llamar a Dispose de clase base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA2215: los métodos Dispose deben llamar al método dispose de clase base](https://docs.microsoft.com/visualstudio/code-quality/ca2215-dispose-methods-should-call-base-class-dispose).

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

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si la llamada a `base`.<xref:System.IDisposable.Dispose%2A> se produce en un nivel más profundo que realiza la llamada a las comprobaciones de la regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo `TypeA` que implementa <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo `TypeB` que hereda del tipo `TypeA` y llama correctamente a su <xref:System.IDisposable.Dispose%2A> método.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Vea también
 <xref:System.IDisposable?displayProperty=fullName> [Patrón de Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



