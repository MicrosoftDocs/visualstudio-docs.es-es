---
title: 'CA2220: Los finalizadores deben llamar al finalizador de la clase base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 034f80c9198ab098070e6642f4a4d96cff1744c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541863"
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

La finalización se debe difundir a través de la jerarquía de herencia. Para asegurarse de esto, tipos deben llamar a su clase base <xref:System.Object.Finalize%2A> método dentro de sus propios <xref:System.Object.Finalize%2A> método. El compilador de C# agrega automáticamente la llamada al finalizador de la clase base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, llame al tipo base <xref:System.Object.Finalize%2A> método desde su <xref:System.Object.Finalize%2A> método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. Algunos compiladores que tienen como destino common language runtime inserción una llamada al finalizador del tipo base en el lenguaje intermedio de Microsoft (MSIL). Si se notifica una advertencia de esta regla, el compilador no inserta la llamada y debe agregarlo a su código.

## <a name="example"></a>Ejemplo

El siguiente ejemplo de Visual Basic muestra un tipo `TypeB` que llama correctamente a la <xref:System.Object.Finalize%2A> método en su clase base.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Vea también

- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)