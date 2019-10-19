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
ms.openlocfilehash: 1a4538c66d351956da8168d4f84c1895190ab453
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663590"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Los finalizadores deben llamar al finalizador de la clase base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|Identificador de comprobación|CA2220|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo que invalida <xref:System.Object.Finalize%2A?displayProperty=fullName> no llama al método <xref:System.Object.Finalize%2A> en su clase base.

## <a name="rule-description"></a>Descripción de la regla
 La finalización se debe difundir a través de la jerarquía de herencia. Para garantizar esto, los tipos deben llamar a su clase base <xref:System.Object.Finalize%2A> método desde dentro de su propio método <xref:System.Object.Finalize%2A>. El C# compilador agrega la llamada al finalizador de la clase base automáticamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame al método <xref:System.Object.Finalize%2A> del tipo base desde el método <xref:System.Object.Finalize%2A>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Algunos compiladores que tienen como destino el Common Language Runtime insertar una llamada al finalizador del tipo base en el lenguaje intermedio de Microsoft (MSIL). Si se indica una advertencia de esta regla, el compilador no inserta la llamada y debe agregarla al código.

## <a name="example"></a>Ejemplo
 En el siguiente ejemplo de Visual Basic se muestra un tipo `TypeB` que llama correctamente al método <xref:System.Object.Finalize%2A> en su clase base.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Vea también
 [Patrón de Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
