---
title: 'CA1816: Llamar a GC. SuppressFinalize correctamente | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e99f722d211b2e1bd548f1bf22c995246f3e0b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Llamar a GC.SuppressFinalize correctamente
|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|Identificador de comprobación|CA1816|  
|Categoría|Microsoft. Uso|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
  
-   Un método que es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Un método que no es una implementación de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> llamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Un método llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> y pasa algo distinto de esto (Me en Visual Basic).  
  
## <a name="rule-description"></a>Descripción de la regla  
 El <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> método permite a los usuarios liberar los recursos en cualquier momento antes de que el objeto se encuentre disponible para la recolección de elementos. Si el <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> se llama al método, libera los recursos del objeto. Esto hace la finalización innecesaria. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>debe llamar a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> por lo que el recolector de elementos no utilizados no llame al finalizador del objeto.  
  
 Para evitar que los tipos derivados con los finalizadores de tener que volver a implementar <xref:System.IDisposable> y para llamarlo, tipos no sellados sin los finalizadores deben llamar a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla:  
  
 Si el método es una implementación de <xref:System.IDisposable.Dispose%2A>, agregue una llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 Si el método no es una implementación de <xref:System.IDisposable.Dispose%2A>, quite la llamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> o moverlo al tipo <xref:System.IDisposable.Dispose%2A> implementación.  
  
 Cambiar todas las llamadas a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para pasar esto (Me en Visual Basic).  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Sólo suprima las advertencias de esta regla si están utilizando de forma deliberada <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para controlar la duración de otros objetos. No suprima las advertencias de esta regla si una implementación de <xref:System.IDisposable.Dispose%2A> no llama a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. En este caso, si no se puede suprimir la finalización disminuye el rendimiento y no proporcionar ninguna ventaja.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un método que incorrectamente llamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un método que correctamente las llamadas <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## <a name="see-also"></a>Vea también  
 [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)