---
title: 'CA2220: los finalizadores deben llamar al finalizador de la clase base | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5d9139314d52c4c50de84a45f227e6df5715bf02
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540665"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Los finalizadores deben llamar al finalizador de la clase base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|Identificador de comprobación|CA2220|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un tipo que invalida no <xref:System.Object.Finalize%2A?displayProperty=fullName> llama al <xref:System.Object.Finalize%2A> método en su clase base.

## <a name="rule-description"></a>Descripción de la regla
 La finalización se debe difundir a través de la jerarquía de herencia. Para garantizar esto, los tipos deben llamar a su <xref:System.Object.Finalize%2A> método de clase base desde dentro de su propio <xref:System.Object.Finalize%2A> método. El compilador de C# agrega automáticamente la llamada al finalizador de la clase base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame al método del tipo base <xref:System.Object.Finalize%2A> desde su <xref:System.Object.Finalize%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Algunos compiladores que tienen como destino el Common Language Runtime insertar una llamada al finalizador del tipo base en el lenguaje intermedio de Microsoft (MSIL). Si se indica una advertencia de esta regla, el compilador no inserta la llamada y debe agregarla al código.

## <a name="example"></a>Ejemplo
 En el siguiente ejemplo de Visual Basic se muestra un tipo `TypeB` que llama correctamente al <xref:System.Object.Finalize%2A> método en su clase base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Consulte también
 [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
