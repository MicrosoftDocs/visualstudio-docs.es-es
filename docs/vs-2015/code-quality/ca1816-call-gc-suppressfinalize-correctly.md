---
title: 'CA1816: Llamar a GC. SuppressFinalize correctamente | Microsoft Docs'
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
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e8c5123cc67dd6de273b9740a0a7dd4d7824eb10
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591917"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Llamar a GC.SuppressFinalize correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1816: llamar a GC. SuppressFinalize correctamente](https://docs.microsoft.com/visualstudio/code-quality/ca1816-call-gc-suppressfinalize-correctly).

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|Identificador de comprobación|CA1816|
|Categoría|Microsoft. Uso|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

-   Un método que es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Un método que no es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> llamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Llama un método <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> y pasa algo distinto de esto (Me en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla
 El <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método permite a los usuarios liberar los recursos en cualquier momento antes que el objeto se encuentre disponible para la recolección de elementos. Si el <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> se llama al método, libera los recursos del objeto. Esto hace que la finalización innecesaria. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> debe llamar a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> por lo que el recolector de elementos no utilizados no llame al finalizador del objeto.

 Para evitar que los tipos derivados con los finalizadores de tener que volver a implementar [System.IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) y para llamar a él, los tipos no sellados los finalizadores deben llamar a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla:

 Si el método es una implementación de <xref:System.IDisposable.Dispose%2A>, agregue una llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Si el método no es una implementación de <xref:System.IDisposable.Dispose%2A>, quite la llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> o muévalo a la del tipo <xref:System.IDisposable.Dispose%2A> implementación.

 Cambiar todas las llamadas a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pasar esto (Me en Visual Basic).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Sólo suprima una advertencia de esta regla si están utilizando de forma deliberada <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para controlar la duración de otros objetos. No suprima una advertencia de esta regla si una implementación de <xref:System.IDisposable.Dispose%2A> no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. En esta situación, no se puede suprimir la finalización disminuye el rendimiento y no proporcionan ninguna ventaja.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que incorrectamente llamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que correctamente las llamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Vea también
 [Patrón de Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



