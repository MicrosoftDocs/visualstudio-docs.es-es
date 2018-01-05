---
title: 'CA2220: Los finalizadores deben llamar al finalizador de la clase base | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 46427cffe64c6c81e0f262520a61c1b1ea01fff8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Los finalizadores deben llamar al finalizador de la clase base
|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|Identificador de comprobación|CA2220|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Un tipo que invalida <xref:System.Object.Finalize%2A?displayProperty=fullName> no llama a la <xref:System.Object.Finalize%2A> método en su clase base.  
  
## <a name="rule-description"></a>Descripción de la regla  
 La finalización se debe difundir a través de la jerarquía de herencia. Para asegurarse de esto, los tipos deben llamar a su clase base <xref:System.Object.Finalize%2A> método desde sus propias <xref:System.Object.Finalize%2A> método. El compilador de C# agrega automáticamente la llamada al finalizador de clase base.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, llame al tipo base <xref:System.Object.Finalize%2A> método desde su <xref:System.Object.Finalize%2A> método.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Algunos compiladores que tienen como destino common language runtime inserción una llamada al finalizador del tipo base en el lenguaje intermedio de Microsoft (MSIL). Si aparece una advertencia de esta regla, el compilador no inserta la llamada y debe agregarlo a su código.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de Visual Basic muestra un tipo `TypeB` que llama correctamente a la <xref:System.Object.Finalize%2A> método en su clase base.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)