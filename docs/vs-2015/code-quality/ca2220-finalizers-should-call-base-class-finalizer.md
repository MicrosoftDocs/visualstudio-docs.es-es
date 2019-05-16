---
title: 'CA2220: Los finalizadores deben llamar al finalizador de la clase base | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e069e3a75e05e958b563430fa02d9def104aa716
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685116"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Los finalizadores deben llamar al finalizador de la clase base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|Identificador de comprobación|CA2220|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo que invalida <xref:System.Object.Finalize%2A?displayProperty=fullName> no llama a la <xref:System.Object.Finalize%2A> método en su clase base.

## <a name="rule-description"></a>Descripción de la regla
 La finalización se debe difundir a través de la jerarquía de herencia. Para asegurarse de esto, tipos deben llamar a su clase base <xref:System.Object.Finalize%2A> método dentro de sus propios <xref:System.Object.Finalize%2A> método. El compilador de C# agrega automáticamente la llamada al finalizador de la clase base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame al tipo base <xref:System.Object.Finalize%2A> método desde su <xref:System.Object.Finalize%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Algunos compiladores que tienen como destino common language runtime inserción una llamada al finalizador del tipo base en el lenguaje intermedio de Microsoft (MSIL). Si se notifica una advertencia de esta regla, el compilador no inserta la llamada y debe agregarlo a su código.

## <a name="example"></a>Ejemplo
 El siguiente ejemplo de Visual Basic muestra un tipo `TypeB` que llama correctamente a la <xref:System.Object.Finalize%2A> método en su clase base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Vea también
 [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
